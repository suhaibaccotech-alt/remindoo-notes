# Leads — Overview

**Purpose:** What the **Leads** module is for, who uses it, and what you can do with it.

Leads holds prospective clients before they sign up. Sales and partners use it to track enquiries, send emails and proposals, and convert a lead into a client.

## The Leads page
- **Status tabs** with counts: All, In-Progress, Not Responding, Archived, Converted to Client, New Lead, plus any custom statuses your firm adds in **Settings → Lead Settings** (e.g. Warm, Wants-to-talk).
- **New Lead**, **Show Kanban View**, column visibility, filters and saved filters.
- Columns include Lead Name (with its latest activity), Date of Creation, Assignees, Email, Source (e.g. Manual, Website, Xero, QuickBooks, Sage, FreeAgent), Status, Address, City, Postal Code, Country, Turnover, Estimated Value and your custom fields.
- **Activities & Actions** tiles on each row: Two Way Communication, Call Logs, Notes, Proposals and Tasks, each with the date it last happened.

## Working with a lead
Clicking a lead opens a summary (email, status, postcode, lead handler, country, phone, website, notes) with actions:
**Go to Lead Profile**, **Edit Lead Profile**, **Create Proposal**, **Update Lead Status**, **Send Lead Email**, **Add Timeline Note**, **Dial Call** and **Delete Lead**.

## The lead profile
**Go to Lead Profile** opens the full record, with **Convert to Client**, **Add Timeline Note**, **Edit Lead** and **Delete Lead** at the top, and four tabs:
- **Tasks**: tasks for this lead, with **Create New Task**. Each task can be expanded, edited or have a reminder email sent.
- **Proposals**: every proposal for the lead with its status, and **Create Proposal**.
- **Contacts**: the people at the lead, with **Create Contact**. One contact should be marked as the **Primary Contact**.
- **Conversation**: emails, email logs and lead activity in one feed, filtered by **Email** or **Activity**. Emails are marked *One way* or *Two way*. The composer at the bottom writes to the lead (template, subject, recipients, BCC, tokens, attachments).

Beside the tabs: **Leads Info / Custom Fields** (the lead's details), **Primary Contact Info**, **Attachments** (**Upload document**) and **Quick Access** shortcuts (Create Proposal, Create Task, Add Notes, Import Contact, Send New Email).

## Filtering leads
Click a status tab to show one status, or use the **funnel** icon to filter by fields such as **Status**, **Source** and **Assignees** (the assignee picker lists employees by name). Filters can be saved, as on every table.

## Custom lead fields
Extra fields for leads are set up in **Settings → Lead Settings → Custom Fields**, where you name each field, pick its type and can make it compulsory. The same page has **Custom Statuses**, **Round Robin Selection** (sharing new leads out between staff) and the **Lead Capture Form**.

## Emailing a lead
**Send Lead Email** lets you:
- **Send from linked account** (your connected mailbox), or **Create campaign** to queue the email for several leads.
- Use lead tokens such as ::Lead Name::, ::Lead Phone Number:: and ::Company Number::.
- Click **Preview Email** to see the email with the lead's details filled in before you send.

**Status:** First draft (5 Nov 2026), updated 13 Nov 2026 from a preprod walk-through. See [Workflows](Workflows.md).

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
