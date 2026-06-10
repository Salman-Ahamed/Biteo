# COMPLETE MERCHANT FEATURE INVENTORY

## 1. PANDA PARTNER DASHBOARD (RESTAURANT PORTAL)

### Overview Dashboard

- Daily orders, sales, and performance metrics across all outlets in a single view
- Toggle between live (real-time) status and historical trends
- Week-on-week data comparison to identify growth areas and slow periods
- Real-time monitoring of cancelled orders, offline alerts, and one-star reviews
- System alerts and instant messages via notification panel
- Business summaries on orders and revenue
- Key Performance Indicator (KPI) overview
- Multi-outlet dropdown selector (top-right) for chain merchants
- Restaurant Portal University (embedded education/training)

### Live Orders Screen

- View all incoming, completed, or cancelled orders in real time
- Filter by outlet, date range, order status, or order ID
- Track preparation time, delivery status, and cancellation reasons
- Export up to 20,000 order records in Excel/CSV

### Panda Partner Mobile App (Android/iOS)

- Track live orders on the go
- Full sales and operations reports
- One-tap menu availability updates
- Adjust store opening hours
- Push notifications for new orders
- Issue resolution while mobile
- Offer discounts and join campaigns

---

## 2. MENU MANAGEMENT

### Item Creation and Editing

- Add dish name, description (including ingredients, size, allergens)
- Set item price with VAT
- Upload dish photo (drag-and-drop)
- Add translations for multiple languages
- Assign item to timetable (availability schedule)
- Assign item to category/categories
- Assign tags to items
- Link modifier groups (choice groups)
- Mark as age-restricted (alcohol) Yes/No
- Item variations (e.g., size, portion)

### Categories

- Create, rename, delete menu categories
- Drag-and-drop reordering of categories
- Add category name translations
- Sequential bulk category creation

### Choice Groups / Modifiers

- Create choice groups (e.g., "Choose side", "Choose drink")
- Add individual choices under each group
- Set pricing per choice
- Customer customization options

### Combo Sets

- Create combo/ bundle meal deals
- Set combo pricing rules

### Menu Strength Tool

- Track photo coverage percentage per item
- Track description coverage
- Identify gaps to improve listing quality

### Photo Management

- Photo guidelines and requirements (4000x2925 px, top/front view, no watermarks, no branding, JPEG format, landscape)
- Photo rejection reasons from review team
- Rename photos to match dish names
- Upload and replace item images

### Bulk Operations

- Copy menus across multiple outlets
- Track submission approvals
- Receive photo guidelines and rejection reasons

### Availability Controls

- Mark items unavailable today (temporary)
- Mark items unavailable indefinitely
- Mass availability toggles

### Menu Import (API/SFTP)

- Submit full catalog via Partner API (POST/PUT catalog endpoints)
- SFTP file-based import (CSV) for bulk catalog updates
- Single File Format, Double File Format, Multi-Vendor file format support
- Asynchronous processing for large catalogs
- Catalog import log and status tracking

---

## 3. ORDER MANAGEMENT

### Order Receiving

- Real-time order push via webhook (RECEIVED status)
- Order appears on Pelican app or partner's own picking device
- Notification bar and alert sound on POS

### Accept / Reject

- Accept incoming orders
- Reject with reason selection (CLOSED, OUT_OF_STOCK_UNAVAILABLE, TOO_BUSY, etc.)
- Manager authorization required for rejection (configurable)
- Auto-accept functionality (configurable on plugin or vendor app)

### Preparation / Fulfillment

- Mark order as "Prepared" (ready for pickup)
- Mark order as "Picked Up" (collected by rider or customer)
- Mark order as "Dispatched" (vendor delivery flow)
- Partial fulfillment support
- Kitchen Order Ticket (KOT) printing
- Official Receipt (OR) printing
- Reprint KOT and OR

### Order Modification (Partner Picking)

- Modify item quantities
- Modify item weight
- Replace out-of-stock items (one replacement per SKU)
- Add additional items to order
- Review items and update cart (UPDATE_CART status for validation)
- Price adjustment on original items only

### Cancellation

