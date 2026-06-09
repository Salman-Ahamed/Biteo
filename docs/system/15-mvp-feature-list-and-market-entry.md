# 15. MVP Feature List and Market Entry Plan

## Role Perspective

Principal Product and Go-To-Market Strategist view:

FastBite's most credible pilot is not a smaller Uber Eats or Deliveroo. It is a focused merchant operating product for food merchants that already have digital demand and need a better way to handle it, recover repeat orders directly, and stay stable during peak periods.

## What This Document Is Trying To Do

This memo should answer one question clearly:

**what is the smallest commercially credible and operationally supportable FastBite launch for one dense micro-zone, and what must be deferred.**

## Key Findings And Issues

### What is validated

- The food-first merchant-operating-platform position is sharper than a broad consumer marketplace launch.
- WhatsApp-led entry plus hosted checkout is a credible low-friction entry thesis.
- The strongest MVP core is the merchant console: queue, prep controls, stock controls, pause controls, manual order capture, status updates, exception handling, and basic proof-of-value analytics.
- Direct ordering is credible as a repeat-order capture path, not as a first-order discovery engine.
- Simple dispatch with manual fallback is realistic in one dense zone.

### What is weak or too ambitious

- Voice is still too ambitious if treated as a launch-critical pillar rather than a controlled experiment.
- Full cross-channel queue unification, especially with marketplace integrations, is heavier than the original document acknowledged.
- Expansion-path sections for grocery, medicine, and skilled services dilute the MVP decision and make the document feel like a wishlist.
- The original draft understated the support burden needed for merchant onboarding, shift monitoring, and exception recovery.

## Claims That Need Correction, Support, Or Softer Wording

- Do not imply FastBite can win broad consumer discovery in the pilot. The better claim is that it improves merchant operations and captures some repeat demand directly.
- Do not imply direct ordering will quickly replace marketplaces. It is more credible as a repeat-order layer attached to merchants' existing demand.
- Do not imply voice ordering is a required MVP differentiator. The evidence is stronger for a staged pilot than for day-one dependence.
- Do not imply deep marketplace parity, write-back, or broad connector reliability unless those integrations already exist and are proven.
- Keep UK WhatsApp adoption references soft. The directional case is strong, but the primary Ofcom report was not directly accessible in this environment.

## Missing Points That Should Be Added

- Merchant selection criteria should be stricter: repeat-heavy demand, compact menus, visible tablet or phone-order pain, and willingness to promote direct ordering.
- Merchant behaviour change should be explicit: QR placement, packaging inserts, cashier prompts, and social links are part of the GTM motion, not optional extras.
- Checkout UX requirements should be stated more clearly: guest checkout, low-friction reorder, clear ETA, useful validation errors, and explicit phone-number rationale.
- Messaging-channel dependencies should be named: policy constraints, approved messaging patterns, and opt-in mechanics matter operationally.
- Pilot support intensity should be stated up front: onboarding, training, launch-week monitoring, manual fallbacks, and weekly merchant reviews.
- Post-pilot proof points should be defined before launch: merchant usage during peaks, repeat direct orders, stable support load, manageable exceptions, and renewal willingness.

## Revised Version Or Rewrite Suggestion

## Purpose

Define the smallest product FastBite should launch to win a real pilot with a small set of food merchants in one dense micro-zone.

This is a pilot decision memo, not a broad platform ambition document.

## Decision

FastBite should launch as:

**a food-first merchant operating layer for direct and assisted ordering, starting with WhatsApp-led entry, hosted checkout, and one merchant control console.**

FastBite should **not** launch as:

- a broad consumer marketplace
- a super app
- a chat-only ordering bot
- a voice-first autonomous ordering product

## Why This Wedge Is Credible

- UK food delivery is meaningful but incumbent-heavy, so broad discovery is a poor first wedge.
- Merchants still face fragmented order operations, tablet overload, menu inconsistency, and weak direct-repeat capture.
- A smaller entrant can credibly win by improving operational control and recovery, not by claiming marketplace-scale demand.

The commercial claim should stay modest:

FastBite is not replacing aggregator demand in the pilot. It is helping merchants handle demand better and capture a higher share of repeat orders through a lower-friction direct path.

