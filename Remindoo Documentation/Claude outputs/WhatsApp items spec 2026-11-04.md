# Spec: WhatsApp group items, 14 Oct – 4 Nov 2026

**Status:** draft for Suhaib's review, 4 Nov 2026. No cards exist yet. They're created once this spec is approved.
**Source:** the "Remindoo Dev Team / ACCOTECH" WhatsApp group, 14 Oct – 4 Nov 2026, checked against Jira, the notes, the Command Center and Slack. The full gap check is in the Project at `claude/whatsapp-gap-check-2026-11-04.md`.
**Home once approved:** `Remindoo Documentation/QA/Specs/WhatsApp items 2026-11.md` in the vault. The notes runs skip the QA folder, so the spec is never read as notes. The QA runs read it from there.

## How this spec is used

- **One item = one card.** Each section below is named `WA-nn`. The card's description is the section's Problem, Requirements and Acceptance criteria, ending with "Spec: WA-nn in Remindoo Documentation/QA/Specs/WhatsApp items 2026-11.md".
- **QA tests against the spec.** Each item's "Test on preprod" block becomes the card's test steps: it's written to `qa/<KEY>.steps` and posted as the card's test-steps comment. When the card reaches Completed without Testing, the QA run tests it with these steps.
- **QA tracks progress every run.** See "QA tracking" at the end. Each run checks every WA card's status, reports a progress table, tests what's on preprod and nudges developers whose scheduled items haven't moved.
- **"Proposed"** marks a detail the chat didn't specify. Confirm or change it at review.
- **"Blocked for the QA run"** marks steps the automated run isn't allowed to do: Super Admin, real payments or Stripe, connected integrations (HMRC, Xero, a mailbox), file uploads, links that arrive by email, and deleting anything. Those parts come to you as a "Needs a person" to-do.

## Summary

