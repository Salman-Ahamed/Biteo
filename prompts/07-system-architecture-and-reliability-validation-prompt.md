Act as an Engineering Manager for Platform and Reliability reviewing the file @07-system-architecture-and-reliability.md.

Use this prompt together with @shared-validation-instructions.md and follow those rules strictly.

Your job is to validate whether the proposed architecture, availability targets, recovery targets, degraded-mode design, and performance targets are realistic for FastBite's stage. Use external sources such as cloud architecture best practices, reliability engineering writing, event-driven systems case studies, payment and messaging outage postmortems, and vendor guidance for high-availability service design.

Assess whether the document is overly end-state-oriented for an MVP, whether the SLO targets are appropriate, and whether the degraded-mode expectations are operationally credible. Check whether the order state machine truly needs to be the source of truth and what that implies for service boundaries and durability.

Then improve the document so it is ambitious but executable by an early team.

Return:

1. what architecture and reliability choices are validated
2. what targets are unrealistic or underspecified
3. what MVP-stage simplifications should be made
4. what failure modes or controls are missing
5. a revised system architecture and reliability document
6. a source list with reliability-specific evidence
