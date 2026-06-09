# 14. Application Stack and Deployment Decision

**Document Version:** 2.1  
**Date:** May 2026  
**Author Role:** Principal Application Architect  
**Status:** Decision memo

## Purpose

Record the recommended application framework and deployment model for FastBite from MVP through early growth, using source-backed claims and explicit assumptions where certainty is limited.

## Decision Summary

- Use Next.js for FastBite's web surfaces: checkout, merchant web, admin tools, and any early rider PWA.
- Use NestJS for backend application services: synchronous APIs, webhook ingestion, canonical order logic, and background execution.
- Keep one backend codebase at MVP, but run separate runtime units for API and workers.
- Prefer scheduled ECS tasks triggered by EventBridge for periodic jobs before introducing an always-on scheduler service.
- Use AWS ECS on Fargate for production compute, in one AWS Region and across at least two Availability Zones.
- Use one VPC per long-lived environment, with public subnets for internet-facing load balancers and private subnets for application and data services.
- Use Amazon RDS for PostgreSQL as the system of record and enable Multi-AZ for production.
- Use Amazon SQS with DLQs for asynchronous work. Keep Redis optional rather than mandatory.

## Decision Context

This decision should be interpreted alongside the rest of the pack:

- [04-product-and-operations.md](./04-product-and-operations.md) requires web-first checkout, merchant workflows, and operator fallback paths.
- [05-integrations-and-data-model.md](./05-integrations-and-data-model.md) requires a canonical order model, adapters, reconciliation, and idempotent integration handling.
- [07-system-architecture-and-reliability.md](./07-system-architecture-and-reliability.md) requires a modular monolith with background workers, transactional outbox, and PostgreSQL as the source of truth.
- [13-platform-architecture.md](./13-platform-architecture.md) assumes managed AWS infrastructure, background execution, and phased complexity rather than day-one microservices.

The stack decision should optimize for those constraints, not for framework fashion.

## Recommended Direction

### Web layer: Next.js

Next.js is the recommended web framework because FastBite is web-first across both customer and operator journeys.

It fits the expected surface area:

- public landing and merchant-facing pages
- hosted checkout
- merchant dashboard and KDS web views
- admin and operator tools
- potential rider PWA before native apps

Why it fits:

- file-based routing and layouts suit multiple web surfaces in one application
- server components and server rendering support strong first-load behavior for checkout and operational pages
- route handlers support UI-adjacent backend endpoints such as callbacks, webhooks, and backend-for-frontend aggregation
- the framework supports both public and authenticated surfaces without requiring a separate bespoke SPA architecture

Boundary for this decision:

- Next.js owns the web layer and backend-for-frontend endpoints close to that web layer.
- It is not the preferred home for long-running queue consumers, reconciliation loops, or the canonical domain engine.

### Backend layer: NestJS

NestJS is the recommended backend framework because FastBite needs modular structure, background execution patterns, and operational discipline more than minimal framework surface area.

It matches the backend shape FastBite needs:

- canonical order creation and state transitions
- payment callbacks and provider webhooks
- adapter boundaries for external integrations
- retries, asynchronous jobs, and reconciliation flows
- explicit places for validation, guards, interceptors, logging, and configuration

Why it fits:

- FastBite's backend is not just a thin REST API; it needs canonical state handling, webhook ingestion, retryable workflows, and operational tooling
- NestJS provides stronger default structure for a growing modular monolith than an ad hoc low-level Node.js framework setup

### Why not use Next.js as the only backend runtime

This is an operating model decision, not a statement that Next.js cannot handle backend work.

Next.js can:

- expose HTTP endpoints
- receive webhooks
- proxy requests
- implement backend-for-frontend behavior

FastBite should still prefer a separate backend runtime because it expects:

- canonical order mutation logic that should stay isolated from UI concerns
- background workers consuming queue-backed jobs
- retries, reconciliation, and integration orchestration that should not share failure domains with page rendering
- deployment and scaling policies that differ between web traffic and background backlog

For this product shape, separating the web runtime from the backend runtime is the safer MVP posture.

### Why TypeScript is the default, but not a universal requirement

FastBite should default to TypeScript because:

- the selected web stack is already Next.js
- the selected backend stack is NestJS
- a single-language stack simplifies hiring, handoff, debugging, and tooling for a small team

This is a delivery decision, not a universal technical truth.

Python remains a reasonable alternative if one of these becomes true:

- the founding or early team is materially stronger in Python than in TypeScript
- major early differentiation depends on ML-heavy workflows
- existing company assets or hiring channels make Python operationally cheaper than a mixed stack

## Deployment Decision

### Runtime model

For MVP, FastBite should keep:

- one frontend codebase using Next.js
- one backend codebase using NestJS

But it should deploy separate runtime units:

1. `frontend` ECS service
2. `api` ECS service
3. `worker` ECS service
4. scheduled ECS tasks triggered by EventBridge

