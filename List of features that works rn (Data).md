
2026-11-13-preprod-regression.md

`# Regression smoke, Fri 13 Nov 2026, 2:20–2:50 pm (asked for in chat)`

``Checklist: `Remindoo Documentation/QA/Regression checklist.md`, all 11 areas. Smoke test for breakage, not a re-test of every card.``

`## Environment`

``- Preprod `https://preprod-crm.remindoo.co`, built-in browser on at-45, viewport 1440×900.``

`- **Test User, Document Testing Tenant 1** (tenant name confirmed in Global Settings).`

`- Scope agreed in chat: regression smoke of every module, report only (no Jira comments, cards or Command Center writes), QA test data allowed, no budget cap.`

`Tally: **24 pass, 2 fail, 1 blocked, 1 not checked.**`

`## Fails`

`1. **Tasks – table chips don't match Kanban (SCRUM-1171, still failing).** On the All view the table chips read All 97, Not started 75, In-Progress 20, Awaiting Feedback 2, **Complete 0, Archived 0**. Kanban shows the same first three and **Complete 3, Archived 2**.`

`2. **Recurring tasks don't refresh (SCRUM-1113, still failing).** "QA Recurring 1113 Daily" (daily, started 03/11) still shows Refresh at **04/11/2026**. The two Weekdays rules still show 23/10/2026.`

`Both were already failing on 9 Nov. Nothing new broke in this run.`

`## Results by area`

`| Area | Check | Result |`

`| --- | --- | --- |`

`| Sign-in & nav | Dashboard loads; Clients, Leads, Tasks, Invoices, Proposals, Automations, Settings open. Inbox, Calendar, Documents Portal and Knowledge Base also open | Pass |`

`| | Console | See "Console" below |`

`| | Profile pictures | Pass (no broken images on the dashboard or Knowledge Base) |`

`| Clients | Table loads (9 active); search "Test" → 3 results; sort Name A→Z and Z→A | Pass |`

`| | Client "Test" opens: quick view, then Basic Information, Contacts, Services, Internal Information, Risk Assessment & AML, Client Portal Management, E-Signatures, Conversation (with the Activity timeline) | Pass. There are still no sections called "Documents" or "Timeline"; the checklist wording is out of date |`

`| | New-client wizard saves step 1 ("QA Regression client 13 Nov", Self-Employed) and moves to Basic Information | Pass |`

`| | Client "Test" Services: VAT Monthly and VAT Quarterly as separate rows | Pass |`

`| | "Export selected clients to CSV" | Not checked: the button appears when a client is selected, but it wasn't clicked because it downloads a file |`

`| Leads | Table loads (34). Source is Manual → 34, all Manual. Status chip In-Progress → 2 of 2. Source Manual + Status New Lead → 0, which matches the "New Lead 0" chip | Pass |`

`| | Lead profile (QA Full Lead 12 Nov) opens; Conversation shows its events (lead added, edited, note, proposal created and sent) | Pass |`

`| | Preview Email in the Send Lead Email modal: "Hello ::Lead Name::" previewed as "Hello QA Full Lead 12 Nov". Nothing was sent | Pass |`

`| Tasks | Table loads (97); In-Progress chip → 20; saved filter "QA Low priority" → 3 | Pass |`

`| | Kanban counts match the table | **Fail** (see 1) |`

`| | Task modal opens (Task, Conversation, Invoices tabs). Progress status change on "QA DashB Due later" saved and survived a reload, then set back to Info Requested. Timer Logs popup opens | Pass |`

`| | "QA Recurring 1113 Daily" refreshed | **Fail** (see 2) |`

`| | Create and complete "QA Regression task" | **Blocked**: Test User has no employee record and the other employees use yopmail addresses, so nothing can be assigned. Completing a task would also fire the active "Complete → Send Email" rule, which emails another user (shown as "ZU") |`

`| Dashboard | Tasks tab loads in under 5 s. Team is QA Team A: Info Requested 93 → 23, grid shows only QA Team A and Cross-team | Pass |`

`| | Card vs list: Internal Overdue 21 → 21 rows; At Risk 4 → 4 rows | Pass |`

`| Invoices | List loads (82); sort by Amount descending is in order | Pass |`

`| | Preview of INV-055 shows Document Testing Tenant 1 seller details | Pass |`

`| | Raise invoice from task "Test - 03-09-26": contact WILLY WONKA LIMITED and the task line are prefilled ("From task: Test - 03-09-26"). Cancelled, not saved | Pass |`

`| | Record Payment opens on INV-055. Cancelled, not saved | Pass |`

`| Proposals | List loads (13); Document Templates → "New Document" opens in the builder; pricing table renders | Pass |`

`| Automations | List loads. Leads: 1 rule, paused. Tasks: "Complete → 1 day → Not started" paused | Pass |`

`| | The paused Tasks rule opens on the canvas. Cancelled, not saved | Pass |`

`| Email | Invoice Reminders tab shows its 17 tokens | Pass |`

`| Settings | Service templates list (13); VAT shows Monthly, Quarterly, Yearly ticked | Pass |`

`| | Teams list shows QA Team A and QA Team B | Pass |`

`| Document portal | Storage 472.6 MB / 3 GB (15.38%) | Pass |`

`## Console`

`- On the first page load after sign-in: one 401 and "Error updating auth: Auth update failed". The app carried on normally.`

``- The known 3CX WebSocket errors (`threecx-calling/ws` failed) repeat on every page: 70+ in this session.``

`- One 500 response while moving through Documents, Inbox, Calendar and Knowledge Base. The request wasn't identified; the pages themselves rendered.`

`## Changed since earlier runs`

`- Record Payment now has a Payment Date field (it was missing on 2 Nov, SCRUM-1162).`

`- Raise invoice is now reachable from the Tasks table row (not found on 9 Nov). The task modal's Invoices tab still has no Raise invoice button.`

`- Proposal prices show "£2.30" (yesterday "£2.3").`

`- The paused Tasks rule reads "1 days" (yesterday the day count was blank).`

`- A progress status change now shows in the table straight away (on 3 Nov it needed a reload).`

`## Other things noticed`

`- **The Tasks rule "Complete → Immediately → Send Email" is still active** and sends to another user (shown as "ZU"; on 9 Nov it was Zain and Hammad). It isn't a QA rule. While it's on, no run can complete a task on Tenant 1.`

`- Preprod is still sending invoice reminder emails by itself: INV-055's audit timeline shows reminders on 5, 7, 9 and 11 Nov. This contact uses your Gmail, but other invoices' contacts may not.`

`- Inbox says "Synced at 13/11/2026 05:00" at 2:45 pm (same as yesterday's bug 18).`

`- Leads: a filter applied with "Apply Without Saving" is still there after leaving the page and coming back (known since 2 Nov).`

`- Dashboard filter dialog: Escape closes the whole dialog and drops the conditions without asking. On the task modal, Escape does nothing.`

`- Proposal builder: opening the "New Document" template shows "Page 1 of 21" and an "Unsaved changes found" prompt for a local draft from 12 Nov. Neither Discard nor Restore was pressed.`

`- Clients: with the search "Test" active, clicking Sort Name Z→A didn't reorder the 3 results within 4 seconds. After the search was cleared the Z→A order was applied. Worth one check by hand.`

`- The Complete and Archived chips on the Tasks table read 0 even on the All view, and "All 97" leaves those 5 tasks out (part of fail 1).`

`## Test data left on preprod`

`- Draft client **"QA Regression client 13 Nov"** (Self-Employed), left at the Basic Information step.`

`- "QA DashB Due later": progress status changed to Info Received - Reminders Off and back to Info Requested (two progress-status changes today).`

`- Leads filter and dashboard filter were both cleared afterwards. The saved leads conditions (Source is Manual, Status is New Lead) are still in the filter dialog.`

`- Nothing was sent, saved on an invoice, approved, deleted or connected.`

`## Follow-up, 3:15–3:50 pm: the four open items`

`Run in **Document Testing Tenant 2 as Michael Eldred Clark**, because that was the account signed in for this part. Yesterday's bugs were found in Tenant 1, so a recheck here shows whether each one is general, not whether the Tenant 1 record is fixed.`

`### 1. Create and complete a task: Pass`

`- "QA Regression task 13 Nov" created from Custom Task (Quick Task), assigned to Michael Eldred Clark, deadlines 20 and 27 Nov. "Created successfully".`

`- Setting it to Complete while progress was "Info Requested" was refused with "Unable to mark task as Complete" (expected). After progress was changed to "Info Received - Reminders Off", Complete saved and the task shows under the Complete chip.`

`- Tenant 2's only Tasks automation fires on "Queries Raised with Client", so nothing was triggered.`

`- Same SCRUM-1171 symptom here: once complete, the task left the All view and the All view's Complete chip stayed at 0.`

`- After creating the task, the table didn't show it and the count stayed at 5652 until I searched for it.`

`### 2. Clients search + sort: Pass (earlier doubt not reproduced)`

`Search "maddy" → 2 results. A→Z gave "maddy pvt 2, maddy pvt ltd"; Z→A reversed them. The 2:25 pm oddity in Tenant 1 was most likely my click not registering.`

`### 3. Export selected clients to CSV: Pass`

`Selecting one client and pressing Export opens an "Export columns" chooser; Export CSV then downloaded a file with a header row and one client row (about 3 KB, columns Name, Assignees, Partners, Service Managers, Email, …). This also covers SCRUM-1221 for a single client. The file is in the laptop's downloads.`

`### 4. Yesterday's 23 bugs`

`**Still happening (13)**`

`| # | Bug | Seen today |`

`| --- | --- | --- |`

`| 1 | SA Register Date lost | Entered 03/11/2026; the profile shows 13/11/2026, which is the LOE Signed Date's value |`

`| 2 | Dates save a day early | Incorporation entered 01/11/2026 shows 31/10/2026. Commenced entered 02/11/2026 also shows 31/10/2026 |`

`| 3 | Turnover lost | 12500 entered; no Turnover field under Basic or Additional fields |`

`| 4 | Personal UTR accepts letters | "abcdefghij" saved and shown on the profile |`

`| 5 | Email shows N/A in the clients table | Still N/A for QA Full Client 12 Nov (Tenant 1, seen at 2:25 pm) |`

`| 6 | Notes shows literal "N/A" in edit mode | Yes, on the new client |`

`| 9 | Knowledge Base article not saved | Partly: the first Save did nothing and showed no message; a second Save saved it (Draft 1 → 2). The word counter read "0 words" until the editor lost focus, so the first click probably saw empty content |`

`| 14 | Checklist template shows "n / n completed" | "3 / 3 completed" on the Email template |`

`| 16 | Calendar flashes "No connected email" on load | Yes, for about 3 seconds, then "Google 2-way sync active" |`

`| 18 | Inbox doesn't sync on open | Tenant 2 says "Synced at 11/11/2026 05:00" at 3:49 pm on 13 Nov; Tenant 1 said 13/11 05:00 at 2:45 pm |`

`| 19 | Edit Lead on a profile says "Lead data not found." | Yes, on a lead created minutes earlier (id 1319). So it's new leads in general, not one record |`

`| 20 | Leads table header shows through dialogs | Yes: the "Lead Name" header cell and its checkbox stay bright behind Create Lead |`

`| 22 | Lead status name has no length limit | The name input still has no limit. I didn't save a long name to confirm the server side |`

`**Not reproduced, looks fixed (5)**`

`- 12 Create Email Template: Save is on screen at 1440×900.`

`- 13 Automations: the paused rule reads "1 days".`

`- 17 Invoice summary cards: no overlap at 1440 wide in either tenant. Yesterday's run may have been at a narrower width.`

`- 21 Contact area code: a new contact shows "United Kingdom | +44".`

`- 23 Proposal totals: all prices in both tenants show two decimals.`

`**Not rechecked (5)**`

`- 7 Services step (needs an assignee choice inside the wizard) and 8 the minor onboarding items.`

`- 10 Knowledge Base preview close.`

`- 11 Edit Own Profile: Tenant 1 only, because Michael has an employee record.`

`- 15 Calendar notification close button: needs another event written to your real Google Calendar.`

`### New things noticed in Tenant 2`

`- **A wizard-stage draft client isn't in the Clients table.** "QA Recheck Client 13 Nov" is found by the top search bar and labelled Draft, but the Draft tab lists only one other client and a table search for "QA Recheck" finds nothing under Active or Draft.`

`- The first click on the Draft chip highlighted it but the list stayed on the 11 active clients; a second click filtered.`

`- Onboarding: the "Personal UTR" switch is labelled "Toggle Company UTR" for screen readers, and "Registered In" came back as "England & Wales" although it was left blank.`

`- Invoices took more than 9 seconds to get past the loading skeleton.`

`- Console: "Supabase sign-out failed: supabaseUrl is required" and "What's new popup: couldn't load new updates, couldn't reach the server".`

`### Test data left in Tenant 2`

`- Task "QA Regression task 13 Nov" (Complete, assigned to Michael Eldred Clark, so the app may have notified that account's own login address).`

`- Draft client "QA Recheck Client 13 Nov" (company "QA Recheck Co"), wizard left at Contacts.`

`- Lead "QA Recheck Lead 13 Nov" (id 1319) with contact "QA Recheck Contact". Both use your Gmail and a fictional 07700 900123 number.`

`- Knowledge Base draft "QA Recheck Article 13 Nov".`

`- Nothing was deleted, sent or approved. The Clients table and Tasks table may still hold my last search text.`

`## Not covered by this run`

`The checklist is a smoke test. Not exercised today: client import, portal invites, Digital AML, proposal sending and signing, invoice approve/send/void/payments, accounting integrations, users/roles/permissions, 3CX, WhatsApp, the Super Admin area and the client portal.`


2026-11-13-retest-ar-zain-looms.md

`# Retest of AR's and Zain's bug lists and this week's Looms, Fri 13 Nov 2026, 5:45–6:10 pm (asked for in chat) — PART 1, run not finished`

`## Environment`

``- Preprod `https://preprod-crm.remindoo.co`, built-in browser on **AT95** (Suhaib overrode the "no browser testing on AT95" rule for this session), viewport 1440×900.``

`- **Test User, Document Testing Tenant 1** (tenant name confirmed in Global Settings before testing).`

`- Scope agreed in chat: the bugs DM'd to Abdur Rehman (17) and Zain (5) today, the five Loom transcripts, and the fails and untested items in the "Links & Messages" note. Report in the project and QA lines in the note; no Jira comments, no DMs.`

`- **The run stopped early.** The browser connection started failing at about 6:05 pm, part-way through Zain's list. Everything below is what was seen before that. "Not retested yet" means I hadn't reached it.`

