# Uber Eats Feature Masterlist v3 — Implementation Breakdown

**Date:** July 2026
**Rate:** £75/hr (blended senior/mid UK rate)
**Total Est. Hours:** 2,512h
**Total Est. Cost:** £188,400

---

## Audit Report — v2 → v3 Corrections

### Missing Features Restored
| v2 Feature | v3 Task Added | Hours |
|------------|--------------|-------|
| AI Voice Agent Flow (v2:25) | M8 AI Engine — new task: conversational AI voice agent for ordering | 12h |
| Card on delivery (v2:1042) | M3 Payment — new task: card payment on delivery | 4h |
| Ibotta Performance Network (v2:1168) | M7 Admin — new task: digital coupon network integration | 6h |
| Cross-platform gift card (v2:357) | M3 Payment — merged into gift card task (rides + Eats) | — |
| Uber One credits earned/expiring (v2:339) | M7 Subscriptions — new task: credits balance & expiry tracker | 4h |
| Cross-platform marketing: bundled offers, Eats for the Way, Expedia (v2:1201-1209) | M7 Admin — new task: cross-platform marketing programmes | 8h |

### Time Estimate Corrections
| Task | Old | New | Δ |
|------|-----|-----|---|
| AI personalised restaurant feed | 14h | 24h | +10h |
| Predictive reordering | 16h | 24h | +8h |
| AI dynamic pricing | 12h | 20h | +8h |
| AI demand forecasting | 10h | 20h | +10h |
| AI route optimisation | 12h | 30h | +18h |
| Voice & chat ordering (NLP) | 14h | 24h | +10h |
| AI chatbot support | 10h | 24h | +14h |
| Email marketing campaign engine | 8h | 16h | +8h |
| A/B testing framework | 10h | 20h | +10h |
| Data collaboration/clean room | 6h | 12h | +6h |

### Structural Corrections
| Change | Detail |
|--------|--------|
| Pickup features moved | From M3 Checkout → M2 Menu System (more natural grouping) |
| Ad privacy controls moved | From M1 Auth → M7 Admin (operational concern) |
| Milestones | No split — M3 maintained as-is; all three modules are tightly coupled at checkout |

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
| 5 | Invoice/receipt view and download | 6h |
| 6 | Order cancellation flow (before preparation) | 8h |
| 7 | Refund status tracking display | 6h |
| 8 | Report an issue flow (categories, attachment) | 8h |
| 9 | Favourite restaurants/dishes/stores list | 8h |
| 10 | Follow/unfollow with quick-access tab | 6h |
| 11 | Saved collection for later browsing | 6h |
| 12 | UGC programme — food photo requests for un-imaged menu items | 6h |
| 13 | In-order feedback prompts (per-item rating, Dish-out style) | 6h |
| 14 | UGC moderation tools (flag, approve, hide) | 4h |

---

## Milestone 2: Core Customer Experience
**Modules: Browse & Discovery (160h) + Menu System (120h) = 280h | £21,000**

### Browse & Discovery — 160h

| # | Task | Hours |
|---|------|-------|
| 1 | Curated personalised restaurant feed | 16h |
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

### Menu System — 120h

| # | Task | Hours |
|---|------|-------|
| 1 | Full menu listing with sticky category navigation | 10h |
| 2 | Item name, description, price, photo display | 8h |
| 3 | Nutritional information display | 6h |
| 4 | Allergen information display | 6h |
| 5 | Popular item badge ("Bestseller" / "Popular") | 4h |
| 6 | Size variants (regular/large/family) | 8h |
| 7 | Toppings/extras selection (multi-select) | 8h |
| 8 | Required choices (doneness, sauce) | 6h |
| 9 | Single-select modifiers with price adjustment | 6h |
| 10 | Special instructions / notes field | 4h |
| 11 | Combo meal bundles | 10h |
| 12 | "Frequently bought together" cross-sell | 8h |
| 13 | Add-ons / upsell suggestions in menu | 4h |
| 14 | Item rating display + user-submitted photo reviews | 10h |
| 15 | Restaurant info section (address, hours, contact) + rating breakdown | 6h |
| 16 | Restaurant rating sub-scores (food quality, delivery, service) | 4h |
| 17 | Pickup: browse restaurants/shops for pickup, select time slot | 6h |
| 18 | Pickup: order ahead, skip the line, pickup instructions for restaurant | 4h |
| 19 | Pickup: verification number, self-collect from partner stores | 4h |
| 20 | Pickup: no minimum order value, extra savings on grocery pickup, grocery support | 4h |

