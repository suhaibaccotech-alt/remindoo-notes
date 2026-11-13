# Known Issues & Limitations

**Purpose:** A running list of known issues, limitations, and things to be aware of across the app. Newest first. Card keys link to Jira.

## Seen in the documentation walk-through, 13 Nov 2026
Preprod, signed in as Michael Eldred Clark. Not carded.

| Area | Issue |
| --- | --- |
| Invoices | Xero Integration tab: Last sync "Failed: QSTASH_TARGET_URL_INVOICE_SYNC_PAGE not configured", and the Contacts sub-tab shows "Internal server error" |
| Settings | MCP access is on Integrations as "AI Assistant Access" and Security is on Edit Own Profile, so the 10 Nov "can't be reached" finding (SCRUM-971, SCRUM-1208) may be a naming change, not a missing page. Worth a recheck in Tenant 1 |
| Automations | Rules whose email template was deleted stay Active ("Deleted template — choose another") |
| Tasks | Progress still shows "0hof 12.2h" (missing space); Status Change still "Not updated yet" |
| Tasks | Recurring task "test a rec" (Daily) shows Refresh at 23/10/2026 (same symptom as SCRUM-1113) |
| Clients | New-client wizard: leaving after step 1 (name and type) keeps nothing; a draft only exists once the correspondence step is saved |
| Proposals | The proposal wizard creates the draft on the first Next, before any pricing is added |
| Dashboard | Timesheet, Leads, Proposals and Client Summary tabs opened on a single past day (22 Sept → 22 Sept 2026) |
| Inbox | "Synced at" was two days old (11/11/2026 05:00) on opening |

### Later the same day, as Test User in Tenant 1
| Area | Issue |
| --- | --- |
| Leads | Convert to Client takes roughly 20–30 s on "Converting lead to client..." with the dialog still open |
| Clients | Resuming onboarding at Contacts still shows an empty "Manage your contacts" screen with no way forward (first seen 3 Nov) |
| Clients | Add service → Assign Team Members: Save Assignees with nobody selected does nothing and gives no message |
| Clients | A client can be finalised (made Active) with no contact and no service |
| Clients | The onboarding URL's `step` stays `services` on the Risk Assessment and Internal Information steps |
| Leads | Create Lead: a typed mobile or email is ignored until + is clicked; the hint only appears after pressing Next |

