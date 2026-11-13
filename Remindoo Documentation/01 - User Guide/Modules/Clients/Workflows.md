# Clients — Workflows

**Purpose:** Step-by-step instructions for common things you do in **Clients**.

## Find a client
1. Open **Clients** and type in the **Search** box. The table narrows to the matches and shows how many there are (e.g. "Showing 1 of 1").
2. Click a column header to sort (e.g. Name A→Z, then Z→A).
3. Click the client to open the quick view, then **Go To Client Profile** for the full record.

## Add a new client
The set-up wizard has five parts: **Introduction**, **Contacts**, **Services**, **Risk Assessment & AML** and **Internal Information**.

1. Clients → **New Client**. *Welcome to Client Creation* opens.
2. **Introduction**: enter the **Client Name** and choose the **Type** (e.g. Self-Employed, Private Limited Company), then **Next**. For a company, **Import from Companies House** can fill the details in. On the next screen, fill in how to reach the client: company name and number, address, key dates, phone and email, plus any fields your firm has added. Fields marked * are compulsory (set in **Settings → Client Custom Fields**). **Next** saves it.
3. **Contacts**: add the people at the client with the contact manager, or pick an existing contact.
4. **Services**: click **Add Services** and add each service you'll provide (see *Add a service to a client* below). **Next** when you're done; you can add services later.
5. **Risk Assessment & AML**: answer the 16 questions **Yes** or **No**, one at a time. A summary then shows every answer and the resulting **AML Risk Assessment** (e.g. *Low Risk*); you can change an answer there. **Save & Continue**. **Digital AML** starts an online identity check instead.
6. **Internal Information**: optionally add the **Previous Accountant**, then the **Client Source** (Type: Existing Client, Facebook, Google or Website, and your relation to it). **Next**, then choose the **Payment** type (e.g. DD – GoCardless, SO – By Client, Payment on Invoice), **Google Review** and the **Yearly Fee – Ex VAT**.
7. **Finish**. You'll see "Client finalised successfully" and the client moves from **Draft** to **Active**.

**Stopping part-way:** once the Introduction has been saved, the client is kept under the **Draft** tab. Click it and choose **Complete your onboarding**. A window shows each part as *Complete* or *Incomplete* and suggests the next one; **Continue onboarding** takes you there, or **Start from beginning** reviews every step with what you've saved filled in.

A lead you convert to a client arrives the same way, as a Draft with the Introduction complete.

## Add a service to a client
1. In the wizard's Services step, or on the client profile → **Services**, click **Add Services**. *Manage Services For <client>* lists every service template.
2. Each service shows what it will create, e.g. "This service will create 1 subtasks and 2 preset reminders." A service that doesn't apply to this type of client shows **Not Allowed**. One the client already has shows **Already Added**, or **Add Another** if it can be added again at a different frequency.
3. Click **Add**. *Choose Frequency And Estimated Time Of This Service* opens:
   - **Frequency** (the ones the service template allows) and the **Estimated Time** in hours and minutes (at least 1 minute).
   - **Additional Info**: the service's own fields, such as dates and reference numbers. The date marked * is the one the task's deadlines and reminders are worked out from.
   - A line tells you how many tasks will be created for your choices.
4. **Next**, then choose who does the work in **Assign Team Members**: pick teams or employees as **Partner**, **Service Manager** and **Assignee**, and **Save Assignees**. At least one person is needed.
5. The service appears in the client's Services table with its frequency, and its tasks are created from the service template (see [Service Templates](../../Features/Service%20Templates.md)).

## Export clients to CSV
1. Tick the clients you want in the table.
2. Click **Export selected clients to CSV** (it only appears once at least one client is ticked).
3. The file downloads and you'll see a confirmation such as "Exported 2 clients to CSV."

## Import clients
Clients → **Import Clients** opens the import window for a CSV file. *The import steps and the column format aren't documented yet.*

## See what a client owes
In the Clients table, click the amount in the **Invoices** column to open *Outstanding invoices – <client>*.

**Status:** First draft (12 Nov 2026), wizard and services walked through 13 Nov 2026. Saving a service's assignees, Companies House sync, AML verification and HMRC authorisation aren't documented yet.

*Source: walked through on preprod (preprod-crm.remindoo.co) on 13 Nov 2026, as Test User in the test tenant, creating a test lead and converting it to a client. The live app may lag preprod until the next release.*
