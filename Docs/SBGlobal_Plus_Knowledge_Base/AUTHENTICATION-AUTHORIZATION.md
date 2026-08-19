# SBGlobal Plus — Authentication & Authorization (AUTHENTICATION-AUTHORIZATION.md)

**(Foundation Document 23 of 31 — SBGlobal Plus Knowledge Base)**

Version: 1.0
Status: Published
Last Updated: 2026-08-19
Governing Authority: `Docs/MI.md` Part 6.5, Part 7.2; `Docs/Raw knowledge files/Master Enterprise Architecture & Product Requirements Source.md` §4, §5; `Docs/Raw knowledge files/02_SBGlobal_Plus_Product_Specification_Requirement.md` §35
Owning Tier: Foundation — Core Platform (industry-neutral)

> **Role of this document.** AUTHENTICATION-AUTHORIZATION.md is the single owning document for authentication method mechanics, risk-based adaptive authentication, digital identity/signature provider integration, and the RBAC authorization model (MI 6.5, 7.2). It does not own application/API security controls, secrets & key management, or API threat protection (`SECURITY-GOVERNANCE.md`), device registration/trust/license-binding enforcement (`LICENSING-DEVICE-MANAGEMENT.md`), tenant-level security policy configuration limits (`MULTI-TENANCY.md` §7), or the audit-trail field standard that authentication/authorization events are recorded under (`DATA-ARCHITECTURE.md` §7) — each is cross-referenced here rather than restated (MI Part 8, P3).

---

## 1. Purpose of This Document

AUTHENTICATION-AUTHORIZATION.md answers: which methods can a user or service authenticate with, how does the platform decide when to demand more proof of identity, how are digital identity and signature providers integrated, and how is a validated identity turned into an enforceable set of permissions. It expands `ARCHITECTURE.md` §5 (the Server-Authoritative access flow) and `MULTI-TENANCY.md` §8 into the full Authentication & Authorization standard and is the document every other Foundation document's "authentication mechanism depth" or "API authentication mechanics" cross-reference resolves to.

---

## 2. Ownership Map

| Concern | Owning Document | This document's role |
|---|---|---|
| Authentication methods and their configuration | **AUTHENTICATION-AUTHORIZATION.md** (this document) | Full ownership |
| Risk-based adaptive authentication | **AUTHENTICATION-AUTHORIZATION.md** (this document) | Full ownership |
| Digital identity & digital signature provider integration | **AUTHENTICATION-AUTHORIZATION.md** (this document) | Full ownership |
| RBAC authorization model (roles, permissions, scope of assignment) | **AUTHENTICATION-AUTHORIZATION.md** (this document) | Full ownership |
| Session and token issuance policy (JWT access/refresh token mechanics) | **AUTHENTICATION-AUTHORIZATION.md** (this document) | Full ownership |
| Application & API security controls, secrets/key management, API threat protection | `SECURITY-GOVERNANCE.md` | Not owned here; cross-referenced only |
| Device registration, trust, license-binding enforcement | `LICENSING-DEVICE-MANAGEMENT.md` | Not owned here; cross-referenced only |
| Tenant-level limits on which security settings a Tenant Admin may configure | `MULTI-TENANCY.md` §7 | Not owned here; cross-referenced only |
| Trust-service validation results as audit-logged events; certificate revocation checking mechanics | `SECURITY-GOVERNANCE.md` §6 | Baseline guarantee only; provider integration owned here |
| Authentication/authorization audit-trail field standard | `DATA-ARCHITECTURE.md` §7 | Not owned here; cross-referenced only |

---

## 3. Authentication Methods

Every method below is pluggable and enabled/disabled entirely through configuration (`CONFIGURATION-METADATA.md` §2 Preference Chain), never through a source-code change, and is independently configurable per Tenant, Role, Device, Platform, and Subscription Plan (`CONFIGURATION-METADATA.md` §3 scope hierarchy):

