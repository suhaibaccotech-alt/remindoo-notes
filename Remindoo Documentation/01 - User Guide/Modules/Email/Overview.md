# Email — Overview

**Purpose:** What the **Emails** module is for and how email works across Remindoo.

**Emails** (left menu) shows your connected mailbox inside Remindoo, so client emails can be read, assigned and linked to clients and tasks. You need to connect a mailbox first (**Connect Email** in any email window, or **Settings → Integrations → Connect Email**).

## The inbox
The page is called **Inbox** in the menu and has an **Email / WhatsApp** switch at the top (see [WhatsApp](../WhatsApp/Overview.md)). Once a mailbox is connected:
- **Folders**: Inbox, Unread, Starred, Archived, Complete, Sent, Spam and Trash.
- **Categories** across the top: All, Primary, Promotions, Social and Updates, with unread counts.
- **Synced at** shows when Remindoo last fetched your email. Click **Refresh** to fetch again; don't rely on it updating by itself.
- **Compose** writes a new email.

**On each email** you can: comment, set as favourite, mark unread, **set as completed**, archive or move to trash, **Add assignee** (give it to a colleague), **Link Task**, **Link Client**, or **Create Lead** from the sender.

**Replying**: the reply box under the email has **Select Email Template**, formatting, **Reply** and **Reply All**. **AI Suggestion** drafts a reply for you; it needs an AI provider connected in **Settings → Integrations**, otherwise you'll see "AI Provider not configured or not active for this tenant".

Without a connected mailbox the page has nothing to show.

## Sending email from anywhere in Remindoo
Every place you can write an email (Tasks, Leads, Invoices and more) uses the same window:
- **From**: your connected mailbox.
- **Select Email Template**, **Recipients**, **Subject**, **BCC** and **Body** (with formatting), plus **Attach files**.
- **Adjustable Tokens** on the right: placeholders like ::Lead Name:: or ::Invoice Number:: that Remindoo fills in for each recipient.
- **Preview Email**: shows the email exactly as it will go out, with the tokens filled in from the real record. Tokens it can't fill stay as written, so you can catch them before sending.
- Tip: don't add your logo or signature in the body; Remindoo adds them.

See [Cross-Module Features](Cross-Module%20Features.md) for where email appears in other modules.

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), inbox updated 13 Nov 2026 from a preprod walk-through.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
