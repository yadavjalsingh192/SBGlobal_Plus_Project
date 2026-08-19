# SBGlobal Plus — Data Architecture (DATA-ARCHITECTURE.md)

**(Foundation Document 13 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/SBGlobal_Plus_Knowledge_Base/CORE-STANDARDS.md` §2; `Docs/Raw knowledge files/04_SBGlobal_Plus_Database_Architecture_Standards.md`; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §6.7
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** DATA-ARCHITECTURE.md is the single owning document for database schema architecture, tenant isolation at the database level, table taxonomy, naming/identifier conventions, the audit-trail field standard, performance, data governance, backup/disaster recovery, and data residency mechanics (`CORE-STANDARDS.md` §2). It does not own application/API-level security controls or secrets management (`SECURITY-GOVERNANCE.md`), configuration/metadata semantics above the storage layer (`CONFIGURATION-METADATA.md`), regulatory compliance depth (`COMPLIANCE-PRIVACY.md`), or AI knowledge-store usage semantics (`AI-API-STRATEGY.md` §8) — each is cross-referenced here rather than restated (MI Part 8, P3).

---

## 1. Purpose of This Document

DATA-ARCHITECTURE.md answers: how is data physically structured, isolated, named, audited, secured at rest, backed up, and located, so that every Core Platform capability and every Industry Suite stores data consistently. It expands `CORE-STANDARDS.md` §2's Ownership Map entry for database concerns into the full Data Architecture standard and resolves the "physical implementation decision owned by `DATA-ARCHITECTURE.md`" deferral made in `MULTI-TENANCY.md` §2.

---

## 2. Ownership Map

| Concern | Owning Document | This document's role |
|---|---|---|
| Database engine, schema architecture, table taxonomy | **DATA-ARCHITECTURE.md** (this document) | Full ownership |
| Tenant isolation strategy at the database level | **DATA-ARCHITECTURE.md** (this document) | Full ownership — satisfies the architectural guarantee owned by `MULTI-TENANCY.md` §2 |
| Naming, identifier, and indexing conventions | **DATA-ARCHITECTURE.md** (this document) | Full ownership |
| Audit-trail field standard (Created/Updated/Deleted By/At, soft delete) | **DATA-ARCHITECTURE.md** (this document) | Full ownership |
| Backup, restore, disaster recovery | **DATA-ARCHITECTURE.md** (this document) | Full ownership |
| Data residency / region selection mechanics | **DATA-ARCHITECTURE.md** (this document) | Full ownership; regulatory driver owned by `COMPLIANCE-PRIVACY.md` |
| Application/API security controls, secrets management | `SECURITY-GOVERNANCE.md` | Baseline principle only (§3); depth cross-referenced |
| Configuration/metadata storage semantics (what is configurable, at what scope) | `CONFIGURATION-METADATA.md` | Storage standard only (§6); depth cross-referenced |
| Regulatory alignment, data-flow maps for cross-border transfer | `COMPLIANCE-PRIVACY.md` | Not owned here; cross-referenced only |

---

## 3. Database Engine & Architecture Posture

- **Engine** — MySQL as the default database engine, with MariaDB supported and PostgreSQL as a future-supported engine. Engine choice does not alter any standard in this document.
- **Architecture posture** — Multi-Tenant, Configuration-Driven, Database-Driven, Modular, Scalable, Normalized, and API-First, consistent with `ARCHITECTURE.md` §2 and §6.
- **Security baseline** — every database follows the Application & API Security Controls baseline (`SECURITY-GOVERNANCE.md` §3): encrypted fields for sensitive data, password hashing, API token security, and access logging are enforced at the data layer as the storage-layer instantiation of that baseline, not restated in depth here.

---

## 4. Tenant Isolation at the Database Level

`MULTI-TENANCY.md` §2 owns the architectural guarantee that cross-tenant data access is never permitted; this document owns the physical strategy that satisfies it:

- **Isolation strategy** — the platform supports row-level tenant-key isolation (a `tenant_id` foreign key present and indexed on every tenant-scoped table) as the default strategy, with schema-per-tenant or a hybrid approach available where a specific deployment's scale or regulatory posture (`COMPLIANCE-PRIVACY.md`) requires it. Whichever strategy a deployment uses, every tenant-scoped query is filtered by tenant at the data-access layer — never left to be filtered correctly by each caller.
- **Enforcement point** — tenant-scoping is enforced identically regardless of product surface (Web, Mobile, Desktop, API, AI-context — `MULTI-TENANCY.md` §2), applied before any query executes, not as a post-query filter.
- **No cross-tenant joins** — a query never joins across two tenants' data, and no tenant can enumerate or infer another tenant's identifiers through sequential or predictable key structures (§6).

---

## 5. Table Taxonomy

Every database follows the same structural taxonomy regardless of Industry Suite: Master Tables, Transaction Tables, Mapping Tables, Configuration Tables, Audit Tables, Log Tables, Notification Tables, Queue Tables, AI Tables, Template Tables, CMS Tables, API Tables, Analytics Tables, Session Tables, and Security Tables. An Industry Suite's Management Systems populate these categories with their own domain tables (e.g., a Suite's own master/transaction data — `ARCHITECTURE.md` §9.3) without introducing a new top-level category at Core Platform tier; a genuinely new category is a Core Platform change under the normal Delivery Lifecycle (`CORE-STANDARDS.md` §8.3).

---

## 6. Identifiers & Naming Conventions

- **Identifiers** — UUID Primary Key on every table; Tenant ID on every tenant-scoped table; Branch ID and Department ID where organizational sub-scoping applies; an Industry Vertical Suite reference per Tenant, resolving which Suite(s) a tenant's data belongs to.
- **Naming standard** — `snake_case` for all database identifiers; plural table names (`invoices`, not `invoice`); singular model/entity names in application code; consistent Foreign Key naming; consistent Index naming.
- UUIDs and naming conventions apply identically across Core Platform tables and every Industry Suite's tables — no Suite defines its own naming dialect.

---

## 7. Audit-Trail & Data Standards

Every table carries the same baseline audit fields, forming the field-level audit standard cross-referenced by `CORE-STANDARDS.md` §2, `CONFIGURATION-METADATA.md` §6, and `MULTI-TENANCY.md` §3:

- **Soft Delete** — records are marked deleted, never physically removed, except at a governed purge event (`MULTI-TENANCY.md` §3, Archived/Purged).
- **Attribution fields** — Created By, Updated By, Deleted By.
- **Timestamp fields** — Created At, Updated At, Deleted At.
- **Configuration Version History** — required wherever a table stores configuration or metadata state (`CONFIGURATION-METADATA.md` §6), using this same field standard.

These fields are mandatory on every Core Platform and Industry Suite table that stores business or configuration data; a table that cannot supply them (e.g., a pure log/queue table with its own append-only audit shape) documents the deviation explicitly rather than silently omitting the standard.

---

## 8. Performance & Scalability

Indexes and Composite Indexes on tenant-scoped and frequently queried columns · Query Optimization · Pagination on every list-returning endpoint · Caching for frequently accessed data (coordinated with the caching standard in `CORE-STANDARDS.md` §4) · Lazy Loading and Eager Loading applied deliberately, not by default · Table Partitioning-Ready schema design · Read-Replica-Ready architecture for horizontal read scaling. These satisfy the Scalability and Performance Non-Functional Requirements baseline (`CORE-STANDARDS.md` §4) at the data layer specifically.

---

## 9. Data Governance

- **Validation & integrity** — Validation Rules enforced at the data layer in addition to application-layer validation; Reference/Referential Integrity enforced through foreign key constraints; no orphan records.
- **Schema change management** — Migration-based schema management with Schema Versioning and Migration Version Control; every migration has a documented Rollback Strategy; Seeder Standards for repeatable, environment-safe demo/reference data.
- **Lifecycle management** — Data Archival Strategy and Data Retention Policy define how data moves from Active to Archived (`MULTI-TENANCY.md` §3); the regulatory retention period that drives a given industry's or jurisdiction's retention policy is supplied by `COMPLIANCE-PRIVACY.md`, not invented here.

---

## 10. Backup & Disaster Recovery

Daily, Weekly, and Monthly Backup schedules for both database and file storage · Backup Verification as a required, not optional, step · Restore Capability tested, not merely assumed · Disaster Recovery procedures documented and exercised. This is the data-layer instantiation of the Backup & Recovery Non-Functional Requirement (`CORE-STANDARDS.md` §4); deeper operational cadence, SLA targets, and infrastructure specifics are owned by `DEPLOYMENT-OPERATIONS.md`.

---

## 11. Data Residency & Sovereignty

Where the underlying infrastructure permits, the platform supports Configurable Region / Data-Center Selection per Tenant, Regional Database Instance support, and Data Sovereignty Compliance Mapping. This document owns the mechanism that makes region selection technically possible; the regulatory drivers, cross-border transfer documentation, and jurisdictional obligations that determine *which* region a given tenant must select are owned by `COMPLIANCE-PRIVACY.md` and `MULTI-TENANCY.md` §10 (which this document does not restate).

---

## 12. Integration Touchpoints

The data layer is reached through REST API, and where an Industry Suite's regulatory or interoperability context requires it, industry-standard data-exchange formats (e.g., healthcare interoperability standards for a Healthcare Industry Suite) alongside Webhook, Import, Export, Queue, and Scheduler mechanisms. Full ownership of integration mechanics (connectors, webhook delivery, third-party data exchange) belongs to `INTEGRATION-FRAMEWORK.md`; this document guarantees only that the underlying data it exposes follows the taxonomy, naming, and audit standards above regardless of which integration mechanism reaches it.

---

## 13. Industry-Neutrality Audit

Every rule in this document was tested against three unrelated industries — a hospital, a school, and a manufacturing plant — and holds identically: the same table taxonomy (§5), the same identifier/naming conventions (§6), the same audit-trail field standard (§7), and the same tenant isolation strategy (§4) apply regardless of which industry's Management Systems populate the schema. Where supporting raw knowledge listed a healthcare-specific interoperability standard as a named integration format (reflecting the Healthcare/LIS concentration noted at MI Part 5.1), §12 above generalizes this to "industry-standard data-exchange formats" applicable to whichever Industry Suite's regulatory context requires them, rather than naming a single industry's standard at Core Platform tier (MI Part 8, P6; ADL-2026-08-19-06).

---

## 14. Traceability

```
Database Architecture Standards raw knowledge (full document); Primary Source of Truth §6.7 (Data Residency & Sovereignty)
        ↓
CORE-STANDARDS.md §2 (Ownership Map — database schema/tenant-isolation-at-DB-level deferral)
        ↓
MULTI-TENANCY.md §2 (isolation guarantee this document's strategy must satisfy — not restated here)
        ↓
DATA-ARCHITECTURE.md  (this document — schema architecture, tenant isolation strategy, table taxonomy,
naming/identifier conventions, audit-trail field standard, performance, governance, backup/DR, data residency)
        ↓
SECURITY-GOVERNANCE.md · CONFIGURATION-METADATA.md §6 · COMPLIANCE-PRIVACY.md ·
INTEGRATION-FRAMEWORK.md · AI-API-STRATEGY.md §8 (depth / consuming owners)
```

---

## 15. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 3. Expands `CORE-STANDARDS.md` §2 and the Database Architecture Standards raw knowledge (plus Primary Source §6.7) into the public Knowledge Base; establishes the database-level tenant isolation strategy deferred by `MULTI-TENANCY.md` §2, the table taxonomy, naming/identifier conventions, and the audit-trail field standard referenced by `CORE-STANDARDS.md`, `CONFIGURATION-METADATA.md`, and `MULTI-TENANCY.md`. | ADL-2026-08-19-05, ADL-2026-08-19-06 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§13) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