## Found in QA on preprod, 6–12 Nov 2026
| Area | Issue | Card |
| --- | --- | --- |
| Invoices | Preview offers "Bank transfer — see details below" but prints no bank details | SCRUM-1161 (failed 12 Nov) |
| Invoices | Paid and Partial invoices show Paid £0.00 and the full amount as Remaining | SCRUM-1508 |
| Invoices | No Refund action on a paid invoice (row, edit view or preview); a "Payment Refunded" template exists | SCRUM-1093 (failed 11 Nov) |
| Invoices | "Void invoice" opens a "Delete Invoice" dialog ("Type Delete to confirm") | SCRUM-1350 (noted again 12 Nov) |
| Invoices | The invoice information modal has no link to the invoice itself | SCRUM-1385 (unclear) |
| Clients | Outstanding invoices modal shows only "Not found in Stripe" for direct debit, and stopped listing WILLY WONKA's overdue INV-055 | SCRUM-1302 (failed 10 Nov) |
| Tasks | Recurring tasks don't refresh ("QA Recurring 1113 Daily" stuck at Refresh at 04/11/2026) | SCRUM-1113 (In Progress) |
| Tasks | On the All view the Complete and Archived chips show 0 while Kanban shows the real counts | SCRUM-1171 (In Progress) |
| Tasks | The task's own view doesn't show what the client owes overall | SCRUM-901 (failed 10 Nov) |
| Tasks | No "Filed" indicator on a task at "Filed Externally" | SCRUM-1083 (failed 10 Nov) |
| Tasks | Status Change column says "Not updated yet" on every task | none yet |
| Tasks, Leads, Clients | Three different colour schemes for action buttons | SCRUM-1360 (failed 10 Nov) |
| Email | Inbox → Compose sends unresolved ::tokens:: as written, with no warning | SCRUM-1129 (failed 12 Nov) |
| Email | Compose: "Reply sent!" toast for a new email; the next Compose keeps the last subject and recipient; Send needs two clicks | noted on SCRUM-1129 |
| Email | The inbox doesn't sync on its own ("Synced at" unchanged for two hours until Refresh) | none yet |
| Leads | An email sent from the lead's Conversation only appears after a reload; "Expand composer to full section" at about 1,060 px hides the conversation and composer | none yet |
| Leads | The Conversation-tab composer has no Preview, and templates show raw ::tokens:: there | none yet |
| Proposals | "Edit Proposal" on a draft opens under the Create New Proposal title and URL (`/proposals/create-new`) | told Abdur Rehman, 12 Nov |
| Proposals | Document name isn't saved separately from the document | SCRUM-532 (failed 6 Nov) |
| Proposals | Unsaved Changes dialog on an unchanged template | SCRUM-1419 |
| Proposals | Signature is about twice as tall in Preview as in the editor | SCRUM-1420 |
| Proposals | At 1280 px the Variables and Header & Footer buttons cover the Pricing Table and Packages buttons | SCRUM-1421 |
| Proposals | Picking a template replaces the open document and its name without asking | SCRUM-1422 |
| Proposals | Initials (and new Headings) can land on top of other elements | SCRUM-1278, SCRUM-1070 |
| Proposals | Existing templates still show "Fee/Month"; only new pricing tables say "Fee" | SCRUM-1252 (note) |
| Proposals | Word (.docx) import isn't available; PDF only | SCRUM-1081 (Not Started) |
| Automations | Fit View does nothing; Zoom In overshoots (about 149–167%) | SCRUM-1185 (failed 12 Nov) |
| Automations | Rules have no names, and "See how this rule runs" is a diagram, not a run log | SCRUM-1130 (failed 9 Nov) |
| Settings | Security and MCP Access can't be reached since the Integrations page was split out | SCRUM-971, SCRUM-1208 |
| Settings | Dashboard History shows year-first dates under a DD/MM/YYYY tenant; currency picker is GBP/EUR/USD only | SCRUM-1383 (failed 10 Nov) |
| Settings | Integrations and Invoices → Payments have disagreed on GoCardless and PayPal ("Coming Soon" vs "Connect") | SCRUM-911, SCRUM-800 (Not Pushed) |
| Calendar | An event created before Google was connected doesn't sync; no "no Gmail" confirmation; Google Meet ticked by default | SCRUM-959 |
| Dashboard | Total Hours counts archived employees (12,600 = 7 × 1,800, 4 of the 7 archived) | SCRUM-287 (question) |
| App-wide | "What's new" label is "What's new", not "New in Remindoo"; preprod's 06/11 entry is raw server log lines | SCRUM-1376 (failed 10 Nov) |
| App-wide | Preprod can be slow: one Tasks table load took 42 s on 12 Nov (usually 2.5–6 s) | none yet |

## Found in QA on preprod, 5 Nov 2026
| Area | Issue | Card |
| --- | --- | --- |
| Tasks | Due Amount and the task Invoices tab show only invoices linked to the task, not the client's outstanding balance | SCRUM-901 (failed QA) |
| Tasks | No latest-action dates under the task modal's action buttons; no Next Step or Next Page | SCRUM-1285 (failed QA) |
| Tasks | The "All" tab count leaves out Complete, Archived and Snooze | none yet |
| Tasks | Progress display "0hof 1h" is missing a space | none yet |
| Clients | Outstanding invoices modal leaves out partly paid invoices | proposed update to SCRUM-815 |
| Clients | No direct debit status in the outstanding invoices modal | SCRUM-1302 (not on preprod) |
| Invoices | Status disagrees with paid amount (Paid with balance remaining; Partial with £0 paid) | proposed |
| Email | /emails never loads when no mailbox is connected | proposed |
| Dashboard | Tabs open on last week; Capacity Planning cards disagree | proposed |
| Leads | Very long status names push the status tabs over three rows | proposed (Low) |
| Settings | Edit Own Profile shows "Employee not found" for the Test User account | question to Suhaib |
| App-wide | Profile pictures 404: the S3 URL is prefixed with the preprod domain | known since 2 Nov |
| Documents | Folder sizes show "-", so the storage total can't be checked against files | SCRUM-943 (question) |
| Proposals | Document Builder: the properties panel covers the page; AR's 4 Nov UI fixes aren't on preprod yet | AR's list |

## Test-tenant limitations (affect QA, not users)
- No HMRC authorisation, no 3CX, no AI provider, AML balance £0. Cards needing these are tested by hand. A Gmail mailbox and Google Calendar (suhaib.accotech@gmail.com) were connected in Tenant 1 on 12 Nov; FreeAgent and Stripe are connected.
- The Test User account has no employee record, so it can't be assigned tasks (creating a task is blocked for it).
- A Tasks automation ("Complete → Send Email", template "tasks tokens") is active in Tenant 1, so completing a task there sends an email.
- Employees use yopmail addresses, so QA doesn't trigger anything that emails them.

**Status:** Started 5 Nov 2026, updated 13 Nov 2026. Card statuses are as of the QA run that found them; check Jira for the current state.
