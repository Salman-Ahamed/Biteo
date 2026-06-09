# 04. Product and Operations

## Purpose

Use this file to define how FastBite should work in day-to-day operations across customer, merchant, and rider flows.

## One-Page Summary

- For pilot, FastBite should use WhatsApp as the primary entry, browsing, guided-ordering, and update channel, with hosted web checkout used for payment and any higher-friction fallback steps.
- The minimum merchant workflow is accept, prepare, manage stock issues, mark ready, pause intake, and escalate exceptions.
- Dispatch should trigger from predicted ready time and active rider availability, not from order creation time alone.
- Every critical workflow needs a degraded-mode fallback because outages, stock mismatches, and missed accepts are normal in live delivery operations.

## Pilot Scope

The pilot should optimize for reliable execution, not full operational elegance.

The pilot should include:

- WhatsApp-led entry with in-chat browsing or guided ordering where practical, plus hosted mobile web checkout for payment completion
- one FastBite operations view for active FastBite orders
- manual fallback for any channel or connector that fails
- merchant controls for acceptance, prep timing, stock status, readiness, pause, and incident escalation
- simple rider assignment with proof of pickup and proof of delivery
- explicit exception rules for payment, stock, dispatch, and handoff failures

The pilot should not depend on:

- aggressive auto-batching
- perfect cross-channel unification if connectors are unstable
- native rider apps
- rich analytics as an operational dependency
- complex substitution logic unless it is supported end to end

## Customer Ordering Model

The recommended pilot experience is:

- discovery through QR, packaging inserts, posters, staff prompts, and merchant social posts
- WhatsApp as the entry point, browsing or guided-ordering surface, support channel, and update channel
- hosted mobile web checkout for payment, guest checkout, and any checkout branches that are more reliable outside chat
- WhatsApp for confirmations, delay notices, and delivery updates when available
- SMS fallback for critical transactional updates if WhatsApp delivery fails

### Pilot Customer Flow

1. customer enters through QR, link, or click-to-WhatsApp entry
2. customer browses the menu or follows a guided ordering path in WhatsApp where the menu shape and platform support allow it
3. customer is handed off to web checkout for payment and any higher-friction checkout steps that are safer outside chat
4. customer receives order confirmation and status updates in WhatsApp
5. customer is routed to support or issue resolution in WhatsApp when exceptions occur

## Why Not Pure WhatsApp Commerce

WhatsApp is practical as an acquisition, communication, browsing, and recovery layer. It is weaker as the only commerce layer when the menu has:

- many items
- multiple modifiers
- flexible checkout requirements
- fallback and recovery requirements

For pilot, the more reliable model is structured ordering in chat where it helps conversion, and transaction completion in web checkout where payment, fallback handling, and recovery are stronger. This keeps the customer inside WhatsApp for more of the journey without depending on chat-only flows for the hardest parts of checkout.

## Merchant Workflow

### MVP-Critical Merchant Actions

The pilot merchant operating flow should include:

1. menu management
2. item availability and out-of-stock control
3. order acceptance or rejection
4. prep-time estimate and updates
5. live preparation view with countdown and priority ordering
6. pause and throttle controls
7. order-ready trigger based on actual readiness
8. incident flags for delay, stock issue, and delivery problems
9. contact path to FastBite support when the workflow breaks

### Pilot Workflow Boundary

For pilot, one live queue is realistic only if FastBite directly controls the incoming orders or has stable ingestion from connected channels. The product should not pretend to provide a perfect single source of truth when a connector is delayed, down, or running in read-only mode.

In degraded mode, the merchant should still be able to:

- see which orders were received by FastBite
- identify whether the kitchen has acknowledged them
- mark stock problems and delays
- pause new intake
- switch to a manual fallback view when channel sync is unreliable

## Merchant Dashboard Requirements

### MVP-Critical

One operating screen should show:

- all live FastBite-managed orders and any connected orders with confirmed ingestion
- clear source label for every order
- acceptance state and prep countdown
- item availability warnings
- kitchen-ready controls
- rider status when FastBite manages delivery
- channel-specific issue flags
- pause and throttling controls
- support or escalation actions

### Nice to Have After Pilot

- cross-channel perfect unification across every connector
- advanced SLA scoring and prediction models
- deep sales and service metrics by source
- detailed staff productivity views
- multi-store comparative reporting

## Rider Workflow

The lowest-risk early rider model is:

- partner courier pools or scheduled peak-time riders
- a lightweight rider PWA or dispatch web app before native apps
- zone and time-block availability
- proof of pickup and proof of delivery

### MVP-Critical Rider Actions

