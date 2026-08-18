# SBGlobal Plus — Master Instruction (MI)

**(Permanent Governance Charter for the SBGlobal Plus Platform)**

Version: 2.0
Status: Governing Charter — Standing, Reusable, Not Task-Limited
Last Updated: 2026-08-18
Supersedes: MI v1.0 (documentation-generation charter)

> **Role of this document.** `Docs/MI.md` is the permanent governance charter for all SBGlobal Plus work. It defines *who has authority*, *what the platform permanently is*, and *how* any future AI session (or human contributor) must plan, decide, build, verify, and record work. It is activated operationally by its companion `Docs/MP.md` (Master Prompt). This charter is standing and reusable: it governs the very next invocation exactly as it will govern the hundredth, whether that invocation rebuilds a document, constructs the Project Foundation, adds an Industry Suite, or corrects a standard.

---

# PART 1 — PERMANENT PROJECT VISION (NON-NEGOTIABLE)

The permanent, governing vision of SBGlobal Plus is:

> **SBGlobal Plus is an API-First, AI-Ready, AI-Powered, Multi-Tenant, Multi-Industry Enterprise SaaS Platform** — built on **one shared, industry-neutral Core Platform**, serving **multiple equal Industry Suites**, each composed of **independently expandable Enterprise Management Systems**.

This vision is permanent. No supporting document, raw knowledge file, industry-specific artifact, roadmap, or prior governance version may replace, weaken, narrow, or redefine it. Every governance decision, architecture rule, and future deliverable must be consistent with it.

### 1.1 Vision Guardrails

- **API-First** — every business capability is exposed through governed, versioned, tenant-aware, permission-aware APIs and events. Business logic is never trapped inside a frontend.
- **AI-Ready** — the architecture is structured so AI can be added to any capability without re-architecture: provider-agnostic, model-agnostic, context-aware, permission-aware, auditable.
- **AI-Powered** — AI is a first-class Core Platform capability, not a bolt-on, available to assist, automate, analyze, recommend, search, and support decisions across the platform.
- **Multi-Tenant** — one shared Core Platform serves many isolated tenants; there is never a separate platform per industry or per tenant.
- **Multi-Industry** — the Core Platform is industry-neutral; every industry is an equal architectural peer. No industry is primary, first, flagship, default, reference, template, benchmark, parent, or dominant.

### 1.2 Scope Posture (Retained from prior governance)

The target architecture is a **Premium Enterprise Multi-Tenant, Multi-Industry SaaS Platform for SMBs and Mid-to-Large Enterprises** — not an SAP / Salesforce / Microsoft Dynamics / Oracle NetSuite mega-ERP equivalent. Do not introduce unnecessary enterprise complexity, hyperscale features, or modules beyond project requirements. Keep every decision practical, maintainable, configurable, AI-ready, and implementation-focused while preserving enterprise-grade quality. This posture supports, and never contradicts, the permanent vision above.

### 1.3 Deployment Posture (Retained from prior governance)

The platform must be production-ready by default for Shared Hosting (where applicable), cPanel, VPS, Dedicated Servers, and Standard Cloud environments. Containerized deployment (Docker, Compose, Kubernetes, OpenShift) remains an *optional* target, never a mandatory architectural requirement. The architecture must not depend on container orchestration, must remain cloud-ready and horizontally scalable, and must support simple, cost-effective deployment.

---

# PART 2 — AUTHORITY MODEL

### 2.1 Authority Order (Governing Hierarchy)

When any two inputs conflict, the higher-ranked source governs. **Conflicts are never resolved by silent merge.**

1. **Current Explicit User Instruction** — always highest.
2. **Primary Source of Truth** — `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` (see Part 3).
3. **Approved Project / Architecture Decisions** — entries in the Architecture Decision Log that a user has approved.
4. **Existing Certified Governance** — this MI, its MP, and any Foundation-tier document that has passed certification.
5. **Supporting Knowledge** — general raw knowledge files providing evidence and detail.
6. **Specialized Standards** — engineering, database, mobile, AI, UI, and default standards.
7. **Industry-Specific Knowledge** — material belonging to a single industry.
8. **Historical / Legacy Knowledge** — retained only for traceability.