- Cancel order after acceptance (with reason selection)
- Handle customer-initiated cancellations
- Handle logistics-initiated cancellations
- Post-pickup cancellation flag detection
- Cancel reasons: CLOSED, OUT_OF_STOCK_UNAVAILABLE, TOO_BUSY, TECHNICAL_PROBLEM

### Delivery Flow Options

- Platform Delivery: rider picks up from restaurant
- Vendor Delivery: restaurant arranges own logistics
- Support for both logistics flows in API

### Order History & Reconciliation

- GET single order details by UUID (last 60 days)
- GET multiple orders by vendor ID with date range filter (last 60 days)
- Paginated results (default 20 per page)
- Order statuses: RECEIVED, READY_FOR_PICKUP, DISPATCHED, CANCELLED, DELIVERED
- Export 20,000+ order records in Excel/CSV

### Pelican Picking App (Android)

- Pick and fulfill customer orders
- Replace products in customer orders
- Change order prices of products
- Cancel an order
- Vendor acceptance toggle
- Enable/disable products for sale
- View order information
- Set store online/offline/busy
- Picker work scheduling
- Available with or without dedicated picking device

---

## 4. PERFORMANCE ANALYTICS

### Sales Reports

- Revenue analysis
- Order volume tracking
- Peak hour identification
- Top-selling items ranking
- Week-over-week sales comparison
- Download reports in multiple formats (Excel, CSV, PDF)

### Operations Reports

- Order rejection rate tracking
- Offline time monitoring
- Average preparation time
- Delivery delay tracking
- Week-over-week operational comparison

### Customer Reports

- New vs. returning customer analysis
- Customer conversion funnel
- Customer loyalty trends
- Customer preferences and behavior insights
- Demographic insights

### Data Insights Dashboard

- Business summaries on orders and revenue
- Daily orders, menu performance, revenue by hour
- Performance trends visualization
- Data analytics as a service (forecast data sold to merchants)

### External BI Integration

- Export data for Power BI, Tableau integration
- Cointab automated reconciliation integration

---

## 5. MARKETING TOOLS

### Panda Ads (Retail Media)

- **In-app advertising:**
  - Homescreen ad (reach at beginning of purchase journey)
  - Order tracking page ad (non-disruptive engagement)
  - Shopping ad (boost conversion on pandamart/shops)
  - Full-page pop-up (high-impact disruptive format)
  - Carousel banner (consideration & conversion)
  - Cart upsell (capture impulse purchases)
  - Payment switch (become payment provider of choice at checkout)
- **Off-app advertising:**
  - Marketing channels (email, social media)
  - Rider bag ads (O2O campaigns)
  - Product sampling (boost awareness and drive sales)
- **Strategic partnerships:**
  - Vouchers
  - Data partnerships
  - Consumer insights
- **Targeting capabilities:**
  - First-party data targeting
  - Advanced audience segmentation
  - 125M app downloads across 11 markets, 400+ cities

### Discount & Promotion Management (Dashboard)

- Pre-set promotions (one-click activation)
- Custom discount creation (choose type, value, target audience)
- Minimum order value conditions
- Panda Pro member exclusive discounts
- Smart pink discount tags on app
- Real-time performance tracking per promotion
- Start/end date scheduling
- Recurring promotion support
- Edit, cancel, or extend promotions with ease

### PandaClicks

- Brand visibility boosting service

### Campaigns

- Join platform-wide marketing campaigns
- Social media promotion support
- Push notifications via foodpanda app
- Featured/Sponsored listings

---

## 6. PROMOTIONS MANAGEMENT (API/SFTP)

### Promotion Types

- **Strikethrough discounts:**
  - Percentage off
  - Absolute value off
  - Final price
- **Same-item bundle discounts:**
  - Percentage off
  - Absolute value off
  - Free item

### API Promotion Management (Partner API/Promotions)

- PUT `/promotion` endpoint to create promotions
- Modify promotions (add/remove SKUs)
- Deactivate promotions (active: false)
- GET endpoint to check promotion status
- Promotion statuses: QUEUED, COMPLETED, FAILED
- Job status tracking

### SFTP Promotions

- Single File Format (Assortment + Promotions in one file)
- Double File Format (Catalog + Promotions in separate files)
- Multi-Vendor file format
- CSV-based upload to SFTP Central Server
- 3 sub-directories: Assortment, Catalog, Promotions

