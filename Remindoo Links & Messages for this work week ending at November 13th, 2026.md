# Monday
## src-ceo
if an employee has been mark as inactive, please remove it from here too. also add button to remove from here too in case it has not been done (Attached was a picture of the roles and permissions)
https://www.loom.com/share/22e0ad0e53554656baab0d80af450432

> **QA 13 Nov – Not tested.** Tenant 2 has no inactive employee, and the QA rules don't let me deactivate one. Seen on Roles & Permissions: each role's users popup lists people with a role dropdown and has no remove button. The user counts there also don't match Employee List (Admin shows 2 users, Employee List has 3 Admins; Employee shows 1, Employee List has 4). The Loom has no transcript, so I only have the text above. Jira: SCRUM-1520 and SCRUM-1557, both Not Started.



## src-sales
can nayone pls explain this error? Client is asking, "I am trying to delete an employee but unable to, I get an error below. I cant even stop there access. Could you please help?" (Attached was an error showing deletion restriction on non-null constraint for lead attachments of relation creator_id's null value)

> **QA 13 Nov – Not tested.** It needs an employee to be deleted, which the QA rules block. Jira: SCRUM-618 is in Completed without Testing and needs a check by hand.


# Tuesday
## src-ceo
https://www.loom.com/share/91411e6ba508406387524eeed47a0fd0 (About Next Week's Client Table Overhaul)

> **QA 13 Nov – Not built yet.** Jira: SCRUM-1541 (Clients table rebuild) is Waiting for Requirements. Nothing to test on preprod.

https://www.loom.com/share/0444e429184642309d2d697093bac8a1

> **QA 13 Nov – Not tested.** This Loom has no transcript and I can't watch video. Add one line on what it shows and I'll test it.


# Wednesday
## src-ceo
@Umair Saeed @Suhaib Osmani As we spoke about revamping forms as well few weeks ago. https://tally.so/ 

> **QA 13 Nov – Nothing to test.** This is an idea for later, not a change on preprod.

Employee and Admin role should have a tooltip that they cannot be renamed as they were created with the tenant upon its creation.

> **QA 13 Nov – Pass, with a note.** In Edit Role for Admin (and Employee) the Role name field is locked and its tooltip reads "Admin and Employee role names cannot be edited". It doesn't give the reason (created with the tenant), and the helper text under the form only talks about colours.

on the service seelection screen we should show dorp down of only those where where they are other option, we are making user to select years for yearly services(where there is only one service)

> **QA 13 Nov – Fail (not done).** Adding "Accounts - Year End + CT600" to a client still shows a Frequency dropdown whose only option is Yearly. Yearly is pre-selected, so nothing has to be picked, but the dropdown is still there.

if an employees i smade inactive, he should be removed from the team too, or we can ask at the time of making inactive, remove it from the team

> **QA 13 Nov – Not tested.** Same reason as Monday's item: no inactive employee in Tenant 2 and I can't deactivate one. Teams page shows 2 teams with 1 member each. Jira: SCRUM-1520 / SCRUM-1557, Not Started.

https://www.loom.com/share/70047e5f85af48eba76eb694c0ace3bd 

> **QA 13 Nov – Not tested.** No transcript (Loom title: "Search results – Mail").

duplicates should be highlighted please

> **QA 13 Nov – Unclear.** I couldn't tell where duplicates should be highlighted (clients, leads or emails). No duplicate highlighting was seen in the Clients table.

Toggle buttons on all custom fields that are compulsory in the client profile custom fields section

> **QA 13 Nov – Unclear / not seen.** Settings → Client Custom Fields shows Compulsory as Yes/No pills, not toggle switches. In the client profile only Personal UTR, National Insurance Number and Authentication Code have toggles. Tell me which screen this means and I'll recheck.



## src-sales
https://www.loom.com/share/910fdd75e09845608a5934ed5adde0bd (When I tag someone, it's not updating under "Mention")

> **QA 13 Nov – Fail (bug reproduced).** On task "QA Regression task 13 Nov" I posted a comment tagging Michael Eldred Clark. The comment and the tag appear in the conversation and Activity, but the row's Mentions popup still says "No unread mentions" with From/Asked/Waiting/Ask all blank, before and after a reload. Caveat: I could only tag my own test account, so a second user should confirm.


# Thursday
## src-ceo
We need to add copilot and claude here too for summaries and then Ai client summary as well as it was there before (Slated for Next Week)

> **QA 13 Nov – Claude/Copilot: not built yet.** Settings → Integrations → Connect AI Account → Add New Provider offers only DeepSeek and OpenAI. Jira: SCRUM-1558, Waiting for Requirements.
> **AI client summary: Pass.** With the OpenAI provider active, AI Summary on client "maddy pvt ltd" produced a summary in about 30 seconds.

https://www.loom.com/share/ce9ecb171b8b4345a1f59088f098814f

> **QA 13 Nov – Not tested.** No transcript (Loom title: "Service & Reminders").

Since no client is associated with a Quick Task, users cannot upload e-signature documents for it. I will keep the activity icon disabled and display a tooltip explaining why this functionality is unavailable. (Zain committed to CEO in Tasks Table)

> **QA 13 Nov – Pass.** On a Quick Task with no client the e-Signatures icon is disabled, shows a not-allowed cursor, and its tooltip says "This is an internal task, you can't add e-sign documents with it."

https://www.loom.com/share/c796304329d749789d9ced485bdb307b (E-Sign)

> **QA 13 Nov – Not tested.** Signing happens through an emailed link, which I can't follow. Jira: SCRUM-1571 (go to the next field, download all at the end) is Not Started.

https://www.loom.com/share/e9cc285d281848ee83d5f8c8b9ed3ed2

> **QA 13 Nov – Fail, if this is the "Document Signed" timeline item (SCRUM-1572, Completed without Testing).** No transcript, so that's my guess from the card raised the same afternoon. On task "QA 1303 Wizard AA LIMITED - 10/11/2026" the Activity entry "Document Signed, 11/11/2026 14:42" shows no signer and no document name, and "Document Sent" shows the sender but no document. The same event in the client's Activity does show the document, task and signer. The entry is from 11 Nov, so a document signed after the fix still needs checking by hand.



## src-sales

https://www.loom.com/share/4f3e7310614a4ede8d5fec64be2420fe

> **QA 13 Nov – Fail (bug reproduced).** I archived client "QA 1303 Wizard A" with the reason "QA archive reason test 13 Nov". Its Activity shows "status: Active → Archived" with my name and time but no reason. (A Tenant 2 automation then moved it to Frozen; I set it back to Active afterwards.) Tasks and leads have no reason field when archived.


---
## QA summary, Fri 13 Nov 2026 (Claude, preprod, Tenant 2 as Michael Eldred Clark)

- **Pass (3):** role-name tooltip (with a wording note), Quick Task e-sign icon and tooltip, AI client summary.
- **Fail (4):** single-option Frequency dropdown still shown, Mentions not updating, "Document Signed" timeline entry (SCRUM-1572), archive reason missing from the client timeline.
- **Not built yet (2):** Claude/Copilot providers (SCRUM-1558), Clients table overhaul (SCRUM-1541).
- **Not tested (7):** inactive employee in roles, inactive employee in teams, employee deletion, multi-document e-sign, and three Looms with no transcript.
- **Unclear (2):** "duplicates should be highlighted", toggles on compulsory custom fields.
- **Nothing to test (1):** tally.so idea.

Test data touched: comment on "QA Regression task 13 Nov"; client "QA 1303 Wizard A" archived and restored to Active (two status changes in its Activity). QA result comments posted on SCRUM-1572 and SCRUM-1558.
