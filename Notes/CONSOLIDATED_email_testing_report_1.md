# Remindoo CRM (preprod): Consolidated Email Testing Report — Mailbox Connected vs Disconnected

**Environment:** preprod-crm.remindoo.co (beta, test data only) · **User:** Test User (tenant "Document Testing Tenant 1") · **Date:** 27 Sep 2026 · **Tester:** Claude

**Recipients:** only suhaib.accotech@gmail.com and its + aliases. Every result was checked in that Gmail inbox (actual From header) and, for campaigns, in Settings → Campaign Management.

**Built from:** the connected-run reports `00`–`07` and the disconnected-retest reports `D00`–`D06`. No new tests were run for this report. Test IDs (L1, DC-L3, …) point back to those reports.

## Key takeaways

- **Connected:** everything sent "from linked account" (Leads, Proposals, Tasks, Clients bulk of 20 or fewer, Emails module, Invoices) came from **dev@remindoo.co**. Campaigns and system emails came from **mail@remindoo.co**. Every attachment tried while connected was delivered.
- **Disconnected:** linked-only actions in Leads and Clients are **blocked with a clear message** ✅. Lead-profile emails, Proposals, Tasks and Invoices **silently switch to mail@remindoo.co**. System emails (portal invite, reminders, checklist, e-sign, Settings test email) are unaffected.
- **Four things go wrong when disconnected:**
  1. 🚨 Emails → Compose sends from an unrelated Gmail, **aftab.zaheer.accotech@gmail.com**.
  2. Lead-profile and campaign emails **with attachments fail** (S3 permission error in the campaign sender). Campaigns with attachments probably fail while connected too; that wasn't tested.
  3. Those failures are **reported as successes** in the popups and logs.
  4. Users aren't told their emails now come from the **no-reply** mail@ address.
- Suhaib **disconnected the mailbox manually** for this test (between 16:37 and 17:16 UTC). Apart from a small "From: No connected accounts" line in send popups, nothing in the app shows that it's disconnected.
- Most other issues (hidden recipients, split email history, read-only recipient fields, e-sign problems, dev/localhost/Vercel links) **exist in both states**.

## 1. Test conditions

| Run | When (27 Sep, UTC) | Mailbox state | Reports |
|---|---|---|---|
| Connected | Up to 16:37 (last confirmed dev@ send, QA-B6) | Email Connections: **dev@remindoo.co** (Google, "Company Email", Connected) | 00–06, start of 07 |
| Transition | 16:37–17:16 | Disconnected manually by Suhaib for testing, at some point in this window | 07 (07-S1 and 07-C1 were sent here; state unknown) |
| Disconnected | 17:16–17:21, then 20:10–20:37 | Email Connections shows only **"Connect Company Email"** (Google / Outlook) | End of 07, D00–D06 |

**Senders**

- **dev@remindoo.co**: the connected Google mailbox ("Send from linked account").
- **mail@remindoo.co**: Remindoo's system and campaign sender. It adds a "This is an automated email from Remindoo. Please do not reply…" footer.
- **aftab.zaheer.accotech@gmail.com**: unexpected. Seen only from the Emails module while disconnected.

**Difference flags used below**

| Flag | Meaning |
|---|---|
| 🟢 Same | Identical in both states |
| 🔵 Changed, correctly | Blocked with a clear message when no mailbox is connected |
| 🟠 Changed silently | Still delivered, but from a different sender or pipeline, and the user isn't told |
| 🔴 Changed and broken | Fails, reports a false success, or sends from the wrong account |
| — | Only tested in one state |

## 2. At a glance: every entry point in both states