---

## Milestone 3: Cart, Checkout & Payments
**Modules: Cart (96h) + Checkout (120h) + Payment & Wallet (172h) = 388h | £29,100**

### Cart — 96h

| # | Task | Hours |
|---|------|-------|
| 1 | Add/remove/edit items with quantity control | 8h |
| 2 | Cart subtotal, delivery fee, service fee, tax | 10h |
| 3 | Small order fee, packaging fee line items | 4h |
| 4 | Promo/voucher code entry and validation | 8h |
| 5 | Auto-applied discounts (subscription, loyalty) | 6h |
| 6 | Free delivery threshold indicator | 4h |
| 7 | Minimum order requirement enforcement | 4h |
| 8 | Item availability check at checkout | 6h |
| 9 | Out-of-stock management (substitution suggestion) | 8h |
| 10 | Item substitution flow (grocery) | 8h |
| 11 | Cross-contamination note display | 4h |
| 12 | Save cart for later | 6h |
| 13 | Cart upsell placement (before checkout) | 4h |
| 14 | Strikethrough pricing display (was/now) | 4h |
| 15 | Happy hour discount engine (time-based pricing) | 6h |
| 16 | BOGO (buy-one-get-one) deal logic | 4h |
| 17 | Weekly promotional mechanics (Fresh Days / Fresh Tuesdays) | 4h |
| 18 | Surprise reward mechanics (post-purchase, auto-applied next checkout) | 4h |

### Checkout — 120h

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
| 9 | Priority/long-range delivery fee calculation | 6h |
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

### Payment & Wallet — 172h

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
| 20 | Multi-acquirer processing support | 8h |
| 21 | Refund policy engine — free cancellation window, post-acceptance charges, in-app credit vs cash rules per market | 8h |
| 22 | Card on delivery (offline payment, select markets) | 4h |

---

## Milestone 4: Order Management & Tracking
**Modules: Order Tracking & Notifications (120h) + Group Ordering (100h) = 220h | £16,500**

### Order Tracking & Notifications — 120h

| # | Task | Hours |
|---|------|-------|
| 1 | Order placed confirmation screen | 4h |
| 2 | Multi-step order progress bar (placed → accepted → preparing → ready → picked up → delivered) | 8h |
| 3 | Real-time order status updates via WebSocket | 12h |
| 4 | Push notifications at each status change | 10h |
| 5 | Delivery person live location on map (WebSocket + GPS) | 16h |
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

### Group Ordering — 100h

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

---

## Milestone 5: Merchant Tools
**Modules: Merchant Dashboard Web (244h) + Merchant Order Management (160h) = 404h | £30,300**

### Merchant Dashboard Web — 244h

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
| 23 | Commission & fee plan management (Lite 20%, Plus 25%, Premium 30%, pickup 7%, custom rates) | 12h |
| 24 | Transparent fee breakdown display on merchant reports | 4h |
| 25 | Merchant financial portal (financing partnerships, working capital programmes) | 10h |
| 26 | Chargeback dispute process UI (view, respond, track) | 4h |
| 27 | Marketplace: catalog integration via API/SFTP | 8h |
| 28 | Marketplace: real-time inventory sync | 6h |
| 29 | Marketplace: retail returns flow management (eligibility, courier pickup, instant refund) | 4h |
| 30 | Marketplace: fashion/grocery category support | 4h |

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
**Module: Rider App (288h) | £21,600**