`- Several items were first found in Tenant 2. A result here in Tenant 1 shows whether the bug is general, not whether the Tenant 2 record is fixed.`

`Tally so far: **still failing 15, pass or looks fixed 5, works in Tenant 1 only 2, not built 1, not retested yet 9.**`

`## 1. Abdur Rehman's list (17 items)`

`Tested with a new client, "QA Retest Client 13 Nov PM" (Self-Employed), created through the wizard.`

`| # | Bug | Result | Seen today |`

`| --- | --- | --- | --- |`

`| 1 | SA Register Date is lost | **Still failing** | Entered 03/11/2026; the profile shows "Not provided" and the field is empty in Edit All |`

`| 2 | Commenced Date saves a day early | **Still failing** | Entered 02/11/2026; the profile shows 01/11/2026 |`

`| 3 | Turnover is lost | **Still failing** | Entered 12500; no Turnover under Basic Fields or Additional Fields |`

`| 4 | Personal UTR accepts letters | **Still failing** | "qwertyuiop" was accepted and saved. New since yesterday: a duplicate check ("This UTR already exists for QA Full Client 12 Nov") when I reused "abcdefghij". The contact step still doesn't prefill the contact UTR |`

`| 5 | Services step: can't save without an assignee; Accounts template 0 mins | **Still failing (first part)** | In Add Services → Assign Team Members, Save Assignees is greyed out with nobody selected. The Accounts template still lists "0 mins"; I didn't re-submit that form |`

`| 6 | Heading overlaps "Import from Companies House"; Next needs a second click | **Not reproduced** | At 1440 wide the heading wraps to two lines and clears the link. Next worked on the first click |`

`| 7 | Email shows N/A in the clients table | **Still failing** | QA Full Client 12 Nov still shows N/A in the Email column |`

`| 8 | Notes prefilled with literal "N/A" in Edit All | **Still failing** | Yes, on the new client |`

`| 9 | AI Summary in the quick view does nothing | **Still failing** | Client "Test": clicking AI Summary gives no summary and no message (Tenant 1 has no AI provider) |`

`| 10 | Create Email Template: Save below the screen at 900 px | **Pass** | Save sits at 751–783 px of 900 |`

`| 11 | Proposal total shown as "£2.3" | **Pass** | All 15 prices on the Proposals page have two decimals ("£2.30") |`

`| 12 | Frequency dropdown shown when there is only one option | **Still failing** | Client "Test" → Add Services → "Accounts - Year End + CT600": Frequency dropdown is there with Yearly preselected |`

`| 13 | Tagging someone doesn't update Mentions | **Not retested yet** | |`

`| 14 | Role user counts don't match Employee List | **Matches in Tenant 1** | Roles page: Admin 6 users. Employee List: 6 active, all Admin. Tenant 2 (where it failed) not rechecked |`

`| 15 | No toggles on compulsory custom fields in Additional Fields | **Not settled** | Tenant 1's only additional field ("Test") shows a toggle. In Settings → Client Custom Fields, Compulsory is still a Yes/No dropdown. The Tenant 2 field "test now" wasn't rechecked |`

`| 16 | Service Templates search doesn't filter while typing | **Still failing** | Typing "test" left all 13 listed; Enter filtered to 5 |`

`| 17 | Team editor doesn't offer employees who aren't in a team | **Works in Tenant 1** | Edit QA Team B: 1 unassigned employee plus 5 under "Assigned in Other Teams", which is all 6 active employees. Tenant 2 not rechecked |`

`## 2. Zain's list (5 items)`

`| # | Bug | Result | Seen today |`

`| --- | --- | --- | --- |`

`| 1 | Edit Lead on the lead profile says "Lead data not found." | **Not retested yet** | Lead 1317's profile opened; the browser dropped as I clicked Edit Lead |`

`| 2 | Leads table header shows through dialogs | **Still failing (likely)** | With the lead quick view open, the header row (Lead Name, Status, Address) stays bright over the dimmed page. Create Lead dialog not rechecked |`

`| 3 | Contact area code becomes "Unknown \| +44" | **Not retested yet** | |`

`| 4 | Lead status name has no length limit | **Not retested yet** | The 980-character status from yesterday is still in the status tabs |`

`| 5 | Inbox doesn't sync on open | **Not retested yet** | |`

`## 3. Loom transcripts`

`**Service & Reminders (12 Nov, CEO)**`

`- Sorting: every column has sort arrows. **Pass.**`

`- Active/Inactive: All 13 / Active 13 / Inactive 0 tabs, and a status menu on each row. Setting "Test Service A" to Inactive and back worked ("Service template set to Inactive."). **Pass.**`

`- "Missing authentication token": **not reproduced** on search or on a status change in Tenant 1.`

`- Search while typing: **still failing** (item 16 above).`

`- Deleting "Test": **not tested**; the QA rules don't allow deleting.`

`**Task timeline, Document Signed (12 Nov, SCRUM-1572):** not retested yet.`

`**CIS Contractor / remaining hours and subtask reassignment (10 Nov, 2:16)**`

`- Remaining hours in Assign Team Members: **not built.** The Teams and Employees tabs show names only, with no allocated or remaining hours.`

`- Reassigning a task should also reassign its subtasks, with a checkbox: not retested yet.`

`**Review call (10 Nov, 26:42)** — most of it is the Clients table rebuild (SCRUM-1541, Waiting for Requirements), which isn't on preprod. The parts that can be checked now:`

`- Client Custom Fields should autosave: **still failing.** Changing "Visible in Clients Table" shows a small save icon on that row; without clicking it the change is gone after a reload. There is no Save Changes button.`

`- A field set to visible should appear in Column Visibility: **Pass** once the row is saved ("Google Review" appeared). I didn't check that it pulls data.`

`- Dropdown fields should be dropdowns in Filters: **still failing.** "Test Dropdown 1" gives a free-text Value box.`

`- Page length: tenant page length is 100. The Clients table (10) and Client Custom Fields (19) both fit on one page, so there aren't enough rows in Tenant 1 to prove it.`

`- Leads "All" shouldn't show Converted: **still failing.** All lists 35, of which 33 are Converted To Client.`

`- Average Hours empty: N/A for all 10 active clients.`

`- "Filed externally" note on tasks, signed e-sign items turning green, close icons on popups: not retested yet.`

`**Clients / GoCardless (9 Nov)**`

`- A "GoCardless Direct Debit" column exists and shows "Not connected" for every client; "Stripe Direct Debit" shows "Not found in Stripe". Mandate statuses and the logo can't be checked without a connected GoCardless account.`

`- Dropdown filter and page length: as above.`

`## 4. Links & Messages note: fails and untested items`

`- Single-option Frequency dropdown: **still failing** (item 12).`

`- Mentions, Document Signed timeline, archive reason: not retested yet.`

`- Service & Reminders Loom and the 10 Nov Looms: now tested in part, see section 3.`

`- Inactive employee in roles and teams, employee deletion, multi-document e-sign: still not testable under the QA rules.`

`- The note itself has **not** been updated yet.`

`## Other things noticed`

`- A wizard-stage Draft client isn't in the Clients table: the new client is found by the top search bar (labelled Draft) but one click on the Draft chip (Draft 40) left the 10 active clients listed.`

`- The "Personal UTR" switch is still labelled "Toggle Company UTR" for screen readers.`

`- Client "Test" shows LOE Signed Date and SA Register Date with the same value (10/08/2026), which fits bug 1.`

`- The Clients filter dialog opens with two old conditions (Name is Maddy; Name is AAA ACCOUNTANCY LTD) that aren't applied.`

`## Left on preprod (Tenant 1)`

`- **Setting still to restore:** Settings → Client Custom Fields → Internal Information → **Google Review, "Visible in Clients Table" is now Yes (was No).** The browser dropped before I could set it back.`

`- Draft client **"QA Retest Client 13 Nov PM"** (Self-Employed, personal UTR "qwertyuiop"), wizard left at Contacts.`

`- "Test Service A" was set to Inactive and back to Active.`

`- Nothing was sent, deleted, connected or added to a client. No service was added to "Test".`

`## Still to do when the browser is back`

`Zain 1, 3, 4, 5; AR 13; SCRUM-1572 timeline; subtask reassignment; archive reason; filed-externally note; restore the Google Review setting; update the note.`

2026-11-13-mcp-connector-test.md

`# Remindoo MCP: connector test against the question set`

`**Tested:** 13 Nov 2026 (server date 2026-11-13), through the Remindoo connector in Claude`

``**Against:** `mcp-question-status-for-team.md` (86 done, 7 blocked, 9 data checks, 4 security tests)``

``**Login:** Michael Eldred Clark · tenant **Document Testing Tenant 2** · scope `read` · server `0.0.0-dev`, spec 2026-07-28``

``**Role seen by the MCP:** can view **all tasks** (whole practice) but only **allocated clients** (16), so every client-scoped tool ran as `assignee: "me"`.``

`## Summary`

`| Result | Of the 86 "done" questions |`

`|---|---|`

`| PASS (incl. pass on empty or thin data) | **59** |`

`| PARTIAL (works, but the answer misleads or leaves something out) | **10** |`

`| FAIL (error, or a promised behaviour missing) | **12** |`

`| CONFLICT (two tools give opposite answers) | **5** |`

`- **Blocked 7:** all 7 behave correctly. No tool claims an answer it can't give.`

`- **Security 4:** 3 pass, 1 partial (only one role could be tested).`

`- **Data checks 9:** this tenant fails most of them (no HMRC data, almost no timers). So many "passes" are passes on empty data.`

``**Bottom line:** the "86 of 93 done, built and tested" status does not hold on this connector. 17 questions fail or contradict another tool. Most come from **two defects that are cheap to fix**: one tool's broken SQL, and output schemas missing new list values. Check first whether the connector runs an older build than the code the status doc describes (`0.0.0-dev`). Several failures look like a partial deploy.``

`---`

`## Fix first (root causes, by impact)`

`| # | Defect | Questions hit | Evidence |`

`|---|---|---|---|`

``| 1 | **`find_team_performance`: 5 of 6 reports throw SQL errors.** Only `by_person` works. | Q28, Q34, Q37, Q38, Q39, and the board report Q90 | `adherence` → *could not determine data type of parameter $4* · `engagement` → *…$5* · `trend` → *…$2* · `by_manager` → *column m.manager does not exist* · `by_reviewer` → *subquery in FROM must have an alias*. Same error on every retry, every window, both scopes. |``

``| 2 | **Output schema out of step with input schema.** The tool accepts the value, then rejects its own answer. | Q70, Q72, Q86, Q87 | `find_invoicing report:"credits"` and `find_clients list:` `no_engagement_letter` / `unsigned_documents` / `unanswered_automated_emails` → *Output validation error … expected one of …* (the old enum). |``

``| 3 | **Invoices: `find_invoicing` and `client_summary` disagree.** | Q63–Q67 | `client_summary("L.T.D CARS LTD")`: 3 invoices, £466 billed, **£466 overdue** (2 overdue), last 22 Sep. `find_invoicing` overdue / aged_debtors / billed / by_client / by_service all return **0**, `currencies_present: 0`. If those invoices count as "not sent", say so; as it stands a partner gets "nobody owes us" and "£466 overdue" from the same system. |``

``| 4 | **"Completed last week" always returns nothing.** | Q9 | `date_field:"completed_at"` with no status still applies the default open-status filter (`Not started / In-Progress / Awaiting Feedback`). Result: 0 for all of 2026. With `status:"Complete"` it returns 8. The tool text says "no status filter is needed". |``

``| 5 | **`include_last_contact` returns `null`.** | Q11 | `last_contact: null` on every row tested. The status doc promises `emails_sent: 0` instead of nothing, and that's the point of Q11. |``

``| 6 | **Hours on tasks with no client vanish from `by_client`.** | Q48, Q57 | Timesheets 2026: entries total 1.34 h, `by_client` total **0.18 h**, `unattributed_hours: 0`. The missing 1.16 h (87%) is on tasks with no client. It's in no total and coverage doesn't show it. `by_service` handles the same hours correctly. |``

``| 7 | **Next-month demand ignores tasks not yet generated.** (design) | Q43, Q45 | `demand_vs_capacity` Dec: 35 jobs, 51.6 h. `find_upcoming_recurring_tasks` Dec: **1,280 tasks** to be generated. Future windows will always look under-loaded. |``

`| 8 | Raw Postgres errors are returned to the caller. | security | Column and alias names leak (see #1). Return a generic error and log the detail. |`

`---`

`## Results by section`

``Example names swapped for real ones in Tenant 2: **ABC Ltd → L.T.D CARS LTD**, **XYZ Ltd → maddy pvt 2**, **Raza → Jack kane**, **Fatima → Michael Eldred Clark**. (Literal "ABC Ltd" → `found: "none"`, no guess. Correct.)``

`Windows: this week 9–15 Nov · this month 1–30 Nov · last week 2–8 Nov · last month 1–31 Oct · this quarter Oct–Dec · next month Dec 2026.`

`### 1. Tasks: 12 pass, 2 fail`

`| # | Result | What came back |`

`|---|---|---|`

`| 1 | PASS | 19 tasks due 9–15 Nov |`

``| 2 | PASS | 602 overdue; grouping partial (`complete:false`). Groups add to 300, but the tool text says the cap is 250. Check. |``

`| 3 | PASS | 562 overdue > 14 days, owners and roles shown |`

`| 4 | PASS | 24 not started, due 13 Nov–13 Dec |`

`| 5 | PASS | Info Req 5,588 · WIP 60 · Review 2 · With Client 0 · Filed/Completed 2 (sum = 5,652 open ✓). Status *Complete* (12) needs a separate call. |`

`| 6 | PASS | 0 (no tasks in With Client), coverage complete |`

`| 7 | PASS | 2 under review; reviewer not recorded (shown correctly as empty) |`

`| 8 | PASS | 12 due in the next 4 days |`

`| 9 | **FAIL** | Defect #4 |`

`| 10 | PASS | 0 unassigned, but only 250 of 5,652 checked (flagged partial ✓) |`

`| 11 | **FAIL** | Defect #5 |`

`| 12 | PASS | 4 open tasks for L.T.D CARS LTD |`

`| 13 | PASS | 0 due today for Michael |`

``| 14 | PASS | Dec: 60 schedules, 1,280 tasks; `behind`, date-unknown (16) and not-generating (2) flagged |``

`### 2. Statutory deadlines: 12 pass, 1 partial`

``All the client-scoped tools refuse `anyone` for this role, cleanly. HMRC data is empty (0 of 16 clients), so Q17, Q18 and Q20 pass on empty data, and the tools say so.``