### Promotion Statuses Visible in Partner Portal

- Cancelled
- Ended
- Running
- Upcoming
- Start/end dates per promotion
- SKUs included
- Promotion name and reason (e.g., COMPETITIVENESS)

---

## 7. OUTLET MANAGEMENT (MULTI-LOCATION)

### Partner Portal Multi-Outlet Features

- Dashboard dropdown to switch between all outlets
- Copy menus across multiple outlets
- View all outlets' orders in one place
- Filter orders by outlet
- Sales and performance metrics aggregated and per-outlet
- User management delegation per outlet

### Partner API/Outlet Management

- PUT `/status` endpoint for outlet status updates
- GET endpoint to retrieve outlet status
- Store statuses:
  - OPEN
  - CLOSED_TODAY
  - CLOSED_UNTIL (with timestamp)
  - CHECKIN (acknowledge scheduled opening)
- `closed_reason` field (e.g., TECHNICAL_PROBLEM)

### Check-in Feature

- Acknowledge scheduled opening time
- Up to 30 minutes before scheduled opening
- If not checked in, store stays closed even if scheduled
- Enable/disable via account manager

### Opening Hours Management

- Set regular opening hours
- Schedule multiple shifts
- Temporary closures (e.g., holidays, renovations)
- Automatically sync hours with visibility to avoid rejections

### Third-Party Multi-Outlet Tools (Ecosystem)

- Klikit integration for multi-country, multi-outlet management
- Centralized menu management with location-specific pricing
- Real-time analytics across all locations
- Multi-brand support (manage different restaurant concepts)

---

## 8. PARTNER API V2 FEATURES

### Authentication

- OAuth 2.0 Bearer token (client_id + client_secret)
- Token valid for 2 hours
- Token management via Partner Portal

### Catalog Management API

- POST `/catalog` - Add new products (store or chain level)
- PUT `/catalog` - Update product status, price, max_sales_quantity
- GET `/catalog` - Retrieve products (paginated, filterable)
- GET `/categories` - Retrieve vendor categories
- POST export - Export product catalog (assortment data: SKU, price, active, max_sales_quantity)
- Bulk operations support
- Asynchronous processing for large catalogs
- Product attributes: SKU, price, active, max_sales_quantity, translations, descriptions, image URLs

### Order Management API (Partner Picking)

- Webhook endpoint for order events (RECEIVED, READY_FOR_PICKUP, DISPATCHED, CANCELLED, DELIVERED)
- PUT `/orders/{order_id}` - Fulfill, modify, replace, cancel orders
- UPDATE_CART status for item modification with validation
- GET `/orders/{order_id}` - Retrieve single order (last 60 days)
- GET `/vendors/{vendor_id}` - Retrieve multiple orders (date range, paginated)
- Item-level promotion information in order payload
- Post-pickup cancellation flag detection

### Order Management API (Pelican Picking)

- GET order by ID
- GET orders by vendor ID with date range
- Page size and page number parameters
- Orders accessible for last 60 days

### Promotion Management API

- PUT `/promotion` - Create, modify, deactivate promotions
- GET `/promotion` - Check promotion job status (QUEUED, COMPLETED, FAILED)
- Promotion types: STRIKETHROUGH, SAME_ITEM_BUNDLE
- Discount subtypes: PERCENTAGE_OFF, ABSOLUTE_VALUE_OFF, FINAL_PRICE, FREE_ITEM
- Vendor-level and SKU-level targeting

### Outlet Management API

- PUT `/status` - Update outlet operational status
- GET `/status` - Retrieve current outlet status
- Status values: OPEN, CLOSED_TODAY, CLOSED_UNTIL, CHECKIN
- Closed reason and closed_until timestamp

### SFTP Integration

- SFTP Central Server with 3 directories (Assortment, Catalog, Promotions)
- File formats: Single Vendor Single File, Single Vendor Double File, Multi-Vendor Double File
- CSV-based file processing
- Scheduled scanning and synchronization

---

## 9. POS MIDDLEWARE INTEGRATION (DELIVERY HERO)

### Architecture

- **Integration Middleware API** - endpoints called by POS plugins (maintained by Delivery Hero)
- **Plugin API** - endpoints implemented by POS partners (maintained by POS partners)
- **Delivery Hero Vendor App** - fallback device for order processing
- **Plugin** - adapter created by POS clients for communication

