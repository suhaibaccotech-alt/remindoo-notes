# Clients — Overview (internal)

**Purpose:** Functional notes on **Clients** for the team.

- Tabs: Active, Archive, Frozen, Draft (onboarding in progress; resume at a step via /clients/clients-on-boarding?resume_client_id=…&step=…).
- Toolbar buttons (aria labels): New Client, Import Clients, Company House Sync, AML Verification Sessions, **Check HMRC authorisation requests**, Column visibility, Filters, Saved filter views.
- About 95 columns, including every service custom field plus Status Changed At, Archived At, Invoices, Contact fields and test custom fields. There's a per-column filter on most (e.g. **Filter HMRC Authorisation**, the closest thing to the SCRUM-1300 "unauthorised clients" view).
- **Invoices column** → "Outstanding invoices – <client>" modal: Total Due, Overdue, Invoices count, list. **Partly paid invoices seem to be left out** (WILLY WONKA LIMITED: £120 shown; the Invoices list has £162 incl. INV-136 £42 Partial, overdue). Proposed as an update to SCRUM-815. No direct debit status in this modal (SCRUM-1302: not on preprod, 5 Nov).
- Quick view shows services with frequency, truncated with no tooltip (see SCRUM-1348 QA, 3 Nov).
- Two client records can share a name (e.g. "WILLY WONKA LIMITED" and "WILLY WONKA LIMITED (08674020)"); invoices show the company number suffix for the second.

**Status:** First draft (5 Nov 2026).
