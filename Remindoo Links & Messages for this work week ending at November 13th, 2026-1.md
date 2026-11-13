# Monday
## src-ceo
if an employee has been mark as inactive, please remove it from here too. also add button to remove from here too in case it has not been done (Attached was a picture of the roles and permissions)
https://www.loom.com/share/22e0ad0e53554656baab0d80af450432

> **QA 13 Nov – Not tested.** Tenant 2 has no inactive employee, and the QA rules don't let me deactivate one. Seen on Roles & Permissions: each role's users popup lists people with a role dropdown and has no remove button. The user counts there also don't match Employee List (Admin shows 2 users, Employee List has 3 Admins; Employee shows 1, Employee List has 4). The Loom has no transcript, so I only have the text above. Jira: SCRUM-1520 and SCRUM-1557, both Not Started.

> **QA 13 Nov evening (Tenant 1, Test User) – Still not tested** (same reason). In Tenant 1 the role counts do match: Roles page Admin 6 users, Employee List 6 active, all Admin.
> **The Loom (now transcribed) is about something else: GoCardless and the Clients table.**
> - Mandate status on the Clients table: a "GoCardless Direct Debit" column exists and shows "Not connected" for every client ("Stripe Direct Debit" shows "Not found in Stripe"). Statuses and the logo can't be checked without a connected GoCardless account.
> - Dropdown custom fields as dropdowns in the filter: **Fail.** "Test Dropdown 1" → "is" gives a free-text Value box.
> - Same page length everywhere: not provable in Tenant 1. Tenant page length is 100; the Clients table (10) and Client Custom Fields (19) both fit on one page.



