# Production Deployment – Completed Features, Enhancements & Fixes

## Production Release Summary

**Release date:** Friday 13 November 2026

---

## Clients and Contacts

- **Search with One Match:** Fixed a search with a single result still offering a second page and leaving the row greyed out.
- **Services Skeleton Loader:** Fixed the Services table showing behind the skeleton loader in the client profile.
- **Bulk Export CSV:** Fixed Export selected clients to CSV downloading nothing.
- **Import and Export Icons:** Updated the Import and Export icons in the Clients module.
- **AML Proof of Address:** The Proof of Address warning section no longer opens automatically.
- **Client Name with Badges:** Fixed the client name being hidden in the list row when the New and LOC badges show.
- **AI Client Summary:** AI Summary in the client quick view generates a summary of the client.
- **Contact Area Code:** A contact's area code is now kept as entered (e.g. United Kingdom | +44).

## Client Onboarding

- **Wizard Heading:** Fixed the heading overlapping the "Import from Companies House" link, and Next now works on the first click.
- **Duplicate UTR:** A personal UTR that already belongs to another client is caught.

## Leads

- **Two-Way Email:** Two-way email in Leads.
- **Notes in Activity:** Notes can be added to the lead's Activity tab.
- **Activities Column:** Added an Activities column to the Leads list.
- **Filter Dialog:** Fixed the filter dialog overlay, and the Assignee filter now shows names instead of IDs.
- **Custom Field Type Selector:** Fixed the field type selector being squashed in the add-field modal.
- **Proposal Details:** Corrected Sent to, Total (incl. VAT), Created by and Sent by in the lead's proposal details.
- **Task Action Tooltips:** Added tooltips to the task action buttons on the lead detail screen.
- **Billable / Non-Billable:** Tasks on the lead detail screen now show whether they are billable or non-billable.

## Tasks

- **New Tasks Table:** The new Tasks table.
- **Task Status and Progress Status:** Added the task status and progress status fields.
- **Sorting:** Added sorting to the Tasks table, consistent with the Clients module.
- **Email Preview:** Task emails are logged in Email Logs, and tokens can be previewed before sending.
- **Service Badge:** The service name appears as a badge; clicking it opens a popover with the SATR, PTR, VAT and Accounts dates.
- **Row Badges:** Only the VAT and Recurring badges are shown next to the task name; the Accounts, SATR and PTR badges were removed from the row.
- **Outstanding Invoices Column:** Added an Outstanding Invoices column showing the task client's outstanding invoices, consistent with the Clients list.
- **Invoices Popover:** The invoices popover now shows all of the client's invoices, not only those tied to the task.
- **Assignees on Subtasks:** When updating a task's assignees, the same assignees can optionally be applied to all of its subtasks.
- **Activity Icons (Tasks and Leads):** Activity icons are grey when there is no activity and use their designated colour when activity exists.
- **E-Sign Icon:** The e-sign icon turns light green when all documents in that activity are signed.
- **E-Sign Resend:** Fixed the styling of Resend when it is enabled after selecting a document to resend.
- **Quick Task E-Signatures:** On a Quick Task with no client, the e-signature icon is disabled, with a tooltip explaining why.

## Conversations (Tasks, Leads and Clients)

- **Conversation Feature:** Added the conversation feature to Tasks, Leads and Clients.
- **Live Updates:** Comments, notes and sent emails appear in the timeline immediately, without refreshing the whole conversation.
- **Unread Indicator:** Unread two-way email threads are now marked so they are easy to spot.
- **Notes Validation:** Invalid or empty notes are blocked with clear feedback.
- **Notes Rendering:** Fixed TinyMCE parsing so note content renders correctly.
- **Email Label Tooltip:** Added a tooltip on the Submit button when adding a label to a two-way email, explaining what happens on submit.

## Email

- **Two-Way Email:** Two-way email as one shared component for Leads, Clients, Tasks and Proposals.
- **Preview Button:** Every email modal has a Preview button showing the email filled with the real client or lead data.
- **Tokens in Composer:** Added tokens to the email composer.
- **Token Replacement in Replies:** When a client, task or lead is attached to an email thread, tokens in replies are automatically replaced with their details.
- **Unresolved Tokens:** Sending an email or creating a campaign is blocked while unresolved merge tokens remain in the message (with override flows where supported).
- **Template Dropdown:** Email templates are grouped by module in the email template dropdown.
- **Linked Task Status:** Linking a task in the Email module now shows the task's completion status.
- **Sync:** Fixed email sync showing old emails.
- **Promotion Emails:** Fixed promotion emails opening with a blank body.
- **AI-Suggested Content:** The line break before [Your Name] is now preserved in AI-suggested email content.

## Proposals

- **Text Block and Heading:** Text Block and Heading elements now open an editor modal.
- **Create for Existing Lead:** Added a "Create for existing Lead" action.
- **Save Warning:** Missing elements (such as signature or products) can now be added straight from the save warning.
- **Prices:** Proposal prices and totals now always show two decimal places (e.g. £2.30).
- **Resend Recipients:** Fixed resending a proposal showing the lead's name instead of the recipients.

