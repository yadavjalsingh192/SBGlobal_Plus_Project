# SBGlobal Plus Mobile Architecture Standards

Version: 1.0

Status: Core Document

Authority: Core Source of Truth

Role in this package: **Tier 4 (Specialized Standards) document.** This is the single authoritative source for mobile technical architecture, frameworks, state management, offline strategy, and per-app module breakdown. `Master Development Instruction` Section 18 and `Product Specification Requirement` Sections 30–31 cross-reference this document rather than duplicating it.

---

## Purpose

Define the complete enterprise mobile application architecture, standards, development guidelines, security, offline capabilities, deployment strategy, and integration rules for the SBGlobal Plus platform.

## Scope

Applies to:

- 🆕 Tenant Staff App
- 🆕 Tenant User/Customer App
- 🆕 Super Admin App
- Future Enterprise Apps

## Supported Platforms

- Android
- iOS
- Future: Web App (PWA)

## Framework

- Flutter (Latest Stable)

## Language

- Dart

## Architecture

- Clean Architecture
- Feature Based Architecture
- Repository Pattern
- Service Layer
- Dependency Injection
- MVVM Compatible
- Offline First
- API First
- Multi Tenant

## State Management

- Riverpod (Default)
- Future Support: Bloc, Cubit

## Local Storage

- SQLite
- Hive
- Secure Storage
- Shared Preferences

## Cache

- API Cache
- Image Cache
- Configuration Cache
- Offline Cache

## Network

- REST API
- JSON
- HTTPS
- JWT
- Multipart Upload
- Retry Mechanism

## Background Services

- Background Sync
- Auto Retry
- Queue Processing
- Offline Upload

## Offline Strategy

- Offline First Architecture
- Local Queue Management
- Automatic Conflict Resolution
- Incremental Synchronization
- Sync Retry Policy

## Notifications

- Firebase Cloud Messaging (FCM)
- Push Notification
- Local Notification
- SMS Trigger
- WhatsApp Trigger
- Email Trigger

## Authentication

- OTP Login
- JWT
- Refresh Token
- Biometric Login
- Fingerprint
- Face ID
- Device Binding
- Session Management
- Multi-Factor Authentication (MFA) Support
- 🆕 Enterprise SSO / OAuth 2.0 / OIDC (Tenant Staff App)

## Security

- Tenant Isolation
- Encrypted Storage
- SSL Pinning
- Certificate Validation
- API Encryption
- Token Expiry
- Logout All Devices
- Root/Jailbreak Detection

## QR & Barcode

- QR Scanner
- Barcode Scanner
- Patient QR
- Report QR
- Invoice QR
- Sample Barcode

## Device Features

- Camera
- Gallery
- GPS
- Bluetooth
- Microphone
- File Picker
- PDF Viewer
- Printer Support
- Share
- Deep Linking

## 🆕 Vertical Suite Note

🆕 The application modules below (Tenant User/Customer App Modules, Tenant Staff App Modules) and the Patient QR/Sample Barcode items in QR & Barcode reflect Healthcare & Diagnostics Vertical Suite functionality — this platform's flagship, fully built-out vertical. The architectural framework defined elsewhere in this document (Framework, State Management, Local Storage, Network, Security, Offline Strategy, etc.) is Core Platform-wide and applies identically across all supported Industry Vertical Suites.

## 🆕 Tenant User/Customer App Modules

- Dashboard
- Appointments
- Lab Booking
- Reports
- Invoices
- Payments
- Medical History
- Prescription
- Notifications
- AI Assistant
- Profile

## 🆕 Tenant Staff App Modules

🆕 > Serves Doctor, Pathologist, Technician, Receptionist, Collection Staff, Billing Executive, Lab Admin, and other internal tenant roles via Role-Based Access Control (RBAC). See Product Specification Requirement — Section 12.

- Dashboard
- Patients
- Appointments
- Reports
- Prescription
- AI Summary
- Digital Signature
- Notifications
- Calendar
- Sample Collection
- Barcode Scan
- QR Scan
- Worklist
- Result Entry
- Pending Tests
- Machine Status
- Offline Sync

## 🆕 Super Admin App Modules

- Dashboard
- Revenue
- Analytics
- Users
- Branches
- Doctors
- Patients
- Approvals
- Reports
- Notifications

## Supported AI Providers

> **Canonical, platform-wide list owned by `SBGlobal_Plus_AI_Architecture_Standards.md` — Supported AI Providers (authoritative).** It applies identically to mobile apps; do not maintain a separate list in this document.

## AI Features

> Selected subset of the platform-wide AI Capabilities list (full list: see AI Architecture Standards) that surfaces specifically in the mobile apps:

- AI Chat
- AI Copilot
- AI Search
- AI OCR
- AI Report Summary
- AI Recommendations
- Voice Assistant
- AI Notification Generator

## Performance

- Lazy Loading
- Image Compression
- Background Processing
- Pagination
- Infinite Scroll
- Code Splitting

## Observability

- Crash Reporting
- Performance Monitoring
- Analytics Events

## Accessibility

- Dark Mode
- Light Mode
- Large Fonts
- Screen Reader
- High Contrast
- Offline Support

## Multi Tenant

- Tenant Isolation
- Branch Isolation
- Role Based Access
- Feature Flags
- White Label Support

## Testing

- Unit Test
- Widget Test
- Integration Test
- API Test
- Performance Test
- Security Test

## Deployment

- Google Play Store
- Apple App Store
- Enterprise APK
- MDM Support

## Update Strategy

- In-App Update Support
- Minimum Supported Version Policy
- Force Update Support

## CI/CD

- GitHub Actions
- Codemagic
- Fastlane

## Versioning

- Semantic Versioning
- Backward Compatibility Policy

---

END OF DOCUMENT

