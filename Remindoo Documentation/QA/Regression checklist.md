# Regression checklist (automated QA runs)

This is the reference list for the release-Wednesday regression in the automated QA runs. It is not a set of notes to turn into cards. Edit it freely on AT95, adding or removing checks; the next run uses whatever is here.

How the runs use it: preprod only (preprod-crm.remindoo.co), signed in as Test User, in the test tenant. These are quick smoke checks of a few minutes per area, not full card tests. Anything new is named "QA Regression <date>". Emails go only to suhaib.accotech@gmail.com. Nothing is deleted.

## Sign-in and navigation
- After sign-in, the dashboard loads, and every main page opens without an error: Clients, Leads, Tasks, Invoices, Proposals, Automations, Settings.
- The console shows no new errors beyond the known 3CX WebSocket errors.
- Profile pictures load. Known bug: the S3 address is prefixed with the preprod domain.

## Clients
- The clients table loads, search finds client "Test", and sorting works.
- A client profile opens, with its Overview, Services, Contacts, Documents and Timeline tabs.
- The new-client wizard saves its first step. Don't finish it unless the release changed the wizard.
- Manage Services: client "Test" shows VAT (Monthly) and VAT (Quarterly) as separate instances.
- "Export selected clients to CSV" works.

## Leads
- The leads table loads, and the Status and Source filters return results.
- A lead profile opens and its timeline shows events.
- Preview Email in the email modal fills in the tokens.

## Tasks
- The tasks table loads, filters and saved filters apply, and the Kanban counts match the table.
- The task modal opens, a progress status change saves, and the Timer Logs popup opens.
- The recurring task "QA Recurring 1113 Daily" has refreshed to the next date.
- Create a task named "QA Regression task <date>", then complete it.

## Dashboard
- The Tasks dashboard loads within a few seconds, and the team filter applies.
- Card counts match list counts on two of the cards.

## Invoices
- The invoices list loads, and sorting by Amount works.
- The invoice preview shows the tenant's seller details.
- Raise Invoice from a task prefills the client and service. Create one only if the release changed invoicing, and email it only to suhaib.accotech@gmail.com.
- Record Payment opens. Don't save unless the release changed payments.

## Proposals
- The proposal templates list loads, the builder opens a template, and the pricing table renders.

## Automations
- The automations list loads, and the QA rules are still paused.
- A rule opens in the builder. Don't save it.

## Email
- The Reminders tab token list loads.

## Settings
- The service templates list opens, and a template shows its frequencies.
- The teams list shows QA Team A and QA Team B.

## Document portal
- Storage usage shows (it was 472.6 MB of 3 GB on Nov 2).
