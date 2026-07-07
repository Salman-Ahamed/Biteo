# Uber Eats Feature Masterlist v3 — Implementation Breakdown

**Date:** July 2026 (QA audit corrected)
**Rate:** £75/hr (blended senior/mid UK rate)
**Total Est. Hours:** 2,812h
**Total Est. Cost:** £210,900

---

## QA Audit Report — v3 Corrections

### Missing Features Restored (12 additions, +86h)

| v2 Ref | Feature | v3 Task Added | Hours |
|--------|---------|--------------|-------|
| v2:6 | B2B corporate invoicing & recurring office lunch scheduling | M4 Group Ordering — new task #13 | 12h |
| v2:7 | Nutrition/macro auto-tracking & fitness goal integration | M8 AI Engine — new task #13 | 16h |
| v2:8 | Dark kitchen / virtual restaurant onboarding & management | M5 Merchant Dashboard — new task #31 | 10h |
| v2:663-665 | Customer claims transparency dashboard & reviews-based recommendations | M5 Merchant Dashboard — new task #32 | 8h |
| v2:669 | Merchant performance benchmarking vs peers | M5 Merchant Dashboard — new task #33 | 6h |
| v2:790 | Training completion tracking (rider) | M6 Rider App — new task #53 | 4h |
| v2:808 | Rider insurance enrolment flow | M6 Rider App — new task #54 | 4h |
| v2:809 | Tax information submission (rider) | M6 Rider App — new task #55 | 4h |
| v2:1054 | Auto-payment on delivery confirmation | M3 Payment — new task #23 | 4h |
| v2:1055-1056 | Fiserv + Cybersource processor integrations | M3 Payment — new task #24 | 8h |
| v2:613 | Merchant notification preferences (store status, connectivity, POS issues, cancellations, missed/inaccurate orders) | M5 Merchant Dashboard — new task #34 | 6h |
| v2:1047 | Single-click reorder payment (one-tap using saved card, bypasses full checkout) | M3 Payment — new task #25 | 4h |

### Time Estimate Corrections (8 adjustments, +42h)

| Task | Module | Old | New | Δ | Reason |
|------|--------|-----|-----|---|--------|
| Curated personalised restaurant feed | M2 Browse #1 | 24h | 32h | +8h | ML recommendation pipeline + cold start + A/B evaluation |
| AI assistant prompt | M8 AI Engine #5 | 16h | 20h | +4h | Multi-context prompt generation + interaction flow |
| Priority/long-range delivery fee | M3 Checkout #9 | 6h | 10h | +4h | Dynamic pricing algorithm with market-specific rules |
| Commission & fee plan management | M5 Dashboard #23 | 12h | 20h | +8h | Multi-tier configurable fee engine with regional rules |
| Per-trip earnings breakdown | M6 Rider #26 | 8h | 12h | +4h | Real-time base/distance/time/surge/boost/tip calculation |
| WhatsApp Business API setup | M8 WhatsApp #1 | 12h | 20h | +8h | Meta approval process + template setup + webhook |
| Live location on map | M4 Order Tracking #5 | 16h | 20h | +4h | GPS + WebSocket + battery-efficient polling |
| AI side dish / upsell suggestion | M8 AI Engine #3 | 12h | 14h | +2h | Revenue impact tracking for merchant dashboard |

### Duplicate Merges (3 resolved, −8h)

| # | Duplicate Pair | Action | Hour Saving |
|---|---------------|--------|-------------|
| 1 | M6 #34 "Uber Eats Pro hub" (14h) + #38 "Uber Eats Pro Programme" (12h) | Merged into single task (22h) | −4h |
| 2 | M6 #41 "Verification screen at pickup" (4h) + #18 "Order pickup confirmation" (8h) | Absorbed into #18 | −4h |
| 3 | M6 #39 "Cross-zone delivery" + #40 "Extended delivery opt-in" | Made adjacent (swapped with #43-44) | 0h (reorder only) |

### Task Reorderings (3 modules)