## MVP Launch Scope

The launch-critical MVP should include six product blocks.

### 1. WhatsApp Entry And Hosted Checkout

Launch capability:

- click-to-WhatsApp entry from QR, packaging, receipts, social profiles, and direct links
- in-chat browsing or guided ordering for menus that fit WhatsApp interaction well
- structured path from WhatsApp into hosted mobile web checkout for payment and any higher-friction checkout steps

Scope rules:

- WhatsApp is the preferred entry, browsing, guided-ordering, and update layer
- hosted web is the payment and fallback transaction layer for the UK pilot
- checkout must support guest completion and simple reorder

### 2. Merchant-Branded Direct Reorder Flow

Launch capability:

- lightweight merchant-branded order page
- reusable direct links for online and offline channels
- repeat-order shortcuts for known customers where technically appropriate

Scope rules:

- design for repeat orders first
- do not assume meaningful first-order demand without merchant promotion

### 3. Merchant Operations Console

Launch capability:

- one live queue for FastBite-native direct orders and manual orders
- accept or reject order
- prep-time setting and updates
- ready state
- pause intake and throttling
- sold-out and item-snooze controls
- issue or escalation trigger

Scope rules:

- this is the real core product
- marketplace aggregation is optional only if a low-risk integration already exists

### 4. Manual And Assisted Order Capture

Launch capability:

- manual order entry for phone, walk-in, or staff-assisted demand
- clear source and payment-state tagging
- same operational state model as digital orders

### 5. Basic Dispatch, Status, And Exception Handling

Launch capability:

- delivery zone or radius rules
- simple dispatch assignment or partner-fleet handoff
- proof of pickup and proof of delivery
- customer confirmation, delay, and status updates
- exception queue for stock issues, delivery failure, payment uncertainty, and no-rider cases
- explicit manual fallback when automation breaks

Scope rules:

- no native rider app requirement
- no route optimization promise
- no aggressive batching logic in MVP

### 6. Baseline Proof-Of-Value Analytics

Launch capability:

- order volume by source
- direct versus non-direct mix inside FastBite-managed flows
- delayed, cancelled, and failed order counts
- prep-time adherence and issue counts
- simple merchant-facing pilot summary

Scope rules:

- enough to support renewal conversations
- not a full analytics suite

## What To Remove, Defer, Or Resequence

Remove from launch-critical scope:

- voice-assisted ordering as a required MVP pillar
- broad marketplace queue unification unless existing integrations are already reliable
- any implied city-wide consumer marketplace launch

Defer to post-pilot:

- office or group ordering
- scheduled ordering
- loyalty and campaign automation beyond simple reorder prompts
- native customer app
- native rider app
- advanced dispatch automation
- deeper marketplace write-back and connector parity
- advanced analytics and benchmarking

Resequence:

1. Launch direct ordering, merchant console, manual order capture, simple dispatch, and exception handling.
2. Prove repeat direct-order behaviour and stable merchant usage.
3. Test voice in a narrow subset of merchants with compact menus or high phone-order volume.
4. Add broader integrations only after operational proof exists.

## Market Entry Plan

### Pilot geography

- one dense micro-zone
- short delivery distances
- enough merchant proximity for high-touch support
- lunch and dinner demand concentration

### Merchant target profile

Prioritize:

- 5 to 8 independent or small-chain QSR merchants
- categories with repeat behaviour and manageable menus
- merchants already feeling tablet or phone-order pain
- merchants willing to promote QR and reorder flows

Avoid in first wave:

- highly bespoke menus with heavy modification complexity
- merchants with weak operational discipline
- merchants expecting FastBite to generate broad marketplace demand immediately

### Go-to-market message

Lead with three pilot outcomes:

1. fewer missed and mishandled orders during peak periods
2. a practical direct reorder path for repeat customers
3. one clearer operating surface for the merchant team

Do not lead with:

- guaranteed lower delivery costs
- rapid migration away from marketplaces
- AI staff replacement
- perfect end-to-end automation

### Merchant adoption playbook

FastBite should require merchant participation in distribution of the direct channel:

