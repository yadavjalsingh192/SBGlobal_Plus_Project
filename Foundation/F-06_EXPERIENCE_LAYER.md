# F-06 — EXPERIENCE LAYER (WEB · MOBILE · DESKTOP)
**Document ID:** F-06 · **Version:** 0.2 · **Status:** SPECIFIED · Cross-refs: F-01 §3 (surfaces), F-03 (identity), F-07…F-09 (industry experiences).

---

## 1. Reusable Industry Experience Model `[SD: MI §11]` — ACTIVE, 3 explicit layers, never collapsed

```
1. INDUSTRY EXPERIENCE DEFINITION        (reusable, Industry-level)
2. TENANT EXPERIENCE CONFIGURATION       (per-Tenant configuration of the Definition)
3. PUBLISHED TENANT EXPERIENCE INSTANCE  (live, branded, configured result)
```
Applies to: Industry Website · Industry Web Application · Industry Staff Mobile · Industry User/Student/Customer Mobile · optional Industry Desktop. Specialized source capabilities (Laboratory Website, Hospital/Clinic Website, School Website, Retail Store Experience…) are specialized reusable Industry experiences — never Core components, never per-tenant codebases (LG-08).

## 2. Public SaaS Website `[SD: S1 §11; S2.2 §9]`
Sitemap: Home · Vision/Company · Platform (Architecture/AI/Security/API) · Industries (all 9) · Solutions (Web/Mobile/Desktop) · Subscription/Pricing (5 tiers) · Book Demo · Request Quote · **Start Free/Self-Serve Signup** · Customers/Partners/Marketplace · Compare · Resources (Docs/Blog/FAQ) · **Trust Center** (security status, compliance certifications, uptime/status page) · **Legal** (ToS, Privacy, Cookie, SLA, DPA, Refund). Components: loader animation ("Enterprise Core Initialization" sequence), hero with dual CTA, announcement bar (priorities, scheduling, analytics), testimonials, pricing/comparison tables, FAQ, demo popup, AI chatbot/live chat widget, cookie consent banner, dark/light mode, language toggle, newsletter, app download, SEO/OpenGraph/structured data. No placeholder or dummy filler text anywhere `[SD: S2.2 §9]`.

## 3. Platform & Tenant Management Applications
Per F-01 §3. Tenant Management covers: tenant profile, primary/enabled industries, subscription/plans/upgrade/downgrade, billing, usage, licensing, services, management systems, modules, domains/subdomains, branding, users/roles/permissions, API, AI, integrations, notifications, configuration, security, settings.

## 4. Mobile Architecture `[SD: MI §15; S2.5 — single technical owner]`
- Apps: **Platform Mobile (Super Admin)** · **Tenant Staff Mobile** (all internal roles via RBAC) · **Tenant User/Customer Mobile** — reusable frameworks configured per Tenant (name, logo, colors, theme, splash, navigation, menus, dashboard, widgets, enabled modules, notifications, content, feature visibility). No per-tenant codebase for configuration.
- Stack: Flutter/Dart, Riverpod, Clean/Feature-based architecture, SQLite/Hive/Secure Storage, REST+JWT, FCM, offline-first (local queue, conflict resolution, incremental sync, retry), SSL pinning, device binding, root/jailbreak detection, QR/barcode, deep linking; store + enterprise APK + MDM distribution; force-update policy.
- Dynamic mobile platform `[SD: S2.2 §31]`: Super Admin manages branding/navigation/endpoints/version control/maintenance mode without rebuild (native package changes excepted).

## 5. Desktop Architecture `[SD: MI §15; S2.1 §18]`
Platform Desktop (platform-level) · optional Industry Desktop Experience enabled by plan/license/tenant/industry need. Windows 10/11 native (.exe/.msi), auto-update, offline-first, secure local storage, same Core Identity/APIs/security/contexts. Fluent-inspired UI, multi-window, ribbon navigation `[SD: S1 §12]`. Gap preserved honestly: full Desktop Architecture Standards document does not yet exist at Mobile-standards depth `[SD: S2.1 §18 note]` → REVIEW_REQUIRED register RR-01. *(Build 2: RR-01 resolved — Foundation-level Desktop specification now at F-10; technology selection remains an Architecture-phase deliverable.)*

## 6. UI/UX Layer Model `[SD: MI §19]`
**Core Design System → Industry Experience Layer → Tenant Branding Layer → Application Surface Layer.** Component library, grid (12/8/4), spacing scale (4…96), radius scale, status colors, breakpoints owned by Enterprise UI Design System `[SD: S2.8]`; brand tokens/typography/table/form defaults owned by Enterprise Default Standards `[SD: S2.7]` (baseline: Asia/Kolkata · dd-MM-yyyy · INR · English/Hindi); industry-specific defaults (LIS report flags, invoice defaults…) scoped to their Suites. Accessibility: keyboard navigation, ARIA, high contrast, screen reader, reduced-motion respect. Never a completely different design system per Tenant.

### 6.1 Approved Global Brand Palette `[UD 04-09-2026 · AC-19]` — ACTIVE, single Foundation-level canonical owner
This subsection is the ONE canonical Foundation-level record of the approved SBGlobal Plus brand palette. Enterprise UI Design System / Enterprise Default Standards instantiate design tokens from these values in the Architecture/Detailed Design phases; no other Foundation document may define competing palette values.

| Role | Value | Semantic meaning |
|---|---|---|
| Primary | `#06B6D4` | Cyan — main brand identity, primary actions, primary CTAs, primary brand highlights |
| Primary Hover | `#2563EB` | Blue — hover/pressed/focused states for primary interactive elements |
| Secondary | `#0F766E` | Deep Teal — secondary actions, supporting controls, secondary highlights |
| Accent | `#7C3AED` | Purple — special highlights, premium/AI-oriented accents, selective emphasis |
| Success | `#16A34A` | Green — positive/completed/success states |
| Warning | `#F59E0B` | Amber — warnings, caution, pending states |
| Danger | `#DC2626` | Red — errors, destructive actions, critical alerts |
| Info | `#0284C7` | Blue — informational and neutral informational states |

**Backgrounds:** White `#FFFFFF` · Gray `#F8FAFC` · Sidebar `#0F172A` · Card `#FFFFFF` · **Text:** Heading `#0F172A` · Body `#475569` · Muted `#64748B` · Border `#E2E8F0`

Scope: Public SaaS Website, Platform & Tenant Management applications, Web/Mobile/Desktop surfaces, dashboards, CTAs, navigation, active/alert/status states; Tenant Branding Layer may override within governed constraints above. Provenance: owner-approved palette migration — supersedes the historical corpus palette (Primary `#0F766E`, Primary Hover `#115E59`, Secondary `#2563EB`, Accent `#06B6D4`) as ACTIVE; `#0F766E` is retained in the Secondary role (not retired), `#115E59` holds no ACTIVE role; historical values remain preserved, unmodified, in RawSourceCorpus as immutable evidence.

**Deferred:** per-surface screen inventories, navigation maps, design-token instantiation — Architecture/Detailed Design.
