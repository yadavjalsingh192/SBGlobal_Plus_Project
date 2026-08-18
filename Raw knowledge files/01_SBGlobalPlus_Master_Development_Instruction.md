# SBGlobal Plus Master Development Instruction

Version: 3.0 (Aligned Edition — see CHANGELOG_ALIGNMENT_NOTES.md)

Status: Production Master Development Standard

Role in this package: **Baseline / Tier 1 document.** Preserved in its original meaning and structure. Only additive cross-reference notes (marked with `>`) have been inserted to resolve overlap with other documents in this set — no original rule, section, or wording has been removed or altered.

---

# 1. Purpose

This document is the highest-priority software development instruction for the entire SBGlobal Plus project.

It governs every development phase, architecture decision, implementation, testing, documentation, deployment and future maintenance.

This document always works together with:

• SBGlobal Plus Production Product Specification / Business Requirement
• Engineering Standards
• Phase Specifications
• Approved User Instructions

---

# 2. Governing Documents Priority

Development shall always follow this order:

1. User Explicit Instructions (Current Task)
2. SBGlobal Plus Master Development Instruction
3. SBGlobal Plus Production Product Specification / Business Requirement
4. Engineering Standards
5. Approved Phase Specifications

Higher-priority documents always override lower-priority documents.

## 2A. Specialized Standards Tier

> Added for cross-document alignment; does not change the priority order above.

Dedicated architecture standards — Database Architecture Standards, Mobile Architecture Standards, AI Architecture Standards — and the design-token documents — Enterprise UI Design System, Enterprise Default Standards — operate as specialized extensions of Tier 4 (Engineering Standards) for their respective domains. Each is the single authoritative owner of its domain's technical detail; every other document in this set cross-references them instead of repeating their content. The Enterprise Development Roadmap operates at Tier 5 (Approved Phase Specifications) and supplies deliverable volume targets, not phase authority. See `00_INDEX.md` for the complete ownership map.

---

# 3. Development Principles

The project shall always be:

• Production Ready
• Enterprise Grade
• AI Ready
• Secure by Design
• API First
• Mobile First
• 🆕 Cross-Platform Ready (Web, Mobile, Windows Desktop)
• Modular
• Configuration Driven
• Database Driven
• Multi-Tenant
• Scalable
• Future Ready
• Backward Compatible
• White Label Ready

---

# 4. Implementation Rules

AI shall:

• Complete implementation instead of leaving placeholders.
• Never generate demo-only architecture.
• Never generate incomplete modules.
• Never intentionally simplify enterprise architecture.
• Never remove existing working functionality.
• Maintain clean, maintainable and production-quality code.

---

# 5. Gap Analysis Policy

Before every implementation phase AI shall compare:

• Actual Source Code
• Business Requirement
• Master Development Instruction
• Engineering Standards

AI shall identify:

• Missing Features
• Incomplete Features
• Architecture Gaps
• API Gaps
• UI/Admin Gaps
• Database Gaps
• Documentation Gaps

All identified gaps shall be completed before implementing new features whenever reasonably possible.

---

# 6. Autonomous Development Policy

Unless explicitly instructed otherwise, AI shall automatically:

• Perform GAP Analysis
• Update Backend
• Update Frontend/Admin
• Update APIs
• Update Database
• Update Tests
• Update Documentation
• Update Recovery Files
• Verify Completion

AI shall ask for confirmation only when an architectural decision cannot be inferred from the governing documents.

# 6A. Silent Development Mode

During implementation AI shall operate in Silent Development Mode unless explicitly instructed otherwise.

AI shall:

• Perform implementation directly.
• Batch related changes together.
• Avoid unnecessary confirmations.
• Never narrate implementation progress.
• Never explain internal reasoning.
• Never output planning messages.
• Never print implementation steps.
• Never dump source code unless explicitly requested.
• Never describe individual file edits.
• Never interrupt development unless blocked.

AI shall communicate only when:

• A genuine blocking issue exists.
• Required project files are missing.
• User approval is explicitly required.
• Phase completion has been reached.

At phase completion AI shall provide only:

• Phase Completion Summary
• Blocking Issues (if any)
• Remaining Work (if any)
• Next Phase (if applicable)

Silent Development Mode shall remain the default behavior throughout the entire project lifecycle.

AI shall perform all modifications directly within the local VS Code workspace.

AI shall not create ZIP packages during normal development unless explicitly requested by the user or required for an official release.

---

# 7. Source of Truth

The following documents are authoritative throughout the project lifecycle:

• SBGlobal Plus Master Development Instruction
• SBGlobal Plus Production Product Specification / Business Requirement
• Engineering Standards

Project progress shall be tracked through:

• Actual Source Code
• PROJECT_STATE.md
• PROJECT_MANIFEST.json

---

# 8. Continuity Policy

Development shall preserve continuity across phases, sessions and conversations.

## Same Chat

When continuing within the same conversation, AI shall verify only:

• Actual Source Code
• PROJECT_STATE.md
• PROJECT_MANIFEST.json

AI shall then continue directly from the latest verified implementation.

## New Chat / Context Loss

When development resumes in a new conversation or after context loss, AI shall verify:

• Entire Project Source Code
• PROJECT_STATE.md
• PROJECT_MANIFEST.json
• CHANGELOG.md
• PHASE_SUMMARY.md
• Latest Verified Local Workspace (if provided)

If documentation differs from the source code:

1. Actual Source Code is authoritative.
2. Update documentation to match.
3. Continue from the verified implementation.

Completed work shall never be recreated unnecessarily.

---

# 9. User Continuation Commands

The following commands shall automatically resume development:

• Continue
• Continue Development
• Continue Writing
• Continue Phase
• Resume
• Next
• Continue from Last State

No additional explanation or reconfirmation shall be required unless a genuine blocking issue exists.

---

# 10. Backup & Recovery Policy

At the completion of every phase AI shall update:

• PROJECT_STATE.md
• PROJECT_MANIFEST.json
• CHANGELOG.md
• PHASE_SUMMARY.md

Then verify that the complete project workspace is fully updated.

The primary development workspace shall be the local VS Code project folder.

AI shall update all project files directly inside the local workspace, including source code, configurations, database files, documentation and recovery files.

A ZIP package shall be created only when explicitly requested by the user or when preparing a release, milestone, backup or production delivery.

A phase shall be considered COMPLETE only after development, testing, documentation and recovery files are updated. If a release package is requested, it shall be generated and verified before delivery. After phase completion, development shall stop and wait for a User Continuation Command (see Section 9) unless the user has explicitly requested continuous/autonomous progress through all phases.

The latest verified local project workspace shall be the primary development and recovery source. Release ZIP packages are optional artifacts created only on user request or for official releases.

---

# 11. No Regression Policy

New implementation shall never break existing functionality.

AI shall preserve:

• Existing Features
• Database Compatibility
• API Compatibility
• UI Compatibility
• Tenant Isolation
• Security
• Performance
• Existing Configurations

Regression verification shall be completed before phase completion.

---

# 12. Deployment Simplicity Policy

> This is the authoritative version of this policy platform-wide. Product Specification Requirement Section 40A cross-references this section rather than repeating it.

The default deployment method shall remain simple and suitable for cPanel, shared hosting and single-server VPS deployments.

Standard deployment workflow:

1. Project Download / Build
2. Upload Project to Server
3. Create Database
4. Import Database (or Fresh Install)
5. Configure .env
6. Enter Database Credentials
7. Run Migration / Seeder (if required)
8. Create Storage Link
9. Clear & Optimize Cache
10. Project Website Live

Advanced infrastructure including:

• Docker
• Kubernetes
• Event Sourcing
• CQRS
• Multi-region Deployment
• Service Mesh
• Data Warehouse
• Enterprise Infrastructure

shall remain OPTIONAL and shall never become mandatory for standard deployment.

The platform shall remain fully functional without implementing these optional enterprise features.

---

# 13. Code Quality Rules

All code shall be:

• Clean
• Readable
• Modular
• Reusable
• SOLID-compliant
• DRY
• Secure
• Performance Optimized
• Properly Documented
• Maintainable

> Detailed coding standards (Laravel practices, PSR-12, SOLID, service layer, repository pattern, etc.): see Engineering Standards — Section 3 Coding Standards (authoritative).

---

# 14. Testing Policy

Before phase completion AI shall verify:

• Backend
• Frontend/Admin
• APIs
• Database
• Integrations
• Authentication
• Authorization
• Multi-Tenant Isolation
• Security
• Regression

> Detailed test type breakdown (unit, feature, integration, tenant isolation, API, performance testing): see Engineering Standards — Section 5 Testing Standards (authoritative).

---

# 15. Documentation Policy

Documentation shall always remain synchronized with the implemented source code.

Whenever implementation changes, the related documentation shall be updated accordingly.

---

# 16. Completion Policy

A phase is considered complete only when:

• GAP Analysis is complete.
• Backend is complete.
• Frontend/Admin is complete.
• APIs are complete.
• Database is complete.
• Tests are complete.
• Documentation is updated.
• Recovery files are updated.
• If a release package is requested, the ZIP package is generated and verified.
• No critical regression exists.

