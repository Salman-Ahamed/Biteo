# 12. Error Detection Strategy

## Purpose

Define the operating policy FastBite uses to detect, classify, escalate, recover from, and communicate errors across inbound channel ingestion, canonical order processing, outbound commands, and post-order reconciliation.

This document is written for an MVP-stage team running a modular monolith with background workers, a transactional outbox, raw event storage, and an operator exception queue, as described in `05-integrations-and-data-model.md`, `07-system-architecture-and-reliability.md`, and `13-platform-architecture.md`.

## Strategy Direction

The operating model should remain queue-first, replay-safe, and audit-friendly.

Core direction:

- queue-first ingestion, idempotency, replay, and reconciliation are the foundation for webhook-heavy integrations
- errors should be separated by whether they are retryable, operator-actionable, merchant-actionable, or incident-grade
- dead-letter queues are for diagnosis and controlled recovery, not silent storage
- on-call pages should be reserved for issues that are immediately human-actionable and threaten active order flow or the practical error budget

This version makes the following changes explicit:

- transient faults are separated from actionable exceptions more clearly
- escalation uses blast radius, age, and user impact instead of paging on every isolated failure
- backlog, silent-failure, replay, and audit controls are made explicit
- merchant-facing degradation rules are tightened so merchants see operational truth without becoming the monitoring system
- planned low-traffic maintenance is treated separately from the main reliability problem, which is unexpected failure during live order flow

## Operating Principles

1. FastBite treats external events as at-least-once and potentially out-of-order.
2. The canonical order record in PostgreSQL is the operational source of truth.
3. Ingestion should acknowledge quickly after authentication, persistence, and enqueue, then process asynchronously.
4. Retries handle short-lived faults, replay handles contained processing failures, and reconciliation handles missed or silent failures.
5. A human should only be paged when immediate action can reduce active order impact.
6. Merchants should only see issues that change what they must do now.
7. Every unresolved exception and every manual override must be auditable.
8. If FastBite cannot confirm a state change, it must present that state as pending, degraded, or at-risk rather than successful.

## What This Document Is Trying To Do

FastBite needs one operating policy that lets product, engineering, and operations answer five questions consistently:

1. Did we receive the event safely?
2. Did we apply it correctly to canonical state?
3. Did we successfully send required actions back out?
4. If not, who needs to act now: automation, operator, merchant, or on-call?
5. Can we later prove what happened and recover without losing order or payment context?

## Failure Classification Model

FastBite should classify failures using both failure family and response class.

### Failure Families

| Family                | Definition                                                     | Typical Examples                                                          |
| --------------------- | -------------------------------------------------------------- | ------------------------------------------------------------------------- |
| ingress failure       | FastBite could not safely accept or interpret an inbound event | bad signature, malformed JSON, unsupported event type                     |
| processing failure    | FastBite accepted the event but could not apply it correctly   | invalid state transition, handler crash, database write failure           |
| delivery failure      | FastBite could not complete an outbound command or side effect | 5xx from channel, timeout on accept call, rate limit                      |
| consistency failure   | data across systems no longer agrees or a signal is missing    | conflicting statuses, missed webhook, payment mismatch                    |
| control-plane failure | the monitoring or recovery mechanism itself is impaired        | queue backlog, stuck workers, exception queue not updating, no-data alert |

### Response Classes

These response classes are more operationally useful than severity labels alone.

| Response Class      | Meaning                                                            | Default Action                                                |
| ------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------- |
| transient           | likely safe to retry automatically                                 | retry with backoff and jitter, no human notification yet      |
| deferred-actionable | automation could not finish, but immediate paging is not warranted | create operator issue, durable trace, business-hours response |
| merchant-actionable | the merchant must change behavior to avoid fulfillment failure     | show degraded state in UI and create operator issue           |
| incident-grade      | active order flow or trust boundary is materially threatened       | page on-call, open incident log, apply runbook                |

## Error Taxonomy And Default Handling

### 1. Inbound Channel And Webhook Errors

