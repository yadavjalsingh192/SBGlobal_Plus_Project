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