| Module | Entry point | Connected | Disconnected | Δ |
|---|---|---|---|---|
| Leads | Quick-view → Send Lead Email (linked) | dev@ ✅, PDF + PNG delivered (L1) | Blocked: "Connect an email account… or choose Create campaign" (DC-L1) | 🔵 |
| Leads | Quick-view → Create campaign, with PDF | Not tested | Timeline says "Email Sent"; campaign **Failed** (DC-L2) | 🔴 |
| Leads | Profile → Communication → Send New Email | dev@ ✅, PDF delivered, tokens replaced (L2) | Becomes a mail@ campaign. With PNG: "Email sent successfully" and logged Success, but **Failed** (DC-L3) | 🔴 |
| Leads | Profile → Quick Access → Send New Email | dev@ ✅ (L3) | No attachment: mail@ ✅ (DC-L6). With PNG: **Failed** (QA-L6) | 🟠 / 🔴 |
| Leads | Bulk → Send from linked account (20 or fewer) | dev@ ✅, 1 email per lead (L4, B4) | Blocked (DC-L4) | 🔵 |
| Leads | Bulk → Create campaign | mail@ ✅, tokens **not** replaced (L5) | mail@ ✅ (DC-L5) | 🟢 |
| Leads | Bulk, 21 or more records | Linked option greyed out; forced campaign; mail@ ✅ (B3) | Not retested (campaign-only in both states) | — |
| Proposals | New Proposal → Send Email to Lead | dev@ ✅ (P1) | mail@ ✅ (DC-P2) | 🟠 |
| Proposals | Resend Proposal | dev@ ✅ (P2) | mail@ ✅ (DC-P1) | 🟠 |
| Tasks | Email Logs → Send New Email | dev@ ✅ (T1) | mail@ ✅ (DC-T1) | 🟠 |
| Tasks | Personal task reminder (R1, due 28 Sep) | Saved | Not received in the test inbox as of 28 Sep 00:30 UTC | ⏳ |
| Clients | Bulk → Send from linked account (20 or fewer) | dev@ ✅ (C1, B6) | Blocked, but still the default option (DC-C1) | 🔵 |
| Clients | Bulk → Create campaign | mail@ ✅ (C2) | mail@ ✅, tokens replaced (DC-C2) | 🟢 |
| Clients | Bulk, 21 or more records | Forced campaign; mail@ ✅ (B5) | Not retested | — |
| Clients | Client Portal Management → invite | mail@ ✅ (C3) | mail@ ✅ (DC-C4) | 🟢 |
| Clients | Services → Reminders → service reminder, with PDF | mail@ ✅ (07-S1, state unknown) | mail@ ✅ (DC-S1) | 🟢 |
| Clients | Services → Reminders → checklist reminder | mail@ ✅ (07-C1, state unknown) | mail@ ✅, with PDF (DC-C3) | 🟢 |
| Clients | E-Signature → invite / "Document Signed" | Not tested | mail@ ✅, with issues (07-E1, 07-E2) | — |
| Emails | Compose | dev@ ✅, CC + BCC + PDF + PNG (E1) | 🚨 **aftab.zaheer.accotech@gmail.com** (DC-E1, DC-E1b) | 🔴 |
| Emails | Reply All / Forward | dev@ ⚠️ wrong recipients / corrupted body (E2, E3) | Not available (empty inbox) | — |
| Invoices | New Invoice → Approve & send | dev@ ✅ (I1) | mail@ ✅ (DC-I2) | 🟠 |
| Invoices | Preview → Send reminder | dev@ ✅ (I2) | mail@ ✅ (DC-I1) | 🟠 |
| Settings | Email Composer → Send Test Email | mail@ ✅ (06-S1) | mail@ ✅ (DC-S) | 🟢 |
| Dashboard, Knowledge Base, Financial Assistant | — | No email features | No email features | 🟢 |

## 3. Standout differences: what the disconnect exposes

### 3.1 🚨 Critical: the Emails module sends from an unrelated person's Gmail

- **Connected:** Compose sends from dev@remindoo.co (E1).
- **Disconnected:** the page shows "All Accounts 0" and an empty inbox. But Compose stays enabled, and both test emails were delivered **from aftab.zaheer.accotech@gmail.com** (DC-E1, DC-E1b).
- That address isn't visible anywhere in the tenant. Email Connections is empty, and Edit Own Profile shows "Employee not found".
- The inbox respects the missing connection but sending doesn't. That suggests the send endpoint falls back to another stored mailbox token when the tenant has none.
- **Impact:** users can send as another person or company without knowing it, and the sent copy lands in that person's mailbox.
- **Fix:** scope the mailbox lookup to the tenant and user, and disable Compose when no account is connected.

### 3.2 🔴 High: the fallback path can't send attachments

