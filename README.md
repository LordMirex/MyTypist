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
</p>

---

## The Vision: The Linear of Document Operations

MyTypist is not just another AI generator. It is a professional **Document Operating System** designed for precision-critical teams. We prioritize **Document Craftsmanship**—the ability to preserve layouts, typography, and structure with absolute fidelity—over generic automation.

---

## Core Value Proposition

| Pillar | Focus |
| :--- | :--- |
| **Formatting Fidelity** | Absolute preservation of document layouts, typography, and structure better than any competitor. |
| **Operational Precision** | Interaction design focused on information density, spatial consistency, and interaction smoothness. |
| **Editorial UX** | A professional workspace that feels like high-end publishing software (Adobe, Notion) rather than a SaaS mockup. |
| **Document Realism** | UI patterns that treat documents as tangible, persistent entities within a sophisticated workflow pipeline. |

---

## Signature Features

| Feature | The MyTypist Advantage |
| :--- | :--- |
| **Precision Placeholder Styling** | Style every individual instance of a placeholder separately — bold, italic, underline per occurrence. |
| **Structure Preservation** | Auto-detects and maintains complex DOCX structure, ensuring no formatting is lost during generation. |
| **High-Density Workspace** | A spatial, persistent operational environment designed for high-throughput document operations. |
| **Fidelity Engine** | Pure-precision processing that outputs DOCX and PDF with 100% visual parity to the original template. |
| **Audit-Ready Operations** | Detailed tracking of every document change, signature, and approval within a professional audit trail. |

---

## Interaction Design Standards

- **Stateful Interfaces:** Contextual toolbars and progressive disclosure for complex tasks.
- **Interaction Smoothness:** Precision in hover logic, animation timing, and loading transitions (Linear-inspired).
- **Workspace Logic:** A persistent, spatial application structure instead of standard page-based CRUD forms.
- **Keyboard-First UX:** Designed for operational speed and efficiency.

---

## Use Cases

- **Legal & HR Operations** — Precision-critical contracts and compliance documents.
- **Enterprise Workflows** — High-volume recurring reports with strict branding requirements.
- **Precision Publishing** — Standardized professional stationery and document systems.
- **Operational Infrastructure** — Automating repetitive document tasks with bank-level reliability.

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