### 2.2 Conflict Rule

When sources conflict:

- Identify and classify the conflict (terminology, factual/data, architectural, scope, or process/priority).
- Resolve it deterministically by applying this authority order and the Conflict-Resolution Principles (Part 8).
- Record the decision — including the rejected alternative — in the Architecture Decision Log.
- If it cannot be resolved deterministically and has material downstream impact, it becomes a **Blocking Condition** (Part 12): stop and obtain user confirmation. Never guess, and never silently merge conflicting sources.

---

# PART 3 — PRIMARY SOURCE OF TRUTH

Inside `Docs/Raw knowledge files/`, the highest product and enterprise-architecture authority is:

> **`Master Enterprise Architecture & Product Requirements Source.md`**

It is the **Primary Source of Truth**. It governs the product and enterprise-architecture vision, including: Product Vision · Product Scope · Platform Scope · Enterprise Architecture · API direction · AI direction · Multi-Tenant architecture · Multi-Industry architecture · Industry Suite model · Management System philosophy · Super Admin philosophy · Tenant philosophy · Configuration philosophy · Product surfaces · Security direction · Business requirements · Project Foundation direction.

- No supporting document may silently override the Primary Source of Truth.
- Supporting documents may supply *evidence and detail* under it, never *replace* it.
- Only a Current Explicit User Instruction outranks it.

---

# PART 4 — RAW KNOWLEDGE RULE

All files under `Docs/Raw knowledge files/` are **knowledge sources**. They may contain architecture, product requirements, engineering / database / mobile / AI / UI / development standards, roadmap information, industry-specific knowledge, and historical material.

- They **provide knowledge** to the project.
- They **do not automatically define** the project identity.
- **Document size, quantity, maturity, industry concentration, or implementation depth must never determine architectural authority.** A large, mature, single-industry document does not outrank the Primary Source of Truth or this charter.

---

# PART 5 — MULTI-INDUSTRY PROTECTION

### 5.1 Single-Industry Knowledge Protection

The supplied raw knowledge may be heavily concentrated in one industry (e.g., Healthcare / LIS). Even if almost all supplied knowledge belongs to a single industry, **SBGlobal Plus must remain a Multi-Industry platform.** The concentrated industry's knowledge must never be allowed to redefine the platform.

No industry may be made **primary, first, flagship, default, reference, template, benchmark, parent, or dominant.** All industries are equal architectural peers. This rule applies identically to every current and future industry.

### 5.2 Correct Handling of Industry-Rich Knowledge

- Extract the *generalizable shape* of an industry pattern (e.g., a domain workflow engine, a master/transaction/mapping/log/configuration/lookup data taxonomy, an AI provider abstraction, an RBAC + tenant-isolation model) and re-home it at the **Core Platform** layer in industry-neutral language.
- Keep the industry-specific instantiation inside that industry's Industry Suite as a worked example — cross-referenced from, never copied into, the Core layer.
- One industry's Management Systems, AI implementation, or regulatory model must never become the universal architecture.

---

# PART 6 — CORE ARCHITECTURE PRINCIPLES

### 6.1 Core Platform Principle

The permanent architecture layering is:

```
One Shared Enterprise Core Platform (industry-neutral)
        ↓
Multiple Equal Industry Suites
        ↓
Industry-Specific Management Systems
        ↓
Modules / Workflows / Data / AI / Automation / Integrations
        ↓
Tenant-Specific Configuration
```

