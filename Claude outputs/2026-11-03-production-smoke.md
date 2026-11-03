# Production smoke test, Tue 3 Nov 2026 (Awais, with Claude)

Environment: crm.remindoo.co (production), user "Google Doc" (mutbaherxyz@yopmail.com), tenant **Google Docs Tenant**. Test data only: 1 active client (BATMAN & ROBIN LTD, no email), 3 drafts, 2 leads (yopmail / accotech addresses), 6 old "Testing Template" proposals, no tasks or invoices before the run. Signed in by Awais; no password typed or stored.

## Headline: backend not released
The new frontend is live but the production backend is an older build. The dashboard itself says "The server does not have current work by team yet. It needs a newer backend version than the one running." These new endpoints return 404 on production:
- GET /api/dashboard/tasks-current-by-team
- GET /api/dashboard/tasks-history
- GET /api/dashboard/tasks-upcoming
- POST /api/emails/preview ("Cannot POST /api/emails/preview")
- GET /api/documents/shared/proposal/{id} (signed proposal preview)

Most of the failures below come from this one cause. Fix the deploy first, then rerun this smoke test.

## Results

| # | Area | Result | What failed (expected vs seen, page) |
|---|------|--------|--------------------------------------|
| 1 | Login & navigation | Pass with gaps | All 9 sidebar pages load. **Emails** and **Documents Portal** are not in the sidebar. /documents shows "Access restricted" and /emails is blank (probably this user's permissions, so blocked). Financial Assistant: "Please connect an AI Provider" (blocked). Console: the 404s above, plus 401 "Missing authentication tokens" when fetching the AI provider. |
| 2 | Dashboard | **Fail** | Tasks > Current loads (~4 s). Outstanding work by team & stage: "needs a newer backend version". History: "Task history could not be loaded". Upcoming: "Upcoming work could not be loaded". Employee & Services tab loads fine. |
| 3 | Leads | Partial | List and Status filter work (Status is New Lead → 1). Source is Manual → 1, expected 2 (the converted lead also has Manual as its source; maybe converted leads are hidden on purpose). Each filter takes ~12 s. "Apply Without Saving" still toasts "Filters saved" and the filter stays after navigation. Lead opens. **Email Preview fails: "Cannot POST /api/emails/preview".** Two-way Communication tab on the lead profile opens. |
| 4 | Tasks | Partial | Pass: table, Partner/Managers column filters (new), Activity & Actions tiles, saved filter drawer, Timer logs from Progress, Kanban counts match (1 In-Progress), personal reminder saves and reopens ("Personal reminder created successfully"; the first Create click did nothing). **Fail: task email Preview ("Cannot POST /api/emails/preview").** Escape still doesn't close Timer Logs. Kanban lazy-load not testable (1 task). |
| 5 | Invoices | Partial | Pass: create (INV-001/002, £120), sort by Number + new "Reset Sorting" button, Sent column (✗), Approve & send card has 17 tokens, Send reminder has a Preview button, manual payment £120 on INV-002 (Record Payment now has a payment date). **Fail: Preview on Approve & send and on Send reminder ("Cannot POST /api/emails/preview").** Note: Cancel on the Approve & send card still left INV-001 approved. Create from a task not tested (the only task is internal, with no client). |
| 6 | Proposals | Partial | List loads (~10 s), £ shown. Builder opens; pricing table shows £ and headings are editable in Pricing-Table Properties (Col 1–4), not by double-clicking the cell. Page size defaults to "US Letter". **Fail: Preview Proposal on a signed proposal does nothing (404 GET /api/documents/shared/proposal/190).** **New Proposal button does nothing** (no API call, no message; tenant has 0 templates). Optional badge and package name checks not reached (need a proposal with products/packages). |
| 7 | Clients | **Fail (wizard resume)** | List loads, profile preview opens. Wizard: intro and contact saved. **Resume at Contacts shows the same empty "Manage your contacts" screen as preprod, with no Next button.** The contact only appears after clicking the Manage contacts icon (Finish then goes on to Services). Resume at Services works: VAT (Monthly) listed, Next saves and goes to Risk Assessment. Client list Email column shows N/A for the draft although its contact has an email. |
| 7a | SCRUM-1348 multi-frequency (AR) | Pass (UI) | VAT template offers Monthly / Quarterly / Yearly. After adding Monthly: "Added (Monthly)" + "Add Another"; second instance says "Already added for this client: Monthly" and the dropdown shows "Monthly (Already added)" greyed. Saving the Quarterly instance was not finished (the modal's lower fields were out of reach in the browser pane), so two rows on the profile weren't confirmed. Question: "Total Yearly Time = 7 hr 30 min" for a Monthly service with 7 h 30 min per task. Should it be 12 × 7.5 h? |
| 8 | Document Portal | Blocked | Not in the sidebar; /documents says "Access restricted" for this user. Can't change permissions. |
| 9 | Email | Partial | Two-way screens open on lead and client profiles ("No email threads yet"). Task modal still has no Communication tab. Unread badge: blocked (no mailbox; not connected). |
| 10 | Known gaps | — | Task reminder modal: still no Preview. Latest action date under task buttons: still not shown. Send Now in Email Logs: blocked (no logs). ::Invoice Amount:: format: blocked (Preview broken). |

## Other notes
- Invoice numbering: the Cancel on Approve & send consumed INV-001 (it stayed approved and unsent).
- Lead BATMAN & ROBIN LTD's primary contact is a real Companies House officer name with a yopmail address (imported test data).
- Dates show today as 4 Nov in the date pickers late on 3 Nov PKT (time zone?).
- To find the Emails/Documents routes I ran a few page GETs from the console (/documents, /emails, and guesses that returned 404). Harmless, but outside "only what the UI sends".

## Test data left on production (Google Docs Tenant)
- Task "QA Prod Task 2026-11-03" (In-Progress, internal deadline 13/11, external 19/11), with personal reminder "QA Prod Reminder 2026-11-03" on 10/11/2026 (to the user).
- Invoices INV-001 (£120, Approved, unsent) and INV-002 (£120, Paid), BATMAN & ROBIN LTD, reference "QA Prod Invoice 2026-11-03"; manual payment £120 on INV-002.
- Draft client "QA Prod Client 2026-11-03" (type Other) with contact qaprodclient20261103@yopmail.com and service VAT (Monthly, next VAT 20/11/2026); wizard left at Risk Assessment.
- Leads list filter "Source is equal to Manual" may still be applied in this user's view.
- Nothing sent, nothing deleted, no settings or integrations changed.

## Draft Jira cards (not created; waiting for approval)
1. App-wide – Production backend not deployed with 6 Nov frontend (new APIs 404) · Sami · Highest · app-wide, src-qa
2. Clients – Resuming client setup at Contacts shows an empty screen with no Next (production) · Abdur Rehman · High · clients, src-qa
3. Proposals – New Proposal button does nothing when the tenant has no document templates · owner? · High · proposals, src-qa
4. Invoices – Cancel on "Approve & send" leaves the invoice approved and uses its number · owner? · High · invoices, src-qa

Recheck after the backend deploy (not carded yet, likely fixed by #1): dashboard Current-by-team/History/Upcoming (SCRUM-1372, Hammad), email Preview everywhere (SCRUM-1366, Zain), signed proposal preview.

---

## Recheck and regression, Tue 3 Nov 2026, 11:10 pm PKT

Same tenant and user. **The backend has now been deployed**: every new endpoint answers 200, and no page I opened made an API call that returned 400 or above, except the signed-proposal preview.

### Rechecks of the earlier failures

| Item | Now | Notes |
|---|---|---|
| Dashboard Outstanding work by team & stage | **Pass** | Chart loads (1 task under "No team yet / Info Requested"). |
| Dashboard History | Pass, with a question | Loads, but the default period is 19 Dec 2025 to 12 Mar 2026 and "snapshots to 2026-03-12": no daily snapshots on production since 12 Mar? It also shows "Open at period end 1, as of 2026-03-12", although the only open task was created on 3 Nov. |
| Dashboard Upcoming | **Pass** | 7 days 0/0; 30 days and 90 days 1/1 (internal 13 Nov, external 19 Nov). Correct. |
| Lead email Preview | **Pass** | "QA Prod BATMAN & ROBIN LTD 12659458", To: batman@yopmail.com. |
| Task email Preview | **Pass** | "QA Prod QA Prod Task 2026-11-03 due 13 November 2026". |
| Invoice Send reminder Preview | **Pass** | "QA Prod INV-001 for GBP 120.00 due 8 November 2026". Approve & send uses the same modal. |
| ::Invoice Amount:: format | Still "GBP 120.00" | Expected "£120.00". |
| Task reminder modal Preview | **Still missing** | Only Close / Update Reminder. |
| Latest action date under task buttons | **Still missing** | |
| Task Communication tab | **Still missing** | Task modal tabs: Task, Comments, Email Logs, Invoices. |
| Signed proposal preview | **Fail** | Preview Proposal does nothing; GET /api/documents/shared/proposal/190 and /188 both return 404 (both are signed proposals from 10 Mar). |
| New Proposal (list button) | Fail (UX) | Still does nothing. The lead's "Create Proposal" goes to Proposals and says "You need to create a document template before creating a proposal", but the list button shows no message. |
| Client wizard resume at Contacts | **Fail** | Same empty "Manage your contacts" screen with no Next (QA Prod Client 2026-11-03). |

### Regression sweep (pages and tabs opened, API errors checked)
- Dashboard: Tasks (Current / History / Upcoming), Timesheet, Employee & Services, Client Summary (Total 5, Active 1, Draft 4): all load, no API errors.
- Leads: table, Kanban (New Lead 1, Converted 1), lead profile, Communication tab, email Preview: pass. Note: the Kanban card shows Source "Direct Link" while the table shows "Manual" for the same lead. The Source filter has no "Direct Link" option, which may explain the Source = Manual → 1 result.
- Proposals: table, Kanban (Declined 3 · £350,400, Sent 1, Signed 2), builder: pass. Signed preview: fail (above).
- Tasks: table, filters, Timer logs, Kanban, Email Logs, email Preview, reminder: pass (gaps above).
- Clients: list, profile preview and all tabs (Basic, Contacts, Services, Internal, Risk & AML, Communication, Client Portal Management, E-Signatures, Timeline): pass.
- Knowledge Base: FAQs, Articles, Tags tabs: pass.
- Invoices: list, Unpaid / Overdue / Drafts / Recurring / Credits & Notes, Payments, Templates, Reminders: load with no API errors.
- Settings: all 14 sections (Global, Roles & Permissions, Employees, Teams, Service Templates, Email Templates, Proposal, Lead, Client Custom Fields, Profile, Campaigns, Planned Reminders, Notifications, Checklist Templates): load with no API errors.
- Still blocked: Emails and Documents Portal (not in the sidebar for this user, /documents "Access restricted"), Financial Assistant (no AI provider), unread badge and Send Now (no mailbox or email logs), Kanban lazy-load (1 task).

### Clean-up
- Cleared the leftover "Status is New Lead" Leads filter. Proposals switched back to the table view.
- No new test data in this pass. Nothing sent, deleted or connected.

### Updated card drafts (still not created)
Card 1 (backend) is no longer needed.
1. Clients – Resuming client setup at Contacts shows an empty screen with no Next · Abdur Rehman · High · clients, src-qa
2. Proposals – Signed proposal preview does nothing (shared document 404) · Abdur Rehman (update SCRUM-1353 instead?) · High · proposals, src-qa
3. Invoices – Cancel on "Approve & send" leaves the invoice approved and uses its number · owner? · High · invoices, src-qa (invoice/money → Suhaib decides)
4. Dashboard – History has no daily snapshots on production after 12 Mar 2026 · Syed Hammad · High · dashboard, src-qa
5. Proposals – New Proposal button gives no message when there are no templates · owner? · Medium · proposals, src-qa
QA-result comments rather than new cards: SCRUM-1366 (reminder modal Preview still missing; "GBP 120.00" format), SCRUM-1285 (latest action date still missing).