This preserves one backend codebase while keeping scaling and failure boundaries separate.

### Responsibilities by runtime

#### Frontend service

- Next.js rendering and static assets
- hosted checkout flows
- merchant dashboard and KDS web views
- admin and operator screens
- any early rider PWA

#### API service

- synchronous HTTP APIs
- authentication and session-adjacent logic
- canonical order creation and state transitions
- payment callbacks and provider webhooks
- merchant actions such as accept, reject, prep updates, and pause controls

#### Worker service

- transactional outbox relay
- asynchronous notification delivery
- channel synchronization
- retry and backoff handling
- reconciliation workflows triggered from queues

#### Scheduled ECS tasks

- timeout sweeps
- stale-order scans
- settlement import triggers
- low-frequency reconciliation scans
- periodic housekeeping

An always-on scheduler service is a later option, not the MVP default.

### Why separate runtime units

The scaling signals are materially different:

- frontend and API scale on request rate, latency, and CPU or memory pressure
- workers scale on queue backlog, age of oldest message, retry pressure, and job duration
- scheduled jobs often do not need continuous capacity at all

Separating these workloads reduces contention and makes incidents easier to isolate.

### AWS baseline topology

The recommended single-region production baseline is:

- one AWS Region initially
- one VPC per long-lived environment such as production and staging
- at least two Availability Zones per environment
- public subnets for ALB and other intentionally internet-facing components
- private application subnets for ECS tasks
- private data subnets for RDS and optional ElastiCache

Illustrative layout:

```text
[AWS Region: eu-west-2]
  -> [1 VPC]
       -> [Public Subnet AZ-A] [Public Subnet AZ-B]
       -> [Private App Subnet AZ-A] [Private App Subnet AZ-B]
       -> [Private Data Subnet AZ-A] [Private Data Subnet AZ-B]

  -> [ALB]
       -> [Next.js Frontend ECS Service]
       -> [NestJS API ECS Service]

  -> [NestJS Worker ECS Service]
  -> [EventBridge -> Scheduled ECS Tasks]
  -> [Amazon RDS for PostgreSQL Multi-AZ]
  -> [Amazon SQS + DLQ]
  -> [Amazon S3]
  -> [Secrets Manager / Parameter Store]
  -> [CloudWatch Logs, Metrics, Alarms, Tracing]
  -> [Optional ElastiCache Redis]
```

### Containers and images

The normal MVP posture is:

- one frontend image for Next.js
- one backend image for NestJS
- separate task definitions or commands for `api`, `worker`, and migration or scheduled-task entry points

Illustrative backend image pattern:

```text
backend image
  -> command: api
  -> command: worker
  -> command: migrate
  -> command: scheduled-task
```

This gives independent deployment and scaling without forcing early repo or service sprawl.

## Key Assumptions And Tradeoffs

### Next.js runtime boundary

Next.js documentation supports backend-for-frontend behavior and route handlers, but it also documents deployment environments where handlers may behave like short-lived functions. That is the main reason not to place canonical order processing and long-running operational jobs there.

### TypeScript versus Python

The recommendation for TypeScript is based on delivery simplicity and stack coherence. It should not be read as proof that Python is inherently the wrong choice for this class of product.

### Scheduler posture

AWS ECS distinguishes between long-running services and scheduled tasks. For MVP, recurring operational jobs should default to EventBridge-triggered scheduled tasks. An always-on scheduler service should be introduced only if job frequency, dynamic scheduling needs, or operational complexity makes that worthwhile.

### Queue and Redis relationship

NestJS queue examples center on Bull or BullMQ, which are Redis-backed. FastBite's default asynchronous transport should still be SQS. Redis should remain optional unless the team deliberately adopts Redis-backed queueing, shared caching, or coordination features that require it.

## MVP-Stage Simplifications And Sequencing

### Keep at MVP

- Next.js frontend service
- NestJS API and worker services from one backend codebase
- ECS on Fargate
- RDS PostgreSQL as the source of truth
- SQS plus DLQ for asynchronous work
- EventBridge scheduled ECS tasks for periodic jobs
- ALB in front of the internet-facing services
- at least two Availability Zones in production

### Defer until justified

- dedicated always-on scheduler service
- Redis, unless sessions, shared cache, rate limiting, or a Redis-backed queue library becomes necessary
- read replicas, unless reporting or read pressure justifies them
- microservice extraction by domain
- multi-region availability
- WebSocket-heavy operator workflows if polling remains adequate

### Environment staging posture

One VPC per environment is reasonable for long-lived environments, but full production network cost should not be copied into every ephemeral environment.

Recommended interpretation:

- production: dedicated VPC, multi-AZ, RDS Multi-AZ
- staging: dedicated VPC if the team needs realistic validation of networking and failover assumptions
- development and previews: lighter-weight environments are acceptable if they do not become the basis for production promises

## Missing Constraints That Should Be Explicit

### Security and networking

