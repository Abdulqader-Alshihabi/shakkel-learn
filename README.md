# Shakkel Learning Hub - Enterprise Workforce Training & LMS Platform

[![Production Status](https://img.shields.io/badge/Status-Production%20Live-brightgreen?style=for-the-badge)](https://learn.shakkel.store/)
[![Client](https://img.shields.io/badge/Client-Shakkel%20(شَكَّل)-0052CC?style=for-the-badge)](https://shakkel.store/)
[![Live Platform](https://img.shields.io/badge/Domain-learn.shakkel.store-green?style=for-the-badge)](https://learn.shakkel.store/)
[![Frontend](https://img.shields.io/badge/Frontend-React%2019%20%7C%20TypeScript-61DAFB?style=for-the-badge)](https://learn.shakkel.store/)
[![Backend](https://img.shields.io/badge/Backend-Supabase%20%7C%20PostgreSQL-3ECF8E?style=for-the-badge)](https://learn.shakkel.store/)
[![Styling](https://img.shields.io/badge/Styling-Tailwind%20CSS%20v4-38B2AC?style=for-the-badge)](https://learn.shakkel.store/)

Production URL: [https://learn.shakkel.store/](https://learn.shakkel.store/)  
Client: Shakkel Industrial & Commercial Solutions (شَكَّل)  
Category: Enterprise Corporate Learning Management System (LMS) & Workforce Upskilling Platform  
Lead Architect & Developer: Abdulqader Alshihabi  

---

## Commercial Notice & IP Confidentiality

> [!IMPORTANT]
> Commercial In-Production Platform Notice:  
> This repository serves as an Architectural Case Study and Technical Specification for the Shakkel Corporate Learning Hub. Because this platform powers commercial enterprise operations and corporate workforce training under non-disclosure and commercial agreements, backend database seeds, sensitive environment variables, and proprietary client source code are maintained in Shakkel's private production infrastructure.

---

## Executive Summary

Shakkel Learning Hub (`learn.shakkel.store`) is a high-performance, enterprise-grade Learning Management System (LMS) engineered to support corporate workforce onboarding, professional industrial certifications, and internal employee skills development. 

Built with React 19, TypeScript, TanStack Router, Tailwind CSS v4, and Supabase / PostgreSQL, the platform delivers zero-latency client-side navigation, robust server-enforced security models, and end-to-end educational administration.

### Core Business Capabilities
- **Enterprise Multi-Tenancy & RBAC**: Strict separation of concerns between Super Administrators, Platform Administrators, Content Editors, Instructors, Corporate Partners, and Enrolled Learners.
- **Rich-Text Curriculum Authoring**: In-browser WYSIWYG course builder powered by Tiptap with support for interactive media, structured chapters, and prerequisite gating.
- **Exam Integrity & Assessment Engine**: Automated evaluation system with randomized question banks, timed completion windows, attempt restrictions, and anti-cheating mechanisms.
- **Corporate Analytics & XLSX Exports**: Real-time workforce progress dashboards, department attendance sheets, and on-demand Excel workbook generation for corporate HR departments.
- **Digital Credentialing & PDF Verification**: Automated generation of tamper-evident completion certificates with unique verification identifiers.
- **Bilingual Interface**: Native Arabic (RTL) and English (LTR) user experience powered by `i18next`.

---

## System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│               Client-Side Web Application (React 19 + Vite)            │
│  - Routing & Navigation: TanStack Router (File-based, Type-safe)       │
│  - Data Fetching & Caching: TanStack React Query v5                    │
│  - UI Tokens & Components: Radix UI Primitives + Tailwind CSS v4       │
│  - Rich Text Engine: Tiptap Core (ProseMirror Headless)                │
│  - Bilingual Localization: i18next (Arabic RTL / English LTR)          │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│                   Secure Edge & Authorization Layer                    │
│  - Route Guards: Authenticated Sessions, Role Verification             │
│  - Token Management: Supabase GoTrue JWT & Secure Cookies              │
│  - Edge Functions: Administrative Privileges & User Governance         │
└──────────────────────────────────┬─────────────────────────────────────┘
                                   │
                                   ▼
┌────────────────────────────────────────────────────────────────────────┐
│               PostgreSQL Database & Relational Storage                 │
│  - Row-Level Security (RLS): Granular per-role access policies         │
│  - Security Definer RPCs: Atomic multi-step business transactions      │
│  - Media Storage: Supabase Storage Buckets for course assets & PDFs    │
│  - Audit Logs: Immutable tracking for student exams & certifications   │
└────────────────────────────────────────────────────────────────────────┘
```

---

## Technical Highlights & Implementation Details

### 1. Robust Server-Enforced Security Matrix (PostgreSQL RLS)
Platform security does not rely solely on front-end route guards. Every database operation is validated at the database layer via PostgreSQL Row Level Security (RLS):
- `anon`: Can query published course overviews and public metadata without access to protected lessons or corporate materials.
- `student`: Can view only enrolled curriculum lessons, submit assessment answers, and access earned credentials.
- `instructor`: Can create, edit, and organize modules for assigned courses, inspect enrolled trainees, and log session attendance.
- `editor` / `admin`: Full content administration across the platform catalog.
- `super_admin`: System settings, financial ledger auditing, and role provisioning via security-definer procedures.

### 2. High-Performance Front-End Stack
- **React 19 & TanStack Router**: Type-safe search parameters, route loading boundaries, and nested layouts for administrative and student dashboards.
- **Tailwind CSS v4 Engine**: Modern styling engine delivering micro-optimized CSS bundles, dark mode, and smooth transitions.
- **TanStack React Query v5**: Stale-while-revalidate caching, optimistic updates for quiz progression, and automated invalidation upon curriculum revisions.

### 3. Examination Integrity & Verification Engine
- Configurable examination parameters: maximum attempts, countdown timers, passing thresholds, and immediate feedback toggles.
- Anti-tampering checks ensuring submission timestamps match backend transaction records.
- PDF certificate issuance leveraging `pdfjs-dist` for dynamic client-side rendering and cryptographic verification QR codes.

### 4. Corporate Reporting & Export Capabilities
- Built-in report generator delivering multi-sheet Microsoft Excel (`.xlsx`) workbooks containing employee training hours, assessment scores, and certification statuses.
- Interactive Recharts visualization panels for administrators to track monthly active learners, course completion rates, and department performance.

---

## Technology Stack

| Layer | Technologies and Libraries |
| :--- | :--- |
| **Frontend Framework** | React 19, TypeScript, Vite 6 |
| **Routing & Navigation** | TanStack Router (`@tanstack/react-router`) |
| **Server State & Cache** | TanStack React Query v5 |
| **Styling & UI Tokens** | Tailwind CSS v4, Radix UI Primitives, Lucide Icons |
| **Content Authoring** | Tiptap (ProseMirror Headless Editor) |
| **Data Visualization** | Recharts (Responsive Line, Bar, and Area Charts) |
| **Document Processing** | PDF.js (`pdfjs-dist`), FFlate, XLSX Generators |
| **Localization** | i18next (Arabic RTL and English LTR) |
| **Backend & Database** | Supabase (PostgreSQL 15), Row Level Security (RLS), Edge Functions |
| **Authentication** | Supabase Auth (JWT, Role Claims, Session Recovery) |

---

## Production Deployment

The platform is deployed and operational at:
- **Production Host**: [https://learn.shakkel.store/](https://learn.shakkel.store/)
- **Parent Enterprise Domain**: [https://shakkel.store/](https://shakkel.store/)

---

## Engineering Credits

**Abdulqader Alshihabi**  
Computer Science Graduate | Software & AI Engineer  
- Portfolio: [https://abdulqader-alshihabi.github.io/](https://abdulqader-alshihabi.github.io/)  
- GitHub: [@Abdulqader-Alshihabi](https://github.com/Abdulqader-Alshihabi)  
- Email: [abdulqader.moh.2003@gmail.com](mailto:abdulqader.moh.2003@gmail.com)  