| Error Type                                          | Response Class                                                                      | Default Handling                                                                 | Notes                                                                                                  |
| --------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------ |
| signature or auth failure                           | incident-grade only if rate spike or multi-connector; otherwise deferred-actionable | reject, log, count by connector, create operator issue if persistent             | A single bad request should not wake on-call; a sustained spike may indicate misconfiguration or abuse |
| replay-window or timestamp failure                  | deferred-actionable                                                                 | reject, log as possible replay or clock skew                                     | Keep separate from generic auth failures                                                               |
| malformed or schema-invalid payload                 | deferred-actionable                                                                 | persist raw payload if possible, dead-letter, create connector issue             | High importance, but often not page-worthy as an isolated event                                        |
| duplicate event                                     | transient                                                                           | deduplicate silently with event ID or business key                               | Count rate for connector health, do not alert on single duplicates                                     |
| out-of-order event                                  | transient first, then deferred-actionable                                           | hold briefly, fetch latest state if supported, apply timestamp or version checks | Do not surface to merchant unless order action is blocked                                              |
| unsupported event type                              | deferred-actionable                                                                 | log, dead-letter, create adapter backlog item                                    | Track as connector coverage gap                                                                        |
| ingestion timeout before durable accept             | incident-grade if sustained                                                         | alert based on failed durable accepts or provider retry storm                    | Threatens order capture or duplicate storms                                                            |
| provider delivered nothing when traffic is expected | deferred-actionable or incident-grade depending on duration and blast radius        | no-data alert, trigger polling or synthetic check, investigate source            | Missing events are a distinct failure class and must not rely on provider retries to reveal themselves |

### 2. Canonical Processing And State Errors

| Error Type                                               | Response Class                                                                         | Default Handling                                                                                                      |
| -------------------------------------------------------- | -------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| invalid state transition                                 | incident-grade if caused by code path or broad data bug; otherwise deferred-actionable | reject transition, record full state context, create bug-linked issue                                                 |
| handler crash after raw event persistence                | deferred-actionable                                                                    | retry worker, then dead-letter and replay after fix                                                                   |
| order created but downstream projection not updated      | deferred-actionable                                                                    | surface to operator if active order view is stale beyond threshold                                                    |
| conflicting state from two external sources              | deferred-actionable or merchant-actionable                                             | freeze auto-advance, show operator both states, expose at-risk banner to merchant only if kitchen action may be wrong |
| stuck order in non-terminal state                        | merchant-actionable                                                                    | flag timed-out state, create operator issue, notify merchant if a decision is required                                |
| missing merchant acknowledgement                         | merchant-actionable                                                                    | alert merchant in dashboard, keep operator issue open until accepted, rejected, or expired                            |
| orphaned canonical record or missing raw event reference | deferred-actionable                                                                    | quarantine for audit review; do not auto-delete                                                                       |
| payment state mismatch blocking next step                | merchant-actionable if order flow blocked; incident-grade if widespread                | hold irreversible transition, create finance or ops issue                                                             |

### 3. Outbound Command And Side-Effect Errors

| Error Type                                                         | Response Class                             | Default Handling                                                                          |
| ------------------------------------------------------------------ | ------------------------------------------ | ----------------------------------------------------------------------------------------- |
| transient 5xx or timeout                                           | transient                                  | retry with backoff and jitter                                                             |
| rate limit exceeded                                                | transient                                  | slow connector lane, retry later, monitor backlog age                                     |
| command not supported by capability matrix                         | not an error if matrix is correct          | suppress action in UI, log capability decision                                            |
| stale command rejected by provider                                 | deferred-actionable                        | fetch latest external state, compare, create operator issue if mismatch remains           |
| retry exhaustion on isolated order                                 | deferred-actionable or merchant-actionable | move to DLQ, create operator issue, show merchant warning only if their action is blocked |
| retry exhaustion across many active orders                         | incident-grade                             | page on-call and consider pausing that connector action path                              |
| outbound command succeeded remotely but local confirmation missing | deferred-actionable                        | reconciliation fetch, idempotent status read, avoid double-send                           |

### 4. Reconciliation, Settlement, And Audit Errors