- application and data services should not have direct public ingress
- use per-task IAM roles with least privilege
- store secrets in Secrets Manager or Parameter Store, not in images or source files
- enable encryption at rest for RDS, SQS, S3, and Redis if used
- define outbound internet access deliberately, because private subnets on Fargate usually imply NAT gateway or VPC endpoint decisions with real cost impact

### Delivery and operations

- use infrastructure as code from day one
- define health checks, log retention, alarms, and rollback expectations before launch
- keep database migrations backward-compatible with rolling deployments
- maintain explicit runbooks for queue backlog, webhook replay, and worker failure recovery

### Database and scaling

- Multi-AZ RDS is for availability, not read scaling
- application scaling must respect database connection limits and write-path constraints
- do not claim autoscaling thresholds until the team has real metrics or load tests

### Queue semantics

- SQS Standard queues are appropriate when FastBite treats deliveries as at-least-once and keeps consumers idempotent
- use FIFO only where strict ordering or deduplication requirements justify the tradeoff
- DLQ handling, replay policy, and operator visibility are part of the MVP operating model, not later hardening

## Tradeoffs

### Fargate versus EC2

Fargate reduces server-management burden and is a good small-team default. The tradeoff is cost: at higher steady-state utilization, self-managed EC2 may become cheaper. That is an early-growth review point, not a day-one blocker.

### RDS Multi-AZ

RDS Multi-AZ improves resilience, but AWS documents that it can increase write and commit latency versus Single-AZ. For FastBite's order system, that tradeoff is acceptable in production because acknowledged order durability matters more than minimizing write latency.

### One VPC per environment

This improves isolation and reduces accidental cross-environment coupling. The tradeoff is duplicated network cost and operational overhead, especially NAT and public IPv4 charges. This is acceptable for long-lived environments, but not for every preview environment.

### Redis optionality

Keeping Redis optional simplifies MVP infrastructure. The tradeoff is that some patterns, especially BullMQ-style queueing, shared cache, and session coordination, become harder or push the design toward other implementations. Redis should stay an explicit later choice rather than a hidden dependency.

## Recommended Phase Posture

### Pilot and MVP

- Next.js frontend service
- NestJS API service
- NestJS worker service
- EventBridge-triggered scheduled ECS tasks
- RDS PostgreSQL Multi-AZ in production
- SQS-backed asynchronous work
- Redis only if a measured requirement appears

### Early growth

- keep the same overall shape
- tune autoscaling policies per runtime
- add Redis or a read replica only if production metrics justify them
- split a worker-heavy domain only if queue pressure, compliance, or team ownership requires it
- do not move to microservices until a real scaling or ownership trigger appears

## Open Questions

- Should FastBite use a monorepo or separate repos for frontend and backend? This is a delivery preference, not an architecture blocker.
- Which schema and contract tooling should the team use to keep web and backend validation aligned?
- Which jobs truly need queue-backed durability versus simple scheduled task execution?
- What is the acceptable non-production fidelity level before staging must mirror production networking?

## Source Notes

- Next.js Layouts and Pages. Primary. Relevant for routed multi-surface web architecture. Last updated May 2026.
- Next.js Server and Client Components. Primary. Relevant for checkout and mixed SSR plus interactive web surfaces. Last updated May 2026.
- Next.js Route Handlers. Primary. Relevant for webhooks and UI-adjacent HTTP endpoints. Last updated May 2026.
- Next.js Backend for Frontend guide. Primary. Relevant because it supports BFF patterns and documents caveats around deployment environments and long-running handlers. Last updated May 2026.
- NestJS Modules and Providers docs. Primary. Relevant for modular monolith structure and dependency injection. Accessed May 2026.
- NestJS Queues docs. Primary. Relevant because they support background processing but also show that official queue integrations are Redis-backed. Accessed May 2026.
- NestJS Task Scheduling docs. Primary. Relevant for periodic jobs, but not sufficient on their own to justify a dedicated always-on scheduler service. Accessed May 2026.
- Amazon ECS docs for ECS overview, services, and scheduling tasks. Primary. Relevant for Fargate, service versus scheduled task distinctions, and small-team container operations. Accessed May 2026.
- Amazon VPC user guide. Primary. Relevant for the VPC-spans-region and subnet-is-single-AZ model. Accessed May 2026.
- Amazon RDS Multi-AZ docs. Primary. Relevant for HA versus read scaling and the write-latency tradeoff. Accessed May 2026.
- Amazon SQS developer guide. Primary. Relevant for durable, decoupled async processing and DLQ posture. Accessed May 2026.
- AWS Well-Architected REL04-BP02 and REL10-BP01. Primary. Relevant for loose coupling, async boundaries, and multi-AZ deployment posture. Accessed May 2026.
- Heroku Worker Dynos, Background Jobs and Queueing. Secondary practitioner source. Relevant for the operational case for separating web and worker runtimes. Last updated January 2026.
