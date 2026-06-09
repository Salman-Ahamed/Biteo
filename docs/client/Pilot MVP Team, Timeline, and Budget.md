# Pilot MVP Team, Timeline, and Budget

This note sets out a realistic delivery shape for FastBite's pilot MVP if the goal is to launch a robust first version that merchants can evaluate seriously.

The assumption behind this estimate is narrow but important:

- the pilot MVP is focused on system reliability, core merchant operations, and one marketplace integration from day one
- the product is web-first rather than native-app-first
- the delivery team is Bangladesh-based, with one senior engineer, one mid-level engineer, and junior-heavy implementation support
- the team uses AI-assisted development with Claude Code to accelerate implementation, testing support, and routine engineering work
- the launch scope is kept tight enough that the team can ship without hesitation

## Recommended Team Shape

For this pilot, the recommended delivery team is:

- 1 system and platform engineer to own system design, environments, CI/CD, deployment, observability, and release readiness
- 2 full-stack engineers to build the checkout, merchant console, admin tooling, backend APIs, worker flows, and marketplace connector
- 1 QA engineer as the minimum practical quality layer for test planning, regression, acceptance support, and launch checks
- 2 QA engineers if the goal is a safer schedule with better connector coverage and less launch risk

This is a focused team rather than a large one. It is enough for a serious pilot build, but it still depends on disciplined scope control and quick product decisions.

## What This Team Can Credibly Launch

With that team shape, FastBite can credibly commit to a pilot MVP that includes:

- hosted mobile web checkout for direct orders
- merchant order console for direct, manual, and one marketplace order source
- manual order entry for phone and walk-in orders
- core order lifecycle controls such as accept, reject, prep updates, ready, delivered or handoff, and cancellation
- simple item availability and pause intake controls
- one reliable outbound notification path
- manual dispatch and exception handling rather than advanced delivery automation
- basic admin setup for merchants, users, and support operations
- audit trail, retry-safe jobs, failure visibility, and operator fallback tools

The main constraint is the marketplace connector. One marketplace integration is realistic in the pilot if the connector scope is narrow and the team avoids promising deep parity across every operational edge case.

## Realistic Timeline

For this team, the realistic timeline is:

- about 6 to 8 weeks for a pilot MVP that includes one marketplace integration and a production-ready first launch posture

A practical delivery breakdown looks like this:

### Week 1

- system design and delivery planning
- repository setup, environments, CI/CD, and deployment baseline
- database schema, canonical order model, auth, and core application scaffolding

### Weeks 2 to 3

- direct ordering checkout
- merchant console and admin tools
- manual order flow
- core order state transitions and audit history

### Weeks 4 to 5

- marketplace integration for one connector
- notification jobs and worker flows
- pause controls, availability updates, and operational exception handling
- observability, error handling, and manual recovery tooling

### Weeks 6 to 8

- QA regression cycles
- user acceptance testing
- merchant onboarding support
- launch rehearsals, bug fixing, and controlled go-live

## Timing Interpretation

- 5 weeks is a best-case internal target for a thin alpha, not the safest client-facing promise
- 6 to 8 weeks is the more credible pilot estimate for a launch that can be presented to merchants with confidence
- 8 to 10 weeks becomes more likely if the marketplace scope expands, external approvals move slowly, or printing, reporting, and role complexity are added too early

Claude Code can reduce engineering time on implementation, boilerplate, refactoring, and test support, but it does not remove the need for integration QA, operational rehearsal, and launch hardening.

## Indicative Budget Range

Using the current salary assumptions for a Bangladesh-based team:

- senior engineer: 2,000 USD per month
- mid-level engineer: 1,000 USD per month
- junior engineer or QA: 500 USD per month

Using a simple planning conversion of 1 USD = about 0.74 GBP, the direct monthly payroll works out as follows:

- 4-person team: 1 senior, 1 mid-level, and 2 juniors = 4,000 USD per month, or about 2,960 GBP per month
- 5-person team: 1 senior, 1 mid-level, and 3 juniors = 4,500 USD per month, or about 3,330 GBP per month

### Raw Team Payroll

For the 6 to 8 week pilot window, raw payroll is approximately:

- about 4,440 to 5,920 GBP for a 4-person team
- about 4,995 to 6,660 GBP for a 5-person team

This is the direct team salary cost only. It does not include pricing buffer, management margin, cloud spend, tools, or post-launch support.

### Recommended Client Quote

For a client-facing delivery price, a more practical quote is:

- about 7,000 to 9,500 GBP for a lean 4-person pilot team
- about 8,000 to 11,000 GBP for a 5-person pilot team with additional QA coverage

These ranges are still lean. They assume Bangladesh-based delivery costs, disciplined scope, and a narrowly defined pilot MVP. The quote can move upward if the marketplace connector proves heavier than expected, if launch support is extended, or if more senior oversight is required during delivery.

## What The Budget Normally Covers

The estimate above usually covers:

- product engineering and platform setup
- AI-assisted development workflow using Claude Code
- QA planning and regression support
- deployment setup and release readiness
- core monitoring and operational visibility for the pilot

It should not automatically be assumed to cover:

- extended post-launch support beyond the initial pilot window
- heavy founder sales time, merchant acquisition, or onboarding fieldwork
- marketplace commercial negotiation delays or provider approval delays
- hardware, tablets, printers, or merchant-specific setup costs
- paid acquisition, promotions, or merchant subsidy programs

## Recommended Client-Facing Position

The strongest client-facing statement is:

FastBite can be launched as a tightly scoped pilot MVP in about 6 to 8 weeks with a focused 4 to 5 person delivery team, provided the product is limited to one marketplace integration, robust core order workflows, and explicit manual fallback where automation is not yet proven.

The weaker statement would be to imply a broader multi-channel, fully automated operations platform in the same timeframe. That would create schedule risk and increase the chance of a fragile first launch.
