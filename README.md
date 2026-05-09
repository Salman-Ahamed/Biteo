# 🍔 Biteo — AI-Powered Multi-Tenant Restaurant SaaS Platform
### Feature List & Requirement Understanding Document
> Prepared based on client-provided requirement document.

---

## 📌 Table of Contents

1. [Project Overview](#1-project-overview)
2. [WhatsApp Ordering System](#2-whatsapp-ordering-system-primary-channel)
3. [Restaurant Admin Panel](#3-restaurant-admin-panel)
4. [Super Admin Panel](#4-super-admin-panel-saas-owner)
5. [AI Marketing Automation](#5-ai-marketing-automation)
6. [AI Voice Ordering](#6-ai-voice-ordering)
7. [Delivery & Logistics](#7-delivery--logistics)
8. [Security & Role Management](#8-security--role-management)
9. [Integrations](#9-integrations)
10. [Technical Architecture](#10-technical-architecture)
11. [Infrastructure & DevOps](#11-infrastructure--devops)
12. [Deliverables](#12-deliverables)
13. [Timeline](#13-timeline)
14. [Bonus Capabilities](#14-bonus-capabilities-preferred)

---

## 1. Project Overview

**Biteo** is a full-stack, AI-powered, multi-tenant SaaS platform built for restaurants. It combines:

| Component | Description |
|---|---|
| 🛒 Marketplace | Like Uber Eats — customers browse, order, and pay |
| 💬 WhatsApp Ordering | Primary order channel via WhatsApp chatbot |
| 🎙️ AI Voice Ordering | Phone-based automated ordering using AI voice |
| 🏢 Multi-Tenant SaaS | Multiple restaurants, each with isolated data & dashboard |
| 🚚 Delivery Automation | Automated delivery assignment and tracking |
| 📣 AI Marketing | AI-generated content, posters, reels, campaigns |

**Target use cases:** Dine-in restaurants, Takeaway, Dark kitchens (cloud kitchens)

---

## 2. WhatsApp Ordering System (Primary Channel)

### 2.1 Overview
The entire ordering journey happens inside WhatsApp — no app download required for customers.

### 2.2 Integration
- **WhatsApp Cloud API** (Meta official API)
- Support for **button messages** and **list messages** (interactive UI inside WhatsApp)

### 2.3 Customer Ordering Flow

```
Step 1 → Customer sends "Hi" to restaurant's WhatsApp number
Step 2 → Bot automatically replies with Menu (categories + items)
Step 3 → Customer selects items using buttons/list
Step 4 → Bot shows Order Summary with price
Step 5 → Customer proceeds to Checkout
Step 6 → Payment link or COD confirmation
Step 7 → Order Confirmed message sent to customer
Step 8 → Order appears on Restaurant Dashboard
Step 9 → Kitchen Printer auto-prints the order (KOT)
Step 10 → Real-time order tracking updates sent to customer
```

### 2.4 Bot Features

| Feature | Description |
|---|---|
| Menu Browsing | Category-wise menu display with images and prices |
| Item Selection | Add/remove items using interactive buttons |
| Cart Management | Review cart, modify quantities before checkout |
| Checkout | Address collection, delivery type (dine-in/takeaway/delivery) |
| Payment | Payment gateway link sent via WhatsApp |
| Smart Upselling | AI suggests add-ons (e.g., "Add fries for ৳50?") |
| Order Tracking | Live status updates — Accepted → Preparing → Out for Delivery → Delivered |
| Order History | Returning customers can reorder previous orders |
| Language Support | Multi-language support based on restaurant setting |

### 2.5 Kitchen Integration
- Automatic **KOT (Kitchen Order Ticket)** print on order confirmation
- Support for **thermal printers** (Bluetooth / LAN / USB)
- Bill/receipt print option at checkout

---

## 3. Restaurant Admin Panel

Each restaurant gets its **own isolated dashboard** after subscription.

### 3.1 Menu Management
- Add / Edit / Delete food categories
- Add / Edit / Delete food items (name, description, price, image, availability toggle)
- Mark items as **Available / Unavailable** in real-time
- Set item variants (size, spice level, add-ons)
- Bulk import/export menu via CSV or Excel
- Set special pricing for dine-in vs takeaway vs delivery

### 3.2 Order Management
- Live order feed (real-time updates)
- Order status management: **New → Accepted → Preparing → Ready → Delivered**
- Filter orders by: date, status, order type, payment method
- View full order details (items, customer info, address, payment)
- Manually assign delivery agent
- Cancel/refund order with reason

### 3.3 Report & Analytics
- **Daily / Weekly / Monthly** sales report
- Revenue breakdown by category, item, and time
- Top-selling items report
- Customer order frequency report
- Export reports as PDF or Excel
- WhatsApp campaign performance report

### 3.4 Restaurant Settings
- Restaurant name, logo, address, contact
- Operating hours (open/close schedule per day)
- Delivery zones and delivery charges
- Minimum order amount
- Tax & VAT configuration

### 3.5 WhatsApp Configuration
- Connect/disconnect WhatsApp Business number
- Configure WhatsApp Cloud API credentials (Phone Number ID, Access Token)
- Set up automated replies and greeting message
- Test bot flow from dashboard

### 3.6 Printer Integration
- Add and configure printers (IP-based or USB)
- Assign printers to Kitchen or Billing
- Auto-print settings (trigger on order accept or on new order)
- Manual reprint option

### 3.7 Staff Management
- Add/remove staff accounts (cashier, manager roles)
- Assign permissions per staff
- Activity log per staff member

---

## 4. Super Admin Panel (SaaS Owner)

This is the **platform owner's dashboard** to manage all restaurants and platform operations.

### 4.1 Restaurant Management
- View all registered restaurants
- Approve / Suspend / Delete restaurant accounts
- View each restaurant's activity, order volume, and revenue
- Impersonate (login as) any restaurant for support

### 4.2 Subscription & Billing Management
- Create and manage **subscription plans** (Basic, Pro, Enterprise)
- Assign plans to restaurants
- View payment history and invoices per restaurant
- Manual plan upgrade/downgrade
- Set feature limits per plan (e.g., max menu items, max WhatsApp messages/month)

### 4.3 Platform Analytics
- Total active restaurants
- Total orders across all restaurants
- Platform revenue (subscription + commission if applicable)
- API usage stats (WhatsApp messages, AI calls)
- Growth charts: new signups, churn rate

### 4.4 WhatsApp & API Management
- Monitor WhatsApp API usage per restaurant
- Alert when restaurants exceed message quota
- Global API configuration management

### 4.5 Content & Notification
- Send platform-wide announcements to all restaurants
- Email/WhatsApp notifications to restaurant admins
- Manage system-level notification templates

### 4.6 Configuration
- Global tax settings
- Payment gateway configuration
- Default bot message templates
- Feature flag management (enable/disable features platform-wide)

---

## 5. AI Marketing Automation

This is a **core differentiator** of the platform.

### 5.1 AI Content Generation

| Feature | How it works |
|---|---|
| 🖼️ AI Poster Maker | Upload raw dish photo + dish name → AI generates professional branded poster |
| 📱 Social Media Content | AI writes captions, hashtags, and post text per platform |
| 🎬 Reel Generation | AI creates short video/reel from dish images and branding |
| ✏️ Edit & Export | Edit the AI output before publishing |

**Poster generation flow:**
```
Step 1 → Restaurant uploads raw photo of dish
Step 2 → Enters dish name and optional promo text
Step 3 → AI generates branded poster with restaurant logo, colors, fonts
Step 4 → Admin can edit or regenerate
Step 5 → Directly publish to social media OR download
```

### 5.2 Social Media Integration & Ad Management

Supported platforms:
- Facebook & Instagram
- Google Ads
- Twitter / X
- TikTok
- YouTube

Features:
- **Storewise Integration:** Each restaurant connects its **own** social media accounts separately (e.g., Restaurant A has its own FB page, Restaurant B has its own)
- **Application-level Integration:** Option for platform-wide social media integration (managed by Super Admin)
- Schedule and publish posts directly from restaurant dashboard
- Run ad campaigns from dashboard
- Set ad budget and target audience per restaurant

### 5.3 Ad & Funnel Tracking

```
Funnel: Ad Impression → Click → WhatsApp/Website Visit → Order Placed
```

- Track ad performance per platform
- Conversion rate per campaign
- Cost per order (CPO) calculation
- ROI report per campaign

### 5.4 Retargeting Automation

| Audience | Action |
|---|---|
| Abandoned users (visited but didn't order) | Send re-engagement WhatsApp message |
| Repeat customers | Send loyalty offers or discount coupons |
| High-value customers | Send VIP offers |
| Inactive customers (30+ days) | Send win-back campaign |

### 5.5 Campaign Automation

- Schedule campaigns to run automatically on specific dates/events (e.g., Eid, weekends)
- Trigger-based campaigns: auto-send offer when customer hasn't ordered in X days
- Multi-step campaign flows: Message 1 → Wait 2 days → Message 2 (if no response)
- Campaign performance dashboard: sent, delivered, read, clicked, converted
- A/B testing: test two message variants to see which performs better
- Campaign template library (pre-built templates for common use cases)

### 5.6 Bulk WhatsApp Messaging (Campaign)

- Upload customer list or use existing customer database
- Create message template with personalization (name, last order, discount)
- Schedule campaign send time
- Track delivery rate, read rate, and click rate
- Comply with WhatsApp Business messaging policies

### 5.6 Coupon & Discount System

- Create coupon codes with:
  - Fixed or percentage discount
  - Minimum order requirement
  - Expiry date
  - Single-use or multi-use
  - Per-customer usage limit
- Attach coupons to WhatsApp campaigns
- Auto-apply eligible coupons during WhatsApp checkout
- Track coupon usage and impact on revenue

---

## 6. AI Voice Ordering

### 6.1 Overview
Customers can call a phone number and place orders by **speaking** — no human operator needed.

### 6.2 Flow
```
Step 1 → Customer calls restaurant's ordering number
Step 2 → AI voice greets customer
Step 3 → AI reads out menu or customer can ask for specific items
Step 4 → Customer speaks their order
Step 5 → AI confirms the order via speech
Step 6 → Order placed in system automatically
Step 7 → SMS/WhatsApp confirmation sent to customer
```

### 6.3 Technology
- **Speech-to-Text (STT):** Converts customer voice to text
- **LLM Processing:** Understands order intent, handles clarifications
- **Text-to-Speech (TTS):** AI responds in natural voice
- Integration via **Twilio** or equivalent voice API

---

## 7. Delivery & Logistics

- Delivery zone management per restaurant
- Delivery charge calculation based on distance or zone
- Assign delivery agent manually or auto-assign
- Delivery agent mobile-friendly view for order details
- Real-time delivery tracking (customer-facing)
- Estimated delivery time (ETA) calculation
- Delivery status: Assigned → Picked Up → On the Way → Delivered

---

## 8. Security & Role Management

### 8.1 Roles & Permissions

| Role | Access Level |
|---|---|
| Super Admin | Full platform access |
| Restaurant Admin | Own restaurant data only |
| Restaurant Manager | Orders, reports, menu (no billing) |
| Cashier / Staff | Orders and POS only |
| Delivery Agent | Own assigned deliveries only |

### 8.2 Authentication
- **JWT (JSON Web Token)** based authentication
- Token refresh mechanism
- Session management and forced logout

### 8.3 Data Isolation (Multi-Tenancy)
- Each restaurant's data is **completely isolated**
- No cross-tenant data leakage
- Database-level separation per tenant (schema-based or row-based)

### 8.4 Subscription-Based Feature Access
- Features unlocked based on subscription plan
- Automatic feature restriction on plan downgrade or expiry

---

## 9. Integrations

| Integration | Purpose |
|---|---|
| **WhatsApp Cloud API (Meta)** | Primary ordering channel, campaigns, notifications |
| **Twilio** | AI Voice ordering, SMS notifications |
| **Stripe / SSLCommerz / bKash** | Payment gateway (online payments) |
| **Facebook & Instagram Graph API** | Social media posting and ad management |
| **Google Ads API** | Ad campaigns and tracking |
| **TikTok & YouTube API** | Social media and ad integration |
| **OpenAI API** | AI chatbot, content generation, voice processing |
| **Thermal Printer SDK** | Kitchen and bill printing |

---

## 10. Technical Architecture

### 10.1 Backend
- **Language:** Python
- **Framework:** FastAPI (preferred for performance) or Django
- **API Style:** REST API (GraphQL as optional layer)
- **Architecture:** Microservices + Multi-tenant

### 10.2 Microservices Breakdown

| Service | Responsibility |
|---|---|
| Auth Service | Login, JWT, role management |
| Restaurant Service | Restaurant CRUD, settings |
| Menu Service | Menu and item management |
| Order Service | Order lifecycle management |
| WhatsApp Service | Bot logic, message handling |
| AI Service | LLM, content generation, voice |
| Marketing Service | Campaigns, coupons, retargeting |
| Notification Service | Email, SMS, WhatsApp alerts |
| Analytics Service | Reports, tracking, funnel |
| Billing Service | Subscriptions, invoices |

### 10.3 Database (Recommended)

| Database | Use Case |
|---|---|
| **PostgreSQL** | Core data: users, restaurants, orders, menus |
| **Redis** | Caching, real-time queue, session management |
| **MongoDB** | Unstructured data: AI content, logs, chat history |

### 10.4 Frontend
- **React / Next.js** (App Router)
- **Tailwind CSS** for styling
- **shadcn/ui** for component library
- **TypeScript** for type safety

---

## 11. Infrastructure & DevOps

| Component | Technology |
|---|---|
| Cloud Provider | AWS / GCP / Azure |
| Containerization | Docker |
| Orchestration | Kubernetes (K8s) |
| CI/CD | GitHub Actions or GitLab CI |
| Media Storage | AWS S3 or Cloudflare R2 |
| CDN | Cloudflare |
| Monitoring | Grafana + Prometheus |
| Logging | ELK Stack (Elasticsearch, Logstash, Kibana) |

---

## 12. Deliverables

- [ ] Fully functional **Backend API** (all modules)
- [ ] **WhatsApp Bot** automation system
- [ ] **Restaurant Admin Panel** (web)
- [ ] **Super Admin Panel** (web)
- [ ] **AI Marketing Module**
- [ ] **AI Voice Ordering** integration
- [ ] **API Documentation** (Swagger / Postman collection)
- [ ] **Setup & Deployment Guide**
- [ ] **Docker + Kubernetes** deployment config
- [ ] Mobile app (optional — future phase)

---

## 13. Timeline

| Phase | Modules | Duration |
|---|---|---|
| **Module 1** | Core backend, Multi-tenant setup, Auth, Restaurant & Menu APIs, WhatsApp ordering bot, Order management, Kitchen printer integration | 4–6 Weeks |
| **Phase 2** | AI Marketing tools, Content generation, Campaign system, Ad tracking, Coupon system, Bulk WhatsApp messaging | 2 Weeks |
| **Phase 3 (Optional)** | AI Voice ordering, Delivery logistics, Mobile app, Advanced analytics | TBD |

---

## 14. Bonus Capabilities (Preferred)

The development team working on Biteo should ideally have experience in the following areas to ensure smooth delivery:

### 14.1 WhatsApp Bot Development
- Hands-on experience building WhatsApp Cloud API bots
- Knowledge of interactive message types: buttons, lists, templates
- Experience handling webhook events, message queues, and delivery receipts
- Understanding of Meta's messaging policy and template approval process

### 14.2 SaaS Platform Development
- Prior experience building multi-tenant SaaS products
- Understanding of tenant isolation strategies (schema-based vs row-based)
- Experience with subscription billing systems (Stripe or similar)
- Knowledge of onboarding flows for B2B SaaS platforms

### 14.3 Scaling & Infrastructure
- Practical experience with Docker and Kubernetes in production
- AWS / GCP / Azure deployment and management
- Knowledge of load balancing, auto-scaling, and zero-downtime deployments
- CI/CD pipeline setup (GitHub Actions, GitLab CI)
- Experience with monitoring and alerting systems (Grafana, Prometheus)

---

## ✅ Summary

Biteo is not just a food ordering app — it is a **complete restaurant operating system** that:

- Lets customers order via **WhatsApp or Phone** without any app
- Gives restaurants a **powerful dashboard** to manage everything
- Uses **AI to generate marketing content** and run campaigns automatically
- Allows the **SaaS owner to manage** all restaurants and subscriptions centrally
- Is built to **scale** with Docker, Kubernetes, and cloud infrastructure

---

*Document prepared for client review and meeting discussion.*
