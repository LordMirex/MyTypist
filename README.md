# MyTypist — The Document Operating System

<p align="center">
  <strong>High-Precision Editorial Infrastructure for Enterprise Document Operations</strong>
  <br>
  Professional document craftsmanship focused on formatting fidelity, operational precision, and restrained sophistication.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/identity-precision--editorial-black" alt="Identity">
  <img src="https://img.shields.io/badge/standard-linear--grade-blue" alt="Standard">
  <img src="https://img.shields.io/badge/focus-fidelity-emerald" alt="Focus">
  <img src="https://img.shields.io/badge/status-building-yellow" alt="Status">
</p>

---

## The Vision: The Linear of Document Operations

MyTypist is not just another AI generator. It is a professional **Document Operating System** designed for precision-critical teams. We prioritize **Document Craftsmanship** — the ability to preserve layouts, typography, and structure with absolute fidelity — over generic automation.

---

## Core Value Proposition

| Pillar | Focus |
| :--- | :--- |
| **Formatting Fidelity** | Absolute preservation of document layouts, typography, and structure better than any competitor. |
| **Operational Precision** | Interaction design focused on information density, spatial consistency, and interaction smoothness. |
| **Editorial UX** | A professional workspace that feels like high-end publishing software (Adobe, Notion) rather than a SaaS mockup. |
| **Document Realism** | UI patterns that treat documents as tangible, persistent entities within a sophisticated workflow pipeline. |

---

## Platform Features

### Document Processing
- **Precision Template Engine** — Upload DOCX, auto-detect `{{ placeholders }}` with per-instance formatting preservation
- **Batch Generation** — Generate hundreds of documents from multiple templates with error isolation
- **Format Conversion** — DOCX → PDF with on-demand caching and graceful fallback
- **Smart Formatting** — Nigerian-context date/address formatting, ordinal casing, document-type-aware layout
- **Auto-Save Drafts** — 3-second interval auto-save with 7-day retention and pay-later for guests

### Authentication & Security
- **JWT Authentication** — Access + refresh token rotation, 24h/30d expiry
- **Two-Factor Authentication** — TOTP-based with recovery codes
- **Role-Based Access Control** — Guest, User, Moderator, Admin with resource-level permissions
- **Session Management** — Active session listing and remote revocation
- **Rate Limiting** — Tiered per-route protection (100 requests/60s default)
- **CSRF Protection** — Double-submit cookie + origin validation
- **Security Headers** — CSP, HSTS, XSS protection, X-Frame-Options
- **Fraud Detection** — Device fingerprinting, velocity checks, cross-browser detection
- **File Encryption** — Fernet encryption at rest, secure delete
- **Audit Logging** — Comprehensive event tracking with geo-IP, 7-year compliance retention

### Billing & Economy
- **Subscription Plans** — Free (5 docs/mo), Pro (1000 docs/mo), Enterprise (unlimited)
- **Token System** — Pay-per-generation with volume discounts
- **Wallet** — Balance, transaction history, spending limits
- **Flutterwave Payments** — Nigerian-optimized payment processing with webhooks
- **Invoicing** — Auto-generated invoices with PDF download

### Signatures
- **Draw Signature** — Canvas-based capture with pressure support
- **Upload Signature** — PNG with transparent background
- **Type Signature** — Font-based with multiple styles
- **Batch Signing** — Request signatures on multiple documents
- **Signature Library** — Store and reuse signatures

### Sharing & Collaboration
- **Link-Based Sharing** — Configurable permissions (view/download/edit)
- **Expiration Controls** — Time-limited share links
- **Access Tracking** — View counts, per-recipient status

### Content Management
- **Blog CMS** — Full content management with categories, SEO metadata
- **FAQ System** — Organized by category with search
- **Support Tickets** — Threaded conversations with email notifications
- **Feedback System** — Categorized feedback with admin review

