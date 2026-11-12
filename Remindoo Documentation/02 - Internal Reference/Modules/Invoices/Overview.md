# Invoices — Overview (internal)

**Purpose:** Functional notes on **Invoices** for the team.

- Integrations tabs: Xero, QuickBooks, Sage, FreeAgent. Side links: Payments, Templates, Reminders.
- List tabs: All Invoices, Unpaid, Overdue, Drafts, Recurring, Credits & Notes. The list loads slowly on preprod (about 10–15 s for 81 invoices).
- Columns: Number, Client, Task, Proposal, Issue Date, Due Date, Created, Amount, Paid, Credit, Remaining, Status, Sent, Plan, FreeAgent (sync: Synced / Not Synced), Actions.
- Row actions (aria labels): Edit invoice, Preview invoice, Record payment, Payment plan, Issue credit note, Void invoice.
- Preview: seller block uses the tenant's details (tenant name, address, email, company reg. no.); Audit Timeline (Invoice Created "from task …", Reminder Sent "by System cron engine"); Credit Notes and Payments tabs; "Remindoo" / "View as in FreeAgent" toggle; Copy payment link; **Send reminder** → "Send Email to Client" with invoice tokens and Preview Email ("Invoice, client, and tenant tokens are merged").
- **Data issue seen 5 Nov:** status and paid amounts disagree (a Sage-synced invoice "Paid" with £233 remaining; INV-136, SI-7 and SI-9 "Partial" with £0 paid). Proposed card for Aftab.
- Automatic reminders go out on their own (the INV-055 timeline shows "Reminder Sent … Email reminder sent for scenario: 3 days before").

## Changes seen 6–12 Nov 2026
- **Payments** tab: Stripe connected in Tenant 1; PayPal and GoCardless show Connect (their cards, SCRUM-800 and SCRUM-911, are Not Pushed).
- **Reminders** → Invoice Reminders: token list per template, a "Payment Refunded" template, and a dispatch log (e.g. INV-055 "Delivered successfully" on 7, 8 and 9 Nov). Preprod does send these emails to invoice contacts.
- **Record Payment:** amount, date picker, provider, reference (SCRUM-1162).
- **Recurring:** 2 schedules for client Test 2 (one Active, next run 24 Nov). The tab shows an empty state briefly before loading.
- Row actions on a synced invoice: Link client, Sync, Preview, Issue credit note. Clicking an Approved invoice opens the full Edit Invoice form with Approve / Update & send. Approve & Send syncs to FreeAgent and emails the client.
- Preview: seller details from the tenant (SCRUM-1137), full dates and VAT per line; no bank details for bank transfer (SCRUM-1161).
- Raise Invoice from a task prefills client and service and warns about an existing invoice; the price field was empty (SCRUM-807).
- Currency picker: GBP, EUR, USD.
- Paid/Partial invoices showing £0 paid is carded as SCRUM-1508.

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA runs.