- **Connected:** lead-profile emails go through the Gmail mailbox, and attachments are delivered (L2).
- **Disconnected:** the same emails are re-routed into the campaign sender (they show up in Campaign Management), and **every campaign with an attachment fails**:

  > `User: arn:aws:sts::084375583143:assumed-role/dev-campaign-sender-lambda-role/dev-campaign-sender is not authorized to perform: s3:ListBucket on resource: "arn:aws:s3:::remindoo-emails-dev"`

- The lead profile is the one place the spec allows attachments, and it's exactly what breaks.
- Service and checklist reminders deliver attachments from mail@ in both states, so only the **campaign sender** is affected.
- **Probably broken while connected too:** the Leads quick-view offers "Create campaign" with an attach option, and that uses the same sender (DC-L2). It wasn't tested with the mailbox connected. This also breaks the spec rule that a visible attach option must not stop the email working.
- **Tokens may be at risk too:** in the connected run, Leads campaigns sent `::Name of Lead Handler ::` as literal text (L5), while Clients campaigns replaced `::Client Name::` (DC-C2). Fallback lead-profile emails with tokens weren't tested.
- **Fix:** give the campaign sender's role read access (`s3:GetObject`, `s3:ListBucket`) to the attachments bucket, and check that it reads the bucket and key the preprod app actually writes to. The role and bucket are "dev"-named in preprod. If the error changes to "not found" once the permission is added, the path is wrong.

### 3.3 🔴 High: success is reported when the email is queued, not when it's sent

- **Connected:** the mailbox sends immediately, so "Email sent successfully" is accurate.
- **Disconnected:** the same toast appears, the Communication tab logs **Success**, and the quick-view adds "Email Sent" to the Timeline. A few minutes later, the campaign goes from "Processing" to **Failed** (DC-L2, DC-L3, QA-L6).
- The failure is only visible in Settings → Campaign Management, as raw AWS text plus "Please retry this campaign from the bulk action". Profile emails have no retry, and the bulk action has no attach option.
- **Fix:** show "queued", update the record's log when the campaign finishes, and notify the sender if it fails.

### 3.4 🟠 High: there's no single rule for "no mailbox connected"

| Behaviour | Where |
|---|---|
| Blocked with a clear message ✅ | Leads quick-view (linked), Leads bulk (linked), Clients bulk (linked) |
| Silently re-routed to a mail@ **campaign** | Lead profile: Communication, Quick Access |
| Silently sent from **mail@** | Proposals, Tasks, Invoices |
| Sent from **another account** 🚨 | Emails module |

- Every popup shows "From: No connected accounts" with a "Connect Email" link, but most still send. The Invoice popup still says "Emails will be sent from your linked mailbox".
- The Clients bulk modal still defaults to "Send from linked account", although the same modal already greys that option out for 21 or more records.
- **Fix:** have one backend check pick the sender for every send (the connected mailbox, an explicit mail@ fallback, or a block), and have the popup always show the real From address.

### 3.5 🟠 Medium: nothing shows that the mailbox is disconnected, and it changes what clients receive

- The only sign of the disconnect (done manually for this test) is a small "From: No connected accounts" line in send popups. There's no banner, and nothing tells other users of the tenant.
- After the disconnect, emails that had come from a real mailbox came from mail@ with a "Please do not reply" footer. Client replies (e.g. to proposals and invoices) no longer reach the practice.
- **Fix:** show a banner while the company mailbox is disconnected (and email an admin), and state the actual sender in every popup.
- Not covered: how the app behaves when the Google token expires or is revoked without anyone disconnecting it.

### 3.6 🟠 Medium: where sent emails are recorded depends on the state

- **Connected:** linked sends land in dev@'s Sent folder (visible in the Emails module, with no link to the record), plus each module's own log.
- **Disconnected:**
  - Lead fallback sends appear as campaigns in Campaign Management, which lists only the record's first address.
  - Tasks still logs sends in Email Logs.
  - I didn't check whether Proposals and Invoices fallback sends appear in Campaign Management.
  - Nothing reaches a mailbox.
- **In both states:** Leads splits history between the Timeline and Communication tabs, and the client timeline and invoice audit log record no sends.

### 3.7 🟢 What stayed the same

