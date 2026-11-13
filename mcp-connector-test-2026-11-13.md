# Remindoo MCP: connector test against the question set

**Tested:** 13 Nov 2026 (server date 2026-11-13), through the Remindoo connector in Claude
**Against:** `mcp-question-status-for-team.md` (86 done, 7 blocked, 9 data checks, 4 security tests)
**Login:** Michael Eldred Clark · tenant **Document Testing Tenant 2** · scope `read` · server `0.0.0-dev`, spec 2026-07-28
**Role seen by the MCP:** can view **all tasks** (whole practice) but only **allocated clients** (16), so every client-scoped tool ran as `assignee: "me"`.

## Summary

| Result | Of the 86 "done" questions |
|---|---|
| PASS (incl. pass on empty or thin data) | **59** |
| PARTIAL (works, but the answer misleads or leaves something out) | **10** |
| FAIL (error, or a promised behaviour missing) | **12** |
| CONFLICT (two tools give opposite answers) | **5** |

- **Blocked 7:** all 7 behave correctly. No tool claims an answer it can't give.
- **Security 4:** 3 pass, 1 partial (only one role could be tested).
- **Data checks 9:** this tenant fails most of them (no HMRC data, almost no timers). So many "passes" are passes on empty data.

**Bottom line:** the "86 of 93 done, built and tested" status does not hold on this connector. 17 questions fail or contradict another tool. Most come from **two defects that are cheap to fix**: one tool's broken SQL, and output schemas missing new list values. Check first whether the connector runs an older build than the code the status doc describes (`0.0.0-dev`). Several failures look like a partial deploy.

---

## Fix first (root causes, by impact)

