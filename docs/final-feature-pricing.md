# Biteo Phased Build & Pricing Plan

**Document purpose:** replace the raw feature masterlist with a dependency-ordered, modular build plan that can be delivered phase by phase.

**Pricing rule:** every hour is billed at **$30**.
**AI time:** AI-assisted delivery is assumed to be **5× faster** than manual delivery, so AI hours = manual hours ÷ 5.
**Two prices shown** for every feature: manual cost (if built without AI) and AI-assisted cost (the expected delivery price).

---

## How to read this document

- **Phase 1–2** are required before any pilot launch.
- **Phase 3** is the first major post-core feature set and includes the highlighted WhatsApp AI assistant, voice-recorded ordering, and scan order capabilities.
- **Phase 4** handles dispatch and live tracking using a React Native rider app plus a web dispatcher console.
- **Phase 5** adds growth, personalisation, and advanced AI.
- **Phase 6** adds scale features such as POS integrations, kitchen display system, and AI-driven tools.

---

## Phase 1 — Platform Foundation & Core Order Flow

**Goal:** a live, trust-first direct-ordering backbone. Every later phase depends on this.
**Duration estimate:** 8–10 weeks.

### 1.1 Backend / Server Core

| Feature / Sub-task                                    | Manual hrs | AI hrs |   Manual $ |       AI $ |
| ----------------------------------------------------- | ---------- | -----: | ---------: | ---------: |
| Project scaffold (NestJS, TypeScript)                 | 40         |      8 |     $1,200 |       $240 |
| Database design & migrations (PostgreSQL)             | 48         |     10 |     $1,440 |       $300 |
| Auth service (phone, email, JWT, RBAC)                | 56         |     11 |     $1,680 |       $330 |
| RBAC & permissions (customer, merchant, admin, staff) | 32         |      6 |       $960 |       $180 |
| API conventions, validation, error handling           | 24         |      5 |       $720 |       $150 |
| Health checks, logging, monitoring baseline           | 24         |      5 |       $720 |       $150 |
| Transactional outbox + background worker skeleton     | 40         |      8 |     $1,200 |       $240 |
| **Subtotal**                                          | **264**    | **53** | **$7,920** | **$1,590** |

### 1.2 Customer Identity & Address Book

| Feature / Sub-task                           | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Phone registration & SMS OTP                 | 32         |      6 |       $960 |     $180 |
| Email registration & verification            | 24         |      5 |       $720 |     $150 |
| Guest checkout flow                          | 24         |      5 |       $720 |     $150 |
| Password reset / change                      | 16         |      3 |       $480 |      $90 |
| Address book (add/edit/delete/default/label) | 32         |      6 |       $960 |     $180 |
| **Subtotal**                                 | **152**    | **30** | **$4,560** | **$900** |

### 1.3 Menu & Catalog Engine

| Feature / Sub-task                                  | Manual hrs | AI hrs |   Manual $ |       AI $ |
| --------------------------------------------------- | ---------- | -----: | ---------: | ---------: |
| Category management                                 | 24         |      5 |       $720 |       $150 |
| Item CRUD (name, desc, price, photo)                | 40         |      8 |     $1,200 |       $240 |
| Modifiers & options (single/multi-select, required) | 48         |     10 |     $1,440 |       $300 |
| Combo / bundle meals                                | 32         |      6 |       $960 |       $180 |
| Allergen & dietary tags                             | 24         |      5 |       $720 |       $150 |
| Nutritional info fields                             | 16         |      3 |       $480 |        $90 |
| Availability hours per item / category              | 24         |      5 |       $720 |       $150 |
| **Subtotal**                                        | **208**    | **42** | **$6,240** | **$1,260** |

### 1.4 Cart & Hosted Checkout

