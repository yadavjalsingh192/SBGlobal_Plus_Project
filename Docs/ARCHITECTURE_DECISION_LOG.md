# SBGlobal Plus — Architecture Decision Log (ADL)

Version: 1.0
Status: Active — Living Document
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 8 (Decision & Conflict-Resolution Principles), Appendix C

> **Role of this document.** Standing log of every non-trivial merge/split/rename/scope/architecture decision made under MI.md, per MI Part 8. Entries are append-only; a later entry may supersede an earlier one but never erases it (MI Part 8, P2/P4). This is the "Approved Project / Architecture Decisions" tier of the MI Part 2 Authority Order.

---

### ADL-2026-08-19-01

**Context:** First working session invoked with the "SBGlobal Plus Reusable Project Foundation Batch Instruction." Repository `yadavjalsingh192/SBGlobal_Plus_Project` (branch `main`) contains `Docs/MI.md` and `Docs/MP.md` at v2.0 (rebuilt and committed per commit `7194a74`), the Primary Source of Truth, and 9 supporting raw knowledge files — but **no Checkpoint Ledger, no Architecture Decision Log, and zero Foundation/Knowledge Base documents existed anywhere in the repository.** MI Part 13.3 gates Phase 3 (Project Foundation Construction) on the governing pair being "rebuilt, validated, and approved," and no prior checkpoint recorded that validation/approval gate as passed.

**Action:** Treated the user's batch instruction — explicitly scoping work to "the SBGlobal Plus Project Foundation work until all 31 Core Foundation documents are completed and certified" — as the Current Explicit User Instruction that satisfies the "approved" element of the Phase 3 gate (MI Part 2.1: Current Explicit User Instruction is always the highest-ranked authority). Did not additionally re-run a standalone Phase 2 validation pass on MI/MP v2.0 content itself, since MI/MP were not part of this invocation's declared scope and showed no internal inconsistency during the required read-through.

**Recommendation:** Proceed directly into Phase 3, Batch 1, under the rebuilt MI/MP v2.0, while flagging this gate-satisfaction reasoning explicitly (this entry) rather than silently assuming it.

**Why:** MI Part 2.1 Authority Order places a Current Explicit User Instruction above even the Primary Source of Truth; MI Part 12 reserves Blocking Conditions for cases that "cannot be resolved deterministically" — this one resolves deterministically by direct application of Part 2.1.

**Alternatives (rejected):** (a) Halt and ask the user to separately re-confirm MI/MP v2.0 validation before any Foundation content is produced — rejected as unnecessary process overhead given an unambiguous, on-point Current User Instruction. (b) Silently skip the gate without recording reasoning — rejected as a violation of MI Part 8 (non-trivial decisions must be logged, not made silently).

**Authority Cited:** MI Part 2.1 (Authority Order); MI Part 13.3 (Phase Boundary).
**Scope Impact:** Process/governance only — no Core Platform or Industry Suite content affected.

---

### ADL-2026-08-19-02

**Context:** The batch instruction requires identifying "the exact next unfinished Foundation documents" via "dependency-aware batches," but no prior batch plan, checkpoint, or explicit ordering of the 31-file Documentation Standard list (Primary Source §12) existed anywhere in the repository or in prior session memory.

**Action:** Selected **VISION.md, ARCHITECTURE.md, CORE-STANDARDS.md** as Foundation Batch 1.

**Recommendation:** These three are the only Tier-1 documents every one of the remaining 28 files structurally depends on: `VISION.md` establishes the permanent vision and Core Principles referenced by name from every other document; `ARCHITECTURE.md` establishes the Core Platform layering, product surfaces, and Industry Suite / Management System framework that every capability-specific document (Multi-Tenancy, Module Framework, AI/API Strategy, Security, Data, Integration, Deployment, etc.) instantiates; `CORE-STANDARDS.md` establishes the documentation header/versioning/lifecycle convention every one of the 31 files (including the three in this batch) must follow, and the Ownership Map that prevents the remaining 28 files from duplicating each other's authority.