- All system emails from mail@: portal invite, service and checklist reminders (attachments work), e-sign, and the Settings test email.
- Campaigns without attachments, in Leads and Clients.
- The 20/21 bulk rule (connected run): 20 or fewer records go from dev@; 21 or more are forced into a campaign from mail@ (confirmed as intended).

## 4. Module by module

### 4.1 Leads (reports 01, D01, 07)

| Entry point | Connected | Disconnected | Δ |
|---|---|---|---|
| Quick-view → Send Lead Email (linked) | **L1:** dev@; 2 To + BCC; PDF + PNG delivered | **DC-L1:** blocked with a clear message | 🔵 |
| Quick-view → Create campaign | Not tested | **DC-L2 (PDF):** Timeline "Email Sent"; campaign **Failed** (S3) | 🔴 |
| Profile → Communication (template "lead-mail") | **L2:** dev@; 3 To + BCC; PDF delivered; tokens replaced | **DC-L3 (PNG):** "Email sent successfully", Communication **Success**; campaign **Failed** | 🔴 |
| Profile → Quick Access | **L3:** dev@; 2 To (invalid chip dropped) | **DC-L6 (no attachment):** mail@ campaign, delivered to both addresses · **QA-L6 (PNG):** **Failed** | 🟠 / 🔴 |
| Bulk → linked (2 leads) | **L4:** dev@; 1 email per lead; tokens resolved | **DC-L4:** blocked | 🔵 |
| Bulk → campaign (2 leads) | **L5:** mail@; tokens **not** replaced | **DC-L5:** mail@; delivered | 🟢 |
| Bulk, one lead with 25 addresses | **B1:** 1 email, all 25 in To, dev@ | Not retested | — |
| Bulk, 22 / 21 / 20 leads | **B3:** 22 → forced campaign, mail@ · 21 → linked greyed out · **B4:** 20 → dev@ | Not retested | — |

**Issues in both states**

- The quick-view modal has an attach option, which the spec doesn't include. In campaign mode it breaks sending (DC-L2).
- Email history is split. Quick-view and bulk sends go to the Timeline only; profile sends go to Communication only.
- Recipients:
  - Quick-view recipients are read-only, and there's no CC field.
  - Invalid addresses (`notanemail`) are accepted and silently dropped.
  - The Primary Contact is never pre-filled.
  - All of a record's addresses go in To, so recipients see each other. Campaign Management lists only the first address.
- The Communication log preview shows raw tokens, and no BCC or attachments.
- UX:
  - The body editor is unreachable at about 1077×643.
  - The Subject field drops fast keystrokes.
  - Create Lead hangs if the custom fields haven't loaded.
  - Converted leads can't be edited ("Lead data not found").
  - The Primary Contact panel doesn't refresh after saving.
  - The campaign count badge shows the page's rows, not the total.

**Only when disconnected:** profile emails switch silently to mail@; attachments fail; failures are reported as successes; the error log shows raw AWS text.

### 4.2 Proposals (reports 02, D02)

| Entry point | Connected | Disconnected | Δ |
|---|---|---|---|
| New Proposal → Send Email to Lead | **P1:** dev@; 3 To + pre-filled BCC; status → Sent | **DC-P2:** mail@; 2 To (new lead "DC Proposal Lead") + pre-filled BCC; status → Sent | 🟠 |
| Resend Proposal | **P2:** dev@; tokens replaced | **DC-P1:** mail@; popup shows "From: No connected accounts" | 🟠 |

**Issues in both states**

- No attach option (matches the spec). The lead gets a "Click Here to Sign this Proposal" link, not a PDF.
- The "do not reply" footer appears even when the email is sent from the real dev@ mailbox.
- BCC is pre-filled with the lead's first email address, which is also in To.
- Proposal Name can't be edited, so every proposal is called "New Document".
- The Primary Contact isn't included, and the Existing Lead dropdown lists only a few leads.

**Noticed in the retest:**

- "Sent Date" in the proposal list doesn't update on resend.
- On the new-lead step, an email address only counts once you click the green **+**.

### 4.3 Tasks (reports 03, D03, 07)

| Entry point | Connected | Disconnected | Δ |
|---|---|---|---|
| Task → Email Logs → Send New Email | **T1:** dev@; 2 To + BCC; `::Task Name::` replaced; logged | **DC-T1:** mail@; same; logged | 🟠 |
| Create Task → Create Reminder (personal reminder) | **R1:** saved for 28/09/2026 | Not received in the test inbox as of 28 Sep 00:30 UTC | ⏳ |