| Error Type                                                               | Response Class                                                  | Default Handling                                                   |
| ------------------------------------------------------------------------ | --------------------------------------------------------------- | ------------------------------------------------------------------ |
| missing webhook but later API or report record exists                    | deferred-actionable                                             | backfill via reconciliation and mark as missed-event recovery      |
| order accepted in FastBite but absent in settlement or payout export     | deferred-actionable until clustered; incident-grade if systemic | create finance issue and connector-quality signal                  |
| settlement amount mismatch                                               | deferred-actionable                                             | hold auto-close of finance case until matched or explained         |
| cancellation or refund not reflected in payout data                      | deferred-actionable                                             | finance review with raw evidence and provider reference            |
| unresolved audit gap for manual override, refund, or state force-advance | incident-grade for compliance posture                           | block privileged action completion until audit metadata is present |

### 5. Control-Plane And Recovery Failures

| Error Type                                 | Response Class                                      | Default Handling                                                                                  |
| ------------------------------------------ | --------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| queue backlog or drain-time growth         | deferred-actionable or incident-grade               | alert on age and drain risk, not raw depth alone                                                  |
| dead-letter queue receiving messages       | deferred-actionable by default                      | open operator issue on first active-order failure; page only on aging backlog or clustered impact |
| exception queue writer failed              | incident-grade                                      | page because human recovery path is impaired                                                      |
| observability no-data condition            | incident-grade if it blinds active-order monitoring | test alert, synthetic probe, restore telemetry                                                    |
| replay tooling unavailable during incident | deferred-actionable                                 | record as recovery-risk issue; fix before scaling connector scope                                 |

## Detection Responsibilities By Layer

Each layer owns the errors it can observe directly. Ownership aligns with the architecture in `05`, `07`, and `13`.

```text
[Inbound Webhook / API Event]
    |
    v
[Adapter Layer]
    Detects: auth failures, replay-window violations, malformed payloads,
             duplicates, out-of-order events, unsupported types,
             durable-accept failures, provider no-data conditions
    Owns:    raw event persistence, connector metrics, initial dead-lettering
    |
    v
[Canonical Order Service]
    Detects: invalid transitions, conflicting states, stuck orders,
             missing acknowledgements, payment-gated state errors,
             projection freshness gaps
    Owns:    canonical correctness, timeout jobs, order risk state
    |
    v
[Outbound Action Router]
    Detects: timeouts, 4xx/5xx responses, rate limits,
             stale command conflicts, retry exhaustion
    Owns:    retry policy, command attempt ledger, DLQ on exhaustion
    |
    v
[Reconciliation Jobs]
    Detects: missed events, external-vs-canonical mismatches,
             settlement and refund mismatches, payout gaps
    Owns:    backfill, finance exception creation, daily control reports
    |
    v
[Exception Queue + Operator Dashboard]
    Detects: aging unresolved issues, missed operator SLAs,
             need for merchant contact or channel escalation
    Owns:    manual triage, override workflow, support handoff
    |
    v
[On-Call / Incident Response]
    Detects: only incident-grade conditions routed from the layers above
    Owns:    restoring active-order flow, reducing blast radius,
             opening incident log and follow-up actions
```

### Ownership Rules

- product owns merchant-visible wording, degraded states, and operator workflow design
- engineering owns detection logic, retry safety, audit completeness, and runbooks
- operations owns queue triage, merchant contact, channel-support escalation, and manual recovery within approved controls
- finance or operations owns settlement mismatch review until dedicated finance operations exists

## Merchant-Facing And Operator-Facing Error Handling Rules

### Merchant-Facing Rules

| Situation                                            | What Merchant Sees                                                | Why                                                   |
| ---------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------- |
| order received but external confirmation pending     | visible order with `pending confirmation` or `pending sync` state | truthful state without false success                  |
| action still retrying in background                  | advisory banner or disabled button, not a fatal error             | merchant usually cannot help yet                      |
| merchant action overdue                              | prominent warning on that order                                   | merchant can still reduce harm                        |
| channel state conflict that changes kitchen behavior | `status at risk` or `check before preparing / handing off`        | only surface when merchant must behave differently    |
| connector degraded but confirmed ingestion continues | top-level degraded-mode banner plus source labels                 | helps the merchant trust what is and is not confirmed |
| reconciliation-only finance issue                    | not shown in live kitchen flow                                    | no immediate merchant action                          |

