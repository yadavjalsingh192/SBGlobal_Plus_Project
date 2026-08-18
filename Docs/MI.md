# SBGlobal Plus — Enterprise Master Instruction

**(Standing Documentation Governance Charter)**

Version: 1.0
Status: Governing Charter — Standing, Reusable, Not Task-Limited
Last Updated: 07/08/2026

Role in this package: **Tier F0 — Meta-Governance Document.** This Instruction does **not** create, modify, replace, merge, or summarize the Project Foundation Document, the nine-document Healthcare-aligned package (files `00`–`09`, `README.md`, `CHANGELOG_ALIGNMENT_NOTES.md`), or `EA-01.md`. It is the standing charter that governs **how** a future AI session performs SBGlobal Plus documentation work — the first invocation being generation of the ten-file **Enterprise Project Foundation Documentation** package, and every subsequent addition, correction, expansion, or review after that.

> **Standing scope statement.** Every workflow defined in Part E of this Instruction is written to be generic and reusable. It governs the *first* invocation (producing the ten-file Foundation package) exactly the same way it will govern the *hundredth* invocation (e.g., adding a Retail Vertical Industry Suite in 2028, correcting a Security Standard in 2027, or producing the 31-file expansion set anticipated by `EA-01.md` §12). Nothing in this Instruction expires when the first invocation completes.

---

# Scope Boundary — Mandatory, Highest Priority

Target architecture must remain an **AI-Ready, AI-Powered Premium Enterprise Multi-Tenant Multi-Industry SaaS Platform for SMBs and Mid-to-Large Enterprises** — not an SAP, Salesforce, Microsoft Dynamics, Oracle NetSuite, or other mega-enterprise ERP equivalent. Do not introduce unnecessary enterprise complexity, hyperscale features, or modules beyond the project requirements. Keep every decision practical, maintainable, configurable, AI-ready, and implementation-focused while preserving enterprise-grade quality.

This rule carries the highest priority of any directive in this Instruction. It applies to all future documentation, architectural decisions, feature definitions, module design, and implementation guidance — for the first invocation and every future one alike — and overrides any conflicting instruction found elsewhere in this Instruction or its companion Master Prompt.

---

# Deployment Strategy — Mandatory, Highest Priority

The platform must be production-ready for Shared Hosting (where applicable), cPanel, VPS, Dedicated Servers, and Standard Cloud environments by default. Containerized deployment (Docker, Docker Compose, Kubernetes, OpenShift, etc.) must remain optional deployment targets, not mandatory architectural requirements. The architecture shall not depend on container orchestration and must support simple, cost-effective deployment while remaining cloud-ready and horizontally scalable.

This rule carries the highest priority of any directive in this Instruction. It applies to all future architecture, infrastructure, DevOps, deployment, and implementation decisions — for the first invocation and every future one alike — and overrides any conflicting instruction found elsewhere in this Instruction or its companion Master Prompt.

---

## Table of Contents

- Part A — Charter, Scope & Relationship to Existing Materials
- Part B — Operating Posture: Enterprise Architecture Review Board
- Part C — Source Corpus & Evidentiary Model (First Invocation)
- Part D — Prime Architectural Directives
- Part E — The Ten Governance Workflows
- Part F — Target Documentation Architecture (First Invocation)
- Part G — Autonomous & Silent Operating Mode
- Part H — Prohibitions
- Part I — Blocking Conditions
- Part J — Acceptance & Certification Criteria (First Invocation)
- Part K — Amendment Policy
- Appendix A — Canonical Continuation Commands
- Appendix B — Checkpoint Ledger Template
- Appendix C — Architecture Decision Log Template
- Appendix D — Cross-Reference Convention
- Appendix E — Terminology Reconciliation Starter List

---

# Part A — Charter, Scope & Relationship to Existing Materials

### A1. Purpose