### Rider App — 288h

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
| 18 | Order pickup confirmation (QR code / photo verification) | 8h |
| 19 | Navigate to customer | 4h |
| 20 | Delivery confirmation + proof of delivery (photo) | 8h |
| 21 | "Leave at door" photo capture | 6h |
| 22 | Call customer (in-app call masking) | 6h |
| 23 | Message customer (in-app chat) | 8h |
| 24 | Contact support during delivery | 4h |
| 25 | Return order flow (if delivery fails) | 8h |
| 26 | Earnings view: per-trip breakdown (base, distance, time, tip) | 8h |
| 27 | Daily/weekly earnings summary + monthly report | 8h |
| 28 | Surge pricing + boost promotion earnings display | 8h |
| 29 | Quest incentives (X deliveries = bonus) tracking | 8h |
| 30 | Instant pay / on-demand payout | 8h |
| 31 | Weekly direct deposit setup | 6h |
| 32 | Safety toolkit: audio recording, share trip with trusted contact, emergency button | 12h |
| 33 | 12-hour daily driving limit enforcement + countdown notifications | 6h |
| 34 | Uber Eats Pro hub (tier display, progress tracker, points balance) | 14h |
| 35 | Refer-a-friend programme with tracking dashboard | 8h |
| 36 | Help centre + driver community forums | 6h |
| 37 | Rider equipment ordering portal | 4h |
| 38 | Uber Eats Pro Programme — 4-tier system (Green/Gold/Platinum/Diamond) with criteria config (acceptance rate, cancellation, satisfaction, on-time) and rewards | 12h |
| 39 | Tier evaluation engine — points earned per delivery, quarterly cycles, seasonal resets | 6h |
| 40 | Trip planner at pickup — batch/multi-order route management | 6h |
| 41 | Verification screen at pickup (item/order verification) | 4h |
| 42 | Cross-zone delivery support | 4h |
| 43 | Shift allocation / schedule booking system | 6h |
| 44 | Score-based scheduling (performance affects shift access) | 4h |
| 45 | Extended delivery opt-in (longer-distance orders) | 2h |
| 46 | Siri Shortcuts integration (call customer, go online, earnings) | 4h |
| 47 | Safety: Aura on-demand emergency response platform integration | 6h |
| 48 | Safety: Predictive risk prevention (telematics data, motion-based risk signals) | 6h |
| 49 | Safety: PPE distribution partnerships / helmet initiatives / safety kits | 4h |
| 50 | Streamlined single drop-off flow | 4h |
| 51 | Drop-off problem resolution screen | 4h |
| 52 | Proof of delivery via QR code (alternative to photo) | 4h |
| 53 | Rider compliance page (penalties, fines, demerit points) | 4h |
| 54 | Traffic rule refreshers + e-bike compliance guidelines in-app | 4h |
| 55 | New joiner fee / referral fee information pages | 2h |

---

## Milestone 7: Admin & Subscriptions
**Modules: Admin & Operations Console (282h) + Subscriptions & Loyalty (104h) = 386h | £28,950**

### Admin & Operations Console — 282h

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
| 22 | **Ad privacy controls dashboard** (personalised ads opt-out, unified preferences — moved from M1) | 4h |
| 23 | Merchant onboarding expansion — dedicated account manager tier, virtual restaurant creation, certified programme | 8h |
| 24 | SmartShoot professional food photography integration + premium photo shoot package | 4h |
| 25 | Merchant marketing tools — co-marketing, joint brand partnerships, success stories, insights hub, merchant awards | 8h |
| 26 | Customer engagement admin — UGC programme management, review moderation | 4h |
| 27 | **Ibotta Performance Network digital coupon integration** | 6h |
| 28 | **Cross-platform marketing programmes** — bundled offers (ride + meal), Eats for the Way, Expedia hotel partnership | 8h |

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
| 14 | **Uber One credits earned/expiring view** (balance, expiry tracker) | 4h |

