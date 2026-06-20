# Uber Eats Feature Masterlist — Index

1. [Customer App — Discovery & Browse](#1-customer-app-discovery-browse)
2. [Customer App — Cart & Checkout](#2-customer-app-cart-checkout)
3. [Customer App — Account & Profile](#3-customer-app-account-profile)
4. [Customer App — Order Tracking](#4-customer-app-order-tracking)
5. [Customer App — Notifications](#5-customer-app-notifications)
6. [Customer App — Accessibility & UX](#6-customer-app-accessibility-ux)
7. [Uber One Subscription](#7-uber-one-subscription)
8. [Uber Eats Marketplace / Grocery & Retail](#8-uber-eats-marketplace-grocery-retail)
9. [Uber Direct / Logistics-as-a-Service](#9-uber-direct-logistics-as-a-service)
10. [Shops / Marketplace (non-food retail)](#10-shops-marketplace-non-food-retail)
11. [Pick-Up & Dine-In](#11-pick-up-dine-in)
12. [Group Order & Corporate/B2B](#12-group-order-corporateb2b)
13. [Merchant / Uber Eats Manager Dashboard](#13-merchant-uber-eats-manager-dashboard)
14. [Partner API & POS Integration](#14-partner-api-pos-integration)
15. [Uber Eats Ads / AdTech](#15-uber-eats-ads-adtech)
16. [Rider/Delivery Person App — Onboarding & Sessions](#16-riderdelivery-person-app-onboarding-sessions)
17. [Rider/Delivery Person App — Delivery & Earnings](#17-riderdelivery-person-app-delivery-earnings)
18. [Rider/Delivery Person App — Safety & Well-being](#18-riderdelivery-person-app-safety-well-being)
19. [Rider/Delivery Person App — Uber Eats Pro Rewards & Tiers](#19-riderdelivery-person-app-uber-eats-pro-rewards-tiers)
20. [Platform — AI Dispatch & Operations](#20-platform-ai-dispatch-operations)
21. [Platform — Dark Store / HUB Operations](#21-platform-dark-store-hub-operations)
22. [Platform — Data, Analytics & Compliance](#22-platform-data-analytics-compliance)
23. [Payment Methods & Financial](#23-payment-methods-financial)
24. [Promotions, Vouchers & Loyalty](#24-promotions-vouchers-loyalty)
25. [Marketing, CRM & Campaigns](#25-marketing-crm-campaigns)
26. [Brand, History & Sustainability](#26-brand-history-sustainability)
27. [Controversies & Challenges](#27-controversies-challenges)
28. [Metrics & KPIs](#28-metrics-kpis)

---

## 1. Customer App — Discovery & Browse

### Search

- Search by restaurant name
- Search by cuisine type
- Search by dish/item name
- Search by grocery product name
- Search by store name (grocery/retail)
- Autocomplete search suggestions
- Recent searches display
- Search history
- Voice search integration (device-native)
- Alexa+ conversational voice ordering (Amazon Echo Show, Mar 2026)
- LLM-powered semantic search (handles synonyms, typos, multilingual queries with two-tower deep network and Qwen LLM backbone)
- Search within a restaurant menu
- Search by dietary preference (vegetarian, vegan, gluten-free)
- Search by featured deal/promotion

### Browse & Feed

- Restaurant list view
- Curated restaurant feed (personalised)
- AI-powered restaurant recommendations
- Promotional banners (top of home screen)
- Daily deals carousel / banner
- Cuisine category tiles (Pizza, Sushi, Burgers, Asian, Mexican, etc.)
- Quick-filter chips (open now, under 30 min, rating 4+)
- "Nearest to you" sorting
- "Top rated" sorting
- "Delivery time" sorting
- Restaurant opening hours display
- Restaurant distance from user display
- Estimated delivery time display
- Delivery fee preview in listing
- Minimum order amount display
- Promo badge on restaurant card
- Rating badge / star display on restaurant card
- "Open Now" filter toggle
- Dietary preference filters (vegetarian, vegan, halal, gluten-free)
- Filter by calorie range / low-calorie
- Price range indicator ($/$$/$$$)
- Service type filter (delivery / pickup)
- Uber One-exclusive offers badge
- Uber One-exclusive filter toggle
- "Previously ordered" section
- "Popular near you" section
- "Trending near you" section (gaining popularity signal)
- "New on Uber Eats" section
- Shortcuts to recent/favourite restaurants
- Horizontal scroll of promo banners
- Near me auto-detect restaurants
- Category visibility for grocery/retail stores (May 2026)
- Grocery category browsing (dairy, produce, snacks, beverages)
- Dedicated grocery tab in bottom navigation
- Restaurant grid/thumbnail view toggle
- "Best match" recommended sorting (algorithmic)
- "Popular cuisines" quick access section on homepage

### Restaurant Menu Page

- Full menu listing with categories
- Item name, description, price display
- Item photo gallery (multiple images per item)
- Nutritional information display
- Allergen information display
- Popular item badge ("Bestseller" / "Popular")
- Customisation options for each item
  - Size variants (regular/large/family)
  - Toppings/extras selection
  - Special instructions / notes field
  - Required choices (e.g. doneness, sauce)
  - Multi-select modifiers
  - Single-select modifiers
- Price adjustment based on modifiers
- Add-ons / upsell suggestions
- Combo meal bundles
- "Frequently bought together" suggestions (cross-sell)
- Individual item rating display
- User-submitted individual item rating
- Restaurant info section (address, hours, contact)
- Restaurant rating breakdown (overall)
- Restaurant rating sub-scores (food quality, delivery, service)
- Photo reviews from other customers
- Uber One badge on eligible items
- AI-generated menu descriptions (auto-fill)
- AI-enhanced food photos (low-quality image upscaling)
- User-generated food photos (customer-submitted)
- Uber Cash incentive for photo submission ($3 in US)

---

## 2. Customer App — Cart & Checkout

### Cart

- Add items to cart
- Remove items from cart
- Edit items in cart (modify customisation)
- Adjust item quantity
- Cart subtotal real-time calculation
- Delivery fee display in cart
- Service fee display
- Small order fee (if below minimum)
- Packaging fee display (market-specific)
- Tax display
- Promo/voucher code input
- Auto-applied Uber One discounts
- Free delivery threshold indicator (Uber One members)
- Minimum order requirement warning
- Item availability check during checkout
- Out-of-stock item management
- Item substitution options (grocery)
- Cart timer (restaurant order deadline)
- Estimated total before placing order
- Multi-store cart (multiple restaurants in single order — limited markets)
- AI Cart Assistant for grocery (image/text-to-cart, Feb 2026)
- Cart Assistant based on past purchases and store availability
- Cross-contamination note (single restaurant per order standard)
- Save cart for later (scheduled order)

### Checkout

- Delivery address input / selection
- Saved addresses quick-select
- New address addition
- Pinpoint on map for address
- Address autocomplete
- Delivery instructions / notes to delivery person
- Contactless delivery toggle ("Leave at door")
- Scheduled delivery time selection (advance booking)
- "ASAP" delivery option
- Pickup time selection
- Service type selection (delivery / pickup)
- Payment method selection
- Save payment method toggle
- Credit/debit card details entry
- Digital wallet selection (PayPal, Uber Cash)
- Cash on delivery option (market-specific)
- Gift card / voucher code redemption
- Uber One benefits applied display
- Order summary review
- Itemised receipt preview
- Tip amount selection (pre-delivery: 15%, 18%, 20%, custom)
- Tip custom amount input
- Order note for restaurant
- Cutlery opt-in/out toggle (market-specific)
- Checkout for someone else (recipient name/address)
- Address geocoding validation (address pin verification)
- Place order confirmation button
- Re-order from previous orders (one-tap)
- Scheduled order up to 7 days in advance
- Priority delivery fee toggle (extra fee for faster delivery)
- Long-range delivery fee (extra fee for longer distance)
- Split payment across multiple methods (limited markets)
- Saved payment tokenisation

---

## 3. Customer App — Account & Profile

### Registration & Login

- Phone number registration
- Email registration
- Google/Apple social login
- SMS OTP verification
- Email verification
- Guest checkout (no account required)
- Post-order account creation (conversion from guest)
- Password creation and management
- Forgot password / reset password flow
- Remember me / auto-login
- Multi-factor authentication (optional)
- Passkey support (biometric login)

### Profile Management

- Profile photo upload
- Name edit
- Phone number edit
- Email edit
- Delivery address management
  - Add new address
  - Edit existing address
  - Delete address
  - Set default address
  - Address label (Home, Work, Other)
  - Geocoded address pin on map
- Saved payment methods management
  - View saved cards
  - Delete saved cards
  - Set default payment method
- Language preference (English + 38+ languages)
- Notification preferences management
- Uber One membership management
- Accessibility settings (app-wide)
- Privacy Center (centralised dashboard for data access, download, account deletion)
- Download your data request (download file of account data, email/text notification when ready)
- Delete account via Privacy Center (90-day deletion window)
- Two-step verification required for privacy data access

### Order History

- Past orders list
- Order details view (items, price, status)
- Repeat order (quick reorder)
- Rate and review past orders
- Photo upload for review
- Order status timeline
- Invoice/receipt view
- Order cancellation (before preparation)
- Refund status tracking
- Support contact for order issues
- Report an issue flow

### Favourites

- Favourite restaurants list
- Favourite dishes list
- Favourite stores list (grocery/retail)
- Follow/unfollow restaurants
- Quick access to favourites tab
- "Saved" collection for later browsing

### Payment & Wallet

- Uber Cash balance view
- Gift card balance view
- Promo code list
- Payment history
- Uber One credits earned/expiring view

### Vouchers & Promos

- Expired vouchers/promos view
- Voucher terms and conditions view

### Gift Cards

- Digital gift cards (email delivery, instant)
- Physical gift cards (postal delivery)
- Custom amount ($5-$500)
- Customisable designs per occasion
- Personal message attachment
- Send gift card from within app (Account > Send a gift)
- Corporate gift card portal (bulk purchase 10+)
- Gift card redemption via wallet (16-digit alphanumeric code)
- Redeemed gift card balance converts to Uber Cash
- Cross-platform use (rides + Eats from same gift card)
- No expiry on gift card balance
- Currency restrictions (redeemable only in same currency)

### Subscriptions

- Uber One subscription management
  - View current plan (monthly/annual)
  - Cancel subscription
  - View benefits summary
  - Uber One for family (share with one additional person)
  - Member Days calendar/schedule
  - Modify subscription plan (upgrade/downgrade between monthly and annual)

---

## 4. Customer App — Order Tracking

### Real-Time Tracking

- Order placed confirmation screen
- Order accepted by restaurant notification
- Food being prepared status
- Delivery person assigned notification
- Delivery person name and photo display
- Delivery person phone number (in-app call masking)
- Delivery person live location on map
- Delivery person ETA countdown
- Delivery person arrival notification ("Courier is arriving")
- Live map with delivery person route
- Restaurant location on map
- Delivery destination on map
- Estimated time remaining
- Order progress bar/steps
- Push notification at each status change
- View as delivery person feature (privacy transparency, Jan 2023)
- Share trip progress with friends/family

### Post-Delivery

- Delivered confirmation
- Photo confirmation of delivery ("Leave at door" photo)
- Rate your delivery person (thumbs up/down)
- Tip delivery person (post-delivery option)
- Rate restaurant (stars + review)
- Photo review upload
- Reorder button
- Report an issue flow
- Contact support
- User-generated food photo submission (for items without menu images)
- Uber Cash reward for published photo ($3 US)

### Delivery Statuses

- Order placed
- Restaurant confirmed
- Preparing food
- Ready for pickup (pickup orders)
- Delivery person picked up order
- Delivery person on the way
- Delivered
- Cancelled (by restaurant/customer/system)
- Failed delivery
- Order delayed notification

---

## 5. Customer App — Notifications

### Order Notifications

- Order confirmation
- Order accepted by restaurant
- Food is being prepared
- Delivery person assigned
- Delivery person arriving
- Order delivered
- Order cancelled
- Order delayed notification
- Out-of-stock item substitution alert
- Scheduled order reminder

### Promotional Notifications

- Personalised deals and offers
- Flash sale alerts
- Free delivery promotion (Uber One)
- New restaurant in area
- Uber One exclusive offers
- Voucher expiry reminders
- Seasonal/cultural campaign alerts
- Abandoned cart push reminder
- Re-engagement push (inactive users)
- Deal Drops time-bound offer alerts (Jun 2026)
- Member Days promotional notifications

### Account Notifications

- Payment successful
- Refund processed
- Subscription renewal notice
- Payment failed alert
- Account security alert (new login)
- Email notification for orders
- SMS order updates
- In-app notification centre
- Uber One credits expiry reminder

---

## 6. Customer App — Accessibility & UX

### Accessibility

- Screen reader compatible (VoiceOver/TalkBack)
- Font size adjustment
- High contrast mode
- Colour contrast compliance
- Language toggle (English + 38+ languages)
- Dynamic type support (iOS)
- Reduced motion setting respect
- Accessibility statement page
- WCAG 2.1 AA compliance target
- VPAT (Voluntary Product Accessibility Template) available on request
- Deaf/HOH-friendly delivery notifications (visual alerts, flash on screen)
- Service animal delivery policy (delivery persons may bring service animals)
- Wait time fee waived for customers with documented accessibility needs (select markets)
- Switch to text-only mode (low-bandwidth, low-complexity UI)
- Large tap target areas (minimum 44pt touch targets)
- Closed captioning on video content (in-app ads, tutorials)

### UI/UX

- Dark mode / light mode (system-follow)
- Bottom tab navigation (Home, Search, Orders, Account, Grocery)
- Pull-to-refresh
- Infinite scroll on restaurant listing
- Skeleton loading screens
- Offline error handling / retry
- Device permissions management (location, camera, microphone, notifications via in-app settings)
- Cookie preferences management
- In-app rating prompt
- App rating redirect to App Store/Play Store
- Tutorial / onboarding walkthrough for new users
- Shortcuts to recent orders on home screen
- One-tap reorder
- Visual redesign (periodic UI refresh)
- Swipe gestures for quick actions (limited)
- Colour blindness friendly palette (limited)

### Device & Platform

- iOS app (iPhone, iPad)
- Android app
- Mobile website (m.ubereats.com)
- Desktop website (ubereats.com)
- iOS 17.0+ required
- Apple Watch app (limited)
- App size: ~363.3 MB (iOS)
- App rating: 4.8/5 (iOS), 4.6/5 (Android)
- 100M+ Android downloads
- 7.45M+ Android reviews
- 10M+ iOS ratings
- Available in 50+ countries, 11,500+ cities
- Huawei AppGallery availability (select markets)



---

## 7. Uber One Subscription

### Plans & Pricing

- Monthly subscription ($9.99/mo US, $96/yr)
- Free trial period (new subscribers, 1 month)
- Student discount (50% off, $4.99/mo)
- Auto-renewal monthly or annually
- Cancel anytime (effective next billing)
- No refunds for partial months
- Automatic cancellation on subscription payment failure
- Payment method required at sign-up
- Partner-funded passes (credit card partnerships)
- Delta SkyMiles Amex partnership (up to 12 months free)

### Benefits — Food Delivery

- $0 Delivery Fee on eligible orders (min. spend varies $12-$25)
- Up to 10% off eligible delivery orders over $15
- Up to 10% off pickup orders
- Service fee discount (retired for new members Mar 2026)
- Variable order minimum per merchant (dynamic min.)
- Priority delivery placement (some markets)
- Uber One icon on eligible stores/items

### Benefits — Grocery & Retail

- $0 Delivery Fee on eligible grocery orders (min. $35)
- 5% off eligible grocery orders over $35
- Fresh Tuesdays: up to 30% off select grocery items
- Member-only grocery deals

### Benefits — Rides (Cross-Platform)

- 6% Uber Cash back on eligible rides
- Top-rated driver matching priority
- Uber One credits earned on rides (expire 60 days)
- UberX Share savings (up to 20% off)

### Benefits — Additional

- Exclusive member promotions and offers
- Uber One Member Days (periodic savings event)
- Voucher/promo refund on order cancellation
- Uber One exclusive tables at select Dine Out restaurants (AU)
- Family sharing (add one additional member at no cost)
- Priority support access

### Credit Card Partnerships

- Delta SkyMiles Amex: free membership with eligible card
- Chase, Capital One partnerships (varying)
- Marriott Bonvoy partnership (Uber One members earn/redeem Marriott points; incentivises Uber One sign-ups)
- Kroger Boost cross-benefit (extended free trial)

### Management

- Subscribe via Uber or Uber Eats app
- View remaining benefits
- Benefits auto-applied at checkout (when eligible)
- Cancel subscription (48-hour notice)
- Modify subscription plan (upgrade/downgrade)
- Modify payment method
- Payment failure retry logic / grace period
- View savings summary
- Terms & conditions per market

---

## 8. Uber Eats Marketplace / Grocery & Retail

### Grocery Store Network

- Albertsons, Safeway, SEG banners
- Kroger family (Ralphs, Fred Meyer, King Soopers, Smiths, Fry's, Harris Teeter, Mariano's — 2026)
- Kroger 2,700-store full assortment rollout (beginning 2026)
- Costco (limited markets)
- ALDI
- Meijer
- Stop & Shop (Ahold Delhaize USA)
- Giant (Ahold Delhaize USA)
- Food Lion (Ahold Delhaize USA)
- Hannaford (Ahold Delhaize USA)
- Wegmans
- Regional chains (Big Y, King Kullen, Vallarta, Lunds & Byerlys, Foxtrot)
- Convenience stores (7-Eleven, Wawa)
- Pharmacies (CVS, Walgreens)
- Total Wine & More, BevMo!
- Petco
- Walmart (limited)
- Target (limited markets)
- Gopuff partnership
- Fresh produce, meat, seafood, dairy, bakery
- Packaged foods, frozen treats
- Household essentials
- Baby care products
- Pet food and supplies
- Over-the-counter medication
- Flowers and plants

### Grocery Features

- In-app grocery tab
- Product search in grocery mode
- Category browsing (produce, dairy, meat, snacks, beverages)
- Item ratings integration (third-party ratings on product pages)
- "Many in stock" badge on product listings
- AI Cart Assistant (image/text-to-cart, Feb 2026)
- Cart Assistant based on purchase history and store availability
- Smarter inventory prediction model (reduced cancellations, May 2026)
- Item substitution options when out-of-stock
- Scheduled delivery up to 7 days in advance
- Variable delivery fee ($1.99+ depending on basket)
- Service fee on grocery (5-10%)
- Uber One benefits on grocery
- Fresh Days weekly program (up to 50% off fresh items, Sep 2025)
- Uber One Fresh Tuesdays (30% off select items)
- SNAP/EBT payment acceptance (via Forage integration, select US stores)
- SNAP-eligible item filter/tag in grocery search
- Savings Slider (choose delivery speed for lower fee)
- Same-day delivery from 100+ metro areas
- Multi-store grocery order (add items from different stores to same cart, limited)
- Grocery-specific promo codes (targeted at grocery categories)
- Ibotta Performance Network digital grocery coupon integration (Mar 2026, multi-year exclusive)
- Bulk ordering option for grocery
- Self pick-up from partner stores (select markets)
- 24/7 grocery ordering availability (market-specific)
- Product/SKU count display per store
- Weight-based pricing for grocery items (per kg/lb, select markets)
- Ready-to-eat meals category
- Imported specialty products
- Local farm produce partnerships
- Plant-based and sustainably-grown products section
- Hyperlocal demand trend assortment planning
- AI-powered demand forecasting for inventory
- AI-powered order processing
- Picking optimisation (store layout for efficiency)
- AI preference prediction for product recommendations
- Consumer insights reporting

### Retail Partnerships

- EB Games (via Uber Direct)
- Flower shops
- Pet stores
- Liquor stores
- Electronics retailers
- Beauty and cosmetics
- Home and living
- Same-day delivery from partnered stores
- Catalog sync via API/SFTP
- Inventory management integration

---

## 9. Uber Direct / Logistics-as-a-Service

### B2C Consumer Services

- Uber Connect (item/person-to-person delivery)
- Package returns (UPS, FedEx, USPS — Oct 2023)
- Up to 5 packages per return trip
- Live tracking of package
- Photo confirmation of drop-off receipt
- Flat $5 fee ($3 for Uber One members)
- Available in 4,950+ US cities
- Insurance coverage (up to $100 declared value included; higher value available for fee)
- Weight limit per package (up to 30 lbs)
- Size limit per package (must fit in standard vehicle boot)
- Same-day delivery
- Return label scanning (QR code scan at pickup, Oct 2023)
- Pre-paid return label not required (can purchase label through Uber, some retailers)
- Tracking link to share with recipient (real-time status page)

### B2B / Enterprise (Uber Direct)

- White-label delivery API for merchants
- On-demand delivery via Uber courier network
- Integration with POS and e-commerce platforms
- Real-time tracking for businesses
- Proof of delivery
- Performance analytics dashboard
- Scheduled pickup and delivery windows
- Flat-fee local delivery (no commission)
- Custom branded tracking page
- Order management dashboard
- Webhook event notifications
- Integration partners (Toast, Otter, Square, etc.)
- 100+ integration partners globally
- Certification program for integration partners
- Toast + Uber Direct native integration (order dispatch from Toast POS)
- Square + Uber Direct integration (first-party delivery from Square merchants)
- Unified tracking page for end customers (branded as merchant)
- SLA delivery window (60-minute)
- 5-minute delivery matching time (select markets)
- No prepaid deposit required (pay-per-order)
- B2B web portal for Direct logistics
- No contract required for B2B clients
- Cash on delivery option (retailers)
- Per-kilometre distance-based fee + base fee
- Available to all businesses (not just Uber Eats partners)

### Uber Direct API Features

- Create delivery endpoint
- Estimate delivery fee
- Track delivery
- Cancel delivery
- Delivery area check
- Proof of delivery
- Webhooks for status updates
- Sandbox testing environment
- Order time estimation (API endpoint)

---

## 10. Shops / Marketplace (non-food retail)

### Categories

- Convenience stores
- Pharmacies and health
- Pet shops and supplies
- Electronics and accessories
- Beauty and cosmetics
- Home and living
- Baby and toys
- Flowers and gifts
- Alcohol / liquor stores
- Sporting goods
- Office supplies

### Marketplace Features

- Individual shop pages with branding
- Shop ratings and reviews
- Product search within shop
- Category browsing
- Promotions and deals per shop
- Scheduled delivery
- Out-of-stock item management
- Minimum order per shop
- Uber One benefits on eligible shops
- Catalog integration via API/SFTP
- Real-time inventory sync
- Same-day delivery
- Flexible fulfillment (own staff or Uber courier network)
- Schedule order up to 7 days in advance
- Retail Returns via courier pickup (Apr 2026, returned items purchased on UE)
  - Instant refund on courier pickup
  - Return fee based on courier time/distance
  - Partners: Best Buy, DICK'S Sporting Goods, Pet Food Express, Pacsun, Petco
  - Item eligibility per store's return policy
  - Minimum $20 item value for courier return
- Return an item flow in order history ("Return an item" button)
- Item eligibility check in app before initiating return
- Shop distance and ETA display

---

## 11. Pick-Up & Dine-In

### Pickup

- Browse restaurants/shops for pickup
- Select pickup time slot
- Skip the line at restaurant
- No delivery fees on pickup
- Flat 6% commission on pickup orders (Mar 2026)
- Pay online or at restaurant
- Real-time order status (when ready)
- Pickup instructions for restaurant
- Address and pickup instructions for couriers (merchant-set, Apr 2025)
- Order ahead feature
- Service type toggle (delivery / pickup)
- Minimum % off pickup orders (automatic discount, market-specific)
- Show order number at restaurant for pickup verification
- Self-collect from partner stores
- Extra savings on grocery pickup
- Minimum discount on pick-up orders (select markets)
- No minimum order value for pick-up (select markets)
- Pick-up for grocery/retail orders

### Dine-In / Dine Out

- Dine Out feature (Australia — Sydney, Melbourne, launch partners 30+ restaurants)
- Uber One exclusive tables at select partner restaurants (AU)
- Gold VIP Dine Out (6-month free Uber One trial via OpenTable partnership)
- QR code menu/ordering at table (limited)
- Restaurant reservation integration (OpenTable partnership, launched Dec 2025)
- Book restaurant directly from Uber Eats app
- Promotions for dine-in through app
- Pay at restaurant through app (limited)
- "Order ahead for pickup" near restaurant
- Cross-promotion between delivery and dine-in
- Dine Out loyalty integration (earn Uber Cash on dine-in spend)
- Dynamic pickup instructions (merchant-set instructions shown to customer when arriving)
- Dine-in promotions at partner restaurants
- 1-for-1 dine-in offers (select markets)
- QR code scan at restaurant to verify/redeem dine-in offer
- Subscription-gated dine-in offers (Uber One exclusive)
- In-restaurant QR code ordering (limited)

---

## 12. Group Order & Corporate/B2B

### Group Order

- Invite link sharing (via messaging apps — WhatsApp, Messenger, SMS)
- Web-based group order flow (no app required for participants to add items)
- Each participant orders from own device
- Host pays on behalf of group (or pay-your-own mode)
- Guest pay mode (each participant pays for their own items)
- Individual item selection per participant
- Real-time order tracking per participant
- Group order session management
- Payment split (manual coordination)
- Spending limit per participant (host-set cap)
- Order deadline set by host (auto-submit when time expires)
- Lock order (host prevents further edits before submitting)
- Order split up to 18 ways (max participants per group order)
- Restaurant orders only (not grocery)
- Recurring group order (save group for weekly/routine orders)
- Order for delivery or pickup

### Uber for Business (Corporate)

- Centralised business dashboard
- Employee meal programmes
- Per-employee spending limits
- Department budget allocation
- Catering for meetings and events
- Scheduled catering orders
- Streamlined billing and invoicing
- Expense management integration
- Corporate credit line
- Employee wellbeing programmes (meal stipends)
- Business travel meal allowances
- Reporting and analytics for HR/finance
- Integration with expense platforms (Concur, etc.)
- Uber One membership perks for employees (via business)
- HR benefits platform integration
- Office pantry stocking (snacks, beverages, essentials)
- Pre-ordering up to 14 days in advance
- Corporate retreat and event ordering
- Team management and access control
- Per-employee daily allowance setting (corporate dashboard)
- Access to grocery/retail for corporate bulk orders
- Exclusive corporate discounts



---

## 13. Merchant / Uber Eats Manager Dashboard

### Dashboard (Desktop)

- Sales overview dashboard
- Real-time order tracking
- Order management
- Menu management
- Performance analytics
- Customer insights
- Revenue reports
- Peak hours analysis
- Payouts view (balance, payment history, earnings breakdown)
- Marketing campaign performance
- Ad performance metrics (Ads Manager)

### Uber Eats Manager App (Mobile)

- Home tab with sales, orders, ticket size, operations, customer data
- Menu tab (edit item names, pricing, availability, descriptions)
- Customer insights tab (ordering behaviour, trends, retention)
- Payouts tab (balance, payment history, earnings breakdown)
- Performance tab (ad metrics)
- Notification settings (store status, connectivity, POS issues, cancelled orders, missed orders, inaccurate orders)
- Customer reviews (read and respond)
- Order issues (view and dispute chargebacks)
- Store info (address, pickup instructions)
- Support access

### Menu Management

- Add new menu items
- Edit menu items (name, description, price, photo)
- Remove menu items
- Create item categories
- Set menu availability hours
- Set item modifiers and options
- Bulk menu upload
- Menu sync via API
- Price update
- AI auto-fill menu descriptions (Jul 2025)
- AI-enhanced food photos (Jul 2025)
- Mark items out of stock (real-time)
- Update regular and holiday hours
- Set delivery radius
- Holiday closure schedule

### Order Management (Uber Eats Orders App)

- Tablet-based order management (iOS/Android)
- Desktop web order management
- Accept/decline orders
- Mark order as preparing
- Mark order as ready
- Alert nearby delivery people when ready
- Delay or cancel orders
- Estimated preparation time update
- Item availability toggle (out-of-stock)
- Order cancellation (initiate by merchant)
- Order notes view
- Contact customer via Live Order Chat (Jul 2025)
- Order history
- Track delivery person in real-time
- View delivery person contact info
- Check delivery person wait time
- Incoming and scheduled order management
- Training guide in-app
- Print order receipt
- Reject order with reason

### Growth Tools & Analytics

- Customer groups data (geographic areas driving sales)
- New vs returning customer segmentation
- AI-powered customer review summaries (Apr 2025)
- Recommended actions based on reviews (Apr 2025)
- Scheduled reporting (automated reports on KPIs, Apr 2025)
- Customer claims transparency (order error adjustments, Apr 2025)
- Sales trend reports
- Menu item performance (top sellers, slow movers)
- Peak hours analysis (busiest periods, staff planning tool)
- Performance benchmarking
- Customer behaviour analytics
- Pricing recommendations tool

### Onboarding & Support

- Self-signup process
- Streamlined onboarding process
- Dedicated account manager (for selected tiers)
- Training resources and guides
- Email support (restaurants@uber.com)
- Help centre (help.uber.com)
- Passkeys / 2-factor authentication (Apr 2025)
- How-to guide in Orders app
- Virtual restaurant creation support (delivery-only brands from existing kitchens)
- Certified Virtual Restaurant Program (Jun 2026, with Virtual Dining Concepts, Nextbite, Acelerate)
- SmartShoot professional food photography (for menu items)
- Premium photo shoot package (complementary for Premium tier merchants)

### Merchant Financial Access

- Payouts (weekly or daily depending on market)
- Transparent fee breakdown
- Performance-based commission tiers
- Fee plans (Lite, Plus, Premium — commission-based)
- Pickup commission (7%)
- Custom rate plans
- Chargeback dispute process
- Merchant financing partnerships (selected markets)
- Working capital programmes (advance on future earnings, limited markets)
- Commission structure management

### Merchant Campaigns & Tools

- Promotions management (discounts, offers)
- Ads Manager integration
- Loyalty program integration (link customer loyalty accounts)
- Co-marketing opportunities
- Merchant recognition programmes
- Partner success stories hub
- Insights hub (articles, guides, product updates)
- Merchant appreciation events and recognition programmes
- Restaurant Transformation Advisory (consultant-led coaching, limited markets)
- Merchant coaching and advisory programmes
- Personalised merchant support programme

---

## 14. Partner API & POS Integration

### Uber Eats Marketplace API

- Store API suite (manage store info, menus, availability)
- Order API suite (manage orders, status updates)
- Promotions API (create promotions, strikethrough discounts, same-item bundle offers, scheduled promotions)
- Reporting API (access performance data)
- Webhooks (incoming order notifications, store updates, cancellations)
- OAuth 2.0 authentication (Client Credentials flow)
- Sandbox testing environment
- Rate limiting per endpoint
- OpenAPI/Swagger specifications
- Approval-based access (partner manager required)
- NDA and API licensing agreement required
- 99% order injection success rate requirement

### Store API Endpoints

- GET /eats/stores/{store_id} (retrieve store details)
- GET /eats/stores/{store_id}/menus (retrieve full menu structure)
- POST /eats/stores/{store_id}/menus (update menu)
- PATCH /eats/stores/{store_id}/availability (update store status)
- Update item pricing, availability, descriptions
- Manage inventory in real-time
- Sync modifiers and customisation options

### Order API Endpoints

- Receive incoming orders (webhook)
- Accept/decline order
- Update order status (preparing, ready, picked up)
- Cancel order
- View order details (items, modifiers, notes)
- Order history

### POS Integration

- Integration with 100+ POS providers globally
- Order dispatch to existing POS system
- Kitchen display system connectivity
- Menu sync via POS (Toast, Otter, Deliverect, etc.)
- Modifier sync via POS
- Real-time inventory sync
- No duplicate menu editing (POS overrides)
- Self-signup integration through partner marketplace
- Toast + Uber Direct integration
- Order management API (two modes: vendor device or full POS)
- Uber Eats Orders tablet app as fallback
- Menu hours sync via POS
- Product data sync via POS
- POS middleware layer for standardised connectivity

### Uber Direct Integration

- Uber Direct API for on-demand delivery
- Integration partners (certified program)
- Webhook status updates
- Proof of delivery
- Sandbox testing
- eCommerce platform integrations (Shopify, etc.)
- POS integrations for first-party delivery

### SFTP Integration

- SFTP integration for catalog upload
- SFTP integration for promotion upload
- Batch product updates via SFTP

### Partner Ecosystem

- Toast
- Otter
- Deliverect
- Square
- HungerRush
- Lavu
- SumUp
- MikMak
- Foodiv
- Winston POS
- 100+ total integration partners
- Self-serve onboarding for qualified partners

---

## 15. Uber Eats Ads / AdTech

### In-App Advertising Formats

- Sponsored listings in search results
- Promoted restaurant/store cards in feed
- Homepage banner ads
- Deal Drops (time-bound promotional offers, Jun 2026)
  - 1-hour window before cultural events
  - Push notification alerts
  - Home feed placement
  - Dedicated deals hub
  - Inventory caps for scarcity
- Reorder Rewards (post-purchase incentive, Jun 2026)
  - Surprise reward after each order
  - Auto-applied at next checkout
- Journey Ads (in Uber rides, cross-platform)
- Journey Takeover (premium brand map display, Jan 2026)
- In-car tablet ads (JourneyTV, JourneyTV Presents)
- Carousel banner ads
- Sponsored product listings in grocery
- Home screen ad (full takeover or banner)
- Order tracking page ad placement
- Shopping ad (grocery/retail)
- Full-page interstitial ad
- Cart upsell placement (before checkout)
- Payment method promotion at checkout
- In-app media placements

### Off-App Advertising

- Open internet display ads (via programmatic)
- Email marketing
- Push notification campaigns
- Retail media integrations (Kroger partnership)
- Cross-platform Uber rides advertising
- Journey Ads programmatic access (10 European markets, Jun 2025)

### Targeting & Analytics

- First-party purchase data targeting
- Audience segmentation by order history
- Demographic targeting (location, age)
- Behavioural targeting (cuisine preferences, order timing)
- Lookalike audience modelling
- Campaign performance analytics
- Real-time campaign optimisation
- Conversion tracking
- ROAS measurement
- Brand lift studies
- Incrementality testing
- Uber Intelligence data collaboration platform (Dec 2025)
  - LiveRamp clean room integration
  - Combined customer + Uber signals
  - Privacy-compliant measurement
- Adelaide + Kantar attention metric (Oct 2025)
- In-store traffic measurement
- Add-to-cart rate measurement

### Self-Serve Tools

- Ads Manager dashboard
- Campaign creation and management
- Budget management
- Performance reporting
- Audience builder
- Creative management
- Self-serve for restaurant advertisers
- Ads APIs for campaign management (Jun 2026)
  - POS integration for ad management
  - CPG brand direct access
- Media kit generator

### Partnerships

- Coca-Cola (Journey Takeover launch partner)
- Joe & The Juice (Deal Drops partner)
- LiveRamp (data clean room)
- Adelaide + Kantar (attention metrics)
- The Trade Desk (programmatic)
- Retail media networks (Kroger)
- $1B+ ad run rate (2025)
- Rider bag ads (physical O2O branding on delivery bags, limited markets)
- Product sampling campaigns (in-bag product samples, CPG partnerships)
- Off-app ad extension to Meta and Google Shopping (Jun 2026)

### Privacy & Controls

- Marketing and advertising preferences (personalised ads opt-out via Privacy Center)
- Rides + Eats unified ad preferences

---

## 16. Rider/Delivery Person App — Onboarding & Sessions

### Registration

- Download driver app (iOS/Android)
- Create profile
- Upload required documents (ID, driver's licence, vehicle insurance)
- Identity verification
- Background check
- Vehicle registration
- Training completion
- Minimum age requirements (per market)
- Social Security Number (US) or equivalent
- Criminal background check (Fair Chance Act compliance)

### Requirements

- Smartphone (iOS/Android)
- Vehicle type options
  - Bicycle
  - Motorcycle
  - Car
  - Scooter
  - Walker (on foot, limited markets)
- Valid driver's licence (motorised vehicles)
- Insurance coverage
- Delivery bag (high-visibility Uber Eats branding)
- Safety equipment
- Rider insurance enrolment
- Tax information submission

### Session Management

- Go online/offline toggle
- Session start confirmation
- Session end summary
- Auto-logout after inactivity
- Break mode
- Zone/area selection
- Scheduled sessions (market-specific)
- Destination transparency (view destination before accepting)
- 12-hour daily driving limit
- Driving time notifications (2h, 1.5h, 1h remaining)
- 6-hour offline reset for driving limit
- Trip planner at pickup (batch order management)
- Verification screen at pickup (item/order verification)
- Cross-zone delivery (courier accepts deliveries across zone boundaries)
- Minimum session hours (select markets)
- Schedule/booking system (select markets)
- Shift allocation (scheduled markets)
- Score-based scheduling (rider performance affects shift access)
- Extended delivery opt-in (longer-distance orders)

### Onboarding Support

- Training materials
- Safety training
- Help centre in-app
- Driver community forums
- Support chat/phone
- Referral programme (refer a friend)
- Rider compliance page (penalties, fines, demerit points for violations)
- Traffic rule refreshers
- Rider equipment ordering portal
- New joiner fee information page
- Referral fees information page
- E-bike compliance and guidelines

---

## 17. Rider/Delivery Person App — Delivery & Earnings

### Order Acceptance

- Incoming order request notification
- Merchant name and location display
- Customer delivery address display (destination transparency)
- Estimated distance display
- Estimated earnings display (including tip)
- Accept/decline order
- Auto-accept timer
- Order queue (multiple orders)
- Batched courier offers (multiple orders from same merchant)
- Second offer hidden until first accepted
- Preferred Deliveries icon (Uber Eats Pro tier benefit)

### Navigation

- In-app navigation (turn-by-turn)
- Google Maps / Waze integration
- Merchant location marker
- Customer location marker
- Optimised route suggestion
- Real-time traffic data
- Trip planner at pickup (multi-order routes)
- Departure screen (navigation start confirmation)

### Earnings

- Per-delivery base fee
- Distance-based fee
- Time-based fee (peak hours)
- Surge pricing (high-demand periods)
- Boost promotion earnings
- Quest incentives (complete X deliveries = bonus)
- Weekly earnings summary
- Daily earnings breakdown
- Transparent fee breakdown (per trip)
- Delivery person tip (100% to courier)
- Referral bonus
- New joiner incentive
- Uber Pro Card cashback (gas)
- Instant pay/on-demand payout (some markets)
- Weekly direct deposit
- Weekly earnings targets/challenges
- Monthly earnings report

### Delivery Flow

- Navigate to merchant
- Order pickup confirmation
- Order items verification (verification screen)
- Navigate to customer
- Delivery confirmation
- Proof of delivery (photo)
- "Leave at door" photo capture
- Call customer (in-app call masking)
- Message customer (in-app chat)
- Contact support during delivery
- Order issue reporting
- Return order flow (if delivery fails)
- Single drop-off flow (streamlined, Oct 2025)
- Drop-off problem resolution screen
- Proof of delivery via QR code

### Courier-Only Features

- Uber Eats Pro hub (rewards, tier status)
- Uber Pro Card (banking/financial product)
- Costco Gold Star membership (first year free, Platinum tier)
- ASU tuition coverage (100%, qualified tiers)
- Cashback on gas (Uber Pro Card)
- Premium Support (Diamond tier, live support agent)
- Driver shop (equipment purchase)
- Refer a friend programme
- Help centre
- Driver community/social
- Rider insurance portal
- Rider perks and deals page
- Rider events and happenings page

---

## 18. Rider/Delivery Person App — Safety & Well-being

### Safety Toolkit

- Audio recording (in-app, for safety incidents)
- Share trip with trusted contact (real-time)
- Emergency assistance button (connects to 911/Aura)
- Aura on-demand emergency response platform
- Destination transparency (view location before accepting)
- 12-hour daily driving limit
- Driving time countdown notifications
- Seat belt reminders
- High-visibility Uber Eats delivery bag and jacket
- PPE distribution partnerships
- Predictive risk prevention (telematics data)
- Motion-based risk signals
- Safety workshops and training
- Helmet distribution initiatives
- Safety kits and reflective decals

### Insurance & Protection

- $1M liability insurance (Uber-provided, during active deliveries, US)
- Contingent comprehensive and collision (auto, for drivers carrying personal insurance)
- Occupational accident insurance (select markets)
- Injury protection plan (per-mile coverage, some markets)
- Disability payments (up to $1,324/wk for qualifying injuries, CA Prop 22)
- Medical payments coverage (up to $5,000 per incident)
- On-trip accident insurance (covers medical expenses up to $1M, select markets)
- WICA / workers compensation insurance
- Medical leave coverage
- Hospitalisation leave coverage
- Permanent incapacity compensation
- Death compensation insurance

### Well-being

- Mental health support resources
- Driver well-being programmes
- Rest break reminders
- Driver hour limits (regulatory compliance)
- Financial literacy resources (via Uber Pro)
- Health insurance access (some markets)
- 24/7 safety support hotline (dedicated team for delivery persons)
- Bike lane navigation (prioritised routing for bicycle couriers, select cities)
- Safety gear recommendations (helmet, reflective vest, phone mount)
- Adverse weather alerts and guidance (extreme heat, storms, flooding)
- Deactivation protection (earnings records and dispute process for deactivations)
- Free safety kit distribution (reflective decals, phone mount, first aid, limited markets)
- Rider recognition awards (periodic)
- Rider community events and gatherings
- Peer support network
- Rider Safety Month / seasonal safety campaigns
- Maio Amarelo traffic safety campaign (Brazil, May 2026)
- Government collaborations for rider safety (per market)
- Petrol/gas subsidies (select markets)
- Phone/data plan subsidies (select markets)
- Health check-up programmes (select markets)
- Upskilling and career advancement programmes
- Financial literacy workshops
- Personal growth programmes
- Rider appreciation programmes
- Retail and restaurant partner discounts for riders
- Rider equipment discounts

### Safety Technology

- AI-based risk detection
- Real-time safety monitoring
- Rider/driver matching verification
- ID verification for alcohol deliveries
- Two-way ratings system (accountability)
- Fraud detection (account takeovers, fake orders)
- Localised safety data ingestion (encrypted SDKs)
- Centralised safety data lake
- Stream processing for real-time anomaly detection
- Batch processing for safety model training

### Partnerships

- Aura (emergency response platform)
- Big Boy Fourways (safety gear partnerships, South Africa)
- Local regulatory collaborations (per market)


---

## 19. Rider/Delivery Person App — Uber Eats Pro Rewards & Tiers

### Uber Eats Pro Programme

- Four tiers: Green, Gold, Platinum, Diamond
- Tier evaluation based on points and metrics
- Points earned per qualifying delivery
- Tier status display in driver app
- Tier progress tracker
- Quarterly/periodic evaluation cycles
- Points threshold system
- Points-based rewards programme (earn points per delivery)
- Redeem points for platform orders
- Partner promotions and discounts via points
- Point balance view in app
- Tier-based earnings multipliers
- Seasonal tier reset

### Tier Criteria

- **Gold**: 30%+ acceptance rate, 8% or less cancellation, 90%+ satisfaction, 70%+ on-time (select markets), 25 points
- **Platinum**: 50%+ acceptance rate, 8% or less cancellation, 95%+ satisfaction, 80%+ on-time (select markets), 80 points
- **Diamond**: 70%+ acceptance rate, 5% or less cancellation, 98%+ satisfaction, 90%+ on-time (select markets), 200 points
- **Green**: No minimum requirements (entry level)
- Acceptance rate criteria varies by market (50% in select markets for Gold)
- Satisfaction rate based on customer thumbs up/down
- On-time rate based on scheduled vs actual pickup
- Cancellation rate: orders accepted but not completed

### Tier Rewards

- **Preferred Deliveries** (Gold+): Priority access to higher-paying deliveries
  - Gold: Standard priority
  - Platinum: Higher priority over Gold
  - Diamond: Highest priority
- **Premium Support** (Diamond): Live support agent during trips
- **Cashback on gas** (Uber Pro Card, all tiers)
- **Costco Gold Star membership** (first year free, Platinum/Diamond)
- **100% tuition coverage at ASU** (qualified tiers)
- **Uber Pro Card** (banking with instant pay)
- **Discounts on maintenance, phone plans, etc.**

### Rider Referral

- Refer a friend programme
- Referral bonus per new active driver
- New joiner incentive
- Referral tracking in app
- Referral earnings credited to account
- Rider referral tracking dashboard

---

## 20. Platform — AI Dispatch & Operations

### Dispatch Engine

- AI-based delivery person dispatch
- Order batching (multiple orders per trip)
- Route optimisation algorithm
- Real-time demand forecasting
- Courier-to-order matching (proximity + capacity)
- Estimated delivery time calculation
- Dynamic dispatch zone management
- Multi-order assignment (batched courier offers)
- Second offer hidden until first accepted (Oct 2025)
- Preferred Deliveries routing (tier-based priority)

### Demand & Supply Management

- Heatmaps of demand density
- Supply/demand balancing
- Surge pricing (high-demand periods)
- Courier allocation to high-demand zones
- Predictive demand modelling
- Dynamic pricing per zone/time
- Promotional intensity per zone
- Heatmaps of micro-district demand

### AI/ML Features

- AI-powered personalised restaurant recommendations
- AI Cart Assistant (grocery image/text-to-cart, Feb 2026)
- AI customer review summary for merchants (Apr 2025)
- AI-generated menu descriptions (Jul 2025)
- AI-enhanced food photo quality (Jul 2025)
- Search ranking algorithm
- Restaurant ranking optimisation
- Cuisine preference modelling
- Basket analysis
- Customer churn prediction
- Menu item popularity prediction
- Fraud detection (payment, orders)
- Inventory prediction model (reduced cancellations, May 2026)
- Cart Assistant learning from past purchases
- Real-time traffic integration for ETAs
- Delivery time AI optimisation (20% reduction in major cities)
- Order accuracy boost metric (AI-driven)
- User preference prediction (ML model)
- Order latency tolerance prediction (delay-aware routing)
- Rider safety risk prediction (ML-based)
- Automated moderation of customer reviews

### Real-Time Operations

- Order status tracking system
- Live courier GPS streaming
- Real-time inventory management (grocery/retail)
- Automated merchant order routing
- Kitchen display system connectivity
- Picklist generation (grocery/retail)
- Packing workflow management
- Picker assignment (grocery/retail)

### Autonomous & New Technology

- Robotaxi partnerships (Waymo, Motional, Avride, WeRide, Nuro)
- Starship Technologies autonomous sidewalk robot delivery (Leeds Dec 2025, global partnership, Europe 2026, US 2027)
- Avride robot delivery for Uber Eats (Arlington VA, Jun 2026, customer chooses bot vs human courier, no tips for robots)
- Serve Robotics + White Castle autonomous robot delivery (Mar 2026)
- Nvidia Drive software partnership
- Drone delivery research (limited)
- Uber Air / Joby Aviation partnership (air taxi)
- Cartken autonomous delivery (select markets)

---

## 21. Platform — Dark Store / HUB Operations

### Dark Store / Grocery Fulfilment

- In-store fulfilment (retail/grocery partners pick from existing stores)
- Dedicated pickers (retail staff or Uber-managed)
- Real-time inventory tracking
- Product substitution management
- Quality control checks
- Temperature control for perishables
- Packaging standards for delivery
- Ready-to-deliver staging area

### Hub Operations (Uber-managed facilities)

- Micro-fulfilment centres (limited markets)
- Inventory arrangement for picking efficiency
- Climate-controlled zones (fresh, frozen, ambient)
- Layout optimisation for speed
- Localised stock planning (data-driven)
- Purpose-built for delivery (no walk-in retail)
- Custom shelving and racking

### Picking & Packing

- Optimised picking routes within store
- Barcode/QR scanning for item verification
- Weight verification for bulk items
- Quality control checks
- Temperature-controlled transport for perishables
- Packaging standards
- Ready-to-deliver staging area
- Dedicated pickup zone for couriers

### Inventory Management

- Real-time stock tracking
- Automated reorder triggers
- Supplier integration
- Demand forecasting per SKU
- Expiry date management
- Fresh produce daily planning
- Waste management
- Inventory prediction model (AI, May 2026)
- Out-of-stock reduction algorithms
- Slow-moving item alerts
- Fresh produce daily replenishment
- Supplier portal

---

## 22. Platform — Data, Analytics & Compliance

### Data Infrastructure

- Centralised data platform
- Regional data handling (GDPR, local compliance)
- Encrypted data in transit and at rest
- Secure cloud environments
- Real-time data streaming
- Batch processing (ML training)
- Data lake architecture
- Privacy-compliant data sharing (LiveRamp clean room)

### Analytics

- Sales analytics (Uber Eats Manager)
- Customer behaviour analytics
- Merchant performance analytics
- Courier performance analytics
- Operations dashboards
- Financial reporting
- Business intelligence tools
- A/B testing framework
- Customer acquisition cost tracking
- Customer lifetime value modelling
- Uber Intelligence (data collaboration platform, Dec 2025)
- Scheduled reporting (automated, Apr 2025)
- Customer group insights (geographic, new vs returning, Apr 2025)
- Payouts and earnings reporting

### Compliance

- GDPR compliance (European operations)
- CCPA/CPRA compliance (California)
- Local data protection regulations per market
- PCI DSS payment security
- Privacy policy and cookie consent management
- Data deletion request handling
- Privacy settings dashboard (emergency data sharing, notification preferences, third-party data sharing)
- Separate Privacy Notice for riders/order recipients and drivers/delivery people
- 90-day data deletion window after account deletion request
- Data encrypted at rest and in transit
- Regulatory reporting (per market)
- Fair Chance Act compliance (NYC background checks)
- Proposition 22 compliance (California)
- Seattle ICP and ABWMP ordinance compliance
- DOT/commercial driving regulations
- Tax reporting (1099-NEC, VAT, GST per market)
- Accessibility compliance (ADA, WCAG)
- Localised data ingestion pipelines per market
- Anonymised data for advertising analytics

---

## 23. Payment Methods & Financial

### Online Payments

- Credit cards (Visa, Mastercard, Amex, Discover)
- Debit cards
- Uber Cash (digital wallet)
  - Pre-load funds
  - Earn via Uber One credits
  - Refund to wallet
  - Cashback to wallet
  - Wallet-to-card transfer (Uber Cash withdrawal to bank/card, select markets)
- PayPal
- Apple Pay
- Google Pay
- Venmo (US)
- Klarna (BNPL, select markets)
- Afterpay (BNPL, select markets)
- SEPA direct debit (EU)
- iDEAL (Netherlands)
- Bancontact (Belgium)
- Sofort (Germany/Austria)
- PayPay (Japan)
- LINE Pay (Japan)
- Rakuten Pay (Japan)
- Card tokenisation (saved cards)
- 3D Secure authentication
- Bank transfer (select markets)
- Touch 'n Go eWallet (Malaysia)
- WeChat Pay (select markets)
- Alipay (select markets)
- GrabPay (Southeast Asia)
- Boost (Malaysia)
- Online banking / FPX (Malaysia)

### Offline Payments

- Cash on delivery (select markets)
- Card on delivery (select markets)

### Payment Features

- PCI DSS compliant processing
- Single-click reorder payment
- Saved payment tokenisation
- Refund to original payment method
- Partial refunds
- Payment history
- Transaction receipts (email)
- Invoice download
- Auto-payment on delivery
- Fiserv payment processing (select markets)
- Cybersource tokenisation
- Refund to platform wallet
- Unified reporting, billing, settlements
- Uber Cash earned on rides via Uber One

### Financial Partnerships

- Visa (payment processing, global)
- Mastercard (payment processing)
- American Express (payment + Delta partnership)
- PayPal
- Klarna
- Afterpay
- LiveRamp (data collaboration)
- Multi-acquirer processing support
- Token management service (card-to-digital-token)
- CTBC Bank co-branded credit card (Taiwan)
- HSBC cashback partnership (select markets, weekends)
- Funding Societies merchant financing
- AEON Bank merchant financing

### Fees for Customers

- Delivery fee (distance/time-based, variable)
- Service fee (5-15% of order, market-dependent)
- Small order fee (if below minimum)
- Priority delivery fee (extra charge)
- Long-range delivery fee (extra charge)
- Surge pricing (high demand)
- Fuel surcharge (added during fuel price spikes, US/Canada, Mar 2022)
- Packaging fee (market-specific, separate line item)
- Rider fee (market-specific, separate line item)
- Platform fee (per-market pricing)
- Uber One membership ($9.99/mo)
- Tip (optional, 100% to courier)

### Merchant Commission

- Commission per order (plan-based: Lite 20%, Plus 25%, Premium 30%)
- Uber One member orders: Plus tier increases to 30% (Mar 2026)
- Pickup commission: 7%
- Custom rates: +3% increase (capped at 30%)
- Advertising costs (Uber Eats Ads)
- Promotion costs
- Registration fee

### Delivery Person Earnings & Banking

- Uber Pro Card (debit card with instant pay)
- Instant pay / on-demand cash-out
- Weekly direct deposit
- Gas cashback (Uber Pro Card)
- ASU tuition benefit (taxable benefit)
- Earnings breakdown per trip (base, distance, time, tip)

---

## 24. Promotions, Vouchers & Loyalty

### Promo Codes & Discounts

- Promo code entry at checkout
- New user discount ($10 off first $20+ order)
- Free delivery promotions
- Percentage discounts (10%, 20%, 30%, 50% off)
- Fixed amount discounts ($X off)
- Spend threshold discounts
- Category-specific promos (pizza, sushi, etc.)
- Time-limited promos (flash sales)
- Deal Drops (time-bound event promos, Jun 2026)
- Seasonal campaign codes
- First-order promo for new customers
- Referral codes (give $X, get $X)
- Uber One-only promotional offers
- Member Days (periodic member-exclusive savings)

### Voucher System

- Auto-applied vouchers at checkout
- Voucher terms and conditions
- Voucher stackability rules
- Minimum order value vouchers
- Expiry date tracking
- Voucher from third-party sources (RetailMeNot, etc.)
- Gift card code redemption
- Promo balance display in wallet

### Loyalty Programme

- Uber One subscription (paid loyalty, primary loyalty programme)
- Points-based loyalty programme (earn points per order)
- Tiered loyalty rewards (basic → premium tiers)
- Points-based loyalty (limited markets, partner-specific)
- Kroger Boost cross-integration (2026)
  - 6% Uber Cash back on rides
  - $0 Delivery Fee on Uber Eats
  - 2X fuel points on Kroger purchases
- yuu Rewards Club (Taiwan — partner)
- Hotel/airline partnerships (Delta, Marriott, etc.)
- Credit card rewards integration (Amex Membership Rewards, Chase Ultimate Rewards)

### Market-Specific Subscriptions

- Priority Plus-style subscription tier (select markets with zero delivery fees)

### Reorder Rewards (Jun 2026)

- Surprise reward after each completed order
- Auto-applied to next order at checkout
- Encourages repeat purchase behaviour
- Available to restaurant advertisers

### Promo Mechanics

- Free delivery promotions
- Bundled deals
- Combo meals
- Strikethrough pricing (was/now)
- Happy hour discounts
- Student discounts
- Fresh Days (weekly grocery, up to 50% off fresh items)
- Fresh Tuesdays (Uber One member-specific, up to 30% off)
- Coupon codes from partner brands
- Ibotta Performance Network digital coupon integration (grocery/retail CPG, Mar 2026, multi-year exclusive)
- BOGO (buy-one-get-one) deals (select markets)

### Gamification

- Uber Eats Pro tiers (delivery persons)
- Quest incentives (delivery persons)
- Boost promotions (delivery persons)
- Surprise perks (Uber One members)
- Reorder Rewards (customers)
- Referral rewards (both sides)
- Daily challenges for customers (limited markets)

### Refund Policy

- Free order cancellation up until store accepts order
- Cancellation after store acceptance may incur charges
- Full cash refund policy for missing/incorrect orders (California AB 578, Jan 2026): refund includes food cost, taxes, and tips; issued to original payment method; human customer service agent available for refund requests
- Refund policy varies by market (legislation-dependent)
- In-app credit vs cash refund determined by market regulations


---


## 25. Marketing, CRM & Campaigns

### CRM & Lifecycle

- Personalised push notification campaigns
- Email marketing
- SMS marketing
- In-app messages
- Lifecycle automation (welcome, win-back, re-engagement)
- Personalised offer sequencing
- Time-of-day targeting
- Tenure-based offers
- Order history-based targeting
- Abandoned cart recovery
- Braze CRM platform integration
- Uber One member lifecycle (free trial → paid conversion)
- Re-engagement for lapsed users

### Campaigns

- Seasonal/cultural campaigns (Valentines, Mothers Day, Halloween, Christmas)
- Sports event campaigns (Super Bowl, World Cup, Olympics)
- Back to school promotions
- Uber One Member Days (May 2026)
- Fresh Days weekly program
- Deal Drops (cultural events, Jun 2026)
- Local restaurant highlight campaigns
- GO-GET 2026 campaign (one app for everything, Apr 2026)
- Travel Concierge mode (curated local recs, hotel room service delivery, forgotten items delivery, GO-GET Apr 2026)
- Women rider initiatives
- Offline activations (physical marketing events)
- Short-form video content strategy (TikTok, Reels)
- Seasonal cuisine narratives
- Payday promotions

### Media & Social

- Instagram presence (@ubereats, per-market accounts)
- Facebook presence (per market)
- TikTok presence (@ubereats)
- Twitter/X (@UberEats)
- YouTube (Uber channel)
- LinkedIn (Uber for Business)
- WhatsApp Business integration
- LINE presence (Taiwan, Japan)
- Influencer marketing (local food creators)
- User-generated content campaigns
- Food photo incentives ($3 Uber Cash, Jul 2025)

### Customer Engagement

- Push notification categories (order, promo, account)
- In-app notification centre
- Personalised daily deals
- Rate your meal / rate your delivery person
- Restaurant review system (stars + written)
- Photo reviews (user-submitted food photos)
- User-generated content (UGC) programme
- Food photo request for un-imaged menu items
- Live Order Chat between merchant and customer (Jul 2025)
- In-order feedback prompts (Dish-out style, rating per item)

### Merchant Marketing

- Co-marketing with restaurant partners
- Joint brand partnerships
- Success story features
- Insights hub (articles, guides)
- Merchant awards/recognition
- Promotion management tools

### Heatmaps

- Micro-district demand heatmaps for marketing allocation
- Restaurant supply alignment heatmaps
- Promo intensity allocation per district
- Rider allocation per zone for campaigns

### Cross-Platform Marketing

- Uber rides app integration (cross-promotion)
- Uber One cross-platform (rides + eats)
- Journey Ads (in-ride advertising)
- Uber Eats promotions within Uber rides app
- Bundled offers (ride + meal)
- Eats for the Way (order coffee/snacks for Uber ride drop-off, LA/SF/SD/Atlanta, May 2026)
- Expedia hotel booking partnership (in-app hotel booking via Expedia Group, microphone voice search, Apr 2026)

---

## 26. Brand, History & Sustainability

### Brand

- Brand colour: Black and white (Uber Eats logo/wordmark)
- App icon: White fork on dark background
- Tagline: "Food delivery" / "Order food delivery online"
- Uber master brand integration (same app ecosystem)
- Uber Eats Pro programme branding
- Uber One sub-brand
- Localised branding per market

### History Timeline

- 2009: Uber founded by Travis Kalanick and Garrett Camp
- Aug 2014: UberFRESH launched in Santa Monica, CA
- 2015: Renamed UberEATS; standalone app launched in Toronto
- 2016: Launched in London and Paris
- 2017: Rebranded to Uber Eats; Travis Kalanick ousted as CEO
- 2017: Dara Khosrowshahi appointed CEO
- 2018: Sold SE Asia operations to Grab (27.5% stake)
- 2019: Uber IPO (May); $3B invested in Uber Eats
- 2020: Acquired Postmates ($2.65B, Dec)
- 2020: Acquired Drizly ($1.1B, alcohol delivery)
- 2020: Uber Eats Pass launched (predecessor to Uber One)
- 2021: Uber One launched (unified rides + eats subscription)
- 2021: Sold Uber Eats India to Zomato
- 2021: Acquired Cornershop (Latin America grocery)
- 2021: Space delivery to ISS with Yusaku Maezawa (Dec)
- 2022: Fuel surcharge added to US/Canada deliveries (Mar)
- 2022: Drizly operations shut down (2024)
- 2023: Postmates integration into Uber Eats
- 2023: Uber Eats Pro updated with Preferred Deliveries
- 2024: Uber Eats + Instacart partnership (restaurant delivery in Instacart app)
- 2025: Uber Eats Pro relaunched with revised criteria (May)
- 2025: Merchant AI tools launched (Jul)
- 2025: Kroger expanded partnership (Oct)
- 2025: Acquired Trendyol Go ($700M, Turkey, May)
- 2025: OpenTable partnership (Mar)
- 2025: Fresh Days program launched (Sep)
- 2026: AI Cart Assistant launched (Feb)
- 2026: Cart Assistant for grocery (Feb)
- 2026: Uber One service fee discount retired for new members (Mar)
- 2026: Marketplace fee update (tiers increased, Mar)
- 2026: Deal Drops and Reorder Rewards launched (Jun)
- 2026: Ads APIs launched for developers (Jun)
- 2026: Grocery category visibility and item ratings (May)
- 2026: Uber Elite launched (ride-hailing loyalty, Mar)
- 2026: Robotaxi service with Motional in Las Vegas (Mar)
- 2026: AI inventory prediction model upgrade (May)
- 2026: Kroger full assortment integration (beginning 2026)
- 2025: Starship Technologies autonomous robot delivery partnership announced (Nov)
- 2026: Alexa+ voice ordering integration (Mar)
- 2026: Ibotta grocery coupon partnership (Mar)
- 2026: Serve Robotics + White Castle autonomous delivery (Mar)
- 2026: Expedia hotel booking integration (Apr)
- 2026: Eats for the Way launched (May)
- 2026: Avride robot delivery pilot in Arlington, VA (Jun)
- 2026: European expansion announced — 7 new countries: Austria, Czech Republic, Denmark, Finland, Greece, Norway, Romania (Feb)
- 2026: Resumed operations in Argentina (Mar)
- 2026: Maio Amarelo traffic safety campaign (Brazil, May)
- 2026: Space delivery anniversary promotion (Dec)

### Company Facts

- Parent: Uber Technologies, Inc.
- CEO: Dara Khosrowshahi (since Aug 2017)
- Global Head of Delivery: Susan Anderson (Jun 2025)
- HQ: San Francisco, California, USA
- Founded: Aug 2014 (as UberFRESH)
- 50+ countries
- 11,500+ cities
- 1.5M+ merchants
- 6M+ delivery persons
- 2025 Delivery revenue: $13.7B
- 2025 Uber total revenue: $52B
- NYSE: UBER
- Market cap: ~$140B (Jun 2026)
- 34,000 employees (Uber total)
- S&P 500 component

### Overseas Markets

- Argentina, Australia, Belgium, Brazil, Canada, Chile, Costa Rica, Denmark, Dominican Republic, Ecuador, El Salvador, Finland, France, Germany, Guatemala, Ireland, Italy, Japan, Kenya, Luxembourg, Mexico, Netherlands, New Zealand, Norway, Panama, Poland, Portugal, South Africa, South Korea, Spain, Sri Lanka, Sweden, Switzerland, Taiwan, Turkey (via Trendyol Go), United Kingdom, United States
- Expansion announced Feb 2026: Austria, Czech Republic, Greece, Romania
- Exited: Southeast Asia (sold to Grab 2018), India (sold to Zomato 2021)

### Sustainability

- 100% carbon neutral by 2040 target (Uber corporate, Sep 2022)
- Zero-emission platform commitment
- SBTi (Science Based Targets initiative) approved emissions reduction targets
- EV courier incentives (bonus per EV trip, some markets)
- Sustainable packaging initiatives (market-specific)
- Greener packaging grants (with Visa, $1M, Jan 2023)
- Green Packaging Badge (labels eco-friendly packaging on restaurant pages)
- No cutlery opt-out (app toggle, some markets)
- Green Mode (opt out single-use plastics for cashback)
- Less plastic cutlery initiative
- Zero waste kitchen partnerships
- Plant-based and sustainably-grown product promotion
- Electric vehicle partnerships (EV charging discounts)
- Zoomo partnership (e-bike leasing for delivery persons, US/AU/UK)
- Zenion partnership (e-motorcycle leasing for delivery persons, select markets)
- 3,000+ e-motorcycles deployed via partnerships
- $800M Green Future commitment (sustainability investment)
- Carbon tracking (limited markets)
- Carbon offset programme (limited markets)
- Reduced packaging waste initiatives
- Local sourcing programmes
- Autonomous/delivery robot pilots (lower carbon footprint)
- Public transit integration (some markets)
- Rebecca Tinucci appointed Head of Sustainability (2024)
- Waste reduction through inventory prediction AI (fewer cancelled/spoiled orders)
- EV-only delivery zones pilot (select cities, limited hours)
- Cultured meat delivery pilot history (select markets)
- Reusable packaging programme (limited, select markets)
- Recycling partnerships (select markets)
- EV battery swapping pilot (select markets)
- Government EV fleet partnerships (select markets)
- Autonomous robot delivery pilots (sidewalk bots, select cities)

### Social Impact

- Uber Eats Grants for Growth ($10K microgrants to small businesses)
- Fair Chance Hiring (background check reform)
- Women rider initiatives
- ASU tuition programme (driver education)
- Accessibility product features
- Women Preferences for delivery persons (opt-in to receive trip requests from women customers, Mar 2026)
- Gas Savings programme for US drivers (discounts at participating stations, 2026)
- Veteran hiring programmes
- COVID-19 relief efforts (free meals for healthcare workers)
- Local restaurant support programmes
- Food bank partnerships (limited)
- Digital inclusion programmes
- Female entrepreneur upskilling
- Women rider upskilling
- Pro-bono financial workshops for riders
- MOU with government agencies for rider support formalisation
- Home chef / cottage food seller initiative

---

## 27. Controversies & Challenges

### Worker Classification

- Drivers/delivery persons classified as independent contractors
- Proposition 22 (California, 2020) — drivers independent but with benefits
- $8.4M settlement for California driver misclassification
- Seattle $15M settlement over ICP and ABWMP violations (Aug 2025)
- Aguilera v. Uber Eats ($3.35M Fair Chance Act settlement, 2024)
- Seattle gig worker pay claims ($15M, Dec 2025)
- California Prop 22 appeal rights lawsuit (Apr 2026)
- UK Supreme Court ruling (2021) — Uber drivers entitled to worker rights
- Employee classification debates in EU (France, Germany, Netherlands)
- Gig worker rights legislation globally

### Fee & Pricing Controversies

- NYC fee cap settlement (Jun 2025) — lawsuit against 20%+ service fees
- Service fees hidden/opaque — restaurant allegations of up to 20% per order
- Uber One misleading subscription benefits allegations
- FTC lawsuit (Apr 2025) — unauthorized Uber One enrollment, consumers charged without consent
  - Amended complaint (Dec 2025) — 21 states + DC joined
  - Alleged ROSCA (Restore Online Shoppers' Confidence Act) violations
  - Cancellation required 7+ screens / 12+ actions (32 actions within 48hrs of billing)
  - Charges applied before billing date / during free trial period
  - $25/month savings claims allegedly unsubstantiated
  - Trial scheduled Feb 2027
- Variable/dynamic minimum orders (2026) — criticism of policy change
- Taiwan fee adjustment controversy (Jun 2026) — 2.5pp increase to 35% cap
- EU regulatory scrutiny of platform fees

### Market Practices

- Aggressive acquisition strategy (Postmates, Drizly, Cornershop)
- SE Asia anti-competitive concerns
- India exit — allegations of unsustainable pricing to gain market share
- Taiwan market concentration concerns (Uber + Foodpanda attempted acquisition)
- Data-sharing with third parties (privacy concerns)

### Antitrust & Regulatory

- Antitrust investigations in EU and US
- NYC Delivery Fee Law (permanent cap on restaurant commissions)
- Seattle minimum pay ordinances (ICP, ABWMP)
- California Prop 22 legal challenges (AB5 debate)
- Taiwan Fair Trade Commission investigation
- EU Digital Markets Act compliance

### Safety Incidents

- Delivery person safety concerns (robberies, accidents)
- Food safety incidents (limited)
- Fraudulent order scams
- Account takeovers and payment fraud
- Driver background check concerns (Fair Chance Act violations)
- AI bias facial recognition settlement (Black courier denied earnings, Mar 2024)

### Criticisms

- High commission rates (up to 30%)
- Lack of transparency in fee breakdown
- Surge pricing during emergencies
- Driver pay dissatisfaction
- Data collection and privacy concerns
- Impact on local restaurant margins
- Market consolidation reducing competition
- Environmental impact of single-use packaging
- Labour rights concerns across markets
- Whistleblower hoax controversy (fabricated claims by Reddit user, Jan 2026)

### Market-Specific Controversies

- Thailand boycott (advert on political programme controversy)
- Malaysia hidden fees allegations
- Philippines rider protests (mass suspension controversy)
- Hong Kong rider strike (income promise disputes)
- India malpractice allegations (non-payments, fake listings)
- Taiwan competitor acquisition blocked by regulators

---

## 28. Metrics & KPIs

### Company Scale

- Operating countries: 50+
- Cities: 11,000+
- Merchants: 1.5M+
- Delivery persons: 6M+
- Monthly active platform users: 200M+ (Uber total)
- Average daily trips: 42M+ (Uber total)
- Total trips since inception: 72B+ (Uber total)
- Market-specific breakdowns (downloads, active users, merchants, riders, market share, revenue)

### Financials (Uber Delivery Segment — Uber Eats)

- Delivery gross bookings: ~$75B (2025)
- Platform-wide GMV
- Delivery revenue: $13.7B (2025, 19% YoY increase)
- Delivery operating income: $2.4B (2025)
- Adjusted EBITDA: $3.5B+ (Delivery segment, 2025)
- Uber total revenue: $52B (2025)
- Uber net income: $10B (2025)
- Uber total gross bookings: $130B+ (2025)
- Mobility take rate: 29.9% (Q4 2025)
- Delivery take rate: 19.2% (Q4 2025)

### Uber One Metrics

- Subscription price: $9.99/mo or $96/yr
- Student price: $4.99/mo (50% off)
- 30 million members (May 2025, 5M new in one month)
- Average monthly savings per member: $27
- Member frequency: higher order frequency vs non-members
- Cross-platform adoption (rides + delivery)
- Subscription membership growth (YoY by market)

### Uber Eats Ads

- Ad run rate: $1B+ (2025)
- Active advertisers: growing (launched Ads APIs Jun 2026)
- Deal Drops partners: increasing
- 75%+ delivery decisions within 1 hour (ad urgency insight)

### Payment Metrics

- Payment success rate
- Mobile payment adoption rate (by market)

### App Metrics

- Android downloads: 100M+
- Android reviews: 7.45M+
- Android rating: 4.6/5
- iOS rating: 4.8/5 (10M+ ratings)
- iOS app size: ~363.3 MB
- iOS requirement: iOS 17.0+
- Languages: 38+ supported

### Market Share

- US food delivery market: ~23% (2nd behind DoorDash 56%, ahead of Grubhub 16%)
- US grocery delivery: smaller share (behind Instacart, Walmart, Amazon)
- Global presence in 50+ countries
- Strong market positions: US, UK, Canada, Australia, Mexico, Brazil, France, Japan, Taiwan
- Competitive position varies by market

### Delivery Operations

- Average delivery time: market-dependent
- AI-driven delivery time reduction: 20% in major cities (Paris, Berlin)
- Same-day grocery delivery: hundreds of US cities
- Uber Direct delivery: thousands of cities
- Delivery area: up to 3 miles standard (longer with Long Range fee)
- Variable minimum orders: $12-$25 depending on merchant/time/distance

### Merchant Metrics

- 1.5M+ merchants globally
- 100+ POS integration partners
- Avg merchant order growth rate: varies by market
- Pickup commission: 7%
- Delivery commission plans: Lite (20%), Plus (25%), Premium (30%)
- Merchant satisfaction: increasing with AI tools

### Courier/Delivery Person Metrics

- 6M+ delivery persons globally
- Uber Eats Pro tiers: Green, Gold, Platinum, Diamond (4 tiers)
- Preferred Deliveries: priority access for Gold+
- 12-hour daily driving limit
- Instant pay availability: varies by market
- ASU tuition programme uptake: thousands enrolled

---

> **Note:** This masterlist was compiled across 4 investigation rounds using Uber's newsroom,
> Google Play/App Store listings, merchants.ubereats.com, developer.uber.com, Wikipedia,
> help.uber.com, Uber blog posts, tech press (TechCrunch, CNBC, Reuters), industry analysis,
> and targeted web searches on specific features and controversies.
>
> **Total: 1,474 micro-features (~1,415 primary + ~59 sub-bullets) across 28 sections, ~2,031 lines.**
> Round 4 gap analysis against FoodPanda masterlist added ~66 additional micro-features.
> Round 5 web investigation added ~9 new features from 2025-2026 partnerships and integrations.
> Round 6 FoodPanda cross-reference audit added ~12 new features across 9 sections from confirmed gaps.
> Round 7 saturation investigation via Wikipedia, App Store listings, and merchant product pages added ~9 new entries (fuel surcharge, Maio Amarelo safety campaign, ISS space delivery, European expansion to 7 new markets, Argentina re-entry, AI bias settlement, whistleblower hoax controversy, market additions).
> Round 8 targeted investigation (Uber Engineering blog, help.uber.com, Japan market payments, California AB 578 legislation, Food On Demand/FODC conference, Uber One Marriott Bonvoy partnership) added ~12 new features: LLM-powered semantic search, PayPay/LINE Pay/Rakuten Pay (Japan), Marriott Bonvoy partnership, free cancellation policy details, California AB 578 full cash refund law with human agent requirement, market-specific refund policies, 30M Uber One members metric.
> Round 9 privacy & FTC investigation (uber.com/privacy, uber.com/legal, FTC lawsuit docs, developer.uber.com, help.uber.com) added ~22 new features: Privacy Center dashboard, download your data, account deletion via Privacy Center, two-step verification for data access, device permissions management, cookie preferences, personalised ads opt-out, privacy settings dashboard (emergency data sharing, notifications, third-party sharing), separate Privacy Notice for drivers/riders, 90-day data deletion window, expanded FTC lawsuit details (21 states + DC, ROSCA violations, 7+ screen cancellation, billing date charges, $25/month claims), gift card 16-digit code format, cross-platform use, currency restrictions, 11,500+ cities metric update.