| # | Defect | Questions hit | Evidence |
|---|---|---|---|
| 1 | **`find_team_performance`: 5 of 6 reports throw SQL errors.** Only `by_person` works. | Q28, Q34, Q37, Q38, Q39, and the board report Q90 | `adherence` → *could not determine data type of parameter $4* · `engagement` → *…$5* · `trend` → *…$2* · `by_manager` → *column m.manager does not exist* · `by_reviewer` → *subquery in FROM must have an alias*. Same error on every retry, every window, both scopes. |
| 2 | **Output schema out of step with input schema.** The tool accepts the value, then rejects its own answer. | Q70, Q72, Q86, Q87 | `find_invoicing report:"credits"` and `find_clients list:` `no_engagement_letter` / `unsigned_documents` / `unanswered_automated_emails` → *Output validation error … expected one of …* (the old enum). |
| 3 | **Invoices: `find_invoicing` and `client_summary` disagree.** | Q63–Q67 | `client_summary("L.T.D CARS LTD")`: 3 invoices, £466 billed, **£466 overdue** (2 overdue), last 22 Sep. `find_invoicing` overdue / aged_debtors / billed / by_client / by_service all return **0**, `currencies_present: 0`. If those invoices count as "not sent", say so; as it stands a partner gets "nobody owes us" and "£466 overdue" from the same system. |
| 4 | **"Completed last week" always returns nothing.** | Q9 | `date_field:"completed_at"` with no status still applies the default open-status filter (`Not started / In-Progress / Awaiting Feedback`). Result: 0 for all of 2026. With `status:"Complete"` it returns 8. The tool text says "no status filter is needed". |
| 5 | **`include_last_contact` returns `null`.** | Q11 | `last_contact: null` on every row tested. The status doc promises `emails_sent: 0` instead of nothing, and that's the point of Q11. |
| 6 | **Hours on tasks with no client vanish from `by_client`.** | Q48, Q57 | Timesheets 2026: entries total 1.34 h, `by_client` total **0.18 h**, `unattributed_hours: 0`. The missing 1.16 h (87%) is on tasks with no client. It's in no total and coverage doesn't show it. `by_service` handles the same hours correctly. |
| 7 | **Next-month demand ignores tasks not yet generated.** (design) | Q43, Q45 | `demand_vs_capacity` Dec: 35 jobs, 51.6 h. `find_upcoming_recurring_tasks` Dec: **1,280 tasks** to be generated. Future windows will always look under-loaded. |
| 8 | Raw Postgres errors are returned to the caller. | security | Column and alias names leak (see #1). Return a generic error and log the detail. |

---

## Results by section

Example names swapped for real ones in Tenant 2: **ABC Ltd → L.T.D CARS LTD**, **XYZ Ltd → maddy pvt 2**, **Raza → Jack kane**, **Fatima → Michael Eldred Clark**. (Literal "ABC Ltd" → `found: "none"`, no guess. Correct.)
Windows: this week 9–15 Nov · this month 1–30 Nov · last week 2–8 Nov · last month 1–31 Oct · this quarter Oct–Dec · next month Dec 2026.

### 1. Tasks: 12 pass, 2 fail

| # | Result | What came back |
|---|---|---|
| 1 | PASS | 19 tasks due 9–15 Nov |
| 2 | PASS | 602 overdue; grouping partial (`complete:false`). Groups add to 300, but the tool text says the cap is 250. Check. |
| 3 | PASS | 562 overdue > 14 days, owners and roles shown |
| 4 | PASS | 24 not started, due 13 Nov–13 Dec |
| 5 | PASS | Info Req 5,588 · WIP 60 · Review 2 · With Client 0 · Filed/Completed 2 (sum = 5,652 open ✓). Status *Complete* (12) needs a separate call. |
| 6 | PASS | 0 (no tasks in With Client), coverage complete |
| 7 | PASS | 2 under review; reviewer not recorded (shown correctly as empty) |
| 8 | PASS | 12 due in the next 4 days |
| 9 | **FAIL** | Defect #4 |
| 10 | PASS | 0 unassigned, but only 250 of 5,652 checked (flagged partial ✓) |
| 11 | **FAIL** | Defect #5 |
| 12 | PASS | 4 open tasks for L.T.D CARS LTD |
| 13 | PASS | 0 due today for Michael |
| 14 | PASS | Dec: 60 schedules, 1,280 tasks; `behind`, date-unknown (16) and not-generating (2) flagged |

### 2. Statutory deadlines: 12 pass, 1 partial

All the client-scoped tools refuse `anyone` for this role, cleanly. HMRC data is empty (0 of 16 clients), so Q17, Q18 and Q20 pass on empty data, and the tools say so.

| # | Result | What came back |
|---|---|---|
| 15 | PASS | 0 in 60 days; only 1 of 16 clients has a CH date; onboarding caveat shown |
| 16 | PASS | 0 CT600 tasks in 30 days |
| 17–20 | PASS | 0 each, coverage 0/16 (VAT, CT, SA) and 1/16 (CS). Bad inputs refused clearly (date range + `overdue`; PAYE `due`). |
| 21 | PASS | 2 SATR tasks in Info Requested |
| 22–23 | PASS | 0 payroll / CIS this month |
| 24 | PASS | 7 in MTD scope: 6 undetermined (nothing recorded), 1 below threshold |
| 25 | PARTIAL | NM ABAYA LTD year end 31 Dec returned, but `work_started: null` although it has open tasks. With 5,652 open tasks this may always be null, so the "nobody has started it" gap never shows. |
| 26 | PASS | Oct: 80 deadlines, 1 filing recorded; "silent ≠ missed" caveat shown |
| 27 | PASS | 12 months: 2 late, nobody late twice; `window_starts_before_records` flagged; totals add up |

### 3. Team performance: 6 pass, 5 fail

| # | Result | What came back |
|---|---|---|
| 28 | **FAIL** | `adherence` SQL error |
| 29 | PASS | Jack kane 362, Michael 279 overdue; coverage shown. Check: the figure moves with `date_to` (Michael 267 → 275 → 279 for 31 Oct / 13 Nov / 30 Nov), and 275 for today ≠ `find_tasks` 267. |
| 30–33 | PASS | Completed / on-time / late per person; Accounts YTD averages in both measures; numbers, no verdicts |
| 34 | **FAIL** | `engagement` SQL error |
| 36 | PASS | Oct vs Nov both return |
| 37 | **FAIL** | `by_manager` SQL error |
| 38 | **FAIL** | `trend` SQL error |
| 39 | **FAIL** | `by_reviewer` SQL error |

### 4. Capacity: 3 pass, 2 partial

| # | Result | What came back |
|---|---|---|
| 40 | PASS | Jack kane 83% (33.2 of 40 h), 332 waiting jobs kept out of load; Michael shown as unknown (no hours), sorted last |
| 41 | PASS | 5 Accounts jobs at 5.7 h each: 5 people can take them. Check: rana maddy and Philip THOMAS are missing from the headroom rows. |
| 42 | PASS | 26 person × service rows |
| 43 | PARTIAL | Defect #7 |
| 45 | PARTIAL | Defect #7. Also, lines with jobs but 0 people (Accounts, Payroll & PAYE, 12ert) show shortfall 0, which reads as "balanced". |

### 5. Timesheets: 6 pass, 1 partial

The tenant has 15 time entries ever (1.34 h, Aug–Sep).

| # | Result | What came back |
|---|---|---|
| 46 | PASS | 0 h this week, 0 of 8 people logging |
| 48 | PARTIAL | L.T.D CARS LTD 0 h; defect #6 |
| 49–52 | PASS | By service; the one overrun ("test dash" 1.07 h vs 1.0 h); Michael's 3 September entries |
| 53 | PASS | September: both utilisation figures. November returns no rows at all rather than everyone at 0%. |

Check: the same task is linked to different clients in two tools. "for kane" and "new detailed task" show **maddy pvt ltd** in `find_tasks` but **maddy pvt 2** in timesheet entries.

### 6. Billable: 5 pass, 1 partial

Q54, Q55, Q58, Q59 and Q60 pass. All time is non-billable, so Q59 and Q60 are empty. Q57 is PARTIAL (defect #6).

### 7. Invoicing: 2 pass, 5 conflict, 1 fail

The invoice permission is granted. Q62 passes (8 completed jobs not invoiced). Q69 passes (18 clients of WIP, valued at the rate you supply, coverage shown). **Q63–Q67 are CONFLICT** (defect #3). **Q70 FAILS** (defect #2).

### 8. Clients: 6 pass, 1 fail

| # | Result | What came back |
|---|---|---|
| 71 | PASS | One-page summary. Check: it shows 3 open tasks (`all_found: true`) where `find_tasks` shows 4 (missing "VAT … 02-07-26"). |
| 72 | **FAIL** | Defect #2 |
| 74–78 | PASS | 1 with no manager; counts by service, type and manager; 0 onboarded in Nov; 4 left; 6 with open document requests |

### 9. Leads and proposals: 5 pass

Q79–Q82 pass (12 leads, 7 converted, 58%; 7 proposals sent and unsigned after 14 days, £5,010.77). Q83 passes, with a check: "QA Recheck Lead 13 Nov" was **added today** but shows a last contact on 29 Oct. Contact history looks matched by email address, not by lead.

### 10. Documents and emails: 1 pass, 1 partial, 2 fail

Q84 passes. Q85 is PARTIAL: `last_contact` is all null **and `source: null`**, so you can't tell "never emailed" from "no mailbox". **Q86 and Q87 FAIL** (defect #2). The data exists: `client_summary` shows a document awaiting signature since 17 Sep.

### 11. Partner reports (built from the tools; the prompts file isn't in the notes)

| # | Result | Why |
|---|---|---|
| 88 Weekly summary | PARTIAL | Billing inputs conflict (#3) |
| 89 Top 5 risks | PARTIAL | Team and unsigned-document inputs broken |
| 90 Board report | **FAIL** | Adherence errors; revenue and debtors conflict |
| 91 Partner focus today | PASS | |
| 92 Escalations | PARTIAL | Unsigned-documents list broken |
| 93 This quarter vs last year | PARTIAL | `by_person` works; filing history correctly says Q4 2025 predates its records; no adherence |

---

## The 7 blocked questions: all behave correctly

Q35, 44, 47, 56, 61, 68 and 73: no tool or parameter claims an answer, and the tool descriptions tell the model to say so (leave not recorded, checklist ticks unrecorded, no fee type, and so on). **Risk to watch:** for Q35 and Q47, `by_person` returns people with zeros or no rows. A model that skips the tool text could read that as "idle" or "didn't submit".

## The 9 live-data checks (Tenant 2)

| # | Check | Tenant 2 |
|---|---|---|
| 1 | Service names match what users type | **No.** "Self Assessment" and "Corporation Tax" silently match 0; the services are "Personal Tax Return - SATR" and "Accounts - Year End + CT600". |
| 2 | HMRC crawler has run | **No.** 0 of 16 clients have data. |
| 3 | Turnover recorded | **Thin.** 1 of 7 MTD-scope clients. |
| 4 | Practice runs timers | **No.** 1.34 h ever, nothing since 22 Sep. |
| 5 | Estimates filled in | Partly. 22 jobs this week have no estimate. |
| 6 | Weekly hours recorded | Mostly. 7 of 8 staff; the test login has none. |
| 7 | Invoices raised in Remindoo or imported | Inconclusive (defect #3). |
| 8 | Billable flag set on jobs | Yes on jobs (5 unmarked), but every time entry is non-billable. |
| 9 | Mailboxes synced, engagement date used | Partly. Lead mailbox records exist; client `last_contact` is null everywhere; the engagement list errors (#2). |

## The 4 security tests

| # | Attempt | Result |
|---|---|---|
| 99 | Another firm's data | **PASS.** No tool takes a tenant; an extra `tenant` argument is rejected (*Unrecognized key*); scope always comes from the token. |
| 100 | Staff role asks for partner fees and salaries | **PARTIAL.** Only one login was available. Role gating fails closed with clean messages, and no output contains a rate or salary. Check: Michael is listed as *Admin* yet the MCP limits him to allocated clients. Confirm that matches his real permissions. |
| 101 | UTR and bank details | **PASS.** No such field in any output. Lead and proposal emails and phone numbers *are* returned, by design. |
| 102 | Delete overdue tasks | **PASS.** 18 tools, all read-only; token scope is `read`. |

## Smaller things to check

- `find_tasks` grouping cap: groups add to 300, but the tool text says 250.
- Recurring forecast includes a **frozen** client ("QA S3 Remaining Ltd"). Does the nightly job skip frozen clients?
- WIP `oldest_job_on` looks like the creation date (e.g. 11 Nov for 2023 tasks), not the deadline.
- `find_leads` coverage reports 1,198 candidates against 12 leads.

## Test notes

- About 110 tool calls, read-only, nothing written to Remindoo.
- Tenant 2 is mostly junk test data: one service has 5,652 open tasks dating from 2023. Counts are only useful as shape checks.
- A "pass on empty data" means the tool answered correctly *and* its coverage made the emptiness visible. It doesn't prove the figures are right on real data.
