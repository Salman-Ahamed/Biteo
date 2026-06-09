# 06. Business Model and Go-To-Market

## Purpose

Use this file to define a practical early commercial model, the best first merchant profile, and a low-cost growth strategy that fits an operator-first FastBite launch.

## One-Page Summary

- The best early customers are independent and small-chain UK QSR operators with repeated local demand, visible order-management pain, and an owner or manager who can adopt a new workflow quickly.
- Early revenue should come first from software subscription revenue and only second from delivery orchestration, because last-mile margins are fragile until zone density is proven.
- Growth should focus on winning merchant operating share in one dense micro-zone and converting existing demand into repeat direct orders, not on broad paid consumer acquisition.

## Best Early Customer Profile

- independent and small-chain UK QSR brands with one to five locations
- roughly 40 to 200 daily orders across dine-in, pickup, and delivery channels
- clear breakfast or lunch peaks and strong repeat local demand
- existing marketplace usage or multi-channel order flow that creates tablet, menu, or fulfilment friction
- owner-led or tightly managed operations that can make a buying decision quickly
- dense catchment with short delivery radii if FastBite is expected to coordinate fulfilment

## Best Early Merchant Categories

- sandwich shops
- bakeries and coffee-led QSR
- lunch-led fast casual brands
- wraps, bowls, salad, and light hot-food formats
- hospital, campus, and business-park food operators with predictable pre-order demand

## Commercial Model

| Revenue Stream                       | Recommended Early Structure                                                                                                              | Why It Works                                                                                                 | Commercial Caveat                                                                                                      |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| software subscription                | pilot launch price around 79 to 149 GBP per store per month, with a path toward 149 to 249 GBP once reliability and retention are proven | creates recurring revenue tied to visible operational value such as aggregation, KDS, reporting, and support | a new product will struggle to justify a premium fee before integrations, onboarding, and support quality are proven   |
| onboarding and setup                 | optional one-time setup fee, often waived for the first cohort or charged only when menu and device setup is heavy                       | helps recover real implementation effort and discourages low-intent pilots                                   | onboarding is a real cost center, so waiving it should be a deliberate acquisition decision rather than an assumption  |
| delivery orchestration fee           | pass-through courier cost plus a coordination fee only when FastBite controls dispatch                                                   | aligns revenue with the work of routing, issue handling, and courier management                              | do not assume this is high-margin early; it becomes attractive only when route density and operational control improve |
| customer delivery fee                | transparent distance-aware and time-aware fee                                                                                            | helps cover courier cost volatility without hiding economics from the customer                               | customer fees alone will not rescue weak fulfilment economics                                                          |
| KDS or tablet rental                 | optional monthly add-on where hardware simplifies launch                                                                                 | useful accessory revenue and can reduce merchant setup friction                                              | should support adoption, not become the main revenue thesis                                                            |
| enterprise or custom integration fee | later-stage custom quote                                                                                                                 | fits chains after proof of value and repeatable implementation                                               | not suitable as an early core revenue assumption                                                                       |

## Pricing Logic

The merchant fee range in the original draft is directionally plausible for a more integrated product, but it is too certain for a first launch. Public restaurant software pricing spans from very low-cost or freemium tools to several hundred pounds or dollars per month for direct-ordering and integration-led products. The practical implication for FastBite is:

- lead with a lower pilot subscription that is easy for an independent operator to say yes to
- earn the higher end of the range only after operational reliability, support quality, and repeat usage are visible
- keep pricing simple enough that merchants can compare it against avoided admin time, fewer order errors, and reduced third-party fee leakage
- avoid making delivery-margin claims before the first zone proves route density and supportable service levels

## What To Avoid Early

- driver subscription as a core revenue model
- a blanket low-commission promise without route density and fulfilment cost control
- treating delivery orchestration as a reliable profit pool before dispatch operations are stable
- assuming direct-order migration will happen quickly without merchant-led promotion and repeat-order tooling
- building AI-led growth modules before ordering, fulfilment, onboarding, and support work consistently

## Go-To-Market Principle

FastBite should win merchant operating share inside one dense zone before trying to win broad consumer mindshare. The initial motion is merchant-led distribution plus repeat-order retention, not consumer-brand advertising.

## Low-Cost Growth Strategy

### Phase 0: Choose One Dense Zone

Choose one office district, hospital cluster, university district, or business-park corridor where merchants share similar order peaks and short fulfilment routes. Zone choice should optimize for repeated local demand, not for city-wide coverage.

### Phase 1: Sign 5 to 8 Anchor Merchants

Best targets are merchants with repeat breakfast or lunch traffic, existing marketplace activity, and visible frustration with multi-tablet operations.

The early offer should include:

- white-glove menu and device setup
- staff training and launch-day support
- a short pilot commitment rather than a long contract
- a simple merchant ROI story based on operational clarity and retained margin, not speculative future marketing gains

### Phase 2: Use Merchant Distribution Instead of Paid Consumer Ads

FastBite should first convert demand that already exists around each merchant.

Most practical low-cost channels are:

- QR stickers and counter signage
- packaging inserts inside existing pickup and marketplace orders
- receipt messaging
- staff prompts to repeat buyers
- office or team ordering links for nearby workplaces
- first direct-order incentives for second purchase behaviour

These tactics are best treated as conversion tools for known customers, not as proof of scalable top-of-funnel demand.

### Phase 3: Build Retention Before Chasing New Demand

Direct-order growth should be treated as a retention program, not as an immediate switch away from marketplaces.

Most practical retention tools are:

- one-tap reorder links
- scheduled breakfast and lunch ordering
- office and group ordering workflows
- opt-in email or SMS reminders
- loyalty credits or repeat-order rewards
- quiet-period offers that improve demand shaping without training customers to wait for discounts

Marketplaces should remain a customer acquisition and discovery channel while FastBite helps merchants capture reorders directly over time.

### Phase 4: Expand Only After Density Is Proven

Do not expand until the first zone shows:

- repeat weekly order volume across several merchants
- stable fulfilment performance and issue resolution
- merchants renewing after pilot rather than churning after onboarding
- rising direct-order usage from existing customers
- support burden per merchant becoming more predictable
- evidence that contribution margin is improving rather than being carried by founder effort

## Onboarding, Support, and Merchant Retention

The original draft understated implementation and support work. For an early FastBite launch, these are part of the product, not overhead to ignore.

Every merchant rollout is likely to require:

- menu setup and QA
- device or KDS installation
- service area and fulfilment rule configuration
- staff training for front-of-house and kitchen workflows
- launch-week monitoring and issue handling
- fast support through phone, chat, or messaging during peak service windows

Merchant retention will depend less on feature breadth and more on whether FastBite reliably saves time, reduces failed orders, and gives operators confidence during busy periods.

## Economic Logic

The business becomes healthier when these conditions hold together:

1. short routes and concentrated demand keep fulfilment coordination manageable
2. order aggregation and clear workflows reduce operational errors and support load
3. repeat direct ordering gradually improves merchant margin and account retention

## Pilot Questions To Validate

- Which merchant archetype has the lowest onboarding burden and the highest renewal intent?
- What software price feels justified after the first month of live use?
- Which merchant-led conversion tactic produces the most repeat direct orders?
- How much support load does each additional merchant create during the first weeks after launch?
- At what zone density do delivery coordination economics stop being fragile?

## Read Next

- [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)
- [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)