### Analytics & Monitoring
- **User Analytics** — Generation statistics, activity timeline
- **Real-Time Monitoring** — Live session tracking, active user counts
- **Admin Dashboard** — System health, revenue metrics, user retention
- **Performance Tracking** — Generation times, time-saved calculations
- **Security Monitoring** — SQLi/XSS detection, incident management

### Marketing & Growth
- **Referral Programs** — Link generation, reward tracking, fraud checks
- **Email Campaigns** — Token gifting, execution logging
- **Partner System** — Tiered partnerships, referral tracking

### SEO & Discovery
- **Meta Tag Generation** — Auto-generated OpenGraph, Twitter Card tags
- **XML Sitemap** — Dynamic sitemap for public content
- **Canonical URLs** — Duplicate content prevention
- **Structured Data** — JSON-LD for templates and documents

---

## Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                        Nginx / Load Balancer                  │
├─────────────────────────────────────────────────────────────┤
│                     FastAPI Application                       │
│  ┌───────────────────────────────────────────────────────┐  │
│  │  Middleware Stack: Security → Auth → Rate Limit →      │  │
│  │  Audit → CSRF → Guest Session → SEO → Token Deduction │  │
│  └───────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────┐  │
│  │  Routes: Auth | Documents | Templates | Signatures     │  │
│  │  | Admin | Payments | Analytics | Blog | Support | ... │  │
│  └───────────────────────────────────────────────────────┘  │
│  ┌───────────────────────────────────────────────────────┐  │
│  │  Services: 55+ modules covering document processing,   │  │
│  │  auth, billing, analytics, search, SEO, fraud, etc.   │  │
│  └───────────────────────────────────────────────────────┘  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────────┐  │
│  │  PostgreSQL   │  │    Redis     │  │    Celery        │  │
│  │   (Primary)   │  │ (Cache/Queue)│  │ (Background Tasks)│ │
│  └──────────────┘  └──────────────┘  └──────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                              │
┌─────────────────────────────────────────────────────────────┐
│                    React + TypeScript Frontend               │
│  ┌──────────┐  ┌──────────────────┐  ┌──────────────────┐  │
│  │ Sidebar  │  │  Main Workspace  │  │  Inspector       │  │
│  │ (256px)  │  │  (1fr)           │  │  Panel (320px)   │  │
│  └──────────┘  └──────────────────┘  └──────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### Tech Stack
- **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Zustand, TanStack Query, Framer Motion
- **Backend:** Python 3.11, FastAPI, SQLAlchemy 2.0, Pydantic v2
- **Database:** PostgreSQL 16 with production connection pooling
- **Cache & Queue:** Redis 7 (L1 memory + L2 Redis)
- **Async Tasks:** Celery with Redis broker
- **Payments:** Flutterwave API
- **Email:** SendGrid (primary) + SMTP (fallback)
- **Containerization:** Docker + Docker Compose

---

## Design System

The MyTypist frontend follows a **Precision Enterprise Editorial** design philosophy:

- **Typography:** Inter (UI) / Geist (code-adjacent), 4px baseline grid
- **Color:** Monochrome-dominant with restrained blue accent, warm off-white surfaces
- **Motion:** Operational transitions (150-250ms), no decorative animation
- **Layout:** Workspace-oriented (Figma/Linear-style) with split-pane, inspector panel, command palette
- **Spacing:** 4px base unit, 32px sidebar items, 24px workspace padding

Detailed specifications:
- **UI System:** `PRODUCT_UI_SYSTEM.md` — Typography, color, motion, workspace architecture
- **Components:** `COMPONENT_SPECIFICATIONS.md` — 26 sections covering all components with state tables, layout diagrams, and backend API mapping
- **Wireframes:** `WIREFRAME_BLUEPRINTS.md` — 14 wireframes for every major screen
- **Routes:** `PAGES_AND_ROUTES_SPEC.md` — Full ~80-route map with priority tiers

