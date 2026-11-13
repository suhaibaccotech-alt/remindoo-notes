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
**Go To Client Profile** opens the full record ("Preview of <client>"), in sections:

| Section | What's in it |
| --- | --- |
| **Basic Information** | Client name, status, type, company name and number, trading name, email, phone, address, key dates (incorporation, commenced, LOE signed, SA register), UTR, National Insurance number, website and notes. **Basic Fields / Additional Fields** switch between the standard fields and your firm's custom ones; **Edit All** makes them editable. |
| **Contacts** | The people at the client. Each contact has a name, type, address, designation, National Insurance number, UTR, date of birth, emails, mobile numbers, Form 64-8 status, nationality and identity-verification details. **Add new contact** adds another. |
| **Services** | The services you provide, with pending tasks, frequency, assignees, tax liabilities, client authorisation, reminders and time estimate for each, and the total yearly time. **Add Services** opens *Manage Services*; **Pause** stops a service; **Company House Sync** refreshes company data. |
| **Internal Information** | Yearly fee, payment type, where the client came from, previous accountant, **View Related Clients** and **Send Letter of Clearance**. |
| **Risk Assessment & AML** | The AML risk questions (the answers give a risk level such as *Low Risk*) and **Digital AML Verification**. |
| **Client Portal Management** | Who at the client can sign in to the client portal: **Invite Contact**, **Create Client User Manually**, and whether each person has been invited or granted access. |
| **E-Signatures** | Documents sent to the client to sign, grouped by task, with **Upload Document**. |
| **Conversation** | Two-way emails and the client's activity (edits, services added, documents sent and signed) in one feed, with **Email** and **Activity** filters. |

In **Services**, each frequency of a service is its own row, so a client can have *VAT (Monthly)* and *VAT (Quarterly)* side by side.

## Outstanding invoices
Click the amount in the **Invoices** column to see *Outstanding invoices – <client>*: Total Due, Overdue, the number of invoices, and each invoice with its issue and due dates, amount and status.

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), updated 13 Nov 2026 from a preprod walk-through.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