1. accept assignment
2. navigate to merchant
3. mark arrived
4. confirm pickup
5. mark delivered or failed delivery attempt
6. contact customer or ops when handoff fails

### Nice to Have After Pilot

- in-app earnings reporting
- route stacking and advanced batching
- richer reliability scoring
- native mobile applications

### Dispatch Priority Order

1. predicted pickup readiness
2. distance to merchant
3. current active load
4. rider availability in the correct zone
5. rider reliability
6. vehicle suitability when the fleet is mixed

Dispatch should not assign a rider solely because the order exists. Early dispatch creates rider waiting time, merchant friction, and stale food. Aggressive batching should stay off by default in pilot unless service quality is clearly preserved.

## Dispatch Rules

The pilot dispatch model should follow these rules:

1. do not request a rider until the prep estimate is reliable enough to avoid avoidable waiting
2. allow merchants to add prep time when the kitchen is behind
3. prefer readiness accuracy over shaving a small number of minutes from dispatch timing
4. escalate to manual dispatch review when no rider can be matched within the target window
5. disable auto-batching by default and enable only in tightly controlled conditions

## Exception and Recovery Flows

The platform must handle:

- unpaid orders
- no available rider
- rider no-show
- item out of stock after payment
- customer unreachable at delivery
- weather surge and capacity shock
- marketplace connector failure
- messaging or payment provider outage

### Recovery Rules

#### Order Acceptance and Payment

- auto-cancel unpaid orders when the payment or reservation window expires
- if payment is authorized but order creation fails, route the order into manual review rather than silently dropping it
- if the merchant does not accept in time, cancel with an explicit reason and notify the customer immediately

#### Stock Problems

- if an item is unavailable before acceptance, allow the merchant to reject or request a supported substitution path
- if an item becomes unavailable after payment, require an explicit rule: approved substitution, partial refund, full refund, or customer confirmation
- do not rely on free-text staff improvisation for paid stock issues

#### Kitchen Delay and Dispatch

- do not dispatch too early when the kitchen is behind
- let the merchant add prep time without forcing support intervention
- if no rider is available within the dispatch threshold, notify the customer, hold dispatch, and surface the order for manual review

#### Delivery Failure

- define the contact sequence for unreachable customers: in-app message, phone call, wait window, then fail-delivery outcome
- define whether failed deliveries are returned, disposed of, or marked completed based on policy and merchant agreement
- capture proof for pickup disputes, dropoff disputes, and no-show claims

#### System and Provider Failure

- preserve carts and queued orders during provider issues when possible
- stop promising automated status changes if the messaging provider is degraded
- give merchants a manual fallback operations view
- if connector acknowledgments fail, stop auto-accept assumptions and surface orders as at-risk
- keep merchant acceptance, prep, pause, and exception actions available from FastBite-owned state even when external sync is degraded
- trigger operator exception handling and the relevant fallback runbook rather than waiting for customer complaints to reveal the issue
- pause only the unsafe automation lane, not the whole merchant workflow, unless the database or canonical write path is at risk
- use credits selectively rather than automatically, based on issue type and customer impact

## MVP-Critical vs Later-Phase Flows

### MVP-Critical

- WhatsApp entry plus web checkout
- order acceptance and rejection
- prep time capture and update
- sold-out and item snooze controls
- ready-for-pickup trigger
- simple rider dispatch and proof events
- pause intake and manual escalation
- explicit outage and exception handling

### Later-Phase

- automated substitutions at scale
- advanced rider scoring and route optimization
- auto-batching
- fully unified multi-channel queue with graceful sync across all partners
- richer analytics and forecast views
- native rider experience

## Operational Risks To Watch In Pilot

- merchants forgetting to accept or update prep times during peaks
- stock availability drifting from the live menu
- riders arriving before food is ready
- connector failures creating false confidence in the live queue
- messaging delivery failures causing silent customer confusion
- no-rider scenarios that are discovered too late, after food is already prepared
- unclear failed-delivery policy creating refund disputes and merchant frustration

## Operating Principles

1. predicted ready time matters more than naive dispatch speed
2. the pilot should prefer operational truth over artificial workflow elegance
3. the dashboard should expose degraded mode clearly rather than hide sync problems
4. exception handling is part of the product, not a support afterthought
5. every automation that can fail needs a human fallback path

## Open Questions

- What is the minimum merchant workflow required for pilot success?
- Which dashboard actions need one-click shortcuts during peak periods?
- Which exceptions can be safely automated without causing refund or fulfillment errors?
- What manual ops coverage is required during lunch and dinner peaks?
- At what failure point should the system automatically pause intake rather than continue accepting risk?

## Read Next

- [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
- [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