### Operator-Facing Rules

Operators need more detail than merchants:

- full connector, order, and raw-event references
- attempt history and retry state
- blast-radius grouping by connector and merchant
- age, first seen, last retried, and drain-time indicators
- recommended runbook or next action
- explicit indicator of whether merchant has already been warned

### Visibility Policy

The merchant UI is not the primary observability surface.

- merchant sees order-local truth and required actions
- operator sees system-local detail, grouped failures, and recovery tooling
- on-call sees only incident-grade summaries with direct runbook links

## Escalation Ladder

The escalation ladder should be based on impact, time, and recovery path, not on technical error existence alone.

### Level 0 — Log Only

Use for noise that is handled safely and has no current operator value.

- duplicates deduplicated successfully
- stale events discarded after version check
- first transient retry attempts within policy
- unsupported merchant action hidden because capability matrix prevented send

### Level 1 — Operator Queue

Use when automation could not complete, but an active page would be disproportionate.

- isolated malformed payloads from one connector
- unsupported event types
- single-order retry exhaustion where manual workaround exists
- settlement mismatch on one order or one payout record
- polling fallback activated for one connector

Target response: same business day during staffed hours; within 15 minutes for active orders during live service.

### Level 2 — Merchant + Operator Action

Use when the merchant must take or avoid an action.

- order awaiting merchant acknowledgement past the configured accept window
- channel state conflict that could cause the kitchen to prepare or stop incorrectly
- payment uncertainty blocking preparation, refund, or completion
- no-rider or dispatch-related blockage if that order remains under FastBite operational responsibility

Target response: immediate in-product warning plus operator follow-up.

### Level 3 — On-Call Page

Use only when immediate human action can reduce active-order harm.

- FastBite cannot durably accept inbound orders
- active-order backlog age is rising enough to threaten order freshness or acknowledgement SLA
- exception queue or telemetry blind spot prevents operators from seeing active failures
- widespread outbound acknowledgement failures across a connector or multiple merchants
- canonical state corruption or invalid transition bug affecting more than one order or connector lane
- security-significant auth failure spike across connectors or from a concentrated source

## MVP Alerting Policy

For an MVP team, static thresholds should be treated as starting values, not promises. Use count plus duration plus blast radius.

### Page On-Call When Any Of The Following Is True

| Signal                                       | Starter Threshold                                                                                                                         | Why This Pages                              |
| -------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| durable inbound accept failure               | any sustained failure for 5 minutes on an active connector                                                                                | threatens order capture                     |
| active-order processing lag                  | p95 age from receipt to canonical write > 2 minutes for 15 minutes, or oldest active event > 5 minutes                                    | backlog is now operational, not cosmetic    |
| outbound acknowledgement failure cluster     | > 20 percent failure rate over 15 minutes on one connector and affecting at least 5 active orders or 3 merchants                          | broad live-service impact                   |
| queue recovery path impaired                 | exception queue write failure, replay pipeline unavailable during live incident, or monitoring no-data on critical signals for 10 minutes | humans are blind or unable to recover       |
| state-machine correctness issue              | repeated invalid transitions from the same release or code path affecting more than one order                                             | likely code or data integrity defect        |
| security-significant signature failure spike | 5x baseline and at least 20 failures in 10 minutes on a connector                                                                         | possible credential rotation issue or abuse |

### Open An Operator Issue, But Do Not Page Yet

| Signal                      | Starter Threshold                                                                                       | Why This Stays With Operators                                    |
| --------------------------- | ------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------- |
| isolated retry exhaustion   | one order or one outbound command family                                                                | manual workaround is possible                                    |
| dead-letter entry           | any active-order event enters DLQ                                                                       | needs triage, but not necessarily immediate page                 |
| aging DLQ backlog           | page only if more than 5 active-order events are older than 15 minutes or drain time exceeds 30 minutes | age matters more than raw count                                  |
| settlement mismatch cluster | more than 10 orders or one merchant-day batch with mismatch                                             | financial review, usually not live-order paging                  |
| polling fallback active     | connector in degraded mode for more than 30 minutes                                                     | business-hours reliability task unless active orders are blocked |

