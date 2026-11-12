# Invoices — Overview

**Purpose:** What the **Invoices** module is for and what you can do with it.

Invoices is where you raise, send and track invoices to clients, record payments, and sync with your accounting software.

## Sections (top of the page)
- **Invoices**: the main list.
- Accounting integrations: **Xero**, **QuickBooks**, **Sage** and **FreeAgent**.
- **Payments**, **Templates** and **Reminders** (automatic chasers).

## The invoice list
- Tabs: **All Invoices**, **Unpaid**, **Overdue**, **Drafts**, **Recurring**, **Credits & Notes**.
- Summary cards at the top (e.g. total outstanding).
- **New Invoice** and a currency selector (e.g. GBP).
- Columns: Number, Client, Task, Proposal, Issue Date, Due Date, Created, Amount, Paid, Credit, Remaining, Status (Draft, Approved, Partial, Paid…), Sent, Plan, accounting sync status, Actions.
- Row actions: **Edit invoice**, **Preview invoice**, **Record payment**, **Payment plan**, **Issue credit note** and **Void invoice**.

- Click a column header (e.g. Amount) to sort. Clicking an invoice opens it for editing, with **Approve** and **Update & send**.
- The **Recurring** tab lists recurring invoice schedules (client, whether it's active, next run date).

## Payments, Templates and Reminders
- **Payments**: the payment providers your firm takes payments through (e.g. Stripe).
- **Reminders**: the automatic emails Remindoo sends about invoices, such as a chaser *3 days before* the due date. Each reminder template shows the tokens it can use, and a log lists every reminder sent, to whom, and whether it was delivered.

## Previewing and chasing an invoice
**Preview invoice** shows the invoice as the client sees it (your firm's details as seller, the client's billing details, items, VAT and totals), next to an **Audit Timeline** (created, reminders sent and so on), **Credit Notes** and **Payments**. From there you can:
- **Copy payment link**.
- **Send reminder**: opens *Send Email to Client* with invoice tokens (::Invoice Number::, ::Invoice Amount::, ::Due Date::, ::Payment Link::). **Preview Email** shows the finished email, including a **Pay Invoice** button for the payment link.

## Invoices elsewhere in the app
- **Tasks**: a task's **Invoices** tab, **Raise Invoice** on the task, and the **Due Amount** column.
- **Clients**: the **Invoices** column opens *Outstanding invoices* for that client (total due, overdue, list).

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA reports.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
