# SBGlobal Plus — Multi-Tenancy (MULTI-TENANCY.md)

**(Foundation Document 07 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 6.5, Part 7.2; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §4, §8, §9
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** MULTI-TENANCY.md is the single owning document for the Tenant entity, its isolation guarantee, its lifecycle, and the complete scope of what is independently tenant-owned (MI 6.5). It does not own database-level isolation mechanics (`DATA-ARCHITECTURE.md`), authentication mechanics (`AUTHENTICATION-AUTHORIZATION.md`), license/device enforcement (`LICENSING-DEVICE-MANAGEMENT.md`), subscription/billing commercial mechanics (`BUSINESS-FRAMEWORK.md`), branding visual tokens (`PLATFORM-BRANDING.md`), sync engine mechanics (`OFFLINE-SYNCHRONIZATION.md`, `MOBILE-OFFLINE-SYNC.md`), or regulatory/residency depth (`COMPLIANCE-PRIVACY.md`) — each is cross-referenced here rather than restated (MI Part 8, P3).

---

## 1. Purpose of This Document

MULTI-TENANCY.md answers: what is a Tenant, what does it guarantee, how does it come into existence and leave, and what is every tenant independently entitled to configure and own. It expands `ARCHITECTURE.md` §5 (which owns the cross-cutting access-flow diagram) into the full Multi-Tenant Principle (MI 6.5) and is the document every Industry Suite, Management System, and tenant-facing product surface must remain consistent with when it makes a tenant-scoping claim.

---

## 2. Tenant Concept & Isolation Guarantee

A **Tenant** is the top-level ownership boundary of the shared Core Platform: one organization (an enterprise, an institution, a business, a branch network) operating under one subscription, with its own users, data, configuration, and branding, on the same shared Core Platform codebase and infrastructure as every other tenant.

**The isolation guarantee is absolute and non-negotiable:**

- Cross-tenant data access is never permitted, under any role, at any layer.
- No tenant can discover, enumerate, or infer the existence, identity, or data of another tenant.
- Isolation applies uniformly at the data layer, the API layer, the storage layer, the cache layer, the queue layer, and the AI-context layer — a request scoped to Tenant A must never be able to read, write, or influence Tenant B's resources.
- Isolation is enforced **server-side** as part of the Server-Authoritative Architecture (`ARCHITECTURE.md` §5): every protected request is Tenant-Validated before Subscription Validation, License Validation, and RBAC Permission Validation are even evaluated.

Database-level isolation strategy (schema-per-tenant vs. row-level tenant-key isolation vs. hybrid, and the naming/indexing convention that enforces it) is a physical implementation decision owned by `DATA-ARCHITECTURE.md`; this document owns the architectural guarantee that strategy must satisfy, not the strategy itself.

---

## 3. Tenant Lifecycle

Every tenant moves through the same governed lifecycle regardless of industry or subscription plan:

```
Provisioning → Active → (Suspended ⇄ Active) → Offboarding → Archived / Purged
```

- **Provisioning** — tenant record created, subscription plan selected (self-serve for Free/Starter per Primary Source §4; assisted/approval-gated for Premium/Enterprise), initial Super Admin-approved default configuration applied, tenant-scoped storage and identifiers allocated. No tenant is Active until Tenant Validation, Subscription Validation, and initial security policy assignment succeed.
- **Active** — full access per subscription plan and configuration; the tenant independently configures itself per §5 without any source-code change.
- **Suspended** — access to protected resources withdrawn (e.g., non-payment, policy violation, Super Admin action, or tenant self-suspension) while data is retained intact; a suspended tenant can be restored to Active without data loss.
- **Offboarding** — tenant-initiated or Super-Admin-initiated exit; data export capability is guaranteed before deletion (see §10, Data Governance).
- **Archived / Purged** — retained per the tenant's data-retention and regulatory obligation (`COMPLIANCE-PRIVACY.md`) before final purge; a purge is irreversible and logged (`OBSERVABILITY-MONITORING.md`, audit trail).

Every lifecycle transition is Super Admin-governed (`ARCHITECTURE.md` §8, Tenant Lifecycle) and is an auditable event (audit trail standard: `DATA-ARCHITECTURE.md`).

---

## 4. What Every Tenant Independently Receives

On reaching Active state, per the platform-wide access flow (`ARCHITECTURE.md` §5), a tenant receives, scoped entirely to itself:

Website (Staff & Users) · CMS · ERP Dashboard · Mobile App (Android/iOS) · Windows Desktop App (.exe/.msi) · REST API · Webhooks · API Documentation.

Which of these surfaces are enabled, and at what capability tier, is governed by the tenant's Subscription Plan (Free / Starter / Premium / Enterprise) — plan-to-capability mapping is owned by `BUSINESS-FRAMEWORK.md`; this document guarantees only that whichever surfaces are enabled are always tenant-isolated per §2.

---

## 5. Tenant Configuration Scope

Every tenant independently configures the following, always without a source-code change (Configuration/Metadata-First Principle, MI 6.6 — mechanism owned by `CONFIGURATION-METADATA.md`):

| Scope Area | This document's role | Depth owned by |
|---|---|---|
| Branding, Domains, Website, CMS, Themes | Confirms tenant-scoping | `PLATFORM-BRANDING.md` (tokens, themes) |
| Dashboard, Mobile & Desktop App configuration | Confirms tenant-scoping | `DESKTOP-APPLICATION.md`, `MOBILE-OFFLINE-SYNC.md` |
| Business Modules enabled for the tenant | Confirms tenant-scoping | `MODULE-FRAMEWORK.md` (what a module is and how it attaches) |
| API Key Integrations, Third-Party Service Keys | Confirms tenant-scoping | `INTEGRATION-FRAMEWORK.md` |
| AI Provider Keys | Confirms tenant-scoping, per-tenant key isolation | `AI-API-STRATEGY.md` |
| Automation, Notifications, Workflows, Reports | Confirms tenant-scoping | `NOTIFICATION-COMMUNICATION.md`, `CONFIGURATION-METADATA.md` |
| Desktop Settings & Auto-Updates | Confirms tenant-scoping | `DESKTOP-APPLICATION.md` |
| Synchronization Policy (offline/online rules, background sync, local storage policy) | Confirms tenant-scoping | `OFFLINE-SYNCHRONIZATION.md` |
| Device Registration & Management | Confirms tenant-scoping | `LICENSING-DEVICE-MANAGEMENT.md` |
| Authorization Policies, Authentication Settings | Confirms tenant-scoping | `AUTHENTICATION-AUTHORIZATION.md` |
| License Management, API Endpoint Configuration | Confirms tenant-scoping | `LICENSING-DEVICE-MANAGEMENT.md` |
| Affiliate & Payout Settings | Confirms tenant-scoping | `AFFILIATE-FRAMEWORK.md` |

This table is the tenant-scoping instantiation of `CORE-STANDARDS.md` §2's Ownership Map discipline: MULTI-TENANCY.md confirms *that* every listed area is tenant-owned and isolated; it never restates *how* each area works.

---

## 6. Subscription, Billing & Licensing (Baseline)

Every tenant operates under exactly one active Subscription Plan (Free / Starter / Premium / Enterprise) at a time, which gates enabled product surfaces (§4), enabled modules (`MODULE-FRAMEWORK.md`), and enforced limits (users, devices, storage, API rate). Plan definition, pricing, upgrade/downgrade mechanics, invoicing, and payment-provider integration are fully owned by `BUSINESS-FRAMEWORK.md`. License issuance, activation, and device-binding enforcement are fully owned by `LICENSING-DEVICE-MANAGEMENT.md`. This document's role is limited to guaranteeing that a tenant's plan and license state are evaluated as part of the mandatory Server-Authoritative access flow (`ARCHITECTURE.md` §5) before any protected resource is served.

---

## 7. Tenant Security Policies (Baseline)

Each tenant may configure, within limits set by Super Admin Security Policy (`ARCHITECTURE.md` §8): authentication method availability, session and device trust rules, IP/geo restrictions, and data residency preference where the underlying architecture permits it (§10). Full application/API security control depth, secrets/key management, and API threat protection are owned by `SECURITY-GOVERNANCE.md`; this document guarantees only that tenant-level security configuration can never weaken the platform-wide Security Baseline (`CORE-STANDARDS.md` §5).

---

## 8. Users, Devices & Authorization Within a Tenant

Users, their roles/permissions, and their registered devices are always scoped to exactly one tenant (a person with access to multiple tenants holds one distinct identity per tenant, never a single cross-tenant identity). Authentication mechanism depth (methods, adaptive/risk-based authentication, digital identity/signature providers) is owned by `AUTHENTICATION-AUTHORIZATION.md`. Device registration, trust, and licensing enforcement depth is owned by `LICENSING-DEVICE-MANAGEMENT.md`. This document guarantees only that no user or device identity, session, or permission grant is ever valid outside the single tenant it was issued under.

---

## 9. Synchronization & Offline Access

Offline mode is available only to a previously authenticated, authorized user of a specific tenant, under that tenant's configurable Synchronization Policy — never as an unauthenticated or cross-tenant local mode (`ARCHITECTURE.md` §5). Locally cached or synchronized data on a device is scoped to the single tenant the device is registered under. Sync engine mechanics (retry queues, conflict resolution, cross-platform sync scope) are owned by `OFFLINE-SYNCHRONIZATION.md`; mobile-specific offline UX and local storage are owned by `MOBILE-OFFLINE-SYNC.md` (see the scope split recorded in the Primary Source of Truth §12 scope note, carried forward here without restatement).

---

## 10. Data Governance, Residency & Localization

Each tenant's data is independently owned, independently exportable on request, and independently deletable at offboarding (§3), subject to the retention and regulatory obligations owned by `COMPLIANCE-PRIVACY.md`. Where the underlying infrastructure permits, a tenant may select a preferred data storage region (Data Residency / Region Selection); the mechanics of that selection and cross-border transfer documentation are owned by `COMPLIANCE-PRIVACY.md` and `DATA-ARCHITECTURE.md`. Localization (language, locale, timezone, currency, number/date formatting) is configured per tenant and, where needed, per user within a tenant, through the Configuration/Metadata-First mechanism (`CONFIGURATION-METADATA.md`); this document confirms only that localization state is always tenant-scoped, never platform-global.

---

## 11. Industry-Neutrality Audit

Every rule in this document was tested against three unrelated industries — a hospital, a school, and a manufacturing plant — and holds identically for all three: each is a Tenant with the same isolation guarantee, the same lifecycle, the same configuration scope table, and the same server-authoritative access flow. Where supporting raw knowledge described tenant isolation using industry-specific examples (e.g., "Independent Patients," "Independent Doctors," reflecting the Healthcare/LIS concentration of the supplied raw knowledge — MI Part 5.1), this document generalizes those into the industry-neutral entities every Industry Suite actually needs (independent users, independent operational records, independent master data) rather than naming a single industry's domain objects at Core Platform tier (MI Part 8, P6; logged as ADL-2026-08-19-04).

---

## 12. Traceability

```
Primary Source of Truth (§4 Platform Scope & Access Flow, §8 Super Admin Philosophy, §9 Tenant Philosophy)
        ↓
MI.md Part 6.5 (Multi-Tenant Principle); Part 7.2 (Super Admin vs. Tenant Admin)
        ↓
ARCHITECTURE.md §5 (cross-cutting access-flow diagram — not restated here)
        ↓
MULTI-TENANCY.md  (this document — Tenant entity, isolation guarantee, lifecycle, configuration-scope ownership map)
        ↓
BUSINESS-FRAMEWORK.md · LICENSING-DEVICE-MANAGEMENT.md · AUTHENTICATION-AUTHORIZATION.md ·
DATA-ARCHITECTURE.md · SECURITY-GOVERNANCE.md · COMPLIANCE-PRIVACY.md · OFFLINE-SYNCHRONIZATION.md ·
MOBILE-OFFLINE-SYNC.md · PLATFORM-BRANDING.md · MODULE-FRAMEWORK.md · AFFILIATE-FRAMEWORK.md (depth owners)
```

---

## 13. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 2. Expands MI Part 6.5 and Primary Source §4/§8/§9 into the public Knowledge Base; establishes the Tenant lifecycle and the tenant configuration-scope Ownership Map. | ADL-2026-08-19-04 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§11) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