| Feature / Sub-task                                                     | Manual hrs | AI hrs |   Manual $ |       AI $ |
| ---------------------------------------------------------------------- | ---------- | -----: | ---------: | ---------: |
| Add/remove/edit cart items                                             | 32         |      6 |       $960 |       $180 |
| Modifier selection in cart                                             | 24         |      5 |       $720 |       $150 |
| Cart subtotal & fee engine (delivery, service, small order, packaging) | 40         |      8 |     $1,200 |       $240 |
| Promo / voucher code application                                       | 32         |      6 |       $960 |       $180 |
| Address selection / pinpoint on map                                    | 24         |      5 |       $720 |       $150 |
| Delivery vs pickup selection                                           | 16         |      3 |       $480 |        $90 |
| ASAP scheduling                                                        | 16         |      3 |       $480 |        $90 |
| Order summary & place order                                            | 24         |      5 |       $720 |       $150 |
| Re-order one-tap                                                       | 16         |      3 |       $480 |        $90 |
| **Subtotal**                                                           | **224**    | **44** | **$6,720** | **$1,320** |

### 1.5 Payments

| Feature / Sub-task                     | Manual hrs | AI hrs |   Manual $ |       AI $ |
| -------------------------------------- | ---------- | -----: | ---------: | ---------: |
| Stripe card integration & tokenisation | 56         |     11 |     $1,680 |       $330 |
| 3D Secure handling                     | 24         |      5 |       $720 |       $150 |
| Cash on delivery                       | 16         |      3 |       $480 |        $90 |
| Refund flow (partial & full)           | 32         |      6 |       $960 |       $180 |
| Webhook reconciliation                 | 24         |      5 |       $720 |       $150 |
| Payment status state machine           | 24         |      5 |       $720 |       $150 |
| **Subtotal**                           | **176**    | **35** | **$5,280** | **$1,050** |

### 1.6 Order State Machine & Lifecycle

| Feature / Sub-task                           | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Canonical order model & state transitions    | 48         |     10 |     $1,440 |     $300 |
| Audit trail for every status change          | 24         |      5 |       $720 |     $150 |
| Cancellation flow (customer/merchant/system) | 32         |      6 |       $960 |     $180 |
| Minimum order requirement check              | 16         |      3 |       $480 |      $90 |
| Item availability check at checkout          | 16         |      3 |       $480 |      $90 |
| Order confirmation / receipt                 | 16         |      3 |       $480 |      $90 |
| **Subtotal**                                 | **152**    | **30** | **$4,560** | **$900** |

### 1.7 Merchant Order Console (Tablet / Web)

| Feature / Sub-task                | Manual hrs | AI hrs |   Manual $ |     AI $ |
| --------------------------------- | ---------- | -----: | ---------: | -------: |
| Live order queue with sound/alert | 40         |      8 |     $1,200 |     $240 |
| Accept / reject order             | 16         |      3 |       $480 |      $90 |
| Prep-time setting & updates       | 24         |      5 |       $720 |     $150 |
| Mark preparing / ready            | 16         |      3 |       $480 |      $90 |
| Delay or cancel with reason       | 24         |      5 |       $720 |     $150 |
| Order notes view                  | 8          |      2 |       $240 |      $60 |
| Print receipt / kitchen ticket    | 24         |      5 |       $720 |     $150 |
| **Subtotal**                      | **152**    | **31** | **$4,560** | **$930** |

### 1.8 Basic Notifications

| Feature / Sub-task                                                           | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ---------------------------------------------------------------------------- | ---------- | -----: | ---------: | -------: |
| WhatsApp message templates & sending                                         | 40         |      8 |     $1,200 |     $240 |
| SMS fallback integration                                                     | 24         |      5 |       $720 |     $150 |
| Order status notifications (confirmed, preparing, ready, delayed, delivered) | 32         |      6 |       $960 |     $180 |
| **Subtotal**                                                                 | **96**     | **19** | **$2,880** | **$570** |

### 1.9 Marketing / Showcase Website

| Feature / Sub-task             | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------ | ---------- | -----: | ---------: | -------: |
| Landing page design & build    | 32         |      6 |       $960 |     $180 |
| Click-to-WhatsApp buttons      | 8          |      2 |       $240 |      $60 |
| QR code generator per merchant | 16         |      3 |       $480 |      $90 |
| Merchant inquiry form          | 16         |      3 |       $480 |      $90 |
| SEO / meta basics              | 8          |      2 |       $240 |      $60 |
| **Subtotal**                   | **80**     | **16** | **$2,400** | **$480** |