- **Credential-based** — Username / Email / Mobile + Password, Mobile OTP, Email OTP, Magic Link, Passwordless, QR Code Login.
- **Federated / Enterprise Identity** — Google Sign-In, Microsoft Entra ID (Azure AD), Apple Sign-In, Enterprise Single Sign-On (SSO), OAuth 2.0, OpenID Connect (OIDC), SAML 2.0, LDAP / Active Directory, Enterprise Identity Federation.
- **Possession- and inherence-based** — Passkeys (FIDO2 / WebAuthn), Authenticator Apps (TOTP), Hardware Security Keys, Face / Fingerprint / Iris / Biometric Authentication.
- **Service-to-service** — API Token Authentication, Service Account Authentication, API Key Authentication.
- **Multi-Factor Authentication (MFA)** — composable with any credential-based or federated method above as an additional required factor, per policy (§4).

No method is mandatory at Core Platform tier beyond the minimum needed to satisfy the Server-Authoritative access flow (`ARCHITECTURE.md` §5); which methods are enabled for a given Tenant, Role, or Platform is a configuration decision, not an architectural one.

---

## 4. Risk-Based Adaptive Authentication

The platform evaluates authentication risk signals and adapts the required proof of identity accordingly:

- **Signals** — Trusted Device recognition, Unknown Device Detection, Impossible Travel Detection, Geo-Fencing, Geo-Restriction, Login Time Restrictions, Concurrent Session Control.
- **Response** — a risk signal may trigger Step-Up Authentication (an additional factor demanded mid-session or at a sensitive action) or MFA enforcement where it was otherwise optional.
- **Configuration scope** — risk policy is configurable per Tenant, User, User Group, Department, Organization, Device, Platform, Module, Location, and Subscription Plan (`CONFIGURATION-METADATA.md` §3), always within the limits a Tenant Admin may set (`MULTI-TENANCY.md` §7) and never below the Platform-Locked Security Settings (`SECURITY-GOVERNANCE.md` §7).
- **Audit** — every adaptive-authentication decision (a step-up challenge issued, a login blocked by geo-restriction) is a security-relevant, audit-logged event under the standard owned by `SECURITY-GOVERNANCE.md` §3 and `DATA-ARCHITECTURE.md` §7.

---

## 5. Digital Identity & Digital Signature Providers

Configurable, pluggable providers for identity verification and document signing, integrated the same way any authentication method is (§3):

- Aadhaar eSign
- DigiLocker
- USB eToken
- Digital Signature Certificates (DSC)
- PKI Certificates
- Government Identity Providers
- Enterprise PKI / Organization Certificates

Each provider's Trust Services validation — Digital Certificate Validation, Timestamp Validation, Certificate Revocation Checking (OCSP/CRL), Certificate Transparency Validation, Non-Repudiation — is guaranteed to produce an audit-logged, security-relevant event by `SECURITY-GOVERNANCE.md` §6; this document owns which providers are integrated and how a tenant enables them, not the audit-evidence guarantee itself. Digital-signature integration for AI Document Intelligence-processed documents (contracts, certificates, and similar) is owned here and consumed by `AI-API-STRATEGY.md` §8 rather than reimplemented.

---

## 6. Authorization Model (RBAC)

- **Roles & Permissions** — access is granted through Role-Based Access Control: a User is assigned one or more Roles, each Role carries a set of Permissions, and every protected request evaluates the User's effective Permissions before proceeding (`SECURITY-GOVERNANCE.md` §3 owns the enforcement point at the application/API layer; this document owns the model that produces the decision it enforces).
- **Permission Groups & Policy-Based Authorization** — Permissions may be organized into reusable Permission Groups, and authorization decisions may additionally be evaluated against declarative Policies (e.g., attribute- or condition-based rules) layered on top of the base RBAC grant, without requiring a source-code change (`CONFIGURATION-METADATA.md` §2).
- **Scope of assignment** — a Role/Permission grant is always evaluated within exactly one Tenant (`MULTI-TENANCY.md` §8: no permission grant is valid outside the tenant it was issued under) and may additionally be scoped to User Group, Department, Organization, Device, Platform, Module, and Location, matching the same configuration scope dimensions used for authentication policy (§4).
- **Super Admin vs. Tenant Admin separation** — the two authorization domains are never confused (`ARCHITECTURE.md` §8): Super Admin manages platform-level Authentication/Authorization Policy defaults and locked settings; a Tenant Admin manages Authorization Policies and Authentication Settings within those limits (`MULTI-TENANCY.md` §5 table), and can never grant a permission the Platform scope has not made available.

