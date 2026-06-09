# 08. Compliance and Risk

## Purpose

Use this file as a UK launch control memo for FastBite. It separates hard pilot-stage blockers from controls that can mature after launch, and it makes ownership explicit for the areas most likely to create regulatory, operational, or trust failure.

## Launch Posture

- Reduce scope before pilot rather than carrying ambiguous legal or partner assumptions into live operations.
- Use hosted payments, explicit customer terms, and manual operational fallbacks to keep regulated exposure low.
- Treat food information accuracy, data protection role mapping, and the rider operating model as launch decisions, not later clean-up work.

## Launch Blockers Before Pilot

| Control Area                             | Why It Is A Blocker                                                                                                                                                                                                                                                                                                    | Minimum Pilot Control                                                                                                                                                                                            | Primary Owner         |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| food business status and registration    | If FastBite sells, distributes, brokers, or otherwise operates as a food business, UK guidance indicates registration with the local authority is required, including for online and distance selling models. In England, Wales, and Northern Ireland, registration must be completed at least 28 days before trading. | Confirm whether FastBite itself, not just merchants, falls inside food business registration scope. Register each relevant site before launch where required.                                                    | founder + legal + ops |
| allergen information in digital ordering | FSA guidance requires allergen information for takeaway and delivery orders before purchase and again when food is delivered. Missing or unclear allergen data is a direct customer safety and trust risk.                                                                                                             | Merchant provides source allergen data. FastBite blocks menu publication without allergen fields, shows allergen info before checkout, and repeats it at delivery or on packing materials.                       | merchant ops          |
| data protection role mapping             | The current document overstates this as "Data Processing Agreements with merchants". ICO guidance requires the parties to determine whether each relationship is controller-processor, controller-controller, or joint control. Processor contracts are mandatory only where a processor relationship actually exists. | Map roles across merchants, FastBite, payments providers, messaging providers, and courier partners. Publish a privacy notice, set retention rules, and execute controller-processor contracts where applicable. | legal / privacy       |
| payment scope                            | Hosted payment flows reduce PCI exposure but do not automatically eliminate compliance responsibility.                                                                                                                                                                                                                 | Use hosted or redirect payment flows, avoid storing card numbers or CVC, and document the responsibility split with the PSP.                                                                                     | engineering + finance |
| rider operating model                    | Employment status changes the legal baseline for onboarding, pay, insurance, and operations. Right-to-work checks are mandatory before employing staff. Employers' Liability insurance is mandatory once FastBite is an employer.                                                                                      | Decide whether riders are employees, workers, or independent contractors before launch. Implement right-to-work checks for hires and get model-specific insurance advice before rider onboarding starts.         | ops + legal           |
| customer-facing order terms              | GOV.UK distance-selling guidance requires key information before the order is placed, including business identity, contact details, price, payment method, delivery arrangements, and complaint path.                                                                                                                  | Show trader identity, contact details, total price including delivery fees and taxes, delivery terms, refund path, and order confirmation records before pilot.                                                  | product + legal       |

## Required For Pilot But Can Mature During Pilot

- VAT-aware invoicing and settlement reporting should be in place from the start, but the exact design depends on whether FastBite is acting as agent, software provider, or merchant of record. The current wording is directionally right but needs finance and tax review before being treated as settled.
- Refund and dispute handling must exist at launch, but the policy can begin as a simple order-source decision tree if ownership is explicit and customer support can execute it consistently.
- Audit logs for operational actions should exist for refunds, order edits, status overrides, and merchant menu changes before pilot. More detailed retention, reporting, and access controls can mature later.
- Marketplace reconciliation can begin with manual review of failed syncs, missing fields, and delayed status updates, then move to automated exception handling once live patterns are understood.
- If FastBite handles food preparation, packing, or storage directly, food safety management procedures such as SFBB-based operating records become launch-stage requirements, not scale-stage nice-to-haves.

## Scale-Stage Hardening

- Formal DPIAs for higher-risk profiling, automation, or sensitive operational analytics.
- More structured vendor governance, including sub-processor inventory, annual review, and contractual refresh.
- Automated finance reconciliation across payment providers, channels, and merchant statements.
- Expanded resilience playbooks for messaging outages, partner outages, and bulk incident communications.
- Any move into age-restricted goods, alcohol, or other licensed categories should be treated as a separate compliance workstream before rollout.

## WhatsApp And Messaging Constraints