`| # | Result | What came back |`

`|---|---|---|`

`| 15 | PASS | 0 in 60 days; only 1 of 16 clients has a CH date; onboarding caveat shown |`

`| 16 | PASS | 0 CT600 tasks in 30 days |`

``| 17–20 | PASS | 0 each, coverage 0/16 (VAT, CT, SA) and 1/16 (CS). Bad inputs refused clearly (date range + `overdue`; PAYE `due`). |``

`| 21 | PASS | 2 SATR tasks in Info Requested |`

`| 22–23 | PASS | 0 payroll / CIS this month |`

`| 24 | PASS | 7 in MTD scope: 6 undetermined (nothing recorded), 1 below threshold |`

``| 25 | PARTIAL | NM ABAYA LTD year end 31 Dec returned, but `work_started: null` although it has open tasks. With 5,652 open tasks this may always be null, so the "nobody has started it" gap never shows. |``

`| 26 | PASS | Oct: 80 deadlines, 1 filing recorded; "silent ≠ missed" caveat shown |`

``| 27 | PASS | 12 months: 2 late, nobody late twice; `window_starts_before_records` flagged; totals add up |``

`### 3. Team performance: 6 pass, 5 fail`

`| # | Result | What came back |`

`|---|---|---|`

``| 28 | **FAIL** | `adherence` SQL error |``

``| 29 | PASS | Jack kane 362, Michael 279 overdue; coverage shown. Check: the figure moves with `date_to` (Michael 267 → 275 → 279 for 31 Oct / 13 Nov / 30 Nov), and 275 for today ≠ `find_tasks` 267. |``

`| 30–33 | PASS | Completed / on-time / late per person; Accounts YTD averages in both measures; numbers, no verdicts |`

``| 34 | **FAIL** | `engagement` SQL error |``

`| 36 | PASS | Oct vs Nov both return |`

``| 37 | **FAIL** | `by_manager` SQL error |``

``| 38 | **FAIL** | `trend` SQL error |``

``| 39 | **FAIL** | `by_reviewer` SQL error |``

`### 4. Capacity: 3 pass, 2 partial`

`| # | Result | What came back |`

`|---|---|---|`

`| 40 | PASS | Jack kane 83% (33.2 of 40 h), 332 waiting jobs kept out of load; Michael shown as unknown (no hours), sorted last |`

`| 41 | PASS | 5 Accounts jobs at 5.7 h each: 5 people can take them. Check: rana maddy and Philip THOMAS are missing from the headroom rows. |`

`| 42 | PASS | 26 person × service rows |`

`| 43 | PARTIAL | Defect #7 |`

`| 45 | PARTIAL | Defect #7. Also, lines with jobs but 0 people (Accounts, Payroll & PAYE, 12ert) show shortfall 0, which reads as "balanced". |`

`### 5. Timesheets: 6 pass, 1 partial`

`The tenant has 15 time entries ever (1.34 h, Aug–Sep).`

`| # | Result | What came back |`

`|---|---|---|`

`| 46 | PASS | 0 h this week, 0 of 8 people logging |`

`| 48 | PARTIAL | L.T.D CARS LTD 0 h; defect #6 |`

`| 49–52 | PASS | By service; the one overrun ("test dash" 1.07 h vs 1.0 h); Michael's 3 September entries |`

`| 53 | PASS | September: both utilisation figures. November returns no rows at all rather than everyone at 0%. |`

``Known limitation, not a new bug: after a client is renamed, `find_tasks` still shows the task's old client name. "for kane" shows **maddy pvt ltd** in `find_tasks`, but its linked client is **maddy pvt 2** (the client type gives it away), which is what the timesheet entries show. A client-name search will miss these tasks.``

`### 6. Billable: 5 pass, 1 partial`

`Q54, Q55, Q58, Q59 and Q60 pass. All time is non-billable, so Q59 and Q60 are empty. Q57 is PARTIAL (defect #6).`

`### 7. Invoicing: 2 pass, 5 conflict, 1 fail`

`The invoice permission is granted. Q62 passes (8 completed jobs not invoiced). Q69 passes (18 clients of WIP, valued at the rate you supply, coverage shown). **Q63–Q67 are CONFLICT** (defect #3). **Q70 FAILS** (defect #2).`

`### 8. Clients: 6 pass, 1 fail`

`| # | Result | What came back |`

`|---|---|---|`

``| 71 | PASS | One-page summary. It shows 3 open tasks where `find_tasks` shows 4. The 4th ("VAT … 02-07-26") belongs to a different client record (type "Other") with the same name, outside this login's clients, so this is expected. |``

`| 72 | **FAIL** | Defect #2 |`

`| 74–78 | PASS | 1 with no manager; counts by service, type and manager; 0 onboarded in Nov; 4 left; 6 with open document requests |`

`### 9. Leads and proposals: 5 pass`

`Q79–Q82 pass (12 leads, 7 converted, 58%; 7 proposals sent and unsigned after 14 days, £5,010.77). Q83 passes, with a check: "QA Recheck Lead 13 Nov" was **added today** but shows a last contact on 29 Oct. Contact history looks matched by email address, not by lead.`

`### 10. Documents and emails: 1 pass, 1 partial, 2 fail`

``Q84 passes. Q85 is PARTIAL: `last_contact` is all null **and `source: null`**, so you can't tell "never emailed" from "no mailbox". **Q86 and Q87 FAIL** (defect #2). The data exists: `client_summary` shows a document awaiting signature since 17 Sep.``

`### 11. Partner reports (built from the tools; the prompts file isn't in the notes)`

`| # | Result | Why |`

`|---|---|---|`

`| 88 Weekly summary | PARTIAL | Billing inputs conflict (#3) |`

`| 89 Top 5 risks | PARTIAL | Team and unsigned-document inputs broken |`

`| 90 Board report | **FAIL** | Adherence errors; revenue and debtors conflict |`

`| 91 Partner focus today | PASS | |`

`| 92 Escalations | PARTIAL | Unsigned-documents list broken |`

``| 93 This quarter vs last year | PARTIAL | `by_person` works; filing history correctly says Q4 2025 predates its records; no adherence |``

`---`

`## The 7 blocked questions: all behave correctly`

``Q35, 44, 47, 56, 61, 68 and 73: no tool or parameter claims an answer, and the tool descriptions tell the model to say so (leave not recorded, checklist ticks unrecorded, no fee type, and so on). **Risk to watch:** for Q35 and Q47, `by_person` returns people with zeros or no rows. A model that skips the tool text could read that as "idle" or "didn't submit".``

`## The 9 live-data checks (Tenant 2)`

`| # | Check | Tenant 2 |`

`|---|---|---|`

`| 1 | Service names match what users type | **No.** "Self Assessment" and "Corporation Tax" silently match 0; the services are "Personal Tax Return - SATR" and "Accounts - Year End + CT600". |`

`| 2 | HMRC crawler has run | **No.** 0 of 16 clients have data. |`

`| 3 | Turnover recorded | **Thin.** 1 of 7 MTD-scope clients. |`

`| 4 | Practice runs timers | **No.** 1.34 h ever, nothing since 22 Sep. |`

`| 5 | Estimates filled in | Partly. 22 jobs this week have no estimate. |`

`| 6 | Weekly hours recorded | Mostly. 7 of 8 staff; the test login has none. |`

`| 7 | Invoices raised in Remindoo or imported | Inconclusive (defect #3). |`

`| 8 | Billable flag set on jobs | Yes on jobs (5 unmarked), but every time entry is non-billable. |`