- The **Core Platform** is industry-neutral and shared by all tenants and all industries.
- **Industry Suites** contain industry-specific business capabilities and are equal peers.
- **Management Systems** represent major operational business domains within an Industry Suite.
- Any capability reusable across industries — Identity & Access, Workflow Engine, Notifications, Document Management, Reporting, AI Services, Audit, Configuration, Metadata, APIs, Integration, Automation, Analytics, Billing, and similar shared services — **resides in the Core Platform** and is consumed by Industry Suites via configuration, metadata, APIs, events, plugins, or workflows, never reimplemented per industry.
- Do **not** create separate platform architectures per industry.

### 6.2 Management System Expansion Principle

Every Industry Suite must be able to **independently expand**, using the same governance framework, without altering the Core Platform:

Enterprise-Critical Management Systems · Optional Management Systems · Modules · Sub-Modules · Workflows · Business Rules · Master Data · Transactions · Reports · Analytics · AI · Automation · Integrations · Security · Compliance · Lifecycle Management · Plugins · Extensions.

- Each Industry Suite defines its own **Enterprise-Critical Management Systems** — the minimum complete operational capability for that industry.
- Additional capabilities are implemented as **optional, modular, configurable, extensible, or plugin-based** Management Systems within the Industry Suite, without affecting the Core Platform architecture.
- No industry's Management Systems become the template for another's. Every industry uses the same framework while defining its own business domains.

### 6.3 API-First Principle

API-First is a permanent architecture principle. Governance must cover: API-first business capabilities · API-first domain exposure · governed APIs · versioning · authentication · authorization · tenant-aware APIs · permission-aware APIs · rate limiting · quotas · API security · Webhooks · Events · integrations · API lifecycle · API documentation · API observability · API auditing.

Business logic must not be trapped inside a frontend. The architecture supports:

```
Domain Capability → Business Service → API / Event →
Web / Mobile / Desktop / Industry Systems / Integrations / AI
```

Web, Mobile, Desktop, AI, and integrations consume shared business capabilities **without duplicating business logic.**

### 6.4 AI-Ready + AI-Powered Principle

AI is a first-class Core Platform capability. Governance must cover: AI-Ready architecture · AI-Powered architecture · AI extensibility · provider-agnostic architecture · model-agnostic architecture · tenant awareness · permission awareness · context awareness · auditability · governance · API accessibility · configuration.

AI may support: assistance · automation · workflow intelligence · analytics · recommendations · search · decision support · operational intelligence · enterprise knowledge · agentic workflows. Industry-specific AI may exist inside an Industry Suite, but one industry's AI implementation must never automatically become the universal AI architecture.

### 6.5 Multi-Tenant Principle

Multi-Tenant architecture is first-class. Governance must cover: Tenant Isolation · Tenant Provisioning · Tenant Lifecycle · Tenant Configuration · Tenant Branding · Tenant Domains · Tenant Applications · Tenant Modules · Subscription · Billing · Licensing · Tenant AI Providers · Tenant Integrations · Tenant Security Policies · Users · Devices · Authorization · Synchronization · Data Governance · Localization.

The shared Core Platform serves multiple tenants. Do not create separate platform architectures per industry or per tenant. Clients never access protected business resources directly — the platform is **server-authoritative**: without successful authentication, authorization, tenant validation, license validation, and server verification, protected resources are not served.

### 6.6 Configuration / Metadata-First Principle

Preserve the configuration-first philosophy:

```
Configuration → Metadata → Templates → Rules → Policies → Plugins →
Automation → AI Assistance → Validation → Authorization →
Business Rules → Platform Access
```

Prefer configuration and extensibility over unnecessary source-code changes. This principle applies across all industries.

---

# PART 7 — PRODUCT SURFACE & ADMINISTRATIVE GOVERNANCE

### 7.1 Product Surfaces (Kept Conceptually Distinct)

The following surfaces must remain conceptually distinct and must never be collapsed into a single generic "application":

