# Email — Cross-Module Features

**Purpose:** Where email shows up in other modules.

| Where | How to get there | Tokens available (examples) |
| --- | --- | --- |
| **Tasks** | Task → View Subtasks → **Email Logs** or **Communication** → Send New Email | ::Task Name::, ::Description::, ::Task Status::, ::Task Progress Status::, ::Task External Deadline:: |
| **Leads** | Lead → **Send Lead Email** (or Create campaign) | ::Lead Name::, ::Lead Phone Number::, ::Company Number:: |
| **Invoices** | Invoice → Preview invoice → **Send reminder** | ::Invoice Number::, ::Invoice Amount::, ::Due Date::, ::Payment Link:: |
| **Task reminders** | Custom Task → **Create Reminder** | Task tokens |
| **Service reminders** | Settings → Services Templates & Reminders | See [Service Templates](../../Features/Service%20Templates.md) |

All of these windows have **Preview Email**. A task's **Email Logs** list every email sent from that task (subject, sent by, status, date and time).

**Status:** First draft (5 Nov 2026).

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
