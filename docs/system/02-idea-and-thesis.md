# 02. Idea and Thesis

## Purpose

Use this file to define the core business idea in a compact, decision-ready form.

## One-Page Summary

- The target customer is a UK independent or small-chain quick-service restaurant with meaningful off-premise demand, repeat local customers, and visible operational pain from fragmented digital ordering.
- The core problem is a combination of margin leakage, peak-time order chaos, and weak ownership of repeat customers.
- The launch thesis is not to build a broad restaurant operating system or a new consumer marketplace, but to become the merchant control layer for digital orders.
- The initial wedge should combine marketplace aggregation, merchant-owned direct ordering, and kitchen-aware order control.
- Dispatch orchestration and deeper retention tooling should be treated as selective second-phase expansions, not required day-one scope.

## Problem Statement

Independent and small-chain UK QSR operators repeatedly face three linked problems:

1. marketplace dependence compresses already-thin margins
2. operations break down during busy periods because orders arrive from too many sources and often require manual handling
3. repeat customers are retained by marketplaces unless the merchant offers an easier direct path

These problems reinforce each other. Merchants want to reduce marketplace dependence, but they cannot push customers toward direct channels if the direct workflow is slower, less reliable, or harder for staff to manage than marketplace demand.

## Solution Thesis

FastBite should start as a merchant-first control layer for off-premise demand rather than a full-stack restaurant OS.

### Core Launch Wedge

1. marketplace aggregation for Uber Eats, Deliveroo, Just Eat, and similar channels into one operational workflow
2. merchant-owned direct ordering through web checkout and QR entry points, with WhatsApp used only as an entry path where it shortens time to checkout
3. kitchen-aware operations control through KDS integration, prep timing, throttling, and status handling so staff can absorb both marketplace and direct demand reliably

### Phase Two Expansion

1. customer retention tooling for reorder prompts, service updates, and first-party customer capture once direct ordering is active
2. dispatch orchestration for merchants with enough short-radius direct delivery density to justify delivery routing and last-mile optimization

## Positioning Statement

FastBite is not primarily a consumer marketplace.

FastBite is not a full restaurant ERP.

FastBite is the merchant control layer for digital orders: one place to run marketplace demand, keep the kitchen stable, and move repeat buyers into merchant-owned channels over time.

## Strategic Logic

The stronger strategy is:

- let merchants keep marketplaces for discovery
- aggregate all inbound digital demand into one internal workflow
- make the direct channel operationally safe before trying to push adoption aggressively
- convert repeat customers to direct channels over time
- add dispatch only where direct-delivery economics justify the complexity

This is easier to sell, more operationally sound, and more commercially realistic than trying to replace existing platforms immediately or launching with a broad all-in-one product story.

## Ideal Early Customer

- UK independent and small-chain QSR brands, typically single-site through a small multi-site footprint
- already active on at least one delivery marketplace and increasingly dependent on off-premise demand
- clear daily pain from multiple order sources, menu inconsistency, manual re-entry, or peak-time bottlenecks
- dense local catchment with repeat demand and enough pickup or short-radius delivery potential to support direct ordering
- owner-operator or operations lead who feels the pain directly and can adopt a workflow tool without enterprise procurement friction

## Non-Goals

- broad citywide marketplace expansion from day one
- becoming a full restaurant operating suite across payroll, inventory, and dine-in workflows at launch
- making dispatch a required part of the product for every merchant from day one
- prioritizing low-density delivery geographies where direct-order economics are weak
- pure chat-based ordering without a structured checkout and order-control layer

## Success Criteria

- one dashboard becomes the default control point for off-premise orders
- merchants see materially less manual handling and less peak-time confusion
- direct-order adoption grows because the merchant can support it operationally, not just because it is cheaper
- the product improves margin and service reliability together without requiring a consumer app strategy

## Working Assumptions

- operators will keep marketplaces if FastBite improves workflow and helps them capture more repeat demand directly
- operational reliability and ease of setup matter more than feature breadth at launch
- direct ordering only becomes viable when it matches marketplace convenience closely enough for both staff and customers

## Open Questions

- What minimum workflow set makes the control layer feel indispensable in the first week?
- How much onboarding, menu sync, and channel setup can be automated in the first release?
- What direct-ordering experience is strong enough to move repeat customers without heavy discounting?
- Which merchant profiles have enough direct-delivery density to justify dispatch earlier?

## Read Next

- [03-market-and-segmentation.md](./03-market-and-segmentation.md)
- [04-product-and-operations.md](./04-product-and-operations.md)