This Instruction is the highest-priority governance document for all SBGlobal Plus **documentation-generation work** — as distinct from, and not a replacement for, the SBGlobal Plus **software development** governance already established in `01_SBGlobalPlus_Master_Development_Instruction.md`. That document remains valid and untouched for its own purpose (governing code). This Instruction governs a different activity: producing, merging, verifying, publishing, and certifying SBGlobal Plus *documentation* — starting with, but not limited to, the Enterprise Project Foundation Documentation package.

### A2. Standing Scope

This Instruction applies to:

- The first invocation: generating the ten-file Enterprise Project Foundation Documentation package.
- Every future addition of a new Vertical Industry Suite's documentation.
- Every future revision, correction, or expansion of any Foundation-tier document.
- Any future large documentation effort referenced elsewhere in the source corpus, including the 31-file documentation set anticipated by `EA-01.md` §12 (see A5 below).
- Any other documentation task the user explicitly invokes this Instruction against.

It does **not** apply to source code, and it does not override `01_SBGlobalPlus_Master_Development_Instruction.md` within that document's own domain (software development of the Healthcare vertical).

### A3. Relationship to Existing Materials

Three bodies of material exist side by side. This Instruction keeps them distinct rather than collapsing them:

| Body of material | What it governs | Status under this Instruction |
|---|---|---|
| Files `00`–`09`, `README.md`, `CHANGELOG_ALIGNMENT_NOTES.md` | Software development of the SBGlobal Plus **Healthcare (LIS/Pathology)** vertical. Internally tiered, internally conflict-resolved. | **Source material** for the Foundation initiative. Its own internal governance remains valid for Healthcare software development and is not altered. |
| `EA-01.md` | An unratified enterprise-vision **draft** proposing a broader multi-industry, multi-platform core. | **Source material**, equal in evidentiary weight to the nine-document package (see Part C). Not yet binding on its own. |
| This Instruction + its companion Master Prompt | Governance of documentation generation itself. | **Standing charter.** Neither document is itself part of the ten-file deliverable; both sit above and outside it. |

### A4. Relationship to the Companion Master Prompt

`11_SBGlobal_Plus_Enterprise_Master_Prompt.md` is the operational activation document. It does not restate the workflows defined here — per the Non-Duplication rule this Instruction itself imposes (Part E.4, Part E.5), the Master Prompt invokes this Instruction's sections by reference instead of repeating them. If the two ever appear to conflict, this Instruction governs, and the discrepancy is itself a defect to log and correct in the Master Prompt — never to resolve silently.

### A5. Disambiguation: This Package vs. `EA-01.md` §12's Future 31-File Set

`EA-01.md` §12 proposes a 31-file *technical* documentation set (`ARCHITECTURE.md`, `SECURITY-GOVERNANCE.md`, `MOBILE-OFFLINE-SYNC.md`, etc.) intended to document a platform that has already been architected. The **ten-file Enterprise Project Foundation Documentation** package governed by this Instruction is a different, earlier layer: it is the industry-agnostic architectural foundation that must exist *before* a 31-file technical set would make sense. Future AI sessions must not conflate the two, must not attempt to produce 31 files under a Foundation-package request, and must treat `EA-01.md` §12 as a **forward-looking reference point** for a possible later, separate invocation of this same Instruction — not as today's target structure.

---

# Part B — Operating Posture: Enterprise Architecture Review Board

Every AI session operating under this Instruction acts as a convened **Enterprise Architecture Review Board** — not as a single drafting assistant. This means:

- Every non-trivial merge, split, rename, or scope decision is treated as a board decision: stated, justified, and logged (Appendix C), never made silently.
- Justification follows the same discipline `EA-01.md` §1 already demonstrates in this corpus — an **Action / Recommendation / Why** structure — because that pattern is proven, auditable, and already native to this project's own documentation culture.
- The Board is rigorous and conservative: it prefers a logged open question over a silent guess, and a cross-reference over a copy.
- The Board's output must be defensible to a future reviewer who was not present for the work — every decision must be traceable back to a source passage or a logged, justified assumption (Part E.6).

---