**Why:** MI Part 8 P1 (Generality Over Specificity) and the batch rule's own "dependency-aware" instruction both favor building the shared foundation before any dependent, capability-specific document. README.md / INDEX.md / CHANGELOG.md (files 01–03) were deliberately deferred rather than batched first: they are index/summary documents that reference the *rest* of the set and are more accurately produced or finalized once meaningful content exists to index — producing them first would either be empty scaffolding or would need to be substantially rewritten once Batch 2+ lands, which is wasted work under MI Part 9.1 ("avoid repeating completed work").

**Alternatives (rejected):** (a) Follow the Primary Source §12 numeric order literally (README → INDEX → CHANGELOG → VISION → ...) — rejected per the reasoning above. (b) Batch all 9 Core-Platform-tier documents (Vision, Architecture, Core-Standards, Multi-Tenancy, Module-Framework, Security-Governance, AI-API-Strategy, Configuration-Metadata, Data-Architecture) together — rejected as too large for one verifiable, reviewable batch; deferred to Batches 2–3.

**Authority Cited:** MI Part 8 (P1); Batch Instruction §"BATCH RULE" (dependency-aware batching; do not guess when a plan is genuinely undeterminable — here it was determinable from architectural dependency, not guessed).
**Scope Impact:** Foundation/Knowledge Base document set — establishes Batch 1 of an anticipated ~9–11 batch sequence across the 31 files.

---

### ADL-2026-08-19-03

**Context:** The Primary Source of Truth (line 404, "Document Status") refers to the target 31-file set collectively as the "`SBGlobal_Plus_Knowledge_Base`" files but does not specify a literal repository folder path for them, and no such folder existed in the repository.

**Action:** Created the 31 Foundation documents under `Docs/SBGlobal_Plus_Knowledge_Base/` inside the existing repository structure, alongside the existing `Docs/MI.md`, `Docs/MP.md`, and `Docs/Raw knowledge files/`.

**Recommendation:** Retain this path for all remaining batches unless the user directs otherwise.

**Why:** Directly reuses the Primary Source's own name for the file set (traceable, not invented — MI Part 8 P5, Justified Assumption Rule), keeps the 31 files together and clearly distinguished from governance (`MI.md`/`MP.md`) and raw knowledge, and requires no change to any existing repository file (MI Part 11.2).

**Alternatives (rejected):** `Docs/Project Foundation/` — rejected as a locally-invented name with no direct textual support, when a directly-sourced name was available.

**Authority Cited:** MI Part 8 (P5); Primary Source of Truth, "Document Status" line (404).
**Scope Impact:** Repository structure — net-new folder only; no existing file modified.

---

### ADL-2026-08-19-04

**Context:** Checkpoint 001 recorded Foundation Batch 2 as recommended but not started, scoped to `MULTI-TENANCY.md`, `MODULE-FRAMEWORK.md`, `CONFIGURATION-METADATA.md`, "open for user confirmation or override before Batch 2 begins." The user's next message was the canonical Continue trigger (MI Appendix A: "Continue from checkpoint" and close variants), which per Appendix A "triggers the Resume Policy... from the last recorded checkpoint" without requiring the user to restate context already in the ledger. Separately, while sourcing this batch, both `Docs/Raw knowledge files/02_...Product_Specification_Requirement.md` and `.../07_...Enterprise_Default_Standards.md` were confirmed to contain Healthcare/LIS-concentrated examples (e.g., "Independent Patients," "Independent Doctors," a dedicated "LIS" setting-module entry, "Lab Websites"/"Lab Admin" terminology) consistent with the Healthcare/LIS concentration already noted in ADL-2026-08-19-01's session context.

**Action:** (a) Treated the Continue trigger itself as satisfying the checkpoint's own "confirmation or override" note and proceeded directly into Batch 2 under the recommended scope, without pausing for a separate confirmation round-trip. (b) Generalized every Healthcare/LIS-specific example encountered while drafting `MULTI-TENANCY.md`, `MODULE-FRAMEWORK.md`, and `CONFIGURATION-METADATA.md` into industry-neutral equivalents (e.g., "Independent Patients/Doctors" → "independent operational records/master data"; the raw "LIS" setting-module entry → "Industry Module Settings") before any Core Platform-tier statement was finalized, per the Industry-Neutrality Audit (MI Part 8, P6).

