# SBGlobal Plus — Module & Management System Framework (MODULE-FRAMEWORK.md)

**(Foundation Document 08 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 6.1, Part 6.2; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §7; `Docs/Raw knowledge files/02_SBGlobal_Plus_Product_Specification_Requirement.md` §45
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** MODULE-FRAMEWORK.md is the single owning document for how an Industry Suite is composed of Enterprise-Critical Management Systems, how those decompose into Modules/Sub-Modules/Workflows, and how a module attaches to, versions on, and detaches from the Core Platform without altering it (MI 6.2). It does not own the Core-vs-Industry-Suite-vs-Tenant layering itself (`ARCHITECTURE.md` §2, §9), third-party/public module distribution commerce (`MARKETPLACE.md`), the plugin SDK and extension-point API contract (`PLUGIN-DEVELOPMENT.md`), or per-tenant module enablement state (`MULTI-TENANCY.md` §5) — each is cross-referenced here rather than restated (MI Part 8, P3).

---

## 1. Purpose of This Document

MODULE-FRAMEWORK.md answers: what is a Management System, what is a Module, how many of each does an Industry Suite have, and by what governed mechanism does a Suite expand without touching the Core Platform. It expands `ARCHITECTURE.md` §9 (Industry Suite & Management System Framework) into the full Management System Expansion Principle (MI 6.2) and is the document every Industry Suite's own architecture document must remain consistent with.

---

## 2. Composition Hierarchy

Every Industry Suite is composed the same way, regardless of industry:

```
Industry Suite
   ↓
Enterprise-Critical Management Systems  (2–8 per Suite, see §3)
   ↓
Modules
   ↓
Sub-Modules
   ↓
Workflows / Business Rules / Master Data / Transactions / Reports / Analytics / AI / Automation / Integrations
```

This is the same layering named in `ARCHITECTURE.md` §2 (Core Architecture Layering) and §9.2, instantiated here as a governed composition rule rather than restated as a diagram.

---

## 3. Enterprise-Critical Management Systems Policy

A **Management System** is a major operational business domain within an Industry Suite — not an individual feature or module (e.g., a Hospital Management System, not a "patient intake form"). Each Industry Suite defines its own focused set of Enterprise-Critical Management Systems: the minimum complete operational capability required for that industry to be considered enterprise-ready.

- **Governance range:** normally **2–8 foundational Management Systems** per Industry Suite. This is a governance guideline against fragmentation, not a hard technical ceiling.
- **Selection criteria:** business criticality · daily operational usage · enterprise-wide applicability · functional dependency · strategic business value · regulatory/compliance need · long-term architectural sustainability · collective ability to represent the industry's complete operational foundation.
- **Exceeding the range** requires formal Enterprise Architecture Governance approval, with documented business justification, architectural impact assessment, dependency analysis, and maintainability evaluation — logged as a Review-Board decision (MI Part 8) in the Architecture Decision Log.
- **No industry's Management System set is a template for another's** (MI 5.1, 5.2) — the illustrative examples in `ARCHITECTURE.md` §9.2 name typical systems per industry without making any of them mandatory or normative for a different industry.
- Each Management System is designed as a complete enterprise-grade business domain in its own right — containing whatever modules, workflows, business rules, master data, transactional processes, reporting, analytics, integrations, AI capability, security, compliance, and lifecycle management it needs to operate as a mature system, while remaining fully integrated with the Core Platform through the API-First path (`ARCHITECTURE.md` §3).

---

## 4. Modules & Sub-Modules

A **Module** is a bounded, independently versionable unit of business capability inside a Management System (e.g., within a Hospital Management System: an Admissions Module, a Billing Module). A **Sub-Module** is a further bounded unit inside a Module.

Every Module:

- belongs to exactly one Management System, which belongs to exactly one Industry Suite;
- exposes its capability only through the API-First path (`ARCHITECTURE.md` §3) — never by a private, undocumented internal call another module or surface depends on;
- is independently enable/disable-able per tenant (state owned by `MULTI-TENANCY.md` §5), without requiring any other module in the same Management System to be enabled, unless a declared functional dependency (§6) requires it;
- consumes Core Platform shared services (Identity & Access, Workflow Engine, Notifications, Document Management, Reporting, AI Services, Audit, Configuration, Metadata, APIs, Integration, Automation, Analytics, Billing) rather than re-implementing them (MI 6.1) — a module that finds itself reimplementing one of these is a signal to generalize that capability into the Core Platform instead (MI Part 8, P1).

---

## 5. Core vs. Industry-Specific Boundary

Any capability that is reusable across multiple industries belongs in the Core Platform and is consumed by every Industry Suite's modules through configuration, metadata, APIs, events, plugins, or workflows — never reimplemented per module or per Suite. A capability beyond an Industry Suite's foundational Management Systems (§3) is implemented as an **optional, modular, configurable, extensible, or plugin-based** Management System or Module within that Suite, without affecting the Core Platform architecture. Before any capability is finalized as Core-tier, it passes the Industry-Neutrality Audit (`ARCHITECTURE.md` §9.4): tested against at least three unrelated industries; a capability that fails for any of them stays Industry-Specific.

---

## 6. Module Lifecycle & Dependency Model

Every module moves through the same governed lifecycle:

```
Registered → Installed (per tenant, per §5 in MULTI-TENANCY.md) → Enabled → Versioned/Updated →
(Disabled ⇄ Enabled) → Deprecated → Removed
```

- **Registered** — the module exists in the platform's module registry (owned architecturally here; distribution/discovery mechanics for third-party or public modules are owned by `MARKETPLACE.md`) with a declared Management System, Industry Suite, semantic version, and any declared functional dependencies on other modules or Core Platform services.
- **Installed / Enabled** — a tenant, within its Subscription Plan entitlement, enables the module; enablement state and per-tenant configuration are owned by `MULTI-TENANCY.md` §5.
- **Versioned/Updated** — a module updates independently of other modules and of the Core Platform, provided it continues to satisfy its declared API contract; breaking API changes follow the API lifecycle/versioning standard owned by `AI-API-STRATEGY.md`.
- **Disabled** — a tenant or Super Admin can disable a module without data loss, reversible back to Enabled.
- **Deprecated / Removed** — governed the same way any Foundation-tier rule removal is governed (`CORE-STANDARDS.md` §8.2; MI Part 8): classified, justified, and logged before removal, with tenant data export guaranteed first (`MULTI-TENANCY.md` §10).

A declared functional dependency between modules must be explicit (e.g., a Billing Module declaring a dependency on the Core Platform's Billing shared service, not on another Industry Suite's module) — undeclared, implicit cross-module coupling is a Verification failure under the Delivery Lifecycle (`CORE-STANDARDS.md` §8.3, §9).

---

## 7. Extensibility: Plugins & Marketplace (Cross-Reference)

The platform supports third-party and custom extension beyond the modules a Suite ships with, via a Plugin Architecture, Module Installer, and Marketplace-readiness (Extension SDK). This document owns the fact that the composition hierarchy (§2) and the Core/Industry boundary (§5) apply identically to a plugin-delivered module as to a natively shipped one — a plugin module is not exempt from the API-First path, the Core-vs-Industry-Specific boundary, or the Industry-Neutrality Audit. The plugin SDK contract, extension points, and sandboxing model are fully owned by `PLUGIN-DEVELOPMENT.md`; marketplace listing, distribution, and monetization mechanics are fully owned by `MARKETPLACE.md`.

---

## 8. Industry-Neutrality Audit

This document's rules were tested against three unrelated industries — a hospital, a school, and a manufacturing plant. In each: an Industry Suite decomposes into 2–8 Management Systems selected by the same criteria (§3); each Management System decomposes into Modules and Sub-Modules that consume, not reimplement, the same Core Platform shared services (§4); and the same lifecycle (§6) and Core/Industry boundary (§5) govern module expansion. The illustrative Management System examples in `ARCHITECTURE.md` §9.2 (Hospital Management System for Healthcare, School Management System for Education, Production Management System for Manufacturing, and so on) are retained there as non-normative, industry-owned examples and are not restated or re-ranked here (MI Part 8, P3; P6).

---

## 9. Traceability

```
Primary Source of Truth (§7 Supported Core Industries & Enterprise-Critical Management Systems Policy);
Raw Knowledge 02 §45 (Future Extension Policy — Plugin Architecture, Module Installer, Marketplace)
        ↓
MI.md Part 6.1 (Core Platform Principle); Part 6.2 (Management System Expansion Principle)
        ↓
ARCHITECTURE.md §2, §9 (layering; Industry Suite & Management System Framework — not restated here)
        ↓
MODULE-FRAMEWORK.md  (this document — composition hierarchy, MS policy, module lifecycle, Core/Industry boundary)
        ↓
MARKETPLACE.md · PLUGIN-DEVELOPMENT.md (extensibility depth) · MULTI-TENANCY.md §5 (per-tenant enablement state) ·
AI-API-STRATEGY.md (module API versioning depth) · every Industry Suite's own Management System documentation
```

---

## 10. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 2. Expands MI Part 6.1/6.2 and Primary Source §7 (plus Raw Knowledge 02 §45) into the public Knowledge Base; establishes the Management System composition hierarchy and module lifecycle. | ADL-2026-08-19-04 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§8) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
