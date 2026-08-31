# F-10 — DESKTOP FOUNDATION (RR-01 RESOLUTION)
**Document ID:** F-10 · **Version:** 1.0 · **Status:** SPECIFIED · Resolves REVIEW_REQUIRED RR-01 under explicit user authorization (Authority tier 2). Provenance: `[SD]` where sourced (S1 §2/§12, S2.1 §18, MI §15); structural completion `[AC — logged D-DECISIONS AC-15]`. Cross-refs: F-01 §3, F-03, F-06.

## 1. Desktop role in the Application Surface Model `[SD]`
Desktop is a **client surface**, never a separate platform: same Core Identity, same REST APIs, same tenant/industry context, same entitlement chain. Two desktop surfaces exist:
- **Platform Desktop** — platform-level application for Platform Owner / Super Admin / Platform Staff operations (part of the Platform Application surface).
- **Industry Desktop Experience** — optional, reusable at Industry level, instantiated per Tenant via the 3-layer model (Definition → Tenant Configuration → Published Instance). Enabled by plan, license, tenant need, industry need. Foundation-identified candidates: Retail POS Desktop (offline-first, AC-06), Hospitality front-desk/POS, Manufacturing plant/shop-floor station, Government counter Desktop, NGO donation-counter Desktop, Healthcare lab workstation.
- **Tenant Management** remains a Web surface only `[SD: MI §12]` — no Tenant Management Desktop is defined.

## 2. Platform & packaging `[SD]`
Windows 10/11 · native installer (.exe/.msi) · auto-update ready · Microsoft Store optional · direct installer distribution. Semantic versioning; minimum-supported-version and force-update policy mirror the mobile policy (single policy owner: release management, F-01 §9/S2.2 §55).

## 3. Authentication, session & context
Same Core Identity & Access system (LG-05): login via configured methods (F-03 §2), JWT + refresh tokens, **device registration mandatory** (desktop device identity = installation-bound device fingerprint), risk-based adaptive rules apply (unknown device, geo/time restrictions, concurrent session control). Tenant/Industry context resolution per F-01 §4 — explicit selection or deterministic surface binding; a Published Industry Desktop Instance is deterministically bound to its Tenant + Industry Context.

## 4. Authorization
RBAC (primary) + ABAC (complementary) evaluated **server-side** per F-03 §4; the desktop client renders only what the resolved permission set allows and never enforces authorization locally as the source of truth. Offline capability never bypasses the entitlement chain: offline access is limited to data/actions already authorized in the last valid server session, per policy (§6).

## 5. Configuration & the reusable Experience model
Tenant-configurable per instance (no per-tenant codebase, LG-08): app name, logo, colors, theme, splash, navigation, menus, dashboard, widgets, enabled modules, notifications, content, feature visibility — the same configuration surface as mobile (F-06 §4), served from the same Tenant Experience Configuration layer.

## 6. Offline & synchronization `[SD: single Synchronization Policy, F-01 §6]`
Offline mode only for previously-authenticated, authorized users. Encrypted secure local storage; local operation queue; automatic background sync on reconnect; conflict resolution per the one canonical Synchronization Policy (shared with Mobile — no desktop-specific sync policy exists). All offline-queued operations are revalidated server-authoritatively on sync (F-03 §3). Local data purged on tenant/device deregistration or remote wipe instruction.

## 7. Notifications & integrations
In-app notification center backed by the Core notification engine; native OS notifications where the platform permits; delivery/read status reported back to the Core engine (F-02 W-09). Device features (printers — receipts/reports/labels, barcode/QR scanners, cash drawers for POS candidates) accessed through a governed device-capability layer; all business I/O flows through the REST API — the desktop never connects directly to the database or to another tenant system.

## 8. Security
Secure local storage encrypted at rest (AES-256 posture, F-03 §5); certificate pinning posture aligned with mobile; token storage in OS-protected credential store; session lock on idle per policy; remote sign-out/device revocation from the Tenant Management App; audit events (login, sync, offline actions) reported to the audit fabric with device identity.

## 9. Testing & acceptance
Test families: authentication/device registration; offline→sync round-trip integrity (no loss, no duplication, conflict rules honored); entitlement enforcement on reconnect; tenant + industry-context isolation on shared machines (multi-profile); update/rollback of installer; notification delivery. Acceptance: a Published Industry Desktop Instance completes its suite's core operational cycle offline and syncs cleanly under the Synchronization Policy with a complete audit trail.

## 10. Dependency boundaries & deferrals
Depends on: Core Identity (F-03), API platform (F-01 §7), Synchronization Policy (F-01 §6), Experience model (F-06 §1). **Explicitly deferred to Architecture phase (recorded, not a gap):** desktop implementation framework selection (e.g., Flutter Windows vs .NET vs web-wrapper), local database engine choice, packaging pipeline, auto-update transport — these are technology decisions with no corpus basis; selecting one at Foundation would be invention. A dedicated **Desktop Architecture Standards** document is a named Architecture-phase deliverable (parity target: Mobile Architecture Standards depth), and its future existence is recorded in D-DECISIONS AC-15. This is the Foundation-complete resolution of RR-01: the source gap (S2.1 §18 note) is closed at Foundation depth with the remaining technology choice explicitly owned by the next phase.