### Merchant-Visible But Not Page-Worthy By Default

- awaiting acknowledgement beyond merchant action window
- one order whose outbound status update is still retrying
- one order whose channel state is unclear and needs merchant caution
- manual fallback mode for a connector where FastBite can still show confirmed ingestion honestly

## Recovery Patterns

### Retry With Exponential Backoff And Jitter

Use for network timeouts, 5xx responses, transient lock contention, and rate-limit recovery.

Starter schedule:

- attempt 1: immediate
- attempt 2: 5 seconds plus jitter
- attempt 3: 30 seconds plus jitter
- attempt 4: 2 minutes plus jitter
- attempt 5: 10 minutes plus jitter

After exhaustion:

- move the work item to DLQ or failed-command ledger
- create an operator issue with the order, connector, attempt history, and last error
- suppress merchant warning unless the merchant must change behavior

### Replay From Raw Event Store

Use after handler defects, consumer crashes, or connector configuration errors.

- store raw payload, headers, receipt timestamp, connector, and verification result before processing
- replay through the same adapter and canonical pipeline, not through ad hoc scripts
- require idempotent handlers and replay reason codes
- record who initiated replay, which event range was replayed, and whether side effects were suppressed or reissued

### Reconciliation As Safety Net

Retries handle minutes of failure. Replay handles contained processing gaps. Reconciliation catches everything else.

Daily or connector-specific reconciliation should:

- compare expected active and terminal orders against external API or report data
- detect missed webhooks, status drift, payment-state mismatches, refund gaps, and payout mismatches
- backfill missing state with explicit provenance such as `recovered_via_poll` or `recovered_via_settlement_import`
- produce a dated control report even when no mismatches are found

### Manual Operator Override

Allow only bounded, auditable actions:

- mark issue reviewed with reason
- requeue failed command
- force state advance or closure only when supported by external evidence
- initiate approved refund or channel-support escalation
- place merchant into manual-fallback mode for a connector

Every override must capture:

- operator identity
- timestamp
- prior and new state
- justification
- evidence reference such as raw event, support ticket, payment reference, or phone confirmation

### Polling Fallback

Polling is a recovery and audit mechanism, not the primary truth path.

Use polling when:

- a connector has documented weak webhook guarantees
- no-data monitoring suggests missed events
- reconciliation needs a point-in-time status read
- payout or payment confirmation requires periodic audit queries

Polling controls:

- store last-processed checkpoint
- rate limit by connector
- send fetched state through the same adapter path as webhook data
- mark records recovered through polling distinctly in audit and metrics

## Observability And Audit Requirements

Each material failure event must emit a structured record with at least:

- `failure_family`
- `error_type`
- `response_class`
- `connector_id`
- `merchant_id` where known
- `order_id` where known
- `external_order_id` where known
- `raw_event_id` where applicable
- `command_id` where applicable
- `occurred_at`
- `first_detected_at`
- `last_attempt_at`
- `attempt_count`
- `current_owner` such as automation, ops, merchant, on_call
- `resolution_state` such as auto_recovered, awaiting_operator, awaiting_merchant, reconciled, resolved

FastBite should additionally track these operational metrics:

- inbound durable accept success rate
- duplicate rate by connector
- unsupported event rate by connector
- active-event backlog age and estimated drain time
- outbound command success and retry exhaustion rate
- stuck-order count by state and merchant
- no-data alerts by connector
- reconciliation mismatch count and aging
- manual override count by type and operator

## Controls That Must Exist Before Expanding Connector Scope

1. raw event persistence before business processing
2. idempotency keys or equivalent dedupe for every inbound and outbound path
3. dead-letter storage with replay path
4. no-data or silence detection for expected inbound traffic
5. operator queue with issue aging and ownership
6. audit log for overrides and finance-impacting changes
7. reconciliation job for critical connectors and payment flows
8. runbooks for connector outage, backlog growth, and payment mismatch scenarios

## Assumptions And Thresholds That Need Tuning After Launch

These are necessary but not yet externally verifiable for FastBite specifically:

