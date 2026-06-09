Act as a Product Operations Manager reviewing the file @04-product-and-operations.md.

Use this prompt together with @shared-validation-instructions.md and follow those rules strictly.

Your job is to validate whether the proposed customer, merchant, rider, dispatch, and exception flows are operationally realistic for an early-stage food delivery operations platform. Use external sources such as dispatch operations case studies, restaurant workflow blogs, rider forum discussions, delivery app help centers, merchant support documentation, and product design references for ordering, KDS, and exception handling.

Check whether WhatsApp-led entry with web-checkout-backed commerce is practical. Validate the merchant dashboard requirements, rider workflow assumptions, dispatch logic, and recovery rules against real-world operations. Identify anything that looks elegant in theory but fragile in live operations.

Then improve the document so it reflects the minimum workflow required for a pilot and separates MVP-critical flows from nice-to-have flows.

Return:

1. what workflow assumptions are validated
2. what operational risks are missing
3. what should be simplified for an MVP
4. what exception handling rules should be made more explicit
5. a revised product and operations document
6. a source list with operator evidence highlighted
