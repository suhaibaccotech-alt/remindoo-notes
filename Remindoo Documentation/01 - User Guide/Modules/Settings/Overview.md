# Settings — Overview

**Purpose:** What the Settings module is for, who uses it, and what you can accomplish with it as a Remindoo user. High-level orientation before diving into workflows.

## Subsections

### Service Templates
Where your firm builds reusable service blueprints once, so the same service (and its tasks) doesn't need to be set up from scratch on every client. See [Workflows.md](Workflows.md) for how to build one, and [Service Templates](../../Features/Service%20Templates.md) for the full picture of how a template turns into real client tasks.

### Roles & Permissions
See [Roles & Permissions.md](Roles%20&%20Permissions.md).

## All Settings pages (as of 5 Nov 2026)
Settings opens a list of pages; click **Show Details** on one to open it.
1. **Global Settings**: firm-wide details, in tabs: Tenant Information, Email Settings, HMRC, Security, AI, MCP Access, Integrations, 3CX Calling.
2. **Employee Roles & Permissions**: what each role can see and do.
3. **Employee List**: add and manage employees (name, email, status, role).
4. **Teams**: group employees into teams.
5. **Services Templates & Reminders**: service blueprints, their tasks, subtasks and reminders (see above).
6. **Email Templates**: reusable emails for anywhere in the app.
7. **Proposal Settings**: proposal templates, defaults and approval rules.
8. **Lead Settings**: how leads are captured, categorised and assigned, including custom lead statuses.
9. **Client Custom Fields**: extra fields on client records.
10. **Edit Own Profile**: your photo, name, phone, 3CX extension, LinkedIn, two-step sign-in (MFA) and AI access tokens.
11. **Campaign Management**: email campaigns.
12. **Planned Reminders**: all scheduled reminders in one place.
13. **Notification Management**: how you're notified about activity.
14. **Checklist Templates**: reusable checklists.
15. **Automations**: rules that act on leads, proposals, tasks, clients and services.

## What changed on preprod, 6–12 Nov 2026
- **Global Settings** is now three tabs: **Tenant Information**, **Email Settings** and **Other Settings** (date and currency formats, and the switch that raises an invoice automatically when a proposal is signed).
- A separate **Integrations** page now holds connections that used to be Global Settings tabs, including **HMRC**, the **AI** provider and payment providers (GoCardless and PayPal were shown as "Coming Soon" until 11 Nov and as **Connect** on 12 Nov).
- **Security** and **MCP Access** couldn't be found on either page during testing.
- **Automations** is reached from Settings. See [Automations](../Automations/Overview.md).
- **Planned Reminders** has **Select all** for acting on several reminders at once, and a **Personal Task Reminders** section.

*Source: observed on preprod, 5 Nov 2026, and the QA run reports of 6–12 Nov 2026.*

**Status:** Partially written — Settings-side of Service Templates documented; Clients and Tasks sides pending.
