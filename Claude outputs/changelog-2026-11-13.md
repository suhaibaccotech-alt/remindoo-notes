# Remindoo Changelog

**Released:** Friday 13 November 2026

---

## Clients and Contacts

- **AI Client Summary:** AI Summary in the client quick view generates a summary of the client.
- **Contact Area Code:** A contact's area code is now kept as entered (e.g. United Kingdom | +44).
- **AML Proof of Address:** The Proof of Address warning section no longer opens automatically.
- **Import and Export Icons:** Updated the Import and Export icons in the Clients module.
- **Bulk Export CSV:** Fixed Export selected clients to CSV downloading nothing.
- **Search with One Match:** Fixed a search with a single result still offering a second page and leaving the row greyed out.
- **Client Name with Badges:** Fixed the client name being hidden in the list row when the New and LOC badges show.
- **Services Loading:** Fixed the Services table showing through while the client profile is loading.

## Client Onboarding

- **Duplicate UTR:** A personal UTR that already belongs to another client is now caught.
- **Wizard Heading:** Fixed the heading overlapping the "Import from Companies House" link, and Next now works on the first click.

## Leads

- **Two-Way Email:** Send and receive emails from within a lead.
- **Notes in Activity:** Notes can be added to the lead's Activity tab.
- **Activities Column:** Added an Activities column to the Leads list.
- **Billable / Non-Billable:** Tasks on the lead detail screen now show whether they are billable or non-billable.
- **Task Action Tooltips:** Added tooltips to the task action buttons on the lead detail screen.
- **Filter Dialog:** Fixed the filter dialog overlay, and the Assignee filter now shows names instead of IDs.
- **Proposal Details:** Corrected Sent to, Total (incl. VAT), Created by and Sent by in the lead's proposal details.
- **Custom Field Type Selector:** Fixed the field type selector being squashed when adding a custom field.

## Tasks

- **New Tasks Table:** A new, redesigned Tasks table.
- **Task Status and Progress Status:** Added task status and progress status fields.
- **Sorting:** Added sorting to the Tasks table, consistent with the Clients module.
- **Service Badge:** The service name appears as a badge; clicking it shows the SATR, PTR, VAT and Accounts dates.
- **Row Badges:** Only the VAT and Recurring badges are shown next to the task name, keeping rows cleaner.
- **Outstanding Invoices Column:** Added an Outstanding Invoices column showing the client's outstanding invoices, consistent with the Clients list.
- **Invoices Popover:** The invoices popover now shows all of the client's invoices, not only those tied to the task.
- **Assignees on Subtasks:** When updating a task's assignees, you can apply the same assignees to all of its subtasks.
- **Email Preview:** Task emails are recorded in Email Logs, and you can preview the email before sending.
- **Activity Icons (Tasks and Leads):** Activity icons are grey when there is no activity and coloured when there is.
- **E-Sign Icon:** The e-sign icon turns light green when all documents in that activity are signed.
- **Quick Task E-Signatures:** On a Quick Task with no client, the e-signature icon is disabled, with a tooltip explaining why.
- **E-Sign Resend:** Fixed the styling of the Resend button after selecting a document to resend.

## Conversations (Tasks, Leads and Clients)

- **Conversations:** Tasks, Leads and Clients now have a conversation timeline for comments, notes and emails.
- **Live Updates:** Comments, notes and sent emails appear in the timeline immediately, without a refresh.
- **Unread Indicator:** Unread email threads are marked so they are easy to spot.
- **Notes Validation:** Empty or invalid notes are blocked with clear feedback.
- **Email Label Tooltip:** Added a tooltip on the Submit button when adding a label to an email, explaining what happens on submit.
- **Notes Display:** Fixed note content not displaying correctly.

## Email

