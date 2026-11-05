# Invoices — Overview (internal)

**Purpose:** Functional notes on **Invoices** for the team.

- Integrations tabs: Xero, QuickBooks, Sage, FreeAgent. Side links: Payments, Templates, Reminders.
- List tabs: All Invoices, Unpaid, Overdue, Drafts, Recurring, Credits & Notes. The list loads slowly on preprod (about 10–15 s for 81 invoices).
- Columns: Number, Client, Task, Proposal, Issue Date, Due Date, Created, Amount, Paid, Credit, Remaining, Status, Sent, Plan, FreeAgent (sync: Synced / Not Synced), Actions.
- Row actions (aria labels): Edit invoice, Preview invoice, Record payment, Payment plan, Issue credit note, Void invoice.
- Preview: seller block uses the tenant's details (tenant name, address, email, company reg. no.); Audit Timeline (Invoice Created "from task …", Reminder Sent "by System cron engine"); Credit Notes and Payments tabs; "Remindoo" / "View as in FreeAgent" toggle; Copy payment link; **Send reminder** → "Send Email to Client" with invoice tokens and Preview Email ("Invoice, client, and tenant tokens are merged").
- **Data issue seen 5 Nov:** status and paid amounts disagree (a Sage-synced invoice "Paid" with £233 remaining; INV-136, SI-7 and SI-9 "Partial" with £0 paid). Proposed card for Aftab.
- Automatic reminders go out on their own (the INV-055 timeline shows "Reminder Sent … Email reminder sent for scenario: 3 days before").

**Status:** First draft (5 Nov 2026).