**Issues in both states**

- Recipients are read-only, although the helper text says "You can still add more". On the WILLY WONKA task this forces `sami.accotech@gmail.com` onto the email.
- No attach option (matches the spec), and the Primary Contact isn't included.
- Email Logs shows "From: Test User", not the sending address, and doesn't show BCC.
- Personal reminders:
  - Today's date can't be selected.
  - There's no recipient or time field.
  - Settings → Planned Reminders shows "No reminders found".
- The Tasks list briefly shows "All 0" while it loads.

**Noticed in the retest:** Email Logs dates the send 28-09-2026, while list views show sends from the same minute as 27-09-2026. The app seems to mix time zones.

### 4.4 Clients (reports 04, 07, D04)

Test IDs from report 07 have a "07-" prefix so they don't clash with report 04's C1–C3.

| Entry point | Connected | Disconnected | Δ |
|---|---|---|---|
| Bulk → linked (2 clients) | **C1:** dev@; 1 email per client + BCC | **DC-C1:** blocked, but still the default option | 🔵 |
| Bulk → campaign (2 clients) | **C2:** mail@ | **DC-C2:** mail@; `::Client Name::` replaced | 🟢 |
| Bulk, one client with 25 addresses | **B2:** 1 email, dev@ | Not retested | — |
| Bulk, 22 / 21 / 20 clients | **B5:** 22 → forced campaign, mail@ · 21 → greyed out · **B6:** 20 → dev@ | Not retested | — |
| Client Portal Management → invite | **C3:** mail@ | **DC-C4 (resend):** mail@ | 🟢 |
| Services → Reminders → "External" (Manage Emails → Send) | **07-S1:** mail@; PDF delivered (mailbox state unknown) | **DC-S1:** mail@; PDF delivered | 🟢 |
| Services → Reminders → "Test Doc Reminder" (checklist) | **07-C1:** mail@; checklist + Provide Information link (state unknown) | **DC-C3:** mail@; PDF delivered | 🟢 |
| Document sharing portal → submit checklist | **07-C2:** "Checklist Submitted!"; no email sent | Not retested | — |
| E-Signature → Upload Document → Send Invite / signer Finish | Not tested | **07-E1 / 07-E2:** mail@; delivered | — |

**Issues in both states**

- There's no "send email" action for a single client. The only way is the bulk action with one client selected.
- The recipients preview shows one address, but every address on the record receives the email. The client timeline records no emails.
- The client bulk modal has no Adjustable Tokens panel, and labels the BCC field differently ("BCC List").
- The service and checklist reminder editors have an attach option (not in the spec). It works.
- Reminder emails:
  - Editing one switches its enabled toggle **off** and resets it to Draft. Send is only offered in Draft.
  - The checklist reminder template pre-fills BCC `zameukanadu-9059@yopmail.com`, and the Internal Reminder goes to that address (probably the assignee). Please confirm this is intended.
  - Service reminders only exist once the service has a task. "Add Custom Reminder" did nothing, and the Reminders panel sometimes hangs on loading.