### 1.10 Simple Web Dispatch Console (Pilot)

| Feature / Sub-task             | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------ | ---------- | -----: | ---------: | -------: |
| Delivery zone / radius rules   | 24         |      5 |       $720 |     $150 |
| Manual rider assignment        | 24         |      5 |       $720 |     $150 |
| Rider contact via web (no app) | 16         |      3 |       $480 |      $90 |
| Status updates to customer     | 16         |      3 |       $480 |      $90 |
| **Subtotal**                   | **80**     | **16** | **$2,400** | **$480** |

**Phase 1 Total:** 1,584 manual hrs → **$47,520** | 316 AI hrs → **$9,480**

---

## Phase 2 — Merchant Admin & Operations Dashboard

**Goal:** give merchants and platform admins the controls needed to run operations day-to-day.
**Duration estimate:** 4–5 weeks.
**Depends on:** Phase 1.

### 2.1 Merchant Self-Service Setup

| Feature / Sub-task                 | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ---------------------------------- | ---------- | -----: | ---------: | -------: |
| Restaurant profile setup           | 24         |      5 |       $720 |     $150 |
| Operating hours & holiday schedule | 16         |      3 |       $480 |      $90 |
| Delivery radius & charges          | 24         |      5 |       $720 |     $150 |
| Staff account management           | 24         |      5 |       $720 |     $150 |
| Notification settings              | 16         |      3 |       $480 |      $90 |
| **Subtotal**                       | **104**    | **21** | **$3,120** | **$630** |

### 2.2 Menu Management Dashboard

| Feature / Sub-task            | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ----------------------------- | ---------- | -----: | ---------: | -------: |
| Item CRUD dashboard           | 32         |      6 |       $960 |     $180 |
| Category management           | 16         |      3 |       $480 |      $90 |
| Modifier builder              | 24         |      5 |       $720 |     $150 |
| Photo upload                  | 16         |      3 |       $480 |      $90 |
| Bulk CSV upload               | 24         |      5 |       $720 |     $150 |
| Real-time out-of-stock toggle | 16         |      3 |       $480 |      $90 |
| **Subtotal**                  | **128**    | **25** | **$3,840** | **$750** |

### 2.3 Platform Admin Dashboard

| Feature / Sub-task               | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------- | ---------- | -----: | ---------: | -------: |
| Merchant onboarding & activation | 32         |      6 |       $960 |     $180 |
| User / role management           | 24         |      5 |       $720 |     $150 |
| Support tools & order lookup     | 24         |      5 |       $720 |     $150 |
| Platform settings & fees         | 24         |      5 |       $720 |     $150 |
| **Subtotal**                     | **104**    | **21** | **$3,120** | **$630** |

### 2.4 Basic Analytics & Reporting

| Feature / Sub-task                  | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ----------------------------------- | ---------- | -----: | ---------: | -------: |
| Order volume by source              | 16         |      3 |       $480 |      $90 |
| Direct vs marketplace mix           | 16         |      3 |       $480 |      $90 |
| Delayed / cancelled / failed counts | 16         |      3 |       $480 |      $90 |
| Prep-time adherence                 | 16         |      3 |       $480 |      $90 |
| Merchant-facing summary dashboard   | 24         |      5 |       $720 |     $150 |
| **Subtotal**                        | **88**     | **17** | **$2,640** | **$510** |

### 2.5 Stock & Pause Controls

| Feature / Sub-task               | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------- | ---------- | -----: | ---------: | -------: |
| Item snooze / sold-out           | 16         |      3 |       $480 |      $90 |
| Kitchen-pressure pause intake    | 24         |      5 |       $720 |     $150 |
| Auto close-of-day stock summary  | 16         |      3 |       $480 |      $90 |
| Re-enable checklist for next day | 16         |      3 |       $480 |      $90 |
| **Subtotal**                     | **72**     | **14** | **$2,160** | **$420** |

### 2.6 Manual Order Entry

