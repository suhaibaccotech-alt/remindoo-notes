# QA run, Thu 5 Nov 2026 ~7:50–8:20 pm (chat, Companies House sync and client import)

Run id: 20261105-qa-ch (task qa-chat, with Suhaib). Stopped at Suhaib's request before any sync was run.

## Environment
- Started in **Tenant 1** as Test User. Willy Wonka (08674020) was already there ("Already Added"), and Test User got "Access denied" on /clients, although the onboarding wizard still opened.
- Continued in **Document Testing Tenant 2** as **Michael Eldred Clark** (Suhaib signed in).

## What was done
1. **Import from Companies House** (New Client): search "WILLY WONKA LIMITED", select it. The name, type, company number, address, SIC 79110 and incorporation date pre-filled. I added SA Register Date 05/11/2026, email suhaib.accotech@gmail.com, and "test now" = "QA CH sync 5 Nov". Saved: "Client created successfully" (Draft). I stopped before Services, so no tasks were created.
2. **CSV import**: built from the frontend template `/client_import_template.csv` (166 columns). 100 real active companies from the public register (bakery, plumbing, consulting, dental and joinery searches; England & Wales, Scotland, NI). Type "Private Limited Company", dates dd/mm/yyyy, every row's email set to suhaib.accotech@gmail.com, note "QA import 5 Nov 2026 - Companies House sync test", all service columns blank. File: `qa_client_import_100.csv`.
3. A 1-row re-test (BLACK RABBIT BAKERY LTD) to check the result reporting.

## Results
- **Pass:** Import from Companies House pre-fills the company data and saves.
- **Fail:** the 100-row import got stuck at "0/100, 0%" (while saying "Item 100 of 100"), then reported **0 created**. In fact the rows were created as Drafts (BLACK RABBIT BAKERY LTD, SG JOINERY LTD and others are found by global search). The 1-row import reported 1 correctly.
- **Fail:** the new drafts (and Willy Wonka) don't show in the Clients list, the Draft tab or list search. Only the top global search finds them. The list seems limited to the user's assigned clients, so **bulk Sync couldn't be run** on them.
- **Fail:** no duplicate check. Tenant 2 already had two WILLY WONKA LIMITED clients and still allowed a third; BLACK RABBIT was imported twice.
- **Fail:** the "Company House Sync" log shows an existing job ("NEW JUST TEST") stuck on Pending.
- **Minor:** CH search says "1 of 222 companies" across 19 pages, but page 2 is empty. After Finalise, the toast says "Showing Draft tab" but the Active list is shown.
- **Bulk actions seen:** selecting a client shows a bar with Send, **Sync**, Download, Transfer, Refresh and Delete. I didn't click any of them.

## Proposed in the Inbox (group "QA: Companies House sync & import", owner to choose)
1. CSV import reports 0 created when all rows were created (High).
2. Imported and new drafts missing from the Clients list and its search (High).
3. No duplicate check on company number (Medium).
4. Companies House sync job stuck on Pending (High).
5. CH search count and pages wrong (Low).
6. Test User can open client creation but not the Clients list (Medium).

## Test data left on preprod (Tenant 2)
- WILLY WONKA LIMITED (Draft, the third copy).
- 100 imported Draft clients, plus a second BLACK RABBIT BAKERY LTD. All have the QA email and note, and no services or tasks. Nothing deleted.

## Next
- Find out why Michael Eldred Clark can't see unassigned or Draft clients in the list. Then re-run bulk Sync on all 101 and check the Updated Fields and New Tasks counts.
