# Invoices — Overview

**Purpose:** What the **Invoices** module is for and what you can do with it.

Invoices is where you raise, send and track invoices to clients, record payments, and sync with your accounting software.

## Sections (top of the page)
- **Invoices**: the main list.
- Accounting integrations: **Xero**, **QuickBooks**, **Sage** and **FreeAgent**.
- **Payments**, **Templates** and **Reminders** (automatic chasers).

## The invoice list
- Tabs: **All Invoices**, **Unpaid**, **Overdue**, **Drafts**, **Recurring**, **Credits & Notes**.
- Summary cards at the top: **Outstanding Invoices**, **Overdue Invoices**, **Invoice Drafts** and **Paid This Month**.
- **New Invoice** and a currency selector (e.g. GBP).
- Columns: Number, Client, Task, Proposal, Issue Date, Due Date, Created, Amount, Paid, Credit, Remaining, Status (Draft, Approved, Partial, Paid…), Sent, Plan, accounting sync status, Actions.
- Row actions: **Edit invoice**, **Preview invoice**, **Record payment**, **Payment plan**, **Issue credit note** and **Void invoice**.

- Click a column header (e.g. Amount) to sort. Clicking an invoice opens it for editing, with **Approve** and **Update & send**.
- The **Recurring** tab lists recurring invoice schedules (client, whether it's active, next run date).

## Payments, Templates and Reminders
- **Payments** (*Payment collection*): the providers clients can pay you through online, and **Record Payment**. Each provider shows what it accepts and its fee: **Stripe** (cards, Apple Pay, Google Pay), **PayPal**, **Adfin** (card, open banking, direct debit) and **GoCardless** (direct debit). **Connect** sets one up.
- **Templates**: branding themes for your invoices (colour, logo, bank details, notes). **New Branding Theme** adds one and **Mark as default** chooses the one used automatically. Themes from a connected Xero account are listed too, read only.
- **Reminders** (*Automated Invoice Reminders*): the emails Remindoo sends around the due date: **7, 3 and 1 days before**, **1, 3 and 7 days overdue**, and **Payment Refunded**. Each has its own subject and body, with tokens such as ::Invoice Number::, ::Invoice Amount::, ::Due Date::, ::Client Name:: and ::Payment Link::. **Reminder Dispatch Logs** underneath list every reminder sent, the invoice, and whether it was delivered. These are sent on top of any reminders from your accounting software.
- **Xero / QuickBooks / Sage / FreeAgent Integration**: connection status, what has synced, and contact and account mapping for each.

## Previewing and chasing an invoice
**Preview invoice** shows the invoice as the client sees it (your firm's details as seller, the client's billing details, items, VAT and totals), next to an **Audit Timeline** (created, reminders sent and so on), **Credit Notes** and **Payments**. From there you can:
- **Copy payment link**.
- **Send reminder**: opens *Send Email to Client* with invoice tokens (::Invoice Number::, ::Invoice Amount::, ::Due Date::, ::Payment Link::). **Preview Email** shows the finished email, including a **Pay Invoice** button for the payment link.

## Invoices elsewhere in the app
- **Tasks**: a task's **Invoices** tab, **Raise Invoice** on the task, and the **Due Amount** column.
- **Clients**: the **Invoices** column opens *Outstanding invoices* for that client (total due, overdue, list).

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), updated 13 Nov 2026 from a preprod walk-through.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
