# Clients — Overview

**Purpose:** What the **Clients** module is for and what you can do with it.

Clients holds every client record: who they are, the services you provide, contacts, compliance (AML, HMRC authorisation) and the key dates for each service.

## The Clients page
- Summary chips: total fee, total hours, spent hours and available hours.
- Tabs: **Active**, **Archive**, **Frozen**, **Draft** (clients part-way through onboarding).
- Toolbar: **New Client**, **Import Clients**, **Company House Sync**, **AML Verification Sessions**, **Check HMRC authorisation requests**, column visibility, filters and saved filters.
- Columns include Name, Assignees, Service Managers, Email, Related Clients, AML Risk Level, AML Digital Verification, **HMRC Authorisation**, Type, UTR, Status Changed At, **Invoices** (outstanding amount and count), and a column for every service custom field (e.g. VAT Number, Next VAT to be filed, CT600 Filing Deadline, PAYE Reference Number).

## Client quick view
Clicking a client shows its services (with frequency, e.g. *VAT (Monthly)*), status, AML digital verification, UTR, website, notes, contact info, email and document folder, with actions:
**Go To Client Profile**, **Document Folder**, **Manage Tasks**, **Add Custom Task**, **Create New Proposal**, **Go To CH** (Companies House), **AI Summary**, **Dial Call**, **Mark Client Archive** and **Delete Client Profile**.

## The client profile
**Go To Client Profile** opens the full record, in sections: **Basic Information**, **Contacts**, **Services**, **Internal Information**, **Risk & AML**, **Client Portal Management**, **E-Signatures** and **Conversation** (notes, emails and WhatsApp messages for this client).

In **Services**, each frequency of a service is its own row, so a client can have *VAT (Monthly)* and *VAT (Quarterly)* side by side.

## Outstanding invoices
Click the amount in the **Invoices** column to see *Outstanding invoices – <client>*: Total Due, Overdue, the number of invoices, and each invoice with its issue and due dates, amount and status.

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA reports.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
