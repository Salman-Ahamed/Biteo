# 05. Integrations and Data Model

## Purpose

Define how marketplace orders, direct orders, and manual orders flow into one canonical operating system that product and engineering can build against.

## One-Page Summary

- FastBite should be the merchant's operational system of record, not just a dashboard layered on top of channel tools.
- A hybrid integration strategy is the right launch choice: use aggregators or partner-managed connectors where that materially shortens time to market, but keep the internal model and orchestration layer fully owned.
- Direct integrations should be prioritized first for owned channels and selectively for marketplaces only after a connector proves commercially important, operationally limiting, or margin-destructive.
- The canonical model must store both normalized business entities and raw channel evidence so FastBite can support retries, replay, reconciliation, and dispute handling.
- The MVP should assume channel asymmetry. Not every connector will support the same order states, menu controls, delivery telemetry, or retry guarantees.

## Integration Direction

FastBite should launch with a hybrid hub model, with one qualification: the architecture must be designed around uneven channel capability from day one.

Why this is the right posture:

- Uber Eats exposes direct APIs for orders, menus, store status, prep time, webhooks, and operational quality requirements. That supports a future direct-integration path for high-value channels.
- Just Eat exposes both POS-oriented order injection flows and a separate logistics product, which shows that marketplace ordering and last-mile delivery are often separate integration surfaces.
- Aggregation vendors such as Deliverect position themselves as a bridge across marketplaces, POS systems, dispatch providers, online ordering, and restaurant tooling. That makes them useful for launch speed, but not a substitute for FastBite's internal orchestration layer.
- Marketplace integrations rely heavily on webhooks and callbacks, which means duplicate delivery, out-of-order updates, and replay handling are architecture concerns, not connector edge cases.

Resulting position:

- Launch with a hybrid model.
- Do not treat aggregator-only architecture as the long-term default.
- Do not force a direct-only launch unless the commercial scope is intentionally narrow.

## Core Requirement

All order channels must feed one operational source of truth for merchant workflows.

That means:

- FastBite owns the canonical order record
- channel connectors translate and enrich external payloads
- the merchant sees one queue, one preparation workflow, and one exception surface
- channel-native tools become fallbacks, not the primary operating interface

## Architecture Decision

FastBite should use a hub-and-spoke model with a canonical order service at the center.

1. Ingest inbound events and payloads from marketplaces, direct ordering, and manual entry.
2. Persist raw channel payloads before business-side processing.
3. Normalize into canonical entities and states.
4. Drive merchant operations from canonical state, not from connector-specific state.
5. Publish outbound actions back to connectors only when the channel supports them.

## Options Considered

| Option                      | Pros                                                                        | Cons                                                                            | Recommendation                          |
| --------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | --------------------------------------- |
| direct integrations only    | strongest control, lower long-run dependency, better margin capture         | longer launch timeline, partner approval friction, higher certification burden  | not best for MVP unless scope is narrow |
| third-party aggregator only | fastest access to broad marketplace coverage                                | weakest control over roadmap, lower visibility into failures, margin dependency | acceptable bridge, weak long-term core  |
| hybrid hub model            | fastest practical launch while preserving control of core workflow and data | requires more upfront architecture discipline                                   | best option                             |

## Why Hybrid Is The Right Launch Choice

Hybrid is the right launch choice if FastBite treats the aggregator as a channel bridge, not as the system architecture.

Use aggregators early when:

- direct marketplace access requires partner approval or certification
- a merchant needs multiple marketplaces live quickly
- the product still needs to validate demand before building direct channel depth

Prioritize direct integrations earlier when:

- one marketplace becomes the dominant source of GMV or operational issues
- the aggregator blocks required workflows such as precise status control, store pause, menu updates, or reconciliation detail
- vendor fees materially compress unit economics
- the business needs channel-specific performance optimizations that a bridge cannot expose

## Delivery Principles

- Store raw payloads and headers for every external event.
- Verify signatures or shared-secret headers where supported.
- Acknowledge webhooks quickly, then process asynchronously.
- Design for at-least-once delivery and out-of-order events.
- Use entity-level idempotency and event-level deduplication.
- Fetch latest channel state when a webhook is only a notification envelope.
- Keep a channel capability matrix instead of assuming symmetric support.
- Prefer additive normalization over lossy simplification.