- E-sign (tested while disconnected, but it's a system email):
  - `doctesttenant1@yopmail.com` is added as a recipient without being shown.
  - A signer can Finish with 0/2 fields signed, and a "Document Signed" email follows.
  - That email links to a **public** Supabase file and says the document is attached when it isn't.
  - Links use a Vercel preview domain and show the Vercel toolbar.
  - The "Send Email to Client" popup's From field stays on "Loading accounts…".
- The portal invite sends in one click, with generic copy and the tenant name in capitals in the subject.
- The checklist portal has click and layout quirks, and sends no confirmation email after submission.
- Converted clients land in Draft (reminders and services paused). Please confirm emails should go to Draft clients.
- Multi-word client search returns nothing, and the client profile preview changes width between sections.

**Only when disconnected:** the bulk modal defaults to the unavailable linked option and only shows an error after Send.

### 4.5 Emails module (reports 05, D05)

| Action | Connected | Disconnected | Δ |
|---|---|---|---|
| Compose | **E1:** dev@; 2 To + CC + BCC; PDF + PNG delivered | **DC-E1, DC-E1b:** 🚨 from **aftab.zaheer.accotech@gmail.com**; the previous subject was appended to the new one | 🔴 |
| Reply All | **E2:** sent To dev@ only; original To and CC dropped | Not available (empty inbox) | — |
| Forward | **E3:** body arrives as raw HTML and MIME; original attachments dropped | Not available | — |

**Issues in both states**

- Compose, Reply and Forward have an attach option (not in the spec). It worked when connected.
- Compose shows a "Reply sent!" toast.

**Only when connected:**

- Replies aren't threaded in Gmail.
- "To" is displayed as a raw array.
- The reading pane jumps to another email after Compose.
- There's no indicator that files are attached.
- The Forward form stays filled in after sending.
- Emails sent from other modules appear in Sent with no link to the record.

**Only when disconnected:**

- Compose is enabled with no account connected, and it sends from the wrong account.
- The subject carries over between Compose sessions.
- The "Sending email…" toast disappears with no result.
- The console repeatedly logs React error #185.

### 4.6 Invoices (reports 06, D06)

| Entry point | Connected | Disconnected | Δ |
|---|---|---|---|
| New Invoice → Approve & send | **I1:** dev@; 2 To (1 shown) + BCC; tokens replaced; "Pay Invoice" link | **DC-I2 (INV-004):** mail@; same content | 🟠 |
| Preview → Send reminder | **I2:** dev@ | **DC-I1 (INV-003):** mail@ | 🟠 |
| Scheduled reminder sequence | Not triggered | — | — |

**Issues in both states**

- No attach option (matches the spec).
- Recipients are read-only, and the preview shows one address while every address receives the email.
- The invoice Audit Timeline doesn't record sends or reminders.
- There are two token formats: `{{invoice_number}}` in the Reminders editor and `::Invoice Number::` in the email popups.
- Scheduled reminders already in the inbox (INV-010, 011 and 013, from mail@, not sent by me) link to **http://localhost:3000/invoices**.

**Only when disconnected:** the popup still says "Emails will be sent from your linked mailbox".

### 4.7 Settings and other modules (reports 06, D06)

| Item | Connected | Disconnected | Δ |
|---|---|---|---|
| Email Composer → Send Test Email | **06-S1:** mail@; one recipient only | **DC-S:** mail@ | 🟢 |
| Email Connections | One mailbox: dev@remindoo.co (Connected) | Only "Connect Company Email" | — |
| Campaign Management | Status per recipient ("Sent / No Error Detected") | Shows **Failed** and raw AWS error text for attachment campaigns | — |
| Dashboard, Knowledge Base, Financial Assistant | No email features | No email features | 🟢 |

**Notes:**

- The header/footer preview doesn't match most real emails: dev@ sends were plain, and only mail@ sends carry the header and footer.
- The test email accepts only one address.
- In the retest, Edit Own Profile showed "Employee not found" for Test User.
- Automations weren't tested (excluded by Suhaib).

## 5. Attachments vs spec

**Spec (confirmed by Suhaib):** attachments are only for Settings, Automations and emails sent from inside a lead's profile. Anywhere else the option shouldn't appear, and if it does appear, it must not stop the email working.

| Where | Attach option | In spec? | Connected | Disconnected |
|---|---|---|---|---|
| Lead profile (Communication, Quick Access) | ✅ | ✅ Yes | ✅ Delivered (L2) | ❌ **Failed** (DC-L3, QA-L6) |
| Leads quick-view "Send Lead Email" | ✅ | ❌ No | ✅ Delivered via linked account (L1) | ❌ **Failed** in campaign mode (DC-L2) |
| Emails module (Compose, Reply, Forward) | ✅ | ❌ No | ✅ Delivered (E1, E2); Forward drops the originals | Not tested with an attachment |
| Client service reminder editor | ✅ | ❌ No | ✅ Delivered (07-S1, state unknown) | ✅ Delivered (DC-S1) |
| Client checklist reminder editor | ✅ | ❌ No | Not used | ✅ Delivered (DC-C3) |
| Bulk (Leads, Clients), Proposals, Tasks, Invoices, portal invite, e-sign | ❌ | ✅ Matches spec | — | — |
| Settings, Automations | Not tested | ✅ Yes | Not tested (excluded) | Not tested |

- **Result:** the "must not stop the email working" rule holds while connected, but **not when disconnected**. Every attachment that goes through the campaign sender fails.
- The upload popover says "Supports PDF, CSV or XLS", but it also accepts JPG/PNG, DOC/DOCX, ZIP and XLSX. `.txt` isn't allowed, and the limit is 10 MB per file.

## 6. Bulk sends and the 20-email limit

- **Connected (Leads and Clients):**
  - With 20 or fewer records, "Send from linked account" is available and everything goes from **dev@** (B4, B6).
  - With 21 or more, the linked option is greyed out ("Only available for 20 or fewer.") and the whole send becomes a campaign from **mail@** (B3, B5). Suhaib confirmed this is intended.
  - One email is sent per record, however many addresses it has. A record with 25 addresses produced 1 email from dev@ with all 25 in To (B1, B2).
- **Disconnected:** the limit no longer matters. Linked sends are blocked at any count, and campaigns go from mail@ as before. The modal doesn't reuse its greying logic for this case, so it still defaults to the linked option (DC-C1).

## 7. Consolidated issue list

**State:** C = seen with the mailbox connected · D = seen disconnected · Both = seen in both states, or a system email that doesn't depend on the mailbox.

| # | Severity | Issue | State | Reports |
|---|---|---|---|---|
| 1 | 🚨 Critical | Emails → Compose sends from an unrelated Gmail (aftab.zaheer.accotech@gmail.com) when no mailbox is connected | D | D05 |
| 2 | High | The campaign sender fails on every attachment (S3 permission). Lead-profile attachments fail when disconnected; quick-view campaign attachments fail | D (likely C too) | D01 |
| 3 | High | Queued fallback sends are reported as successful (toast, Communication "Success", Timeline "Email Sent") | D | D01, 07 |
| 4 | High | E-sign: hidden recipient; signing with 0/2 fields; public signed-document link; claimed attachment missing | Both | 07 |
| 5 | High | Emails → Reply All drops recipients; Forward corrupts the body and drops attachments | C | 05 |
| 6 | High | Token replacement in campaigns is inconsistent (raw in Leads, replaced in Clients) | Both | 01, D04 |
| 7 | High | Recipient previews hide addresses that still receive the email (Clients bulk, Invoices, campaign log) | Both | 04, 06, D01 |
| 8 | High | Email history is split or missing (Lead Timeline vs Communication; nothing on the client timeline or invoice audit log) | Both | 01, 04, 06 |
| 9 | High | No single "no mailbox" rule: block vs silent re-route vs wrong account. The popups still say "linked mailbox", and the linked option stays the default | D | D00–D06 |
| 10 | Medium | Nothing outside the send popups shows that the company mailbox is disconnected (the disconnect in this test was manual) | D | 07, D00 |
| 11 | Medium | Silent switch to the no-reply mail@ sender, so client replies are lost | D | D02, D03, D06 |
| 12 | Medium | Recipients are read-only in the Lead quick-view, Task and Invoice popups, despite the helper text | Both | 01, 03, 06 |
| 13 | Medium | Attach option outside the spec (Leads quick-view, Emails module, service and checklist reminder editors) | Both | 00, 07, D04 |
| 14 | Medium | No CC outside the Emails module; invalid addresses accepted; Primary Contact never pre-filled | Both | 01, 02, 03 |
| 15 | Medium | Editing a reminder email switches it off and resets it to Draft | Both | 07, D04 |
| 16 | Medium | Config points at dev or preview resources: "dev" campaign role and bucket in preprod; invoice reminder link to localhost:3000; e-sign on a Vercel preview domain | Both | D01, D06, 07 |
| 17 | Medium | The campaign error log shows raw AWS ARNs, and its retry advice doesn't fit profile emails | D | D01 |
| 18 | Medium | Emails Compose: "Reply sent!" toast, reading pane jumps, subject carried over, React error #185 loop | Both | 05, D05 |
| 19 | Medium | The header/footer preview doesn't match real emails; "do not reply" footer on dev@ proposal emails | Both | 02, 06 |
| 20 | Medium | The assignee's address is pre-filled as BCC on checklist reminders, and the Internal Reminder goes to it | Both | 07, D04 |
| 21 | Medium | Personal task reminders: today can't be selected, no recipient or time, not listed in Planned Reminders | Both | 03, 07 |

**Low (both states):**

- Upload popover text doesn't match the allowed file types.
- The Subject field drops keystrokes, and the body editor is hidden on small screens.
- Create Lead hangs before the custom fields load, and converted leads can't be edited.
- Proposal Name can't be edited; the proposal BCC is pre-filled with the lead's own address; "Sent Date" doesn't update on resend.
- The campaign count badge shows the page's rows, not the total.
- There are two token syntaxes.
- The Emails module shows "To" as a raw array, doesn't thread replies, and leaves the Forward form filled in after sending.
- Multi-word client search fails.
- Dates mix time zones.
- The checklist portal has quirks and sends no confirmation email.
- Service reminders need a task first, and "Add Custom Reminder" does nothing.
- The portal invite sends in one click, with generic copy.
- Converted clients land in Draft.
- Edit Own Profile shows "Employee not found".

## 8. Not tested / still pending

- **Personal task reminder (R1):** due 28 Sep. Not received in the test inbox as of 00:30 UTC; no Remindoo email of any kind has arrived since 27 Sep 20:36 UTC. No recipient is shown when creating the reminder, so it may go to the assignee or the creating user. A second check is scheduled for 10:15 UTC.
- A campaign with an attachment while the mailbox is connected. It's expected to fail the same way.
- Token replacement on fallback lead-profile emails.
- Whether Proposals and Invoices fallback sends appear in Campaign Management.
- Emails module Reply and Forward while disconnected, and Forward with an attachment.
- Attachments in Settings and Automations (excluded).
- Proposal signing and decline notifications, and "Complete your onboarding" emails.
- How a contact's "Email Addresses (Included / Excluded)" fields affect recipients.
- A second From address (only one mailbox was ever connected).
- What happens when the Google token expires or is revoked on its own (the disconnect in this test was manual).
- BCC delivery on its own (Gmail keeps one copy per mailbox), and replies to real third-party inbox emails.

## 9. Test data created (beta)

- **Leads and clients:**
  - "Claude Email Test Lead" (ID 1239; `suhaib.accotech@`, `+lead2`; contact "QA Contact One" `+contact1`; now a Draft client)
  - "Claude Bulk Limit Lead" (ID 1240; 25 `+bulkNN` addresses; now a client)
  - "QA Limit Lead 01–22" (IDs 1241–1262; `+lim01`…`+lim22`; now Draft clients)
  - "DC Proposal Lead" (`+prop3`, `+prop4`)
- **Proposals:** one each for Claude Email Test Lead and DC Proposal Lead (both Sent).
- **Tasks:** "QA Email Test Task", and "QA Reminder Test Task" (reminder set for 28/09).
- **Client QA Limit Lead 01:**
  - Services Confirmation Statement and Test External Service (task "Test - 27-09-26").
  - Edited reminder emails: "External" now has subject `[DC-S1]` and a PDF; "Test Doc Reminder" now has subject `[DC-C3]` and a PDF, and its assignee BCC was removed.
  - E-sign document "claude_test_doc" with 2 signers (`+esign1`, `+esign2`).
- **Invoices:** INV-003 and INV-004 (Claude Email Test Lead, £1.05 each, Sent).

## 10. Source reports

| Module | Connected run | Disconnected retest |
|---|---|---|
| Summary | `00_email_testing_summary.md` | `D00_disconnected_summary.md` |
| Leads | `01_leads_email_test.md` | `D01_leads_disconnected.md` |
| Proposals | `02_proposals_email_test.md` | `D02_proposals_disconnected.md` |
| Tasks | `03_tasks_email_test.md` | `D03_tasks_disconnected.md` |
| Clients | `04_clients_email_test.md` | `D04_clients_disconnected.md` |
| Emails module | `05_emails_module_test.md` | `D05_emails_module_disconnected.md` |
| Invoices, Settings, other modules | `06_invoices_and_other_modules_test.md` | `D06_invoices_settings_disconnected.md` |
| Reminders, e-sign, checklist | `07_additional_tests_reminders_esign_checklist.md` (the mailbox was disconnected during this run) | — |