SBGlobal Plus Corporate Website · Tenant Website · Tenant Application · Super Admin / Platform Administration · Industry Management Systems · Web Application · Mobile Application · Windows Desktop Application · API Platform · Webhooks · Developer / API Documentation · AI Platform.

### 7.2 Super Admin vs. Tenant Admin

Two authority domains are kept separate and must never be confused:

- **Super Admin** — platform-level governance: Platform · Marketplace · Subscription · Branding Standards · Security Policies · Tenant Lifecycle · Module Ecosystem · AI Ecosystem · API Ecosystem · Deployment Policies · Identity · Authentication/Authorization Policies · License · Device Management.
- **Tenant Admin** — tenant-level administration: Branding · Domains · Website · CMS · Dashboard · Mobile & Desktop Applications · Themes · Business Modules · API Key Integrations · AI Provider Keys · Third-Party Keys · Automation · Notifications · Workflows · Reports · Desktop Settings & Auto-Updates.

### 7.3 Security and Compliance

The Core Platform's security and compliance direction is set by the Primary Source of Truth and is **industry-neutral**. Industry-specific regulatory requirements may exist inside an Industry Suite, but no single industry's regulatory architecture may redefine the Core Platform. Core security concerns include (non-exhaustive): centralized secrets & key management with per-tenant key isolation, API threat protection (rate limiting, gateway, WAF, DDoS/bot protection), and data residency & sovereignty controls where tenants require them.

---

# PART 8 — DECISION & CONFLICT-RESOLUTION PRINCIPLES

All non-trivial merge, split, rename, scope, or architecture decisions are **Review-Board decisions**: stated, justified with an **Action / Recommendation / Why** structure, and logged in the Architecture Decision Log — never made silently.

**Conflict-Resolution Principles (P1–P6):**

- **P1 — Generality Over Specificity.** Between an industry-specific rule and a generalizable pattern, generalize the pattern into the Core Platform and demote the specific rule to its Industry Suite.
- **P2 — Settled Conflicts Stay Settled.** Do not reopen a resolution already recorded in an approved Architecture Decision Log entry, except when generalizing it to a new scope surfaces a new conflict.
- **P3 — Single Owning Document.** Every rule lives in exactly one place; every other mention is a cross-reference.
- **P4 — Full Preservation (No Silent Loss).** Nothing valid is silently dropped. Anything out of current scope goes into the Deferred / Descoped Register with a stated reason.
- **P5 — Justified Assumption Rule.** Any gap not covered by source material is filled only with an explicit, logged assumption citing the closest supporting evidence — never invented unannounced.
- **P6 — Industry-Neutrality Audit.** Before finalizing any Core Platform-tier content, test every substantive statement against at least three unrelated industries (e.g., a hospital, a school, a factory). If it fails for any, it is not yet Core Platform content.

**No Silent Loss — Removal Classification.** If an existing rule is removed during any rebuild or revision, it must be classified as exactly one of: **Deprecated · Superseded · Duplicate · Contradictory · Historical · Implementation-Specific · Deferred** — and the classification recorded.

---

# PART 9 — CONTINUATION GOVERNANCE (CONTINUE · CHECKPOINT · RESUME)

This charter must allow work to continue safely across many AI sessions without repeating or overwriting valid work.

### 9.1 Continue Policy

Every future session must be able to:

1. inspect the existing Project Foundation state;
2. inspect the last completed task;
3. inspect the current checkpoint;
4. verify previous outputs;
5. identify incomplete work;
6. identify the next valid task;
7. continue from the exact last verified state;
8. avoid repeating completed work;
9. avoid overwriting existing valid work;
10. record the new checkpoint before ending.

**Never restart the Project Foundation from zero when a verified checkpoint already exists.**

### 9.2 Checkpoint Policy

A checkpoint must preserve enough information to resume work safely, including as applicable: Current Phase · Current Task · Completed Tasks · In-Progress Task · Remaining Tasks · Files Created/Modified · Architecture Decisions · Open Issues · Dependencies · Validation Status · GitHub Branch · Last Commit · Next Action · Blocking Conditions. The checkpoint must be recoverable by a future AI session (see Appendix B template).

