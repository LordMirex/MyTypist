# MyTypist

<p align="center">
  <strong>Automated Document Generation for Teams</strong>
  <br>
  Create professional documents from templates in minutes — not hours.
</p>

<p align="center">
  <img src="https://img.shields.io/badge/status-active-brightgreen" alt="Status">
  <img src="https://img.shields.io/badge/license-proprietary-blue" alt="License">
  <img src="https://img.shields.io/badge/platform-web-8A2BE2" alt="Platform">
</p>

---

## Problem Statement

Document-heavy teams waste time on repetitive typing, inconsistent formatting, and error-prone manual updates across templates, reports, and client deliverables.

## Solution Overview

MyTypist centralizes document workflows and automates the repetitive steps so users can generate accurate, brand-consistent documents in minutes instead of hours.

---

## Features

| Feature | Description |
| :--- | :--- |
| **Template-Based Generation** | Upload DOCX templates with `{{ placeholder }}` syntax and generate filled documents instantly |
| **Smart Placeholder Detection** | Auto-extracts fields from templates with intelligent type inference |
| **Batch Processing** | Generate multiple documents simultaneously from a single data entry form |
| **Multiple Output Formats** | Download as DOCX or PDF with perfect formatting preservation |
| **Individual Placeholder Styling** | Style each `{{ name }}` instance separately — bold, italic, underline per occurrence |
| **100+ Font Families** | Google Fonts, Microsoft Office fonts, and professional typography |
| **E-Signatures** | Draw, type, or upload signatures and embed them into documents |
| **Token-Based Billing** | Pay-per-document or subscribe with Flutterwave payment integration |
| **Admin Dashboard** | Manage templates, monitor usage, and control the platform |
| **Audit Logging** | Track every document generation and user action |

---

## Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│   Frontend   │────▶│    API       │────▶│  Document    │
│   React/Vite │     │  FastAPI     │     │  Engine      │
└──────────────┘     └──────┬───────┘     └──────┬───────┘
                            │                     │
                            ▼                     ▼
                     ┌──────────────┐     ┌──────────────┐
                     │  PostgreSQL  │     │   Storage    │
                     │  Database    │     │   (DOCX/PDF) │
                     └──────────────┘     └──────────────┘
                            │
                            ▼
                     ┌──────────────┐
                     │    Redis     │
                     │  Cache/Queue │
                     └──────────────┘
```

- **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Redux Toolkit
- **Backend:** Python, FastAPI, SQLAlchemy, Celery
- **Database:** PostgreSQL 16 with Alembic migrations
- **Cache:** Redis 6+ for caching, sessions, and task queues
- **Payments:** Flutterwave integration for Nigerian payment methods

---

## Use Cases

- **Operations Teams** — Recurring reports and client deliverables
- **Legal & Compliance** — Standardized contracts and policy documents
- **HR & Finance** — Onboarding packets and offer letters
- **Agencies** — Proposals, statements of work, and invoices

---

## Document Generation Pipeline

```
Upload DOCX Template
       │
       ▼
Extract {{placeholders}} ← Auto-detect fields, types, formatting
       │
       ▼
Generate Dynamic Form ← One field per placeholder
       │
       ▼
Fill Data → Process → Output DOCX/PDF
```

---

## Screenshots

![Dashboard Overview](assets/screenshots/dashboard-placeholder.svg)
![Document Editor](assets/screenshots/editor-placeholder.svg)
![Automation Flow](assets/screenshots/automation-placeholder.svg)

---

## Getting Started

1. **Visit the application** at your deployment URL
2. **Sign up** for an account (token-based or subscription)
3. **Upload a template** — any DOCX file with `{{ placeholders }}`
4. **Configure fields** — set types, defaults, and validation
5. **Generate documents** — fill the form and download

---

## Project Structure

This public repository is a product hub only. Application code lives in private repositories.

| Repository | Purpose |
| :--- | :--- |
| **Public (this repo)** | Product documentation and branding assets |
| **Frontend (private)** | User interface and client experience |
| **Backend (private)** | APIs, workflows, and business logic |

---

## Security

- **JWT-based authentication** with token rotation and refresh
- **Role-based access control** (Guest, User, Moderator, Admin)
- **Input validation** via Pydantic schemas
- **File upload validation** — MIME type checking, size limits
- **HTTPS** in production with SSL termination
- **Audit logging** for all user actions and system events
- **Flutterwave** for PCI-compliant payment processing

---

## Roadmap

- [ ] Advanced template intelligence for complex documents
- [ ] Role-based workflow approvals and audit controls
- [ ] CRM and cloud storage integrations
- [ ] Multi-region deployment for global performance
- [ ] Real-time collaborative editing
- [ ] AI-powered template suggestions

---

## Links

- **Application:** https://mytypist.com (coming soon)
- **Frontend repo:** Private
- **Backend repo:** Private

---

*MyTypist is built for teams that want faster document workflows without sacrificing accuracy or compliance.*