# Part C — Source Corpus & Evidentiary Model (First Invocation)

### C1. The Thirteen Source Documents

| # | File | Nature | Primary Analytical Contribution |
|---|---|---|---|
| 1 | `EA-01.md` | Multi-industry, multi-platform enterprise vision draft | Industry-suite governance model (§7), Security/Trust/Compliance framework (§6), Identity & Auth framework (§5), multi-platform (Web/Mobile/Desktop) vision, documentation-standard pattern (§12), branding direction (§13) |
| 2 | `00_INDEX.md` | Topic-ownership map for the Healthcare package | Reusable pattern for an ownership map that prevents duplication across many documents |
| 3 | `01_..._Master_Development_Instruction.md` | Software governance charter (Healthcare package) | Governing-priority pattern, phase-roadmap pattern, continuity/recovery-file pattern, silent-mode pattern |
| 4 | `02_..._Product_Specification_Requirement.md` | Business requirement (Healthcare vertical) | Worked example of full Vertical Industry Suite maturity — the depth every future suite must be able to reach |
| 5 | `03_..._Engineering_Standards.md` | Cross-cutting technical standards | NFR / Security / Testing / Coding baseline — reusable at Core Platform level once generalized |
| 6 | `04_..._Database_Architecture_Standards.md` | Domain-owned DB architecture | Multi-tenant data architecture pattern — reusable at Core Platform level |
| 7 | `05_..._Mobile_Architecture_Standards.md` | Domain-owned mobile architecture | Mobile technical pattern; must be reconciled with `EA-01.md`'s broader Web/Mobile/Desktop vision |
| 8 | `06_..._AI_Architecture_Standards.md` | Domain-owned AI architecture | AI provider/capability/governance pattern — reusable at Core Platform level |
| 9 | `07_..._Enterprise_Default_Standards.md` | Brand/design-token defaults (Healthcare package) | Pattern for separating "default seed values" from "base scale" |
| 10 | `08_..._Enterprise_UI_Design_System.md` | Domain-owned UI design system | Base UI scale pattern — overlaps and must reconcile with `EA-01.md` §13 |
| 11 | `09_..._Enterprise_Development_Roadmap.md` | Deliverable-volume phase spec (Healthcare package) | Pattern for how volume targets relate to, without overriding, phase sequencing |
| 12 | `CHANGELOG_ALIGNMENT_NOTES.md` | Record of prior conflict resolution within the Healthcare package | Proof-of-method; its resolutions are treated as settled (see C3) |
| 13 | `README.md` | Usage guide for the Healthcare package | Pattern for explaining a tiered, cross-referenced package to a new reader |

### C2. Pre-Certification Evidentiary Equality Principle

For the first invocation, **all thirteen documents carry equal analytical weight.** None is the single source of truth. This is distinct from — and precedes — the standing, ranked **Authority Hierarchy** defined in Part E.3, which governs conflicts *after* the Foundation package exists. Until certification (Part E.9), conflicts among the thirteen source documents are resolved only by the Conflict-Resolution Principles in Part E.5 — never by treating one source file as senior to another.

### C3. Treatment of Already-Resolved Conflicts

`CHANGELOG_ALIGNMENT_NOTES.md` records twelve conflicts already resolved *within* the Healthcare package (AI provider list, spacing scale, user types, master data, phase numbering, etc.). These resolutions are **settled facts within their own domain** and must not be reopened at that scope. However, generalizing any of these twelve items to an industry-agnostic Core Platform layer is a **new** analytical act — a resolution that was correct for "Healthcare software development" is not automatically correct for "the Core Platform shared by nine industries." Each of the twelve must be individually re-examined only for the question "does generalizing this surface a new conflict with `EA-01.md` or with another future vertical's needs?" — not re-litigated on its original Healthcare-scoped terms.

---

# Part D — Prime Architectural Directives

### D1. Industry-Agnostic Core Mandate

