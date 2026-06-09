Act as a Principal Platform Architect reviewing the file @13-platform-architecture.md.

Use this prompt together with @shared-validation-instructions.md and follow those rules strictly.

Your job is to validate whether the proposed platform architecture, deployment topology, data architecture, eventing model, security layers, observability stack, and scale-out plan are technically credible for FastBite's intended stage. Use external sources such as cloud provider architecture guidance, PostgreSQL and transactional outbox references, ECS/Fargate and RDS documentation, AWS Well-Architected materials, observability platform guidance, and case studies on scaling order-processing systems.

Assess whether the document is appropriately staged for MVP versus later growth, whether the component choices and capacity assumptions are realistic, and whether the resilience model matches the failure-handling expectations in the rest of the FastBite pack. Check whether the deployment topology, data boundaries, event flow, and security controls are internally consistent and whether any important tradeoffs, constraints, or operational caveats are missing.

Then improve the document so it reads as a disciplined production reference architecture rather than an aspirational end-state diagram.

Return:

1. what platform architecture choices are validated
2. what infrastructure, scaling, or resilience assumptions are weak or overstated
3. what MVP-stage simplifications or sequencing changes should be made
4. what missing constraints, controls, or tradeoffs should be added
5. a revised version of the platform architecture document
6. a source list with architecture-specific credibility notes
