# Tasks — Workflows

**Purpose:** Step-by-step instructions for common things you do in **Tasks**.

## Create a custom task
1. Tasks → **Custom Task**. The **Create Quick Task** form opens (switch to **Detailed Task** for more fields).
2. **Task name**: pick an existing name or type a new one and press Enter.
3. Set **Task Status**, **Priority**, and **Estimated Time** (hours and minutes).
4. Turn on **Is this task billable?** if you'll invoice it. Use **Make Recurring** for repeating work.
5. Set the **Internal Deadline** and **External Deadline**.
6. **Assignees**: click **+**, choose a team or employees, then **Save Assignees**.
7. Optionally add a description and tags.
8. **Create Reminder** (optional): set a reminder date, subject and message to remind yourself about the task. You can use tokens such as ::Task Name::.
9. **Create Task**.

## Filter the task list
1. Click the **funnel** icon → **Filter 1** → choose a field (e.g. Progress Status), a condition (is, is not, are) and a value.
2. **Add Condition** for more rules.
3. **Save & Apply Filter** → give it a name and **Save & Apply**, or **Apply Without Saving**.
4. The filter shows as a chip above the table. Click its **×** to remove it.

Filterable fields: Assignees, Billable, Client Name, Client Type, Completed At, Creation Date, Due Amount, External and Internal Deadline, Managers, Name, Partner, Priority, Progress, Progress Status, Service Name, Status, Tag.

## Change a task's status
Click the **Status** cell in the table and pick the new status. For the workflow step, use **Progress Status**.

## Send an email from a task (with preview)
1. Open the task → **View Subtasks** → **Email Logs** or **Communication** tab → **Send New Email**.
2. Recipients are filled in from the client. Pick an email template or write your own subject and body.
3. Use **Adjustable Tokens** (e.g. ::Task Name::, ::Task Status::, ::Description::) to pull in task details.
4. Click **Preview Email** to see the email exactly as it will be sent, with the tokens filled in. Tokens Remindoo can't fill stay as written.
5. Close the preview, edit if needed, then **Send**. You need a connected mailbox ("From:" at the top). If it says *No connected accounts*, use **Connect Email** first.

## See a task's invoices
Open the task → **Invoices** tab: what's due and what's paid for invoices linked to this task, with **Link invoice** and **View in Invoices**.

**Status:** First draft (5 Nov 2026).

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA. The live app may lag preprod until the next release.*