## Proposed Integration Architecture

```text
[Marketplace / Dispatch / Direct Channel]
		|
		v
      [Connector + Webhook Endpoint]
		|
		v
	[Raw Event Store + Dedupe]
		|
		v
	 [Channel Adapter Layer]
		|
		v
       [Canonical Order Service]
	 |        |         |
	 |        |         +--> [Reconciliation + Exceptions]
	 |        +------------> [Merchant Dashboard + KDS]
	 +---------------------> [Outbound Action Router]
				      |
				      v
			   [Channel API / Aggregator API]
```

## Channel Capability Model

FastBite should not model channels as equal. Each channel connection should declare supported capabilities such as:

- inbound order creation
- scheduled orders
- order accept or reject
- prep-time update
- ready-for-pickup update
- cancellation notification
- cancellation initiation
- refund visibility
- menu publication
- item-level availability update
- store pause or online status update
- courier telemetry
- settlement export
- replay or historical fetch

If a capability is unsupported, the merchant UI should degrade cleanly instead of pretending the action succeeded.

## Phased Integration Scope

### Phase 0: Foundations Before Channel Expansion

- canonical order schema and state model
- raw event storage
- idempotency keys and replay-safe consumers
- per-connector capability registry
- audit trail and operator exception queue
- manual order entry that uses the same canonical pipeline as external orders

This phase is mandatory. Without it, every later integration becomes expensive and fragile.

### Phase 1: Inbound Order Unification

- direct web orders
- manual or phone orders
- WhatsApp-led order capture only if FastBite controls the checkout handoff or confirms the final order explicitly
- marketplace ingestion through aggregator or approved partner connector
- one unified order queue and one KDS view

Scope note:

- The MVP should focus on reliable inbound normalization and merchant acknowledgement workflows, not on full two-way parity across every channel.

### Phase 2: Operational Two-Way Sync

- accept or reject where supported
- prep-time updates where supported
- ready status where supported
- cancellation receipt and propagation where supported
- store online or pause sync where supported
- item availability sync for high-risk stockout items where supported

Adjustment:

- Full menu publication should not be required for every channel in this phase. Item availability and serviceability controls usually matter more operationally than full catalog authoring.

### Phase 3: Exception Handling And Reconciliation

- replay failed events
- detect stale or conflicting state transitions
- reconcile accepted orders against merchant POS or KDS acknowledgement
- reconcile cancellation, amendment, and substitution flows
- surface unhandled channel events to operations
- add settlement and payout imports where data is available

### Phase 4: Direct Channel Optimization

- native integrations for the highest-volume or highest-margin channels
- channel-specific SLA logic
- richer store and menu controls
- delivery-provider orchestration and dispatch routing
- deeper profitability analytics by source and fulfillment type

## Canonical Data Model

The original object list is directionally correct but incomplete for a production integration layer.

### Core Reference Objects

- Merchant
- Store
- ChannelConnection
- ChannelCapability
- Menu
- MenuCategory
- MenuItem
- ModifierGroup
- ModifierOption
- CatalogAvailabilityRule

### Core Transaction Objects

- Order
- OrderRevision
- OrderLine
- FulfillmentPlan
- Payment
- Charge
- Tax
- Discount
- Tip
- Customer
- CustomerContact
- DeliveryAddress

### Operational State Objects

- OrderState
- PrepState
- DispatchState
- PaymentState
- CancellationState
- ExceptionCase
- ReconciliationIssue

### Integration Control Objects

- RawEvent
- IdempotencyKey
- ExternalReference
- IntegrationAttempt
- OutboundCommand
- SyncCheckpoint
- SettlementRecord

## Minimum Canonical Order Fields

Every order should capture at least:

- internal order ID
- channel order ID
- merchant and store IDs
- source channel and connector type
- fulfillment type: delivery-by-marketplace, delivery-by-merchant, pickup, dine-in if later supported
- order placement timestamp
- requested promise times: collect, deliver, ready, scheduled
- current order, prep, dispatch, payment, and cancellation states
- customer notes split by kitchen, collection, and delivery intent when available
- item lines, modifiers, quantities, unit prices, and total amounts
- taxes, discounts, fees, tips, and settlement-relevant amounts
- customer contact and masked contact fields when partial data is all a channel exposes
- courier or collector details when available
- raw payload reference and source event history