---

# 17. Blocking Rule

Development shall stop only when:

• Required project files are missing.
• Uploaded project is corrupted.
• Critical dependencies are unavailable.
• User instructions directly conflict with governing documents.
• Continuing would risk damaging verified implementation.

Otherwise development shall continue automatically.

---

# 18. Technology Stack

The following technology stack is the default baseline for SBGlobal Plus and shall not be changed without an explicit user instruction.

## Backend

• Laravel 13
• PHP 8.4

## Frontend

• Blade
• Tailwind CSS
• Alpine.js

## Database

• MySQL

## Admin Panel

• Filament 5

## Authentication

• Laravel Authentication (Web)
• OTP Authentication
• JWT Authentication (API Only)
• Role & Permission Management
• 🆕 Enterprise SSO
• 🆕 OAuth 2.0
• 🆕 OpenID Connect (OIDC)
• 🆕 SAML 2.0
• 🆕 LDAP / Active Directory
• 🆕 Passkeys (FIDO2/WebAuthn)
• 🆕 Multi-Factor Authentication (MFA)
• 🆕 Biometric Authentication
• 🆕 PKI / Digital Certificates
• 🆕 Aadhaar eSign
• 🆕 DigiLocker Integration
• 🆕 Enterprise Identity Federation

> 🆕 Business-capability detail (which methods surface to which user types, compliance framing) and technical security-control depth (protocol implementation, token handling): see Product Specification Requirement — Section 35 (Security & Compliance) and Engineering Standards — Section 4 (Security Standards). Those documents require their own follow-up integration pass to reflect this expanded baseline.

## Deployment Constraints

• cPanel Compatible
• No Docker Dependency (Docker remains optional per Section 12)
• No Vercel Dependency

> 🆕 Desktop application distribution (.exe/.msi to end-user machines) is separate from, and does not conflict with, this server-side deployment simplicity policy.

## Mobile Application Stack

Framework:

• Flutter (Latest Stable)

Platforms:

• Android
• iOS

Architecture:

• REST API
• JWT Authentication
• Offline Ready
• Firebase Cloud Messaging (FCM)

Deployment:

• Google Play Store
• Apple App Store

Mobile application development runs in parallel with the corresponding portal phases (see Section 20).

> Full mobile technical architecture — state management, local storage, background services, security, QR/barcode, device features, and app-specific modules: see SBGlobal_Plus_Mobile_Architecture_Standards.md (authoritative for this domain).

## 🆕 Desktop Application Stack

Platform:

• 🆕 Windows 10/11

Packaging:

• 🆕 Native Installer (.exe / .msi)
• 🆕 Auto-Update Ready

Architecture:

• 🆕 REST API
• 🆕 JWT Authentication
• 🆕 Offline Ready
• 🆕 Secure Local Storage

Deployment:

• 🆕 Direct Installer Distribution
• 🆕 Microsoft Store (Optional)

Desktop application development runs in parallel with the corresponding portal phases (see Section 20).

> 🆕 Full desktop technical architecture — packaging framework, local database, background sync, and security model — is not yet defined at the depth Mobile Architecture Standards defines for mobile. A dedicated Desktop Architecture Standards document may be warranted once implementation details are decided; not created at this time.

---

# 19. Reference Architecture

The following repositories are approved as architecture, workflow and best-practice references only.

AI shall NEVER:

• Copy source code from these repositories.
• Merge external code into the project.
• Introduce license conflicts.
• Add unnecessary dependencies because a reference uses them.

AI shall use these references only for inspiration on architecture, workflow, feature ideas and best practices. All project code shall remain freshly written and original.

| Purpose | Repository | Use For |
|---|---|---|
| Laboratory Information System | OpenELIS Global — https://github.com/DIGI-UW/OpenELIS-Global-2 | Patient workflow, sample lifecycle, laboratory workflow, result management, reporting concepts |
| Multi-Tenant Architecture | https://github.com/michaelnabil230/laravel-multi-tenancy | Tenant isolation, multiple labs, secure data separation |
| Admin Dashboard | Filament — https://github.com/filamentphp/filament | Super Admin, Lab Admin, CRUD, analytics, settings |
| SaaS Foundation | https://github.com/mohammedelkarsh/laravel-tenant-kit | SaaS foundation patterns |
| PDF Generation | https://github.com/barryvdh/laravel-dompdf | PDF report generation |
| QR Codes | https://github.com/SimpleSoftwareIO/simple-qrcode | QR generation and verification |
| Inventory | https://github.com/akaunting/akaunting | Inventory and accounting concepts |

