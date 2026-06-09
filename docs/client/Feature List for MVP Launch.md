# Feature List for MVP Launch

This document defines the committed MVP feature scope for FastBite's pilot launch in one dense operating zone.

The MVP is focused on merchant operations, direct ordering, customer status updates, and basic dispatch support. Features requiring continuous rider GPS, live ETA prediction, or a dedicated rider app are excluded from the MVP scope.

## MVP Development Commitment

For the MVP launch, FastBite will build a standout but tightly scoped merchant-first operating product. The committed MVP is grouped below by the workflows that matter in a live pilot.

### Customer Ordering and Direct Reorder

- WhatsApp-led entry from QR codes, packaging, receipts, social links, and direct links, with in-chat menu browsing or guided ordering where practical before handoff to hosted mobile web checkout.
- Hosted checkout for payment, guest checkout, and any higher-friction checkout steps that are not reliable to complete inside WhatsApp for the UK pilot.
- Merchant-branded direct ordering and repeat-order flow for customers returning to the same merchant.
- One marketplace channel integration for MVP, starting with Uber Eats, so participating merchants can manage at least one external order source inside FastBite.

### Merchant Operations and Kitchen Workflow

- One live merchant order console for FastBite-managed direct orders, manual orders, and Uber Eats orders confirmed through the MVP connector.
- Order acceptance or rejection, prep-time setting, prep-time updates, ready-state control, delay handling, and cancellation with reason where needed.
- Manual order entry for phone and walk-in orders, with clear source and payment-state tagging, so merchants retain a reliable non-AI fallback when needed.
- Basic menu management and availability controls, including category or item updates, item availability, sold-out or item-snooze control, and pause or throttle controls when the kitchen is under pressure.
- Automatic order ticket printing or simple kitchen-display handoff for participating merchants, limited to one operational path per merchant.
- Incident and exception actions for stock issues, payment uncertainty, delayed prep, and delivery problems.

### AI Assisted Features

- AI-assisted natural-language ordering support, allowing customers to describe what they want through written text or voice input, with the system mapping intent into relevant menu options or a draft basket for confirmation.
- AI-assisted manual order entry for phone and walk-in orders, allowing staff to enter orders through written text or voice input, with the system extracting details, requesting any missing required information, and clearly tagging source and payment status before confirmation.

### Dispatch, Delivery, and Customer Updates

- Delivery zone or radius rules and simple dispatch assignment with manual fallback for exceptions.
- Proof of pickup and proof of delivery capture in the pilot workflow.
- Customer notifications when the order is confirmed, being prepared, picked up, delayed, and delivered, using one reliable outbound channel.
- Explicit exception handling for no available rider, rider no-show, failed handoff, and customer-unreachable delivery cases.

### Merchant Setup, Access, and Pilot Reporting

- Merchant setup for menu, operating hours, delivery areas or charges, and basic notification settings.
- Basic role-based access for merchant admin and staff users involved in order handling.
- Basic platform admin controls for restaurant onboarding, activation, and pilot support.
- MVP reporting for order volume, delays, cancellations, failed orders, prep-time adherence, and direct-order usage.

This MVP commitment is designed to stand out on three points that are commercially useful in pilot: better repeat-order capture, stronger merchant operating control during peak periods, and clearer exception recovery when live operations break.

## MVP Scope Boundaries

- Auto-printing should be configurable per merchant and should not include complex kitchen routing or multi-station setup in v1.
- Kitchen-display support should be framed as simple kitchen workflow support, not as a full kitchen orchestration product.
- WhatsApp should be treated as the preferred entry, browsing, guided-ordering, and update channel where platform support is reliable, but the MVP should still assume hosted web checkout for payment and any checkout steps that need stronger fallback handling.
- Customer notifications should use one reliable outbound channel, ideally WhatsApp where policy and opt-in allow, with SMS fallback if needed.
- The MVP should not depend on continuous rider GPS, live ETA prediction, aggressive route optimization, or native rider apps.
- The MVP marketplace scope should be limited to one launch connector, Uber Eats, with only the ingestion and operational controls that can be implemented reliably in pilot.
- The MVP should not promise full marketplace-grade queue unification or deep two-way connector parity across multiple channels.
- The MVP should not assume native WhatsApp payment support for the UK, and should be designed to hand off to web payment without breaking the customer journey.
- The MVP should not position fully autonomous AI voice ordering, autonomous dispatch, or marketing automation as launch-critical capabilities.

## Nice to Have / Post-MVP Features

The following items are explicitly outside the MVP commitment and should be treated as later-phase features after the pilot proves the core workflow. The strongest post-MVP differentiators are growth and retention features built on first-party customer capture, followed by deeper automation once operational trust is already proven.

### Growth, Retention, and Merchant Differentiation

1. Loyalty and repeat-order rewards, including simple points or credits.
2. Better discount and coupon tools beyond basic reorder prompts.
3. WhatsApp marketing tools to message customers in bulk, target customer groups, automatically bring customers back, and track results.
4. AI tools to create simple marketing content such as posters, captions, and branded visuals.
5. A better customer history and reorder experience, including saved baskets or merchant favourites where useful.

### Ordering and Channel Expansion

6. Scheduled orders, office or group orders, and more advanced delivery options.
7. Multi-language ordering and better guided ordering where merchants need it.
8. Wider support for voice notes and phone orders for simple baskets, with transcription, confirmation, and staff review.
9. Full AI voice ordering only after the simpler voice-input workflow proves reliable and useful.
10. Just Eat and Deliveroo as later marketplace integrations after Uber Eats, followed by deeper menu sync and stronger cross-channel order management.

### Delivery and Operations Expansion

11. Automatic arrival-soon messages shortly before the rider reaches the customer.
12. Live rider tracking with real-time ETA.
13. More advanced dispatch automation, route planning, batching, and rider performance scoring.
14. A dedicated rider app or ongoing rider GPS tracking.
15. More advanced analytics, benchmarking, and comparisons across multiple stores.

### SaaS Platform Expansion

16. Self-serve billing, plan controls, automated invoicing, and broader platform commercial settings.
17. More advanced staff management, audit visibility, and detailed user permissions.

## Recommended Launch Positioning

FastBite should position the MVP launch as a merchant-first ordering and operations launch that improves order handling, direct reorder capture, and customer status visibility.

It should not be positioned as:

- a full marketplace-equivalent delivery stack
- a live-map delivery platform from day one
- an AI-driven autonomous dispatch system
