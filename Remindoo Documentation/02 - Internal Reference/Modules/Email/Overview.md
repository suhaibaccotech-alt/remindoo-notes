# Email — Overview (internal)

- One shared compose window for Tasks ("Send Email to 1 task"), Leads ("Send Email to 1 lead", with Send from linked account or Create campaign) and Invoices ("Send Email to Client"). Each has Select Email Template, Recipients, Subject, BCC, a TinyMCE body, Attach files and Adjustable Tokens, plus **Preview Email** (yellow) beside **Send** (SCRUM-1366).
- Preview behaviour: tokens resolved from the record; an empty value renders blank; an unknown token stays as typed (e.g. ::Not A Token::); the payment link renders as a "Pay Invoice" button; the recipient is shown.
- Test tenant: "From: No connected accounts". **/emails never finishes loading** with no mailbox (spinner over 20 s, twice). Proposed card for Zain. This blocks QA of SCRUM-1205 and SCRUM-1206.
- Task Email Logs: one log's Subject column shows an email address (possibly the subject field holding the address).

## Changes seen 6–12 Nov 2026
- With Gmail connected (Tenant 1, 12 Nov): folders Inbox, Unread, Starred, Archived, Complete, Sent, Spam, Trash all load; sync works (SCRUM-1307) but only on Refresh, not on its own.
- Inbox → Compose doesn't check tokens: raw ::tokens:: are sent (SCRUM-1129). The task email Preview says unfilled merge fields "are listed when you send", so a check exists there but not in Compose.
- Compose quirks: "Reply sent!" toast for a new email; the next Compose keeps the previous subject and recipient; the first click on Send does nothing.
- AI Suggestion without a provider shows "AI Provider not configured or not active for this tenant".
- Template dropdowns group templates under module headings (Calendar, Leads, …) (SCRUM-1276).
- Two-way email composer on lead, client, task and proposal Conversation tabs (SCRUM-910, 960, 961, 1091, 1092). Only the lead one was sent from.
- With no mailbox, the Inbox page stays on "Loading..." (still true 10 Nov).

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA runs.