| ID | Card title | Owner | Type · Priority | Sprint | QA run can test |
| --- | --- | --- | --- | --- | --- |
| WA-01 | Tenant Pricing – Super Admin and Stripe show trial tenants as Active/Paid | Aftab | Bug · High | AZ Sprint 5 | No (Super Admin, Stripe) |
| WA-02 | Proposals – Saving a product drops its category, and categories picked in Edit Product don't save | Abdur Rehman | Bug · High | AR Sprint 5* | Yes |
| WA-03 | Proposals – Product search doesn't rerun, and the category product picker only sees the last search | Abdur Rehman | Bug · Medium | AR Sprint 5* | Yes |
| WA-04 | Service Templates – Internal deadline offset accepts days only, and VAT internal deadline isn't calculated | Abdur Rehman (suggested) | Bug · High | AR Sprint 5* | Yes |
| WA-05 | Proposals – Packages-only LOE still demands a Pricing Table, and packages don't fill the pricing table | Abdur Rehman | Bug · High | AR Sprint 5* | Mostly (sending only to allowed addresses) |
| WA-06 | Proposals – Packages show as "group 99" instead of their names | Abdur Rehman | Bug · Medium | AR Sprint 5* | Yes |
| WA-07 | Proposals – Document template preview leaves out the Packages element | Abdur Rehman | Bug · Medium | AR Sprint 5* | Yes |
| WA-08 | Proposals – Pricing variables show $ instead of £ | Abdur Rehman | Bug · Medium | AR Sprint 5* | Yes |
| WA-09 | App-wide – Picking a client or task in global search should open its profile | Abdur Rehman (suggested) | Task · High | AR Sprint 5* | Yes |
| WA-10 | Tasks – Subtasks aren't auto-selected when creating a task | Aftab (suggested) | Bug · High | AZ Sprint 5 | Yes |
| WA-11 | Tasks – Importing a checklist into a task doesn't upload and is very slow | Aftab (suggested) | Bug · High | AZ Sprint 5 | Yes |
| WA-12 | HMRC – Authorisation code entry and "Authorization request unknown" | Sami | Bug · High | Team Sprint 5 | No (HMRC connection) |
| WA-13 | Tenant Pricing – Upgrading Core to Growth doesn't update the Admin role's permissions | Aftab | Bug · Medium | AZ Sprint 5 | No (plan change, permissions) |
| WA-14 | Leads – Every note shows on the Lead Timeline | Abdur Rehman (suggested) | Story · High | AR Sprint 5* | Mostly (no deleting) |
| WA-15 | Proposals – Notify the tenant when a lead views a sent proposal | Abdur Rehman | Story · Medium | AR Sprint 5* | No (lead's link arrives by email) |
| WA-16 | Proposals – Clone an existing LOE template | Abdur Rehman | Story · Medium | AR Sprint 5* | Yes |
| WA-17 | Proposals – Undo and Redo in the Document Builder | Abdur Rehman | Story · Medium | AR Sprint 5* | Yes |
| WA-18 | Proposals – Apply page padding to every page at once | Abdur Rehman | Task · Low | AR Sprint 5* | Yes |
| WA-19 | Email – Link incoming emails to leads and tasks automatically, not just clients | Sami | Story · High | Team Sprint 5 | No (connected mailbox) |
| WA-20 | Email – Email templates in the Email module's compose and reply | Sami | Story · Medium | Team Sprint 5 | Partly (needs a mailbox to send) |
| WA-21 | Email – Show completed tasks, tagged Completed, when linking an email to a task | Sami | Task · Medium | Team Sprint 5 | Partly (needs an email in the module) |
| WA-22 | Invoices – "Not in Xero" status with sync, and renamed Outstanding Invoices, in Clients and Tasks | Aftab | Task · Medium | AZ Sprint 5 | Partly (no Xero sync) |
| WA-23 | Clients – Client import accepts common abbreviations in list fields | Abdur Rehman | Task · Medium | AR Sprint 5* | No (CSV upload) |
| WA-24 | Clients – Client table shows the primary director with "+N" when there are more | Abdur Rehman | Task · Medium | AR Sprint 5* | Yes, if a client has several directors |
| WA-25 | Settings – One company-wide currency (and date format) used everywhere | Aftab | Story · Medium | AZ Sprint 5 | Partly (no sends) |

\* AR Sprint 5 doesn't exist yet. Until it does, AR's cards wait in the backlog (see Decisions).

Every card gets exactly one module label and one source label. `src-ceo` is for Sir Waqas's messages and Looms; `src-sales` is for Hamna, Salman and Omaima. Customer requests also get `customer-request`.

## Decisions needed before the cards are created

1. **AR Sprint 5:** create it, or leave his 14 cards in the backlog? Abdur Rehman is exempt from the card cap.
2. **WA-04, WA-09, WA-10, WA-11, WA-14 owners** are suggestions; nobody named an owner in the chat. Confirm or change them.
3. **WA-22:** what should "Outstanding Invoices" be renamed to? Sir Waqas didn't say.
4. **WA-24:** what did Sir Waqas's 22 Oct voice note say: list every director, or the primary one plus "+N"?
5. **Email limit:** Sir Waqas asked for 5× active clients (29 Oct), but Sami shipped 10× (30 Oct). Keep 10× or change to 5×? This is a question for Sir Waqas, so it goes through you.
6. **Nudges:** how many working days without a status change before a developer gets a nudge? Proposed: 5 working days, and only for cards in an open sprint.
7. **Chat-only fixes:** create a "record" card for each, moved to Completed without Testing so QA tests it like any other card? Or keep them as verify-only checks with no card? Proposed: record cards, so QA can track them by key.
8. **Postcode lookup:** OK to write it as a PRD (`remindoo-prd`) rather than a card? It isn't one of the 25.

---

## Items

### WA-01 Tenant Pricing – Super Admin and Stripe show trial tenants as Active/Paid

Card: Bug · High · Aftab · `tenant-pricing`, `src-sales` · AZ Sprint 5

**Problem.** Since the billing change that moved Stripe charging to month end, new firms show as "Active"/"Paid" in both Super Admin and Stripe, even while on their free trial. Sales can't report who is on trial, which trial they're on, or when it ends. The trial itself was fixed on 27 Oct (SCRUM-925: 14 days without a card, 60 with one, no promo code), but the status display wasn't. Super Admin's "joined" date was the current billing period start; Zain says he fixed it on 3 Nov.

**Requirements**
- Super Admin shows each firm's real subscription state: on trial (14-day or 60-day), active and paying, cancelled.
- Super Admin shows the joining date (sign-up date), the trial end date and the first payment date. Where the first payment date was never recorded, show "not recorded" rather than a wrong date.
- Stripe shows trialing firms as on trial until the end date, as it did before the change.
- Existing firms are corrected, not just new sign-ups.

**Acceptance criteria**
- A firm that signs up without a card shows "Trial (14 days)" with its end date in Super Admin, and trialing in Stripe.
- A firm that signs up with a card shows "Trial (60 days)" with its end date.
- After the first charge, the firm shows Active, with its first payment date.
- The joining date is the sign-up date, not the billing period start.
- Firms that signed up since the change show the right state after the fix.

**Test on preprod**
Where: Super Admin → Firms; Stripe test dashboard. Blocked for the QA run (Super Admin and Stripe), so it comes to you as a "Needs a person" to-do.
Steps:
1. Sign up a test firm on preprod without a card.
2. Open it in Super Admin and check the status, trial type, joining date and trial end.
3. Sign up a second test firm with a Stripe test card and check the same fields.
4. Open both customers in Stripe (test mode) and check they show as trialing with the right end dates.
Expected:
- Statuses, dates and trial types as in the acceptance criteria. Nothing shows "Active"/"Paid" while trialing.
Also check: the sign-up email to Super Admin still sends (SCRUM-1214), and the trial choice on sign-up still works without a promo code (SCRUM-925).

**Source.** Salman, WhatsApp, 14 Oct 2:03 pm and 27 Oct 4:13 pm ("reported the last time on 14th Oct… creating big trouble in our Sales reporting"). Hamna, 3 Nov 8:20 pm (wants the joining date and the first payment date). Zain, 3 Nov 8:26 pm.

---

### WA-02 Proposals – Saving a product drops its category, and categories picked in Edit Product don't save

Card: Bug · High · Abdur Rehman · `proposals`, `src-ceo` · AR Sprint 5

**Problem.** Sir Waqas lost the category on all 21 Limited Company products while setting them up on live. Editing and saving a product sets its category to N/A and lowers the category's product count. A category picked in the Edit Product form doesn't save; it only sticks when products are added from the Categories tab. The form sometimes opens with no category even when the product has one, and saving from that state wipes it. Likely cause: the update sends an empty category list, or replaces the category link instead of keeping it.

**Requirements**
- Saving a product keeps its category unless the user changes it.
- A category chosen in Edit Product → Choose Categories saves, the same as adding the product from the Categories tab.
- The Edit Product form always opens with the product's current categories.

**Acceptance criteria**
- Edit any field of a categorised product and save: the category and the category's product count are unchanged.
- Pick a category in the form and save: the product shows in that category, and the count goes up by one.
- Reopen Edit Product: the saved categories are shown.

**Test on preprod**
Where: Settings → Proposal Setting → Products and Categories, as Test User.
Before you start: create category "QA Category WA-02" and product "QA Product WA-02" in it, from the Categories tab.
Steps:
1. Products → QA Product WA-02 → Edit. Check Choose Categories shows QA Category WA-02.
2. Change only the description and click Update.
3. Check the product's category and the category's product count.
4. Create "QA Product WA-02b" with no category, then Edit → Choose Categories → QA Category WA-02 → Update.
5. Reopen both products' Edit forms.
Expected:
- After step 2, the category is still QA Category WA-02 and the count hasn't changed.
- After step 4, WA-02b is in QA Category WA-02 and the count is one higher.
- Step 5 shows the category in both forms.
Also check: adding products from the Categories tab still works, and the product picker in a proposal still lists products by category.

**Source.** Sir Waqas, WhatsApp, 29 Oct 6:21 pm, "Remindoo bugs I found while setting up the Limited Company products", bugs 2, 3 and 4 (all High). Bug 1 (raw HTML) is SCRUM-1354; bug 7 (package preview period) is SCRUM-1105.

---

### WA-03 Proposals – Product search doesn't rerun, and the category product picker only sees the last search

Card: Bug · Medium · Abdur Rehman · `proposals`, `src-ceo` · AR Sprint 5

**Problem.** In the Products tab, after a product is saved the list goes back to all 153 products while the search box still shows the old text, and pressing Enter on the same text does nothing. In Categories → category "+" → Products → Available Products, the list only holds what matched the last Products-tab search, and its own search can't find anything outside that list. Sir Waqas also wants an all-products search box in the product pickers, like the one in Categories.

**Requirements**
- After saving a product, the Products tab keeps the current search results, or searching the same text again works.
- Available Products in a category searches every product, independent of the Products tab.
- The product pickers (Categories → Add products, and Proposals → Products and Pricing → "+ Products") have a search box that searches all products.

**Acceptance criteria**
- Search, save a product, then press Enter on the same text: the filtered list returns.
- Available Products finds any product by name, whatever was last searched in the Products tab.
- Both pickers have a working all-products search.

**Test on preprod**
Where: Settings → Proposal Setting → Products and Categories; Proposals → new proposal → Products and Pricing.
Before you start: QA Product WA-02 from WA-02, or any two products with distinct names.
Steps:
1. Products tab: search "QA Product", open one, Update.
2. Check the list and the search box, then press Enter.
3. Products tab: search a name that matches only one product.
4. Categories → any category → "+" → Products → Available Products: search for a different product.
5. In a draft proposal, open "+ Products" and search for a product by name.
Expected:
- Step 2: the filtered results show (or return on Enter).
- Step 4 finds the other product.
- Step 5 finds products across all categories.
Also check: product descriptions in the picker (SCRUM-1354) and category counts (WA-02).

**Source.** Sir Waqas, WhatsApp, 29 Oct 6:21 pm (bugs 5 and 6, Low); 29 Oct 7:21 pm ("We should have product search box there too, like we have for categories"); 2 Nov 5:55 pm ("all product search button so we can search all the products").

---

### WA-04 Service Templates – Internal deadline offset accepts days only, and VAT internal deadline isn't calculated

Card: Bug · High · Abdur Rehman *(suggested)* · `service-templates`, `src-sales`, `customer-request` · AR Sprint 5

**Problem.** A pilot firm is waiting on two deadline settings. Accounts Year End needs an internal deadline 8 months after the trigger date, but the internal deadline offset only accepts days, and editing it also changes the frequency settings. VAT needs an internal deadline 30 days after the trigger date and an external one 1 month and 7 days after; the internal deadline isn't calculated when the task is created.

**Requirements**
- The internal (and external) deadline offset can be set in months and days.
- Editing a deadline offset never changes the template's frequency settings.
- When a task is created from the service, its internal and external deadlines are calculated from the trigger date and the offsets. A task with no progress shows as Info Requested.

**Acceptance criteria**
- Accounts Year End with an 8-month internal offset: a task with trigger date 1 Apr 2026 gets an internal deadline of 1 Dec 2026.
- VAT with a 30-day internal offset and a 1 month 7 days external offset: a task with trigger date 1 Oct 2026 gets an internal deadline of 31 Oct 2026 and an external one of 8 Nov 2026.
- After editing an offset and saving, the frequency tab settings are as they were.

**Test on preprod**
Where: Settings → Service Templates; a client's services; Tasks. This changes tenant settings, so record the old values first and put them back afterwards.
Before you start: the QA client "QA Multi Freq Client", or "Test".
Steps:
1. Open the Accounts – Year End template and note the frequency settings.
2. Set the internal deadline offset to 8 months and save. Check the frequency settings are unchanged.
3. Open the VAT template: internal offset 30 days, external offset 1 month 7 days, save.
4. On the QA client, add or refresh the VAT service so a task is created, and open the task.
5. Do the same for Accounts Year End.
Expected:
- Months can be entered in step 2, and the frequency settings don't change.
- The tasks' internal and external deadlines match the offsets from the trigger date.
- The new tasks show Info Requested.
Also check: trigger dates after February and on 30-day months (SCRUM-981), and existing tasks keep their deadlines.

**Source.** Hamna, WhatsApp, 26 Oct 8:16 pm ("the client is waiting"). Looms: https://www.loom.com/share/f4d6e57d7ff0452faf46e273b10bdaad ("Can't change internal deadline date") and https://www.loom.com/share/899eea27fc564407b30ddddd6e306a11 ("Internal deadline not calculated").

---

### WA-05 Proposals – Packages-only LOE still demands a Pricing Table, and packages don't fill the pricing table

Card: Bug · High · Abdur Rehman · `proposals`, `src-sales`, `customer-request` · AR Sprint 5

**Problem.** A pilot firm wants to send LOEs with packages only. Today the Document Builder makes both a Pricing Table and a Signature mandatory, so a packages-only template can't be saved. When a template has both, the pricing table only lists products, and choosing a package doesn't fill it. Umair proposed, as a quick fix, making only the signature mandatory. Sir Waqas wants users to be able to add packages, products or both, and have whatever they add show correctly.

**Requirements**
- Only the Signature element is mandatory (Umair's proposal). *Proposed, confirm:* a template still needs at least one of Pricing Table or Packages.
- A packages-only LOE lets the lead choose a package and sign.
- When a template has both and the lead selects a package, the pricing table shows that package's details and total price.
- The builder can suggest keeping just one, but must not block saving with both.

**Acceptance criteria**
- A template with only Packages and a Signature saves, and the LOE sends.
- On the lead's signing page, choosing a package and signing works with no pricing table.
- With both elements, choosing a package fills the pricing table with the package and its total; changing the choice updates it.
- *(If the proposed rule is confirmed)* A template with neither Pricing Table nor Packages can't be saved, and says why.

**Test on preprod**
Where: Settings → Document Templates (Document Builder); Proposals.
Before you start: a package group with at least two packages.
Steps:
1. Create template "QA LOE WA-05 packages" with a Packages element and a Signature only. Save.
2. Create a proposal for a QA lead whose only email is suhaib.accotech@gmail.com, using this template. Send it.
3. Open the proposal preview and select a package.
4. Create "QA LOE WA-05 both" with Packages, Pricing Table and Signature. Save, use it in a proposal and select a package in the preview.
5. Try to save a template with only a Signature.
Expected:
- Steps 1 and 2 succeed.
- In step 4, the pricing table shows the selected package and its total.
- Step 5 follows the rule you confirm (blocked with a clear message, or allowed).
Blocked for the QA run: signing from the emailed link.
Also check: SCRUM-1352 (grouped packages adding all tiers to the total) and SCRUM-1070 (signature overlapping the pricing table).

**Source.** Hamna, WhatsApp, 26 Oct 3:45 pm and 28 Oct 6:26 pm ("A client wants to send LOEs with packages… Could we please prioritise fixing this today?"). Umair, 28 Oct 6:41 pm. Sir Waqas, 28 Oct 6:49 pm.

---

### WA-06 Proposals – Packages show as "group 99" instead of their names

Card: Bug · Medium · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**Problem.** After AR's 30 Oct push, packages in a proposal show labels such as "group 99" instead of the package names.

**Requirements and acceptance criteria**
- Every place a package appears (builder, proposal, preview, the lead's page, PDF) shows the package's own name.

**Test on preprod**
Where: Proposals, with a template that has a Packages element.
Steps:
1. Open a proposal that uses packages (e.g. the one from WA-05) in the builder and in the preview.
2. Download the PDF, if the preview offers it.
Expected:
- Each package shows its name everywhere, and no "group <number>" label appears.
Also check: package names over the length limit and duplicate names in a group are still blocked (AR's 30 Oct change list).

**Source.** Hamna, WhatsApp, 30 Oct 8:54 pm ("Packages name are not visible… should show with name instead of group 99").

---

### WA-07 Proposals – Document template preview leaves out the Packages element

Card: Bug · Medium · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**Problem.** Previewing a document template that has a Packages element doesn't show the packages, although the builder does. This happens only in the template preview.

**Requirements and acceptance criteria**
- The document template preview shows the Packages element as the builder shows it.

**Test on preprod**
Where: Settings → Document Templates.
Steps:
1. Open a template with a Packages element (e.g. "QA LOE WA-05 packages") in the builder.
2. Open its preview.
Expected:
- The preview shows the packages, as in the builder.
Also check: SCRUM-1262 (tables spanning several pages preview correctly).

**Source.** Hamna, WhatsApp, 30 Oct 9:14 pm.

---

### WA-08 Proposals – Pricing variables show $ instead of £

Card: Bug · Medium · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**Problem.** In the Document Builder, Insert variables → Pricing variables shows prices with a dollar sign. Sir Waqas's 21 Oct Loom also shows a dollar sign in one place after the pound sign was fixed elsewhere.

**Requirements and acceptance criteria**
- Pricing variables use £ (and, once WA-25 exists, the tenant's currency) in the builder, preview, sent proposal and PDF.

**Test on preprod**
Where: Settings → Document Templates → builder → Insert variables → Pricing variables.
Steps:
1. Insert each pricing variable into a QA template.
2. Preview it and check the symbol.
Expected:
- Every pricing variable shows £.
Also check: the pricing table totals (SCRUM-1244) and invoice amounts still show £.

**Source.** Hamna, WhatsApp, 26 Oct 5:53 pm ("sign should be £"). Omaima, 30 Oct 4:05 pm (location). Sir Waqas's Loom, 21 Oct: https://www.loom.com/share/ce37603369594c2ab1eef69372f885d4

---

### WA-09 App-wide – Picking a client or task in global search should open its profile

Card: Task · High · Abdur Rehman *(suggested; he holds SCRUM-1026)* · `app-wide`, `src-ceo` · AR Sprint 5

**Problem.** Selecting a client in global search takes the user to the Clients table rather than the client's profile, and for tasks the page blinks. Sir Waqas has asked twice.

**Requirements**
- Selecting a client result opens that client's profile.
- Selecting a task result opens that task.
- *Proposed:* if search returns leads, selecting one opens the lead's profile.

**Acceptance criteria**
- From any page, searching a client name and clicking the result opens the client profile in one step.
- The same for a task, with no blinking or reload loop.

**Test on preprod**
Where: the global search bar, as Test User.
Steps:
1. From the Dashboard, search "Test" and click the client result.
2. Search a QA task's name and click it.
3. Repeat from the Clients and Tasks pages.
Expected:
- Each click opens that client's profile or that task directly.
Also check: SCRUM-1026 (Tasks module stuck loading from global search).

**Source.** Sir Waqas, WhatsApp, 14 Oct 7:57 pm ("when we search client it should open client profile, shouldnt bring here") and 21 Oct 2:23 pm ("When we search client or task, it should open profile instead of blinking").

---

### WA-10 Tasks – Subtasks aren't auto-selected when creating a task

Card: Bug · High · Aftab *(suggested; he holds the task-creation cards SCRUM-1054 and SCRUM-1018)* · `tasks`, `src-ceo` · AZ Sprint 5

**Problem.** When a task is created from a service, its subtasks used to come pre-selected; now the user has to select them. Sir Waqas says it was reported before.

**Requirements and acceptance criteria**
- Creating a task (quick or detailed) from a service pre-selects all of that service's subtasks, so saving without touching them creates every subtask.
- The user can still untick subtasks before saving.

**Test on preprod**
Where: Tasks → New task (quick and detailed), as Test User.
Before you start: a service template with at least two subtasks, on the client "Test".
Steps:
1. Create a quick task for "Test" with that service.
2. Check the subtask list before saving, then save.
3. Repeat with a detailed task.
4. Repeat, unticking one subtask before saving.
Expected:
- In steps 1–3 every subtask is pre-selected and created.
- In step 4 only the ticked subtasks are created.
Also check: SCRUM-1054 (subtasks not created on crm) and the creation modal closing after a successful save (Sir Waqas, 14 Oct).

**Source.** Sir Waqas, WhatsApp, 14 Oct 7:26 pm ("sub task should be auto seelcted, pls fix this asap… it was reported in the past too").

---

### WA-11 Tasks – Importing a checklist into a task doesn't upload and is very slow

Card: Bug · High · Aftab *(suggested)* · `tasks`, `src-ceo` · AZ Sprint 5

**Problem.** Importing a checklist into a task doesn't work the way it used to. The team found it's the same slowness as task creation and added a skeleton loader, but Sir Waqas says it still doesn't upload, and the wait is too long.

**Requirements**
- Importing a checklist into a task adds it to the task.
- The import finishes quickly; time it before and after the fix, as with SCRUM-1213.
- If it fails, the user sees an error instead of an endless loader.

**Acceptance criteria**
- A checklist template imported into a task appears in the task within a few seconds. *(Target in seconds: Aftab to propose.)*
- A failed import shows an error message.

**Test on preprod**
Where: a task → Document Checklist → import a checklist template.
Before you start: a checklist template in Settings and a QA task on "Test".
Steps:
1. Open the QA task and import the checklist template.
2. Time it from click to the checklist appearing.
3. Reload the task and check the checklist is saved.
Expected:
- The checklist appears and stays after reload, and the time is within the target.
Also check: SCRUM-1240 (deleting a checklist) and SCRUM-1236 (the checklist "Go" button).

**Source.** Sir Waqas, WhatsApp, 21 Oct 2:35 pm and 2:40 pm ("why does it not import checklist? like it used to?"; "But it doesn't upload… we cannot make user to go and grab coffee so it loads"). Your reply, 21 Oct 2:38 pm.

---

### WA-12 HMRC – Authorisation code entry and "Authorization request unknown"

Card: Bug · High · Sami · `hmrc`, `src-ceo` · Team Sprint 5

**Problem.** In his 2 Nov Loom, Sir Waqas shows three problems. The flow fetches automatically where it should ask the user to enter the code. The code text is hard to read. After the code is submitted and the page refreshed, it shows "Authorization request unknown". Separately, Hamna sent a screenshot of an error when a tenant's client requested an authorisation code (3 Nov).

**Requirements**
- The UI prompts the user to enter the code (e.g. "Enter code here") instead of fetching automatically.
- The code is shown in a dark, readable colour.
- An issued code appears in the expected place without manual steps.
- After a valid code is submitted, refreshing shows the authorisation's real state, not "Authorization request unknown".
- Requesting an authorisation code for a client works, or shows a clear reason when it can't.

**Acceptance criteria**
- Each requirement above holds on preprod with a test HMRC agent connection.

**Test on preprod**
Blocked for the QA run: it needs an HMRC connection and a real code. Comes to you, or to Sami, as a "Needs a person" to-do.
Steps (for a person):
1. On a client with HMRC agent authorisation, request an authorisation code.
2. Enter the code where prompted and submit.
3. Refresh and check the status.
Expected:
- As in the requirements, and no "Authorization request unknown".
Also check: SCRUM-1304 (HMRC outside menu) and SCRUM-1292 (PAYE client authorisation).

**Source.** Sir Waqas's Loom, 2 Nov: https://www.loom.com/share/965b5f0a9d524385af3a3df5fc6628e2 (to Sami, you and Umair). Hamna, WhatsApp, 3 Nov 7:27 pm.

---

### WA-13 Tenant Pricing – Upgrading Core to Growth doesn't update the Admin role's permissions

Card: Bug · Medium · Aftab · `tenant-pricing`, `src-sales` · AZ Sprint 5

**Problem.** When a firm upgrades from Core to Growth (from the package icon at the top), the Admin role keeps its Core permissions, so the firm has to grant itself the Growth features by hand. Sir Waqas agreed it should be automatic.

**Requirements and acceptance criteria**
- On upgrade to Growth, the Admin role gets every Growth feature's permission automatically, at once.
- *Proposed, confirm:* on downgrade, Growth-only permissions are removed from every role.
- Custom roles keep what the firm set, apart from removing features the plan no longer includes.

**Test on preprod**
Blocked for the QA run: it changes the plan and permissions. Comes to you as a "Needs a person" to-do.
Steps (for a person):
1. On a Core test firm, note the Admin role's permissions.
2. Upgrade to Growth from the package icon.
3. Reopen Settings → Roles → Admin.
Expected:
- The Growth features are enabled for Admin, with no manual change.
Also check: SCRUM-217 (roles and permissions by package at onboarding) and SCRUM-1333 (AI Summary access by package).

**Source.** Hamna, WhatsApp, 29 Oct 6:05 pm. Sir Waqas, 6:09 pm ("Yes agreed"). Aftab, 6:06 pm ("I'll take a look into this").

---

### WA-14 Leads – Every note shows on the Lead Timeline

Card: Story · High · Abdur Rehman *(suggested)* · `leads`, `src-ceo` · AR Sprint 5

**Context.** Accountants rely on a lead's history for AML and onboarding evidence, and for handovers within the team. Today the lead timeline shows only "Lead Added", and notes added on the lead don't appear. Sir Waqas says this was asked for before, and wrote the full requirement on 30 Oct.

**What to do**
- Write a timeline event (`note_created`, `note_updated`, `note_deleted`) inside the single notes service, so every entry point is covered. Don't build it per screen.
- Backfill existing notes into the timeline with their original timestamps.

**Acceptance criteria**
- Notes from every entry point show on the timeline as "Note Added": the lead side panel Notes section, the timeline's own "+ Add notes" button, notes on tasks, call logs, proposals and emails, and notes created by import or the API.
- Each entry shows the full note text, the author's name and avatar, and the date and time in UK format (Europe/London). Entries are grouped by day under headers like the existing "TODAY".
- Editing a note updates its entry and shows "Edited [date/time] by [user]". Deleting a note leaves the entry as "Note deleted by [user]".
- The "Search timeline…" box finds notes, the Filter has a Notes type, and Latest First / Oldest First applies to notes.
- Existing notes are backfilled with their original timestamps.
- On Convert to Client, the full timeline, notes included, carries over to the client.
- Notes added from the side panel appear on the timeline straight away, without a refresh.

**Test on preprod**
Where: Leads → a QA lead → side panel and Timeline, as Test User.
Before you start: lead "QA Lead WA-14", email suhaib.accotech@gmail.com, no phone number.
Steps:
1. Add a note from the side panel Notes section, then check the timeline without refreshing.
2. Add a note from the timeline's "+ Add notes".
3. Add a note on a task linked to the lead.
4. Edit the first note.
5. Search the timeline for a word in the second note, filter by Notes, and switch Oldest First.
6. Convert the lead to a client and open the client's timeline.
Expected:
- Steps 1–3 each give a "Note Added" entry with the text, author, avatar and UK date and time, grouped by day.
- Step 4 shows "Edited … by …".
- Step 5 finds and filters notes.
- Step 6 shows every note on the client.
Blocked for the QA run: deleting a note, and checking that old notes were backfilled (a person compares an older lead's notes with its timeline).
Also check: 3CX call notes on the timeline (SCRUM-1154) and Convert to Client logging once (SCRUM-1126).

**Source.** Sir Waqas, WhatsApp, 30 Oct 4:39 pm and 4:49 pm ("Remindoo CRM – Notes must appear on the Lead Timeline", priority High).

---

### WA-15 Proposals – Notify the tenant when a lead views a sent proposal

Card: Story · Medium · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**Context.** Hamna asked whether Remindoo tells the firm when a lead opens a proposal. It doesn't. Sir Waqas said it has to be added, as discussed before, and you said you'd assign it to Abdur Rehman (16 Oct). No card was made.

**What to do**
- When a lead opens a sent proposal, notify the firm (the proposal's owner).
- *Proposed:* notify in-app and by email on the first view only. Add a "Proposal viewed" event with the date and time to the lead's timeline, and show "Viewed" with the date in the Proposals table.

**Acceptance criteria** (with the proposed details)
- Opening the proposal link as the lead creates one notification for the owner, one timeline event and a "Viewed" status with the date.
- Opening the proposal preview inside Remindoo doesn't count as a view.

**Test on preprod**
Blocked for the QA run: the lead's link arrives by email. Comes to you as a "Needs a person" to-do.
Steps (for a person):
1. Send a proposal to a QA lead whose email is suhaib.accotech@gmail.com.
2. Open the link from that inbox in a private window.
3. In Remindoo, check notifications, the lead's timeline and the Proposals table.
Expected:
- As in the acceptance criteria.
Also check: SCRUM-1215 (sent proposal sorting) and SCRUM-412 (the proposal-sent event on the timeline).

**Source.** Hamna, WhatsApp, 16 Oct 3:36 pm. Sir Waqas, 3:37 pm ("this has to be added in feature as discussed in the past"). Your reply, 3:37 pm ("assigning to Abdur Rehman").

---

### WA-16 Proposals – Clone an existing LOE template

Card: Story · Medium · Abdur Rehman · `proposals`, `src-ceo` · AR Sprint 5

**What to do**
- Add a Clone (copy) action to each LOE / document template, working the same way as cloning in Prices.
- *Proposed:* the copy is named "<name> (copy)", keeps every element and setting, and opens for editing.

**Acceptance criteria**
- Cloning creates a new template that matches the original. Editing the copy leaves the original unchanged.

**Test on preprod**
Where: Settings → Document Templates.
Steps:
1. Clone "QA LOE WA-05 both" (or any QA template).
2. Compare the copy with the original in the builder and the preview.
3. Change the copy's heading and save, then reopen the original.
Expected:
- The copy matches the original, and the original keeps its heading.

**Source.** Sir Waqas, WhatsApp, 29 Oct 5:38 pm ("Please add an option to clone /copy the existing LOE and create new one. Like we are doing in Prices").

---

### WA-17 Proposals – Undo and Redo in the Document Builder

Card: Story · Medium · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**What to do**
- Add Undo and Redo to the Document Builder.
- *Proposed:* buttons plus Ctrl+Z / Ctrl+Y (Cmd on Mac), covering adding, moving, deleting and editing elements and page settings.

**Acceptance criteria**
- Undo reverses the last change, step by step. Redo reapplies it. History lasts for the editing session.

**Test on preprod**
Where: Document Builder on a QA template.
Steps:
1. Add a text element, move it, then delete it.
2. Undo three times, then Redo three times.
3. Try the keyboard shortcuts.
Expected:
- Each step reverses and reapplies in order, and the shortcuts work.

**Source.** Hamna, WhatsApp, 28 Oct 2:37 pm. AR, 2:40 pm ("ill add that in the list, and schedule it for next sprint").

---

### WA-18 Proposals – Apply page padding to every page at once

Card: Task · Low · Abdur Rehman · `proposals`, `src-sales` · AR Sprint 5

**What to do**
- In page settings, add "Apply to all pages" for padding.
- Consider the same option for the font and background-image settings from the 20 Oct boss meeting notes.

**Acceptance criteria**
- Setting padding with "Apply to all pages" changes every page, and new pages inherit it.

**Test on preprod**
Where: Document Builder on a QA template with three or more pages.
Steps:
1. On page 1, change the padding and choose Apply to all pages.
2. Check every page, then add a new page.
Expected:
- Every page, including the new one, has the new padding.

**Source.** Hamna, WhatsApp, 27 Oct 7:22 pm. AR, 7:24 pm ("noted").

---

### WA-19 Email – Link incoming emails to leads and tasks automatically, not just clients

Card: Story · High · Sami · `email`, `src-ceo` · Team Sprint 5

**Context.** Today an incoming email links automatically only to a client whose email address matches. Sir Waqas wants every email stored where it belongs, otherwise "it kills the purpose of communication". Sami said they'll add it (3 Nov).

**What to do**
- When a connected mailbox receives an email from an address stored on a lead, link it to that lead.
- When a client replies to a task email, link the reply to that task (and to the client).
- Apply the same rule wherever an email address is stored: leads, clients, contacts and tasks.

**Acceptance criteria**
- An email from a lead's address shows on the lead's Communication tab, with the unread badge.
- A reply to a task email shows on that task's Communication tab and the client's.
- Emails from unknown addresses stay unlinked, as now.

**Test on preprod**
Blocked for the QA run: it needs a connected mailbox. Comes to you as a "Needs a person" to-do.
Steps (for a person):
1. With a mailbox connected on preprod, create a QA lead whose email is suhaib.accotech@gmail.com.
2. Email the connected mailbox from that address.
3. Send a task email to a QA client with that address, and reply to it.
Expected:
- The email and the reply land on the lead, task and client, as in the acceptance criteria.
Also check: two-way email in Leads, Clients and Tasks, and the unread badges (in the 6 Nov release).

**Source.** Sir Waqas, WhatsApp, 3 Nov 3:12 pm and 3:16 pm. Sami, 3:14 pm and 3:19 pm ("sure sir. We'll add it.").

---

### WA-20 Email – Email templates in the Email module's compose and reply

Card: Story · Medium · Sami · `email`, `src-ceo` · Team Sprint 5

**Context.** Sir Waqas wants the email templates from Settings available in the Email module. Hamna sent two screenshots of where, the compose window and a second spot (4 Nov).

**What to do**
- Add a template picker to the Email module's compose and reply windows, the two places in Hamna's screenshots. It inserts the template's subject and body.
- Fill tokens for the linked client, lead or task where one is set, with the existing preview (SCRUM-1366).

**Acceptance criteria**
- Choosing a template in compose or reply fills the subject and body.
- Tokens resolve when a client, lead or task is linked. Unresolved tokens are flagged before sending (see SCRUM-1129).

**Test on preprod**
Where: Email module, as Test User. Sending needs a connected mailbox, which the QA run can't use.
Steps:
1. Open compose and pick a template.
2. Open a reply on any existing email and pick a template.
Expected:
- Subject and body fill in both places.
Blocked for the QA run: sending, if no mailbox is connected.

**Source.** Hamna for Sir Waqas, WhatsApp, 4 Nov 3:15 pm ("Sir Waqas wanted email templates to be integrated here in the email module… Here as well").

---

### WA-21 Email – Show completed tasks, tagged Completed, when linking an email to a task

Card: Task · Medium · Sami · `email`, `src-sales` · Team Sprint 5

**What to do**
- In the Email module's "link to task" picker, list completed tasks too, each with a "Completed" tag.

**Acceptance criteria**
- Completed tasks appear in the picker with a Completed tag, and can be linked.
- Open tasks still show first. *(Proposed)*

**Test on preprod**
Where: Email module → an email → link to task, as Test User. It needs at least one email in the module.
Steps:
1. Mark a QA task on "Test" as Complete.
2. Open an email and start linking it to a task for "Test".
Expected:
- The completed QA task is listed with a Completed tag, and linking works.

**Source.** Hamna, WhatsApp, 4 Nov 3:18 pm. Sami, 3:19 pm ("Acknowledged.").

---

### WA-22 Invoices – "Not in Xero" status with sync, and renamed Outstanding Invoices, in Clients and Tasks

Card: Task · Medium · Aftab · `invoices`, `src-ceo` · AZ Sprint 5

**What to do**
- Rename the "Outstanding Invoices" section in the client view and in Tasks. **The new name is waiting on Sir Waqas** (Decisions, item 3).
- When an invoice isn't in Xero (Xero connected), show "Not in Xero" next to it, with a Sync action that pushes it to Xero, as Contacts already offer.
- Do the same in Tasks.

**Acceptance criteria**
- The section shows the new name in Clients and Tasks.
- With Xero connected, an invoice missing from Xero shows "Not in Xero" and syncs from there. After the sync, the label goes.
- Without an accounting connection, no "Not in Xero" label is shown.

**Test on preprod**
Where: a client's invoices section and a task's invoices, as Test User.
Steps:
1. Open "Test" → invoices section and check the section name.
2. Open a QA task with invoices and check the same.
Expected:
- The new name in both places.
Blocked for the QA run: the "Not in Xero" label and the Sync action (no integration syncs). That part comes to you as a "Needs a person" to-do.
Also check: SCRUM-1289 (Tasks show outstanding invoices only) and SCRUM-1160 (invoice numbers).

**Source.** Sir Waqas, WhatsApp, 28 Oct 6:50 pm (to Aftab: "Update the name Outstanding Invoices, also if they are not in xero we should show here No in Xero and should be able to sync from here to like we are doing in contacts. and same in Tasks"). Aftab, 6:53 pm ("Noted").

---

### WA-23 Clients – Client import accepts common abbreviations in list fields

Card: Task · Medium · Abdur Rehman · `clients`, `src-ceo` · AR Sprint 5

**Problem.** A firm wrote "LLP" in the Client Type column of the import CSV. Remindoo only accepts "Limited Liability Partnership", so the row fails.

**What to do**
- For every list-type column in the client import (Client Type, Client Source, Frequency and the rest), accept common abbreviations and other spellings, and map them to the list's options. Matching ignores case and extra spaces.
- Start with the abbreviation list in the acceptance criteria. Keep the list in one place so more can be added.
- Show which mapping was applied in the import results.

**Acceptance criteria**
- "LLP", "llp" and "Limited Liability Partnership" all import as Limited Liability Partnership.
- *Proposed starting list, confirm:* Ltd / Limited Company, LLP, Sole Trader / Self Employed, Partnership, CIC, Charity, Trust. Abdur Rehman to complete it from the options in the system.
- An unknown value still fails, with the row's client name and the accepted values in the error (see SCRUM-1009).

**Test on preprod**
Blocked for the QA run: it needs a CSV upload. Comes to you as a "Needs a person" to-do.
Steps (for a person):
1. Import a CSV with three QA clients whose Client Type is "LLP", "ltd" and "Sole trader".
2. Open each client.
Expected:
- Each gets the full option, and the import results show the mapping.
Also check: SCRUM-1368 (template dropdowns), SCRUM-1369 (imported data dropped) and AR's 30 Oct change ("new values in imported dropdown fields are added as options"). That change may conflict with mapping: an abbreviation should map to the existing option, not be added as a new one.

**Source.** Sir Waqas, WhatsApp, 26 Oct 5:50 pm. Your reply, 5:52 pm (accepted abbreviations mapping onto the original options).

---

### WA-24 Clients – Client table shows the primary director with "+N" when there are more

Card: Task · Medium · Abdur Rehman · `clients`, `src-ceo` · AR Sprint 5 · **wait for Decisions item 4**

**Context.** In his 21 Oct Loom, Sir Waqas says a company with several directors should show "+2" and so on, and that the directors show on some clients and not others. On 22 Oct AR asked whether to list every director, and Sir Waqas answered by voice note.

**What to do** *(confirm against the voice note)*
- Clients table: show the primary contact or director, plus "+N" when the company has more. Hovering or clicking "+N" lists the rest.
- Show directors consistently on every company client.

**Acceptance criteria**
- A company with three directors shows one name and "+2". The tooltip or popup lists the other two.
- Every company client with directors shows them.

**Test on preprod**
Where: Clients table, as Test User.
Before you start: a company client synced from Companies House with two or more directors. If there isn't one, the result is Blocked (no data).
Steps:
1. Find the company in the Clients table and check the directors column.
2. Hover or click "+N".
Expected:
- As in the acceptance criteria.
Also check: SCRUM-1335 (contact type "Director" from the AML modal) and the primary-contact subtitle from the 20 Oct boss notes.

**Source.** Sir Waqas's Loom, 21 Oct (https://www.loom.com/share/ce37603369594c2ab1eef69372f885d4, around 2:17–2:51). AR, WhatsApp, 22 Oct 3:55 pm. Sir Waqas's voice note, 3:59 pm.

---

### WA-25 Settings – One company-wide currency (and date format) used everywhere

Card: Story · Medium · Aftab · `settings`, `src-ceo` · AZ Sprint 5 · stays in Waiting for Requirements until the meeting Aftab asked for

**Context.** In his 4 Nov Loom, Sir Waqas says the currency and date format chosen in Global Settings should apply at company level and be used as the default everywhere: proposals, client values, fee totals and invoices. When the currency changes, values convert at a rate. Use a live rate or a monthly rate, keep it simple, and convert only when needed. Aftab asked Sir Waqas for a meeting on this the same day.

**What to do** *(after the meeting)*
- One currency setting and one date format setting in Global Settings, applied as the default across the app.
- Decide the conversion approach (live or monthly rate) and when conversion happens.

**Acceptance criteria** *(to complete after the meeting)*
- Changing the company currency changes the symbol and formatting in proposals, invoices, client values and fee totals.
- Changing the date format changes it everywhere dates are shown.

**Test on preprod**
Where: Settings → Global Settings, then proposals, invoices and a client. This changes a tenant setting, so record the old value and put it back afterwards.
Steps:
1. Change the currency, and check a proposal's pricing table, an invoice and the client's fee totals.
2. Change the date format and check the same pages.
3. Restore both settings.
Expected:
- To be completed from the acceptance criteria after the meeting.
Also check: SCRUM-877 (invoice-level currency override), SCRUM-982 (tenant-wide date format) and WA-08 (£ in pricing variables). Hamna's 4 Nov date format and alignment screenshot may belong here.

**Source.** Sir Waqas's Loom, 4 Nov: https://www.loom.com/share/156a5ba9378b48c29ee236b0aeda64b8 (to Aftab). Aftab, WhatsApp, 4 Nov 2:08 pm (asks for a meeting on the global currency setting).

---

## Chat-only fixes to verify

These were fixed or changed in the WhatsApp group with no card. If you agree (Decisions, item 7), each gets a record card, moved to Completed without Testing, so the QA run tests it like any card and the progress tracker follows it.

| ID | Card title (proposed) | Owner | What QA checks | QA run can test |
| --- | --- | --- | --- | --- |
| WA-C1 | Email – Sending limit is 10× active clients for every tenant | Sami | The tenant's email limit shown equals 10 × its active clients. Emails sent through a connected Google or Outlook mailbox don't count. Waiting on Decisions item 5 (5× or 10×) | Partly: reading the limit and the client count; not sending 100+ emails |
| WA-C2 | Invoices – Invoice reminders can be turned off, with a warning when accounting software is connected | Aftab | The on/off toggle exists. Turning it off stops Remindoo's invoice reminders. Turning it on with accounting software connected shows the "in addition to the reminders your software sends" confirmation | Partly: the toggle; not the connected-software warning |
| WA-C3 | Super Admin – Disabling a user's MFA while impersonating logged the admin out | Abdur Rehman | Impersonate a test user, disable their MFA, stay logged in, MFA is off | No (Super Admin) |
| WA-C4 | Invoices – Frozen clients were billed | Aftab | A frozen client isn't included in billing. The Season Associates charge itself is your money decision | No (billing) |
| WA-C5 | Proposals – "Can't find? Add Product" button in the product picker | Abdur Rehman | The button is at the top right of the product picker and opens Add Product | Yes |
| WA-C6 | Clients – Bulk import button missing for a firm's admin | Abdur Rehman | A tenant admin sees the bulk import button at the top right of the Clients table | Yes, for Test User |

The 30 Oct and 2 Nov internal server errors (Sami fixed the timeout) don't need a card. If they come back, the QA run's Hangouts reading and the light sweep will catch them.

---

## QA tracking

What the QA system does with these items once the spec is approved and the cards exist.

### 1. Test against the spec
- For each card, the "Test on preprod" block is written to `qa/<KEY>.steps` and posted on the card as its test-steps comment, through the normal `qa_steps` flow. Auto-applied, because every card states its expected behaviour.
- When a card reaches Completed without Testing, the QA run tests it with those steps, as it does any queue card. Results go on the card, with a pass or send-back for you in the Command Center's "QA: results" group.
- Parts marked "Blocked for the QA run" come to you as "Needs a person" to-dos. The run still tests the rest.

### 2. Progress tracker, every QA run
- A watch record in the Command Center, `qawatch/wa-2026-11`, lists every WA card: key, owner, spec section, last status, when it last moved, last QA result and last nudge.
- Each run (4:37 pm and 10:07 pm) makes one Jira query for all the keys and updates the record.
- It adds a **"WhatsApp items progress"** table to the run report and the Dashboard: Waiting for Requirements / Not Started / In Progress / Completed without Testing / Production Ready / Deployed, with days in the current status and the last QA result.
- A card that skipped QA (e.g. went straight to Deployed) or came back after a send-back is flagged in the table.
- When every item is Deployed (or you close it), the watch is marked done.

### 3. Nudges for stalled items
- A card in an **open sprint** that hasn't changed status for **5 working days** (Decisions, item 6) gets a nudge. Backlog cards are never nudged.
- The nudge is one Slack DM per developer, listing their stalled WA cards with key, title and days stalled, and asking for a status update or a blocker.
- It's sent as `dev-dm`, auto-sent under your current settings, with an Activity row. It goes at most once every 5 working days per developer, and never to Sir Waqas, Umair or Sales.

### 4. Chat-only fixes
- With record cards (Decisions, item 7), they're in the QA queue at once, and the next QA run tests them like any card.
- Without record cards, they go in as one `qatests` request (`kind: "chat"`) for the next QA run, marked verify-only.

### 5. What has to change for this to run
- **QA run skill:** `remindoo-qa-run` gets a short "Watch lists" section covering parts 2 and 3. I'll update the staged copy in the Project (`claude/skills-next/remindoo-qa-run.md`). **You re-save the skill on the dev2 account**, since dev2 keeps its own copy of each skill. Test steps (part 1) and chat-only checks (part 4) already work with today's skill.
- **Command Center:** a new `qawatch` collection, plus a `qa.watch` field on the Dashboard. The page shows the Dashboard field once its layout is updated; until then the table is in each QA run report.
- **Vault:** this spec is copied to `Remindoo Documentation/QA/Specs/WhatsApp items 2026-11.md` only after approval, so no sweep reads a draft and makes cards from it.

### 6. On approval, in order
1. Apply your answers to the Decisions, and update this spec.
2. Create the cards (25, plus the record cards if you choose them) by the `remindoo-jira-cards` rules. Each description is the item's section with a link to the spec, and each gets an Activity row (`actor: "chat"`).
3. Write `qa/<KEY>` with the steps, and post the test-steps comments.
4. Create `qawatch/wa-2026-11`, and queue the chat-only checks.
5. Update `claude/skills-next/remindoo-qa-run.md` with the Appendix below, and remind you to re-save it on dev2.
6. Copy the final spec into the vault and the Project.
7. Write the postcode lookup PRD separately, if you agree (Decisions, item 8).

---

## Appendix: "Watch lists" section for the `remindoo-qa-run` skill (draft)

This is the exact text to be added to the QA run skill after "Developer lists". It's here so you can review the wording.

> ## Watch lists (`qawatch`)
>
> Suhaib can ask the QA runs to follow a set of cards through to release, such as the items in a spec. A watch is `qawatch/<id>`: `{name, spec (vault path), status ("active" or "done"), nudgeAfterWorkingDays, items: [{id, key, title, ownerJiraId, slackUserId, specSection, lastStatus, lastMovedAt, lastQaResult, flags, lastNudgeAt}], createdAt}`. The cards' test steps are already in `qa/<KEY>.steps`, written from the spec when the watch was set up.
>
> Each run, after Start and before building the work list:
>
> 1. **Read** `qawatch` where `status` is `active`. For each watch, make one Jira query, `key in (...)`, for status, assignee and sprint (`customfield_10020`).
> 2. **Update each item.** If the status differs from `lastStatus`, set `lastStatus` and `lastMovedAt` (the run time). Copy `lastQaResult` from `qa/<KEY>.testResult`. Set `flags`:
>    - `skipped-qa`: the card is in Production Ready or Deployed with no QA pass (`qa/<KEY>.testResult` isn't `pass` and `result` isn't `passed`).
>    - `sent-back`: it went back to In Progress after a fail.
>    - `no-sprint`: it's in the backlog.
>    Write the watch back, pinned.
> 3. **Testing.** Watch cards in Completed without Testing are tested through the normal work list with their steps. Being on a watch doesn't move them up the queue.
> 4. **Nudges** (afternoon run only, at most once a day). Pick items that meet all of these:
>    - The card is in an open sprint (not the backlog, not Housekeeping).
>    - Its status is Waiting for Requirements, Requirements Updated, Not Started, In Progress or Waiting on Team Dependency.
>    - `lastMovedAt` is more than `nudgeAfterWorkingDays` working days ago (count Mon–Fri, skipping `config/settings.pausedDates`).
>    - `lastNudgeAt` is empty or older than that.
>
>    Group the picked items by developer. Write one `message` item per developer: `messageKind: "dev-dm"`, `group: "QA: watch nudges"`, `ops: [slack.send to their Slack user id]`. Text:
>
>    > Hi <name>, these <watch name> cards haven't moved in <n> working days: KEY title (status, n days), one per line. Could you update the status, or tell Suhaib what's blocking them?
>
>    Auto-send when `config/settings.autoSendMessages` includes `dev-dm` and nothing matches `config/settings.escalate`. Write an Activity row (recipient, link, full text) and set `lastNudgeAt`. Never nudge anyone who isn't the card's developer.
> 5. **Report.** Add a "Watch: <name>" section to the run report. It has a table (ID, KEY, title, owner, status, days in status, last QA result, flags) and the count per status. Set `dashboard/current.qa.watch` to `{name, byStatus, stalled, flagged, updatedAt}`, keeping the other `qa` fields. Add `watchItems` and `nudges` to the runs record's counts.
> 6. **Done.** When every item is Deployed or Delete, set the watch's `status` to `done`, say so in the report, and stop nudging.
>
> Watches are read-only towards Jira: a watch never moves a card or changes its fields. Status moves still come only from test results and Suhaib's approvals.