> These documents live in the private frontend repository. Contact maintainers for access.

---

## Document Generation Pipeline

```
Upload DOCX Template
       │
       ▼
Extract {{placeholders}} ← Auto-detect fields, types, formatting
       │                     (font, size, bold, italic, alignment)
       ▼
Configure Fields ← Set types, defaults, validation, options
       │
       ▼
Fill Data → Preview → Generate → Output DOCX/PDF
                                  (with caching)
```

---

## Getting Started

1. **Visit the application** at your deployment URL
2. **Sign up** for an account (free tier available)
3. **Upload a template** — any DOCX file with `{{ placeholders }}`
4. **Configure fields** — set types, defaults, and validation
5. **Generate documents** — fill the form and download

---

## Project Structure

This repository is a **public product hub**. Application code lives in private repositories.

| Repository | Purpose | Visibility |
| :--- | :--- | :--- |
| **MyTypist (this repo)** | Product documentation, branding, design system | Public |
| **Frontend** | React/TypeScript editorial workspace | Private |
| **Backend** | FastAPI document processing engine | Private |

---

## Security

- **JWT authentication** with token rotation and refresh (24h access / 30d refresh)
- **Two-factor authentication** (TOTP) with recovery codes
- **Role-based access control** (Guest, User, Moderator, Admin)
- **Rate limiting** per-route (100 requests/60s default, configurable)
- **CSRF protection** — Double-submit cookie + origin header
- **Security headers** — CSP, HSTS, X-Content-Type-Options, X-Frame-Options
- **File encryption** at rest (Fernet), quarantine for suspicious uploads
- **Fraud detection** — Device fingerprinting, velocity checks, cross-browser detection
- **Input validation** via Pydantic v2 schemas
- **File upload validation** — MIME type checking, magic bytes, size limits (100MB max)
- **SQL injection & XSS detection** — Middleware-level threat monitoring
- **Audit logging** — 7-year retention with geo-IP enrichment
- **GDPR compliance** — Data retention controls, consent management
- **Flutterwave** for PCI-compliant payment processing
- **Encryption at rest** — Database-level and file-level encryption

See `SECURITY.md` for vulnerability reporting.

---

## Roadmap

### Phase 1 — Core Platform ✓
- [x] Precision document generation from DOCX templates
- [x] Placeholder detection with formatting preservation
- [x] Batch processing with error isolation
- [x] DOCX ↔ PDF conversion with caching
- [x] Nigerian academic context smart defaults
- [x] User authentication (JWT + 2FA)
- [x] Role-based access control
- [x] Subscription billing (Flutterwave)

### Phase 2 — Operational Features
- [x] Token economy and wallet system
- [x] Signature capture (draw/upload/type)
- [x] Document sharing with permissions
- [x] Blog CMS, FAQ, support tickets
- [x] Real-time analytics and monitoring
- [x] Admin dashboard and user management
- [x] SEO automation (meta tags, sitemap, structured data)

### Phase 3 — Advanced Capabilities
- [ ] Advanced template intelligence for complex documents
- [ ] Role-based workflow approvals and audit controls
- [ ] CRM and cloud storage integrations
- [ ] Multi-region deployment for global performance
- [ ] AI-powered template suggestions
- [ ] Real-time collaborative editing

---

## Screenshots

![Dashboard Overview](assets/screenshots/dashboard-placeholder.svg)
![Document Editor](assets/screenshots/editor-placeholder.svg)
![Automation Flow](assets/screenshots/automation-placeholder.svg)

---

## Links

- **Website:** https://mytypist.com (domain owned, deployment pending)
- **Current Live Site:** https://zenvault.one
- **Frontend:** Private repository
- **Backend:** Private repository
- **Design Docs:** Private repository (contact maintainers)

---

## License

Proprietary. All rights reserved.

---

*MyTypist is built for teams that want faster document workflows without sacrificing accuracy or compliance.*