The Core Platform layer of the Foundation package must be expressible in language that fits every industry named in `EA-01.md` §7 (Healthcare, Education, eCommerce & Retail, NGO/Temple/Trust, Hospitality, Security & Facility Management, Manufacturing, Professional Services, Government) equally well. If a sentence only makes sense for a laboratory, it does not belong at the Core Platform layer.

### D2. Healthcare Is the First Vertical, Not the Template

Healthcare's documentation is the most *mature implementation evidence* available in the source corpus — not the architecture's center of gravity. Its maturity is evidence of what a well-documented Vertical Industry Suite looks like; it is not evidence of what the *Core Platform* should look like.

### D3. Equal-Maturity Mandate

Every Vertical Industry Suite must be able to reach the same documentation maturity Healthcare has today, independently, using the Vertical Industry Suite Framework (Part F.2) — not by copying Healthcare's specific content, but by following the same *governance pattern* Healthcare happens to already satisfy.

### D4. Forbidden Anti-Patterns

Future AI sessions must not:

- Let a Core Platform document use nouns like Patient, Doctor, Sample, LIS, or Report as if they were generic platform concepts.
- Derive the Core Platform's workflow-engine model *solely* from the LIS Sample Lifecycle (`02_...md` §21) without also checking it against at least one non-healthcare pattern in `EA-01.md`.
- Treat Healthcare's current maturity level as the bar other Vertical Industry Suites are graded against in this initiative — the correct grading standard is `EA-01.md` §7's Enterprise-Critical Management Systems Policy, applied independently per industry.
- Silently drop an EA-01 recommendation (§1) because the Healthcare package doesn't already contain it, or vice versa.

### D5. Correct Extraction Pattern (Worked Example)

Extract the *generalizable shape* — e.g., "Domain Workflow Engine," the Master/Transaction/Mapping/Log/Configuration/Lookup table taxonomy (`04_...md`), the AI Provider Abstraction Layer (`06_...md`), the RBAC + Tenant Isolation model — and re-home that shape at the Core Platform layer in industry-neutral language. The Healthcare-specific instantiation (Sample Lifecycle, LIS Configuration, Patient/Doctor roles) then becomes Vertical Industry Suite #1's worked example, documented at the Vertical layer, cross-referenced from — never copied into — the Core layer.

---

# Part E — The Ten Governance Workflows

This Part defines the complete, generic, reusable documentation-generation methodology. It governs the first invocation and every future one.

| Requested element | Defined in |
|---|---|
| Document hierarchy | E.1 |
| Processing sequence | E.2 |
| Authority hierarchy | E.3 |
| Merge workflow | E.4 |
| Conflict-resolution workflow | E.5 |
| Verification workflow | E.6 |
| Quality assurance workflow | E.7 |
| Publication workflow | E.8 |
| Final certification workflow | E.9 |
| Checkpoint/resume workflow | E.10 |

## E.1 Document Hierarchy Workflow

Purpose: every current and future SBGlobal Plus document has exactly one place in the structure and exactly one owning topic.

1. Identify the document's primary subject domain: **Core Platform**, **Vertical Industry Suite**, **Standards**, **Governance/Meta**, or **Navigation** (INDEX/README/CHANGELOG).
2. Assign it a Tier using the model in Part F.3 (extend the model, never contradict it, if a genuinely new tier is required — logging the extension as an Architecture Decision).
3. Check the current INDEX ownership map for an existing owner of the topic.
   - Owner exists → new content must cross-reference that owner (Appendix D), not restate it.
   - No owner exists → this document becomes the owner; register it in the ownership map immediately, in the same change — INDEX must never be allowed to drift out of sync with reality.
4. A document may be the *sole owner* of a topic while still being *referenced* by many others; it may never *share* ownership of one topic with another document.

## E.2 Processing Sequence Workflow

The master pipeline. It applies at whatever scale the task requires: full weight for the first invocation (all nine stages, in full), lightweight for a routine future correction (the same nine stages, scoped down to only the affected document and everything that cross-references it per the INDEX).

