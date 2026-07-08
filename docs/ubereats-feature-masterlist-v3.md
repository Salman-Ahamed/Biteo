# Uber Eats Feature Masterlist — v3 (Client Proposal)

## Milestone 0: Project Setup

| # | Task | Est. Time |
|---|------|-----------|
| 1 | Repository setup and monorepo configuration | 4h |
| 2 | Development environment and Docker setup | 6h |
| 3 | CI/CD pipeline setup (GitHub Actions, EAS Build) | 8h |
| 4 | Cloud infrastructure provisioning (AWS/GCP) | 8h |
| 5 | Database schema design and migration framework | 8h |
| 6 | Authentication service integration (Clerk) | 6h |
| 7 | API framework, routing, and middleware setup | 6h |
| 8 | Mobile app shell (Expo/React Native) | 6h |
| 9 | Monitoring, logging, and error tracking | 4h |
| 10 | Third-party service integrations scaffolding | 4h |
|    | **Subtotal** | **60h** |

---

## Milestone 1: Merchant & Rider

### Merchant Dashboard Web

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **288h** |

### Merchant Order Management

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **160h** |

### Rider App

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **374h** |

---

## Milestone 2: Frontend Customer Experience

### Auth & Profile

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **120h** |

### Customer Account

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **96h** |

### Browse & Discovery

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **186h** |

### Menu System

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **126h** |

---

## Milestone 3: Core Transaction Flow

### Cart

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **102h** |

### Checkout

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **130h** |

### Payment & Wallet

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **240h** |

### Order Tracking & Notifications

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **140h** |

### Group Ordering

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **112h** |

---

## Milestone 4: Admin & Advanced Features

### Admin & Operations Console

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **286h** |

### Subscriptions & Loyalty

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **104h** |

### AI & Personalisation Engine

| # | Task | Est. Time |
|---|------|-----------|
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
|    | **Subtotal** | **260h** |

### WhatsApp Integration

| # | Task | Est. Time |
|---|------|-----------|
| 1 | WhatsApp Business API setup + Meta business verification + webhook signature verification (approval process, template setup) | 20h |
| 2 | QR code generation (table, menu, window, packaging) → opens WhatsApp with pre-filled message | 8h |
| 3 | Click-to-WhatsApp button on website | 4h |
| 4 | Single Biteo number: direct message entry point (Facebook, Instagram, TikTok, Google ads → WhatsApp) | 8h |
| 5 | WhatsApp menu browsing flow (interactive message menus) | 14h |
| 6 | WhatsApp ordering flow (add items, confirm, payment link, scan order) | 14h |
| 7 | Voice-recorded order via WhatsApp (audio → speech-to-text → order parsing) | 12h |
| 8 | Order confirmation + real-time status updates via WhatsApp | 8h |
|    | **Subtotal** | **88h** |

---

## Payment Milestones

| Milestone | Advance (50%) | Completion (50%) | Total |
|-----------|---------------|------------------|-------|
| 0. Project Setup | $2,250 | $2,250 | $4,500 |
| 1. Merchant & Rider | $30,825 | $30,825 | $61,650 |
| 2. Frontend Customer Experience | $19,800 | $19,800 | $39,600 |
| 3. Core Transaction Flow | $27,150 | $27,150 | $54,300 |
| 4. Admin & Advanced Features | $27,675 | $27,675 | $55,350 |
| **Total** | **$107,700** | **$107,700** | **$215,400** |

## Grand Total Time: 2,872 hours