**Recommendation:** Adopt both as the standing pattern for all future batches: a bare Continue-family trigger resumes a checkpoint's own recommended Next Action without a separate confirmation message unless the checkpoint flagged a genuine open question (not merely "open for override"); and every batch sourced from the Healthcare/LIS-concentrated raw knowledge files must run the Industry-Neutrality generalization pass described here before Verification.

**Why:** MI Appendix A is explicit that a Continue-family trigger resumes "from the last recorded checkpoint" and instructs the session to "never ask the user to restate context already in the Checkpoint Ledger" — re-asking for confirmation of a Next Action the ledger already recommended would violate that instruction. The generalization pass is required directly by MI Part 5.1 (Single-Industry Knowledge Protection) and Part 8 P6 (Industry-Neutrality Audit), and was foreseeable given ADL-2026-08-19-01's own note that the supplied raw knowledge is Healthcare/LIS-concentrated.

**Alternatives (rejected):** (a) Pause after loading the checkpoint and ask the user to explicitly re-confirm Batch 2's scope before drafting anything — rejected as contrary to MI Appendix A's explicit instruction for Continue-family triggers. (b) Reproduce the raw knowledge's Healthcare/LIS examples verbatim in the Core-tier documents and flag them as "to be generalized later" — rejected because MI Part 10 (Quality Assurance gate) requires the Industry-Neutrality Audit to pass *before* publication, not after.

**Authority Cited:** MI Appendix A (Canonical Continuation Commands); MI Part 5.1 (Single-Industry Knowledge Protection); MI Part 8, P6 (Industry-Neutrality Audit); MI Part 9.3 (Resume Policy).
**Scope Impact:** Foundation/Knowledge Base document set — Batch 2 of the anticipated ~9–11 batch sequence across the 31 files (`MULTI-TENANCY.md`, `MODULE-FRAMEWORK.md`, `CONFIGURATION-METADATA.md`).

---

### ADL-2026-08-19-05

**Context:** Checkpoint 002 recorded Foundation Batch 3 as recommended but not started, scoped to `SECURITY-GOVERNANCE.md`, `AI-API-STRATEGY.md`, `DATA-ARCHITECTURE.md`, explicitly flagged "open for user confirmation or override before Batch 3 begins" — a stronger flag than Checkpoint 001's Batch 2 note, since the user's resume message this session was a literal Appendix A trigger phrase ("Continue from the latest verified... checkpoint") sent as a fresh top-level request rather than mid-session shorthand, and no session-level instruction had yet scoped work to a specific batch.

**Action:** Surfaced the recommended Batch 3 scope and the GitHub-handling question to the user as two explicit confirmation options before drafting anything, rather than applying ADL-2026-08-19-04's "bare Continue trigger resumes without re-confirmation" pattern automatically.

**Recommendation:** The user confirmed the recommended scope as-is ("Yes, proceed as recommended") and elected to supply a temporary repository-scoped PAT for the commit/push step. Proceeded to draft `SECURITY-GOVERNANCE.md` (10 of 31), `AI-API-STRATEGY.md` (11 of 31), and `DATA-ARCHITECTURE.md` (13 of 31) under that confirmed scope.

**Why:** MI Part 12 treats a missing required confirmation as a Blocking Condition when it "cannot be filled by a logged, justified assumption." Batch 3 is the first batch where the checkpoint's own open-question note was addressed to the user directly at the start of a new session (not mid-flow), and the batch also introduces a live credential-handling decision (GitHub PAT) that ADL-2026-08-19-04's precedent did not need to address for Batch 2. Both are genuine open questions, not merely restating context already in the ledger, so asking did not violate MI Appendix A.

**Alternatives (rejected):** (a) Apply ADL-2026-08-19-04's precedent uniformly and proceed directly into the recommended Batch 3 scope without asking — rejected because it would have also silently decided the GitHub-handling question, which the checkpoint ledger had no recorded answer for. (b) Ask only about GitHub handling and silently assume the batch scope — rejected as inconsistent given both were flagged together in Checkpoint 002's Next Action.