Workflow: Reference Analysis → AI Development → Fresh SBGlobal Plus Code.

---

# 20. Development Phase Roadmap

Development shall proceed through the following phases in order. Each phase shall follow the Completion Policy (Section 16) before the next phase begins, unless the user has explicitly instructed continuous/autonomous progress through multiple phases.

01. Project Foundation
02. Database Architecture
03. Authentication
04. Super Admin Dashboard
05. SaaS Website CMS
06. Multi Tenant
07. 🆕 Tenant Web Portal – Core Modules
08. 🆕 Tenant Web Portal – Customer/User Modules
08A. Mobile API Foundation
08B. 🆕 Flutter Tenant User/Customer App
09. 🆕 Tenant Web Portal – Staff Modules
09A. 🆕 Flutter Tenant Staff App (Doctor Modules)
10. LIS Core
10A. 🆕 Flutter Tenant Staff App (Lab Staff Modules)
11. Reports + PDF + QR
12. Billing
13. Inventory
14. Communication
15. AI Core
16. AI Advanced
17. Enterprise & Integration (Branch/Department/Appointment Management, Enterprise Integration, API & Interoperability, Analytics, Localization, Document Management — per the Business Requirement)
18. Security
19. Performance
20. Testing
21. Final Production Release
21A. Mobile Production Release
21B. 🆕 Windows Desktop Production Release

Mobile application development (08A/08B/09A/10A/21A) runs in parallel with the corresponding portal phases. 🆕 Windows Desktop application development (21B) likewise runs in parallel with the corresponding portal phases; granular per-portal desktop phase codes (a desktop counterpart to 08A/09A/10A) are deferred until implementation details are decided. Phase 17 exists to absorb the additional business modules defined in the Business Requirement (Sections 13–14, 18, 27–29, 34, 39, 49, 63) that extend beyond the original core module set; it does not remove or replace any other phase.

> This Section 20 sequence is authoritative for phase order and phase gating. Thematic construction checklists and expected deliverable volumes supporting these phases (e.g., expected table counts, master data counts, dropdown values, settings pages, permission counts) are maintained in `SBGlobal_Plus_Enterprise_Development_Roadmap.md`. Where that document's thematic groupings (its own "Phase 01–14" labels) differ in numbering from the sequence above, this Section 20 remains authoritative for sequencing; the Roadmap document is authoritative only for volume/deliverable targets.

---

# 21. Recovery File Specifications

## PROJECT_STATE.md shall include:

• Project Name • Current Phase • Status • Completed Tasks • Pending Tasks • Next Action • Database Changes • Files Created • Files Modified • Configuration Changes • Dependencies • Known Issues • Testing Status • Last Working Point • Last Updated

## PROJECT_MANIFEST.json (machine-readable) shall maintain:

• Current Phase • Version • Completed Modules • Pending Modules • Migrations • Seeders • Models • Controllers • Services • Routes • APIs • Assets • Dependencies • AI Providers • Last Release Package (if generated) • Last Updated

## PHASE_SUMMARY.md shall include:

• Phase Number • Objectives • Completed Features • Files Created • Files Modified • Database Changes • Dependencies • Bugs Fixed • Known Issues • Testing Results • Next Action

---

# 22. Final Delivery Package

Before preparing the final production delivery package, verify the full Acceptance Criteria (Business Requirement, Section 58) plus:

• All Development Phases (Section 20) • Architecture • Authentication • Multi-Tenant • Super Admin Portal • 🆕 Tenant Web Portal • SaaS Website • Lab Website • LIS • Billing • Inventory • AI (all providers including Amazon Bedrock) • Reports • QR • Communication • Security • Performance • Documentation • PROJECT_STATE.md • PROJECT_MANIFEST.json • CHANGELOG.md • PHASE_SUMMARY.md • ZIP Integrity • Mobile APIs • 🆕 Flutter Tenant User/Customer/Tenant Staff/Super Admin Apps • Push Notifications • API Documentation • 🆕 Windows Desktop Application

The Final Production Delivery Package shall include:

• Complete Source Code • Complete Database • All Modules • Documentation • Installation Guide • Deployment Guide • User Manual • Final PROJECT_STATE.md • Final PROJECT_MANIFEST.json • Final CHANGELOG.md • Final PHASE_SUMMARY.md • 🆕 Windows Desktop Application Installer Package  • Administrator Guide • API Reference

Only after successful verification may the project be marked Production Ready.

---

End of Master Development Instruction


