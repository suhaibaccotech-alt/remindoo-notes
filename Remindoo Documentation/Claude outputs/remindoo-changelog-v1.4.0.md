# v1.4.0 – 22 October 2026

This release brings new tools across Clients, Tasks, Proposals and Invoices, a clearer Tasks table, a more capable Document Builder and a long list of fixes.

## New

- **Whole App** – A new in-app changelog, so you can see what's new and what's been fixed in each release.
- **Clients** – Client Authorisation status shown on each custom field column in the Clients table.
- **Clients** – Outstanding invoices shown on the client card and client profile.
- **Clients** – Letter of clearance tracker, to record when a letter of clearance has been received.
- **Clients** – The primary contact's name now appears under the client name (or the linked company for contacts converted to clients).
- **Clients** – Direct debit status shown in the invoice window.
- **Clients** – Pausing a service, and switching reminders or emails on or off, now asks you to confirm and is recorded on the timeline.
- **Clients** – Bulk delete in the AML window.
- **Tasks** – Task Completion Date column, with a filter.
- **Tasks** – A pop-up for the Progress column.
- **Tasks** – The latest action date now shows under the task window's action buttons, with a new Next Step button beside Next Page.
- **Tasks** – Emails sent from a task now go through Email Logs, and you can preview how tokens will be filled in before sending.
- **Proposals and E-Sign** – When creating a proposal from a lead's profile, you can choose to edit an existing proposal or create a new one. There's also a New Proposal button in Document Templates.
- **Proposals and E-Sign** – Document Builder: global font styling, page backgrounds for one or all pages, uploads, better contrast for white text, a way back to Pricing and more templates.
- **Proposals and E-Sign** – "Greater than" and "less than" options in the pricing filter.
- **Invoices** – Invoice templates are pulled from your connected accounting software.
- **Email** – Every automated email now carries the Remindoo header and footer.
- **Settings** – Separate visibility permissions for Tasks and Clients.
- **Settings** – Client custom fields: a visibility button with Save, tooltips on each column and the remaining client fields.

## Improved

- **Whole App** – The upper-right menu now has a Sign out button, changing your package works properly and the balance uses the same font as the rest of the app.
- **Clients** – Faster bulk reassignment of service assignees, service managers and partners from the Clients table.
- **Clients** – Bulk emails to clients now offer tokens.
- **Clients** – Assignee columns are left-aligned, and sorting applies to the whole page, with an option to sort the whole table.
- **Clients** – Accounts and confirmation statement dates now come from service custom fields everywhere, replacing the separate Companies House import fields.
- **Clients** – Security improvements to client list filtering.
- **Clients** – The bulk email information note is no longer shown in red like an error.
- **Leads** – Applied filters are clearer, with their sections separated.
- **Tasks** – The Tasks table now has Partner and Service Manager columns, plus the columns and icons from the previous table.
- **Tasks** – Only outstanding invoices are shown.
- **Proposals and E-Sign** – "Send Invite" is now "Send for Signature", with the same E-Sign icon in Tasks and Clients.
- **Proposals and E-Sign** – Searching the proposals table now matches the lead's name as well as the proposal name.
- **Proposals and E-Sign** – Loading indicators on the package and product creation buttons.
- **Invoices** – Accounting software logos, a cleaner look for the main cards and the same token layout as the rest of the app.
- **Invoices** – Invoices now show bank details for bank transfer, the VAT rate on each line and full dates including the year.
- **Email** – Loading placeholders while email categories load.
- **Automation** – Timeline notes now show when an action was carried out by an automation.
- **Settings** – Multi-factor authentication is now on by default for new firms.
- **Settings** – The HMRC settings page has a cleaner design with better use of space.
- **Settings** – The HMRC "Delete Account" button is now called "Disconnect".
- **Plans and Billing** – Free trial: 14 days without a card, or 60 days with a card.

## Fixed