### Integration Flows

- **Indirect Flow:** Vendor uses Delivery Hero Vendor App to accept/reject; accepted orders forwarded to POS
- **Direct Flow:** Vendor uses only POS system (no vendor app); plugin required; auto-accept possible

### Order Management (POS Middleware)

- Update Order Status endpoint (accept, reject, mark picked up)
- Mark Order as Prepared (ready for pickup)
- Order Dispatch (receive notification of new order)
- Order Status Update (receive notification of canceled order)
- Auto-accept functionality possible (plugin or vendor app)
- Reject reasons list
- Order Report Service (retrieve completed orders)

### Catalog Management (POS Middleware)

- Submit Catalog (create, update, delete menu and menu items)
- Catalog Import Log
- Update Item Availability
- Unavailable Item endpoint
- Status of Catalog Import
- Menu Import Request (receive notification to submit catalog)
- Centralized Kitchen catalog import (shared POS for multiple brands)

### Store Management (POS Middleware)

- Vendor Availability endpoint (open/close status)
- If closed, vendor marked offline on platform

### Order Report Service

- Retrieve completed orders
- Query order details for orders placed less than 24 hours ago
- Not meant for order processing, only reconciliation

### Technical Requirements

- Credentials (username and password)
- Plugin base URL for notifications
- IP address whitelist
- HTTPS with valid SSL certificate
- 1-2 week onboarding if POS provider already integrated

### Post-Production

- 24-hour advance notice for maintenance (email: log_vendor_pos_integrations@deliveryhero.com)
- Contact details for escalation
- Integration may be disabled for technical issues without response
- POS support email: pos-support@deliveryhero.com

---

## 10. MERCHANT ONBOARDING PROCESS

### Registration Steps

1. **Fill registration form** on Vendor Signup Page:
   - Name, email, phone number
   - Business name and address (map pin or manual entry)
   - Type of cuisine
   - Tax ID / BIR (Philippines) / SSM (Malaysia)
   - Bank details for payouts
   - Commission plan selection (commercial package)
   - Electronic contract signing (tick box, receive signed contract via email)

2. **Upload essential documents:**
   - Business registration certificate (SSM / BIR 2303 / Trade License)
   - Identification proof (IC/Passport of signatory)
   - Proof of bank account ownership (bank statement/cheque/passbook)
   - Brand logo (JPEG/PNG)
   - Delivery menu with prices, photos, opening hours
   - SST certification (if applicable, Malaysia)
   - Halal certification (if applicable)
   - Alcohol license (if applicable)

3. **Approval process:**
   - Review by foodpanda team (24-48 hours typical)
   - Notification if anything missing
   - Fast approval (usually within days)

4. **Create online profile:**
   - Add menu items and photos
   - Set opening hours
   - Configure delivery zones and minimum order amounts

5. **Training and onboarding:**
   - Training materials provided
   - Dedicated support team guidance
   - Restaurant Portal University access

6. **Go live:**
   - Restaurant appears on foodpanda app
   - Start receiving orders
   - Download Panda Partner mobile app

### Commercial Plans (Vary by market)

- **Basic** (~30% commission): Standard listing, basic support
- **Premium** (~26-28%): Priority visibility, marketing support
- **Express** (~22-25%): Delivery by foodpanda, lowest commission
- **Exclusive vs. Non-exclusive partnerships** (Philippines: 27% exclusive, 30% non-exclusive + VAT)
- No application fee
- No lock-in period
- Monthly platform fee (e.g., PHP 1,000 in Philippines, includes device + 2GB data + portal access + retraining)

---

## 11. COMMISSION STRUCTURE DETAILS

### Commission Ranges (by market)

- **General range:** 15% -- 35% of order value
- **Singapore:** 15-20% standard, 18-23% premium, 12-15% Foodpanda Prime
- **Malaysia:** 12-20% (Klikit sources) / 25-30% (commission guides) / tiered: Basic 30%, Premium 26-28%, Express 22-25%
- **Philippines:** 27% exclusive, 30% non-exclusive (+VAT)
- **Bangladesh:** ~22% commission + 1.5% online payment fee (example from vendor contract)