---

## Milestone 8: Advanced Features
**Modules: AI & Personalisation Engine (230h) + WhatsApp Integration (80h) = 310h | £23,250**

### AI & Personalisation Engine — 230h

| # | Task | Hours |
|---|------|-------|
| 1 | AI-powered personalised restaurant feed (collaborative + content-based filtering, heavy R&D) | 24h |
| 2 | Predictive reordering (based on order history + contextual signals — ML pipeline) | 24h |
| 3 | AI side dish / upsell suggestion (based on real order combination data, toggle per restaurant) | 12h |
| 4 | Multi-dimensional context engine (time, weather, past orders, family preferences, loyalty balance) | 18h |
| 5 | AI assistant prompt: "Would you like your usual…?" with smart group ordering | 16h |
| 6 | AI dynamic pricing (demand-based surge — time-series modelling) | 20h |
| 7 | AI demand forecasting for merchants (ML forecast pipeline, historical + seasonal) | 20h |
| 8 | AI route optimisation for riders (VROPTW solver, multi-stop routing) | 30h |
| 9 | Voice & chat ordering (natural language parsing, free-form order extraction, scan order) | 24h |
| 10 | AI chatbot for customer support (NLU, fallback, escalation, context-aware) | 24h |
| 11 | AI quality control (order accuracy anomaly detection, outlier flagging) | 6h |
| 12 | **AI Voice Agent Flow** — conversational AI agent for full ordering flow (wake word, multi-turn dialogue, confirm/cancel, integration with cart and checkout) | 12h |

### WhatsApp Integration — 80h

| # | Task | Hours |
|---|------|-------|
| 1 | WhatsApp Business API setup + webhook signature verification | 12h |
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
| **M2** | Browse & Discovery + Menu System | 280h | £21,000 | £10,500 | £10,500 |
| **M3** | Cart + Checkout + Payment & Wallet | 388h | £29,100 | £14,550 | £14,550 |
| **M4** | Order Tracking & Notifications + Group Ordering | 220h | £16,500 | £8,250 | £8,250 |
| **M5** | Merchant Dashboard Web + Merchant Order Mgmt | 404h | £30,300 | £15,150 | £15,150 |
| **M6** | Rider App | 288h | £21,600 | £10,800 | £10,800 |
| **M7** | Admin & Operations Console + Subscriptions & Loyalty | 386h | £28,950 | £14,475 | £14,475 |
| **M8** | AI & Personalisation Engine + WhatsApp Integration | 310h | £23,250 | £11,625 | £11,625 |
| **Total** | **16 modules** | **2,512h** | **£188,400** | **£94,200** | **£94,200** |

### Changes from Previous v3

| Metric | Previous | Updated | Δ |
|--------|----------|---------|---|
| Total hours | 2,356h | 2,512h | +156h |
| Total cost | £176,700 | £188,400 | +£11,700 |
| Missing features | 6 gaps | 0 gaps | +6 tasks |
| Unrealistic estimates | 10 tasks | 0 tasks | corrected |

### Feature Coverage Summary

