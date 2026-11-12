# Automations — Overview

**Purpose:** What the **Automations** module is for, who uses it, and what you can accomplish with it as a Remindoo user. High-level orientation before diving into workflows.

Automations are rules that do something for you when a record changes, such as emailing someone when a task is completed or moving a task to another status after a set time. They're set up in **Settings → Automations** and can act on leads, proposals, tasks, clients and services.

## The Automations page
- Rules are listed by module (e.g. a list for Leads and a list for Tasks).
- Each rule has an **Active** switch on its row, so you can pause a rule without removing it.
- **See how this rule runs** shows a diagram explaining what the rule does. It isn't a history of when the rule ran.

## The rule builder
Opening a rule shows it as a flow on a canvas: the trigger first, then each step in order. For example:
- *Task status becomes Complete → Send Email* (using one of your email templates), or
- *Task status becomes Complete → wait 1 day → set status to Not started*.

New steps are added to the end of the flow. Zoom buttons let you move around a larger rule.

## What a rule can do
- **Send Email**: to your own team, or to the lead or client the record belongs to ("Email leads" / "Email clients").
- **Change a status** after a delay.

## Built-in safeguards
- A rule that would move tasks **backwards** (for example reopening completed tasks) asks you to confirm before it can be switched on.
- Rules that email clients or leads send real emails as soon as they're active, so check the template and recipients before switching one on.

**Status:** First draft (12 Nov 2026). The full list of triggers and actions, and building a rule step by step ([Workflows](Workflows.md)), aren't documented yet.

*Source: preprod QA run reports of 6–12 Nov 2026 (see `QA/Runs`), added 12 Nov 2026 without a fresh walk-through. The live app may lag preprod until the next release.*