| Feature / Sub-task                             | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ---------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Phone / walk-in order capture form             | 24         |      5 |       $720 |     $150 |
| Source tagging (phone, walk-in, WhatsApp, web) | 16         |      3 |       $480 |      $90 |
| Payment status tagging (paid, unpaid, COD)     | 16         |      3 |       $480 |      $90 |
| Integration into same order queue              | 8          |      2 |       $240 |      $60 |
| **Subtotal**                                   | **64**     | **13** | **$1,920** | **$390** |

**Phase 2 Total:** 560 manual hrs → **$16,800** | 112 AI hrs → **$3,360**

---

## Phase 3 — WhatsApp AI Assistant, Voice & Scan Orders

**Goal:** deliver the primary differentiators on top of a working core.
**Duration estimate:** 5–6 weeks.
**Depends on:** Phase 1.

### 3.1 WhatsApp Business API Integration

| Feature / Sub-task                         | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------------------ | ---------- | -----: | ---------: | -------: |
| WhatsApp Business Account & number setup   | 16         |      3 |       $480 |      $90 |
| Webhook receiver & signature validation    | 32         |      6 |       $960 |     $180 |
| Session & message template management      | 32         |      6 |       $960 |     $180 |
| QR code entry flow                         | 16         |      3 |       $480 |      $90 |
| Social ad deep links (FB/IG/TikTok/Google) | 24         |      5 |       $720 |     $150 |
| Referral link handling                     | 16         |      3 |       $480 |      $90 |
| **Subtotal**                               | **136**    | **27** | **$4,080** | **$810** |

### 3.2 WhatsApp Guided Ordering

| Feature / Sub-task                     | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------------- | ---------- | -----: | ---------: | -------: |
| Menu browsing via WhatsApp             | 40         |      8 |     $1,200 |     $240 |
| Add-to-cart via chat                   | 24         |      5 |       $720 |     $150 |
| Basket review & edit                   | 24         |      5 |       $720 |     $150 |
| Handoff to hosted checkout for payment | 24         |      5 |       $720 |     $150 |
| Order confirmation in chat             | 16         |      3 |       $480 |      $90 |
| **Subtotal**                           | **128**    | **26** | **$3,840** | **$780** |

### 3.3 AI Text Ordering Assistant

| Feature / Sub-task                  | Manual hrs | AI hrs |   Manual $ |       AI $ |
| ----------------------------------- | ---------- | -----: | ---------: | ---------: |
| Intent recognition for food orders  | 40         |      8 |     $1,200 |       $240 |
| Menu item matching & disambiguation | 48         |     10 |     $1,440 |       $300 |
| Modifier extraction                 | 32         |      6 |       $960 |       $180 |
| Basket draft generation             | 24         |      5 |       $720 |       $150 |
| Customer confirmation flow          | 24         |      5 |       $720 |       $150 |
| Fallback to human-readable prompts  | 16         |      3 |       $480 |        $90 |
| **Subtotal**                        | **184**    | **37** | **$5,520** | **$1,110** |

### 3.4 Voice-Recorded Order _(most important)_

| Feature / Sub-task                                   | Manual hrs | AI hrs |   Manual $ |       AI $ |
| ---------------------------------------------------- | ---------- | -----: | ---------: | ---------: |
| WhatsApp voice note reception & storage              | 24         |      5 |       $720 |       $150 |
| Speech-to-text transcription                         | 32         |      6 |       $960 |       $180 |
| Entity extraction from voice (items, qty, modifiers) | 48         |     10 |     $1,440 |       $300 |
| Missing-info clarification prompts                   | 32         |      6 |       $960 |       $180 |
| Staff review & confirm screen                        | 24         |      5 |       $720 |       $150 |
| Learning loop from corrections                       | 24         |      5 |       $720 |       $150 |
| **Subtotal**                                         | **184**    | **37** | **$5,520** | **$1,110** |

### 3.5 Scan Order

| Feature / Sub-task                           | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Customer scan QR/menu/receipt → open order   | 24         |      5 |       $720 |     $150 |
| Customer image-based menu parsing (OCR)      | 48         |     10 |     $1,440 |     $300 |
| Customer pre-fill basket from scanned item   | 32         |      6 |       $960 |     $180 |
| Rider scan digital bill/QR at pickup         | 24         |      5 |       $720 |     $150 |
| Rider scan customer QR / receipt at delivery | 24         |      5 |       $720 |     $150 |
| **Subtotal**                                 | **152**    | **31** | **$4,560** | **$930** |