- the exact merchant acknowledgement timeout per channel or merchant segment
- the specific backlog ages that correlate with order spoilage or missed SLA in live traffic
- the exact no-data expectation per connector and daypart
- which connectors require polling from day one rather than only as fallback
- how many active orders or merchants justify paging for connector-specific outbound failures

Until live baselines exist, FastBite should review these thresholds weekly, not treat them as fixed policy.

## Relationship To Other Documents

| Document                                                                                 | Relationship                                                                                                               |
| ---------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)                 | Defines raw event storage, adapter behavior, capability asymmetry, and canonical order ownership that detection depends on |
| [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md) | Defines transactional outbox, modular-monolith MVP posture, durability goals, and observability baseline                   |
| [04-product-and-operations.md](./04-product-and-operations.md)                           | Defines merchant degraded mode, manual fallback, and operator exception handling needs                                     |
| [13-platform-architecture.md](./13-platform-architecture.md)                             | Defines queue, DLQ, worker, and observability platform responsibilities                                                    |

## Source Notes

These sources informed the operating policy. They support the direction of the policy, but not every numeric threshold above. FastBite-specific thresholds remain assumptions until live data exists.

| Source                                                           | Type                          | Why It Matters                                                                                                                                                  | Recency                                                |
| ---------------------------------------------------------------- | ----------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| Google SRE Workbook: Alerting on SLOs                            | primary-practice reference    | Supports paging on significant user-impact or error-budget threats, not every threshold breach; recommends page versus ticket separation and multi-window logic | 2018 reference, still widely used operational guidance |
| Google SRE Workbook: Implementing SLOs                           | primary-practice reference    | Supports choosing measurable user-centric signals, using error budgets, and documenting owner actions when objectives are threatened                            | 2018 reference                                         |
| PagerDuty Incident Response: Alerting Principles                 | practitioner primary guidance | Supports the rule that pages must be immediately human-actionable and include runbook context                                                                   | live documentation accessed 2026                       |
| PagerDuty Incident Response: Severity Levels                     | practitioner primary guidance | Supports metric-driven severity definitions and separating major incidents from lower-priority operational issues                                               | live documentation accessed 2026                       |
| AWS SQS Developer Guide: Using dead-letter queues in Amazon SQS  | primary vendor documentation  | Supports DLQ use for isolation, diagnosis, redrive, retention policy, and avoiding overly low receive-count settings                                            | AWS docs accessed 2026                                 |
| AWS SQS Developer Guide: Error handling and problematic messages | primary vendor documentation  | Supports treating problematic messages and retention as explicit operational controls                                                                           | AWS docs accessed 2026                                 |
| Svix: Best Practices for Receiving Webhooks                      | practitioner guidance         | Supports signature verification, replay-window checks, and event-level idempotency for webhook receivers                                                        | accessed 2026                                          |
| Svix: Webhook Retry Best Practices                               | practitioner guidance         | Supports exponential backoff, jitter, and DLQ after retry exhaustion                                                                                            | accessed 2026                                          |
| Hookdeck: Webhooks at Scale                                      | practitioner guidance         | Supports queue-first ingestion, backlog age and drain-time monitoring, and layered retry, replay, and reconciliation controls                                   | published 2025, updated 2026                           |
| Hookdeck: How to Implement Webhook Idempotency                   | practitioner guidance         | Supports durable idempotency storage, processed-event ledgers, TTL aligned to retry windows, and replay-safe handlers                                           | accessed 2026                                          |
| Payabli: Decision Guide - Webhooks vs Polling                    | vendor documentation          | Supports using webhooks for real-time notifications plus polling for daily reconciliation, audits, and missed-event recovery                                    | live documentation accessed 2026                       |

## Open Questions

- What launch-day connectors have enough expected volume to justify no-data alerting by daypart?
- Which merchant actions should automatically pause connector-originated auto-advancement for that single order?
- What operator staffing window is realistic during lunch and dinner peaks for exception queue response?
- Which payment flows are allowed to proceed under `payment uncertain` versus `payment blocked` states?
- What evidence is sufficient for a forced order closure when channel and merchant records disagree?

## Read Next

- [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
- [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
- [04-product-and-operations.md](./04-product-and-operations.md)