- **Two-Way Email:** Two-way email now works the same way across Leads, Clients, Tasks and Proposals.
- **Preview Button:** Every email window has a Preview button showing the email filled with the real client or lead details.
- **Tokens in Composer:** Tokens can now be added in the email composer.
- **Tokens in Replies:** When a client, task or lead is attached to an email thread, tokens in replies are filled in automatically.
- **Unresolved Tokens:** Emails and campaigns can't be sent while unfilled tokens remain in the message.
- **Template Dropdown:** Email templates are grouped by module in the template dropdown.
- **Linked Task Status:** Linking a task to an email now shows the task's completion status.
- **Sync:** Fixed email sync showing old emails.
- **Promotion Emails:** Fixed promotion emails opening with a blank body.
- **AI-Suggested Content:** Fixed a missing line break before your name in AI-suggested emails.

## Proposals

- **Create for Existing Lead:** Added a "Create for existing Lead" action.
- **Text Block and Heading:** Text Block and Heading elements now open in an editor.
- **Save Warning:** Missing elements (such as a signature or products) can be added straight from the save warning.
- **Prices:** Proposal prices and totals always show two decimal places (e.g. £2.30).
- **Resend Recipients:** Fixed resending a proposal showing the lead's name instead of the recipients.

## Invoices and Payments

- **GoCardless:** Connect GoCardless to collect payments by Direct Debit.
- **Direct Debit Statuses:** Clients' Direct Debit statuses sync with GoCardless.
- **Refunds:** Invoices can now be refunded.
- **Create from a Task:** Invoices can be created and linked from a task.
- **Auto-Create Invoices:** Added a toggle for creating invoices automatically.
- **Record Payment:** Record Payment now has a payment date, the provider and a reference.
- **Seller Details:** Invoices show your firm's own details as the seller.
- **Sorting:** Added sorting to the Invoices tables.
- **Summary Cards:** Fixed the amounts on the Outstanding and Overdue cards overlapping their icons.
- **Tax Rate and Item Dropdowns:** Tidied up the Tax Rate and item dropdowns and the Reference field.
- **Paid Invoice Preview Icon:** Fixed the preview icon being highlighted incorrectly on paid invoices.

## Calendar

- **Google Calendar Integration:** Two-way sync with Google Calendar. Task deadlines and events created or moved in Remindoo sync to Google Calendar.

## Dashboard

- **Current Work by Team:** Added a current work by team chart to the Tasks dashboard.
- **Total Hours:** Total Hours now shows the total for all employees.
- **History:** Fixed History not showing daily snapshots.

## Automations

- **Deadline Reminders:** Deadline reminders now cover existing and overdue tasks.
- **Delay Days:** Automation rules show their number of days in the rules list.
- **Visual Builder:** New steps now appear on the canvas, Zoom In stops at 100%, and Fit View re-centres the flow.

## Settings

- **Currency and Date/Time Formatting:** Choose how currency, dates and times are displayed.
- **Service Templates:** Added sorting on every column and Active/Inactive tabs, with a status option on each template.
- **Planned Reminders:** Added Select All to bulk actions in Planned Reminders.
- **Employee Deletion:** Employees assigned to tasks, subtasks or leads can't be deleted until their work is reassigned.
- **Roles:** The Admin and Employee role names are locked, with a tooltip explaining why.
- **Client Custom Fields:** A custom field set to visible in the Clients table now appears in Column Visibility.
- **Dialog Close Icon:** Every dialog in Settings now has a close icon.
- **Create Email Template:** The Save button stays on screen on smaller windows.
- **Consistent Names:** Fixed inconsistent names in Settings.

## Across the App

- **Assignee Search:** Assignee search now includes both employees and teams, with an improved look.
- **Delete Confirmations:** Clearer delete confirmation messages across the app.
- **Button Loading State:** Buttons show a loading state while an action is in progress.
- **Table Pagination:** Pagination buttons are hidden when there is only one page.

## Support and Feedback

- **Live Chat:** Chat live with the Remindoo team from inside the app.
- **Changelog Tab:** What's New is now a tab docked on the right edge of the app.
- **Public Changelog and Roadmap:** The changelog and roadmap are now available on remindoo.co.
- **Share an Idea:** Share ideas on remindoo.co with images, and vote on ideas from others.
- **Comments on Ideas:** Comment on and follow ideas, with a red dot marking new comments.