- Meta states that a 24-hour customer service window opens when a user messages or calls the business. Outside that window, FastBite can only send pre-approved template messages.
- Meta also requires opt-in before messaging users. Template approval alone is not a substitute for lawful UK marketing practice.
- WhatsApp product browsing and structured order capture are plausible for pilot, but native payment support is region-dependent and should not be assumed for the UK launch plan.
- UK direct marketing rules still matter. If FastBite uses WhatsApp or SMS for promotional outreach, PECR and data protection rules need to be checked in addition to Meta platform policy.
- Meta measures message quality using user feedback signals such as blocks and reports. This creates a real platform dependency risk if messaging volume or content becomes too aggressive.
- Pilot control should separate transactional messaging from promotional messaging, monitor message cost and quality, and keep SMS and web fallback paths for critical updates.

## Marketplace Integration Reality

- The underlying risk is real: integration coverage varies by partner, geography, and system combination.
- Deliverect's UK integration catalogue shows channel and system support is selective rather than universal, which supports the current caution against assuming deep direct integrations from day one.
- "Partner approval" and "commercial agreements" are plausible and often likely, but they should be treated as channel-specific assumptions until confirmed for each target marketplace.
- Pilot planning should assume a hybrid adapter model with manual reconciliation and exception handling, not perfect real-time sync across every external order source.

## Highest-Risk Failure Modes

| Risk                                                  | Failure Mode                                                                    | Minimum Mitigation                                                                                                           | Owner                          |
| ----------------------------------------------------- | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| incorrect allergen or product data                    | customer harm, complaints, enforcement action, immediate trust loss             | merchant data ownership, required allergen fields, no-publish rule for incomplete menu items, delivery-stage allergen repeat | merchant ops                   |
| wrong legal model for merchant or rider relationships | contracts, insurance, tax, or onboarding controls do not match reality          | confirm legal model before launch and rewrite contracts and workflows accordingly                                            | founder + legal                |
| marketplace data mismatch                             | missing menu items, order exceptions, broken status updates, finance errors     | start with limited channel set, manual exception queue, adapter-level field mapping tests                                    | engineering + ops              |
| WhatsApp policy or delivery degradation               | update failures, higher costs, account quality issues, blocked marketing plans  | transactional-only default at pilot, opt-in evidence, template governance, SMS/web fallback                                  | product + growth + engineering |
| refund ownership ambiguity                            | support delays, duplicated credits, merchant disputes, customer dissatisfaction | define owner by order source and payment flow before pilot                                                                   | support + finance              |
| weak settlement controls                              | unreconciled payouts, VAT confusion, merchant mistrust                          | daily exception review, source-of-truth ledger, finance sign-off on settlement model                                         | finance                        |
| over-promised SLA                                     | credits, churn, and reputational damage during peak demand                      | zone-based SLA rules, transparent cutoffs, manual fallback for late orders                                                   | ops                            |

## Ownership And Policy Gaps To Close

The business should assign one accountable owner for each of the following before pilot:

- privacy notice, retention schedule, data incident handling, and subject-rights process
- merchant contract terms, including who owns menu accuracy, allergen accuracy, cancellations, and refunds
- rider onboarding standard, including right-to-work evidence and insurance checks where applicable
- checkout terms and customer communications, including when marketing consent is needed
- settlement reconciliation, VAT treatment, and credit-note or refund reporting
- operational audit trail for refunds, order edits, manual dispatch overrides, and merchant menu changes
- incident command for customer-facing failures, including messaging fallback and marketplace outages

## Items That Need Legal Or Specialist Confirmation

- whether FastBite itself must register as a food business in every operating scenario, or only when it directly conducts food distribution or fulfilment activity
- the correct contract structure with merchants in each flow: controller-processor, controller-controller, or joint control
- the exact VAT invoicing and settlement treatment for each commercial model, especially if FastBite ever becomes merchant of record
- the insurance package required for rider operations, especially if contractors use their own vehicles or if FastBite controls shifts tightly enough to affect employment status analysis
- the exact cancellation and refund rights wording for prepared food orders under FastBite's intended terms and operating model

## Decision Summary

- The original document is directionally correct that compliance risk is material, WhatsApp and marketplace dependence create platform risk, and hosted payments are the safer UK pilot default.
- It was not sufficiently clear about what must be solved before pilot versus what can mature later.
- It also missed one material launch blocker: food business registration and food-information duties may apply to FastBite itself depending on the operating model, not only to merchants.
- The highest-value correction is to replace generic checklists with explicit launch gates, legal-model confirmation, and named owners.

## Read Next

- [09-roadmap-and-budget.md](./09-roadmap-and-budget.md)
- [10-open-questions-and-next-design-inputs.md](./10-open-questions-and-next-design-inputs.md)