---

## 7. Session & Token Management

Every successful authentication in the Server-Authoritative access flow (`ARCHITECTURE.md` §5: `Authentication Service → Tenant Validation → Subscription Validation → License Validation → Device Registration Validation → RBAC Permission Validation → JWT Access Token → Refresh Token → Platform Access Granted`) issues a JWT Access Token and a Refresh Token:

- **Access Token** — short-lived, carries the validated identity, tenant, and effective permission context needed to authorize subsequent requests without re-evaluating the full access flow on every call.
- **Refresh Token** — used to obtain a new Access Token without re-prompting credentials, subject to Concurrent Session Control (§4) and the same risk-based re-evaluation as a fresh login when risk signals warrant it.
- **Session security mechanics** (secure storage, transport, brute-force protection around token endpoints) are owned by `SECURITY-GOVERNANCE.md` §3; this document owns only the issuance policy and the identity/permission content a token carries.
- **API authentication mechanics** referenced by `AI-API-STRATEGY.md` §3 (Governance scope) resolve to this section: every API call is authenticated via the same token standard regardless of which product surface issued it.

---

## 8. Industry-Neutrality Audit

Every rule in this document was tested against three unrelated industries — a hospital, a school, and a manufacturing plant — and holds identically: the same Authentication Methods catalogue (§3), the same Risk-Based Adaptive Authentication mechanism (§4), the same Digital Identity & Signature Provider integration pattern (§5), and the same RBAC Authorization Model (§6–§7) apply regardless of industry. Digital identity providers such as Aadhaar eSign and DigiLocker are jurisdiction-specific rather than industry-specific — every industry operating in that jurisdiction receives the same access to them, and an industry operating elsewhere is unaffected, so no industry is made primary, first, or dominant by their inclusion (MI Part 5.1). Where supporting raw knowledge framed authentication and compliance capability together as a single "Security & Compliance" business requirement, this document draws the line at the mechanism/method boundary and defers the regulatory-compliance framing entirely to `COMPLIANCE-PRIVACY.md`, consistent with the Single-Owning-Document discipline (MI Part 8, P3).

---

## 9. Traceability

```
Primary Source of Truth (§5 Identity, Authentication & Authorization Framework);
Product Specification Requirement raw knowledge §35 (Authentication / Authorization, business-level)
        ↓
MI.md Part 6.5 (Multi-Tenant Principle — Authorization); Part 7.2 (Super Admin vs. Tenant Admin)
        ↓
ARCHITECTURE.md §5 (Server-Authoritative access flow) · MULTI-TENANCY.md §8 (not restated here)
        ↓
AUTHENTICATION-AUTHORIZATION.md  (this document — authentication methods, risk-based adaptive
authentication, digital identity/signature providers, RBAC authorization model, session/token policy)
        ↓
SECURITY-GOVERNANCE.md · LICENSING-DEVICE-MANAGEMENT.md · COMPLIANCE-PRIVACY.md ·
AI-API-STRATEGY.md §3, §8 (depth / consuming owners)
```

---

## 10. Change Log

| Version | Date | Change | Decision Reference |
|---|---|---|---|
| 1.0 | 2026-08-19 | Initial publication — Foundation Batch 4. Expands MI Part 6.5/7.2 and Primary Source §5 (plus Product Specification Requirement §35) into the public Knowledge Base; establishes the Authentication Methods catalogue, Risk-Based Adaptive Authentication, Digital Identity & Signature Provider integration, the RBAC Authorization Model, and Session/Token Management policy. | ADL-2026-08-19-07 |

---

**Document Status:** ✅ Published v1.0 — Verified and QA'd under MI Part 10, including the Industry-Neutrality Audit (§8) for all Core-tier content in this document. Not yet Certified (milestone-level only — MI Part 10).