## Invoices and Payments

- **Create from a Task:** Invoices can be created and linked from a task.
- **GoCardless:** Added the GoCardless integration.
- **Direct Debit Statuses:** Clients' debit statuses now sync with GoCardless.
- **Refunds:** Added a refund feature for invoices.
- **Auto-Create Invoices:** A toggle for automatically creating invoices is now available.
- **Seller Details:** Invoices now show the firm's own seller details instead of placeholder details.
- **Record Payment:** Record Payment now has a payment date picker, the provider and a reference.
- **Sorting:** Added sorting to the Invoices tables.
- **Paid Invoice Preview Icon:** Fixed the preview icon being highlighted incorrectly on paid invoices.
- **Reference Field:** Fixed the Reference field's text size.
- **Tax Rate and Item Dropdowns:** Fixed the Tax Rate dropdown UI, the item dropdown cursor and the Reference field label.
- **Summary Cards:** Fixed the amounts on the Outstanding and Overdue cards overlapping their icons.

## Calendar

- **Google Calendar Integration:** Two-way sync with Google Calendar. Task deadlines and events created or moved in Remindoo sync to Google Calendar.

## Dashboard

- **Current Work by Team:** Added the current work by team chart to the Tasks dashboard.
- **Total Hours:** Total Hours now shows the total for all employees.
- **History Snapshots:** Fixed History having no daily snapshots.

## Automations

- **Deadline Reminders:** Deadline reminders now cover existing and overdue tasks.
- **Visual Builder:** New steps now appear on the canvas, Zoom In stops at 100%, and Fit View re-centres the flow.
- **Delay Days:** Automation rules now show their number of days in the rules list.

## Settings

- **Currency and Date/Time Formatting:** Added currency and date/time formatting settings.
- **Service Templates:** Added sorting on every column and Active/Inactive tabs, with a status option on each template.
- **Planned Reminders:** Added Select All to bulk actions in Planned Reminders.
- **Roles:** The Admin and Employee role names are locked, with a tooltip saying they can't be edited.
- **Employee Deletion:** Employees assigned to tasks, subtasks or leads cannot be deleted until their work is reassigned to someone else.
- **Client Custom Fields:** A custom field set to visible in the Clients table now appears in Column Visibility.
- **Dialog Close Icon:** Added a close (cross) icon to every dialog box in Settings.
- **Create Email Template:** The Save button now stays on screen on smaller windows.
- **Consistent Names:** Fixed inconsistent names in Settings (Knowledge Base, "1 Member").

## App-wide

- **Changelog Tab:** Replaced the What's New button with a tab docked on the right edge.
- **Assignee Component:** Assignee search now includes both employees and teams, and the component's UI has been improved.
- **Delete Confirmations:** Updated the delete confirmation messages across the application.
- **Button Loading State:** Buttons now show a loading state.
- **Table Pagination:** Pagination buttons are now hidden instead of disabled when there is only one page.

## Super Admin

- **Login and Users:** Added a separate login with separate accounts, invite-by-email, two-step sign-in codes (MFA), roles and permissions, and an audit log. The Users and Roles screens now update live.
- **Live Chat:** Added live chat between Remindoo users and the team, with a new Conversations inbox that has notes, resolve and reopen, delete, an Unread filter and alert emails.
- **Product Updates:** Added What's new popups for chosen firms, Kanban boards with renamable columns, Slack alerts for new feedback, and table improvements.
- **Conversations:** Unread chats are bold and can be filtered, and a user's chats about different feedback are told apart.
- **Firm-side Chat:** Adding a screenshot no longer freezes the page, and long messages no longer overlap their label.
- **Sidebar:** "Tickets" now opens Tickets, and Conversations can be reached from the sidebar.
- **Account Setup:** Added password strength rules, and Skip for Now now shows a pointer cursor.
- **Roles & Permissions:** A role without Settings access no longer sees an empty Settings menu, and Reload has a tooltip.
- **Manage Users:** Changing an action no longer disables Delete and Send reset password, and the oldest Super Admin can't be deleted.
- **Disabled Users:** Disabled users no longer count toward their role, and re-enabling a user asks for a role.
- **Impersonate:** The buttons in the confirm popup are now centred.
- **Feedback List:** Fixed the status sort and the date format, and added a Created at column.
- **Roadmap:** The table cells are now centre-aligned.

## Public Website (Changelog, Roadmap and Feedback)

- **Public API:** Added the APIs that connect the changelog, roadmap and feedback to a public view, plus Lovable prompts for the pages.
- **Public Feedback:** Added consent, public ideas, voting and Slack alerts for feedback on remindoo.co.
- **Share an Idea:** Added Share an idea with image uploads, and a Share menu.
- **Comments on Public Ideas:** Customers and visitors can comment and Follow an idea, a red dot marks new comments, and comments are moderated in Super Admin.
- **Comment Posting:** Comments now appear as soon as they're posted, the text locks while posting, and Super Admin sees the avatar and time.