### What Commission Covers

- Delivery logistics and rider compensation
- Rider insurance
- Cashless payment processing
- Marketing and app visibility
- Customer support
- Platform maintenance

### Additional Fees

- Online payment processing fee (~1.5%)
- Monthly platform fee (e.g., PHP 1,000)
- Promotional campaign participation costs
- Delivery fees (paid by customer, indirectly affects demand)
- Packaging charges
- Vendor-funded discounts

### Negotiation Factors

- Higher volume restaurants can negotiate 2-5% reductions
- 200+ orders/month puts merchants in negotiation position
- Subscription programs (Foodpanda Premium/Prime) for reduced rates
- Location and market competition
- Cuisine type

### Commission Calculation

- Based on total value of items in customer's cart
- Before delivery fees, platform fees, certain taxes
- Commission deducted from payout; net amount remitted to merchant

---

## 12. MERCHANT FINANCING PROGRAMS

### Funding Societies Partnership (Malaysia & Bangladesh)

- **Pre-approved financing** based on foodpanda sales transaction data
- **Financing amount:** Up to MYR 100,000 (Bumiputera merchants) / up to MYR 200,000 (general)
- **Interest rate:** From 2% annual (promotional) / 0.8% - 1.5% per month
- **Tenure:** Up to 18-24 months
- **Micro Credit Line:** 30-90 day short-term credit for inventory, suppliers, emergency
- **Benefits:** Disbursement within days, competitive rates, minimal documentation
- **Eligibility:** Sole proprietorship/partnership/private limited, minimum 30% local shareholding, minimum 6 months in operation, SSM registration
- **History:** Partnership since May 2021, exceeded RM1 million disbursed, 500+ merchants assisted
- 3-month no-principal-repayment grace period (promotional)

### AEON Bank Partnership (Malaysia)

- **AEON Bank to Business (AB2B) Programme** -- financing for wholesale purchases
- Inventory expansion financing
- Business growth financing
- Targeted campaigns for foodpanda merchants
- Shariah-compliant products (Islamic digital bank)
- Financial literacy programmes
- Co-branded campaigns with Neko + Pau-Pau mascots

### Hong Kong Bank Partnerships

- Collaborations with major banks, payment partners, and card schemes
- Co-created campaigns and attractive offerings
- Drive additional orders for merchants

---

## 13. AI-DRIVEN RECOMMENDATIONS FOR MERCHANTS

### AI Capability (Pilot in Singapore, expanding to all 10 markets in 2026)

- AI-driven recommendations offering tailored insights
- Vendors receive personalized suggestions to strengthen and expand business
- Data analysis of platform-wide ordering patterns

### Specific AI Applications

- **Menu optimization recommendations** -- identify top-selling items, suggest pricing adjustments
- **Demand forecasting** -- ~90% SKU-level accuracy for inventory planning
- **Peak hour identification** -- optimize staffing and preparation
- **Customer preference analysis** -- tailor offerings to local demand
- **Marketing spend optimization** -- channel-level recommendations
- **Operations efficiency** -- reduce stockouts by ~28%, reduce understaffing hours by ~8%

### Results

- Jaggi's café (Singapore): monthly orders grew fivefold after adopting these tools
- Partners raised average order value 18% and revenue per merchant by 27% (FY2025)

---

## 14. RESTAURANT TRANSFORMATION ADVISORY (TAIWAN)

### Program Name

- "Restaurant Transformation Advisory Team" / "餐饮钱力股计划" (Restaurant Money Power Plan)

### Partners

- Commerce Development Research Institute (CDRI / 商研院)
- Asia Marketing Transformation Alliance (AMT / 亞太行銷數位轉型聯盟協會)

### Scale

- First such team in Taiwan
- 100+ consultants with strategy, data, and marketing background
- Analysis of over 1 billion (10亿) orders' worth of data
- Serving 100,000+ local restaurants

### Three Core Tools

1. **Customized Money Power Report (客製化錢力報告):**
   - Integrates platform big data
   - Customized transformation solutions per merchant
   - Insights on popular meal combos, competitor pricing, regional consumer behavior, marketing strategy comparison

