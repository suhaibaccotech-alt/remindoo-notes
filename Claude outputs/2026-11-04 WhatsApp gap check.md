# WhatsApp gap check: Remindoo Dev Team / ACCOTECH, 14 Oct – 4 Nov 2026

Checked against Jira SCRUM (titles and descriptions, all statuses), the Obsidian and Joplin notes, the Command Center Inbox and Activity, and Slack searches. Looms were read through their titles and auto-summaries where they had them.

Who's who in the export: +44 7912 225796 = Sir Waqas, +44 20 4618 3024 = Hamna (her 26 Oct report matches SCRUM-1371), +44 7516 733672 = Salman, "Anniee" = Omaima (her Looms are the ones in SCRUM-1368/1369), +92 302 1653490 = Zain.

Sprints: AZ Sprint 5 (116) and Team Sprint 5 (115) are open. **There's no AR Sprint 5 yet**, so AR's cards go to the backlog until it exists.

---

## A. Draft cards for items that are missing (25)

Everything lands in Waiting for Requirements. Owners marked *(suggested)* aren't stated in the chat.

### Bugs

**1. Tenant Pricing – Super Admin and Stripe show trial tenants as Active/Paid**
Aftab · `tenant-pricing`, `src-sales` · Bug · High · AZ Sprint 5
- **Steps to reproduce:** 1. Sign up a new firm on remindoo.co (with or without a card). 2. Open the firm in Super Admin, then the customer in Stripe.
- **Expected:** Both show the firm as on trial, with the trial type (14 days without a card, 60 with a card), the joining date, the trial end date and, once it starts paying, the first payment date.
- **Actual:** Both show "Active"/"Paid". Super Admin's "joined" date is the current billing period start. Zain says he fixed the joining date on 3 Nov, but there's no record of the first payment date.
- **Source:** Salman, WhatsApp, 14 Oct and 27 Oct ("reported for weeks… creating big trouble in our Sales reporting"). Hamna, 3 Nov (wants both dates). Related: SCRUM-925.

**2. Proposals – Saving a product drops its category, and categories picked in Edit Product don't save**
Abdur Rehman · `proposals`, `src-ceo` · Bug · High · backlog (no AR Sprint 5)
- **Steps to reproduce:** Settings → Proposal Setting → Products → Edit → Update. Then try choosing a category in Edit Product → Choose Categories.
- **Expected:** The category stays unless the user changes it. A category chosen in the form saves, just as it does from the Categories tab.
- **Actual:** After saving, the category shows N/A and the category's product count drops (all 21 Limited Company products lost theirs). A category chosen in the form doesn't stick. The form sometimes opens with no category, and saving from that state wipes it. Likely cause: the update sends an empty category list.
- **Source:** Sir Waqas, WhatsApp, 29 Oct, bugs 2–4 (all High). Bug 1 is SCRUM-1354 and bug 7 is SCRUM-1105.

**3. Proposals – Product search doesn't rerun, and the category product picker only sees the last search**
Abdur Rehman · `proposals`, `src-ceo` · Bug · Medium · backlog
- **Expected:** After a product is saved, the results stay filtered, or Enter on the same text searches again. Categories → "+" → Products → Available Products searches every product. The product pickers get an "all products" search box, like the one in Categories.
- **Actual:** After a save, the list resets to all 153 products while the box still shows the old text, and Enter does nothing. Available Products lists only the last search's matches.
- **Source:** Sir Waqas, WhatsApp, 29 Oct (bugs 5–6), 29 Oct 7:21 pm and 2 Nov ("all product search button so we can search all the products").

**4. Service Templates – Internal deadline offset accepts days only, and VAT internal deadline isn't calculated**
Abdur Rehman *(suggested)* · `service-templates`, `src-sales`, `customer-request` · Bug · High · backlog
- **Expected:** Accounts Year End: internal deadline 8 months after the trigger date. The offset accepts months, and editing it leaves the frequency alone. VAT: internal deadline 30 days after the trigger, external 1 month 7 days after. Both are calculated when the task is created, with status Info Requested.
- **Actual:** The offset accepts days only, and editing it changes the frequency settings. The VAT internal deadline isn't set at task creation.
- **Source:** Hamna, WhatsApp, 26 Oct ("the client is waiting"). Looms: https://www.loom.com/share/f4d6e57d7ff0452faf46e273b10bdaad and https://www.loom.com/share/899eea27fc564407b30ddddd6e306a11

