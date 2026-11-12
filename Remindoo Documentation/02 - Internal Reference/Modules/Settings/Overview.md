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

**Status:** Partially written — Settings-side of Service Templates documented; Clients and Tasks sides pending.