### 3.6 Order Status via WhatsApp

| Feature / Sub-task          | Manual hrs | AI hrs |   Manual $ |     AI $ |
| --------------------------- | ---------- | -----: | ---------: | -------: |
| Automated status messages   | 24         |      5 |       $720 |     $150 |
| ETA & delay alerts          | 24         |      5 |       $720 |     $150 |
| Rider-assigned notification | 16         |      3 |       $480 |      $90 |
| Delivery completion message | 16         |      3 |       $480 |      $90 |
| **Subtotal**                | **80**     | **16** | **$2,400** | **$480** |

**Phase 3 Total:** 864 manual hrs → **$25,920** | 173 AI hrs → **$5,190**

---

## Phase 4 — Dispatch & Live Tracking (React Native Rider App + Web Dispatcher)

**Goal:** deliver orders end-to-end using a React Native rider app for execution and a web dispatcher console for control and exceptions.
**Duration estimate:** 6–7 weeks.
**Depends on:** Phase 1.

### 4.1 Dispatcher Web Console

| Feature / Sub-task             | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------ | ---------- | -----: | ---------: | -------: |
| Delivery zone / radius rules   | 24         |      5 |       $720 |     $150 |
| Manual rider assignment        | 24         |      5 |       $720 |     $150 |
| Live tracking dashboard        | 40         |      8 |     $1,200 |     $240 |
| Exception queue view & actions | 40         |      8 |     $1,200 |     $240 |
| **Subtotal**                   | **128**    | **26** | **$3,840** | **$780** |

### 4.2 React Native Rider App

| Feature / Sub-task                              | Manual hrs |  AI hrs |    Manual $ |       AI $ |
| ----------------------------------------------- | ---------- | ------: | ----------: | ---------: |
| React Native scaffold + navigation + auth       | 80         |      16 |      $2,400 |       $480 |
| Online/offline toggle + push notifications      | 48         |      10 |      $1,440 |       $300 |
| Incoming order request + accept/decline         | 48         |      10 |      $1,440 |       $300 |
| Turn-by-turn navigation (Google Maps / Mapbox)  | 64         |      13 |      $1,920 |       $390 |
| Pickup confirmation (scan + photo)              | 56         |      11 |      $1,680 |       $330 |
| Delivery confirmation (photo + OTP / signature) | 56         |      11 |      $1,680 |       $330 |
| Live GPS location streaming to platform         | 48         |      10 |      $1,440 |       $300 |
| In-app chat / call masking with customer        | 48         |      10 |      $1,440 |       $300 |
| Earnings view                                   | 32         |       6 |        $960 |       $180 |
| Order history                                   | 24         |       5 |        $720 |       $150 |
| **Subtotal**                                    | **504**    | **102** | **$15,120** | **$3,060** |

### 4.3 Customer Live Tracking

| Feature / Sub-task                   | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------------ | ---------- | -----: | ---------: | -------: |
| Map view on customer web status page | 40         |      8 |     $1,200 |     $240 |
| Rider GPS location consumption       | 32         |      6 |       $960 |     $180 |
| ETA countdown                        | 24         |      5 |       $720 |     $150 |
| Route display                        | 24         |      5 |       $720 |     $150 |
| **Subtotal**                         | **120**    | **24** | **$3,600** | **$720** |

### 4.4 AI Route Optimisation

| Feature / Sub-task                          | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Multi-stop route suggestions for dispatcher | 40         |      8 |     $1,200 |     $240 |
| Traffic-aware ETA calculation               | 40         |      8 |     $1,200 |     $240 |
| Batchable order detection                   | 32         |      6 |       $960 |     $180 |
| In-app route guidance for rider             | 32         |      6 |       $960 |     $180 |
| **Subtotal**                                | **144**    | **28** | **$4,320** | **$840** |

### 4.5 Exception Handling