2. **Money Power Workshop (錢力股實戰坊):**
   - 4-hour intensive practical course
   - In-person consultant coaching
   - Peer experience exchange
   - Topics: traffic conversion, operational pitfalls, marketing实战
   - Limited名额 (seats)

3. **Money Power Assessment Test (錢力股檢定測驗):**
   - 12 interactive questions
   - Based on Ministry of Economic Affairs' Digital Transformation Assessment Guide
   - 3 minutes to assess merchant's "money power" score
   - Focus: digital transformation awareness, required conditions, practical application

### Coaching Areas

- Consultant-led coaching
- Data analysis guidance
- Tailored action plans for SME digitization
- "看懂数据" (understand data) to "活用数据" (apply data)

---

## 15. LOCAL HEROES CAMPAIGNS AND MERCHANT AWARDS

### Panda Local Heroes (Philippines)

- Recognizes micro, small, and medium enterprises (MSMEs)
- First awarded in September 2022 (80 awardees)
- Categories: home-based online shops, local mom-and-pop stores
- **Perks:**
  - Vendor ambassador pink tag on app
  - Special deals and discounts
  - Exclusive deals
- Selection based on: outstanding performance, entrepreneurial skills, 2nd quarter performance

### Vendor PandAwards (Philippines)

- Multi-category awards for partner vendors
- Categories include:
  - Panda Local Heroes (local vendors who exponentially grew)
  - Other performance-based categories
- Metro Manila, Luzon, Visayas, Mindanao area winners

### Merchant Recognition (Regional, expanding 2026)

- Appreciation events
- Spotlighting standout businesses exemplifying innovation and community spirit
- Part of expanded merchant care programme across all 10 APAC markets

### Panda Preferred Partner Program (India/Philippines legacy)

- Three tiers: Blue (default), Gold (good), Platinum (outstanding)
- Quarterly evaluation based on operational metrics
- Benefits: dedicated account desk, quicker issue resolution, personal calls, certificate of excellence, newsletter feature

### Top Restaurant Programme

- Badge for meeting criteria: low cancellation/delay/offline rates + high ratings
- Priority placement and better visibility on app
- Performance tracking and tips for improvement in Portal

### Vendor Scoring / Panda Score

- Five tiers: Diamond, Gold, Silver, Bronze, Blue
- Commission rebates/reductions for higher tiers
- 6 key metrics for ranking
- Panda Score = average rating x number of reviews (verified customers only)

---

## 16. MERCHANT SUPPORT CHANNELS

### In-App / Portal Support

- **Help Center** in foodpanda app and website
- **Live Chat** on GoDroid device
- **Service Center** in Restaurant Portal for:
  - Billing/invoice/reconciliation queries
  - Merchant information changes
- **Notification panel** for system alerts and messages

### Email Support

- **Partner Service:** partner@foodpanda.ph (PH) / partner@foodpanda.hk (HK) / Partner Service (SG)
- **Key Account Integration:** keyaccountsQC@deliveryhero.com (integration technical support)
- **POS Integration:** pos-support@deliveryhero.com
- **App Support:** appsupport@foodpanda.com
- **Maintenance Notification:** log_vendor_pos_integrations@deliveryhero.com
- **Corporate:** corporate@foodpanda.sg
- **Press:** press@foodpanda.ph

### Account Management

- Dedicated account managers for personalized support
- Strategic partnerships for top chains
- Direct liaison for joint marketing campaigns

### Training and Education

- Restaurant Portal University
- Training materials during onboarding
- Re-training as required
- Step-by-step guides and video tutorials
- Menu Editor Guide documentation

### Support Issues Commonly Reported

- Restaurant going offline without reason
- Slow menu updates
- Operational hours difficulties
- Delayed support responses
- Invoice complexity
- Hidden charges/discrepancies

---

## 17. SETTLEMENT AND PAYOUT FEATURES

### Payout Cycle (Example: Taiwan)

- Monthly settlement with two cut-offs per month:
  - 1st-15th: Payment on 25th of same month
  - 16th-end of month: Payment on 10th of following month
- Bills available for download on statement dates
- Bank processing may cause 1-day delay

### Payout Cycle (Example: Philippines)

- Weekly cut-offs (1-7, 8-15, 16-22, 23-end of month)
- Remittance 3-5 days after each cut-off
- Two emails post-cutoff:
  - Payment Advice Note (remittance notice)
  - PH FICA / Invoice (fee/deduction breakdown)