| Module | Change |
|--------|--------|
| M2 Menu System | Pickup tasks (#17-20) moved to positions #3-6 (after allergen info) |
| M3 Cart | Promo mechanics (#14-18) moved after #5 (auto-applied discounts) |
| M1 Customer Account | UGC tasks (#12-14) moved after #4 (rate & review) |

### Arithmetic Corrections (Round 3 — systematic module re-sums)

| Module | Header Value | Actual Task Sum | Correction |
|--------|-------------|----------------|------------|
| M2 Browse & Discovery | 168h | 186h | +18h |
| M2 Menu System | 120h | 126h | +6h |
| M3 Cart | 96h | 102h | +6h |
| M3 Checkout | 124h | 130h | +6h |
| M3 Payment & Wallet | 184h | 240h | +56h |
| M4 Order Tracking & Notifications | 124h | 140h | +16h |
| M5 Merchant Dashboard Web | 276h | 288h | +12h |
| M6 Rider App | 296h | 374h | +78h |
| M7 Admin & Operations Console | 282h | 286h | +4h |
| M8 AI & Personalisation Engine | 258h | 260h | +2h |
| **Subtotal (module corrections)** | **2,608h** | **2,810h** | **+204h** |
| Header-claim alignment (file claimed 2,512h vs module headers 2,608h) | 2,512h | 2,608h | +96h |
| **Total cumulative** | **2,512h** | **2,812h** | **+300h** |

### Absorbed Low-Severity Items (63 items, no new tasks)

The following v2 features are implementation details already covered by existing v3 tasks:

| v2 Ref | Feature | Absorbed Into |
|--------|---------|---------------|
| v2:87 | "Best match" algorithmic sorting | M2 Browse #10 — sort options augmented |
| v2:225 | Place order button | M3 Checkout — implicit in checkout flow |
| v2:343-344 | Expired vouchers/promos view + terms | M3 Payment #16 — voucher expiry tracking |
| v2:353 | Send gift card from within app | M3 Payment #13 — gift card system |
| v2:356 | Gift card balance converts to Uber Cash | M3 Payment #14 — gift card redemption to wallet |
| v2:371, 520 | Modify subscription plan (upgrade/downgrade) | M7 Subscriptions #1 — plan management |
| v2:381 | Delivery person name and photo display | M4 Order Tracking #5 — live location implies driver info |
| v2:416 | Scan Bill (digital) for pickup auth | M6 Rider #18 — order pickup confirmation |
| v2:475 | 6-month subscription plan (select markets) | M7 Subscriptions #1 — plan variants |
| v2:505 | Priority support access (Uber One benefit) | M7 Subscriptions #6 — benefits engine |
| v2:521 | Modify payment method for subscription | M7 Subscriptions #1 — account management |
| v2:523 | View savings summary | M7 Subscriptions #6 — benefits engine |
| v2:540 | Flexible fulfillment (own staff or Uber fleet) | M5 Dashboard #27-30 — marketplace operations |
| v2:547 | Return an item flow in order history | M5 Dashboard #29 — retail returns flow |
| v2:559 | Pay online or at restaurant (pickup) | M2 Menu #3-6 — pickup flow |
| v2:700 | Co-branded credit card marketing for merchants | M5 Dashboard #25 — financial portal |
| v2:711 | Dedicated deals hub | M2 Browse #6 — promotional banners |
| v2:750 | Real-time campaign optimisation | M7 Admin #9 — campaign analytics augmented |
| v2:759 | Adelaide + Kantar attention metric | M7 Admin #19 — brand lift studies framework |
| v2:760 | In-store traffic measurement | M7 Admin #9 — campaign analytics augmented |
| v2:761 | Add-to-cart rate measurement | M7 Admin #9 — campaign analytics augmented |
| v2:770 | Creative management (self-serve ads) | M7 Admin #7 — Ads Manager campaign creation |
| v2:772 | Ads APIs for campaign management | M7 Admin #7 — Ads Manager |
| v2:773 | POS integration for ad management | M7 Admin #4 — advertising platform + M5 Order Mgmt #19 — POS |
| v2:774 | CPG brand direct access | M7 Admin #7 — self-serve Ads Manager |
| v2:806 | Delivery bag branding (rider) | M6 Rider #37 — equipment ordering portal |
| v2:821, 853 | Destination transparency (riders) | M6 Rider #10 — order details display |
| v2:824 | 6-hour offline reset for driving limit | M6 Rider #33 — driving limit enforcement |
| v2:828 | Minimum session hours (select markets) | M6 Rider #41 — shift allocation |
| v2:860 | Second offer hidden until first accepted | M6 Rider #12 — batched courier offers |
| v2:891 | Weekly earnings targets/challenges (rider) | M6 Rider #26-28 — earnings views |
| v2:925 | Rider perks and deals page | M6 Rider #34 — Pro Programme |
| v2:926 | Rider events and happenings page | M6 Rider #36 — help centre + community forums |
| v2:1000 | Courier performance analytics | M7 Admin #13 — BI reporting dashboard |
| v2:1034 | Bank transfer (payment method) | M3 Payment #4-6 — payment methods |
| v2:1058 | Unified reporting, billing, settlements | M3 Payment #20 — multi-acquirer + M5 Dashboard #13 — payouts |
| v2:1085, 1087, 1088 | Fuel surcharge / rider fee / platform fee | M3 Cart #2 — fee line items |
| v2:1100 | Registration fee (merchant commission) | M5 Dashboard #23 — commission & fee plan |
| v2:474 | No refunds for partial months (subscription) | M7 Subscriptions #5 — cancellation policy |
| v2:488 | Uber One icon on eligible stores/items | M7 Subscriptions #6 — benefits engine |
| v2:713 | Reorder Rewards (post-purchase incentive) | M3 Cart #10 — surprise reward mechanics |
| v2:722 | Order tracking page ad placement | M7 Admin #4 — in-app advertising platform |
| v2:724 | Full-page interstitial ad | M7 Admin #4 — in-app advertising platform |
| v2:726 | Payment method promotion at checkout | M7 Admin #4 — in-app advertising platform |
| v2:937 | Seat belt reminders | M6 Rider #32 — safety toolkit |
| v2:939 | PPE distribution partnerships | M6 Rider #46 — PPE distribution / helmet initiatives / safety kits |
| v2:1072 | CTBC Bank co-branded credit card (Taiwan) | M7 Subscriptions #10 — credit card partnerships |
| v2:1073 | HSBC cashback partnership (select markets, weekends) | M7 Subscriptions #10 — credit card partnerships |
| v2:1074 | Funding Societies merchant financing | M5 Dashboard #25 — merchant financial portal |
| v2:1075 | AEON Bank merchant financing | M5 Dashboard #25 — merchant financial portal |
| v2:1203 | Uber rides app integration (cross-promotion) | M7 Admin #28 — cross-platform marketing programmes |
| v2:1207 | Bundled offers (ride + meal) | M7 Admin #28 — cross-platform marketing programmes |
| v2:1208 | Eats for the Way | M7 Admin #28 — cross-platform marketing programmes |
| v2:119 | Uber One-exclusive offers badge on restaurant card | M2 Browse #12 — restaurant card promo badge |
| v2:444 | "New restaurant in area" promotional notification | M4 Order Tracking #13 — promotional notification engine |
| v2:459 | Account security alert (new login) | M1 Auth #11 — Privacy Center account notifications |
| v2:942 | Safety workshops and training | M6 Rider #44-46 — safety toolkit & PPE initiatives |
| v2:1149 | yuu Rewards Club (Taiwan partner) | M7 Subscriptions #10 — credit card & loyalty partnerships |
| v2:1175 | Full cash refund policy for missing/incorrect orders (California AB 578) | M3 Payment #21 — refund policy engine |
| v2:502 | Voucher/promo refund on order cancellation (Uber One benefit) | M3 Payment #21 — refund policy engine |
| v2:503 | Uber One exclusive tables at select Dine Out restaurants (AU) | M7 Subscriptions #6 — benefits engine |
| v2:524 | Terms & conditions per market (subscription) | M7 Subscriptions #1 — plan management |
| v2:614 | Customer reviews (read and respond) | M5 Dashboard #32 — reviews-based recommendations |
| v2:820 | Scheduled sessions (market-specific) | M6 Rider #41 — shift allocation / schedule booking system |

---

## Payment Terms

- **50% advance** per milestone — before work starts on that milestone
- **50% on completion** — after milestone is fully delivered and accepted
- Milestones billed sequentially; next milestone advance is due when current milestone is signed off
- Any change in scope after milestone sign-off will be assessed and priced separately

---

## Milestone 1: Auth & Account Foundation
**Modules: Auth & Profile (120h) + Customer Account (96h) = 216h | £16,200**

### Auth & Profile — 120h

| # | Task | Hours |
|---|------|-------|
| 1 | Phone number registration with SMS OTP verification | 16h |
| 2 | Email registration with email verification flow | 8h |
| 3 | Google/Apple social login integration | 12h |
| 4 | Password creation, management, forgot/reset flow | 12h |
| 5 | Remember me / auto-login session persistence | 4h |
| 6 | Profile photo upload (S3/CDN) | 4h |
| 7 | Profile CRUD (name, phone, email edit) | 8h |
| 8 | Address book — add/edit/delete/set default/label | 16h |
| 9 | Geocoded address pin on map (Google Maps integration) | 8h |
| 10 | Notification preferences management | 8h |
| 11 | Privacy Center (data access, download, account deletion) | 12h |
| 12 | Two-step verification for sensitive data access | 12h |

### Customer Account — 96h

| # | Task | Hours |
|---|------|-------|
| 1 | Past orders list with pagination | 8h |
| 2 | Order detail view (items, price, status timeline) | 8h |
| 3 | Repeat order (quick reorder from history) | 6h |
| 4 | Rate & review past orders with photo upload | 10h |
| 5 | UGC programme — food photo requests for un-imaged menu items | 6h |
| 6 | In-order feedback prompts (per-item rating, Dish-out style) | 6h |
| 7 | UGC moderation tools (flag, approve, hide) | 4h |
| 8 | Invoice/receipt view and download | 6h |
| 9 | Order cancellation flow (before preparation) | 8h |
| 10 | Refund status tracking display | 6h |
| 11 | Report an issue flow (categories, attachment) | 8h |
| 12 | Favourite restaurants/dishes/stores list | 8h |
| 13 | Follow/unfollow with quick-access tab | 6h |
| 14 | Saved collection for later browsing | 6h |

---

## Milestone 2: Core Customer Experience
**Modules: Browse & Discovery (186h) + Menu System (126h) = 312h | £23,400**

### Browse & Discovery — 186h

| # | Task | Hours |
|---|------|-------|
| 1 | Curated personalised restaurant feed frontend (rendering personalised ranking display, A/B test integration) | 32h |
| 2 | "Previously ordered" section | 6h |
| 3 | "Popular near you" / "Trending" sections | 12h |
| 4 | "New on platform" section | 4h |
| 5 | Shortcuts to recent/favourite restaurants | 6h |
| 6 | Promotional banners & daily deals carousel | 8h |
| 7 | Cuisine category tiles (horizontal scroll) | 8h |
| 8 | Restaurant list view + grid/thumbnail toggle | 10h |
| 9 | Quick-filter chips (open now, under 30 min, rating 4+) | 8h |
| 10 | Sort: nearest, top rated, delivery time | 8h |
| 11 | Filter: dietary, calorie range, service type | 10h |
| 12 | Restaurant card: hours, distance, ETA, fee, min order, promo badge, rating | 12h |
| 13 | Entity search (restaurant, cuisine, dish, grocery, store) | 16h |
| 14 | Search within a restaurant menu | 6h |
| 15 | Search UX: autocomplete, recent searches, history | 10h |
| 16 | Dietary preference search (vegan, halal, gluten-free, vegetarian) | 8h |
| 17 | Search by featured deal/promotion | 4h |
| 18 | Dedicated grocery tab with category browsing (dairy, produce, snacks) | 10h |
| 19 | Near-me auto-detect restaurants (geolocation) | 8h |

### Menu System — 126h

| # | Task | Hours |
|---|------|-------|
| 1 | Full menu listing with sticky category navigation | 10h |
| 2 | Item name, description, price, photo display | 8h |
| 3 | Pickup: browse restaurants/shops for pickup, select time slot | 6h |
| 4 | Pickup: order ahead, skip the line, pickup instructions for restaurant | 4h |
| 5 | Pickup: verification number, self-collect from partner stores | 4h |
| 6 | Pickup: no minimum order value, extra savings on grocery pickup, grocery support | 4h |
| 7 | Nutritional information display | 6h |
| 8 | Allergen information display | 6h |
| 9 | Popular item badge ("Bestseller" / "Popular") | 4h |
| 10 | Size variants (regular/large/family) | 8h |
| 11 | Toppings/extras selection (multi-select) | 8h |
| 12 | Required choices (doneness, sauce) | 6h |
| 13 | Single-select modifiers with price adjustment | 6h |
| 14 | Special instructions / notes field | 4h |
| 15 | Combo meal bundles | 10h |
| 16 | "Frequently bought together" cross-sell | 8h |
| 17 | Add-ons / upsell suggestions in menu | 4h |
| 18 | Item rating display + user-submitted photo reviews | 10h |
| 19 | Restaurant info section (address, hours, contact) + rating breakdown | 6h |
| 20 | Restaurant rating sub-scores (food quality, delivery, service) | 4h |

---

## Milestone 3: Cart, Checkout & Payments
**Modules: Cart (102h) + Checkout (130h) + Payment & Wallet (240h) = 472h | £35,400**

### Cart — 102h

| # | Task | Hours |
|---|------|-------|
| 1 | Add/remove/edit items with quantity control | 8h |
| 2 | Cart subtotal, delivery fee, service fee, tax | 10h |
| 3 | Small order fee, packaging fee line items | 4h |
| 4 | Promo/voucher code entry and validation | 8h |
| 5 | Auto-applied discounts (subscription, loyalty) | 6h |
| 6 | Strikethrough pricing display (was/now) | 4h |
| 7 | Happy hour discount engine (time-based pricing) | 6h |
| 8 | BOGO (buy-one-get-one) deal logic | 4h |
| 9 | Weekly promotional mechanics (Fresh Days / Fresh Tuesdays) | 4h |
| 10 | Surprise reward mechanics (post-purchase, auto-applied next checkout) | 4h |
| 11 | Free delivery threshold indicator | 4h |
| 12 | Minimum order requirement enforcement | 4h |
| 13 | Item availability check at checkout | 6h |
| 14 | Out-of-stock management + cancellation-triggered intelligent substitution suggestion | 8h |
| 15 | Item substitution flow (grocery) | 8h |
| 16 | Cross-contamination note display | 4h |
| 17 | Save cart for later | 6h |
| 18 | Cart upsell placement (before checkout) | 4h |

### Checkout — 130h

| # | Task | Hours |
|---|------|-------|
| 1 | Address input with Google Places autocomplete | 10h |
| 2 | Pinpoint on map with drag-to-refine | 8h |
| 3 | Delivery instructions (note to driver) | 4h |
| 4 | Contactless delivery toggle | 4h |
| 5 | Scheduled delivery (up to 7 days) + ASAP option | 10h |
| 6 | Pickup time selection | 4h |
| 7 | Service type toggle (delivery / pickup) | 6h |
| 8 | Address geocoding validation | 6h |
| 9 | Priority/long-range delivery fee calculation (dynamic distance/demand/priority algorithm) | 10h |
| 10 | Payment method selection (saved cards, wallet, cash) | 10h |
| 11 | Card tokenisation (add new card via Stripe/3DS) | 12h |
| 12 | Digital wallet selection (Apple Pay, Google Pay, PayPal) | 10h |
| 13 | Cash on delivery toggle | 4h |
| 14 | Gift card redemption at checkout | 6h |
| 15 | Split payment selection | 8h |
| 16 | Itemised order summary + receipt | 6h |
| 17 | Tip selection (%, fixed, custom) | 6h |
| 18 | Order note + cutlery opt-in | 2h |
| 19 | Checkout for someone else | 4h |

### Payment & Wallet — 240h

| # | Task | Hours |
|---|------|-------|
| 1 | PCI DSS compliant payment processing setup | 20h |
| 2 | Credit/debit card processing (Visa, MC, Amex, Discover) | 16h |
| 3 | Digital wallet integration (Apple Pay, Google Pay, PayPal) | 16h |
| 4 | Venmo, Klarna, Afterpay BNPL integration | 12h |
| 5 | EU payment methods (SEPA, iDEAL, Bancontact, Sofort) | 12h |
| 6 | WeChat Pay, Alipay, GrabPay integration | 10h |
| 7 | Digital wallet (pre-load funds, wallet balance analogue) | 14h |
| 8 | Earn/spend wallet logic (credits, cashback) | 10h |
| 9 | Wallet-to-card transfer (select markets) | 8h |
| 10 | Card tokenisation + saved cards management | 10h |
| 11 | 3D Secure authentication flow | 8h |
| 12 | Gift card system (digital + physical, custom amount $5-$500, cross-platform rides + Eats) | 14h |
| 13 | Gift card: custom designs per occasion, personal message, bulk corporate portal (10+) | 10h |
| 14 | Gift card redemption (16-digit code to wallet) + no expiry + currency restrictions | 6h |
| 15 | Promo/voucher code engine (creation, validation, auto-apply, stackability rules) | 14h |
| 16 | Voucher terms & conditions, expiry tracking, third-party sources (RetailMeNot) | 6h |
| 17 | Refund engine: full, partial, to original method or in-app credit | 10h |
| 18 | Transaction receipts (email) + invoice download | 4h |
| 19 | Payment history view | 4h |
| 20 | Multi-acquirer processing support (Visa, MC, Amex, PayPal, Klarna, Afterpay) | 8h |
| 21 | Refund policy engine — free cancellation window, post-acceptance charges, in-app credit vs cash rules per market | 8h |
| 22 | Card on delivery (offline payment, select markets) | 4h |
| 23 | Auto-payment on delivery confirmation (trigger charge on delivery completion) | 4h |
| 24 | Fiserv + Cybersource payment processing & tokenisation integration | 8h |
| 25 | Single-click reorder payment (one-tap payment using saved card, bypasses full checkout flow) | 4h |

---

## Milestone 4: Order Management & Tracking
**Modules: Order Tracking & Notifications (140h) + Group Ordering (112h) = 252h | £18,900**

### Order Tracking & Notifications — 140h

| # | Task | Hours |
|---|------|-------|
| 1 | Order placed confirmation screen | 4h |
| 2 | Multi-step order progress bar (placed → accepted → preparing → ready → picked up → delivered) | 8h |
| 3 | Real-time order status updates via WebSocket | 12h |
| 4 | Push notifications at each status change | 10h |
| 5 | Delivery person live location on map (GPS + WebSocket + battery-efficient polling) | 20h |
| 6 | ETA countdown with dynamic recalculation | 8h |
| 7 | Live map with route polyline + restaurant/destination markers | 12h |
| 8 | Share trip progress with friends/family | 6h |
| 9 | In-app call masking (contact delivery person) | 6h |
| 10 | View as delivery person feature (privacy transparency) | 6h |
| 11 | Post-delivery: delivered confirmation, photo proof, rate driver, tip | 10h |
| 12 | Order notification system (push, SMS, email) | 10h |
| 13 | Promotional notification engine (personalised deals, flash sales, seasonal campaigns) | 8h |
| 14 | Abandoned cart push reminder | 4h |
| 15 | Re-engagement push for inactive users | 4h |
| 16 | In-app notification centre | 8h |
| 17 | Scheduled order reminder | 4h |

### Group Ordering — 112h

| # | Task | Hours |
|---|------|-------|
| 1 | Invite link sharing (WhatsApp, Messenger, SMS, email) | 8h |
| 2 | Web-based group order flow (no app needed for participants to add items) | 12h |
| 3 | Each participant orders from own device (real-time sync) | 14h |
| 4 | Host pays mode (host pays on behalf of group) | 6h |
| 5 | Guest pay mode (each participant pays for their own items) | 8h |
| 6 | Payment split with manual coordination UI | 10h |
| 7 | Spending limit per participant (host-set cap) | 6h |
| 8 | Order deadline set by host (auto-submit on expiry) | 8h |
| 9 | Lock order (host prevents further edits before submitting) | 4h |
| 10 | Real-time order tracking per participant | 8h |
| 11 | Recurring group order (save group for weekly/routine orders) | 8h |
| 12 | Group order session management (max 18 participants, restaurant only) | 8h |
| 13 | B2B corporate invoicing & recurring office lunch scheduling (corporate accounts, invoice generation, recurring order schedules) | 12h |

---

## Milestone 5: Merchant Tools
**Modules: Merchant Dashboard Web (288h) + Merchant Order Management (160h) = 448h | £33,600**

### Merchant Dashboard Web — 288h

| # | Task | Hours |
|---|------|-------|
| 1 | Sales overview dashboard (daily/weekly/monthly) | 14h |
| 2 | Real-time order feed with status badges | 10h |
| 3 | Menu management: add/edit/remove items, categories, modifiers | 16h |
| 4 | Bulk menu upload (CSV/XLSX) | 10h |
| 5 | Menu sync via API | 8h |
| 6 | Price update + AI-enhanced food photos | 8h |
| 7 | Set menu availability hours + holiday closure schedule | 6h |
| 8 | Item-level availability toggle (real-time stock) | 8h |
| 9 | Set delivery radius + regular/holiday hours | 6h |
| 10 | Performance analytics: top sellers, slow movers | 12h |
| 11 | Customer insights: ordering behaviour, trends, retention | 12h |
| 12 | Revenue reports + peak hours analysis | 10h |
| 13 | Payouts view: balance, payment history, earnings breakdown | 10h |
| 14 | Marketing campaign performance metrics | 8h |
| 15 | Ad performance metrics (Ads Manager) | 10h |
| 16 | Scheduled reporting (automated KPI reports via email) | 8h |
| 17 | Customer groups data (geographic segmentation) | 8h |
| 18 | New vs returning customer segmentation | 6h |
| 19 | Pricing recommendations tool | 8h |
| 20 | Store info management (address, pickup instructions, contact) | 8h |
| 21 | Staff-facing stock visibility dashboard (real-time remaining counts per item, kitchen/admin view) | 6h |
| 22 | Restaurant close reminder (list out-of-stock items, prompt re-enable next day) | 6h |
| 23 | Commission & fee plan management (Lite 20%, Plus 25%, Premium 30%, pickup 7%, custom rates, regional rules) | 20h |
| 24 | Transparent fee breakdown display on merchant reports | 4h |
| 25 | Merchant financial portal (financing partnerships, working capital programmes) | 10h |
| 26 | Chargeback dispute process UI (view, respond, track) | 4h |
| 27 | Marketplace: catalog integration via API/SFTP | 8h |
| 28 | Marketplace: real-time inventory sync | 6h |
| 29 | Marketplace: retail returns flow management (eligibility, courier pickup, instant refund) | 4h |
| 30 | Marketplace: fashion/grocery category support | 4h |
| 31 | Dark kitchen / virtual restaurant onboarding & management (delivery-only brand creation, kitchen network management) | 10h |
| 32 | Customer claims transparency dashboard & reviews-based recommendations | 8h |
| 33 | Merchant performance benchmarking vs peers | 6h |
| 34 | Merchant notification preferences — configure alerts for store status, connectivity, POS issues, cancellations, missed/inaccurate orders | 6h |

### Merchant Order Management — 160h

| # | Task | Hours |
|---|------|-------|
| 1 | Incoming order queue with sound alert | 10h |
| 2 | Accept/decline order with reason selection | 8h |
| 3 | Mark order as preparing → ready | 6h |
| 4 | Estimated preparation time update | 6h |
| 5 | Alert nearby delivery people when order ready | 8h |
| 6 | Delay order with ETA update to customer | 6h |
| 7 | Cancel order (by merchant) with reason + propagate to customer | 8h |
| 8 | Item availability toggle (out-of-stock in real-time) | 6h |
| 9 | View order notes + customer special instructions | 4h |
| 10 | Live Order Chat between merchant and customer | 12h |
| 11 | Track delivery person in real-time (map view) | 10h |
| 12 | View delivery person contact info + wait time | 6h |
| 13 | Incoming + scheduled order management view | 8h |
| 14 | Print order receipt (auto-print config per merchant) | 8h |
| 15 | Tablet-based responsive UI (iPad/Android tablet) | 12h |
| 16 | Training guide / in-app how-to | 4h |
| 17 | Order history with search/filter | 8h |
| 18 | KDS (Kitchen Display System) web view | 10h |
| 19 | POS Integration — two-way sync with restaurant POS systems (order push, status sync, menu sync) | 20h |

---

## Milestone 6: Rider App
**Module: Rider App (374h) | £28,050**

### Rider App — 374h

| # | Task | Hours |
|---|------|-------|
| 1 | Rider registration: document upload (ID, licence, vehicle insurance) | 12h |
| 2 | Identity verification + background check integration | 8h |
| 3 | Vehicle registration (bicycle, scooter, car, motorbike, walker) | 8h |
| 4 | Minimum age / SSN / Fair Chance Act compliance checks | 4h |
| 5 | Go online/offline toggle | 6h |
| 6 | Zone/area selection | 6h |
| 7 | Session start confirmation + end summary | 8h |
| 8 | Break mode + auto-logout after inactivity | 6h |
| 9 | Incoming order request (notification + sound) | 8h |
| 10 | Order details: merchant name, customer address, distance, earnings | 8h |
| 11 | Accept/decline with auto-accept timer | 8h |
| 12 | Order queue (multiple orders, batched courier offers) | 10h |
| 13 | Travel time / navigation start confirmation | 6h |
| 14 | In-app turn-by-turn navigation (Google Maps SDK) | 14h |
| 15 | Google Maps / Waze deep link integration | 6h |
| 16 | Optimised route suggestion (multi-order) | 10h |
| 17 | Real-time traffic data integration | 6h |
| 18 | Order pickup confirmation + item verification screen (QR code / photo) | 12h |
| 19 | Navigate to customer | 4h |
| 20 | Delivery confirmation + proof of delivery (photo) | 8h |
| 21 | "Leave at door" photo capture | 6h |
| 22 | Call customer (in-app call masking) | 6h |
| 23 | Message customer (in-app chat) | 8h |
| 24 | Contact support during delivery | 4h |
| 25 | Return order flow (if delivery fails) | 8h |
| 26 | Earnings view: per-trip breakdown (base, distance, time, surge, boost, quest, tip — real-time) | 12h |
| 27 | Daily/weekly earnings summary + monthly report | 8h |
| 28 | Surge pricing + boost promotion earnings display | 8h |
| 29 | Quest incentives (X deliveries = bonus) tracking | 8h |
| 30 | Instant pay / on-demand payout | 8h |
| 31 | Weekly direct deposit setup | 6h |
| 32 | Safety toolkit: audio recording, share trip with trusted contact, emergency button | 12h |
| 33 | 12-hour daily driving limit enforcement + countdown notifications | 6h |
| 34 | Uber Eats Pro Programme (4-tier: Green/Gold/Platinum/Diamond, criteria config, progress tracker, hub, rewards, evaluation engine, seasonal resets) | 22h |
| 35 | Refer-a-friend programme with tracking dashboard | 8h |
| 36 | Help centre + driver community forums | 6h |
| 37 | Rider equipment ordering portal | 4h |
| 38 | Trip planner at pickup — batch/multi-order route management | 6h |
| 39 | Cross-zone delivery support | 4h |
| 40 | Extended delivery opt-in (longer-distance orders) | 2h |
| 41 | Shift allocation / schedule booking system | 6h |
| 42 | Score-based scheduling (performance affects shift access) | 4h |
| 43 | Siri Shortcuts integration (call customer, go online, earnings) | 4h |
| 44 | Safety: Aura on-demand emergency response platform integration | 6h |
| 45 | Safety: Predictive risk prevention (telematics data, motion-based risk signals) | 6h |
| 46 | Safety: PPE distribution partnerships / helmet initiatives / safety kits | 4h |
| 47 | Streamlined single drop-off flow | 4h |
| 48 | Drop-off problem resolution screen | 4h |
| 49 | Proof of delivery via QR code (alternative to photo) | 4h |
| 50 | Rider compliance page (penalties, fines, demerit points) | 4h |
| 51 | Traffic rule refreshers + e-bike compliance guidelines in-app | 4h |
| 52 | New joiner fee / referral fee information pages | 2h |
| 53 | Training completion tracking | 4h |
| 54 | Rider insurance enrolment flow | 4h |
| 55 | Tax information submission | 4h |

---

## Milestone 7: Admin & Subscriptions
**Modules: Admin & Operations Console (286h) + Subscriptions & Loyalty (104h) = 390h | £29,250**

### Admin & Operations Console — 286h

| # | Task | Hours |
|---|------|-------|
| 1 | User management (merchants, riders, customers, admins) | 12h |
| 2 | Merchant onboarding workflow + approval process | 14h |
| 3 | RBAC system (admin, merchant admin, staff, support) | 12h |
| 4 | In-app advertising platform: sponsored listings, promoted cards, banner ads, carousel banners | 20h |
| 5 | Deal Drops (time-bound promotional offers with inventory caps, scarcity, push alerts) | 12h |
| 6 | Journey Ads (cross-platform in-ride advertising) | 10h |
| 7 | Self-serve Ads Manager for merchants (campaign creation, budget, performance) | 14h |
| 8 | Audience builder + segmentation tools | 12h |
| 9 | Campaign performance analytics + ROAS measurement | 10h |
| 10 | A/B testing framework (assignment logic, split testing, statistical engine, results dashboard) | 20h |
| 11 | Customer acquisition cost tracking | 6h |
| 12 | Customer lifetime value modelling | 8h |
| 13 | Business intelligence reporting dashboard | 12h |
| 14 | Support ticket system + escalation workflow | 10h |
| 15 | Operations dashboard (incident monitoring, health checks) | 8h |
| 16 | Off-App Advertising platform — programmatic display, OTT/CTV, music streaming, in-game ads | 12h |
| 17 | Email marketing campaign engine (templates, segmentation, delivery, analytics, A/B subject lines) | 16h |
| 18 | Advanced ad targeting — lookalike modelling, demographic, behavioural, first-party data | 10h |
| 19 | Brand lift studies & incrementality testing framework | 6h |
| 20 | Data collaboration platform / clean room integration (LiveRamp-style, privacy-compliant) | 12h |
| 21 | Audience builder & media kit generator for advertisers | 8h |
| 22 | Ad privacy controls dashboard (personalised ads opt-out, unified preferences) | 4h |
| 23 | Merchant onboarding expansion — dedicated account manager tier, virtual restaurant creation, certified programme | 8h |
| 24 | SmartShoot professional food photography integration + premium photo shoot package | 4h |
| 25 | Merchant marketing tools — co-marketing, joint brand partnerships, success stories, insights hub, merchant awards | 8h |
| 26 | Customer engagement admin — UGC programme management, review moderation | 4h |
| 27 | Ibotta Performance Network digital coupon integration | 6h |
| 28 | Cross-platform marketing programmes — bundled offers (ride + meal), Eats for the Way, Expedia hotel partnership | 8h |

### Subscriptions & Loyalty — 104h

| # | Task | Hours |
|---|------|-------|
| 1 | Subscription plans: monthly/annual pricing tiers | 8h |
| 2 | Free trial period (1 month for new subscribers) | 6h |
| 3 | Student discount programme (50% off) | 4h |
| 4 | Auto-renewal with payment failure retry + grace period | 8h |
| 5 | Cancel anytime (effective next billing) with 48-hour notice | 6h |
| 6 | Subscription benefits engine ($0 delivery fee, % off, priority placement, service fee discount) | 12h |
| 7 | Variable order minimum per merchant (dynamic rule engine) | 8h |
| 8 | Member Days calendar/schedule (periodic savings events) | 6h |
| 9 | Family sharing (add one additional member at no cost) | 8h |
| 10 | Credit card partnership integrations (Delta, Chase, Marriott, Kroger) | 10h |
| 11 | Points-based loyalty programme (earn points per order, redeem on platform) | 10h |
| 12 | Tiered loyalty rewards (basic → premium tiers) | 8h |
| 13 | Referral programme (give X, get X) with tracking dashboard | 6h |
| 14 | Uber One credits earned/expiring view (balance, expiry tracker) | 4h |

---

## Milestone 8: Advanced Features
**Modules: AI & Personalisation Engine (260h) + WhatsApp Integration (88h) = 348h | £26,100**

### AI & Personalisation Engine — 260h

| # | Task | Hours |
|---|------|-------|
| 1 | AI-powered personalised restaurant feed ML pipeline (collaborative + content-based filtering, cold start optimisation, A/B evaluation framework, model training pipeline) | 32h |
| 2 | Predictive reordering (based on order history + contextual signals — ML pipeline) | 24h |
| 3 | AI side dish / upsell suggestion (based on real order combination data, toggle per restaurant, revenue impact tracking shown on merchant dashboard) | 14h |
| 4 | Multi-dimensional context engine (time, weather, past orders, family preferences, loyalty balance, courier availability) | 18h |
| 5 | AI assistant prompt: "Would you like your usual…?" with smart group ordering (multi-context prompt generation + interaction flow) | 20h |
| 6 | AI dynamic pricing (demand-based surge — time-series modelling) | 20h |
| 7 | AI demand forecasting for merchants (ML forecast pipeline, historical + seasonal) | 20h |
| 8 | AI route optimisation for riders (VROPTW solver, multi-stop routing) | 30h |
| 9 | Voice & chat ordering (natural language parsing, free-form order extraction, scan order) | 24h |
| 10 | AI chatbot for customer support (NLU, fallback, escalation, context-aware) | 24h |
| 11 | AI quality control (order accuracy anomaly detection, outlier flagging) | 6h |
| 12 | AI Voice Agent Flow — conversational AI agent for full ordering flow (wake word, multi-turn dialogue, confirm/cancel, integration with cart and checkout) | 12h |
| 13 | Nutrition/macro auto-tracking & fitness goal integration (auto-calculate calories/macros from orders, link to fitness goals, dietary target tracking) | 16h |

### WhatsApp Integration — 88h

| # | Task | Hours |
|---|------|-------|
| 1 | WhatsApp Business API setup + Meta business verification + webhook signature verification (approval process, template setup) | 20h |
| 2 | QR code generation (table, menu, window, packaging) → opens WhatsApp with pre-filled message | 8h |
| 3 | Click-to-WhatsApp button on website | 4h |
| 4 | Single Biteo number: direct message entry point (Facebook, Instagram, TikTok, Google ads → WhatsApp) | 8h |
| 5 | WhatsApp menu browsing flow (interactive message menus) | 14h |
| 6 | WhatsApp ordering flow (add items, confirm, payment link, scan order) | 14h |
| 7 | Voice-recorded order via WhatsApp (audio → speech-to-text → order parsing) | 12h |
| 8 | Order confirmation + real-time status updates via WhatsApp | 8h |

---

## Summary

| Milestone | Modules | Hours | Cost (£75/hr) | 50% Advance | 50% on Completion |
|-----------|---------|-------|--------------|-------------|-------------------|
| **M1** | Auth & Profile + Customer Account | 216h | £16,200 | £8,100 | £8,100 |
| **M2** | Browse & Discovery + Menu System | 312h | £23,400 | £11,700 | £11,700 |
| **M3** | Cart + Checkout + Payment & Wallet | 472h | £35,400 | £17,700 | £17,700 |
| **M4** | Order Tracking & Notifications + Group Ordering | 252h | £18,900 | £9,450 | £9,450 |
| **M5** | Merchant Dashboard Web + Merchant Order Mgmt | 448h | £33,600 | £16,800 | £16,800 |
| **M6** | Rider App | 374h | £28,050 | £14,025 | £14,025 |
| **M7** | Admin & Operations Console + Subscriptions & Loyalty | 390h | £29,250 | £14,625 | £14,625 |
| **M8** | AI & Personalisation Engine + WhatsApp Integration | 348h | £26,100 | £13,050 | £13,050 |
| **Total** | **16 modules** | **2,812h** | **£210,900** | **£105,450** | **£105,450** |

### QA Audit Change Summary

| Check | Result | What Was Fixed |
|-------|--------|----------------|
| 1. All v2 features exist in v3 | **PASS** | Restored 12 missing features (+86h) + 64 absorbed as existing-task notes (52 from Round 3 final audit) |
| 2. No extras beyond v2 | **PASS** | No v2-absent features added |
| 3. Time estimates realistic | **PASS** | Adjusted 8 underestimates (+42h) |
| 4. Milestone grouping logical | **PASS** | All 8 milestones retained — M3 grouping justified (coupled modules) |
| 5. Task ordering correct | **PASS** | Reordered 3 modules (Menu System: pickup earlier; Cart: promos with discounts; Customer Account: UGC after reviews) |
| 6. No duplicates/contradictions | **PASS** | Merged 3 duplicate pairs (−8h), fixed systematic arithmetic errors across 10 modules (+300h cumulative) |
| 7. Round 3 final independent audit | **PASS** | 14 more minor features absorbed (+52 total), arithmetic corrections reconciled (+300h cumulative) |
| 8. Round 4 final independent audit | **PASS** | Fixed v2:793,807→v2:790 ref error; 6 more minor features absorbed (+58 total) |
| 9. Round 5 final independent audit | **PASS** | 5 more minor features absorbed (v2:502,503,524,614,820) — all absorbable, no new tasks needed (+63 total) |
| 10. Round 6 — final independent audit | **PASS** | Absorbed v2:726 into M7 Admin #4 (+64 total); distinguished M2 Browse #1 frontend vs M8 AI #1 ML pipeline descriptions; fixed stale merge refs (v3:48); corrected QA count (54→52) |

---

*End of document — v3 contains **2,812 task hours** across **16 modules** and **8 payment milestones**. All v2 features audited, gaps closed, estimates corrected, duplicates resolved.*
