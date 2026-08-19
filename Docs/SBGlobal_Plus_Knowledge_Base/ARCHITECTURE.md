# SBGlobal Plus — Enterprise Architecture (ARCHITECTURE.md)

**(Foundation Document 05 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Parts 6–7; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §4, §7
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** ARCHITECTURE.md is the single owning document for *how* SBGlobal Plus is structurally built to deliver the vision defined in `VISION.md`. It expands MI.md Parts 6–7 into the public Knowledge Base. Depth on any one architectural concern (data, AI, integration, deployment, multi-tenancy, security) is owned by that concern's dedicated Foundation document; this document owns the layering and cross-cutting shape that ties them together and is cross-referenced by all of them rather than restated in them (MI Part 8, P3).

---

## 1. Purpose of This Document

ARCHITECTURE.md defines the permanent structural shape of the platform: its layering (§2), its cross-cutting architectural principles (§3–§6), its product surfaces and administrative domains (§7–§8), its Industry Suite / Management System framework (§9), and its deployment and cross-platform posture (§10–§11). Every Core Platform capability and every Industry Suite must be describable in these terms.

---

## 2. Core Architecture Layering

The permanent layering, from which no Foundation document or Industry Suite may deviate, is:

```
One Shared Enterprise Core Platform (industry-neutral)
        ↓
Multiple Equal Industry Suites
        ↓
Industry-Specific Enterprise Management Systems
        ↓
Modules / Workflows / Data / AI / Automation / Integrations
        ↓
Tenant-Specific Configuration
```

- **Core Platform** — industry-neutral, shared by all tenants and all industries. Owns every capability that is reusable across industries: Identity & Access, Workflow Engine, Notifications, Document Management, Reporting, AI Services, Audit, Configuration, Metadata, APIs, Integration, Automation, Analytics, Billing, and equivalent shared services (MI 6.1).
- **Industry Suites** — industry-specific business capability, equal peers to one another (see §9). Consume Core Platform capability via configuration, metadata, APIs, events, plugins, or workflows — **never** by re-implementing it.
- **Management Systems** — major operational business domains within an Industry Suite (see §9.2).
- **Modules / Workflows / Data / AI / Automation / Integrations** — the working parts of a Management System.
- **Tenant-Specific Configuration** — the layer every tenant actually touches; changes here never require a source-code change (`CONFIGURATION-METADATA.md`).

No separate platform architecture may be created per industry or per tenant. A capability implemented once in an Industry Suite and later found useful elsewhere is a signal to generalize it into the Core Platform (MI Part 8, P1), not to copy it.

---

## 3. API-First Architecture

Business logic is never trapped inside a frontend. Every domain capability reaches every consumer through the same governed path:

```
Domain Capability → Business Service → API / Event →
Web / Mobile / Desktop / Industry Systems / Integrations / AI
```

Governance for this principle covers: API-first business-capability and domain exposure, versioning, authentication, authorization, tenant-awareness, permission-awareness, rate limiting, quotas, API security, Webhooks, Events, integrations, API lifecycle, API documentation, API observability, and API auditing. Full mechanism: `AI-API-STRATEGY.md` (API strategy and AI exposure), `INTEGRATION-FRAMEWORK.md` (webhooks/events/third-party integration), `AUTHENTICATION-AUTHORIZATION.md` (API auth), `SECURITY-GOVERNANCE.md` §API Threat Protection.

---

## 4. AI-Ready + AI-Powered Architecture

AI is a first-class Core Platform capability, not a bolt-on. The architecture must let AI be added to any capability without re-architecture: provider-agnostic, model-agnostic, tenant-aware, permission-aware, context-aware, auditable, governed, and API-accessible. AI may support assistance, automation, workflow intelligence, analytics, recommendations, search, decision support, operational intelligence, enterprise knowledge, and agentic workflows. Industry-specific AI may exist inside an Industry Suite, but one industry's AI implementation must never automatically become the universal AI architecture (MI 6.4). Full mechanism: `AI-API-STRATEGY.md`.

---

## 5. Multi-Tenant Architecture

One shared Core Platform serves many isolated tenants; there is never a separate platform per industry or per tenant. The platform is **server-authoritative** — clients never access protected business resources directly:

```
Single Enterprise Core
   ↓ Tenant chooses Subscription Plan (Free / Starter / Premium / Enterprise)
   ↓ Tenant receives: Website (Staff & Users) · CMS · ERP Dashboard ·
     Mobile App (Android/iOS) · Windows Desktop App (.exe/.msi) ·
     REST API · Webhooks · API Documentation
   ↓ Tenant configures: Branding · Themes · Modules · Workflows · Notifications · Integrations
   ↓ Ready to Live
```

**User access flow** (every protected request, every platform):

```
User → Web / Mobile / Windows Desktop → Secure Login → HTTPS / REST API
   → Authentication Service → Tenant Validation → Subscription Validation
   → License Validation → Device Registration Validation → RBAC Permission Validation
   → JWT Access Token → Refresh Token → Platform Access Granted
```

Without successful authentication, authorization, tenant validation, license validation, and server verification, no protected resource is served. Offline mode is available only to previously authenticated, authorized users under a configurable synchronization/security policy — never as an unauthenticated local mode. Full mechanism: `MULTI-TENANCY.md` (isolation, provisioning, lifecycle), `AUTHENTICATION-AUTHORIZATION.md`, `LICENSING-DEVICE-MANAGEMENT.md`.

---

## 6. Configuration / Metadata-First Architecture

```
Configuration → Metadata → Templates → Rules → Policies → Plugins →
Automation → AI Assistance → Validation → Authorization →
Business Rules → Platform Access
```

Configuration and extensibility are preferred over source-code change across every industry and every tenant (MI 6.6). Full mechanism: `CONFIGURATION-METADATA.md`.

---

## 7. Product Surfaces

The following surfaces are architecturally and conceptually distinct and must never be collapsed into a single generic "application":

SBGlobal Plus Corporate Website · Tenant Website · Tenant Application · Super Admin / Platform Administration · Industry Management Systems · Web Application · Mobile Application · Windows Desktop Application · API Platform · Webhooks · Developer / API Documentation · AI Platform.

Each surface consumes the same Core Platform business capability through the API-First path (§3); none re-implements business logic locally.

---

## 8. Super Admin vs. Tenant Admin

Two authority domains are architecturally separate and must never be confused:

- **Super Admin** — platform-level governance: Platform · Marketplace · Subscription · Branding Standards · Security Policies · Tenant Lifecycle · Module Ecosystem · AI Ecosystem · API Ecosystem · Deployment Policies · Identity · Authentication/Authorization Policies · License · Device Management · API Security · Session Management · Affiliate Program (Commission Rules, Referral Policies, Payout Management).
- **Tenant Admin** — tenant-level administration: Branding · Domains · Website · CMS · Dashboard · Mobile & Desktop Applications · Themes · Business Modules · API Key Integrations · AI Provider Keys · Third-Party Keys · Automation · Notifications · Workflows · Reports · Desktop Settings & Auto-Updates · Synchronization Policy · Device Registration & Management · Affiliate & Payout Settings.

---

## 9. Industry Suite & Management System Framework

### 9.1 Nine Equal Industry Suites

Healthcare · Education · eCommerce & Retail · NGO, Temple & Trust · Hospitality · Security & Facility Management · Manufacturing & Inventory · Professional Services · Government & Public Sector — all consuming the same Core Platform (see `VISION.md` §7 for the equality rule; it is not restated here).

### 9.2 Enterprise-Critical Management Systems Policy

Each Industry Suite defines a focused set of **Enterprise-Critical Management Systems** — the minimum complete operational capability for that industry. As a governance guideline (not a hard ceiling), each Industry Suite normally consists of **2–8 foundational Management Systems**, selected for business criticality, daily operational usage, enterprise-wide applicability, functional dependency, strategic business value, regulatory/compliance need, long-term architectural sustainability, and their collective ability to represent the industry's complete operational foundation. Exceptions beyond 2–8 require formal Enterprise Architecture Governance approval with documented business justification, architectural impact assessment, dependency analysis, and maintainability evaluation.

Illustrative examples (non-exhaustive; naming an industry's typical systems does not make that industry a template for the others — MI 5.2):

| Industry Suite | Typical Foundational Management Systems (illustrative) |
|---|---|
| Healthcare | Hospital Management System, Laboratory Information System, Radiology Information System, Pharmacy Management System, Clinic Management System |
| Education | School Management System, College & University Management System, Coaching & Training Management System, Learning Management System, Examination Management System |
| eCommerce & Retail | Retail Store Management System, Point of Sale Management System, Inventory & Warehouse Management System, Order Management System, Marketplace Management System |
| Manufacturing & Inventory | Production Management System, Inventory & Warehouse Management System, Quality Management System, Procurement Management System, Maintenance Management System |
| Hospitality | Hotel Management System, Restaurant Management System, Banquet & Event Management System, Reservation & Booking Management System |
| NGO, Temple & Trust | Donor Management System, Donation & Fund Management System, Temple Administration Management System, Membership & Volunteer Management System |
| Security & Facility Management | Security Guard Management System, Patrol Management System, Visitor Management System, Facility Maintenance Management System |
| Professional Services | CRM Management System, Project Management System, Service Delivery Management System, Resource & Timesheet Management System, Studio Management System (Photography/Videography) |
| Government & Public Sector | Citizen Service Management System, Case & File Management System, Permit & License Management System, Revenue & Tax Management System |

### 9.3 Core vs. Industry-Specific Separation

Any capability reusable across multiple industries belongs in the Core Platform, consumed by Industry Suites through configuration, metadata, APIs, events, plugins, or workflows — never reimplemented per industry. Capability beyond an Industry Suite's foundational Management Systems is implemented as optional, modular, configurable, extensible, or plugin-based, without altering the Core Platform. Full mechanism: `MODULE-FRAMEWORK.md`.

### 9.4 Industry-Neutrality Audit

Before any statement is finalized as Core Platform-tier content (in this document or any other Foundation document), it must be tested against at least three unrelated industries (e.g., a hospital, a school, a factory — MI Part 8, P6). A statement that fails for any of them is Industry-Specific content and belongs in that industry's Suite documentation, not here.

---

## 10. Deployment Architecture Posture

Production-ready by default for Shared Hosting (where applicable), cPanel, VPS, Dedicated Servers, and standard Cloud environments. Containerized deployment (Docker, Compose, Kubernetes, OpenShift) is optional, never mandatory. The architecture remains cloud-ready and horizontally scalable without depending on container orchestration. Full mechanism: `DEPLOYMENT-OPERATIONS.md`, `INSTALLATION-DEPLOYMENT.md`.

---

## 11. Cross-Platform Architecture

Web, Mobile (Android/iOS), and Windows Desktop (native `.exe`/`.msi`) consume the same API-First business capability (§3) and share one Synchronization Policy for offline-first operation. No platform implements its own copy of business logic. Full mechanism: `DESKTOP-APPLICATION.md`, `MOBILE-OFFLINE-SYNC.md`, `OFFLINE-SYNCHRONIZATION.md`.

---

## 12. Data & Integration Architecture (Summary)

Data architecture (schema, tenant isolation at the database level, naming, indexing, audit history) is fully owned by `DATA-ARCHITECTURE.md`. Third-party and cross-platform integration (webhooks, events, external system connectors) is fully owned by `INTEGRATION-FRAMEWORK.md`. Both consume and are consumed through the API-First path defined in §3 above.

---

## 13. Traceability

```
Primary Source of Truth (§4 Platform Scope & Access Flow, §7 Supported Core Industries)
        ↓
MI.md Parts 6–7 (Core Architecture Principles; Product Surface & Administrative Governance)
        ↓
ARCHITECTURE.md  (this document — public Knowledge Base expression)
        ↓
MULTI-TENANCY.md · MODULE-FRAMEWORK.md · AI-API-STRATEGY.md · CONFIGURATION-METADATA.md ·
DATA-ARCHITECTURE.md · INTEGRATION-FRAMEWORK.md · DEPLOYMENT-OPERATIONS.md · and all remaining
Foundation documents that instantiate this architecture
```

---

## 14. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 1. Expands MI.md Parts 6–7 and Primary Source §4/§7 into the public Knowledge Base. | ADL-2026-08-19-01 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§9.4) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
