# Clients — Workflows

**Purpose:** Step-by-step instructions for common things you do in **Clients**.

## Find a client
1. Open **Clients** and type in the **Search** box. The table narrows to the matches and shows how many there are (e.g. "Showing 1 of 1").
2. Click a column header to sort (e.g. Name A→Z, then Z→A).
3. Click the client to open the quick view, then **Go To Client Profile** for the full record.

## Add a new client
1. Clients → **New Client**. *Welcome to Client Creation* opens.
2. Enter the **Client Name** and choose the **Type** (e.g. Self-Employed, Private Limited Company), then **Next**. For a company, **Import from Companies House** can fill the details in for you.
3. On the correspondence step, fill in how to reach the client: company name and number, address, nature of business, key dates, turnover, website, phone and email, plus any fields your firm has added. Fields marked * are compulsory (your firm sets these in **Settings → Client Custom Fields**). **Next** saves the step.
4. Work through the remaining steps, which include **Contacts**, **Services** and **Risk Assessment**.
5. You can stop part-way once a step has been saved. The client is kept under the **Draft** tab and you can resume it from there. Nothing is kept if you leave before saving the correspondence step.

*The steps after correspondence aren't documented field by field yet.*

## Add a service to a client
1. Open the client profile → **Services** → **Add Services**. *Manage Services For <client>* lists every service template.
2. Each service shows what it will create, e.g. "This service will create 2 subtasks and 2 preset reminders."
3. Click **Add** on the service you want. A service the client already has shows **Already Added**, or **Add Another** if it can be added again at a different frequency.
4. The service appears in the client's Services table with its frequency, and its tasks are created from the service template (see [Service Templates](../../Features/Service%20Templates.md)).

*What you're asked for after clicking Add (frequency, dates, assignees) isn't documented yet.*

## Export clients to CSV
1. Tick the clients you want in the table.
2. Click **Export selected clients to CSV** (it only appears once at least one client is ticked).
3. The file downloads and you'll see a confirmation such as "Exported 2 clients to CSV."

## Import clients
Clients → **Import Clients** opens the import window for a CSV file. *The import steps and the column format aren't documented yet.*

## See what a client owes
In the Clients table, click the amount in the **Invoices** column to open *Outstanding invoices – <client>*.

**Status:** First draft (12 Nov 2026), updated 13 Nov 2026 from a preprod walk-through. Companies House sync, AML verification and HMRC authorisation aren't documented yet.

*Source: preprod QA run reports of 6–12 Nov 2026 (see `QA/Runs`), added 12 Nov 2026 without a fresh walk-through. The live app may lag preprod until the next release.*