### 9.3 Resume Policy

To resume, a session must:

```
Load Governance (MI + MP) → Load Primary Source → Inspect Repository →
Inspect Current State → Read Latest Checkpoint → Verify Existing Work →
Identify Exact Resume Point → Continue → Validate → Update Checkpoint
```

Do not repeat already-completed work unless verification proves it invalid.

### 9.4 New-Session Recovery

If checkpoint state is unavailable (a fresh conversation with no prior state supplied), first ask the user only for whatever prior output/state exists (published files, the Checkpoint Ledger, the Architecture Decision Log), then resume from that point. Do not re-ingest the full corpus from zero if prior work is supplied; treat it as source material at its appropriate authority tier.

---

# PART 10 — DELIVERY LIFECYCLE (VERIFY · QA · PUBLISH · CERTIFY)

Every deliverable produced under this charter passes through these gates in order. They scale: full weight for a large invocation (e.g., building the Project Foundation), lightweight for a routine correction (the affected item plus everything cross-referencing it).

- **Verification** — traceability (every claim maps to a source or a logged assumption), completeness, non-duplication, cross-reference integrity, internal consistency.
- **Quality Assurance** — header/structure convention, Industry-Neutrality Audit (P6) for Core content, no placeholder/filler content, consistent formatting and terminology, defensible Review-Board tone.
- **Publication** — assign a semantic version, update the item header (Version / Status / Last Updated / Role), update the ownership/index map if ownership changed, add a dated change entry citing decision-log entries. Never publish something that failed Verification or QA.
- **Certification** — milestone-level only (a full package or a full new Industry Suite): confirm every in-scope item is Published, the decision log has zero unresolved entries, the Deferred/Descoped Register is empty or acknowledged, the Industry-Neutrality Audit passed for all Core content, the index is consistent, and the checkpoint is clean. Only then may the milestone be called "Production Ready" / "Approved."

---

# PART 11 — GITHUB & TRACEABILITY GOVERNANCE

### 11.1 Repository

Repository: `yadavjalsingh192/SBGlobal_Plus_Project` · Default branch: `main`. Use the existing repository structure. Do not create duplicate Master Instruction or Master Prompt files. The final active governance pair remains exactly `Docs/MI.md` and `Docs/MP.md`.

### 11.2 Modification Scope Discipline

For any given invocation, modify only the files in that invocation's declared scope. In particular: **do not modify, delete, or rename Raw Knowledge files, and do not modify unrelated repository files.** If an additional file change becomes genuinely necessary, document the reason before making it.

### 11.3 Commit Governance

Commit only the intended, in-scope changes unless explicitly required otherwise. Use clear, dated, descriptive commit messages. **Never claim a commit, push, or PR unless it actually succeeded.**

### 11.4 Source Traceability

Important governance decisions must be traceable:

```
Primary Source → Architecture Rule → MI.md → MP.md → Future Project Foundation
```

Supporting documents may provide evidence but must not silently override the Primary Source.

---

# PART 12 — BLOCKING CONDITIONS

Stop and obtain user confirmation (do not guess) when:

- A conflict between sources cannot be resolved deterministically and has material downstream impact.
- A required input, decision, or approval is missing and cannot be filled by a logged, justified assumption.
- An action would fall outside the declared scope of the current invocation (e.g., beginning Project Foundation construction during a governance-rebuild phase).
- Repository state is inconsistent with the last recorded checkpoint in a way that risks overwriting valid work.

---

# PART 13 — PHASE BOUNDARY & PROJECT FOUNDATION

### 13.1 This Charter Is Not Implementation

This MI (and its MP) are the **governance foundation** used *later* to construct the SBGlobal Plus Project Foundation. Rebuilding or holding this governance is never, by itself, license to build the platform.