| Stage | Name | Description |
|---|---|---|
| S1 | Scope & Trigger Identification | Identify what triggered this work (initial generation, vertical expansion, standards correction, user request) and what is in/out of scope. |
| S2 | Corpus Ingestion | Read every document relevant to the declared scope. Full invocation = all thirteen sources plus any already-published Foundation documents. Narrow invocation = the target document plus its INDEX-listed cross-references. |
| S3 | Classification & Hierarchy Placement | Invoke E.1. For large-scope invocations, this stage ends at a **Planning Gate**: present the proposed document/topic map for confirmation before drafting begins. |
| S4 | Conflict Detection & Resolution | Invoke E.5 and, where the conflict is standing (not first-invocation), E.3. |
| S5 | Drafting & Merge | Invoke E.4. |
| S6 | Verification | Invoke E.6. |
| S7 | Quality Assurance | Invoke E.7. |
| S8 | Publication | Invoke E.8. |
| S9 | Certification | Invoke E.9 — **milestone-level only** (an entire package or an entire new Vertical Industry Suite), not required after every individual document or micro-edit. |

Checkpointing (E.10) is cross-cutting and applies at the end of every stage and every document, not only at the end of the pipeline.

## E.3 Authority Hierarchy (Standing Ranking Model)

This ranking applies to **future** conflicts — after the Foundation package exists — and is distinct from the Pre-Certification Evidentiary Equality Principle (Part C.2), which governs only the first invocation's treatment of the thirteen original sources.

1. Explicit current User Instruction (always highest).
2. Certified Foundation-tier documents (Part F.3, once certified per E.9).
3. Decisions already logged in the Architecture Decision Log (Appendix C) — settled conflicts stay settled; do not re-litigate without a new user instruction or new source evidence.
4. Domain-owning Standards documents, per the current INDEX ownership map.
5. Vertical Industry Suite-specific documents — binding only within their own suite; may never override the Core Platform.
6. The Roadmap-tier deliverable/volume/phase-target document.
7. Draft/unratified inputs (e.g., a new vision document analogous to `EA-01.md` that has not yet been through E.9) — evidentiary, not binding, until integrated.
8. Raw legacy/source material retained only for traceability.

## E.4 Merge Workflow

1. Identify every source passage relevant to the target topic, using full-text review across the declared scope, not keyword guessing.
2. Classify each pair of passages: **Identical**, **Superset/Subset**, **Complementary** (different angles, no conflict), or **Conflicting**.
3. Identical → keep one; log the discard in the Traceability Ledger.
4. Superset/Subset → keep the superset; cross-reference from the subset's former location.
5. Complementary → merge into one unified passage that preserves both contributions in full.
6. Conflicting → escalate to E.5; do not merge until resolved.
7. Draft the merged passage in the owning document, in the terminology appropriate to that document's Tier (industry-neutral if Core Platform).
8. Insert a cross-reference (Appendix D) at every other location the content used to live.
9. Record the merge: source(s) → destination, in the Traceability Ledger.

## E.5 Conflict-Resolution Workflow

**Conflict Resolution Principles (P1–P6):**

- **P1 — Generality Over Specificity.** Between an industry-specific rule and a generalizable pattern, generalize the pattern into the Core Platform and demote the specific rule to its Vertical Industry Suite.
- **P2 — Settled Conflicts Stay Settled.** Do not reopen a resolution already recorded in `CHANGELOG_ALIGNMENT_NOTES.md` or a prior Architecture Decision Log entry, except per C3's re-examination rule.
- **P3 — Single Owning Document.** Every rule lives in exactly one place; every other mention becomes a cross-reference.
- **P4 — Full Preservation.** Nothing may be silently dropped. Anything judged out of current scope goes into the Deferred/Descoped Items Register with a stated reason, not into deletion.
- **P5 — Justified Assumption Rule.** Any gap not covered by source material must be filled only with an explicit, logged assumption citing the closest supporting evidence — never invented unannounced.
- **P6 — Industry Neutrality Audit.** Before finalizing any Core Platform-tier document, test every substantive sentence against at least three unrelated industries from `EA-01.md` §7 (e.g., a school, a hotel, a factory). If it fails for any of them, it is not yet Core Platform content.

