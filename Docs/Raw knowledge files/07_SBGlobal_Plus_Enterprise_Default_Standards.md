# SBGlobal Plus Enterprise Default Standards

Version: 1.0

Role in this package: **Tier 4 (Specialized Standards / Design Tokens) document.** This is the authoritative source for default brand tokens, typography defaults, layout defaults, portal/module default configuration, master-dropdown seed data, and system defaults. The base UI **scale** (spacing scale, border-radius named scale, animation timing, status color mapping) is owned by `SBGlobal_Plus_Enterprise_UI_Design_System.md`; this document applies that scale as product defaults rather than redefining it. The authoritative, complete **User Types** list is owned by `Product Specification Requirement` — Section 5.

---

## Product Name

SBGlobal Plus

## Tagline

🆕 AI-Powered Enterprise Intelligence. One Core. Unlimited Possibilities.

## 🆕 Organization Information

- 🆕 Organization: SBGlobal Plus Pvt Ltd.
- 🆕 Founder / CEO: Mr. Jal Singh Yadav
- 🆕 Address: 2835/1, Swatantra Nagar, Madhya Pradesh, India – 477001
- 🆕 Email: info@sbglobalplus.com

## Default Brand Colors

- Primary: `#0F766E`
- Primary Hover: `#115E59`
- Secondary: `#2563EB`
- Accent: `#06B6D4`
- Success: `#16A34A`
- Warning: `#F59E0B`
- Danger: `#DC2626`
- Info: `#0284C7`

### Background

- White: `#FFFFFF`
- Gray: `#F8FAFC`
- Sidebar: `#0F172A`
- Card: `#FFFFFF`

### Text

- Heading: `#0F172A`
- Body: `#475569`
- Muted: `#64748B`
- Border: `#E2E8F0`

## Typography

- Primary Font: Inter
- Secondary Font: Poppins
- Report Font: Roboto
- Invoice Font: Inter
- PDF Font: Roboto

### Font Weight

- Regular: 400
- Medium: 500
- SemiBold: 600
- Bold: 700

### Font Size

- H1: 36px
- H2: 30px
- H3: 24px
- H4: 20px
- H5: 18px
- Body: 16px
- Small: 14px
- Extra Small: 12px
- Table: 14px
- Sidebar: 15px
- Button: 14px
- Input: 14px

## Border Radius

- Card: 12px
- Button: 10px
- Input: 8px

> These are semantic product defaults. Base named scale: see Enterprise UI Design System — Border Radius (Small 6px / Medium 8px / Large 12px / XL 16px / Round 999px). Button 10px is an intentional product-specific value between Medium and Large; this is not a conflict with the base scale.

## Spacing

> Full spacing scale: see Enterprise UI Design System — Spacing Scale (authoritative: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96). Default Standards applies this scale as-is; no separate scale is maintained here.

## Shadow

- Card: `0 2 8 rgba(0,0,0,.08)`
- Popup: `0 8 30 rgba(0,0,0,.15)`

## Default Layout

- Top Navbar
- Left Fixed Sidebar
- Sticky Header
- Scrollable Content
- Rounded Cards
- Light Theme Default
- Dark Theme Optional

### Animation

> See Enterprise UI Design System — Default Animation (authoritative: Fade / Slide / Zoom, Duration 200ms). Applied platform-wide as-is.

## Default Website

- Container: 1320px
- Hero Height: 700px
- Section Padding: 100px
- Button Radius: 10px
- Icon Size: 22px
- Hero CTA: Start Free Trial, Login, Get Demo

## 🆕 Vertical Suite Note

🆕 The following sections — Tenant Web Portal, LIS Module, Invoice Default, and Report Default — define Healthcare & Diagnostics Vertical Suite defaults specifically. General layout, typography, table, and form defaults elsewhere in this document are Core Platform-wide.

## 🆕 Tenant Web Portal

🆕 > Serves every tenant-side role (Lab Admin, Doctor, Pathologist, Technician, Receptionist, Patient, and others) through a single unified web experience, scoped by Role-Based Access Control (RBAC). See Product Specification Requirement — Section 12.

- Reports
- Notifications

### 🆕 Dashboard & Analytics

- KPI Cards: Revenue, Patients, Doctors, Reports, Pending Samples, Collections
- Revenue Graph
- Quick Actions
- Recent Activity
- Calendar
- Todo
- Top Tests
- Top Branches

### 🆕 Patient-Facing Modules

- Appointments
- Invoices
- Payments
- Medical History
- Download PDF
- QR Verification
- AI Summary
- Profile

### 🆕 Doctor-Facing Modules