### 13.2 Do Not Implement During a Governance Phase

During any phase whose scope is governance (such as rebuilding MI/MP), the AI shall **not**: build application code · create databases · implement APIs · build UI · build mobile apps · build desktop apps · create infrastructure · implement Industry Management Systems · create business modules · implement AI services · implement tenant services · start deployment engineering · start application development.

### 13.3 Future Lifecycle

```
Phase 1  MI.md + MP.md Complete Rebuild
   ↓
Phase 2  Validation + GitHub Commit
   ↓
Phase 3  Project Foundation Construction  (uses the rebuilt MI + MP)
   ↓
Phase 4+ Continue / Checkpoint / Resume
```

The Project Foundation phase begins only after the governing pair is rebuilt, validated, and approved — and is executed by invoking the rebuilt MI/MP under the Continue / Checkpoint / Resume policy.

---

# PART 14 — DOCUMENTATION QUALITY & AMENDMENT

### 14.1 Quality Bar

MI and MP must be: complete · internally consistent · mutually consistent · reusable · clear · implementation-governance ready · traceable · versionable · extensible. They must not be mere summaries, blind copies of prior versions, or unnecessarily duplicated.

### 14.2 Amendment Policy

This charter is amended only by a Current Explicit User Instruction or an approved Architecture Decision. Every amendment bumps the version, records the change with rationale, and preserves the removed content's classification per Part 8. MP is updated in lockstep so the pair never drifts apart.

---

# APPENDIX A — Canonical Continuation Commands

A message consisting solely of any of the following triggers the Resume Policy (Part 9.3) from the last recorded checkpoint: `Continue` · `Resume` · `Proceed` · `Continue from checkpoint` · `Resume from last checkpoint`. On such a trigger: resume from the last checkpoint; never restart from zero; never regenerate Published/Certified work; never duplicate prior output; never ask the user to restate context already in the Checkpoint Ledger.

# APPENDIX B — Checkpoint Ledger Template

```
Checkpoint ID:        <sequential id / timestamp>
Current Phase:        <e.g., Phase 3 — Project Foundation Construction>
Current Task:         <task name>
Completed Tasks:      <list>
In-Progress Task:     <task + % / stage>
Remaining Tasks:      <ordered list>
Files Created/Modified: <paths>
Architecture Decisions: <ADL entry ids>
Open Issues:          <list>
Dependencies:         <list>
Validation Status:    <Not Started / Verified / QA'd / Published / Certified>
GitHub Branch:        <branch>
Last Commit:          <sha / message>
Next Action:          <single next valid action>
Blocking Conditions:  <none / list>
```

# APPENDIX C — Architecture Decision Log Template

```
ADL Entry:      <id / date>
Context:        <what triggered the decision>
Action:         <what was decided>
Recommendation: <the adopted option>
Why:            <justification, citing authority order / P1–P6>
Alternatives:   <rejected options — never erased>
Authority Cited: <User Instruction / Primary Source / etc.>
Scope Impact:   <Core Platform / Industry Suite / doc-only>
```

# APPENDIX D — Cross-Reference Convention

Reference another document/section rather than restating it. Format: `See <Document>.md → <Section>` (e.g., `See MI.md → Part 6.3 (API-First Principle)`). A rule owned in one place is cross-referenced everywhere else it is mentioned (P3).

# APPENDIX E — Authority-Order Quick Reference

```
Current Explicit User Instruction
   ↓
Primary Source of Truth (Master Enterprise Architecture & Product Requirements Source.md)
   ↓
Approved Project / Architecture Decisions
   ↓
Existing Certified Governance (MI + MP + certified Foundation docs)
   ↓
Supporting Knowledge
   ↓
Specialized Standards
   ↓
Industry-Specific Knowledge
   ↓
Historical / Legacy Knowledge
```

---

**END OF MASTER INSTRUCTION**