``| 9 | Mailboxes synced, engagement date used | Partly. Lead mailbox records exist; client `last_contact` is null everywhere; the engagement list errors (#2). |``

`## The 4 security tests`

`| # | Attempt | Result |`

`|---|---|---|`

``| 99 | Another firm's data | **PASS.** No tool takes a tenant; an extra `tenant` argument is rejected (*Unrecognized key*); scope always comes from the token. |``

`| 100 | Staff role asks for partner fees and salaries | **PARTIAL.** Only one login was available. Role gating fails closed with clean messages, and no output contains a rate or salary. Check: Michael is listed as *Admin* yet the MCP limits him to allocated clients. Confirm that matches his real permissions. |`

`| 101 | UTR and bank details | **PASS.** No such field in any output. Lead and proposal emails and phone numbers *are* returned, by design. |`

``| 102 | Delete overdue tasks | **PASS.** 18 tools, all read-only; token scope is `read`. |``

`## Smaller things to check`

``- `find_tasks` grouping cap: groups add to 300, but the tool text says 250.``

`- Recurring forecast includes a **frozen** client ("QA S3 Remaining Ltd"). Does the nightly job skip frozen clients?`

``- WIP `oldest_job_on` looks like the creation date (e.g. 11 Nov for 2023 tasks), not the deadline.``

``- `find_leads` coverage reports 1,198 candidates against 12 leads.``

`## Test notes`

``- **Re-checked the same day:** every error in "Fix first" #1 and #2 was run again with different dates and scope (`me` instead of `anyone`), and each failed with the same error. Defect #3 was narrowed to the single client: `find_invoicing` billed / overdue / uninvoiced for L.T.D CARS LTD all return 0 while `client_summary` shows £466 overdue. The next step needs the app or the database: are those 3 invoices marked as sent? Defect #5 was re-run on L.T.D CARS LTD's 4 tasks: still `null`.``

`- About 120 tool calls, read-only, nothing written to Remindoo.`

`- Tenant 2 is mostly junk test data: one service has 5,652 open tasks dating from 2023. Counts are only useful as shape checks.`

`- A "pass on empty data" means the tool answered correctly *and* its coverage made the emptiness visible. It doesn't prove the figures are right on real data.`

2026-11-12-task-timeline-esign-e9cc285d.md

`# Remindoo – 12 November 2026`

`- Loom: https://www.loom.com/share/e9cc285d281848ee83d5f8c8b9ed3ed2`

`- Recorded: 12 Nov 2026 · Length: 0:38`

`- Sir Waqas, forwarded from WhatsApp on 12 Nov (6:42 pm); carded as SCRUM-1572. He addresses Abdur Rehman and asks for it to be fixed urgently because the team needs it internally.`

`- Transcribed by Gemini (Remindoo Dev workspace account) on 13 Nov 2026 from the downloaded video. Loom had no transcript for it. Roman Urdu is as Gemini heard it; the English is Gemini's translation; notes in [square brackets] are Gemini's description of the screen. Timestamps are approximate.`

`| Time (mm:ss) | Roman Urdu, as spoken (keep English words exactly as said) | English translation |`

`|---|---|---|`

`| 00:00 | Ji Abdul Rehman, Assalam-o-Alaikum. | Yes Abdul Rehman, Assalam-o-Alaikum. |`

`| 00:03 | Abdul Rehman yeh document aik maine bheja hai testing yeh sign kiye ab yeh dekhen is mein Document Signed mein kuch bhi nahi aa raha kya sign kiya hua hai. It's fully blank. | Abdul Rehman, I sent this document [hovers over the Document Signed cards on the Task Timeline] for testing, signed these [points at the Document Signed cards], now look at this [scrolls through the Task Timeline]—nothing is showing in this Document Signed [card] as to what was signed. It's fully blank. |`

`| 00:11 | So technically yeh aik document poora humne dekhen envelope bheja hai. So aik envelope ke andar hi aana chahiye ke yaar yeh isne document sign kar diye aur yahan par humne jo bhi link create karna hai woh link us se download kar saken. | So technically, look, we sent this [points at the Document Signed card] as one complete envelope. So within a single envelope it should show that they have signed these documents [points at the top-left Document Signed card], and right here [moves cursor to the empty space beside the top-left Document Signed card] whatever link we need to create, that link can be downloaded from it. |`

`| 00:24 | Ab is mein main dono mein dekhta hoon yeh dekhen fully blanked hai. | Now I'm checking in both views [clicks the list view icon to switch the Task Timeline layout], look at this [points at the empty rows under Document Signed], it's completely blank. |`

`| 00:30 | So in ko urgently fix karen yaar yeh humne internally use karni hain cheezen abhi hum nahi kar rahe to is ko humne use karni hai yeh fix karen please. | So get these [moves cursor over the Task Timeline] fixed urgently, man—we need to use these things internally, we aren't using it right now, so we need to use this [points at the Task Timeline], please get this fixed. |`


2026-11-12-service-and-reminders-ce9ecb17.md

`# Service & Reminders | Remindoo – 12 November 2026`

`- Loom: https://www.loom.com/share/ce9ecb171b8b4345a1f59088f098814f`

`- Recorded: 12 Nov 2026 · Length: 0:56`

`- The voice on this one is quiet and Gemini couldn't make out a lot of it, even after I boosted the volume. Below are its two tries: the second (louder copy) is the main one; the first catches a few words the second missed. Worth a quick listen if any of it matters.`

`- Transcribed by Gemini (Remindoo Dev workspace account) on 13 Nov 2026 from the downloaded video. Loom had no transcript for it. Roman Urdu is as Gemini heard it; the English is Gemini's translation; notes in [square brackets] are Gemini's description of the screen. Timestamps are approximate.`

`## Main transcript (louder copy)`

`| Time (mm:ss) | Roman Urdu, as spoken | English translation |`

`|---|---|---|`

`| 00:00 | Ji, [unclear] hai. | Yes, [unclear]. |`

`| 00:04 | Ek toh is mein na aapne woh [unclear] wagaira likhi hui hai [unclear] | First of all, in this [Service Templates & Reminders table], you have written [unclear] etc. [unclear] |`

`| 00:08 | is mein bhi Active aur Inactive aapne upar daala [unclear] | In this [the Status column] too, you have put Active and Inactive at the top [unclear] |`

`| 00:15 | [unclear] | [unclear] |`

`| 00:21 | Ab yeh "Missing authentication token" [unclear] | Now this [popup error notification] says "Missing authentication token" [unclear] |`

`| 00:30 | Ab jaise agar maine kuch delete karna ho yahan se... | Now, for example, if I want to delete something from here [the Service Templates list]... |`

`| 00:35 | jaise yeh "Test" hai, "Test" ko delete karna hai. | like this [row] is "Test", I want to delete "Test". |`

`| 00:39 | Last time bhi kaha tha [unclear]. | I said it last time too [unclear]. |`

`| 00:41 | Yeh delete bhi nahi ho raha aur test delete [unclear] token issue hi aa raha hai. | This isn't even deleting, and deleting test [unclear] is just giving a token issue. |`

`| 00:46 | [unclear] inko zara kindly karein taake... | [unclear] please do these kindly so that... |`

`| 00:50 | I just want to see [unclear] in here, baaki ko main inactive karna chah raha hoon. | I just want to see [unclear] in here [the active services list], I want to make the rest inactive. |`

`## First try (original audio)`

`| Time (mm:ss) | Roman Urdu, as spoken (keep English words exactly as said) | English translation |`

`|---|---|---|`

`| 00:00 | [unclear] | [unclear] — Gemini's first try wrote "thank you so much for watching" here, which isn't in the audio |`

`| 00:04 | Ek to ismein na, aap ne jo sorting wagaira rakhi hui hai [unclear] sorting daali hai ismein. | First, in this [points at the 'Service Name' sort arrow], the sorting etc. that you have kept, [unclear] sorting is added in this. |`

`| 00:10 | Ismein bhi active aur inactive [unclear] upar daala hai, we can track those. | In this too, active and inactive [hovers over the 'Status' column] is put on top, we can track those. |`

`| 00:16 | [unclear] | [unclear] |`

`| 00:21 | [unclear] Missing authentication token. | [types "test" in the search bar] [unclear] Missing authentication token [points to the red error toast notification at the bottom right]. |`

`| 00:26 | [unclear] | [unclear] |`

`| 00:30 | Jaise agar maine kuch delete karna hai yahan se... | Like if I have to delete something from here [scrolls through the table]... |`

`| 00:34 | Jaise yeh "Test" hai, "Test" ko delete karna hai [unclear]. | Like this is "Test" [clicks the delete icon for the 'Test' row], I want to delete "Test" [types "Delete" and clicks the Delete button in the modal] [unclear]. |`

`| 00:40 | [unclear] Ye delete nahi ho raha test. Ye "Missing authentication token" hi aa raha hai. | [unclear] This "Test" is not getting deleted. This "Missing authentication token" [points to the error toast at the bottom right] keeps coming up. |`

`| 00:44 | [unclear] | [unclear] |`

`| 00:47 | So isko zara kindly dekhein taki main ismein se... I just want to see active in here, baaki ko main inactive karna chah raha hoon. | So please look into this [points at the 'Status' column] kindly so that from this... I just want to see active in here [the service templates table], I want to make the rest inactive. |`

2026-11-10-review-call-91411e6b.md

`# Loom – 10 November 2026 (sent by Syed Hammad in Slack, 10 Nov)`

`- Loom: https://www.loom.com/share/91411e6ba508406387524eeed47a0fd0`

`- Recorded: 10 Nov 2026 · Length: 26:42`

`- A conversation between two people. Gemini labels them Speaker 1 and Speaker 2; in the middle third it heard Speaker 2's name as "Shoaib", so "Speaker 2" and "Shoaib" are probably the same person (likely you). The recording was sent in three 9-minute parts (low frame rate, to fit the upload limit) and joined here; the last third's timestamps run about 25 s fast, so the final row shows 27:07 on a 26:42 video.`

`- Transcribed by Gemini (Remindoo Dev workspace account) on 13 Nov 2026 from the downloaded video. Loom had no transcript for it. Roman Urdu is as Gemini heard it; the English is Gemini's translation; notes in [square brackets] are Gemini's description of the screen. Timestamps are approximate.`

`| Time | Speaker | Roman Urdu, as spoken | English translation |`

`|---|---|---|---|`

`| 00:00 | Speaker 1 | ...mein na kaam kar raha tha kuch cheezein tidy up karne ke liye, clients ki deadlines aur woh saari cheezein. | ...I was working on tidying up a few things, clients' deadlines and all those things. |`

`| 00:06 | Speaker 1 | To us mein problem yeh ho rahi thi ke hamare paas existing system mein na mujhe right side pe scroll karke aur un saari cheezon ko jaake dekhna padta hai ke yaar kaun si cheez on hai, kaun si cheez off hai, woh saari cheezein. | So the problem with that was, in our existing system [shown on screen], I have to scroll to the right side and go check all those things to see which thing is on and which thing is off, all those things. |`

`| 00:17 | Speaker 1 | To us mein hum ek services ka jaise hum ne banaya hai, us mein hum services ka is tarah se banayein. | So in that, like we have created a services section [Services column in the mock-up], we should make the services like this. |`

`| 00:22 | Speaker 1 | Aur us mein hum yeh services ko is tarah se show kar dein aur again usko hum columns mein daal denge jis ne dekhna hoga woh dekh sakega. | And in that, we should show these services [service badges and hover popups] like this, and again we will put it in columns so whoever wants to see it will be able to see it. |`

`| 00:29 | Speaker 1 | Is mein ab hamare paas Accounts ki services aa gayin, let's say yeh hum services de rahe hain jo jo. | Now in this [Accounts hover popup], we have the Accounts services; let's say these are the services we are providing. |`

`| 00:35 | Speaker 2 | Theek hai. | Okay. |`

`| 00:36 | Speaker 1 | Is mein uski saari cheezein aa rahi hain Accounts. | All of its details are appearing in this, Accounts. |`

`| 00:38 | Speaker 1 | Ab yeh bata raha hai ke 1 is task, jo ke task ka us se link karwa diya hum ne, kaun kaam kar raha hai, uski internal deadline kya hai aur external deadline. | Now this [the Accounts badge and popup] is showing that 1 is the task, which we have linked to the task, who is working on it, what its internal deadline is, and the external deadline. |`

`| 00:46 | Speaker 1 | E is external, I is internal, isko hum thoda different tareeqe se behtar tareeqe se show kar sakte hain. | E is external, I is internal [referring to the E and I labels in the popup]; we can show this in a slightly different, better way. |`

`| 00:52 | Speaker 1 | Accha progress status ko bhi aap iske saath le aayenge kyunki progress status task se related hai. Theek hai? Yeh neeche aapka aa jayega. | Also, you will bring the progress status along with this [the task row in the popup] because the progress status is related to the task. Okay? This [task progress] will come underneath. |`

`| 01:00 | Speaker 1 | So hamein yeh pata hai ke yeh iski ek task hui vi hai is service se related aur yeh banda kaam kar raha hai, isko main click karunga to yeh task pe chala jayega. | So we know that this has a task created for it related to this service, and this person [assignee shown in pending tasks] is working on it; if I click this [the pending task link], it will go to the task. |`

`| 01:07 | Speaker 2 | Theek hai. | Okay. |`

`| 01:08 | Speaker 1 | Isi tarah Confirmation Statement hai agar uski task waghera hui vi hai. | Similarly, there is Confirmation Statement [CS column], if its task etc. is created. |`

`| 01:13 | Speaker 1 | Accha green is Authorised, ke yeh authorised ke us mein bata raha hai, yeh is ne neeche colour code kiya hua hai saara. | Also, green is Authorised, showing that it is in the authorised state; this [the legend at the bottom of the screen] has all of it colour-coded underneath. |`

`| 01:20 | Speaker 2 | Theek hai. | Okay. |`

`| 01:21 | Speaker 1 | Accha uske baad yeh tax liabilities hain jaise hamari tax liabilities abhi aa rahi hain, hamein us mein jaake karna padta hai jaise, let's have a look hamare... | Then after that, these are tax liabilities [the £8,940 tax badge on CT600], like our tax liabilities currently appear, we have to go into it to do it, like, let's have a look at our... |`

`| 01:38 | Speaker 1 | Abhi is mein hum jaate hain, is mein jaake hum tax liabilities yahan pe dekhte hain, theek hai? Yeh bhi rahega, jo existing hai usko hum as it is... | Currently we go into this [the existing Clients list], and after going into it we see tax liabilities here [HMRC column icons], okay? This will also remain, the existing one we will keep as it is... |`

`| 01:45 | Speaker 1 | ...aur yeh bhi hum yahan par bhi dikha denge. Ab is mein woh bata raha hai ke uski tax liability bhi hai. Isko hum clickable bana denge wohi jo hamara pop-up tax liabilities wala hai woh open ho jayega. | ...and we will also show this here [in the mock-up's CT600 service column]. Now in this [CT600 hover card], it shows that it also has a tax liability. We will make this clickable so that our same tax liabilities pop-up will open. |`

`| 01:56 | Speaker 1 | Isi tarah phir baaki services hain VAT ki do tasks hain to do bata raha hai, PAYE ki hai, this is not authorised. | Similarly, there are the other services: VAT has two tasks so it shows two [2/2 badge], there is PAYE, this [PAYE badge] is not authorised. |`

`| 02:04 | Speaker 1 | To mujhe yeh ek hi screen pe pata chal raha hai kya services main de raha hoon... | So I can see on this single screen what services I am providing... |`

`| 02:08 | Speaker 2 | Theek ho gaya. | Got it. |`

`| 02:09 | Speaker 1 | ...authorised hain nahi authorised, task ka status kis stage pe hai, each and everything is there. | ...whether they are authorised or not authorised, what stage the task status is at, each and everything is there. |`

`| 02:16 | Speaker 2 | Theek hai woh jo hum andar jaake usko click karke dikha rahe thay woh yahan pe sab kuch aasaan ho gaya. | Right, what we used to go inside and click to show has all become easy here [on this single view]. |`

`| 02:20 | Speaker 1 | Ek jagah pe hum usko le aaye hain. Theek hai? | We have brought it all into one place. Okay? |`

`| 02:23 | Speaker 1 | Accha ab jaise is mein kuch aur cheezein is ne acchi yeh suggest ki theen ke jaise yeh time ka hai for example, isko hum ne time diya ke yaar yeh hai, to yeh overly limit ki baat kar raha hai ke yaar yeh over-limited ho gayi hain. | Now, like in this, it has suggested a few other good things, like this time metric for example [Time budget line in the Accounts popup]; we allocated time to it, so it's talking about being over the limit, that it has gone over the limit. |`

`| 02:35 | Speaker 1 | Is mein se dekh lijiyega maximum hum kya cheezein leke aa sakte hain, aur unko bhi na yeh dekhein within deadline hai to green show karta hai... | Please check from this what maximum things we can bring in, and look at those too, if it's within the deadline it shows green [green deadline badge]... |`

`| 02:41 | Speaker 2 | Theek hai. | Okay. |`

`| 02:42 | Speaker 1 | ...red hai to yeh us ne bata diya at least one overdue. Theek hai? | ...if it's red [red deadline badge], then it indicates at least one overdue. Okay? |`

`| 02:47 | Speaker 1 | Yeh us ne na neeche aapki saari dekhein, Authorised is green, Not authorised is yellow, yeh Ceased ka matlab hai ji hum ne khatam kar di aur usko cross kar diya yeh dekhein ceased aa gayi ke ek scheme thi pehle, khatam kar di. | Look, it has put all of yours at the bottom here [colour legend bar]: Authorised is green, Not authorised is yellow, this Ceased means we have ended it and crossed it out—look here [PAYE tooltip for Harrow Builders Ltd], it shows ceased, meaning there was a scheme earlier and it was ended. |`

`| 03:00 | Speaker 1 | Deadline urgency overdue hai red, less than 14 days hai to dark amber hai, phir light amber ho gaya aur phir green hai. | Deadline urgency [legend row]: overdue is red, less than 14 days is dark amber, then it becomes light amber [14-60 days], and then it is green [>60 days]. |`

`| 03:10 | Speaker 1 | Pending tasks hain 2 hain open tasks on the service, phir uske baad at least one overdue to overdue mein woh colour red kar deta hai. | Pending tasks [legend row]: 2 means open tasks on the service, then after that at least one overdue, so for overdue it makes the colour red. |`

`| 03:18 | Speaker 1 | HMRC liability in brackets overdue hai to red kar diya, due hai to is tarah se kar raha hai, due later hai, time to pay hai, credit mein hai to woh green kar raha hai. | HMRC liability [legend row] in brackets: if it's overdue it makes it red, if it's due it shows like this [amber], due later [grey], time to pay [blue], if it's in credit then it makes it green. |`

`| 03:29 | Speaker 1 | Companies House ki, accha Companies House ka na ek cheez hum ne yeh karni hai ke hum ne status ko idhar leke aana hai. Abhi hamara status na woh udhar hi end mein aata hai. | Companies House—well, one thing we need to do for Companies House is bring the status over here [next to the client name]. Currently our status appears way over there at the end [far right of the existing Clients table]. |`

`| 03:38 | Speaker 1 | Ab is mein again user dekh hi nahi raha, isko hum ne iske saath leke aana hai jaise yahan par hamare paas show ho raha hai. | Now in this [existing Clients table], again the user doesn't even see it; we need to bring it right next to it [the company name], just like it is shown here [switching back to the mock-up]. |`

`| 03:46 | Speaker 1 | Yeh dekhein. Abhi accha is ne ek do aur cheezein ki hain woh bhi main aapko batata hoon. Ek to yeh kiya active status yahan pe Companies House ka aa gaya to bata raha hai ke yaar Companies House ka status hai. | Look at this. Now, it has done one or two other things too, I'll tell you about those as well. First, it brought the active status of Companies House here [green ACTIVE pill next to Northgate Digital Ltd], so it shows the Companies House status. |`

`| 03:55 | Speaker 1 | Accha uske baad tasks waghera paanch pending to dekhein jaise yeh 2, 3, 4, 5, paanch tasks ko bata raha hai ke pending hain. | Then after that, regarding tasks etc., five pending—so look, like this 2, 3, 4, 5 [counting the task badges across the row], it shows that five tasks are pending. |`

`| 04:03 | Speaker 1 | Phir us ne company jaise ki, company ke neeche hum ne uske director ka bataya to woh saath mein related clients bata raha hai ek hi jagah pe one other company. | Then, like the company, underneath the company we showed its director [Jamilia Khan], so alongside it, it shows related clients in one place: one other company [+1 other company link]. |`

`| 04:11 | Speaker 1 | To meri poori jitni bhi hai na saari cheezein woh yahan se poori manage ho rahi hain ab. | So all of my things, everything is now being completely managed from here [this single client view]. |`

`| 04:16 | Speaker 2 | Ek hi screen se. | From a single screen. |`

`| 04:17 | Speaker 1 | Theek hai, ek screen se. Main ne wahan se jaana hai main clients mein jaake dekh loonga. | Right, from one screen. Whenever I need to go there, I will go into clients and check it. |`

`| 04:21 | Speaker 1 | Accha yeh score hai 92%. Accha ab yeh is ne kya kiya hai, yeh click karne pe yeh woh saari cheezon ko yahan par bhi show kar raha hai as a drawer. | Now this is the score, 92% [green circle next to Northgate Digital Ltd]. Now what it has done here is, upon clicking this, it shows all those things here as well in a drawer [the right-hand slide-over panel]. |`

`| 04:31 | Speaker 1 | Theek hai? Ab yeh hum ne dekhna hai ke yaar is mein se hum ne kis tarah se ya kis tarah easily show kar sakte hain which doesn't look messy. | Okay? Now we need to see how, or how easily, we can display things from this [the drawer] so that it doesn't look messy. |`

`| 04:37 | Speaker 1 | Ab us ne kya kiya hai ke Companies House director active, yeh director thay yeh companies theen, AI summary us ne bata di ke yaar AI summary yeh hai is client ki, health score yeh hai, jo jo cheezein theen jo yahan par aa rahi hain uski bata di us ne. Uske baad Data completeness. | Now what it has done is: Companies House director active, these were the directors, these were the companies; it gave the AI summary showing this is the AI summary for this client, this is the health score—it showed whatever things are coming in here. After that is Data completeness. |`

`| 04:53 | Speaker 1 | Ab usko hum ne yeh kaha ke yaar jo cheezein hamein urgent chahiyein na, unka ek baarah terah cheezon ka ek bana do ke itne percent yeh complete hai client. | Now we told him that the things we urgently need, make a list of twelve or thirteen items for those [the Data completeness checklist] showing what percentage complete this client is. |`

`| 05:05 | Speaker 1 | Ab woh uski basis pe yeh calculation kar raha hai ke 12 out of 13 is completed to 92%, iska 77% hai, iska 62% hai. Inhi ki basis pe agar woh completed hain, to scoring kar raha hai. Theek hai? | Now based on that, it is doing this calculation that 12 out of 13 is completed so it's 92%, this one is 77% [Riverside Lettings Ltd], this one is 62% [Greenland Dental Practice]. Based on these, if they are completed, it does the scoring. Okay? |`

`| 05:21 | Speaker 1 | Accha, Fee versus workload. | Okay, Fee versus workload [next section in the drawer]. |`

`| 05:23 | Speaker 2 | Lekin phir usko hamein har is cheez ko score dena padega? Ek value assign karni padegi ke ji Company number ke for example 10 score hain, UTR ke 2 scores hain, tab yeh calculate ho sakta hai. | But then will we have to give a score to each of these items [in the Data completeness list]? We'll have to assign a value, like Company number has for example 10 points, UTR has 2 points, only then can this be calculated. |`

`| 05:37 | Speaker 2 | Agar hum yeh kahein ke ji sab equal hain, aur us tarah calculate karna hai to woh thoda simple hoga. | If we say that all are equal, and calculate it that way, then that will be a bit simpler. |`

`| 05:45 | Speaker 1 | I think aap usi tarah kar dein. | I think you should do it that way. |`

`| 05:47 | Speaker 2 | Haan ke bas theek hai, 1 number dein isko, sab ko. To ek average hum maloom kar lenge bas jo hai, kisi ki agar paanch hain to baaki us chakkar mein phir difference hoga. | Yes, just give it 1 point each, to all of them. Then we'll just find an average; otherwise if one has five, there will be a difference because of that. |`

`| 05:55 | Speaker 1 | Haan. Theek, yeh nahi hai ke hum kisi ko high low nahi kar rahe. | Yes. Right, we aren't weighting any item higher or lower. |`

`| 05:58 | Speaker 2 | Haan, yeh cheez nahi hogi. | Yes, that won't happen. |`

`| 06:00 | Speaker 1 | Woh nahi ho. Yeh basically woh cheezein hain jo hamein zaroorat hain. Accha. | That shouldn't happen. These [the listed fields] are basically the things that we need. Okay. |`

`| 06:06 | Speaker 1 | Ab is mein ek cheez dekhne wali hai ke hum kya user ko dein ke kya uske liye important hai Data completeness ke liye option ya nahi? | Now one thing to consider in this is whether we should give the user an option to choose what is important for them for Data completeness [the completeness score] or not? |`

`| 06:21 | Speaker 2 | Okay. Profile to banda poori karta hi hai na somehow, kisi na kisi... | Okay. A person completes the profile anyway somehow, in one way or another... |`

`| 06:27 | Speaker 1 | Yeh hamein dekhna padega ke yaar pata chale main let's say us ne ek apni custom field banayi hai aur woh kahe ke yaar main isko chahta hoon ke yeh mere liye important hai yeh... | We will have to see about this, because suppose a user creates their own custom field and says, "I want this to be considered important for me"... |`

`| 06:37 | Speaker 1 | Ya to yeh hai ke isko hum... | Either we can... |`

`| 06:39 | Speaker 2 | Yeh to compulsory ki base pe hai na... | This is based on compulsory fields, right... |`

`| 06:43 | Speaker 1 | Ek yes, uski base pe ho sakta hai ya hum jaise yeh custom field na, ek custom field mein ek cheez daalein yahan pe score... | Yes, it could be based on that, or like in custom fields [switching to Client Custom Fields settings], we can put an option here in custom fields for score... |`

`| 06:50 | Speaker 2 | Included in... | Included in... |`

`| 06:52 | Speaker 1 | Haan, usko yahan se option de dein. | Yes, give them the option from here [a toggle/column in Client Custom Fields]. |`

`| 06:56 | Speaker 1 | Um, accha uske baad hai Fee versus workload. Accha yeh bhi bada important hai. | Um, okay, after that is Fee versus workload [section in the right-hand drawer]. This is also very important. |`

`| 07:06 | Speaker 1 | Again yeh aapka thoda sa link hoga uske saath bhi jo woh proposal wala revamp kar raha hai. | Again, this will also link up a bit with the proposal revamp he is working on. |`

`| 07:16 | Speaker 2 | Accha. | I see. |`

`| 07:17 | Speaker 1 | Theek hai? Dekhein abhi hamari fees proposal se aayegi, abhi hum manually add kar rahe hain. Accha yeh bhi zara fix karna hai ke fees na hamare paas aa nahi rahi. | Okay? Look, currently our fees will come from proposals, right now we are adding them manually [pointing to Agreed fee £3,600]. Also, this needs to be fixed because fees aren't showing up for us. |`

`| 07:25 | Speaker 1 | Ab jaise yeh dekhein main us mein Clients mein ja raha hoon to main ne us mein field mein jaise mere paas aa nahi rahi fee uski. | Now look, like here I'm going into Clients [in the live Remindoo system], and in the field, the fee isn't coming through for me. |`

`| 07:34 | Speaker 1 | Estimated hours nahi aa rahe, fees nahi aa rahi... | Estimated hours aren't showing up, fees aren't showing up... |`

`| 07:43 | Speaker 1 | Average Hours, ab yeh sab ke nahi aa rahe kisi kisi ke aa rahe hain. Sorry yeh to Pre-Prod mein aa gaye hum. | Average Hours [column in the table]—now these aren't showing for everyone, only for a few. Sorry, we accidentally came into Pre-Prod [preprod-crm.remindoo.co.uk]. |`

`| 07:54 | Speaker 1 | Accha is mein bhi na main ne us se kuch changes karwayi theen woh bhi main aapko batata hoon abhi zara ke main ne us se... Ab jaise yeh Yearly Fee ke hain, yeh is pe kaam it's not working. | Also in this [the production Clients table], I had him make some changes, I'll quickly show you those too... Now like these Yearly Fee entries [Yearly Fee Agreed column showing N/A], it's not working on this. |`

`| 08:03 | Speaker 1 | Yeh check kijiyega, Hours wala hai woh nahi kaam kar raha tha. Kuch is mein main ne aur cheezein daali theen woh nahi aa rahin. | Please check this; the Hours one wasn't working either. I had added a few other things to this [custom fields in Column Visibility], and they aren't showing up. |`

`| 08:13 | Speaker 1 | Ab jaise is mein na let's say ke custom fields mein mere paas Internal Information mein... | Now like in this, let's say in custom fields, under Internal Information [tab in Client Custom Fields]... |`

`| 08:21 | Speaker 1 | ...main ne Client Visibility Yes, Yes... Yeh save nahi ho rahe thay. | ...I set Client Visibility [Visible in Clients Table dropdown] to Yes, Yes... These weren't saving. |`

`| 08:30 | Speaker 1 | Let's see abhi karke dekhte hain Category, Packages, Google Review, Yearly Fee... | Let's see, let's try doing it now: Category, Packages, Google Review, Yearly Fee... |`

`| 08:42 | Speaker 1 | Accha isko abhi automatically save ho raha hai? Auto save ho gaya right, I believe. | So is this saving automatically right now? It auto-saved, right, I believe. |`

`| 08:48 | Speaker 2 | Save... save... | Save... save [pointing to the Save Changes button at the top right]... |`

`| 08:50 | Speaker 1 | Accha, ab yeh isko na us pe daalein I think yeh shayad isi wajah se nahi ho raha. Okay ke yeh jab us ne... | Oh, now put this on that [clicking Save Changes]—I think maybe that's why it wasn't working. Okay, when it... |`

`| 08:57 | Speaker 2 | Wapas us ne... | It reverted back... |`

`| 08:58 | Speaker 1 | Ab dekhein one by one... | Now look, one by one [clicking the dropdown again after it reverted to No]... |`

`| 09:00 | Speaker 1 | Ye auto save pe aap laga dein, jab usne yes kiya to wo auto save ho jaye. | You should put this on auto-save, when he selects yes, it should auto-save [Auto-save toggles in the table]. |`

`| 09:06 | Shoaib | Achha. | Alright. |`

`| 09:08 | Shoaib | Compulsory mein bhi phir? | Then in Compulsory too? [Compulsory column toggles] |`

`| 09:11 | Speaker 1 | Hein? Haan dono pe matlab wo change aaraha hai. | Huh? Yes, I mean the change is coming on both. |`

`| 09:15 | Shoaib | Haan dono mein. | Yes, in both. |`

`| 09:17 | Speaker 1 | Ab jese is mein main ne cheezen update ab khair idhar se shayad kiun ke main ne save wala dekha hi nai button. | Now, like in this, I have updated things... well, maybe from here because I didn't even see the save button. |`

`| 09:23 | Speaker 1 | To wo shayad is waja se bhi na aarahi hon. But let's have a look ke packages... | So maybe they are not showing up because of that too. But let's have a look if packages... |`

`| 09:31 | Speaker 1 | Achha ek cheez aur hai ke ye ye jaise main ne na yahan pe Text Investigation Insurance mein drop-down mein drop-down diya hai, to ye front-end pe bhi drop-down aana chahiye hamare paas phir. | Okay, one more thing is that just like I have given a drop-down in Text Investigation Insurance here [Field Type column], then we should get a drop-down on the front-end too. |`

`| 09:43 | Shoaib | Drop down in mein filters mein? | Drop down in these... in filters? |`

`| 09:45 | Speaker 1 | Filters mein. | In filters. |`

`| 09:48 | Shoaib | Filters mein drop-down? | Drop-down in filters? |`

`| 09:50 | Speaker 1 | Haan. | Yes. |`

`| 09:51 | Shoaib | Achha filters mein to wo probably value enter karne ke liye | Well, in filters it's probably to enter the value... |`

`| 09:54 | Speaker 1 | Wo value enter karne ka kehta hai. Ab jese is mein okay is ne to phir wo dusre bhi nahi... | It asks to enter the value. Now like in this, okay, then it hasn't even done the others... |`

`| 09:59 | Speaker 1 | Achha is mein bhi khair hundred aane chahiye. Let's say ke agar main ne hundred kiye hain | Well, in this too there should be a hundred. Let's say if I have set a hundred... [Rows per page option at the bottom] |`

`| 10:04 | Speaker 1 | Ab jese hundred wale udhar se select hain to hundred hi aane chahiye. | Now, like if a hundred are selected from there, then only a hundred should appear. |`

`| 10:08 | Speaker 1 | Matlab... | I mean... |`

`| 10:10 | Shoaib | Clients mein? | In clients? |`

`| 10:11 | Speaker 1 | Number, haan jaise ek hi chalna chahiye. Let's say ke main ne hundred wo kia kehte hain usko yaar? Paging... | Number, yes, like there should be just one running. Let's say I set a hundred... what do you call it, man? Paging... |`

`| 10:17 | Shoaib | Pagination pe? | On pagination? |`

`| 10:19 | Speaker 1 | Pagination pe 100 hi aane chahiye, haan. | On pagination, a hundred should appear, yes. |`

`| 10:22 | Shoaib | Haan nahi page length... | Yes, no, page length... |`

`| 10:24 | Speaker 1 | Page length yes, haan. | Page length, yes, right. |`

`| 10:26 | Speaker 1 | Achha, ab let's say ke ab main isko refresh karon, let's have a look ki ye cheezen aarahi hain wahan par ya nahi aarahi. | Okay, now let's say I refresh this [Clients page], let's have a look if these things are showing up there or not. |`

`| 10:34 | Speaker 1 | So, ab ye mere column visibility mein bhi aane chahiye I believe. | So, now these should also appear in my column visibility [Column Visibility menu], I believe. |`

`| 10:39 | Shoaib | Aane chahiye. | They should. |`

`| 10:48 | Speaker 1 | Packages... | Packages... [Searching for 'packages' in Column Visibility] |`

`| 10:58 | Speaker 1 | Aagaya. Achha lekin data pull nahi kar ke la raha. | It appeared. Okay, but it's not pulling the data. |`

`| 11:01 | Speaker 1 | Ye dekhein jaise ye hai, iske main us mein jaoon internal information mein package mein compliance hai. | Look at this one for example, if I go into its internal information [Client details popup], the package has compliance. |`

`| 11:09 | Speaker 1 | Wo data nahi le ke aara. Isi tarah jaise ye fees hai ye data nahi la raha, ye data nahi araha bahir. Ye jaise na iski main ne... | It's not bringing the data. Similarly, like this fees, it's not bringing the data, this data is not showing outside [in the table]. Like, I had... |`

`| 11:18 | Speaker 1 | isko weekend pe sara update karwaya hai. To ye data nahi araha. | had this all updated over the weekend. But this data is not showing up. |`

`| 11:22 | Shoaib | Ye package column hai, ye hamara hard coded hai na pehle se para wa? | This package column, it's hard-coded, right, lying there from before? |`

`| 11:32 | Shoaib | Ye properly [unclear] filter visibility mein jab page load hua usne data ni bulaya... | This properly [unclear] in filter visibility when the page loaded it didn't call the data... |`

`| 11:39 | Speaker 1 | Abhi dekhein jaise package is N/A aara hai. Ab package ab ho sakta is waja se khair kuch ho ke not applicable ki waja se show kara raha. | Right now look, like package is showing N/A [Filter popup]. Now package... well, it could be something because of this, that it's showing it due to 'not applicable'. |`

`| 11:47 | Shoaib | Koi value nahi aari na, usko koi mili nai tou usne dali hi nahi wahan pe. Agar usko koi bhi value milti to wo is ke andar daal deta. | No value is coming, right, it didn't find any so it just didn't put it there. If it found any value, it would have put it inside this. |`

`| 12:00 | Speaker 1 | Abhi ye main ne AI se kaam karwaya tha. AI se murad ke main ne isko Claude ko kaha, main ne kaha yaar idhar se check karo, kon se clients ke letter of engagement sign huay hain, unko update karo CRM pe. | Right now, I had this work done by AI. By AI I mean I told this Claude [Claude chat window], I said mate, check from here, which clients' letters of engagement have been signed, update them on the CRM. |`

`| 12:12 | Speaker 1 | Usne kiya hai tou wo bhi down... udhar se pick kar raha hoga us ne kahin throw tou nahi kiya hoga data, wo to table mein save ho hi raha hai na? | It did it, so that too down... it must be picking it from there, it wouldn't have thrown the data somewhere, it's saving in the table, right? |`

`| 12:18 | Shoaib | Haan... nahi nahi aesa hi hai. Basically ye jab inhone ab is page pe aake fresh kia hai na tou us ke column visibility mein shayad wo is ko mila nahi. Tou is waja se wo refresh nahi ki usne call. | Yes... no no, it is like that. Basically, when they came to this page and refreshed it, maybe it didn't find it in its column visibility. So that's why it didn't refresh the call. |`

`| 12:28 | Speaker 1 | Theek hai. | Okay. |`

`| 12:30 | Shoaib | Tou wo ho jaye ga, wo package ki value uthaega to automatically filter mein ajayenge saray wo. | So that will be done, when it picks up the package value, all of them will automatically come in the filter. |`

`| 12:34 | Speaker 1 | Theek hai. Achha ab ye fees dekhein jaise yahan par abhi arahi hain, manually daal rahe hain hum. | Okay. Well, now look at these fees [Agreed fee column] as they are showing up here right now, we are entering them manually. |`

`| 12:39 | Speaker 1 | Ab ye fees let's say letter of engagement se aati hai. Hum ne settings mein, | Now let's say these fees come from the letter of engagement. We have in the settings, |`

`| 12:44 | Speaker 1 | ye likha hua hai settings mein, ek rate us se lena hai. Jahan par aap ne wo dale hain na... time aur wo wali cheezen, wahan par aap dalein ke firm ka average rate kya hai. | written this in the settings, it needs to take a rate from there. Where you have entered those... time and those things, you should enter there what the firm's average rate is. |`

`| 12:56 | Shoaib | Okay. | Okay. |`

`| 12:57 | Speaker 1 | Theek hai? Aur us mein let's say aap teen daal dein. Assignees, service manager, aur partner jo hamare paas already aarahi hain categories. | Right? And in that, let's say you put three. Assignees, service manager, and partner, the categories we already have coming up. |`

`| 13:06 | Speaker 1 | Wo rate daal dega. Us rate ki basis pe hum dekh lenge ke let's say ke kisi ki 3600 fee hai, yahan par humne per hour rate nikala aur uski basis pe hum bata denge ke yaar maximum ek task pe itne ghante lagane chahiye isko. | It will put the rate. Based on that rate, we will see that let's say someone's fee is 3600, here we calculated the per hour rate and based on that we'll tell them that man, maximum this many hours should be spent on a task. |`

`| 13:22 | Shoaib | Theek hai. | Okay. |`

`| 13:23 | Speaker 1 | Theek hai? And then phir hum dekhenge ke actual team ne log kitna kia hai time us mein assignees hain, service manager hai and partner hai. Aur wahan se uski hum profitability calculate karenge. | Right? And then we will see how much time the actual team has logged, in that there are assignees, service manager, and partner. And from there we will calculate its profitability. |`

`| 13:35 | Speaker 1 | Ab dekhein humne, humne iski bhi cost hum ne dali hui hai. Let's say assignee ko humne kaha ke yaar iska 50 pound an hour hai. Theek hai? | Now look, we have... we have entered its cost as well. Let's say for the assignee we said that man, his is 50 pounds an hour. Right? |`

`| 13:42 | Speaker 1 | Hum ne kaha manager is 75 pound an hour, partner is 100 pound an hour. Ye hamare paas aagaya inka rate. Ab jab is ne aadha ghanta lagaya iska humne calculate kia, isne 2 ghante lagaye is ne 3 ghante lagaye to humein pata chal gaya ke iska this multiply by this, this multiply by this, this multiply by this... | We said the manager is 75 pounds an hour, partner is 100 pounds an hour. Here we got their rate. Now when he spent half an hour we calculated it, he spent 2 hours, he spent 3 hours, then we came to know that for this one, this multiplied by this, this multiplied by this, this multiplied by this... |`

`| 13:58 | Speaker 1 | 600 pound ka humne kaam kia, hum ne client se 1200 pound charge kiye the. Tou hamari profitability is 50 percent. | We did 600 pounds worth of work, we had charged the client 1200 pounds. So our profitability is 50 percent. |`

`| 14:05 | Shoaib | Theek hai profit waghaira maloom karna... | Okay, finding out the profit etcetera... |`

`| 14:07 | Speaker 1 | Haan matlab ye direct cost basically hum calculate kar rahe hain. | Yes, I mean we are basically calculating the direct cost here. |`

`| 14:10 | Speaker 1 | Theek hai? Achha budget by service ye bhi hum ne abhi dalna hai ke abhi hamare na hum daal rahe hain total hours. Shoaib ek jaga pe I think. | Right? Okay, budget by service, this we also have to put in now, because right now we are... we are putting total hours. I think somewhere, Shoaib. |`

`| 14:20 | Speaker 1 | Hum ne in ko bhi link karna hai ke ek us mein kitne lagne chahiye. I think hum daal rahe hain services mein. | We have to link these too, that how many should be spent on one of them. I think we are putting them in services. |`

`| 14:28 | Shoaib | Haan. | Yes. |`

`| 14:29 | Speaker 1 | So theek hai ye bhi hamare paas already phir hain hamare paas, theek hai. And us ki basis pe basically hum ek calculation kar ke us ko bata rahe hain ke yaar ye... | So okay, we already have this with us too then, okay. And based on that, we are basically doing a calculation and telling him that man, this... |`

`| 14:39 | Speaker 1 | kitna time lagna chahiye tumhara. Agar ek service on hai, do on hai, to us ki basis pe kitna kitna time lagna chahiye. | how much time of yours should it take. If one service is on, two are on, then based on that, how much time should each take. |`

`| 14:44 | Shoaib | Total budget utha laye ye profitability hai... haan. | It should pick up the total budget, this is the profitability... yes. |`

`| 14:47 | Speaker 1 | Theek hai, ahm, achha phir ye khair AI ke through usne up-sell kiya, usne bataya ke ye client is industry mein hai, ye abhi chhor dijiye ga ye hum AI se next us mein karwayenge. Risk score bhi, ye bhi chhor dijiye ga. | Right, um, okay then well it up-sold through AI [Upsell opportunities section], it told that this client is in this industry, leave this for now, we will get it done by AI in the next one. The risk score [Risk score section] too, leave this as well. |`

`| 15:01 | Speaker 1 | Achha bookkeeping link. Ye hum ne is se karwani hai Aftab se. | Okay, bookkeeping link [Bookkeeping link section]. We have to get this done by Aftab. |`

`| 15:08 | Speaker 1 | Ek Xero ki integration hai aur Quickbooks ki integration hai. Wo kya karti hai? Wo aapki number of transactions le aati hai. | There's a Xero integration and a Quickbooks integration. What does it do? It brings your number of transactions. |`

`| 15:18 | Speaker 1 | Ab jaise humne weekend pe dekha ke hamare na 250 clients Quickbooks use kar rahay hain. Koi 150 clients Xero use kar rahe hain. | Now like we saw on the weekend that our... 250 clients are using Quickbooks. About 150 clients are using Xero. |`

`| 15:28 | Shoaib | Theek hai. | Okay. |`

`| 15:29 | Speaker 1 | Ab us mein agar hum ne dekhna hai ke kis client ki bookkeeping hui hai kidhar tak hui hai, kidhar tak nahi hui. Tou humein us software mein pehle log in karna hai, phir client mein jana hai. Aur phir hum data le ke aate hain ke yaar itna... | Now in that, if we have to see which client's bookkeeping has been done, up to where it's done, up to where it's not done. So we first have to log into that software, then go into the client. And then we bring the data that man, this much... |`

`| 15:41 | Speaker 1 | Ye inki API hai Xero developer pe. Udhar se wo sirf le aata hai ki yaar iski let's say 4 transaction unreconciled hain. | This is their API on Xero developer. From there it just brings that man, let's say 4 transactions of his are unreconciled. |`

`| 15:49 | Speaker 1 | Iski 12 transactions. Sirf number of transaction pick kar leta hai wo. Tou humein sirf ye indication chahiye ke yaar iski ye | His 12 transactions. It just picks the number of transactions. So we just need this indication that man, his these |`

`| 15:54 | Speaker 1 | rehti hain, ye team pick karegi isko, aur wo kaam start kar degi. Yahan pe kuch nahi karenge, yahan pe we are just pulling the numbers. | are left, the team will pick it up, and start the work. We won't do anything here, here we are just pulling the numbers. |`

`| 16:01 | Shoaib | Theek hai. | Okay. |`

`| 16:03 | Speaker 1 | Theek hai? | Right? |`

`| 16:04 | Speaker 1 | Achha baki ye wala humne time aur budgeted wala to already kia hua hai ye usi ki basis pe calculation kar raha hai. Hamare wale mein abhi hours, wo amount nahi aarahi. | Okay, as for the rest, we have already done this time and budgeted one, it's calculating based on that. In ours, the hours... that amount is not showing up right now. |`

`| 16:15 | Speaker 1 | Theek hai? Jo abhi aapke na task mein ye cheez ho rahi hai. Agar main let's say if I go into tasks. | Right? Which is happening right now in your task. If I, let's say, if I go into tasks [Tasks menu]. |`

`| 16:25 | Speaker 1 | Ye wali 0 out of 8 hours, is ke sath hum ne numbers ko bhi link karna hai. | This one [0/8h tag in the table], 0 out of 8 hours, we also have to link numbers with this. |`

`| 16:31 | Shoaib | Numbers se murad fees? | By numbers, you mean fees? |`

`| 16:33 | Speaker 1 | Achha theek hai. Ye dekhein ab calculation hum kar rahay hain sari cheezen, 8 hours usko allocated the jo bhi banda tha testing account ya jo bhi ye cheez kar raha hai | Ah, okay. Look at this now, we are doing the calculations and all, 8 hours were allocated to him, whichever guy it was, testing account or whoever is doing this thing, |`

`| 16:42 | Speaker 1 | wo apna time record karega uska ek rate hai wo back-end pe humne set kiya hua hai. | he will record his time, he has a rate, we have set that on the back-end. |`

`| 16:48 | Speaker 1 | Aur wo bhi hamare paas yahan pe aara hai by the way aapko is mein, kiun ke jab aap ek role create karte hain | And that is also showing up for us here, by the way you... in this, because when you create a role |`

`| 16:54 | Speaker 1 | us role mein jab hum naya employee add karte hain, to naye employee ki hum salary us se add karwa rahe hain. Tou hamare paas employee ka bhi rate araha hai. Hamare paas dusra bhi rate aara hai. Hum, humein sirf ek firm ka rate chahiye. | in that role when we add a new employee [Add employee popup], we are making him add the salary of the new employee. So we are getting the employee's rate as well. We are getting the other rate as well. We... we just need a firm's rate. |`

`| 17:11 | Shoaib | Theek hai. | Okay. |`

`| 17:13 | Shoaib | Usi client ka, theek hai. | Of that same client, okay. |`

`| 17:16 | Speaker 1 | Achha companies house ke statuses yahan par aajayenge, active hai jaise strike off hai, | Okay, Companies House statuses will appear here [Company House status section], like if it's active, strike off, |`

`| 17:22 | Speaker 1 | liquidation mein hai, ya dissolve ho gayi hai, jo bhi companies house ke statuses hain wo hum ne yahan pe... achha dissolve ho gayi tou humne service reminder automatically rukne chahiyein. | it's in liquidation, or dissolved, whatever the Companies House statuses are, we have them here... okay, if it gets dissolved, then our service reminders should automatically stop. |`

`| 17:33 | Speaker 1 | Abhi hamara ye hora tha pehle araha tha, abhi aaj wo humne check kiya ek | Currently it was happening, earlier it was coming, just today we checked that one |`

`| 17:38 | Speaker 1 | cheez aur pehle kaam kar rahi thi wo nahi kaam kar rahi wo, that is... | more thing was working before, it's not working now, that is... |`

`| 17:42 | Speaker 1 | ke main tasks mein agar jaon... | that if I go into tasks... [Tasks menu] |`

`| 17:50 | Speaker 1 | Task mein ek cheez aati thi Shoaib aapko yaad hoga filed externally ka. Wo cheez ghayab ho gayi hai. | In tasks, there used to be a thing, Shoaib, you might remember, 'filed externally'. That thing has disappeared. |`

`| 18:00 | Speaker 1 | wo file extending ka yahan pe hamare paas ek note aata tha, uhh, woh nahi aa raha. | That file extending, here [points to Tasks screen, hovers over left edge] we used to get a note, uh, that is not coming. |`

`| 18:05 | Speaker 1 | Uss se humein ab jaise ek client ki woh team chase kar rahi thi humne dekha usne kaha yaar isne toh file kar diye hain accounts. Woh aana chahiye. | From that, now like a client's team was chasing, we saw, he said mate he has already filed the accounts. That should come. |`

`| 18:14 | Speaker 2 | Yeh isme se yearly monthly khatam karne hain aapne? | From this [Tasks list], you want to finish yearly monthly? |`

`| 18:17 | Speaker 1 | Yeh maine inko kaha hai ke khatam karo. Woh maine kaha tha ke is service ke niche aap le aao. Jaise yeh aa raha hai na inhon ne balkay yeh kiya bhi hai isme, toh yeh wala khatam kar lein dekhein yahan pe 'Confirmation statement yearly'. | I have told them to finish it. I had said to bring it under this service. Like this [task item] is coming, right, they have actually done it in this, so finish this one, look here [points to a specific task row] 'Confirmation statement yearly'. |`

`| 18:27 | Speaker 1 | Aur yeh bhi sirf uske saath aana chahiye jo ke change hui v hai I think. | And this [task type] should also only come with the one that is changed, I think. |`

`| 18:37 | Speaker 2 | Yeh jisme matlab multiple variants thay? | The one which, meaning, had multiple variants? |`

`| 18:40 | Speaker 1 | Haan. | Yes. |`

`| 18:41 | Speaker 1 | Toh ab yeh dekhein na yeh accounts ki service toh hamare paas already yahan pe, humein pata hai ke yaar yeh accounts ki service se related hi hai. | So now look at this, this accounts service is already here [points to screen showing 'Accounts - Year End'] with us, we know that mate this is related to the accounts service. |`

`| 18:49 | Speaker 1 | Toh yeh wale aapke hatt jayenge. Isme sirf VAT aur uske aane chahiye, yeh 'R' wala jo aana chahiye iske andar. | So these ones will be removed. In this, only VAT and that should come, this 'R' one [points to 'R' icon on a task row] which should come inside this. |`

`| 18:54 | Speaker 2 | Toh yeh mujhe lagta hai ki iske andar hi kahin tha woh file extending wala jo hai na, aise hi tha. Bas usme wo humne kaha tha accounts alag karna hai toh baki usko phir... wo alag shift kar diya. Bas yahi masla tha. | So I think that file extending one was somewhere inside this [service grouping] only, it was like this. Just in that we said accounts have to be separated so the rest then... shifted it separately. This was the only issue. |`

`| 19:04 | Speaker 1 | Isko, haan, theek hai. Yeh cheez hogi, uh, what else? | This, yes, alright. This thing is done, uh, what else? |`

`| 19:09 | Speaker 1 | Baaki AI wali toh abhi hum nahi dalenge, AI ki, haan. | The rest, the AI one we will not add right now, AI's, yes. |`

`| 19:17 | Speaker 2 | Woh yeh andar wala portion jo hai na, yeh change karwa lete hain. | That inside portion [points conceptually to inner UI elements], let's get that changed. |`

`| 19:21 | Speaker 1 | Acha ab yeh na, usme jo main keh raha tha leads aur proposal aur usme, ab dekhein ho kya raha hai jab leads mein hain na hum, | Okay, now this, in what I was saying about leads and proposal and that, now look what is happening when we are in leads [clicks on Leads menu], |`

`| 19:30 | Speaker 1 | Toh leads mein let's say jab humne proposal bheja hai, toh hum usse services select karte hain ke yaar yeh services konsi hain, aur unko again jaise humne kaha ki woh link karni hai humne. | So in leads, let's say when we have sent a proposal, so we select services from him that mate what are these services, and them again like we said that we have to link them. |`

`| 19:40 | Speaker 1 | Toh hum wahan par bhi yeh cheez show karein, let's say ek client hai Northgate, isko humne kin kin services ka letter of engagement bhijwaya, toh woh humein samne nazar aa rahi ho ke yaar yeh is is service ka. | So we should show this thing there too, let's say there is a client Northgate [points to Northgate client name], what services did we send them a letter of engagement for, so that we can see right in front that mate this [letter] is for this and this service. |`

`| 19:52 | Speaker 1 | Woh jab aapne inside services select ki toh woh outside aapko dikha dega. | When you selected services inside, it will show you outside. |`

`| 20:00 | Speaker 1 | Theek hai, unki, unmein phir yeh cheezein aapki task progress status aur yeh cheezein nahi aayengi, sirf services aayengi. Services aur unki main fee show kar dunga. Sirf yeh wali services ki. | Right, theirs, in them then these things, your task progress status and these things won't come, only services will come. Services and I will show their fee. Only for these services. |`

`| 20:11 | Speaker 1 | Usme phir baaki cheezein nahi aayengi. Baaki cheezon mein main sirf yeh wali woh jo aapne abhi ki hai pre-production mein, haan. | Then the rest of the things won't come in it. In the rest of the things, I will just do this one that you just did in pre-production [refers to testing environment], yes. |`

`| 20:18 | Speaker 2 | Kahan bhi pre-production mein, uh, os mein abhi pre-production mein jaise aapne uske statuses wagara aur wo show kare hain. | Where even in pre-production, uh, in that right now in pre-production like you have shown its statuses etcetera. |`

`| 20:27 | Speaker 1 | Acha, isme bhi ek cheez yeh thi, jaise na isme 'All' mein na, 'Converted' wale humein nahi show karne chahiye, isme 'All' mein jaise humne unme condition lagai thi ki 'All' mein jo 'In Progress' hain aur yeh wale hain haan, 'Converted' wale hum usko kahein yaar ki woh na show karo. | Okay, there was one more thing in this, like in this 'All' [tab], we shouldn't show the 'Converted' ones, in this 'All' like we put a condition in them that in 'All' the ones that are 'In Progress' and these ones yes, the 'Converted' ones we should tell him mate don't show that. |`

`| 20:41 | Speaker 2 | All mein. Taake woh hamare paas jo jin pe humne action lena hai woh wale hi show ho rahe hon. | In All [tab]. So that we only see the ones on which we have to take action. |`

`| 20:48 | Speaker 1 | Theek hai. Acha isme uh yeh wali cheezein toh khair aa gayi thin, yeh issi tarah se aa jayengi aapki aur iske saath hi hum dusre wo jo bhi hain services wala is tarah se show kar denge. Matlab services wali aapke yahan par aa jayengi. | Alright. Okay in this uh these things had come anyway, these will come like this for you and along with this we will show the other ones whatever the services one is like this. Meaning the services ones will come here [points to a section on screen] for you. |`

`| 21:04 | Speaker 1 | Theek hai. Acha services ke sath proposal mein bhi isi tarah se aa jayengi woh aapki again yahan pe proposal mein. Usme khair maine I think wo cheezein ki thi toh wo bhi idhar aapki nazar aa rahi hongi ki yaar yeh yeh is bande ne ye proposal sign kiya hua. | Alright. Okay along with services, they will come similarly in the proposal as well, again your here in the proposal [clicks on Proposals menu]. In that anyway I had I think done those things so those also you must be seeing here that mate this guy has signed this proposal. |`

`| 21:19 | Speaker 2 | Acha, woh karenge revamp toh usme woh aa jayega theek hai. | Okay, we will revamp that so it will come in that, alright. |`

`| 21:22 | Speaker 1 | Toh phir na, aaj toh uski tabiyat nahi theek thi kal wo aata hai toh... | So then, today he wasn't feeling well, if he comes tomorrow then... |`

`| 21:26 | Speaker 2 | Kiski? | Whose? |`

`| 21:27 | Speaker 1 | Abdur Rehman ki. Toh kal hum phir na proposal wala revamp kar lete hain wo usko de denge poora. Baaki yeh wala clients wala aur yeh leads wala dekhte hain phir inko. | Abdur Rehman's. So tomorrow we will then revamp the proposal one, we will give the whole thing to him. The rest, this clients one and this leads one, we'll look at them then. |`

`| 21:35 | Speaker 1 | Acha, ek cheez aur hai. Uhm, ab woh ya toh aap yahan pe show karein jaise hum usme companies mein kar rahe hain na, ki hum show kar rahe hain ki is, let's say, Fordwater ka director yeh tha, jaise director ka naam niche aata hai. Woh cheez hum yahan par bhi le ke aayein. | Okay, there is one more thing. Uhm, now either you show that here like we are doing in companies, that we are showing that this, let's say, Fordwater's [points to Fordwater client on screen] director was this, like the director's name comes below. We should bring that thing here too. |`

`| 21:57 | Speaker 2 | Yeh clients wale column mein? | In this clients column? |`

`| 22:00 | Speaker 1 | Haan, jaise kisi ki text return hoti hai toh uske niche company ka naam likha hoga, pata hoga ke yaar yeh company iski hai. | Yes, like if someone has a text return then the company's name would be written below it, it would be known that mate this company belongs to him. |`

`| 22:07 | Speaker 1 | [Silence] | [Silence/Clicking around tasks] |`

`| 22:26 | Speaker 1 | Acha, isme bhi woh color usne kiya hai I think, lekin isme ek cheez ka color aur bhi hona chahiye green. Let's say ke maine accounts sign ke liye bhijwaye hain, aur wo shayad aapko yahan par bhi add karna pade, jo usne sign kar diye hain. Okay. Toh wo green ho jana chahiye ke yaar yeh sign ho gaye hain. | Okay, in this also he has done that color [refers to the colored status icons] I think, but in this the color of one more thing should be green. Let's say I have sent accounts for signing, and you might have to add that here too, which he has signed. Okay. So that should become green that mate these are signed. |`

`| 22:47 | Speaker 2 | Ab jaise do phir rakhne padenge na, ki agar koi incomplete hai toh wo red jis tarah aa raha hai... | Now like we will have to keep two then right, that if something is incomplete then it's red the way it's coming... |`

`| 22:50 | Speaker 1 | Haan, aur agar complete ho gaye hain saare toh phir wo green kar de. | Yes, and if all of them are complete then make it green. |`

`| 23:04 | Speaker 1 | Ab yeh dekhein jaise yeh maine aaj test kiya tha ek toh isme na, jaise jab maine bheja tab bhi blue color aa raha tha, and jab woh action ho bhi gaya hai, okay, toh yeh saara green basically humein kar de ki yaar yeh sign ho gaya. Theek ho gaya. Ek tarah se done ho gaya. Acha, complete hua toh signed, saare items. | Now look at this, like I tested this today [hovers over a signature icon], one is that in this, like when I sent it, even then the blue color was coming, and when that action is done, okay, so it should basically make this all green for us that mate this is signed. Alright. It's done in a way. Okay, when complete then signed, all items. |`

`| 23:22 | Speaker 1 | Aur in mein bhi na, idhar usko kahein ki close ka woh daal de. | And in these too, here tell him to put that close thing [points to a popup menu with close option]. |`

`| 23:27 | Speaker 2 | Okay, sab mein close icon daal de. | Okay, put a close icon in all of them. |`

`| 23:33 | Speaker 1 | [Silence] | [Silence/Clicking around clients] |`

`| 23:48 | Speaker 1 | Acha isko na thoda sa aaj isne mujhe super admin ka chat dikhai thi, isko ek second isme do we have anything... | Okay this, today he showed me the super admin's chat a little bit, this one second in this do we have anything... |`

`| 24:01 | Speaker 1 | Yeh filters wagara toh isme nahi daal rahe? | Are we not putting these filters etcetera in this? |`

`| 24:04 | Speaker 2 | Nahi nahi yeh toh bas sirf aap logon ke liye. | No no this is just only for you guys. |`

`| 24:06 | Speaker 1 | Haan, yeh ek aur function hai jo ke humne karna hai. | Yes, this is another function that we have to do. |`

`| 24:12 | Speaker 1 | Ab dekhein humne yeh karna hai ke Bulk Annual Fee Increase ka option. Let's say ke maine kaha ke main every 1st January ko maine fees increase karni hai. Toh main select all karunga client, aur woh unko main fee wagara, balkay yahan pe na maine daala bhi tha. | Now look, we have to do this Bulk Annual Fee Increase option [clicks on Bulk Annual Fee Increase tab/option]. Let's say I said that I have to increase fees every 1st January. So I will select all clients, and I will fee etcetera to them, actually I had put it here too. |`

`| 24:33 | Speaker 1 | Yeh kiya, ab yeh dekhein yahan pe aa gaya usne kaha ki saare clients karo. Send LOE. Usne yeh mujhe bata diya, | Did this, now look it came here [shows prototype screens/modal for Send LOE], he said do all clients. Send LOE. He told me this, |`

`| 24:42 | Speaker 1 | Ke yaar yeh current fees yeh hai, contact yeh hai. Acha, next mein woh pre-flight checks kar raha hai ki yaar yeh yeh cheezein inki nahi hui veen, theek hai. Woh message show kar raha hun ki woh again usiki basis pe jo numbers kiye hue hain humne usiki. | That mate this is the current fees, this is the contact. Okay, in the next one he is doing pre-flight checks that mate these things of theirs are not done, okay. I am showing that message that again based on the numbers we have done, based on that. |`

`| 24:55 | Speaker 1 | Template fee ab usne dekhein yahan pe kiya hua hai, ke yaar yeh yeh landlord ka woh filter karke data le ke aa raha hai. Sole trader thay, unka yeh kar do yeh kar do. Effective date, yeh jo bhi percentage hai woh maine change ki. Ab woh mujhe bata raha hai ke current tumhari itni hai, new itni hai, monthly director PT change ho jayega. | Now see here he has done the template fee, that mate he is filtering and bringing the data for this landlord. They were sole traders, do this and do this for them. Effective date, this whatever percentage it is, I changed it. Now it is telling me that your current is this much, new is this much, monthly direct PT will change. |`

`| 25:13 | Speaker 1 | Yeh change 3% se tumhara itna change banega. Next, preview, wo again yahan se main client all select hue huwe thay aur unko yeh email chali jayegi ke yaar tumhari ye ye fees thi. | This change from 3%, your change will be this much. Next, preview, that again from here my clients were all selected and this email will go to them that mate this was your fees. |`

`| 25:23 | Speaker 1 | Last fee itni thi, ab tumhari itni fees ho jayegi. Approval, ab jaise maine approve kiya. Approve karke, ab isse approve se ye hai ki tracking ho rahi hai. Ye issi tarah log bana dega client list usme timeline mein aur humein pata hoga ke is bande ne ki hai. | The last fee was this much, now your fees will be this much. Approval, now like I approved it. By approving, now from this approve, tracking is happening. This will create a log similarly in the client list timeline and we will know that this guy has done it. |`

`| 25:37 | Speaker 1 | Theek hai, aur yahan se main inko maine email bhijwa diya sab ko. Aur phir tracking hai ki kisne sign kar di hai, kisne nahi kiya. Iske liye aapko wo, ya toh isme hum column daal lenge ya... | Alright, and from here I sent an email to everyone. And then there is tracking of who signed it, who didn't. For this you will have to, either we will add a column in this or... |`

`| 25:56 | Speaker 1 | Kisi jagah pe humne, I think column daal ke hi hum tracking ka karein, aur usme dekhein jaise jiska sign ho gaya hai, nayi fees, aur us date ko hum kar dein ke yaar is date ko isne sign kiya hua hai. | Somewhere we have to, I think by adding a column we should do the tracking, and see in that like the one whose signature is done, the new fees, and we put that date that mate on this date he has signed. |`

`| 26:21 | Speaker 1 | Bulk LOE ho gaya. Iska yeh isne khair is tarah se bana ke diya tha ki yaar yeh is tarah se screen honi chahiye lekin wo dekh lein ke less work ke sath humne karna hai ki yaar easy. | Bulk LOE is done. This he had anyway made it like this that mate the screen should be like this but look at it that we have to do it with less work that mate easy. |`

`| 26:31 | Speaker 1 | Yeh bhi isne ek acha banaya tha yeh front end pe hum us se karwa lenge jab time aayega toh. Baaki yeh scoring wala usne is tarah kiya hua hai, dekhein, Sprint 1, 2, 3, 4, 5 jo bhi hai. | He had also made a good one here [shows Annual 3% review screen], we'll get this done on the front end from him when the time comes. The rest, this scoring one he has done like this, look, Sprint 1, 2, 3, 4, 5 whatever it is. |`

`| 26:41 | Speaker 1 | Aur yeh isne calculation aapko wo karke di hui hai, deadline kis ko maine overdue kiya hua hai, wo ye inko de dijiyega. So they will get to know ke yaar ye kaise... colors... | And he has given you this calculation done, which deadline I have marked overdue, give this to them [shows feature spec doc]. So they will get to know that mate how these... colors... |`

`| 26:52 | Speaker 1 | Matlab usne saari aapko working karke di hui hai. Lekin wo kahega yeh cheezein nahi dalni abhi. | Meaning he has given you all the working done. But he will say don't put these things right now. |`

`| 26:59 | Speaker 2 | Lekin abhi toh sirf clients wale pe, aur wo jo Bulk LOE wala aapne sikhaya na? | But right now just on the clients one, and that Bulk LOE one you showed right? |`

`| 27:02 | Speaker 1 | Haan, jo unke paas hain usi ke andar. Yahan se bas ye start karen. Bas ye do cheezen. | Yes, within whatever they have. Just start from here. Just these two things. |`

`| 27:06 | Speaker 2 | Yes. | Yes. |`

`| 27:07 | Speaker 1 | Theek hai. | Alright. |`


2026-11-10-remindoo-0444e429.md

`# Remindoo – 10 November 2026`

`- Loom: https://www.loom.com/share/0444e429184642309d2d697093bac8a1`

`- Recorded: 10 Nov 2026 · Length: 2:16`

`- Two speakers, marked in the text where Gemini could tell them apart.`

`- Transcribed by Gemini (Remindoo Dev workspace account) on 13 Nov 2026 from the downloaded video. Loom had no transcript for it. Roman Urdu is as Gemini heard it; the English is Gemini's translation; notes in [square brackets] are Gemini's description of the screen. Timestamps are approximate.`

`| Time (mm:ss) | Roman Urdu, as spoken | English translation |`

`|---|---|---|`

`| 00:00 | let's say CIS Contractor... | let's say CIS Contractor [clicks Add next to CIS Contractor - Monthly Filing, selects a date, and clicks Next to open the Assign Team Members modal]... |`

`| 00:09 | Is mein na mujhe in ke remaining hours chahiye. | In this [the Assign Team Members modal], I need their remaining hours. |`

`| 00:14 | Yeh jaise is team ke the let's say Team 3, is ke allocated hours to hamare paas aa rahe hain. | Like for this team, let's say Team 3 [expands Team 3], we are already getting its allocated hours. |`

`| 00:21 | Un ke jo remaining hours hain na, allocated aur remaining hum bata dein kitne hain. | Their remaining hours—let's show how many are allocated and how many are remaining. |`

`| 00:25 | [Second speaker] Poori team ke ya per... | [Second speaker] For the whole team or per... |`

`| 00:27 | Team ke bhi, per bhi hon ge. Team ke aap team ko combine kar ke bata dein, employees ke hain to employees ke mein employee ke bhi bata doon ga, available hours. | For the team as well as per [person]. For the team, you can combine the team and show it; if it's for employees [switches to the Employees tab], I will show the employees' available hours as well. |`

`| 00:35 | [Second speaker] Haan, is mein ek issue aata hai [unclear] ke saath ke, maloom hai shayad aap ko pata ho ke multiple log assign hote hain ek subtask mein to woh differentiate karna ke kaun banda actually kaam kar raha hai us mein issue hai. | [Second speaker] Yes, there is an issue in this with [unclear], maybe you know that when multiple people are assigned to a subtask, there is an issue differentiating who is actually doing the work. |`

`| 00:48 | Achha yes, woh bhi maine us... achha hua yeh bhi yaad karwa diya aap ko. | Oh yes, that too, I... good thing I reminded you of this as well. |`

`| 00:52 | Yeh bhi... us mein ek cheez thi... | This too... there was one thing in it... |`

`| 00:57 | Woh ek separate hai is se. Woh yeh tha ke let's say hum ne jab yeh task reallocate kiya is ko kisi ko... | That's separate from this. That was, let's say when we reallocated this task [closes modal, clicks the Assignee icon on Accounts - Year End - CT600] to someone... |`

`| 01:04 | Theek hai, Partner ko ya kisi ko... Assignees ko mainly. | Right, to a Partner or someone... to Assignees mainly [clicks on the Assignee icon and switches to the Employees tab]. |`

`| 01:09 | Assignees ko jab kiya to is ko yeh subtask bhi reallocate... Woh mujhe bata raha tha ke let's say ke agar Ali hai task ke saath, aur maine agar reallocate kiya Waqas ko, main task to ho raha hai lekin subtask mein Ali aur jo bhi pehle number the wahi bande nazar aa rahe hain. | When done for Assignees [selects Thomas Hughes], this subtask should also reallocate... He was telling me that let's say if Ali is on the task, and if I reallocate it to Waqas, the main task gets updated, but in the subtask, Ali and whoever the previous members were are still showing up. |`

`| 01:26 | Aisa to nahi hai? Woh subtask bhi Ali ko hi saare hone chahiyein. | Is that not the case? All those subtasks should also be assigned to Ali [meaning the newly assigned person]. |`

`| 01:30 | [Second speaker] Ji us mein [unclear] yahi ke jo aap ne changes ki hain woh jo naya task aur subtask bhi ho us mein change ho. | [Second speaker] Yes, in that [unclear] is that the changes you made should update in the new task and subtask as well. |`

`| 01:39 | Aur let's say ke maine jo task mein ja ke allocate kiye hain us mein kya hoga phir? | And let's say what I went into the task and allocated, what will happen in that case then? |`

`| 01:44 | [Second speaker] Us mein... us mein bhi sirf task hi ho raha hai, woh subtask nahi change ho raha. | [Second speaker] In that... in that too, only the task is updating, the subtask is not changing. |`

`| 01:48 | Achha is ke subtask mein bhi hona chahiye. Is mein hona yeh chahiye ke main us ko main... main task and subtasks, to woh subtask us ko select kare to subtask mein bhi ho jaana chahiye phir. | Okay, it should happen in its subtasks too. What should happen in this [closes modals, returning to the main Clients list] is that I give it [an option for] main task and subtasks, so if one selects subtasks, it should update in the subtasks as well then. |`

`| 02:00 | [Second speaker] Haan, ek matlab checkbox daal dein. | [Second speaker] Yes, meaning put a checkbox. |`

`| 02:01 | Checkbox daal dein, haan. Ya us ko hum auto-select kar ke rakhein, us ko kahein ke exclude kare. Exclude if you don't want... haan. | Put a checkbox, yes. Or we keep it auto-selected and say to exclude. Exclude if you don't want... yes. |`

`| 02:11 | [Second speaker] Default jo hai woh select... | [Second speaker] By default, it is selected... |`

2026-11-09-clients-22e0ad0e.md

`# Clients | Remindoo – 9 November 2026`

`- Loom: https://www.loom.com/share/22e0ad0e53554656baab0d80af450432`

`- Recorded: 9 Nov 2026 · Length: 2:56`

`- Two speakers; Gemini marks them inside the text as [First speaker] / [Second speaker]. Sent to Gemini as a compressed copy (1280 px) to fit its upload limit.`

`- Transcribed by Gemini (Remindoo Dev workspace account) on 13 Nov 2026 from the downloaded video. Loom had no transcript for it. Roman Urdu is as Gemini heard it; the English is Gemini's translation; notes in [square brackets] are Gemini's description of the screen. Timestamps are approximate.`

`| Time (mm:ss) | Roman Urdu, as spoken | English translation |`

`|---|---|---|`

`| 00:00 | Yeh dekhen jaise yeh hain cheezen. Pehli cheez yeh hai ke in ke hamare paas yeh jo statuses hain yeh aane chahiyen. Mandate active hai, yeh dekhen mandate status aa raha hai. | Look, like these [points at the client list in Remindoo CRM] things. The first thing is that we should get these [switches to the GoCardless Customers tab and hovers over the Mandate status column] statuses. The mandate is active; look, the mandate status is showing up. |`

`| 00:10 | Yeh aap pull karen aur GoCardless ka logo saath le ke aayenge yahan par, theek hai clients mein. | You pull this and bring the GoCardless logo along with it here [switches to Client Custom Fields tab, then back to the Remindoo Clients list], okay, in Clients. |`

`| 00:15 | Achha jab woh hamare, sorry yahan par, woh hamare paas aa gaya so maine kya karna hai us ka filter laga ke I'll pick up the clients who do not have a direct debit aur main un ko email karunga. | Okay, when that is in our—sorry, here [points at the Remindoo Clients table]—when we get that, what I will do is apply its filter [clicks the Filter icon] and I'll pick up the clients who do not have a direct debit [selects clients and clicks the email icon], and I will email them. |`

`| 00:25 | Again template bana kar main kahunga yaar ke yahan se direct debit set up karo. Theek hai woh again woh main us mein yeh is ka link nikal aata hai to link daal ke email draft kar lunga. | Again, after creating a template [clicks inside the email body box], I will say, "Hey, set up direct debit from here." Okay, again, in that—its link comes out [switches briefly to Client Custom Fields], so I will draft an email by putting the link in [switches back to Remindoo Clients]. |`

`| 00:34 | Theek hai aur jis ka jaise hi direct debit set up hota hai woh automatically yahan par aana chahiye. Theek hai? Yeh Adfin ka bhi hona chahiye aur is ka bhi hona chahiye. Theek hai? | Okay, and as soon as someone's direct debit is set up, it should automatically show up here [moves cursor over the client status icons]. Okay? This should be for Adfin as well as for this [GoCardless]. Okay? |`

`| 00:44 | Achha us ke ilawa um is mein ek aur cheez jo honi chahiye column visibility mein jo ke nahi hai. Let's say column visibility mein ek to yeh maine bataya aap ko ke yaar yeh agar wahan par 100 hain to yeh bhi ek page pe 100 hi show hone chahiyen, yahan pagination ek jaisi honi chahiye. | Okay, apart from that, um, one more thing in this [clicks the Column Visibility icon] that should be there in column visibility, which isn't. Let's say in column visibility [switches to Client Custom Fields], first, as I told you, if there are 100 there, then 100 should show up on one page here too [points at the pagination controls at the bottom]; the pagination here should be uniform. |`

`| 01:04 | Secondly jab maine yahan pe dropdown kiya na, theek hai, to yeh dropdown wahan par bhi mujhe aana chahiye. Dekhen Tax Investigation Insurance hai ya next jaise hai, yeh nahi aata. Turnover Band hai jaise dropdown. | Secondly, when I selected dropdown here [hovers over 'Dropdown' under Field Type for Tax Investigation Insurance], okay, then I should get this dropdown there as well. Look, there is Tax Investigation Insurance, or like on the next page [clicks page 2 of Client Custom Fields], it doesn't show up. Like Turnover Band is a dropdown [points at Turnover Band's Field Type]. |`

`| 01:20 | Text hai to text hi hoga, dropdown hai to dropdown aana chahiye. Jaise main is mein agar jaun, let's see yeh pre-prod hai, main actual wale mein jaata hoon, theek hai. | If it's text, it will be text; if it's dropdown, a dropdown should appear. Like if I go into this [switches to Remindoo Clients tab, then to another browser tab with live Remindoo], let's see, this is pre-prod, I'll go into the actual one, okay. |`

`| 01:31 | Is mein main agar client mein jaun and if I pick up Turnover Band, to yeh Turnover Band mein mere paas dropdown nahi aa raha. Theek hai? So yeh zara dekhen ke yeh dropdown aana chahiye and then I should be able to select multiple. | In this, if I go into Clients [clicks Clients in the left sidebar, then clicks Filter] and if I pick up Turnover Band, then in this Turnover Band [clicks the value field next to Turnover Band], I am not getting a dropdown. Okay? So please look into this, that this dropdown should appear, and then I should be able to select multiple. |`

`| 01:48 | [Pauses while clicking around the filter modal, closing it, and hovering over client status icons, then briefly switches to Slack before returning to Remindoo] | [Silent pause while navigating the screen] |`

`| 02:09 | [Second speaker]: Sir, jo mandate status aur direct debit yeh dono ek hi cheez hai? [First speaker]: Ek hi cheez hai. Direct debit payment method hai, mandate status status basically us ka jis ka active... | [Second speaker]: Sir, are mandate status and direct debit both the same thing? [First speaker]: It's the same thing. Direct debit is the payment method, and mandate status is basically the status of the one whose [mandate] is active [switches to the GoCardless Customers tab]... |`

`| 02:18 | [Second speaker]: [unclear] [First speaker]: Yes, hamein authorize kiya hai we can take the payment. Theek hai? | [Second speaker]: [unclear] [First speaker]: Yes, [the customer] has authorized us so we can take the payment [hovers over the green 'Active' badge tooltip]. Okay? |`

`| 02:26 | So yeh hai, achha is mein ab active wala yeh dekhen All mein yeh bhi aa rahe hain status: no mandate, cancelled, no mandate. Jin ka hai, they are our client but they don't have a mandate. | So that's it. Okay, in this [switches briefly to Remindoo and back to GoCardless], now the active ones—look, in 'All' [clicks the 'All' filter tab], these statuses are also showing up: 'No mandate', 'Cancelled', 'No mandate' [hovers over the 'No mandate' and 'Cancelled' badges]. Those who have this, they are our clients, but they don't have a mandate. |`

`| 02:37 | Theek hai? So in ka isi tarah se aana chahiye: active hai, no hai, cancelled hai, jo bhi hai. So we can see ke kis ke kya statuses hain. | Okay? So theirs should show up in the exact same way: whether it's active, no [mandate], cancelled, whatever it is. So we can see who has what statuses. |`

`| 02:45 | [Second speaker]: To yeh wali hum linking tab kar sakte hain jab woh jo apna tenant hai woh GoCardless account connect karega tabhi hum linking kar sakte hain is ki, theek hai. [First speaker]: Yes, theek hai. | [Second speaker]: So we can do this linking only when our tenant connects their GoCardless account, only then can we link this, okay. [First speaker]: Yes, okay. |`


