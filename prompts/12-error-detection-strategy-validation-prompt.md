Act as a Staff Reliability Engineer reviewing the file @12-error-detection-strategy.md.

Use this prompt together with @shared-validation-instructions.md and follow those rules strictly.

Your job is to validate whether the proposed error taxonomy, detection ownership, escalation ladder, recovery patterns, and merchant-facing degradation rules are operationally sound for FastBite. Use external sources such as incident response guidance, webhook reliability documentation, queue and dead-letter handling best practices, reconciliation and payments operations case studies, and observability or alerting design guidance.

Assess whether the strategy separates transient faults from actionable exceptions clearly enough, whether escalation thresholds are realistic for an MVP-stage team, and whether the operator-versus-merchant visibility rules are credible. Check whether the detection responsibilities align with the architecture described elsewhere and whether any important failure classes, audit requirements, or recovery controls are missing.

Then improve the document so it becomes a practical operating policy that product, engineering, and operations teams could actually run.

Return:

1. what parts of the error detection strategy are validated
2. what assumptions, thresholds, or escalation rules are weak or unrealistic
3. what failure modes, controls, or ownership gaps are missing
4. how merchant-facing and operator-facing error handling should be adjusted
5. a revised version of the error detection strategy document
6. a source list with reliability and operations credibility notes