**Authority Cited:** MI Part 12 (Blocking Conditions); MI Part 9.3 (Resume Policy); ADL-2026-08-19-04 (distinguished, not overturned).
**Scope Impact:** Foundation/Knowledge Base document set — Batch 3 of the anticipated ~9–11 batch sequence across the 31 files (`SECURITY-GOVERNANCE.md`, `AI-API-STRATEGY.md`, `DATA-ARCHITECTURE.md`). Also governs GitHub credential handling for this session (§11.3/11.4 practice): the user-supplied PAT is used only as an in-memory auth header for the push command, never written to any file, git config, log, or the checkpoint.

---

### ADL-2026-08-19-06

**Context:** While drafting Batch 3, the AI Architecture Standards raw knowledge listed Core Platform-tier AI Agent lists that included Healthcare-specific personas (e.g., role-specific clinical agent names) alongside genuinely industry-neutral Platform Agents, consistent with the Healthcare/LIS concentration already noted in ADL-2026-08-19-01 and generalized once before in ADL-2026-08-19-04. Separately, the Database Architecture Standards raw knowledge's Integration section named a healthcare-specific interoperability data-exchange standard alongside industry-neutral integration mechanisms (REST API, Webhook, Import, Export, Queue, Scheduler).

**Action:** In `AI-API-STRATEGY.md` §7, retained only the industry-neutral Platform Agents (Knowledge, Workflow, Automation, Analytics, Notification, Integration, Support, Security) at Core Platform tier and generalized the Healthcare-specific agent personas into the pattern "each Industry Suite may define its own specialized AI Agents," cross-referencing that ownership outward rather than naming any single industry's personas at Core tier. In `DATA-ARCHITECTURE.md` §12, generalized the named healthcare interoperability standard into "industry-standard data-exchange formats" applicable per Industry Suite.

**Recommendation:** Continue applying the same generalization pattern established in ADL-2026-08-19-04 to every remaining batch sourced from the Healthcare/LIS-concentrated raw knowledge files, before Verification, not after.

**Why:** MI Part 5.1 (Single-Industry Knowledge Protection) and Part 8 P6 (Industry-Neutrality Audit) require this generalization before a statement is finalized as Core Platform-tier content; MI Part 10 requires the Industry-Neutrality Audit to pass before publication.

**Alternatives (rejected):** Reproduce the Healthcare-specific personas and the named interoperability standard verbatim in Core-tier sections with a "to be generalized later" flag — rejected for the same reason ADL-2026-08-19-04 rejected it: the QA gate must pass before, not after, publication.

**Authority Cited:** MI Part 5.1 (Single-Industry Knowledge Protection); MI Part 8, P6 (Industry-Neutrality Audit); MI Part 10 (Delivery Lifecycle); ADL-2026-08-19-04 (precedent applied again).
**Scope Impact:** Foundation/Knowledge Base document set — `AI-API-STRATEGY.md` §7, `DATA-ARCHITECTURE.md` §12 (Batch 3).

---

### ADL-2026-08-19-07

**Context:** Checkpoint 003 recommended Foundation Batch 4 as `AUTHENTICATION-AUTHORIZATION.md`, `COMPLIANCE-PRIVACY.md`, `INTEGRATION-FRAMEWORK.md`, flagged "open for user confirmation or override." The user, resuming with the canonical "Continue from the latest verified checkpoint" trigger, was asked to confirm scope and GitHub-handling per the ADL-2026-08-19-05 precedent (a genuine open question at a fresh-session start, not restated context); the user confirmed the recommended scope and elected to supply a temporary repository-scoped PAT pasted directly into the chat message. Separately, while sourcing this batch: (a) `02_...Product_Specification_Requirement.md` §35 scoped "HIPAA Readiness" explicitly to a "Healthcare & Diagnostics Vertical," distinct from the unscoped GDPR/DPDP/SOC 2/ISO 27001 items in the same list; (b) §27–§29 of the same file and the Database Architecture Standards raw knowledge's Integration section named healthcare-specific interoperability standards (HL7, FHIR, HIS, EMR, EHR, LIS, RIS, PACS) alongside industry-neutral integration mechanisms (REST API, Webhook, Import, Export, Queue, Scheduler), consistent with the Healthcare/LIS concentration already noted at ADL-2026-08-19-01 and generalized under the same pattern at ADL-2026-08-19-04/-06; (c) `01_...Master_Development_Instruction.md` §18 named a specific web-framework authentication implementation ("Laravel Authentication (Web)") alongside the industry-neutral, architecture-level method catalogue.