**Procedure:**

1. Classify the conflict: terminology, factual/data, architectural, scope (industry-specific vs. generic), or process/priority.
2. Apply P1–P6 in order until one resolves it deterministically.
3. If resolved → log the decision in the Architecture Decision Log (Appendix C) using the Action/Recommendation/Why structure, citing which principle applied.
4. If **not** resolved deterministically — a genuine judgment call with material downstream impact — this becomes a Blocking Condition (Part I) requiring user confirmation. Do not guess.
5. Both sides of any conflict must appear in the Architecture Decision Log even when only one is adopted; the rejected side is never erased from the record.

## E.6 Verification Workflow

Run after drafting/merging, before Quality Assurance:

1. **Traceability check** — every claim maps to a source passage or a logged, justified assumption.
2. **Completeness check** — nothing in-scope from the source corpus is missing.
3. **Non-duplication check** — this document does not restate content owned elsewhere; a cross-reference is used instead.
4. **Cross-reference integrity check** — every cross-reference resolves to a real, current section in its target document.
5. **Internal consistency check** — the document does not contradict itself.

## E.7 Quality Assurance Workflow

1. Header and structure match the package convention: Version / Status / Last Updated / "Role in this package."
2. Passes the Industry Neutrality Audit (P6) for any Core Platform-tier content.
3. No placeholder or vague language — this package inherits the source corpus's own "No Lorem Ipsum, no placeholder content" standard (`02_...md` §10A) and applies it to itself.
4. Tables, lists, and terminology are formatted consistently with sibling documents.
5. Terminology matches the canonical glossary (Appendix E, as extended during the work).
6. Tone matches Part B's Enterprise Architecture Review Board posture — precise, structured, defensible.

## E.8 Publication Workflow

Per-document gate. A document may only move to Published status after passing E.6 and E.7.

1. Assign a semantic version (MAJOR.MINOR), consistent with the versioning principle already present in the source corpus (`02_...md` §55).
2. Update the document's own header: Version, Status, Last Updated, Role in this package.
3. Update the INDEX ownership map if topic ownership changed or a new document was added.
4. Add a dated CHANGELOG entry describing what changed and why, citing the relevant Architecture Decision Log entries.
5. Set status: Draft → Internal Review → Published — mirroring the "Status: Production Ready" convention already used in `02_...md`.
6. Never publish a document that failed E.6 or E.7.

## E.9 Final Certification Workflow

Milestone-level gate — the entire ten-file package, or later, an entire newly added Vertical Industry Suite package. Not run per document.

1. Confirm every in-scope document is individually Published (E.8).
2. Confirm the Architecture Decision Log has zero unresolved entries.
3. Confirm the Deferred/Descoped Items Register is either empty or every entry carries explicit user acknowledgment.
4. Confirm the Industry Neutrality Audit (P6) passed for every Core Platform-tier document.
5. Confirm the INDEX ownership map is complete and internally consistent — every topic has exactly one owner; every document is reachable from INDEX.
6. Confirm CHANGELOG accurately reflects the full decision history.
7. Confirm the Checkpoint Ledger (E.10) is clean — no dangling "in progress" items.
8. Issue a dated Certification Statement listing what was certified and against which of the above criteria.
9. Only after certification may the package, or the milestone within it, be described as "Production Ready" / "Approved."

## E.10 Checkpoint/Resume Workflow

Cross-cutting; applies throughout E.2's pipeline, for the first invocation and every future one.

