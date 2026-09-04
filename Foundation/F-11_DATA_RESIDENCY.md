# F-11 — TENANT DATA RESIDENCY MODEL (RR-02 RESOLUTION)
**Document ID:** F-11 · **Version:** 1.0 · **Status:** SPECIFIED · Resolves REVIEW_REQUIRED RR-02 under explicit user authorization (Authority tier 2). Decision recorded as **D-DECISIONS DR-01**. Provenance: requirement `[SD: S1 §6.7, S2.4]`; mechanism `[AC + UD]`. Cross-refs: F-03 §5–§6, F-01 §4, F-02 W-04/W-14.

## 1. Decision (DR-01) — Regional Data Home model — ACTIVE

**Context:** the corpus requires per-tenant/per-region data storage "where architecture permits" and regional DB instance support, without defining the mechanism. The mechanism materially affects tenant data boundaries; the user has explicitly authorized its resolution.

**Decision:** the platform adopts a **Regional Data Home** model: one logical Core Platform (single codebase, one control plane) operating over **one or more Regional Data Homes** — regional database + file/media storage locations. Every Tenant is assigned **exactly one Data Residency Region at tenant creation** (F-02 W-04, BR-W04-3); all tenant-owned data classes (business/transaction data, documents/media, AI knowledge & memory, backups) reside only in that region.

**Alternatives considered:** (a) single-region only — rejected: contradicts S1 §6.7 and Gov/Enterprise tenant requirements; (b) per-tenant database everywhere — rejected: operationally infeasible at the cPanel/VPS baseline and unnecessary for the residency guarantee; (c) fully independent regional platforms — rejected: violates one-Core architecture (LG-06/LG-07).

**Trade-offs / consequences:** control-plane metadata must be explicitly minimized and documented; cross-region features (platform-wide analytics) must aggregate on anonymized/non-residency-bound data only; region migration becomes a governed, audited procedure; the cPanel/VPS baseline supports a single-region start with regions added as infrastructure permits — the model degrades gracefully to one region with zero schema change.

**Dependencies:** residency metadata schema, application-layer regional router, and per-region provisioning runbooks → Architecture phase (§26B).

## 2. Residency policy & metadata
- **Tenant residency policy:** region chosen at signup/provisioning from the platform's offered region catalog; recorded as immutable residency metadata (tenant_id → region_code, effective date, chosen-by, plan basis). Change only via the governed **Region Migration** procedure (§6).
- **Control plane (global, region-neutral, minimized):** tenant directory (id, name, region, status), subscription/entitlement state, routing metadata, platform user identities for platform staff. Explicitly documented in the **cross-border data-flow map** `[SD: S1 §6.7]`; contains no tenant business records, documents, or AI knowledge.

## 3. Regional routing & storage placement
Application-layer routing: every authenticated request resolves Tenant Context → residency metadata → Regional Data Home connection/storage scope. No client ever selects a region directly. Storage placement rules: business DB rows, uploaded files, generated documents/reports, media, AI vectors/embeddings/memory, logs containing tenant PII → tenant's region. Aggregated, anonymized platform metrics → control plane permitted.

## 4. Cross-region rules
- **Access:** cross-region tenant-data access is **denied by default**. A request served in Region A never reads Tenant data homed in Region B.
- **Transfers:** only via governed export/import with Tenant Owner request or documented legal basis, Super Admin approval, and full audit (what, why, source/destination regions, approver). Recorded on the data-flow map.
- **Administrative access:** platform staff access to tenant data follows residency (access is to the region's systems), requires recorded justification (AC-03), and is always audited with region attribution.

## 5. Backup, DR & failover
Backups of a Regional Data Home remain **in-region** by default; cross-region backup replication only where the tenant's policy/contract permits it (recorded per tenant). DR: in-region replica/restore is the default path; cross-region failover is offered only as an explicit, per-tenant opt-in (because it is itself a residency event) and is audited. RPO/RTO per plan defined at Architecture phase. Backup-aware deletion (F-04 §11) applies per region.

## 6. Region migration (governed procedure)
Trigger: Tenant Owner request or regulatory requirement. Steps: approval (Required-Approval class — affects tenant data boundary) → freeze window → verified export → import to target region → integrity verification → routing metadata switch → source-region data destruction per retention policy → audit record. Never silent; never partial.

## 7. Auditability, compliance & expansion
Every residency-relevant event (assignment, access, transfer, migration, backup replication, failover) carries region attribution in the audit fabric (F-04 §7). Compliance: model satisfies GDPR/DPDP data-localization postures and government/enterprise contractual residency guarantees (F-03 §6); consent and DPA records reference the tenant's region. **Future regional expansion:** adding a region = provision Regional Data Home + add to region catalog + update data-flow map — configuration and infrastructure only, no code fork, one Core preserved.
