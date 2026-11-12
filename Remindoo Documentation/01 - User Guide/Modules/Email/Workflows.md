# Email — Workflows

**Purpose:** Step-by-step instructions for common things you do with email in Remindoo.

## Connect your mailbox
Use **Connect Email** in any email window, or **Settings → Global Settings → Email Settings**, and sign in to your email provider. *The sign-in steps aren't documented yet.*

## Send a new email from the inbox
1. Open the inbox (**Emails** or **Inbox** in the menu) → **Compose**.
2. Add the recipient, subject and body. Check them carefully: Compose can open with the previous email's subject and recipient still filled in.
3. **Send**.
4. The email appears under **Sent**.

**Tokens aren't checked here.** If you type a token such as ::Client Name:: in Compose, it's sent exactly as written. To send an email with tokens filled in, send it from the task, lead or invoice instead and use **Preview Email** first.

## Email a lead from its record
1. Open the lead → **Go to Lead Profile** → **Conversation**.
2. Write your email in the composer and send. You'll see "Email sent successfully!".
3. The email shows in the lead's Conversation as a **Two way** thread. If it doesn't appear, reload the page.

Client, task and proposal Conversation tabs use the same composer.

## Preview an email before sending
In the email window on a task, lead or invoice, click **Preview Email**. Tokens are replaced with the record's real values. Any that can't be filled stay as written, so fix them before you send.

## Fetch new email
Click **Refresh** in the inbox. **Synced at** shows the time of the last fetch.

**Status:** First draft (12 Nov 2026).

*Source: preprod QA run reports of 6–12 Nov 2026 (see `QA/Runs`), added 12 Nov 2026 without a fresh walk-through. The live app may lag preprod until the next release.*