**Action:** (a) Proceeded to draft Batch 4 under the confirmed scope. (b) In `COMPLIANCE-PRIVACY.md` §3, preserved the raw knowledge's own "Healthcare & Diagnostics Vertical" scoping for HIPAA-readiness rather than promoting it to a Core Platform-tier default, and stated explicitly (§10) that each tenant's applicable regulatory alignments are determined by jurisdiction/context, never by industry. (c) In `INTEGRATION-FRAMEWORK.md` §3 and §7, retained only REST API, Webhook, Import, Export, Queue, and Scheduler at Core Platform tier and deferred the named healthcare interoperability standards to the Industry Suite layer, mirroring `DATA-ARCHITECTURE.md` §12's existing generalization. (d) Excluded the "Laravel Authentication (Web)" implementation detail from `AUTHENTICATION-AUTHORIZATION.md` entirely — not generalized, simply out of scope — since it names a specific technology-stack choice at the Historical/Legacy authority tier (MI Part 2.1, tier 8) and no other published Foundation document names a specific framework at Core Platform tier. (e) The user-supplied PAT is used only as an in-memory auth header for this session's commit/push step and is never written to any file, git config, log, checkpoint, or this decision log; the user was separately advised, given the token was pasted directly into a chat message rather than supplied through a secret-handling channel, to revoke/rotate it once this session's push is complete.

**Recommendation:** Adopt (b)–(d) as the standing pattern: a raw-knowledge item that is already explicitly scoped to one vertical (not merely concentrated in it) should have that scoping *preserved and stated*, not silently widened or silently dropped; a named industry-specific technical standard continues to follow the ADL-2026-08-19-04/-06 generalization pattern; and a named specific technology/framework choice is out-of-scope for Core Platform-tier architecture documents by default, deferred to `DEVELOPMENT-GUIDE.md` if it belongs anywhere in the 31-file set.

**Why:** MI Part 5.1 and Part 8 P6 (Industry-Neutrality Audit) govern (b)–(c); P1 (Generality Over Specificity) governs (d) — a hardcoded framework name is the specific case P1 requires generalizing away from, and unlike (b)/(c) there was no generalizable *pattern* worth retaining at Core tier, so exclusion (not generalization) was the correct action. MI Part 11.3/11.4 (credential handling) and the practice recorded at ADL-2026-08-19-05 govern (e); advising rotation reflects that a chat message is not a secret-handling channel, independent of how carefully this session itself avoids persisting the token.

**Alternatives (rejected):** (a) Widen HIPAA-readiness into an unscoped Core-tier compliance default — rejected as contrary to MI Part 5.1 and inconsistent with the raw knowledge's own explicit scoping. (b) Name a single interoperability standard at Core Platform tier for developer convenience — rejected for the same reason ADL-2026-08-19-06 rejected it. (c) Include "Laravel Authentication (Web)" with a caveat that it is "the current implementation" — rejected: no other Foundation document mixes a specific framework name into Core Platform-tier architecture content, and doing so here would create exactly the duplication/drift risk `CORE-STANDARDS.md` §8.4 (Single-Owning-Document Discipline) exists to prevent. (d) Silently use the pasted token without comment — rejected as inconsistent with giving the user complete, accurate information about a live credential's exposure.

**Authority Cited:** MI Part 5.1; MI Part 8, P1 and P6; MI Part 11.3–11.4; MI Appendix A; ADL-2026-08-19-04, -05, -06 (precedent applied and, for HIPAA-readiness scoping, distinguished rather than merely repeated).
**Scope Impact:** Foundation/Knowledge Base document set — Batch 4 of the anticipated ~9–11 batch sequence across the 31 files (`AUTHENTICATION-AUTHORIZATION.md`, `COMPLIANCE-PRIVACY.md`, `INTEGRATION-FRAMEWORK.md`). Also governs GitHub credential-handling practice for this session (extends §11.3/11.4 practice recorded at ADL-2026-08-19-05).

---
