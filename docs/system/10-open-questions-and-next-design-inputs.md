# 10. Open Questions and Next Design Inputs

## Purpose

Use this file as the active decision backlog of unresolved cross-document items and as the bridge into the next system-design phase.

## One-Page Summary

- The original monolith contained good answers, but it also mixed conclusions, assumptions, and unresolved items.
- This file should track decision-ready backlog items, not broad brainstorming topics.
- Several original questions remain valid, but some should be narrowed because the commercial and roadmap documents already constrain the direction of travel.
- The next design phase should prioritize the decisions that unblock multiple downstream artifacts: state, permissions, channel contracts, exception handling, and operational guardrails.

## Inputs Already Constrained By Current Evidence

These items should not remain open as broad questions in this file:

- FastBite stays merchant-first and zone-first.
- Early rollout is phased, high-touch, and onboarding-heavy.
- Early growth should rely on merchant-led distribution and repeat-order retention loops, not broad paid consumer acquisition.
- Expansion should be gated by measurable operational and commercial proof, not product completeness alone.

## Backlog Rules

Each item in this file should:

- name one decision, not a broad topic area
- state why the decision is still open
- show the main dependency or prerequisite
- identify the owner track responsible for driving the answer
- name the target output document or artifact

When a decision is large enough to affect interfaces, reliability, governance, or operating policy, it should graduate into a decision record or primary design document rather than staying here indefinitely.

## Active Decision Backlog

### Priority 0: Resolve Before Detailed Solution Design

| Decision                                                                                              | Why It Is Still Open                                                                                                                                                                                                          | Main Dependency                                                    | Owner Track               | Target Output                            |
| ----------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | ------------------------- | ---------------------------------------- |
| Define the pilot metrics pack for zone viability, contribution margin, support load, and continuation | [06-business-model-and-go-to-market.md](./06-business-model-and-go-to-market.md) and [09-roadmap-and-budget.md](./09-roadmap-and-budget.md) require measurable gates, but the exact metric definitions are not yet documented | current pilot and finance assumptions                              | PMO and Commercial        | pilot metrics and phase-gate definitions |
| Define the canonical order state machine                                                              | this is the core dependency for adapters, refunds, exceptions, events, and observability                                                                                                                                      | none                                                               | Architecture and Product  | canonical order state machine            |
| Define roles and permissions for merchant, rider, operator, and customer users                        | support, refund, audit, and incident workflows need actor boundaries before process detail                                                                                                                                    | none                                                               | Product and Architecture  | roles and permissions matrix             |
| Define refund ownership and decision authority by order source                                        | this remains legally and operationally sensitive and cannot be inferred safely from current material                                                                                                                          | roles and permissions, order states, channel ownership assumptions | Operations and Compliance | refund ownership matrix                  |

### Priority 1: Resolve Once Core State And Roles Exist

| Decision                                                                                       | Why It Is Still Open                                                                          | Main Dependency                           | Owner Track                   | Target Output                                    |
| ---------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- | ----------------------------------------- | ----------------------------- | ------------------------------------------------ |
| Define channel acknowledgement and sync rules for each inbound and outbound source             | the question is valid but too broad without a settled state model                             | canonical order state machine             | Architecture and Integrations | channel adapter contracts                        |
| Define menu and availability synchronization rules, including throttle and auto-pause behavior | the current questions overlap product and reliability concerns and need one combined contract | roles, adapters, merchant operating rules | Product and Integrations      | menu and availability sync specification         |
| Define out-of-stock and substitution policy after payment                                      | this affects customer promises, refunds, audit, and merchant workflow                         | order states, refund ownership            | Product and Operations        | exception and substitution policy                |
| Define the support and dispute workflow for merchant, customer, and operator paths             | the current wording is valid but should be framed as ownership, escalation, and SLA design    | roles, refund ownership, order states     | Operations and Product        | support and dispute operations design            |
| Define the event model for order, prep, dispatch, payment, and settlement                      | event boundaries should follow the state model and exception policy rather than precede them  | order states, core workflows              | Architecture                  | domain event model and service boundary document |

### Priority 2: Resolve Before Pilot Hardening And Zone Replication

| Decision                                                                                    | Why It Is Still Open                                                                                 | Main Dependency                                | Owner Track                  | Target Output                              |
| ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ---------------------------------------------- | ---------------------------- | ------------------------------------------ |
| Define SLOs, SLIs, and failure budgets for each critical service                            | reliability objectives need named services and critical flows first                                  | event model, service boundaries                | Reliability and Architecture | reliability objectives document            |
| Define degraded-mode behavior for each external dependency                                  | this cannot be finalized until adapters and critical workflows exist                                 | adapters, SLOs, core workflows                 | Reliability and Operations   | degraded-mode playbook                     |
| Define UK reporting needs for VAT, settlement, and merchant billing                         | this is valid, but it should become a concrete reporting matrix rather than stay as a broad question | refund ownership, payment and settlement flows | Finance and Compliance       | finance and reporting requirements matrix  |
| Define rider compliance requirements by phase, including right-to-work and insurance checks | this is phase-sensitive and should resolve into a checklist, not a lingering topic                   | operating model by phase                       | Operations and Compliance    | rider compliance checklist                 |
| Define audit, observability, and incident response coverage                                 | this should follow the event model, actor model, and reliability choices                             | event model, roles, SLOs, degraded modes       | Reliability and Operations   | observability and incident response design |

## Questions To Narrow Or Move Out Of This File

- Which merchant mix produces the best pilot economics? This remains useful, but it is a commercial experiment question rather than a system-design blocker. Keep it in the commercial or pilot-learning backlog unless it changes architecture scope.
- What customer acquisition channels work best without paid ads? Current evidence already narrows this to merchant-led distribution and repeat-order retention tactics. The remaining open item is which tactic performs best in the pilot, which belongs in the commercial experimentation backlog.
- What is the exact density threshold for a viable zone? Keep this open, but narrow it to a measurable threshold definition tied to pilot metrics and expansion gates.
- What contribution margin target is required before expansion? Keep this open, but narrow it to a formal definition plus threshold, including support and service-recovery cost.

## Recommended Next Design Outputs

The next round of work should produce the following outputs, in dependency order:

1. pilot metrics and phase-gate definitions
2. canonical order state machine
3. roles and permissions matrix
4. refund ownership matrix
5. channel adapter contracts
6. menu and availability sync specification
7. exception, substitution, support, and dispute workflow design
8. domain event model and service boundary document
9. reliability objectives document
10. degraded-mode playbook
11. finance and reporting requirements matrix
12. rider compliance checklist
13. observability and incident response design

## Design Principles To Preserve

- order capture must not depend on one channel
- merchant operations must not depend on one tablet
- dispatch must not depend on one operator
- status updates must not depend on one provider
- releases must not require downtime

## Suggested Authoring Sequence

1. define pilot metrics and decision ownership so the next phase has measurable targets
2. define the canonical order state machine
3. define roles and permissions
4. define refund ownership by order source
5. define channel adapter and menu availability contracts
6. define exception flows, substitutions, and support workflows
7. define the event model and service boundaries around those workflows
8. define reliability objectives and degraded-mode behavior
9. define audit, reporting, compliance, and operational response tooling

## How To Use This File

When a decision is answered:

1. move the decision into its primary document or decision record
2. record the rationale, not just the conclusion, when the choice affects interfaces, reliability, or governance
3. remove or narrow the backlog item here
4. keep this file focused on unresolved items only

## Read Next

- return to [README.md](./README.md) and choose the next domain-specific document to deepen