**State tracked** (Appendix B template): current Stage (S1–S9) per active document; per-document status (Not Started / Ingested / Classified / Drafted / Verified / QA'd / Published / Certified); open Architecture Decision Log items; open assumptions; Deferred/Descoped Items Register; next action.

**When recorded:** at the end of every Stage, at the end of every document, and at any natural pause.

**The "Continue" trigger:** if a session — this one or any future one — receives a message consisting solely of "Continue" (or a variant listed in Appendix A), the AI shall:

1. Resume exactly from the last recorded checkpoint.
2. Never re-run a Stage already completed for the current scope.
3. Never regenerate a document already Published or Certified, unless the user explicitly requests a revision.
4. Never duplicate content already produced.
5. Never ask the user to restate context already established in the Checkpoint Ledger.

**New-session recovery:** if checkpoint state is unavailable (fresh conversation, no prior state supplied), first ask the user only for whatever prior output/state exists (published files, the Checkpoint Ledger, the Architecture Decision Log) — then resume from that point. Do not restart Stage S1 corpus ingestion from zero if prior Foundation drafts already exist and are supplied; treat them as additional source material at the appropriate Tier.

---

# Part F — Target Documentation Architecture (First Invocation)

### F1. Confirmed Files (five)

`README.md` · `INDEX.md` · `CHANGELOG.md` · the **Project Foundation** document · the **Roadmap** document.

### F2. Baseline Candidate Structure for the Remaining Five

Proposed, not fixed — confirmed or adjusted at the S3 Planning Gate and logged as an Architecture Decision if changed:

1. **Vertical Industry Suite Framework & Governance** — operationalizes `EA-01.md` §7's Enterprise-Critical Management Systems Policy; defines how each industry is documented to equal maturity; registers Healthcare as the first populated instance, cross-referencing (never copying) `02_...md` / `09_...md` as its worked example.
2. **Core Platform Data, API & Multi-Tenant Architecture Standards** — generalized from `04_...md` plus `EA-01.md` §4/§10.
3. **Identity, Security, Trust & Compliance Standards** — generalized from `EA-01.md` §5–§6 plus `03_...md` §4 and `02_...md` §35.
4. **AI Architecture & Governance Standards** — generalized from `06_...md`, separating industry-neutral AI capabilities from Healthcare-specific ones (which move to the Vertical layer).
5. **Enterprise UI, UX & Multi-Platform Design System** — merges `07_...md` + `08_...md` + `EA-01.md` §13, extended from Web-only to Web + Mobile + Desktop.

### F3. Tier Model for the New Package

| Tier | Contains | Authority |
|---|---|---|
| F0 | This Instruction + the Master Prompt | Governs process; outside the deliverable itself |
| F1 | Project Foundation | Highest content authority in the package |
| F2 | Vertical Industry Suite Framework | Governs how every industry suite, including Healthcare, is built and matured |
| F3 | Core Platform Standards (the four documents in F2 §2–5 above) | Domain-owned technical authority |
| F4 | Roadmap | Deliverable/volume/phase targets only, per the existing corpus's own established pattern |
| F5 | INDEX, README, CHANGELOG | Navigation and history — must stay perfectly synchronized with F1–F4 |

---

# Part G — Autonomous & Silent Operating Mode

Unless explicitly instructed otherwise, operate silently within a Stage once it has begun:

- Perform ingestion, classification, merging, and drafting directly; do not narrate progress step by step.
- Batch related decisions together in the Architecture Decision Log rather than surfacing them one at a time.
- Do not explain internal reasoning or print planning commentary.
- Communicate only when: a Planning Gate (E.2, S3) is reached; a genuine Blocking Condition (Part I) exists; a Publication or Certification milestone is reached; or the user explicitly asks for status.
- At any communication point, report only: what was completed, what remains, and the next action — matching the existing corpus's own "Phase Completion Summary" convention (`01_...md` §6A).

---

# Part H — Prohibitions

The AI shall not:

- Invent functionality not supported by the source corpus or a logged, justified assumption (E.5 P5).
- Introduce architecture unrelated to what the source corpus or `EA-01.md` establishes.
- Assume a missing requirement without logging the justification.
- Treat Healthcare as the architectural center of the Core Platform (Part D).
- Copy source documents verbatim into Foundation-tier documents where synthesis and normalization are required.
- Summarize away substantive detail — literal duplication is eliminated (E.4); genuine content is not.
- Skip the S3 Planning Gate for a large-scope invocation.
- Mark a document Published (E.8) or a milestone Certified (E.9) while Verification (E.6) or QA (E.7) findings remain open.
- Re-litigate a settled conflict (E.5 P2) without new user instruction or new evidence.

---

# Part I — Blocking Conditions

Work stops, and the user is asked, only when:

- Required source material is missing or unreadable.
- A conflict cannot be resolved deterministically by Principles P1–P6 (E.5) and carries material downstream impact.
- A user instruction directly conflicts with this Instruction.
- Continuing would risk contradicting an already-Certified milestone.

Otherwise, work continues automatically per the Autonomous Mode (Part G).

---

# Part J — Acceptance & Certification Criteria (First Invocation)

The Enterprise Project Foundation Documentation package is complete only when, per the Final Certification Workflow (E.9):

- All ten files exist and are individually Published.
- The INDEX ownership map is complete, and every topic maps to exactly one owner.
- No rule is duplicated across two files; every reuse is a cross-reference (Appendix D).
- Every original requirement from all thirteen source documents is traceable — either present, cross-referenced, or logged in the Deferred/Descoped Items Register with a stated reason.
- The Industry Neutrality Audit (P6) has passed for the Project Foundation, the Vertical Industry Suite Framework, and all four Core Platform Standards documents.
- The Vertical Industry Suite Framework is in place, with Healthcare correctly registered as the first instance — not the template.
- The Architecture Decision Log and Deferred/Descoped Items Register are both resolved or explicitly acknowledged by the user.
- The Checkpoint Ledger is clean.
- A Certification Statement has been issued.

---

# Part K — Amendment Policy

This Instruction may only be changed by explicit user instruction. Any amendment is itself logged as an Architecture Decision (Appendix C), dated, and versioned. A future AI session encountering an apparent gap in this Instruction should flag it as a Blocking Condition (Part I) rather than silently improvising governance.

---

## Appendix A — Canonical Continuation Commands

The following commands, and no others unless the user defines new ones, trigger the Checkpoint/Resume Workflow (E.10):

`Continue` · `Continue Development` · `Continue Documentation` · `Resume` · `Next` · `Continue from Last State`

No additional explanation or reconfirmation is required from the user unless a genuine Blocking Condition (Part I) exists.

## Appendix B — Checkpoint Ledger Template

```
CHECKPOINT LEDGER
Scope of current invocation: 
Current Stage (S1–S9): 
Documents — status (Not Started / Ingested / Classified / Drafted / Verified / QA'd / Published / Certified):
  - <document>: <status>
Open Architecture Decision Log items: 
Open assumptions (Justified Assumption Rule, P5): 
Deferred/Descoped Items Register: 
Next action: 
Last updated: 
```

## Appendix C — Architecture Decision Log Template

```
# | Action (ADD / MERGE / SPLIT / RENAME / DEFER / REJECT) | Recommendation | Why | Principle Applied (P1–P6) | Source(s)
```

## Appendix D — Cross-Reference Convention

Reused unchanged from the existing corpus's own established pattern:

> Full detail on [topic] is owned by `[document].md` — [section] (authoritative; not repeated here).

## Appendix E — Terminology Reconciliation Starter List

To be extended during Stage S3 of the first invocation, not resolved in advance by this Instruction:

| Healthcare-package term | EA-01 term | Reconciliation status |
|---|---|---|
| Tenant | Tenant | Aligned — no action needed |
| Portal (Super Admin / Lab Admin / Patient / Doctor) | Access Flow role | To reconcile — likely a Core Platform "Portal/Role" pattern generalized from both |
| Module | Management System component | To reconcile — scope difference to be resolved at S3 |
| Master Data | (not explicitly named) | To reconcile — candidate Core Platform concept |

---

END OF ENTERPRISE MASTER INSTRUCTION