- Patients
- Pending Review
- AI Insights
- Digital Signature
- Follow Up
- Prescription

## LIS Module

- Patient Registration
- Appointment
- Billing
- Sample Collection
- Barcode
- QR
- Sample Tracking
- Worklist
- Machine Integration
- Result Entry
- Verification
- Approval
- Report
- Dispatch
- Archive

## Invoice Default

- A4 Portrait
- Logo Top Left
- QR Top Right
- Invoice Number
- Patient Details
- Doctor
- Test Table
- GST
- Discount
- Grand Total
- Terms
- Digital Signature

## Report Default

- A4 Portrait
- Logo
- Patient Information
- Doctor
- Collection Date
- Report Date
- Parameter Table
- Reference Range
- Flag
- Trend Graph
- AI Summary
- Pathologist Signature
- QR Verification
- Footer

## Table Settings

- Row Height: 48px
- Header Height: 52px
- Pagination: 10 / 25 / 50 / 100
- Sticky Header
- Resizable Columns
- Column Picker
- Search
- Export: CSV, Excel, PDF
- Print
- Bulk Actions

> Component-level table capability list (sorting, filtering, sticky column, table actions): see Enterprise UI Design System — Tables / Table Actions.

## Form Settings

- Required (`*`)
- Auto Save
- Autocomplete
- Input Mask
- Date Picker
- Validation
- Draft Save
- Audit Log

## Master Dropdowns

> This is the **default seed list** applied at installation. For the complete enterprise master-data catalogue and category breakdown, see Product Specification Requirement — Section 10A. For build-tracking volume targets (e.g., 250+ masters, 1000+ dropdown values), see Enterprise Development Roadmap — Phase 03/04.

- Session
- Country
- State
- District
- City
- Language
- Currency
- Gender
- Blood Group
- Religion
- Category
- Department
- Designation
- Role
- Branch
- Doctor
- Patient Status
- Appointment Status
- Sample Status
- Report Status
- Invoice Status
- Payment Status
- Test Category
- Test
- Package
- Specimen
- Container
- Method
- Machine
- Vendor
- Manufacturer
- Tax
- Discount
- Shift
- Holiday
- Priority
- Severity

## Session Format

- 2026-2027
- 2027-2028
- 2028-2029
- Automatically Generate
- Current Session Default

## Master Data Table (Standard Columns)

- UUID
- Code
- Name
- Description
- Status
- Sort Order
- Tenant ID
- Created By
- Created At
- Updated By
- Updated At
- Deleted By
- Deleted At

## Setting Modules

- General
- Branding
- Theme
- Typography
- Localization
- Session
- Company
- Branches
- Departments
- Users
- Roles
- Permissions
- Master Data
- LIS
- Billing
- Inventory
- Communication
- Email
- SMS
- WhatsApp
- Storage
- Payment Gateway
- API
- AI
- Security
- Backup
- Logs
- Audit
- CMS
- Website
- 🆕 Tenant Portal Settings
- Reports
- Invoice
- Notifications
- Integrations
- Subscription
- Feature Flags

## Default Status

> Canonical status values. Status-to-color mapping for badges: see Enterprise UI Design System — Default Status Colors.

- Active
- Inactive
- Draft
- Pending
- Approved
- Rejected
- Completed
- Cancelled
- Deleted

## Default User Role Seeds

> **Authoritative complete list: see Product Specification Requirement — Section 5 (User Types).** The roles below are only the default subset pre-seeded at installation:

- Super Admin
- Tenant Owner
- Lab Admin
- Branch Manager
- Doctor
- Pathologist
- Receptionist
- Technician
- Collection Staff
- Billing Executive
- Accountant
- Patient
- API User

🆕 > Doctor, Pathologist, Collection Staff, and Patient reflect Healthcare & Diagnostics Vertical role defaults. Other supported Industry Vertical Suites will receive their own default role seed sets as they are built out.

## System Defaults

- Timezone: Asia/Kolkata
- Date Format: dd-MM-yyyy
- Time Format: Configurable (12/24 Hour)
- Default Currency: INR (Configurable per Tenant)
- Default Language: English
- Secondary Language: Hindi
- Additional Languages: Configurable (Per Tenant)
- OTP Login: Enabled
- 2FA: Optional
- Audit Log: Enabled
- Soft Delete: Enabled
- UUID: Enabled
- Multi Tenant: Enabled
- API First: Enabled
- White Label: Enabled
- Dark Mode: Supported
- AI Features: Enabled
- Feature Flags: Enabled

---

END OF ENTERPRISE DEFAULT STANDARDS
