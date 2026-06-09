Act as a Solutions Architect reviewing the file @05-integrations-and-data-model.md.

Use this prompt together with @shared-validation-instructions.md and follow those rules strictly.

Your job is to validate whether the proposed hybrid integration model, adapter architecture, and canonical data model are technically and commercially sound for FastBite. Use external sources such as marketplace developer documentation, integration vendor materials, POS integration blogs, engineering case studies on order normalization, event-driven commerce architecture writing, and platform API discussions.

Assess whether the phased integration plan is realistic, whether the canonical objects are sufficient, and whether the adapter responsibilities are complete. Validate whether a hybrid bridge strategy is the right launch choice or if direct integrations should be prioritized earlier. Look for missing concepts such as state models, idempotency boundaries, reconciliation logic, and unsupported channel behaviors.

Then improve the document so it becomes a stronger integration specification that product and engineering teams could act on.

Return:

1. what architecture choices are validated
2. what technical assumptions are weak or incomplete
3. what critical model elements or states are missing
4. how the phased integration strategy should be adjusted
5. a revised version of the integration and data model document
6. a source list with technical credibility notes
