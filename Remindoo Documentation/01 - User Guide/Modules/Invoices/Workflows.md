# Invoices — Workflows

**Purpose:** Step-by-step instructions for common things you do in **Invoices**.

## Raise an invoice from a task
1. Open the task and click **Raise Invoice**.
2. The invoice form opens with the task's client and service already filled in. If the task already has an invoice, you're warned before you make another.
3. Check the items, price, VAT and dates, then save. The price may not be filled in for you, so check it.
4. The invoice then shows on the task's **Invoices** tab (status, amount, due date). **Link invoice** on that tab attaches an invoice that already exists.

## Create an invoice from the Invoices page
Invoices → **New Invoice**, choose the currency (GBP, EUR or USD), then fill in the client, items and tax rate. *The fields on this form aren't documented one by one yet.*

## Preview an invoice
Click the **Preview invoice** icon on the row. The preview shows your firm's details as the seller, full dates, VAT for each line and the totals, next to the **Audit Timeline**, **Credit Notes** and **Payments**.

## Record a payment
1. Click **Record payment** on the invoice's row.
2. Enter the **amount**, pick the **date**, choose the **provider** (how it was paid) and add a **reference**.
3. Save. Recorded payments are listed under **Payments** in the invoice preview.

## Chase an invoice
1. Open **Preview invoice** → **Send reminder**.
2. Check the recipient, subject and body. Tokens such as ::Invoice Number::, ::Invoice Amount::, ::Due Date:: and ::Payment Link:: are filled in for you.
3. **Preview Email** to see the finished email, then **Send**.
4. Or use **Copy payment link** and send the link yourself.

Automatic reminders are sent on their own schedule (see **Reminders** at the top of the Invoices page), so check the invoice's **Audit Timeline** first to see what the client has already received.

## Sort and find invoices
Use the tabs (Unpaid, Overdue, Drafts…) to narrow the list and click a column header such as **Amount** to sort either way.

**Status:** First draft (12 Nov 2026). Credit notes, payment plans, voiding, recurring invoices and the accounting integrations aren't documented yet.

*Source: preprod QA run reports of 6–12 Nov 2026 (see `QA/Runs`), added 12 Nov 2026 without a fresh walk-through. The live app may lag preprod until the next release.*
