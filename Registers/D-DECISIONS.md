# D-DECISIONS — Decision Register (Foundation Builds 1–2)
Seeded from MASTER_INSTRUCTION v2.5 §29 (conflict resolutions CR) plus this project's ARCHITECTURAL-COMPLETION log (AC) and residency decision (DR). All CR resolutions below are inherited ACTIVE governance decisions; both sides preserved in traceability, never deleted.

## Inherited conflict resolutions (CR)
| ID | Conflict | Resolution (ACTIVE) |
|---|---|---|
| CR-01 | Subscription tiers: 4-tier (S1) vs 5-tier with Pro (S2.2 §26) | Union adopted: Free / Starter / Pro / Premium / Enterprise; Free+Starter self-serve, others sales-assisted |
| CR-02 | Tagline conflict (S1 vs S2.7) | RESOLVED — USER-DIRECTED: "One Intelligent Platform. Every Industry. Infinite Possibilities."; both corpus taglines preserved as historical |
| CR-03 | Industry list differences (S1 §7 vs S2.2 §4 vs S2.6) | Union adopted — 9-industry catalog ACTIVE (F-00 §5) |
| CR-04 | Phase numbering 01-21B vs Roadmap 01-14 | Both preserved as knowledge; dependency-driven phase governance ACTIVE; Roadmap = volume targets only |
| CR-05 | "Healthcare is flagship" vs Vision | Vision prevails; Healthcare depth preserved, flagship posture retired (LG-03) |
| CR-06 | One common tenant application vs multiple | Superseded by Application Surface Model + Reusable Industry Experiences (LG-01/LG-02) |
| CR-07 | S1 dangling 31-file reference; v1.0/v1.1 mismatch | RESOLVED — source hygiene recorded; S1 preserved unmodified; LG-09 retires fixed file counts |
| CR-08 | Website roadmap Phases 1-3 vs development phases | Different scopes; both preserved, cross-referenced, non-competing |

## Build 1 ARCHITECTURAL-COMPLETION log (AC) — §35 label, never presented as SOURCE-DERIVED
| ID | Location | Completion | Rationale / dependencies |
|---|---|---|---|
| AC-01 | F-01 §5 BR-SUB-04 | Downgrade guard rule | Entitlement-chain integrity on plan change; no silent data loss. Depends: plan limit model |
| AC-02 | F-02 W-04 | Idempotent, resumable tenant provisioning | Prevents half-visible tenants; standard SaaS provisioning safety |
| AC-03 | F-03 §4 | Super Admin tenant-business-data access requires recorded justification | Zero-trust + privacy-first posture applied to platform operators |
| AC-04 | F-03 §6 BR-SEC-01 | Erasure vs mandatory-retention reconciliation (pseudonymize + audit skeleton) | GDPR/DPDP erasure vs audit-preservation conflict needs a deterministic rule |
| AC-05 | F-04 §5 | Financial transactions immutable post-approval; corrections via reversal | Audit/compliance integrity; applies platform-wide |
| AC-06 | F-07 §3.5 | Offline-first POS Desktop named primary Industry Desktop candidate (RTL) | Industry-appropriate application of the optional Industry Desktop capability |
| AC-07 | F-07 §2 | Education Suite operational specification (workflows, rules, masters) | Source names suite + MS list only; §9 standard requires operational depth. No Healthcare content copied |
| AC-08 | F-07 §3 | eCommerce/Retail Suite operational specification | idem |
| AC-09 | F-08 §1 | Hospitality Suite operational specification | idem |
| AC-10 | F-08 §2 | Manufacturing Suite operational specification | idem |
| AC-11 | F-08 §3 | Professional Services Suite operational specification | idem |
| AC-12 | F-09 §1 | Government & Public Sector Suite operational specification | idem |
| AC-13 | F-09 §2 | NGO/Temple/Trust Suite operational specification | idem |
| AC-14 | F-09 §3 | Security & Facility Management Suite operational specification | idem |

## Build 2 additions (31-08-2026 – 02-09-2026)
| ID | Location | Decision / Completion | Rationale · Trade-offs · Dependencies |
|---|---|---|---|
| DR-01 | F-11 | Regional Data Home residency model (one Core, one control plane, N regional data homes; tenant→one region; cross-region denied by default; governed migration) | USER-DIRECTED resolution of RR-02. Alternatives (single-region only / per-tenant DB everywhere / regional platform forks) rejected — see F-11 §1. Consequences: minimized control plane, region-attributed audit, graceful single-region degradation. Depends: residency schema + regional router (Architecture phase) |
| AC-15 | F-10 | Desktop Foundation completed; implementation framework/local-DB/packaging pipeline explicitly deferred; Desktop Architecture Standards named as Architecture-phase deliverable | USER-DIRECTED resolution of RR-01. Selecting a desktop technology at Foundation would be invention (no corpus basis); all Foundation-level dimensions (surfaces, auth, RBAC/ABAC, config, offline/sync, security, testing) are specified |
| AC-16 | F-12 | Remaining §9-standard dimensions completed for all 9 suites (docs/templates, notifications, KPIs, events, integrations, compliance, entitlements, dependencies, MS modules) | Equal-depth requirement (LG-04); per-suite content industry-specific; zero Healthcare copying (pattern-reuse note recorded for IWM) |
| AC-17 | F-13 | FF-01/FF-02 depth completion: HLT-HMS/RIS/PMS/CMS specified at Foundation depth; EDU-CTM, RTL-RSM, MFG-IWM, PSV-SDM brought to sibling depth; NGO-DMS review closed | Resolves the depth findings that revoked certification at CP-F1-003. Healthcare depth anchored to source-named systems `[SD]`, operational detail `[AC]`; non-Healthcare content industry-specific, zero Healthcare copying (LG-03). Depends: per-suite re-evaluation + dual re-audit + traceability extension before any certification decision |

Legacy Register LG-01..LG-14 verified absent from ACTIVE architecture in this package (see NO_LOSS_AUDIT §3).
