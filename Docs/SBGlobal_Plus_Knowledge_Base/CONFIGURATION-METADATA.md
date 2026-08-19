# SBGlobal Plus — Configuration & Metadata Framework (CONFIGURATION-METADATA.md)

**(Foundation Document 12 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 6.6; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §10; `Docs/Raw knowledge files/02_SBGlobal_Plus_Product_Specification_Requirement.md` §7, §8, §39; `Docs/Raw knowledge files/07_SBGlobal_Plus_Enterprise_Default_Standards.md` (Setting Modules)
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** CONFIGURATION-METADATA.md is the single owning document for the Configuration/Metadata-First mechanism (MI 6.6): the full preference chain, the configuration scope hierarchy, the settings taxonomy, and the metadata-driven building blocks (templates, master data, lookup values, custom fields, feature flags) every other Foundation document relies on instead of source-code change. It does not own visual design tokens (`PLATFORM-BRANDING.md`), database schema for configuration storage (`DATA-ARCHITECTURE.md`), notification channel/template delivery mechanics (`NOTIFICATION-COMMUNICATION.md`), or per-tenant configuration state ownership (`MULTI-TENANCY.md` §5) — each is cross-referenced here rather than restated (MI Part 8, P3).

---

## 1. Purpose of This Document

CONFIGURATION-METADATA.md answers: in what order does the platform prefer to solve a business requirement without writing code, what is configurable, at what scope, and how is that configuration stored and validated. It expands `ARCHITECTURE.md` §6 (Configuration/Metadata-First Architecture) into the full Configuration/Metadata-First Principle and is the document every Foundation document's "full mechanism: `CONFIGURATION-METADATA.md`" cross-reference resolves to.

---

## 2. The Preference Chain

No business requirement is solved by a source-code change while a higher step in this chain can solve it:

```
Configuration → Metadata → Templates → Rules → Policies → Plugins →
Automation → AI Assistance → Server Validation → API Authorization →
Identity → Authentication → Authorization → License Validation →
Business Rules → Platform Access
```

Only the following genuinely require developer intervention and therefore sit outside this chain: framework changes, database schema changes, Core Architecture changes, security enhancements, performance optimizations, unsupported integrations, and net-new features. Everything else — including anything a Tenant Admin or Super Admin can reach through an admin panel — is expected to be solvable by moving left in the chain, not by writing code.

---

## 3. Configuration Scope Hierarchy

Configuration resolves through exactly four scopes, each able to override the one above it unless a higher scope explicitly locks a setting:

```
Platform (Super Admin default) → Industry Suite → Tenant → User
```

- **Platform scope** — Super Admin-set defaults and hard limits; the floor and ceiling every Industry Suite and Tenant operates within (`ARCHITECTURE.md` §8).
- **Industry Suite scope** — defaults appropriate to an industry (e.g., default report templates for a given Suite) that a Tenant in that Suite inherits unless it overrides them.
- **Tenant scope** — the Tenant Admin's independently configured values (`MULTI-TENANCY.md` §5); never permitted to weaken a Platform-scope security or compliance lock.
- **User scope** — an individual user's preferences (locale, notification channel preference, dashboard layout) within what the Tenant permits.

A setting that must never be overridden below Platform scope (e.g., the isolation guarantee in `MULTI-TENANCY.md` §2, the Security Baseline in `CORE-STANDARDS.md` §5) is declared **locked** at Platform scope; this is a configuration-governance concept owned here, while the specific list of locked security settings is owned by `SECURITY-GOVERNANCE.md`.

---

## 4. Settings Taxonomy

The following setting categories exist across the platform, each independently manageable without code change, each resolved through the scope hierarchy (§3): General · Branding · Theme · Typography · Localization · Session · Company · Branches · Departments · Users · Roles · Permissions · Master Data · Industry Module Settings (the industry-specific configuration surface each Management System exposes, per `MODULE-FRAMEWORK.md`) · Billing · Inventory · Communication (Email/SMS/WhatsApp) · Storage · Payment Gateway · API · AI · Security · Backup · Logs · Audit · CMS · Website · Tenant Portal Settings · Reports · Invoice · Notifications · Integrations · Subscription · Feature Flags.

Ownership of *depth* for several of these is elsewhere: Branding/Theme/Typography tokens → `PLATFORM-BRANDING.md`; Security/Backup/Logs/Audit depth → `SECURITY-GOVERNANCE.md`, `OBSERVABILITY-MONITORING.md`, `DATA-ARCHITECTURE.md`; Billing/Subscription depth → `BUSINESS-FRAMEWORK.md`; Communication depth → `NOTIFICATION-COMMUNICATION.md`; API/AI provider depth → `AI-API-STRATEGY.md`, `INTEGRATION-FRAMEWORK.md`. This document owns the taxonomy and the storage/versioning standard (§5–§6) that every one of them follows; it does not restate their individual field-level detail.

> **Industry-Neutrality Audit note:** the supporting raw knowledge's "LIS" setting-module entry (Laboratory Information System — a Healthcare-only artifact, MI Part 5.1) is generalized above to **Industry Module Settings**, the neutral category every Industry Suite's Management Systems populate with their own settings, so no single industry's setting module is named at Core Platform tier (MI Part 8, P6; ADL-2026-08-19-04).

---

## 5. Metadata-Driven Building Blocks

Business behavior is expressed through these reusable, database-stored building blocks rather than hardcoded logic:

- **Master Data & Lookup Values** — shared reference data (statuses, categories, units) editable through configuration; the master-data table standard (required columns, audit fields) is owned by `DATA-ARCHITECTURE.md`.
- **Custom Fields & Dynamic Fields** — tenant- or Suite-defined fields attachable to any entity without a schema migration.
- **Forms & Validation Rules** — form structure and validation logic defined as metadata, editable per scope (§3).
- **Templates** — Report, Invoice, Print, QR, PDF, Email, SMS, WhatsApp, and Notification templates; template *definition and versioning* is owned here as a metadata concept, while multi-channel delivery mechanics are owned by `NOTIFICATION-COMMUNICATION.md`.
- **Menus, Navigation, Dashboards, Widgets** — UI composition driven by configuration, not by per-tenant frontend code branches; visual token depth is owned by `PLATFORM-BRANDING.md`.
- **Feature Flags** — capability toggles resolved through the scope hierarchy (§3), used to gate module rollout (`MODULE-FRAMEWORK.md` §6) and plan-based entitlement (`BUSINESS-FRAMEWORK.md`) without a deploy.
- **Workflows, Business Rules, Policies** — condition/action logic configured per the preference chain (§2) rather than encoded in application logic; workflow *engine* mechanics are a Core Platform shared service (`ARCHITECTURE.md` §2) consumed, not reimplemented, by every module (`MODULE-FRAMEWORK.md` §4).

---

## 6. Storage & Versioning Standard

All configuration and metadata is stored in the database wherever reasonably possible — never hardcoded, never file-based where a database-backed alternative exists — so that it can be read, changed, and audited through the same governed path as any other tenant data. Every configuration and metadata change is versioned: **Configuration Version History** is a required audit category (cross-reference: `CORE-STANDARDS.md` §4 Non-Functional Requirements Baseline; audit-trail field standard owned by `DATA-ARCHITECTURE.md`). A configuration change at Tenant or User scope never requires a deployment; a change to what is configurable at all (a new setting category, a new metadata building block type) is itself governed as a Core Platform change under the normal Delivery Lifecycle (`CORE-STANDARDS.md` §8.3).

---

## 7. Industry-Neutrality Audit

Every rule in this document was tested against three unrelated industries — a hospital, a school, and a manufacturing plant — and holds identically: the same preference chain (§2), the same four-level scope hierarchy (§3), the same settings taxonomy with "Industry Module Settings" as the industry-neutral placeholder (§4), and the same metadata-driven building blocks (§5) apply regardless of which industry's Management Systems populate them. See §4 above for the specific generalization this audit required.

---

## 8. Traceability

```
Primary Source of Truth (§10 Dynamic/Configuration Philosophy);
Raw Knowledge 02 §7–§8, §39 (Global Configuration Policy; Dynamic Configuration); Raw Knowledge 07 (Setting Modules)
        ↓
MI.md Part 6.6 (Configuration/Metadata-First Principle)
        ↓
ARCHITECTURE.md §6 (Configuration/Metadata-First Architecture — not restated here)
        ↓
CONFIGURATION-METADATA.md  (this document — preference chain, scope hierarchy, taxonomy, metadata building blocks, storage/versioning standard)
        ↓
PLATFORM-BRANDING.md · NOTIFICATION-COMMUNICATION.md · BUSINESS-FRAMEWORK.md · SECURITY-GOVERNANCE.md ·
DATA-ARCHITECTURE.md · MODULE-FRAMEWORK.md · MULTI-TENANCY.md §5 (depth / per-tenant state owners)
```

---

## 9. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 2. Expands MI Part 6.6 and Primary Source §10 (plus Raw Knowledge 02 §7/§8/§39 and Raw Knowledge 07) into the public Knowledge Base; establishes the configuration scope hierarchy and settings taxonomy. | ADL-2026-08-19-04 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§7) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
