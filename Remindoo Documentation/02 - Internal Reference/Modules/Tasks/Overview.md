# Tasks — Overview (internal)

**Purpose:** Functional overview of **Tasks** for the team: behaviour, rules and where things are.

## Table
- 21 columns in **Column visibility** (freeze up to 5), grouped as Task information, Assignment Details, Billing & Classification, Progress Tracking, Scheduling and Actions. "Activity & Actions" is always shown at the end.
- Status counts (5 Nov, test tenant): All 97 = Not started + In-Progress + Awaiting Feedback. **All excludes Complete, Archived and Snooze**. Noted 4 Nov, still true. On 4 Nov All was 164.
- Filter fields: Assignees, Billable, Client Name, Client Type, Completed At, Creation Date, Due Amount, External Deadline, Internal Deadline, Managers, Name, Partner, Priority, Progress, Progress Status, Service Name, Status, Tag. Conditions: are, is, is not. Filters can be saved as named views (Save Filter View) or applied without saving. Applying one takes about 4 s on preprod.
- **Status** is editable inline (Archived, Awaiting Feedback, Complete, In-Progress, Not started).
- **Progress, Time & Variance**: logged against estimate, rounded to 2 decimals (e.g. "0.01h of 1h, +0.99 hr"). The unrounded "0.009h" is fixed (Zain, 3 Nov). The display is missing a space ("0hof 1h").
- **Due Amount**: only invoices linked to that task. SCRUM-901 expects the client's outstanding balance (failed QA 5 Nov).
- **Activity & Actions** tiles (aria labels): Email Logs, Checklist / Records (popover "Requested documents x of y received"), e-Signatures, Call Logs, Mentions, Comments, Invoices. The date under a tile is the latest activity of that type.
- Partner and Managers columns have header filters (Zain, 3 Nov). No test task has values.

- **Status Change** and **Progress Status Change** columns, with sort, visibility and filters (SCRUM-900). Status Change reads "Not updated yet" on every task. 13 columns are sortable; name sort ignores spaces and punctuation (SCRUM-874, SCRUM-1349).
- Kanban loads 20 cards per column (`/api/task-table-1/kanban?perColumn=20`) and fetches the next 20 for a column on scroll.
- On the All view the Complete and Archived chips show 0 (SCRUM-1171). Recurring rules show a "Refresh at" date; they aren't refreshing (SCRUM-1113).
- Action buttons are coloured by activity: pink needs action, orange waiting on client, purple mention, red overdue invoices, with a legend on the pagination bar (SCRUM-1287 unclear).

## Task modal and workspace
- Modal tabs: Task, Comments, Email Logs, Invoices (Due, Paid, invoice list, Link invoice, View in Invoices).
- Modal actions: View Subtasks, Edit Task, Raise Invoice, Reassign Task, Archive Task, Snooze Task, Add Subtask, AI Task Analysis, View Timeline, Delete This Task. **No latest-action dates under them, and no Next Step or Next Page** (SCRUM-1285 failed QA 5 Nov).
- Workspace (View Subtasks): Subtasks (steps with timers, "Ready To Start", due date), Comments, Checklist, Timeline, Email Logs, Communication. Header shows "Deadline exceeded by N days", a timer, and the internal and external deadlines.
- Email Logs and Communication both have **Send New Email** → "Send Email to 1 task" (recipients from client contacts, Adjustable Tokens, Preview Email). The preview note says "Tokens are replaced with task data. Unresolved tokens stay as written." An empty token value renders blank. (SCRUM-1283, SCRUM-1366: passed QA 5 Nov.)

## Custom tasks
- Create Quick Task / Detailed Task. Required: name (select or create), estimated time, internal and external deadlines, assignees (teams or employees). Billable toggle, Make Recurring, description, tags.
- **Create Reminder** → "Customise Your Reminder" (date, subject, body, tokens): an email reminder to the user (SCRUM-1370: not verified, blocked in QA).

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026, from QA on preprod.
