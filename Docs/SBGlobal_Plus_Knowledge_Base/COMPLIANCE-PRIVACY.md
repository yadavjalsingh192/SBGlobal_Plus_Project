# SBGlobal Plus — Compliance & Privacy (COMPLIANCE-PRIVACY.md)

**(Foundation Document 31 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 7.3; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §0 Recommendation #1/#4, §6.4, §6.6, §6.7, §12 (item 31); `Docs/Raw knowledge files/02_SBGlobal_Plus_Product_Specification_Requirement.md` §35
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** COMPLIANCE-PRIVACY.md is the single owning document for data privacy and regulatory-alignment framework, consent management, data subject rights, Data Processing Agreements, the certification roadmap (SOC 2 Type II / ISO 27001), and regulatory breach-notification timelines (MI 7.3; Primary Source Recommendations #1 and #4). It does not own the technical security-incident response runbook itself (`SECURITY-GOVERNANCE.md` §8), secrets/key management or API threat protection (`SECURITY-GOVERNANCE.md` §4–§5), the technical mechanism that makes region/data-center selection possible (`DATA-ARCHITECTURE.md` §11), or the Cookie Consent Banner UI component (owned at the marketing/website layer under Primary Source §11.4, not yet a published Foundation document) — each is cross-referenced here rather than restated (MI Part 8, P3). This document was newly introduced by the Primary Source's architect gap review (§0, Recommendations #1 and #4) because its content does not fit cleanly inside `SECURITY-GOVERNANCE.md` alone.

---

## 1. Purpose of This Document

COMPLIANCE-PRIVACY.md answers: which data-protection regulations does the platform align to, how is user consent captured and honored, how does a data subject exercise their rights, what does a tenant's Data Processing Agreement cover, what security-certification roadmap does the platform pursue, and on what timeline must a breach be disclosed. It expands `MI.md` Part 7.3 (Security and Compliance) into the full Compliance & Privacy standard and is the document every other Foundation document's "regulatory alignment," "consent management," or "breach-notification timeline" cross-reference resolves to.

---

## 2. Ownership Map

| Concern | Owning Document | This document's role |
|---|---|---|
| Regulatory alignment roadmap (GDPR, DPDP, HIPAA-readiness, SOC 2, ISO 27001) | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Consent Management (capture, storage, honoring consent) | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Data Subject Rights (right-to-access, right-to-erasure) | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Data Processing Agreements (DPA) | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Certification roadmap (SOC 2 Type II, ISO 27001) | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Regulatory breach-notification timelines and jurisdictional obligations | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership |
| Security Incident Response Plan (detection/triage/containment/recovery runbook) | `SECURITY-GOVERNANCE.md` §8 | Not owned here; this document supplies only the regulatory clock the plan must meet |
| Secrets & key management, API threat protection | `SECURITY-GOVERNANCE.md` §4–§5 | Not owned here; cross-referenced only |
| Technical mechanism for per-tenant/per-region data storage selection | `DATA-ARCHITECTURE.md` §11 | Not owned here; this document supplies the regulatory drivers only |
| Regulatory data-retention period feeding a table's archival policy | **COMPLIANCE-PRIVACY.md** (this document) | Full ownership — consumed by `DATA-ARCHITECTURE.md` §9, not redefined there |
| Cookie Consent Banner UI / Privacy Preference Center presentation | Marketing/website layer (Primary Source §11.4) | Not owned here; this document supplies the consent data model it presents |

---

## 3. Regulatory Alignment Roadmap

The platform pursues alignment with the following, as a roadmap rather than a one-time claim — each is tracked to a maturity stage (Planned / In Progress / Aligned / Certified) rather than asserted as complete by default:

- **GDPR** (EU General Data Protection Regulation) — applies to any tenant or data subject within its jurisdictional scope, regardless of the tenant's Industry Suite.
- **India's Digital Personal Data Protection (DPDP) Act, 2023** — applies to any tenant or data subject within its jurisdictional scope.
- **HIPAA-readiness** — available as an Industry Suite-layer capability for tenants operating in a regulated-health context; this is a jurisdiction-and-context-driven alignment a Healthcare Industry Suite tenant opts into, not a Core Platform-tier default applied to every tenant (§8 Industry-Neutrality Audit).
- **SOC 2 Type II** and **ISO 27001** — platform-wide security-management-system alignment, tracked under the Certification Roadmap (§7).

Which alignments apply to a given tenant is determined by that tenant's jurisdiction and regulatory context, evaluated the same way regardless of Industry Suite; a tenant's Data Residency selection (`DATA-ARCHITECTURE.md` §11) and this document's alignment tracking are configured together, not independently.

---

## 4. Consent Management

- **Capture** — user consent (e.g., cookie/privacy preference, marketing communication opt-in, data-processing purpose acknowledgment) is captured at the point of collection, with the specific purpose stated at capture time.
- **Storage** — consent records are stored with the same audit-trail field standard as any other data (`DATA-ARCHITECTURE.md` §7: attribution and timestamp fields), so a consent's provenance and history are always reconstructable.
- **Honoring consent** — every downstream capability that depends on consent (communications, tracking, data processing for a stated purpose) checks the current consent record before acting; consent is never assumed.
- **Presentation layer** — this document owns the consent data model and the honoring guarantee; the Cookie Consent Banner / Privacy Preference Center widget that captures it at the website layer (Primary Source §11.4) is a presentation surface that reads and writes to this data model, not a separate consent authority.

---

## 5. Data Subject Rights

- **Right to Access** — a data subject may request a copy of the personal data the platform holds about them; the request is logged and fulfilled within the alignment roadmap's applicable regulatory timeline (§3).
- **Right to Erasure** — a data subject may request deletion of their personal data, subject to any overriding legal retention obligation; fulfillment follows the Soft-Delete-then-governed-purge lifecycle owned by `DATA-ARCHITECTURE.md` §9, with this document supplying the regulatory trigger and timeline, not the deletion mechanics themselves.
- Both rights are available to a data subject regardless of Industry Suite, Tenant, or Subscription Plan; no tier gates a data subject's regulatory rights (§8).

---

## 6. Data Processing Agreements (DPA)

A Data Processing Agreement is available per tenant, documenting the platform's role as data processor (or controller, where applicable) for that tenant's data, the categories of data processed, the purposes of processing, and the sub-processors involved. DPA availability is a Tenant-scope capability (`CONFIGURATION-METADATA.md` §3) that does not vary by Industry Suite; its legal terms are a compliance artifact owned here, distinct from the commercial subscription agreement owned by `BUSINESS-FRAMEWORK.md`.

---

## 7. Certification Roadmap

- **SOC 2 Type II** and **ISO 27001** alignment are tracked as platform-wide milestones, each independent of the MI Part 10 document-certification concept (`CORE-STANDARDS.md` §8.3): a "Certified" Foundation document milestone and a "SOC 2 Type II Certified" compliance milestone are different achievements that must never be conflated in reporting.
- Certification-readiness depends on the Vulnerability & Incident Response Program (`SECURITY-GOVERNANCE.md` §8) operating on the cadence that program defines; this document tracks the compliance milestone the program's operation supports, without restating the program itself.
- Progress against this roadmap is reported the same way for every tenant and Industry Suite; no Industry Suite receives an accelerated or deferred certification claim (§8).

---

## 8. Breach Notification

This document owns the regulatory notification deadlines and jurisdictional obligations that apply once `SECURITY-GOVERNANCE.md` §8's Security Incident Response Plan determines a breach has occurred:

- The applicable notification deadline is determined by which regulatory alignments (§3) govern the affected tenant's data.
- `SECURITY-GOVERNANCE.md` §8 guarantees that a breach triggers the incident response plan; this document guarantees only that the plan's execution is measured against the correct regulatory clock and that affected parties are notified within it.
- Breach notification content and process are never weakened or delayed based on Industry Suite, Tenant Subscription Plan, or region — only the specific regulatory deadline varies, and only because the underlying law varies (§8).

---

## 9. Data Residency & Sovereignty (Regulatory Drivers)

Where `DATA-ARCHITECTURE.md` §11 makes per-tenant/per-region data storage selection technically possible, this document supplies the regulatory reasoning that determines which region a given tenant must select: jurisdictional data-sovereignty law, sectoral regulation, and the tenant's own contractual requirements. A documented data-flow map for any cross-border transfer is maintained here, cross-referencing `MULTI-TENANCY.md` §10 for the tenant-level data-governance guarantee it feeds, without restating the storage mechanism itself.

---

## 10. Industry-Neutrality Audit

Every rule in this document was tested against three unrelated industries — a hospital, a school, and a manufacturing plant — and holds identically: the same Consent Management data model (§4), the same Data Subject Rights (§5), the same DPA availability (§6), the same Certification Roadmap (§7), and the same Breach Notification guarantee (§8) apply regardless of industry. Where supporting raw knowledge listed "HIPAA Readiness" as a compliance capability scoped explicitly to a "Healthcare & Diagnostics Vertical," this document preserves that scoping rather than promoting it to a Core Platform-tier default (§3): every Industry Suite receives the same regulatory-alignment *mechanism*, and each tenant's *applicable* alignments are determined by its own jurisdiction and regulatory context, never by which industry it belongs to (MI Part 5.1).

---

## 11. Traceability

```
Primary Source of Truth §0 (Recommendations #1, #4), §6.4 (Data Privacy & Regulatory Compliance),
§6.6 (Encryption, cross-reference only), §6.7 (Data Residency), §12 (Documentation Standard, item 31);
Product Specification Requirement raw knowledge §35 (Compliance, business-level)
        ↓
MI.md Part 7.3 (Security and Compliance)
        ↓
SECURITY-GOVERNANCE.md §8 (Incident Response Program this document supplies the regulatory clock for — not restated here)
        ↓
COMPLIANCE-PRIVACY.md  (this document — regulatory alignment roadmap, consent management,
data subject rights, Data Processing Agreements, certification roadmap, breach-notification timelines,
data residency regulatory drivers)
        ↓
AUTHENTICATION-AUTHORIZATION.md · DATA-ARCHITECTURE.md §9, §11 · MULTI-TENANCY.md §10 ·
BUSINESS-FRAMEWORK.md (depth / consuming owners)
```

---

## 12. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 4. Expands MI Part 7.3 and Primary Source §6.4/§6.7 (plus Product Specification Requirement §35) into the public Knowledge Base as the 31st and final Foundation document named in Primary Source §12; establishes the Regulatory Alignment Roadmap, Consent Management, Data Subject Rights, Data Processing Agreements, the Certification Roadmap, and regulatory Breach Notification timelines, including the Industry-Neutrality scoping of HIPAA-readiness to its jurisdictional/regulatory trigger rather than a per-industry default. | ADL-2026-08-19-07 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§10) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