### Invoice Components

- Gross sales / order value
- Commission deductions (itemized per order)
- Online payment processing fees
- Promotional/discount costs (vendor-funded)
- Pandabox fees
- Packaging/container charges
- Wastage charges (60% of gross food value for wastage orders)
- VAT on service fees
- Net payable amount
- Outstanding amounts from previous periods

### Reconciliation Features

- Download invoices with fee/commission/net payout breakdown
- Payment advice for reconciliation
- Export records for accounting
- 7 business days to raise objections on invoice discrepancies
- Cointab automated reconciliation support (third-party)

### Payment Advice

- Shows exact remittance amount
- Itemizes all deductions
- Provides order-level detail

### Bank Account Management

- Modify merchant/bank account info via Service Center
- Payment verification required
- Multiple bank support (varies by market)

---

## 18. DELIVERY HERO POS MIDDLEWARE API DETAILS

### API Categories

- **Integration Middleware API** (DH-maintained): Order dispatch, order status update, catalog submission validation, store availability management
- **Plugin API** (POS partner-maintained): Webhook for receiving orders, order status updates, catalog import requests

### Access & Configuration

- Credentials: username + password
- Plugin base URL (HTTPS, valid SSL)
- IP address whitelist required
- Test vendor provided for integration testing
- Integration setup via local DH representative

### Order Integration Flows

| Flow         | Vendor App         | POS                                  | Auto-Accept   |
| ------------ | ------------------ | ------------------------------------ | ------------- |
| **Indirect** | Yes (mandatory)    | Optional (accepted orders forwarded) | On vendor app |
| **Direct**   | No (fallback only) | Yes (primary)                        | On plugin     |

### POS Plugin Architecture

- Plugin acts as adapter between Integration Middleware and vendor POS
- Translates DH order format to POS-understandable format
- Receives order dispatch notifications
- Sends order status updates back to DH
- Supports both Platform Delivery and Vendor Delivery flows

### Order Report Service

- Retrieve completed orders from DH platform
- Query by date/time
- Not for real-time processing, only reconciliation
- Covers last 24 hours

### Centralized Kitchen Support

- Submit individual menu imports for vendors sharing same physical location
- Shared POS for multiple brands

### Technical Requirements Checklist

| Requirement                    |  Indirect Flow   | Direct Flow |
| ------------------------------ | :--------------: | :---------: |
| Plugin development             |   Recommended    |  Required   |
| Vendor App device              |     Required     |  Fallback   |
| Order Status Update endpoint   |   Recommended    |  Required   |
| Auto-accept                    |     Optional     | Recommended |
| Cancellation notification      |   Recommended    |  Required   |
| 24h maintenance notice         | Strongly advised | Compulsory  |
| Contact details for escalation |     Required     |  Required   |

### Q-Commerce (Quick Commerce) API Extensions

- **Assortment API** -- manage individual/bulk items (price, status, quantity)
- **Order Transmission API** -- receive and manage incoming orders
- **Pelican picking solution** -- fulfill orders using DH app
- **Logistics Delivery vs. Own Delivery** options

---

## SUMMARY STATISTICS (as of 2025-2026)

| Metric                                  | Value                                       |
| --------------------------------------- | ------------------------------------------- |
| Markets                                 | 10 (SG, HK, MY, PK, TW, PH, BD, LA, KH, MM) |
| App downloads                           | 125M+                                       |
| Cities                                  | 400+                                        |
| Merchant GMV (2025)                     | $5.2B                                       |
| Top-50 partners                         | 38% of orders                               |
| Merchant fee revenue (2025)             | ~$420M                                      |
| Merchant orders/month (SEA)             | 1.2M+                                       |
| Merchant GMV growth                     | +18% YoY                                    |
| Avg. commission range                   | 15% - 35%                                   |
| AI demand forecast accuracy             | ~90% SKU-level                              |
| Invoicing cut-offs                      | Bi-monthly / weekly                         |
| Local Heroes awardees (PH)              | 80+                                         |
| Restaurant Transformation Advisors (TW) | 100+                                        |
| Orders analyzed (TW program)            | 1 billion+                                  |