- QR on packaging and counters
- receipt or bag inserts
- social profile links
- staff prompts for repeat customers
- post-order reminder flows where permitted

If a merchant will not promote the direct channel, that merchant is a weaker pilot candidate.

## Controlled Post-Launch Experiment

### Voice-Assisted Ordering

Voice should be treated as a controlled experiment after launch stability, not as a required launch pillar.

Allowed early experiment:

- WhatsApp voice-note or phone-order capture for simple baskets
- draft order created for customer confirmation or operator review
- limited to merchants with compact menus and existing phone-order behaviour

Not allowed in pilot positioning:

- claims of broad autonomous conversational ordering
- claims that voice replaces staff operations
- claims that voice can safely handle all modifiers, substitutions, or edge cases

## Pilot Operating Model And Proof Points

FastBite should assume high-touch pilot support:

- initial menu and merchant setup
- training on peak-time controls
- launch-week shift monitoring
- manual exception handling
- delivery issue escalation
- weekly merchant review of operational outcomes

Before expansion, FastBite should be able to show:

1. merchants actively use the console during busy periods
2. repeat direct orders arrive through FastBite links and flows
3. exception handling remains manageable for the support team
4. dispatch failures are visible and recoverable without breaking trust
5. merchants see enough value to continue beyond the high-touch pilot phase

## Open Questions

- Which two or three merchant categories in the target micro-zone have the highest repeat-order potential and the lowest menu complexity?
- What merchant behaviours will FastBite require to promote the direct channel during the pilot?
- Will dispatch be handled through a partner fleet, merchant-managed riders, or a mixed model in the first zone?
- What minimum pilot evidence will count as commercial success for renewal and expansion decisions?
- When should voice move from experiment to roadmap commitment, if at all?

## Sources Consulted Or Research Gaps

Sources consulted:

- WhatsApp Business Platform. Primary source. Relevant for business messaging, notifications, CTAs, and commerce-oriented flows. Accessed May 2026.
- Baymard Institute, Checkout UX 2025: 10 Pitfalls and Best Practices. Secondary research. Relevant for guest checkout, form friction, fulfilment choice, and error recovery. Updated November 2025.
- Baymard Institute, Food Delivery & Takeout App & Website Ecommerce UX Research. Secondary research. Relevant for food-ordering-specific browse, customize, reorder, and fulfilment UX complexity. Accessed May 2026.
- Lumina Intelligence, UK Food Delivery Market: Growth, Share, & Size Statistics (2025). Secondary market analysis. Relevant for UK market structure and incumbent concentration. Accessed May 2026.
- Deliveroo investor results archive. Primary company source. Relevant for confirming the scale and maturity of incumbent operators. Accessed May 2026.
- Orders.co, 6 Simple Ways To Manage Orders From Multiple Delivery Apps With Ease. Practitioner or vendor commentary. Useful qualitative input on tablet overload, menu inconsistency, and centralized operations. April 2025.
- Otter, Complete guide to voice ordering for restaurants. Practitioner or vendor commentary. Useful for staged voice adoption and multichannel operational framing. October 2025.
- Restaurant HQ, Complete Guide to Voice Ordering for Restaurants. Secondary or practitioner commentary. Useful for voice-ordering benefits, costs, and discoverability limits. Updated September 2024.
- DataReportal, Digital 2025: The United Kingdom. Secondary digital market analysis. Relevant for mobile-first and socially mediated behaviour in the UK. February 2025.
- Love Ballymena summary of Ofcom Online Nations 2025. Secondary summary. Used only as directional support for WhatsApp reach, not as sole proof for a hard numeric claim. December 2025.

Research gaps:

- Direct access to Ofcom's underlying 2025 report was blocked in this environment, so UK WhatsApp reach should be treated as directionally supported rather than as a hard primary-source statistic here.
- I did not find a strong independent source quantifying direct-order conversion for UK independent restaurants specifically, so the memo should avoid hard uplift assumptions.
- I did not find strong sourceable evidence that voice ordering should be a first-wave requirement for independent merchants, which reinforces treating it as an experiment rather than a launch pillar.

## Read Next

- [04-product-and-operations.md](./04-product-and-operations.md)
- [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md)
- [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)
