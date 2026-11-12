# Clients — Overview (internal)

**Purpose:** Functional notes on **Clients** for the team.

- Tabs: Active, Archive, Frozen, Draft (onboarding in progress; resume at a step via /clients/clients-on-boarding?resume_client_id=…&step=…).
- Toolbar buttons (aria labels): New Client, Import Clients, Company House Sync, AML Verification Sessions, **Check HMRC authorisation requests**, Column visibility, Filters, Saved filter views.
- About 95 columns, including every service custom field plus Status Changed At, Archived At, Invoices, Contact fields and test custom fields. There's a per-column filter on most (e.g. **Filter HMRC Authorisation**, the closest thing to the SCRUM-1300 "unauthorised clients" view).
- **Invoices column** → "Outstanding invoices – <client>" modal: Total Due, Overdue, Invoices count, list. **Partly paid invoices seem to be left out** (WILLY WONKA LIMITED: £120 shown; the Invoices list has £162 incl. INV-136 £42 Partial, overdue). Proposed as an update to SCRUM-815. No direct debit status in this modal (SCRUM-1302: not on preprod, 5 Nov).
- Quick view shows services with frequency, truncated with no tooltip (see SCRUM-1348 QA, 3 Nov).
- Two client records can share a name (e.g. "WILLY WONKA LIMITED" and "WILLY WONKA LIMITED (08674020)"); invoices show the company number suffix for the second.

## Changes seen 6–12 Nov 2026
- Profile sections: Basic Information, Contacts, Services, Internal Information, Risk & AML, Client Portal Management, E-Signatures, Conversation. There are no "Documents" or "Timeline" sections.
- Access depends on the role's Clients permissions (7 of them). With 0/7 the sidebar item disappears and /clients shows "Access denied – You don't have permission to view clients." (seen on every Tenant 1 role on 9 Nov; Admin was then restored to 7/7).
- Search with one match shows one page, "Showing 1 of 1" (SCRUM-1190). The Services section shows a skeleton only while loading (SCRUM-1016).
- Export: "Export selected clients to CSV" appears once a row is ticked; "Exported 2 clients to CSV." (SCRUM-1221, SCRUM-1525).
- New-client wizard: step 1 is the client type (e.g. Self-Employed), then Basic Information; later steps include Contacts, Services and Risk Assessment. Known bug (3 Nov): resuming at the Contacts step shows an empty "Manage your contacts" screen with no Next button.
- Outstanding invoices modal: direct debit shows only "Not found in Stripe" (SCRUM-1302).
- Digital AML verification emails failed to send on production for weeks (SCRUM-1518); confirmed sending again on 11 Nov.
- Risk Assessment & AML page: no Proof of Address warning opens on its own (SCRUM-1068).

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA runs.