| v2 Section | Status in v3 | Location |
|------------|-------------|----------|
| AI-Powered Personalisation | ✅ | M8 AI Engine |
| Predictive Reordering | ✅ | M8 AI Engine |
| Voice & Chat Ordering | ✅ | M8 AI Engine + M8 WhatsApp |
| AI Voice Agent Flow | ✅ Restored | M8 AI Engine |
| Group Ordering with Split Payments | ✅ | M4 Group Ordering |
| Dietary & Allergen Filtering | ✅ | M2 Browse & Discovery |
| AI Chatbot Support | ✅ | M8 AI Engine |
| Subscription & Loyalty Tiers | ✅ | M7 Subscriptions |
| Real-Time Step-by-Step Tracking | ✅ | M4 Order Tracking |
| AI demand forecasting / route optimisation / dynamic pricing / quality control | ✅ | M8 AI Engine |
| Kitchen display system / POS integration | ✅ | M5 Merchant Order Mgmt |
| WhatsApp QR entry + Click-to-WhatsApp | ✅ | M8 WhatsApp |
| Type 1 AI Upselling (side dish) | ✅ | M8 AI Engine |
| Type 2 Stock Visibility (staff-facing) | ✅ | M5 Merchant Dashboard |
| Entity Search + Search UX | ✅ | M2 Browse & Discovery |
| Browse & Feed (personalised, visuals, sort, filter, grocery) | ✅ | M2 Browse & Discovery |
| Menu + Customisation + Modifiers + Reviews | ✅ | M2 Menu System |
| Cart (fees, promos, availability) | ✅ | M3 Cart |
| Checkout (delivery, payment, scheduling) | ✅ | M3 Checkout |
| Pickup features | ✅ | M2 Menu System (moved) |
| Payment & Wallet (cards, digital wallets, gift cards, BNPL, SEPA) | ✅ | M3 Payment |
| Offline Payments (cash + card on delivery) | ✅ | M3 Payment |
| Promo Codes, Voucher System, Promo Mechanics | ✅ | M3 Cart + M3 Payment |
| Refund Policy | ✅ | M3 Payment |
| Customer Account (order history, favourites, reviews, UGC) | ✅ | M1 Customer Account |
| Auth + Profile + Address Book + Privacy Center | ✅ | M1 Auth & Profile |
| Real-Time Tracking (map, ETA, WebSocket) | ✅ | M4 Order Tracking |
| Notifications (order, promo, account, in-app centre) | ✅ | M4 Order Tracking |
| Group Ordering (invite, split, session management) | ✅ | M4 Group Ordering |
| Merchant Dashboard (sales, menu, analytics, payouts) | ✅ | M5 Merchant Dashboard |
| Merchant Order Management (accept/decline, KDS, POS) | ✅ | M5 Merchant Order Mgmt |
| Merchant Financial Access (commission, financing, chargebacks) | ✅ | M5 Merchant Dashboard |
| Rider App (reg, sessions, orders, navigation, earnings, delivery) | ✅ | M6 Rider App |
| Rider Safety Toolkit (audio, share trip, emergency, 12h limit) | ✅ | M6 Rider App |
| Uber Eats Pro Programme (4-tier, evaluation, rewards) | ✅ | M6 Rider App |
| Rider Referral | ✅ | M6 Rider App |
| In-App Advertising (sponsored, promoted, Deal Drops, Journey Ads) | ✅ | M7 Admin |
| Off-App Advertising (programmatic, OTT, in-game) | ✅ | M7 Admin |
| Targeting & Analytics (lookalike, clean room, brand lift) | ✅ | M7 Admin |
| Self-Serve Ads Manager | ✅ | M7 Admin |
| Merchant Onboarding & Support | ✅ | M7 Admin |
| Merchant Marketing | ✅ | M7 Admin |
| Cross-Platform Marketing (Journey Ads, bundled offers, Eats for the Way, Expedia) | ✅ | M7 Admin (restored) |
| Customer Engagement (UGC, notifications, live chat, in-order feedback) | ✅ | M1 Customer Account + M4 Order Tracking |
| Privacy & Controls (ad preferences opt-out, unified) | ✅ | M7 Admin (moved) |
| Subscriptions & Plans (tiers, benefits, partnerships) | ✅ | M7 Subscriptions |
| Loyalty Programme (points, tiers, referral, credit card partnerships) | ✅ | M7 Subscriptions |
| Uber One credits earned/expiring view | ✅ Restored | M7 Subscriptions |
| Cross-platform gift card (rides + Eats) | ✅ Restored | M3 Payment |
| Ibotta Performance Network | ✅ Restored | M7 Admin |
| Card on delivery (offline) | ✅ Restored | M3 Payment |

---

*End of document — v3 contains 2,512 task hours across 16 modules and 8 payment milestones. All v2 features audited and covered.*
