# Tasks — Overview

**Purpose:** What the **Tasks** module is for, who uses it, and what you can do with it.

Tasks is where all client work lives. A task is created either **automatically** from a client's service (see [Service Templates](../../Features/Service%20Templates.md)) or **by hand** as a **Custom Task**. Everyone in the firm uses it: staff to see and progress their work, managers and partners to see what's stuck.

## The Tasks page
- **Status tabs** at the top: All, Not started, In-Progress, Awaiting Feedback, Complete, Archived, Snooze, each with a count. *All* shows open work (it doesn't include Complete, Archived or Snoozed tasks).
- **Custom Task** and **Recurring Tasks** buttons, **Show Kanban View**, column visibility, filters and saved filters.
- The table has 21 columns you can show or hide, grouped as:
  - *Task information*: Name, Priority, Type, Services, Tag
  - *Assignment*: Assignees, Partner, Managers, Client Name
  - *Billing & classification*: External Deadline, Internal Deadline, Billable, Due Amount
  - *Progress tracking*: Status, Progress Status, Progress Time & Variance, Completed At, Timer
  - *Scheduling*: Creation Date
  - *Actions*: Timeline, Comments
- Two more columns, **Status Change** and **Progress Status Change**, show when each was last changed. Most columns can be sorted by clicking the header.
- **Recurring Tasks** lists your repeating-task rules with the date each one next refreshes (**Refresh at**).
- **Activity & Actions** column: one tile each for Email Logs, Checklist / Records, e-Signatures, Call Logs, Mentions, Comments and Invoices. The date under a tile is the last time that kind of activity happened. Clicking a tile opens it.
- Colour key at the bottom: needs action now, waiting on client, mention for you, overdue invoices.

## Status vs Progress Status
- **Status** is the simple state of the task: Not started, In-Progress, Awaiting Feedback, Complete, Archived. You can change it straight from the table by clicking it.
- **Progress Status** is the step the job has reached in your firm's workflow, e.g. *Info Requested*, *Filed Externally*, *Accounts Approved But Invoice Pending*, *Hold CT600 – Invoice Pending*. The steps come from your service templates.

## Two deadlines
- **Internal Deadline**: when your team should finish.
- **External Deadline**: the real deadline (e.g. HMRC or Companies House).

## Opening a task
Clicking a task opens a summary card (service, client, type, priority, dates, status) with tabs for **Task**, **Comments**, **Email Logs** and **Invoices**, plus action buttons: View Subtasks, Edit Task, Raise Invoice, Reassign Task, Archive Task, Snooze Task, Add Subtask, AI Task Analysis, View Timeline and Delete This Task.

**View Subtasks** opens the task workspace with tabs for **Subtasks**, **Comments**, **Checklist**, **Timeline**, **Email Logs** and **Communication**, a timer, and the internal and external deadlines.

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA reports.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