**5. Proposals – Packages-only LOE still demands a Pricing Table, and packages don't fill the pricing table**
Abdur Rehman · `proposals`, `src-sales`, `customer-request` · Bug · High · backlog
- **Expected:** A template with only the Packages element saves and sends; only the signature is mandatory (Umair's suggestion, 28 Oct). When a template has both, picking a package fills the pricing table with that package's details and total.
- **Actual:** Saving is blocked until a Pricing Table is added, and packages and the pricing table don't work together.
- **Source:** Hamna, WhatsApp, 26 and 28 Oct (client request, "prioritise fixing this today"). Sir Waqas, 28 Oct: users should be able to add packages, products or both.

**6. Proposals – Packages show as "group 99" instead of their names**
Abdur Rehman · `proposals`, `src-sales` · Bug · Medium · backlog
- **Expected:** Each package shows its own name. **Actual:** Labels like "group 99" appear instead.
- **Source:** Hamna, WhatsApp, 30 Oct 8:54 pm, while testing AR's 30 Oct push on crm.

**7. Proposals – Document template preview leaves out the Packages element**
Abdur Rehman · `proposals`, `src-sales` · Bug · Medium · backlog
- **Expected:** The preview shows the Packages element as the builder does. **Actual:** It's missing, in the template preview only.
- **Source:** Hamna, WhatsApp, 30 Oct 9:14 pm.

**8. Proposals – Pricing variables show $ instead of £**
Abdur Rehman · `proposals`, `src-sales` · Bug · Medium · backlog
- **Steps to reproduce:** Document Builder → Insert variables → Pricing variables.
- **Expected:** £. **Actual:** $.
- **Source:** Hamna, 26 Oct ("sign should be £"). Omaima, 30 Oct (location). Sir Waqas's Loom of 21 Oct also shows a dollar sign.

**9. App-wide – Picking a client or task in global search should open its profile**
Abdur Rehman *(suggested; he owns SCRUM-1026)* · `app-wide`, `src-ceo` · Task · High · backlog
- **Expected:** Selecting a result opens that client's or task's profile. **Actual:** It goes to the table, or the page blinks.
- **Source:** Sir Waqas, WhatsApp, 14 Oct and 21 Oct (repeated).

**10. Tasks – Subtasks aren't auto-selected when creating a task**
Aftab *(suggested; he owns the task-creation cards)* · `tasks`, `src-ceo` · Bug · High · AZ Sprint 5
- **Expected:** A service's subtasks come pre-selected when a task is created, as before. **Actual:** The user has to select them.
- **Source:** Sir Waqas, WhatsApp, 14 Oct ("it was reported in the past too", "fix this asap").

**11. Tasks – Importing a checklist into a task doesn't upload and is very slow**
Aftab *(suggested; same slowness as task creation, skeleton loader from SCRUM-1018)* · `tasks`, `src-ceo` · Bug · High · AZ Sprint 5
- **Expected:** The checklist imports quickly, as it used to. **Actual:** It doesn't upload, even with the new skeleton loader.
- **Source:** Sir Waqas, WhatsApp, 21 Oct ("we cannot make user go and grab coffee"). Related: SCRUM-1213.

**12. HMRC – Authorisation code entry and "Authorization request unknown"**
Sami · `hmrc`, `src-ceo` · Bug · High · Team Sprint 5
- **Expected:** The UI asks the user to enter the code instead of fetching it automatically. The code text is dark enough to read. A submitted code goes where expected with no manual step. Requesting an authorisation code for a client works.
- **Actual:** After submitting and refreshing, it shows "Authorization request unknown". A tenant's client got an error requesting an authorisation code.
- **Source:** Sir Waqas's Loom, 2 Nov: https://www.loom.com/share/965b5f0a9d524385af3a3df5fc6628e2. Hamna, WhatsApp, 3 Nov (screenshot).

**13. Tenant Pricing – Upgrading Core to Growth doesn't update the Admin role's permissions**
Aftab · `tenant-pricing`, `src-sales` · Bug · Medium · AZ Sprint 5
- **Expected:** After an upgrade, Admin gets every Growth feature automatically. **Actual:** The tenant has to change the permissions by hand.
- **Source:** Hamna, WhatsApp, 29 Oct. Sir Waqas agreed. Aftab is looking into it.

### Features and changes

**14. Leads – Every note shows on the Lead Timeline**
Abdur Rehman *(suggested)* · `leads`, `src-ceo` · Story · High · backlog
- **Context:** Accountants rely on lead history for AML, onboarding evidence and handovers. Today the timeline only shows "Lead Added".
- **What to do:** Write a timeline event (note_created, note_updated, note_deleted) inside the single notes service, not per screen.
- **Acceptance criteria:**
  - Notes from every entry point appear as "Note Added": the side panel, the timeline's "+ Add notes", tasks, call logs, proposals, emails, import and the API.
  - Each entry has the full text, the author's name and avatar, and the date and time (UK format, Europe/London), grouped by day.
  - An edit shows "Edited [date/time] by [user]". A delete leaves "Note deleted by [user]".
  - Notes can be found in timeline search, get a Notes filter type and follow the Latest/Oldest sort.
  - Existing notes are backfilled with their original timestamps.
  - The timeline carries over on Convert to Client.
  - Side-panel notes appear without a refresh.
- **Source:** Sir Waqas, WhatsApp, 30 Oct (full spec; he says it was asked before).

**15. Proposals – Notify the tenant when a lead views a sent proposal**
Abdur Rehman · `proposals`, `src-sales` · Story · Medium · backlog
- **Source:** Hamna asked, WhatsApp, 16 Oct. Sir Waqas: "this has to be added… as discussed in the past". You replied "assigning to Abdur Rehman", but no card exists.

**16. Proposals – Clone an existing LOE template**
Abdur Rehman · `proposals`, `src-ceo` · Story · Medium · backlog
- **What to do:** Add a clone/copy action to LOE templates, the same as in Prices.
- **Source:** Sir Waqas, WhatsApp, 29 Oct.

**17. Proposals – Undo and Redo in the Document Builder**
Abdur Rehman · `proposals`, `src-sales` · Story · Medium · backlog
- **Source:** Hamna, WhatsApp, 28 Oct. AR: "I'll add that in the list, and schedule it for next sprint."

**18. Proposals – Apply page padding to every page at once**
Abdur Rehman · `proposals`, `src-sales` · Task · Low · backlog
- **Context:** Padding is set page by page today.
- **Source:** Hamna, WhatsApp, 27 Oct. AR: "noted". This is similar to the 20 Oct boss notes on global font styling and backgrounds for all pages.

**19. Email – Link incoming emails to leads and tasks automatically, not just clients**
Sami · `email`, `src-ceo` · Story · High · Team Sprint 5
- **What to do:** When a connected mailbox receives an email from an address stored on a lead, it links to the lead. A client's reply to a task email links to the task. "Wherever we have email stored it should be added there."
- **Source:** Sir Waqas, WhatsApp, 3 Nov. Sami: "We'll add it."

**20. Email – Email templates in the Email module's compose and reply**
Sami · `email`, `src-ceo` · Story · Medium · Team Sprint 5
- **Source:** Hamna for Sir Waqas, WhatsApp, 4 Nov (two screenshots: compose and a second spot).

**21. Email – Show completed tasks, tagged Completed, when linking an email to a task**
Sami · `email`, `src-sales` · Task · Medium · Team Sprint 5
- **Source:** Hamna, WhatsApp, 4 Nov. Sami: "Acknowledged."

**22. Invoices – "Not in Xero" status with sync, and renamed Outstanding Invoices, in Clients and Tasks**
Aftab · `invoices`, `src-ceo` · Task · Medium · AZ Sprint 5
- **What to do:** Rename the Outstanding Invoices section. **The new name needs Sir Waqas.** Invoices missing from Xero show "Not in Xero" and can be synced from there, as Contacts already can. Do the same in Tasks.
- **Source:** Sir Waqas, WhatsApp, 28 Oct. Aftab: "Noted".

**23. Clients – Client import accepts common abbreviations in list fields**
Abdur Rehman · `clients`, `src-ceo` · Task · Medium · backlog
- **What to do:** Map accepted short forms onto the full options, e.g. "LLP" → "Limited Liability Partnership", for every list-type column.
- **Source:** Sir Waqas, WhatsApp, 26 Oct. You proposed the abbreviation mapping. Related: SCRUM-1368/1369.

**24. Clients – Client table shows the primary director with "+N" when there are more**
Abdur Rehman · `clients`, `src-ceo` · Task · Medium · backlog
- **Source:** Sir Waqas's Loom, 21 Oct (https://www.loom.com/share/ce37603369594c2ab1eef69372f885d4, around 2:30). AR asked on 22 Oct whether to list every director, and Sir Waqas answered by voice note. **Confirm what the voice note said before carding.**

**25. Settings – One company-wide currency (and date format) used everywhere**
Aftab · `settings`, `src-ceo` · Story · Medium · AZ Sprint 5 · Waiting for Requirements
- **Context:** The currency chosen in Global Settings should apply to proposals, client values, fee aggregates and invoices. For conversion, use either a live or a monthly rate and keep it simple. Aftab asked for a meeting on this on 4 Nov.
- **Source:** Sir Waqas's Loom, 4 Nov: https://www.loom.com/share/156a5ba9378b48c29ee236b0aeda64b8. Related: SCRUM-982 (date format), SCRUM-877.

**PRD rather than a card:** **Postcode lookup for addresses that don't come from Companies House** (Sir Waqas, 26 Oct). It's a full spec spanning sole traders, landlords, leads and web forms, LOE, the client portal, staff onboarding and CSV import. It covers autocomplete, auto-fill, validation and an address-source field, plus an audit of every address field. That's several modules, so it fits `remindoo-prd` better than one card.

---

## B. Updates to existing cards

- **SCRUM-1371** (AccoTech custom fields on the demo account): Hamna says it still shows on the DD Accounting tenant after AR's deploy (27 Oct). Also add Sir Waqas's 21 Oct note: a live client has 57 fields but the list shows over 100 (see also SCRUM-1176).
- **SCRUM-1369** (bulk import): Omaima's 2 Nov follow-up adds three points. Mapping works, but clients still land in Draft. Services aren't assigned automatically. Ltd clients shouldn't be asked for data Companies House supplies (SIC, address, service deadline dates).
- **SCRUM-1160** (invoice numbers): Sir Waqas, 28 Oct: number-less invoices "surely" came from Remindoo, so investigate the source. Aftab now skips invoices with no number and blocks creating one.
- **SCRUM-1211** (View Task link in emails, Deployed): probably the cause of Sir Waqas's 22 Oct "task email opens a blank screen". Confirm with him, since you'd asked him to forward the email.

## C. Fixed in the chat with no card (create as Deployed for the record, or leave)

- **Invoice reminders on/off toggle**, with a warning when accounting software is connected. Aftab, live 26 Oct.
- **Email sending limit is now 10× active clients** for every tenant on both plans. Module emails (Google/Outlook) don't count. Sami, live 30 Oct. **Sir Waqas asked for 5×**, so the team shipped double what he said.
- **Frozen clients were billed** (Season Associates Ltd). Aftab pushed a fix on 4 Nov. **The client's charge is a money decision for you.**
- **Disabling MFA while impersonating logged the user out** (Cairngorm Accounting). AR's fix was pushed on 2 Nov.
- Internal server errors and timeouts on 30 Oct and 2 Nov. Sami fixed the timeout.
- "Can't find? Add Product" button (AR, 29 Oct). Bulk import button missing for one firm (AR, 26 Oct).

## D. To-dos and decisions (not cards)

- Aftab promised Sir Waqas a list of integration credentials (Sage, FreeAgent, Xero, Stripe, PayPal), an Adfin status, PayPal live credentials and sandbox details (26 Oct). Keep the credentials themselves out of Jira.
- Aftab: deactivate the test Sage account (18 Oct). He asked whether to; Sir Waqas said cancel it.
- AR needs PandaDoc access. Sir Waqas asked Hamna to set it up on info@accotax.co.uk (3 Nov).
- Sales asked to be told whenever changes go live (Salman, 27 Oct). Today's release lists go to Slack only.
- Decision-log candidate (Sir Waqas, 29 Oct): no testing on live tenants or AccoTech data, ever. Test on preprod with hello@remindoo.co.

## E. Couldn't verify, needs your eyes

- **Looms with no transcript or summary:** 3 Nov 11-minute Loom to Syed Ali Raza, Umair and you (b1e79a99…). 29 Oct ×2 (22c9259e…, 8d68ebb2…). 4 Nov "Tasks" to Aftab (1f10d89d…).
- **Looms with Hindi auto-summaries that suggest new asks:**
  - 4 Nov "bug": photo ID upload not working, plus a "not applicable" condition in automation (3195d300…).
  - 4 Nov: compact task view, per-user column visibility, outstanding tasks filtered by client status (5de49c40…).
  - 4 Nov: automation indicator on checklists, and client-level checklist reminders when global reminders are on (b4018548…).
  - 29 Oct: monthly and frequency editing in custom quotes (502c35ef…).
  - 2 Nov: price override should update the quarterly grand total (1576eed3…).
- **Screenshots or voice notes only:**
  - 14 Oct: Xero "super urgent" bugs.
  - 19 Oct: "reported many many times" ×2, and "this email address does not work for Remindoo team".
  - 23 Oct: packages display.
  - 2 Nov: "This keeps coming up".
  - 4 Nov: date format and alignment, location unknown.
  - 15 Oct: "Email Templates in this module too" (Document folders).
  - 30 Oct: whether to cap the package feature list.
- **Open but unconfirmed:**
  - LOE tokens not working (20 Oct; AR asked for steps).
  - Campaign bulk-email tokens not filled, and the quota not dropping on a live Growth tenant (29 Oct).
  - Sage connection error (21 Oct; Aftab asked if it's a Sage Business account).
- **Requests nobody approved:** Zoho Mail over IMAP/SMTP (Sami: needs a separate integration). Email recall (Salman). Filtering clients by service (AR pointed to the "Next VAT to be filed" filter).

## Already in the system (for reference)

| Item | Card |
| --- | --- |
| Speed review (frontend and backend) | SCRUM-1217, SCRUM-1213 |
| Super Admin email on sign-up | SCRUM-1214 |
| "User tokens please" | SCRUM-1156 |
| Signature overlaps pricing table | SCRUM-1070 |
| Proposal sent to lead shows at the bottom | SCRUM-1215 |
| Client CSV export fails | SCRUM-1221 |
| Several payroll frequencies, frequency shown with the service | SCRUM-1348 |
| Sorting and filters on everything new | SCRUM-1367 |
| Custom fields leak to demo | SCRUM-1371 |
| Personal task reminder not saved | SCRUM-1370 |
| CSV template and bulk import | SCRUM-1368, SCRUM-1369 |
| Product picker raw HTML | SCRUM-1354 |
| Package preview shows / Year | SCRUM-1105 |
| Calendar | SCRUM-959 |
| Document upload in the builder | SCRUM-1081 |
| Custom tasks from client card | SCRUM-1373, SCRUM-1231 |
| Free trial 14/60 with no promo code | SCRUM-925 |
| Sent email missing from timeline | SCRUM-1027 |
| Companies House sync changes not shown | Sales Meeting note, pending Inbox item 20261103-sweep-2030-001 |
| The six 21 Oct boss-meeting Looms | Boss Meeting Notes 20-10-2026 (about 64 cards) |