- **Whole App** – Knowledge Base article cards show the right view count, the details no longer wrap and co-author photos no longer overlap.
- **Clients** – The duplicate Personal UTR warning no longer refers to a Company UTR.
- **Clients** – The bulk actions bar no longer covers the Total Fee and Hours figures.
- **Clients** – Client onboarding no longer freezes when you switch Previous Accountant on the Internal Information step.
- **Clients** – "Service is at capacity" error no longer appears when refreshing the page.
- **Clients** – Inactive VAT reminders are no longer sent.
- **Clients** – The National Insurance toggle is back when creating a client.
- **Leads** – Status and Source filters now return the right leads.
- **Leads** – Convert to Client now asks you to confirm, and the conversion is logged once.
- **Leads** – Dragging cards on the Kanban board now moves them.
- **Leads** – Warm, Cold and Wants to Talk status labels now have their colours.
- **Leads** – Companies House dates are carried over when a lead is converted to a client.
- **Leads** – The tokens list now shows the real lead tokens.
- **Tasks** – Emails sent from a task now appear in the timeline notes.
- **Tasks** – Email Logs now include emails sent by automations.
- **Tasks** – The description editor no longer drops the first word you type.
- **Tasks** – The completion date is now saved when a task is moved to Complete.
- **Tasks** – The timeline icon is no longer cut off on the first entry.
- **Tasks** – The Document Checklist "Go" button opens the right page.
- **Tasks** – Document checklists can be deleted inside a task.
- **Tasks** – The "Edit Reminder" tooltip now says the right thing.
- **Tasks** – The recurring tasks manager shows the correct next refresh date, and the next run moves forward as it should.
- **Tasks** – Monthly recurring tasks are no longer created every day.
- **Tasks** – The detailed task name list only shows the selected client's tasks.
- **Tasks** – Kanban totals match the table, and the In Progress count stays the same on reload.
- **Tasks** – Review checklist text no longer breaks in the middle of words.
- **Tasks** – Photos on the task timeline now load properly.
- **Proposals and E-Sign** – The email field no longer accepts invalid email addresses.
- **Proposals and E-Sign** – The notes field no longer shows raw code.
- **Proposals and E-Sign** – The "Service Proposal" template no longer appears upside down in the Document Builder.
- **Proposals and E-Sign** – Elements no longer overlap when importing a template.
- **Proposals and E-Sign** – Pre-built cover page designs can be edited properly.
- **Proposals and E-Sign** – The date on a signed proposal can no longer be changed in preview.
- **Proposals and E-Sign** – The "is not" filter now excludes the selected lead.
- **Proposals and E-Sign** – PDF content no longer spills onto the bottom of the send-email step.
- **Proposals and E-Sign** – Kanban cards in the Sent column now show the lead's name.
- **Proposals and E-Sign** – Opening a submitted template in the editor no longer sets it back to Draft.
- **Proposals and E-Sign** – Turnover-bracket prices now show correctly in the pricing table and client letter, instead of £0.
- **Invoices** – Monthly recurring plans now run monthly, and duplicate plans no longer send two invoices a day.
- **Invoices** – Invoices now show your firm's details instead of placeholder seller details.
- **Invoices** – Recurring invoices follow your invoice numbering sequence.
- **Invoices** – Invoices due today are no longer listed as overdue.
- **Invoices** – The Copy Link button copies the invoice link.
- **Invoices** – FreeAgent invoicing uses the right account.
- **Document Portal and Client Portal** – The Document Portal shows the correct storage information.
- **Document Portal and Client Portal** – Opening the client portal from Remindoo no longer gives an "invalid link" error.
- **Email** – The tokens list now shows in every email editor.
- **Email** – The View Task button in emails for tasks created from client services opens the right page.
- **Automation** – Inactive automation rules no longer run.
- **Settings** – When creating subtask templates, typing in the Title field no longer fills Step 1 as well.
- **Settings** – The first "Show Details" click in the Settings hub now works.
- **Settings** – "Request agent authorisation" is only offered once an HMRC agent account is set up.
- **Settings** – The HMRC client authorisation request email uses the right tokens and supports attachments.
- **Integrations and AI** – The Financial Assistant now responds when you send a question.