## src-sales
can nayone pls explain this error? Client is asking, "I am trying to delete an employee but unable to, I get an error below. I cant even stop there access. Could you please help?" (Attached was an error showing deletion restriction on non-null constraint for lead attachments of relation creator_id's null value)

> **QA 13 Nov – Not tested.** It needs an employee to be deleted, which the QA rules block. Jira: SCRUM-618 is in Completed without Testing and needs a check by hand.


# Tuesday
## src-ceo
https://www.loom.com/share/91411e6ba508406387524eeed47a0fd0 (About Next Week's Client Table Overhaul)

> **QA 13 Nov – Not built yet.** Jira: SCRUM-1541 (Clients table rebuild) is Waiting for Requirements. Nothing to test on preprod.

> **QA 13 Nov evening (Tenant 1) – the parts of this call that are on preprod now:**
> - Client Custom Fields should autosave: **Fail.** Changing "Visible in Clients Table" shows a small save icon on the row; without clicking it the change is gone after a reload. There is no Save Changes button.
> - A field set to visible should appear in Column Visibility: **Pass** once the row is saved ("Google Review" appeared). I didn't check that it pulls data.
> - Dropdown fields as dropdowns in Filters: **Fail** (see Monday).
> - Leads "All" shouldn't show Converted: **Fail.** All lists 35 leads, 33 of them Converted To Client.
> - Average Hours: N/A for all 10 active clients.
> - Not tested yet: "Filed externally" note on tasks, signed e-sign items turning green, close icons on popups.

https://www.loom.com/share/0444e429184642309d2d697093bac8a1

> **QA 13 Nov – Not tested.** This Loom has no transcript and I can't watch video. Add one line on what it shows and I'll test it.

> **QA 13 Nov evening (Tenant 1) – now transcribed: remaining hours in Assign Team Members, and reassigning subtasks with the task.**
> - Remaining hours: **Not built.** Client "Test" → Add Services → Assign Team Members: the Teams and Employees tabs show names only, with no allocated or remaining hours.
> - Subtasks following a reassigned task (with a checkbox): not tested yet.


# Wednesday
## src-ceo
@Umair Saeed @Suhaib Osmani As we spoke about revamping forms as well few weeks ago. https://tally.so/ 

> **QA 13 Nov – Nothing to test.** This is an idea for later, not a change on preprod.

Employee and Admin role should have a tooltip that they cannot be renamed as they were created with the tenant upon its creation.

> **QA 13 Nov – Pass, with a note.** In Edit Role for Admin (and Employee) the Role name field is locked and its tooltip reads "Admin and Employee role names cannot be edited". It doesn't give the reason (created with the tenant), and the helper text under the form only talks about colours.

on the service seelection screen we should show dorp down of only those where where they are other option, we are making user to select years for yearly services(where there is only one service)

> **QA 13 Nov – Fail (not done).** Adding "Accounts - Year End + CT600" to a client still shows a Frequency dropdown whose only option is Yearly. Yearly is pre-selected, so nothing has to be picked, but the dropdown is still there.

> **QA 13 Nov evening (Tenant 1) – Still failing.** Same result on client "Test": the Frequency dropdown is there with Yearly preselected.

if an employees i smade inactive, he should be removed from the team too, or we can ask at the time of making inactive, remove it from the team

> **QA 13 Nov – Not tested.** Same reason as Monday's item: no inactive employee in Tenant 2 and I can't deactivate one. Teams page shows 2 teams with 1 member each. Jira: SCRUM-1520 / SCRUM-1557, Not Started.

> **QA 13 Nov evening (Tenant 1) – Still not tested** (same reason). The team editor itself works here: Edit QA Team B lists the 1 unassigned employee and the 5 in other teams.

https://www.loom.com/share/70047e5f85af48eba76eb694c0ace3bd 

> **QA 13 Nov – Not tested.** No transcript (Loom title: "Search results – Mail").

duplicates should be highlighted please

> **QA 13 Nov – Unclear.** I couldn't tell where duplicates should be highlighted (clients, leads or emails). No duplicate highlighting was seen in the Clients table.

Toggle buttons on all custom fields that are compulsory in the client profile custom fields section

> **QA 13 Nov – Unclear / not seen.** Settings → Client Custom Fields shows Compulsory as Yes/No pills, not toggle switches. In the client profile only Personal UTR, National Insurance Number and Authentication Code have toggles. Tell me which screen this means and I'll recheck.

> **QA 13 Nov evening (Tenant 1) – Still not settled.** Compulsory is still a Yes/No dropdown in Settings. In the client profile, Tenant 1's only additional field ("Test") shows a toggle. The Tenant 2 field "test now" wasn't rechecked.



## src-sales
https://www.loom.com/share/910fdd75e09845608a5934ed5adde0bd (When I tag someone, it's not updating under "Mention")

> **QA 13 Nov – Fail (bug reproduced).** On task "QA Regression task 13 Nov" I posted a comment tagging Michael Eldred Clark. The comment and the tag appear in the conversation and Activity, but the row's Mentions popup still says "No unread mentions" with From/Asked/Waiting/Ask all blank, before and after a reload. Caveat: I could only tag my own test account, so a second user should confirm.

> **QA 13 Nov evening – Not retested yet** (the browser connection dropped before I got to it).


# Thursday
## src-ceo
We need to add copilot and claude here too for summaries and then Ai client summary as well as it was there before (Slated for Next Week)

> **QA 13 Nov – Claude/Copilot: not built yet.** Settings → Integrations → Connect AI Account → Add New Provider offers only DeepSeek and OpenAI. Jira: SCRUM-1558, Waiting for Requirements.
> **AI client summary: Pass.** With the OpenAI provider active, AI Summary on client "maddy pvt ltd" produced a summary in about 30 seconds.

> **QA 13 Nov evening (Tenant 1) – AI Summary with no provider connected: Fail.** On client "Test" the AI Summary button does nothing and shows no message.

https://www.loom.com/share/ce9ecb171b8b4345a1f59088f098814f

> **QA 13 Nov – Not tested.** No transcript (Loom title: "Service & Reminders").

> **QA 13 Nov evening (Tenant 1) – now transcribed and tested, Settings → Services Templates & Reminders:**
> - Sorting: **Pass.** Every column has sort arrows.
> - Active / Inactive: **Pass.** All 13 / Active 13 / Inactive 0 tabs, and a status menu on each row. "Test Service A" went to Inactive and back to Active.
> - "Missing authentication token": **not reproduced** on search or on a status change.
> - Search while typing: **Fail.** Typing "test" left all 13 listed; Enter filtered to 5.
> - Deleting the "Test" template: **not tested**, the QA rules don't allow deleting.

Since no client is associated with a Quick Task, users cannot upload e-signature documents for it. I will keep the activity icon disabled and display a tooltip explaining why this functionality is unavailable. (Zain committed to CEO in Tasks Table)

> **QA 13 Nov – Pass.** On a Quick Task with no client the e-Signatures icon is disabled, shows a not-allowed cursor, and its tooltip says "This is an internal task, you can't add e-sign documents with it."

https://www.loom.com/share/c796304329d749789d9ced485bdb307b (E-Sign)

> **QA 13 Nov – Not tested.** Signing happens through an emailed link, which I can't follow. Jira: SCRUM-1571 (go to the next field, download all at the end) is Not Started.

https://www.loom.com/share/e9cc285d281848ee83d5f8c8b9ed3ed2

> **QA 13 Nov – Fail, if this is the "Document Signed" timeline item (SCRUM-1572, Completed without Testing).** No transcript, so that's my guess from the card raised the same afternoon. On task "QA 1303 Wizard AA LIMITED - 10/11/2026" the Activity entry "Document Signed, 11/11/2026 14:42" shows no signer and no document name, and "Document Sent" shows the sender but no document. The same event in the client's Activity does show the document, task and signer. The entry is from 11 Nov, so a document signed after the fix still needs checking by hand.

> **QA 13 Nov evening – the transcript confirms this is the Document Signed item (SCRUM-1572).** Not retested yet (the browser connection dropped before I got to it).



## src-sales

https://www.loom.com/share/4f3e7310614a4ede8d5fec64be2420fe

> **QA 13 Nov – Fail (bug reproduced).** I archived client "QA 1303 Wizard A" with the reason "QA archive reason test 13 Nov". Its Activity shows "status: Active → Archived" with my name and time but no reason. (A Tenant 2 automation then moved it to Frozen; I set it back to Active afterwards.) Tasks and leads have no reason field when archived.

> **QA 13 Nov evening – Not retested yet.**


---
## QA summary, Fri 13 Nov 2026 (Claude, preprod, Tenant 2 as Michael Eldred Clark)

- **Pass (3):** role-name tooltip (with a wording note), Quick Task e-sign icon and tooltip, AI client summary.
- **Fail (4):** single-option Frequency dropdown still shown, Mentions not updating, "Document Signed" timeline entry (SCRUM-1572), archive reason missing from the client timeline.
- **Not built yet (2):** Claude/Copilot providers (SCRUM-1558), Clients table overhaul (SCRUM-1541).
- **Not tested (7):** inactive employee in roles, inactive employee in teams, employee deletion, multi-document e-sign, and three Looms with no transcript.
- **Unclear (2):** "duplicates should be highlighted", toggles on compulsory custom fields.
- **Nothing to test (1):** tally.so idea.

Test data touched: comment on "QA Regression task 13 Nov"; client "QA 1303 Wizard A" archived and restored to Active (two status changes in its Activity). QA result comments posted on SCRUM-1572 and SCRUM-1558.

---
## QA summary, Fri 13 Nov 2026 evening, 5:45–6:10 pm (Claude, preprod, Tenant 1 as Test User, on AT95) – run not finished

The browser connection dropped at about 6:05 pm. Full report: `claude/qa-runs/2026-11-13-retest-ar-zain-looms.md` in the project.

- **Still failing:** single-option Frequency dropdown; service template search while typing; Client Custom Fields autosave; dropdown custom fields in the Clients filter; Leads "All" lists converted leads; AI Summary with no provider gives no message.
- **Pass:** service template sorting and Active/Inactive; a field set to visible appears in Column Visibility.
- **Not reproduced:** "Missing authentication token" on service templates.
- **Not built:** remaining hours in Assign Team Members.
- **Not retested yet:** Mentions, Document Signed timeline (SCRUM-1572), archive reason, subtask reassignment, "Filed externally" note.
- **Still not testable under the QA rules:** inactive employee in roles and teams, employee deletion, deleting a service template, multi-document e-sign.

Left on preprod (Tenant 1): draft client "QA Retest Client 13 Nov PM" (wizard left at Contacts). **Setting still to restore:** Client Custom Fields → Internal Information → Google Review, "Visible in Clients Table" is Yes (was No).
