# Leads — Overview (internal)

**Purpose:** Functional notes on **Leads** for the team.

- Table: 33 leads in Tenant 1; it can take about 10 s to fill. Status chips filter by status. The filter dialog opens with the user's last saved conditions (SCRUM-1163, On-Hold); its Assignee picker lists employees by name (SCRUM-1524).
- Custom lead statuses with very long names stretch the status chip bar (test data in Tenant 1).
- Lead preview shows the latest activity. The lead profile's history is under **Conversation**; there's no tab called "Activity" or "Timeline".
- **Notes:** saved from the Conversation tab's Notes composer; shown at once and after reload (SCRUM-1526).
- **Email, two ways to send:**
  - *Send Lead Email* modal: shared compose window with Preview Email (tokens resolved from the lead).
  - *Conversation composer:* two-way email through the connected mailbox (SCRUM-910, SCRUM-1091). "Email sent successfully!", then a "TWO WAY" thread, visible only after a reload. No Preview here, and templates show raw ::tokens::. Reply threading isn't verified.
- Custom fields: Settings → Lead Settings, with a card-width type selector (SCRUM-1188).

**Not verified by QA:** creating a lead, converting a lead to a client, campaigns, Kanban.

## Walk-through, 13 Nov 2026
- Routes: `/leads`, lead profile `/leads/<id>`.
- **Create Lead** modal: steps Basic Information, Contacts, Information & Attachments (the later steps unlock after Next). Compulsory: Lead Name, Mobile no., Lead Email, plus compulsory custom fields. "Enter Additional Details" adds Company Number, Lead Type, Assignment Type (Round-Robin: "The system will determine an assignee for this lead at the end of this onboarding"), Turnover, Business Website, Country, City, Address, Postal Code, Tags. Import from Companies House. Save & Exit / Next.
- Quick view actions: Go to Lead Profile, Edit Lead Profile, Create Proposal, Update Lead Status, Send Lead Email, Add Timeline Note, Dial Call, Delete Lead.
- Profile: header actions Convert to Client, Add Timeline Note, Edit Lead, Delete Lead; side panel Leads Info / Custom Fields; tabs Tasks, Proposals, Contacts, Conversation; Primary Contact Info; Attachments; Quick Access.
- Conversation feed entries are tagged ONE WAY or TWO WAY; filters Email and Activity.
- Table row tiles: Two Way Communication, Call Logs, Notes, Proposals, Tasks.
- Not walked: saving a lead, Contacts and Attachments steps, Convert to Client (the tenant has an active New Lead → Send Email automation).

**Status:** First draft (12 Nov 2026), updated 13 Nov 2026 from a preprod walk-through.