## State Model Requirements

The current document names state objects but does not define the state system. That is a gap.

FastBite should use multiple orthogonal state dimensions rather than one flat status field.

### Canonical Order Lifecycle

- received
- fetched
- pending_acceptance
- accepted
- rejected
- in_preparation
- ready_for_handoff
- handed_off
- completed
- cancelled
- failed_injection
- awaiting_resolution

### Prep State

- not_started
- queued
- prepping
- ready
- delayed
- abandoned

### Dispatch State

- not_required
- awaiting_assignment
- assigned
- arriving_at_store
- at_store
- picked_up
- en_route
- at_customer
- delivered
- failed_delivery
- returned

### Payment State

- unknown
- prepaid
- authorized
- captured
- cash_on_delivery
- refunded_partial
- refunded_full
- settlement_pending
- settled

### Cancellation State

- none
- cancel_requested
- cancelled_by_customer
- cancelled_by_merchant
- cancelled_by_channel
- cancellation_failed

## Why The Canonical Model Matters

Every platform expresses timing, line items, statuses, and modifications differently. Without a canonical model:

- the merchant queue becomes inconsistent
- automation rules become connector-specific
- analytics become misleading
- reconciliation becomes manual
- every new connector forces product behavior to change

## Adapter Architecture

```text
[Uber Eats Connector] -----|
[Just Eat / JET Connector]-|
[Aggregator Connector] ----|--> [Channel Adapter Layer] --> [Canonical Order Service] --> [Dashboard + KDS + Dispatch + Reconciliation]
[Direct Web Orders] -------|
[Manual / Phone Orders] ---|
```

## Adapter Responsibilities

The original list is incomplete. A production adapter should own:

- authentication, credential rotation, and connector configuration
- inbound signature verification where available
- raw payload capture before transformation
- event deduplication and idempotency enforcement
- channel-to-canonical field mapping
- fetch-latest behavior when the webhook is only a notification wrapper
- state transition validation against channel capability rules
- outbound command mapping and retry policy
- rate-limit handling and backoff
- observability: logs, metrics, traces, and dead-letter cases
- replay support and reconciliation hooks
- versioning support for connector schema changes

## Canonical Order Service Responsibilities

- source-of-truth order aggregates
- entity-level state machines
- merchant workflow rules
- throttling and load-shedding logic
- preparation and readiness timing
- dispatch triggers and dispatch handoff
- operator exception routing
- audit logs and event history
- reconciliation jobs against external systems

## Reliability And Unsupported Channel Behaviors

The document should explicitly assume the following:

- webhook retries may happen, and some providers require a fast acknowledgement path
- webhook ordering cannot be relied on globally
- some connectors provide only a notification plus a fetch URL or order ID
- some connectors support async acknowledgement windows rather than immediate synchronous completion
- some dispatch APIs do not retry failed webhooks, so FastBite needs polling or status fetch fallbacks where available
- store status, menu updates, substitutions, and cancellation reasons are channel-specific and may not normalize perfectly

Implication:

- the canonical system must preserve raw channel semantics even while exposing a simplified merchant-facing view

## Reconciliation Requirements

FastBite should treat reconciliation as part of the core design, not a later finance feature.

Minimum reconciliation loops:

- inbound event received versus canonical order created
- order accepted versus merchant actually saw it in KDS or POS
- cancellation received versus merchant preparation state
- item substitution or amendment request versus final order revision
- completed order versus settlement record when data is available
- outbound command sent versus provider acknowledgement or failure

## Commercial Value Of The Integration Layer

This is a technical moat and a sales wedge.

The merchant pitch remains:

Keep your discovery channels if you want. FastBite gives you one operational workflow, one exception queue, and a controlled path to shift volume into direct channels without creating channel chaos.

## Open Questions

- Which aggregator or bridge partner offers the best UK coverage, error visibility, and commercial terms for the first launch cohort?
- Which marketplace capabilities are required for MVP versus merely desirable?
- Which state transitions must block merchant actions, and which can remain advisory?
- What is the fallback when a channel cannot confirm the final outcome of an outbound command?
- Which settlement artifacts are available per connector, and at what latency?

## Read Next

- [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md)
- [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
- [12-error-detection-strategy.md](./12-error-detection-strategy.md)
