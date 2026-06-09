# FastBite System Documentation Pack

## Purpose

This pack replaces one long note with a decision-oriented set of internal system documents.

It is designed to be easy to scan by:

- a founder who wants the business case quickly
- a product person who wants workflow clarity
- an engineer who wants system boundaries
- an LLM that needs smaller, cleaner context windows

If the immediate goal is to get oriented quickly, begin with [01-executive-summary.md](./01-executive-summary.md).

For a client-shareable concept summary, use [High Level Overview of UK Food Delivery System (Pilot MVP).md](<../client/High%20Level%20Overview%20of%20UK%20Food%20Delivery%20System%20(Pilot%20MVP).md>).

## Document Pattern

Each file follows the same structure:

1. purpose
2. one-page summary
3. detailed decisions
4. open questions
5. read next

This keeps every document usable on its own while still fitting into a larger study sequence.

## Recommended Reading Order

1. [01-executive-summary.md](./01-executive-summary.md)
2. [02-idea-and-thesis.md](./02-idea-and-thesis.md)
3. [03-market-and-segmentation.md](./03-market-and-segmentation.md)
4. [04-product-and-operations.md](./04-product-and-operations.md)
5. [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
6. [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md)
7. [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
8. [08-compliance-and-risk.md](./08-compliance-and-risk.md)
9. [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)
10. [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)
11. [11-market-validation-report.md](./11-market-validation-report.md)
12. [11a-executive-summary-validation.md](./11a-executive-summary-validation.md)
13. [12-error-detection-strategy.md](./12-error-detection-strategy.md)
14. [13-platform-architecture.md](./13-platform-architecture.md)
15. [14-application-stack-and-deployment.md](./14-application-stack-and-deployment.md)
16. [15-mvp-feature-list-and-market-entry.md](./15-mvp-feature-list-and-market-entry.md)

## MVP Start Path

1. [01-executive-summary.md](./01-executive-summary.md)
2. [04-product-and-operations.md](./04-product-and-operations.md)
3. [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
4. [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)
5. [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
6. [13-platform-architecture.md](./13-platform-architecture.md)
7. [14-application-stack-and-deployment.md](./14-application-stack-and-deployment.md)
8. [15-mvp-feature-list-and-market-entry.md](./15-mvp-feature-list-and-market-entry.md)
9. [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)

## Reading Paths By Goal

### 5-minute business scan

1. [01-executive-summary.md](./01-executive-summary.md)
2. [02-idea-and-thesis.md](./02-idea-and-thesis.md)
3. [03-market-and-segmentation.md](./03-market-and-segmentation.md)
4. [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md)

### Product and operations study

1. [01-executive-summary.md](./01-executive-summary.md)
2. [04-product-and-operations.md](./04-product-and-operations.md)
3. [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
4. [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)
5. [14-application-stack-and-deployment.md](./14-application-stack-and-deployment.md)
6. [15-mvp-feature-list-and-market-entry.md](./15-mvp-feature-list-and-market-entry.md)

### System design study

1. [01-executive-summary.md](./01-executive-summary.md)
2. [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)
3. [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)
4. [08-compliance-and-risk.md](./08-compliance-and-risk.md)
5. [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)

## Document Map

| File                                                                                         | Primary Question                                                  | Main Output                                           |
| -------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- | ----------------------------------------------------- |
| [01-executive-summary.md](./01-executive-summary.md)                                         | Is FastBite worth pursuing?                                       | top-line answer and win conditions                    |
| [02-idea-and-thesis.md](./02-idea-and-thesis.md)                                             | What problem are we solving and how?                              | positioning, problem, solution thesis                 |
| [03-market-and-segmentation.md](./03-market-and-segmentation.md)                             | Where does this work in the UK?                                   | launch zones, demand logic, pain analysis             |
| [04-product-and-operations.md](./04-product-and-operations.md)                               | How should the day-to-day workflow operate?                       | customer, merchant, rider, and exception flows        |
| [05-integrations-and-data-model.md](./05-integrations-and-data-model.md)                     | How do all channels flow into one system?                         | integration strategy, canonical model, adapter design |
| [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md)             | How does the business make money and grow cheaply?                | ICP, pricing, distribution, retention                 |
| [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md)     | What architecture supports scale and resilience?                  | services, SLOs, degraded mode, performance targets    |
| [08-compliance-and-risk.md](./08-compliance-and-risk.md)                                     | What could block or break the business?                           | compliance checklist and risk controls                |
| [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)                                       | What should happen in what order?                                 | phased plan, cost ranges, phase gates                 |
| [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md) | What still needs to be decided?                                   | research backlog and next design deliverables         |
| [11-market-validation-report.md](./11-market-validation-report.md)                           | How much of the FastBite thesis is externally supported?          | evidence check, claim validation, decision framing    |
| [11a-executive-summary-validation.md](./11a-executive-summary-validation.md)                 | What should leadership conclude from the validation work?         | board-level recommendation and pilot framing          |
| [12-error-detection-strategy.md](./12-error-detection-strategy.md)                           | How should failures be detected and surfaced across the platform? | error taxonomy, escalation logic, operator visibility |
| [13-platform-architecture.md](./13-platform-architecture.md)                                 | What production reference architecture supports the platform?     | platform blueprint, resilience model, deployment view |
| [14-application-stack-and-deployment.md](./14-application-stack-and-deployment.md)           | Which application stack should be used and how should it deploy?  | framework choice, process boundaries, deployment path |
| [15-mvp-feature-list-and-market-entry.md](./15-mvp-feature-list-and-market-entry.md)         | What should the food-first MVP include and how should it enter?   | feature scope, market wedge, expansion path           |

## Validation Prompt Pack

The [../prompts](../prompts) folder contains a parallel review pack for the numbered documents.

- `shared-validation-instructions.md` defines the common evidence, sourcing, and output rules
- `01` through `15` each have a matching `*-validation-prompt.md` file for document-specific review and rewrite work
- `11a-executive-summary-validation-prompt.md` extends the validation flow with a leadership-focused summary prompt

Use the document in `docs/system/` together with its matching prompt in `prompts/` when you want structured external validation or a grounded rewrite.

## Source Note

This documentation pack is now the primary internal working source for study, structured editing, client-document generation, and future expansion.