| Feature / Sub-task               | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------- | ---------- | -----: | ---------: | -------: |
| No-rider alert & manual fallback | 16         |      3 |       $480 |      $90 |
| Rider no-show workflow           | 16         |      3 |       $480 |      $90 |
| Customer unreachable flow        | 16         |      3 |       $480 |      $90 |
| Failed delivery return flow      | 24         |      5 |       $720 |     $150 |
| **Subtotal**                     | **72**     | **14** | **$2,160** | **$420** |

**Phase 4 Total:** 968 manual hrs → **$29,040** | 194 AI hrs → **$5,820**

---

## Phase 5 — Growth, Personalisation & Advanced AI

**Goal:** increase retention, average order value, and operational intelligence.
**Duration estimate:** 5–6 weeks.
**Depends on:** Phases 1–3.

### 5.1 AI Personalisation & Predictive Reorder

| Feature / Sub-task                 | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ---------------------------------- | ---------- | -----: | ---------: | -------: |
| Customer preference learning       | 40         |      8 |     $1,200 |     $240 |
| Time/context-aware recommendations | 48         |     10 |     $1,440 |     $300 |
| "Usual" order prompts              | 24         |      5 |       $720 |     $150 |
| Family/household profiles          | 32         |      6 |       $960 |     $180 |
| **Subtotal**                       | **144**    | **29** | **$4,320** | **$870** |

### 5.2 AI Upsell Engine

| Feature / Sub-task                       | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ---------------------------------------- | ---------- | -----: | ---------: | -------: |
| Order-combination data mining            | 40         |      8 |     $1,200 |     $240 |
| Side-dish suggestion in chat/cart        | 32         |      6 |       $960 |     $180 |
| Per-restaurant toggle & revenue tracking | 24         |      5 |       $720 |     $150 |
| **Subtotal**                             | **96**     | **19** | **$2,880** | **$570** |

### 5.3 Staff Stock Visibility

| Feature / Sub-task               | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------------- | ---------- | -----: | ---------: | -------: |
| Remaining-stock display in admin | 24         |      5 |       $720 |     $150 |
| Prioritise-before-batch alerts   | 16         |      3 |       $480 |      $90 |
| Close-of-day re-enable workflow  | 16         |      3 |       $480 |      $90 |
| **Subtotal**                     | **56**     | **11** | **$1,680** | **$330** |

### 5.4 Group Ordering

| Feature / Sub-task                        | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ----------------------------------------- | ---------- | -----: | ---------: | -------: |
| Invite links via WhatsApp/SMS             | 24         |      5 |       $720 |     $150 |
| Web-based group order session             | 40         |      8 |     $1,200 |     $240 |
| Individual item selection per participant | 32         |      6 |       $960 |     $180 |
| Host pay / guest pay modes                | 40         |      8 |     $1,200 |     $240 |
| Order deadline & lock                     | 24         |      5 |       $720 |     $150 |
| **Subtotal**                              | **160**    | **32** | **$4,800** | **$960** |

### 5.5 Dietary & Allergen Filtering

| Feature / Sub-task                                          | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ----------------------------------------------------------- | ---------- | -----: | ---------: | -------: |
| Dietary preference filters (veg, vegan, halal, gluten-free) | 24         |      5 |       $720 |     $150 |
| Calorie range filter                                        | 16         |      3 |       $480 |      $90 |
| Cross-contamination notes                                   | 16         |      3 |       $480 |      $90 |
| **Subtotal**                                                | **56**     | **11** | **$1,680** | **$330** |

### 5.6 Loyalty, Vouchers & Referrals

| Feature / Sub-task        | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------- | ---------- | -----: | ---------: | -------: |
| Points-based loyalty      | 48         |     10 |     $1,440 |     $300 |
| Promo codes & vouchers    | 32         |      6 |       $960 |     $180 |
| Referral codes (give/get) | 32         |      6 |       $960 |     $180 |
| First-order discounts     | 16         |      3 |       $480 |      $90 |
| **Subtotal**              | **128**    | **25** | **$3,840** | **$750** |

**Phase 5 Total:** 640 manual hrs → **$19,200** | 127 AI hrs → **$3,810**

---

## Phase 6 — Scale & Ecosystem

