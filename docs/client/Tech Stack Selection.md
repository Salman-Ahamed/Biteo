We chose Next.js, NestJS, and TypeScript because they give us the best balance of speed, structure, and hiring practicality for this project. Next.js fits a web-first product like checkout, merchant panels, and admin tools; NestJS gives us a proper backend for APIs, webhooks, workers, and order logic; and TypeScript lets us keep one language across frontend and backend. It also matches the team’s familiarity with the Node.js ecosystem, and finding developers in this ecosystem is generally easier than many alternatives.

For context, here is a quick view of why we did not go with some other common options:

**Ruby on Rails**  
Good option because it is excellent for shipping business-heavy MVPs quickly.  
We did not choose it because we wanted a TypeScript-first stack across frontend and backend, with easier type sharing and less context switching.

**Go**  
Good option because it is strong for high-concurrency and performance-sensitive backend systems.  
We did not choose it because those benefits are not the main need at MVP stage, and it would slow product iteration.

**Java**  
Good option because it is very strong for large, structured, enterprise-grade backend systems.  
We did not choose it because it is heavier than we need for an early-stage product and would reduce development speed.

**Python**  
Good option because it is productive for backend work and especially strong for ML, data, and automation-heavy products.  
We did not choose it because this project is not primarily ML-first, and it would still likely require a separate TypeScript frontend.

**Bun or Deno**  
Good option because they are modern runtimes with promising developer experience and performance.  
We did not choose them because Node.js is still the more proven ecosystem for production systems with mature libraries, integrations, payments, queues, hosting support, and a larger hiring pool.

**Only Next.js for frontend and backend**  
Good option because it can handle the web layer and some lightweight backend endpoints.  
We did not choose that approach because this product also needs a dedicated backend for canonical order logic, provider webhooks, background jobs, retries, and reconciliation.

**Svelte**  
Good option because it is lightweight and can produce very fast, clean frontend experiences.  
We did not choose it because its ecosystem and hiring pool are smaller, and we wanted the safer mainstream path for a business-critical product.

**Angular**  
Good option because it provides strong structure and works well for large frontend teams.  
We did not choose it because it is heavier than we need, and it would slow down MVP iteration compared with a more flexible Next.js approach.

**Vue**  
Good option because it is productive, clean, and easier to learn than some other frontend frameworks.  
We did not choose it because Next.js gave us a more natural fit with our preferred TypeScript and Node.js ecosystem, stronger React-based hiring availability, and a better match for the team’s familiarity.
