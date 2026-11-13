# Settings — Overview

**Purpose:** Technical and functional overview of the Settings module: what it does, how it fits into the wider Remindoo architecture, key data entities, and how it's built.

## Subsections

### Service Templates
The origin point of the **Service Templates** feature, which spans Settings, Clients, and Tasks. A Service Template is the reusable blueprint ("cast") from which actual services and tasks are created on client profiles.

- Full field-by-field spec: [Workflows.md](Workflows.md)
- End-to-end cross-module feature page: [Service Templates](../../Features/Service%20Templates.md)

### Roles & Permissions
Per-role permission counts overall and per module (Tenant 1, 9 Nov: Admin 79/79; Employee, "1" and Test 66/79 with Clients 0/7). A module with 0 permissions is hidden from the sidebar and its route shows "Access denied". See [Roles & Permissions.md](Roles%20&%20Permissions.md) (not yet written).

### Page structure on preprod (6–12 Nov 2026)
- **Global Settings** tabs: Tenant Information, Email Settings, Other Settings (was "Date & Currency"; holds the auto-invoice switch). Old links to removed tabs redirect.
- **Integrations** is its own Settings page (SCRUM-971): HMRC, AI, and payment providers (GoCardless and PayPal "Coming Soon" until 11 Nov, "Connect" on 12 Nov), among others. 3CX isn't listed in Tenant 1. Security and MCP Access aren't reachable from either page (SCRUM-971 failed QA 10 Nov; SCRUM-1208 blocked).
- **Automations** lives under Settings.
- Planned Reminders has Select all (SCRUM-1088) and a Personal Task Reminders section (empty in Tenant 1).
- Opening `/settings` directly once sent the browser to the login page (6 Nov).

### Routes and page contents (walk-through, 13 Nov 2026)
| Page | Route | Notes |
| --- | --- | --- |
| Global Settings | `/settings/globalSettings?tab=tenant-information` / `email-settings` / `other-settings` | Email Settings has Email Composer (Header, Footer, Send Test Email) and Other. Other Settings: auto-create invoice on signed proposal, currency (locked once proposals exist), date format (5 options), time format. |
| Roles & Permissions | `/settings/rolesPermissions` | 80 permissions in total. Modules: Dashboard 14, Clients 7, Tasks 10, Leads 9, Knowledge Base 2, Proposals 3, Document Portal 2, Invoices 11, Calendar 1, Email 3, WhatsApp 5, Settings 13. Dashboard is per tab with Data Visibility and Export CSV. Create Role, Expand All. |
| Employee List | `/settings/employeeList` | New User, card view, filter, column visibility. |
| Teams | `/settings/teams` | Create New Team, Edit, Delete. |
| Services Templates & Reminders | `/settings/serviceAndReminders` | All / Active / Inactive counts. Columns: Service Name, Type, Status, Trigger Date, Estimated Time, Task Templates, Subtask Templates, Reminders, Checklist. Built-in services (🔒) have Edit but no Delete. Create and Import. |
| Email Templates | `/settings/emailTemplate` | Categories: Clients, Leads, Proposals, Invoices, Tasks. Create, Import, bulk select. |
| Proposal Settings | `/settings/proposalSetting` | Tabs: Categories, Variables, Ranges, Products, Packages. Categories mirror client types. |
| Lead Settings | `/settings/lead?tab=customFields` | Tabs: Custom Fields, Custom Statuses, Round Robin Selection, Lead Capture Form. |
| Client Custom Fields | `/settings/clientSettings` | Groups: Basic Information, Internal Information, Contacts. Per field: Compulsory, Visible in Clients Table, Client Type count, Field Type, Options. Set as Default. |
| Edit Own Profile | `/settings/profile` | Profile Info, Security, AI access tokens. |
| Campaign Management | `/settings/campaign_management?type=client` | Clients, Leads, Employees. |
| Planned Reminders | `/settings/reminder_management` | Services and Personal Task Reminders; columns include Recipients, BCC, Status, Finished At, Error Log. |
| Notification Management | `/settings/notification_settings` | Groups: Task & Subtask (15 types), Lead (10), Document (2), Calendar (2, with Popup), WhatsApp (1). In-App and Email per type; Email is N/A for some. |
| Checklist Templates | `/settings/checklistTemplates` | |
| Automations | `/settings/automations` | See Automations. |
| Integrations | `/settings/integration` | AI Account, AI Assistant Access (MCP clients), HMRC, Email, AI Calling Agent, Xero, QuickBooks, Sage, FreeAgent, Go Cardless, Adfin, Stripe, PayPal, WhatsApp, Invoco (Coming Soon). MCP access now lives here as **AI Assistant Access**; Security is on Edit Own Profile. |

**Status:** Partially written. Service Templates documented in full; page inventory added 13 Nov 2026 from a preprod walk-through.
