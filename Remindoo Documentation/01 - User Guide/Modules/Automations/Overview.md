# Automations — Overview

**Purpose:** What the **Automations** module is for, who uses it, and what you can accomplish with it as a Remindoo user. High-level orientation before diving into workflows.

Automations are rules that do something for you when a record reaches a status, such as emailing someone when a task is completed or moving a client to another status. They're set up in **Settings → Automations** (*Automations Rules*).

## One list per module
Tabs across the top, each with its number of rules: **Leads**, **Proposals**, **Tasks**, **Clients** and **Services**.

| Tab | A rule runs when… |
| --- | --- |
| Leads | a lead enters a status (e.g. *New Lead*) |
| Proposals | a proposal enters a status |
| Tasks → **Status** | a task enters a status |
| Tasks → **Deadlines** | a set time before or after a task's internal or external deadline |
| Clients | a client enters a status (e.g. *Archive*, *Frozen*) |
| Services | the subtasks of a chosen service's task enter a status |

## How a rule reads
Each rule is one row: **status or condition → After (how long to wait) → Then do (the action) → Email template or details → Send / assign to → Active**. For example: *New Lead → Immediately → Send Email → "Welcome" template*, or *Archive → Immediately → Change Status → Frozen*.

## Rules to know
- A status rule runs when a record **enters** the status, not for records already sitting in it. It runs once per entry, and only if the record is still in that status when the wait is up.
- Deadline rules send once per deadline. Complete, archived and snoozed tasks are never reminded. Day-based reminders go out at 09:00 UTC.
- Each rule has an **Active** switch. The counts under the table show total, active and paused rules.
- If a rule's email template is deleted, the rule shows "Deleted template — choose another" until you pick a new one.
- Rules that email leads or clients send real emails as soon as they're active, so check the template and recipients first.
- A rule that would move tasks backwards (for example reopening completed tasks) asks you to confirm before it can be switched on.

See [Workflows](Workflows.md) for adding a rule.

**Status:** First draft (12 Nov 2026), rewritten 13 Nov 2026 from a preprod walk-through. The full list of actions isn't documented yet.

*Source: walked through on preprod (preprod-crm.remindoo.co) on 13 Nov 2026, signed in as Michael Eldred Clark. The live app may lag preprod until the next release.*
