# 09. Roadmap and Budget

## Purpose

Use this file to sequence execution and keep the project aligned with realistic cost and proof milestones.

## One-Page Summary

- Start with a tightly managed pilot in one dense micro-zone and treat setup, onboarding, and support as part of the work, not as invisible overhead.
- Expand scope only after live operational proof, merchant continuation, and support capacity are visible.
- Budget assumptions should distinguish between cash spend and unpaid founder labour, because a lean pilot can look cheap on paper while still being operationally expensive.

## Planning Assumptions

These assumptions shape the roadmap below:

- FastBite stays merchant-first and zone-first.
- The first release is web and operations-led, not native-app-led.
- Early pilots use founder involvement and manual operations where needed.
- Integrations are staged; the team does not try to connect every marketplace at once.
- Delivery orchestration is treated as operationally fragile until density and support load are proven.

## Phase 0: Pilot Design and Commitments

### Duration

2 to 4 weeks

### Scope

- secure a target cohort of 5 to 8 merchants
- plan a first live wave of 3 to 5 merchants
- one micro-zone
- define the pilot offer, pricing, support model, and participation expectations
- collect baseline data for each merchant such as order mix, prep flow, peak windows, and current operating pain
- prepare onboarding checklists, incident playbooks, and weekly review cadence

### Goal

Enter the live pilot with a signed cohort, clear success criteria, and realistic operational readiness.

## Phase 1: Concierge Pilot Live

### Duration

8 to 12 weeks from first merchant go-live

### Scope

- one dense micro-zone
- 3 to 5 merchants live in the first wave, then expand toward 5 to 8 only after stability is demonstrated
- manual operations support explicitly allowed
- one direct-order flow plus at least one marketplace ingestion path
- narrow fulfilment coverage windows rather than full-day operational complexity
- weekly merchant reviews and active incident logging

### Goal

Validate:

- real merchant pain from multiple channels
- value of the one-dashboard workflow in live service
- realistic onboarding effort per merchant
- prep timing, dispatch issues, and delay patterns
- support load per merchant and per peak window
- early continuation or renewal intent
- contribution margin by order source, with assumptions made explicit where data is incomplete

## Phase 2: Operational MVP

### Duration

3 to 6 months

### Scope

- 8 to 15 active merchants, not all launched at once
- unified dashboard
- KDS
- web checkout
- opt-in customer messaging and order updates
- 1 to 2 priority marketplace adapters rather than broad channel coverage
- courier-facing workflow or simple rider PWA only if FastBite is controlling dispatch
- live operations console
- documented onboarding and support runbooks

### Goal

Prove the platform handles peak-hour operations better than the merchant's current multi-tablet setup while reducing manual effort per merchant.

## Phase 3: Zone Replication

### Duration

4 to 9 months after Operational MVP gates are met

### Scope

- add one adjacent dense zone only after the first zone is stable
- standardize rollout, support, and issue-response playbooks
- deepen analytics, reconciliation, and merchant reporting
- expand direct-order retention mechanics carefully
- improve automation only where manual pain is already proven

### Goal

Build repeatable zone economics and a repeatable rollout process before considering multi-city growth.

## Budget Reality

| Scenario                                                                        | Realistic Range                  | Notes                                                                                                           |
| ------------------------------------------------------------------------------- | -------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| founder-led setup plus first live wave                                          | about 20,000 to 50,000 GBP cash  | only realistic if unpaid founder labour covers much of product, onboarding, and live support                    |
| lean 6-month pilot with limited integrations                                    | about 60,000 to 120,000 GBP cash | plausible only if founders still carry major product and operations load                                        |
| staffed operational MVP with dedicated engineering, implementation, and support | about 120,000 to 250,000+ GBP    | more realistic for a genuinely professional pilot with broader support coverage and live operational resilience |

The original 60,000 to 120,000 GBP range is directionally plausible for a lean execution model, but it is weak as a default assumption for a fully staffed restaurant-operations platform. UK salary benchmarks alone imply that paid engineering and delivery management capacity can consume a large share of that budget before heavy support, integrations, or service recovery costs are added.

## How To Keep Cost Low Without Breaking The Business

- use managed cloud infrastructure
- build web and PWA first, not native apps first
- use a hybrid integration model and limit custom integrations early
- stay in one micro-zone
- keep service windows narrow during the live pilot
- stage merchant onboarding in waves instead of launching everyone at once
- avoid heavy paid acquisition
- delay non-core AI modules until operations are proven

## Measurable Phase Gates

Move from one phase to the next only when the current phase meets measurable conditions.

### Phase 0 to Phase 1

- at least 5 merchants are contracted for the pilot cohort, or 3 are ready to go live with 2 more scheduled
- baseline metrics are captured for every pilot merchant
- pilot pricing, responsibilities, and feedback cadence are agreed in writing
- onboarding checklist, support path, and incident log are ready before first go-live

### Phase 1 to Phase 2

- first-wave merchants have been live long enough to assess real usage rather than launch-week behavior
- most live merchants are using FastBite during agreed service windows on a recurring basis
- operational KPIs such as on-time performance, failed orders, or issue rate meet pre-agreed thresholds for a sustained period
- support hours per merchant and per 100 orders are stable or improving
- a majority of eligible pilot merchants agree to continue on a paid or extended basis

### Phase 2 to Phase 3

- onboarding time and launch effort per merchant are predictable enough to document and repeat
- founder intervention is no longer required for every merchant launch or incident
- contribution margin is positive or clearly improving after including support and service-recovery costs
- the first zone shows enough repeat weekly order density that adding the next zone is unlikely to break service quality

## Why The Pilot Needs To Be Structured This Way

The original draft moved too quickly from a small pilot to a larger operational MVP.

What external rollout and pilot guidance suggests instead is:

- use a small first live wave for deep learning, but maintain a slightly larger total cohort so you can test onboarding repeatability and continuation risk
- allow enough live time to observe actual usage, retraining needs, and renewal intent rather than just launch excitement
- treat rollout success as a combination of product performance, team adoption, training quality, and support responsiveness
- make budget decisions based on the real people needed to launch and support the product, not just the cost of building software

## Open Questions

- What exact KPI thresholds should be agreed before the first merchant goes live?
- Which manual activities are acceptable in the live pilot but must be automated before zone replication?
- How many support hours per merchant per week are economically acceptable?
- Which integration path is truly required for pilot learning, and which ones can wait?
- What budget should be treated as cash outlay versus unpaid founder contribution?

## Read Next

- [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)
