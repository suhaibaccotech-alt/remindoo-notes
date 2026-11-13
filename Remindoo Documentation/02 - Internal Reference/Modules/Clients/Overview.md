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

## Walk-through, 13 Nov 2026
- New-client wizard at `/clients/clients-on-boarding`: step 1 "Welcome to Client Creation" (Client Name, Type, Import from Companies House); step 2 "<Type> <name> Correspondence" with built-in and custom fields (compulsory ones set in Client Custom Fields). **No draft is created by step 1 alone**; the earlier note that step 1 saves refers to saving the Basic Information step.
- The profile opens as an overlay on `/clients` ("Preview of <client>", "Overview CH"), not a separate route. Sections: Basic Information, Contacts, Services, Internal Information, Risk Assessment & AML (tabs Risk Assessment, Digital AML Verification), Client Portal Management, E-Signatures ("Client Portal Documents", grouped by task), Conversation (Email / Activity).
- Basic Information and Contacts have Basic Fields / Additional Fields and Edit All.
- Services table columns: Services, Pending Tasks, Frequency, Assignees, Additional Info, Tax Liabilities, Client Authorisation, Reminders, Estimate; Pause per service; "Total Yearly Time". **Add Services** → "Manage Services For <client>": each template shows "This service will create n subtasks and m preset reminders" with Add / Add Another / Already Added ("Added (Daily)").
- Risk Assessment: 16 yes/no questions producing "AML Risk Assessment: Low Risk", with Save.
- Conversation activity entries: Basic Information Edited (old and new value), Service Added, Document Sent, Document Signed, Email Linked.
- Table row buttons: unread emails (opens Communication), document folder, signed e-sign documents, pending tasks, invoices ("Invoice summary").
- Not walked: Companies House sync, AML verification send, HMRC authorisation.

## Onboarding wizard end to end (Tenant 1 as Test User, 13 Nov 2026)
- Resume: Draft client quick view → **Complete your onboarding** → dialog listing Introduction, Contacts, Services, Risk Assessment & AML, Internal Information as Complete / Incomplete ("suggested next step"), with "Start from beginning" and "Continue onboarding".
- Route: `/clients/clients-on-boarding?resume_client_id=<id>&step=<introduction|contacts|services>`. **The `step` param stays `services` through Risk Assessment and Internal Information.**
- Contacts on resume: still the empty "Manage your contacts" screen with only Go back (bug first seen 3 Nov).
- Services: Add Services → Manage Services (Add / Not Allowed / Already Added / Add Another, "will create n subtasks and m preset reminders"). Add → frequency, estimated time (validation "Estimated time must be at least 1 minute"), the template's custom fields with the trigger date compulsory, and a live count ("Based on your current selection, n task(s) will be created"; it showed 1 before a date was chosen and 0 with a trigger date a week ahead). Next → Assign Team Members (All / Partner / Service Manager / Assignee; Teams / Employees; UNLOCK; Save Assignees). **Save with nobody selected does nothing and shows no message.** Not saved in the walk-through, to avoid notifying the test employees.
- Services step → Next works with no services ("Client information saved successfully").
- Risk Assessment: one question per screen (No / Yes, question jump buttons, View Past Questions, Digital AML), then a summary with a toggle per answer and Save & Continue → "AML answers saved successfully".
- Internal Information, page 1: Previous Accountant switch, Client Source Type (Existing Client, Facebook, Google, Website) and Relation, both compulsory. Page 2: Payment (DD - Go Cardless [Recommended], DD - By Client, SO - By Client, No Work - Always Ask for Advance, Late Payer - but Pays, No payment - F&F, Payment on Invoice - Good Payer, Other), Google Review, Yearly Fee - Ex VAT, all compulsory. Finish → "Client finalised successfully", back to `/clients`, client now Active.
- **A client can be finalised with no contact and no service.**

**Status:** First draft (5 Nov 2026), onboarding walked end to end 13 Nov 2026.