**Goal:** integrate backend systems, kitchen workflow tools, and AI-driven automation.
**Duration estimate:** 6–8 weeks.
**Depends on:** Phases 1–5.

### 6.1 POS Integrations

| Feature / Sub-task    | Manual hrs | AI hrs |   Manual $ |       AI $ |
| --------------------- | ---------- | -----: | ---------: | ---------: |
| Generic POS sync API  | 64         |     13 |     $1,920 |       $390 |
| One major POS adapter | 64         |     13 |     $1,920 |       $390 |
| Menu sync             | 32         |      6 |       $960 |       $180 |
| Order push to POS     | 32         |      6 |       $960 |       $180 |
| **Subtotal**          | **192**    | **38** | **$5,760** | **$1,140** |

### 6.2 Kitchen Display System

| Feature / Sub-task       | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------ | ---------- | -----: | ---------: | -------: |
| Multi-station KDS screen | 56         |     11 |     $1,680 |     $330 |
| Prep timing & routing    | 40         |      8 |     $1,200 |     $240 |
| Ticket prioritisation    | 24         |      5 |       $720 |     $150 |
| **Subtotal**             | **120**    | **24** | **$3,600** | **$720** |

### 6.3 AI Demand Forecasting

| Feature / Sub-task         | Manual hrs | AI hrs |   Manual $ |     AI $ |
| -------------------------- | ---------- | -----: | ---------: | -------: |
| Historical demand analysis | 40         |      8 |     $1,200 |     $240 |
| Peak prediction            | 32         |      6 |       $960 |     $180 |
| Prep recommendations       | 24         |      5 |       $720 |     $150 |
| **Subtotal**               | **96**     | **19** | **$2,880** | **$570** |

### 6.4 AI Dynamic Pricing

| Feature / Sub-task                   | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------------------ | ---------- | -----: | ---------: | -------: |
| Demand-based delivery fee adjustment | 40         |      8 |     $1,200 |     $240 |
| Surge / peak pricing rules           | 32         |      6 |       $960 |     $180 |
| **Subtotal**                         | **72**     | **14** | **$2,160** | **$420** |

### 6.5 AI-Based Social Media Ads

| Feature / Sub-task        | Manual hrs | AI hrs |   Manual $ |     AI $ |
| ------------------------- | ---------- | -----: | ---------: | -------: |
| Ad creative generation    | 40         |      8 |     $1,200 |     $240 |
| Caption / copy generation | 24         |      5 |       $720 |     $150 |
| **Subtotal**              | **64**     | **13** | **$1,920** | **$390** |

**Phase 6 Total:** 544 manual hrs → **$16,320** | 108 AI hrs → **$3,240**

---

## Master Summary Table

| Phase                                                       | Manual hrs |    AI hrs |  Manual Cost |     AI Cost | Calendar Weeks |
| ----------------------------------------------------------- | ---------: | --------: | -----------: | ----------: | -------------: |
| Phase 1 — Foundation & Core Order Flow                      |      1,584 |       316 |      $47,520 |      $9,480 |           8–10 |
| Phase 2 — Merchant Admin & Ops Dashboard                    |        560 |       112 |      $16,800 |      $3,360 |            4–5 |
| Phase 3 — WhatsApp AI, Voice & Scan                         |        864 |       173 |      $25,920 |      $5,190 |            5–6 |
| Phase 4 — Dispatch & Live Tracking (React Native App + Web) |        968 |       194 |      $29,040 |      $5,820 |            6–7 |
| Phase 5 — Growth & AI Personalisation                       |        640 |       127 |      $19,200 |      $3,810 |            5–6 |
| Phase 6 — Scale & Ecosystem                                 |        544 |       108 |      $16,320 |      $3,240 |            6–8 |
| **TOTAL**                                                   |  **5,260** | **1,028** | **$157,800** | **$30,840** |      **34–42** |

### Pilot launch scope (Phases 1–3)

For the first commercially shippable pilot, build **Phases 1–3 only**:

- Manual cost: **$90,240**
- AI-assisted cost: **$18,030**
- Estimated calendar timeline: **17–21 weeks** (~4–5 months)
