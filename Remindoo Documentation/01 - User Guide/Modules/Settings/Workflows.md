# Settings — Workflows

**Purpose:** Step-by-step instructions for the common tasks users perform in the Settings module.

## Setting up a Service Template

Service Templates live in **Settings → Service Templates**. A Service Template is the reusable blueprint your firm builds once, so the services and tasks used on client profiles don't have to be created from scratch every time.

Also see the cross-module feature page: [Service Templates](../../Features/Service%20Templates.md) for how this connects to Clients and Tasks.

### Step 1 — Create the Service Template

- **Name** — anything you like.
- **Type** — `Internal` or `External`:
  - **External** is the normal case: it creates a service on a client's profile that automatically generates tasks (and, where relevant, emails) at the right time.
  - **Internal** is a simpler building block meant to be pulled into Custom Tasks, so your team doesn't have to manually recreate the same subtasks over and over.
- **Estimated time** — how long the task usually takes (hours & minutes).
- **Active** — whether the template is currently usable.

If you're creating an **External** template, you'll also set:

- **Frequencies** — tick every frequency this service can run on (`Daily`, `Weekly`, `Fortnightly`, `Monthly`, `Quarterly`, `Yearly`). You can select more than one — each becomes its own variant you configure separately.
- **Custom fields** — any extra fields you want captured for this service (`Text`, `Number`, `Date`, or `Dropdown`). You must include at least one `Date` field and mark one of them as the **Trigger Date** — the anchor date everything else in the template is calculated from.
- **Folder automation** — turn this on if you want a matching folder created automatically in the Document Sharing Portal whenever this service is added to a client.

Internal templates skip Frequencies, Custom Fields, Trigger Date, and Folder Automation entirely.

### Step 2 — Build the Task Template

Every Service Template has exactly one Task Template attached to it, controlling what the task created from this service will look like.

**Task details** (both Internal and External):

- **Name** — you can use placeholders like `::ClientName::`; the system fills in the real value when the task is created, if it's available.
- **Priority** — `High`, `Medium`, or `Low`.
- **Billable** — yes/no.
- **Tags** — any labels you want attached.
- **Description** — free text, multiple lines.

**Frequency settings** *(External templates only)* — for each frequency you selected in Step 1, configure when the resulting task is due:

- **Internal Deadline** — either:
  - Trigger Date + a number of days, or
  - Tied to a task status — leave it blank until someone changes the task's status to a status you pick (e.g. `Info Received`); the deadline is then set automatically to that date plus your offset.
- **External Deadline** — depending on the frequency, choose:
  - Same as the Internal Deadline (note: if you edit the Internal Deadline by hand later, that change does **not** carry over to the External Deadline)
  - Trigger Date + a set number of months/days
  - A fixed day of the month (using the Trigger Date's month/year)
  - A fixed month and day (using the Trigger Date's year)

  Not every option is available on every frequency — Daily/Weekly/Fortnightly only offer the first two, Monthly/Quarterly add the fixed-day option, and Yearly offers all four.

**Important:** a frequency you ticked in Step 1 can't be used on a client until you've saved its Frequency Settings here. If you select `Quarterly` but never configure its deadlines, you won't be able to create a Quarterly service on a client with this template.

### Step 3 — Add Subtask Templates (optional)

Subtasks let you break a task down into the significant milestones needed to complete it. For each subtask you set:

- **Title**
- **Estimated time** — hours & minutes
- **Steps** — the smallest, most basic steps that make up that subtask

### Step 4 — Add a Checklist Template (optional)

A checklist is a final sign-off list — something the person who did the work, their supervisor, and an executive can all use to review the completed work before it's considered done. You set:

- **Items** — each one is just a line of text
- **Estimated time** — hours & minutes for the whole checklist

### Step 5 — Add Reminder Templates (External templates only)

Reminders let you set up automated emails that go out to clients, assignees, service managers, and/or partners, timed around the Trigger Date you set in Step 1. Internal templates can't have Reminders.

Each **Reminder** is a container you configure with:

- **Title**
- **Document checklist** — turn this on if you want the reminder to be able to ask an external person to upload documents; whatever they upload lands automatically in a specific folder in the Document Sharing Portal.
- **Who it goes to** — either **Clients** (external) or **Employees** such as assignees/service managers/partners (internal) — you pick one per Reminder.
- The **Trigger Date** from your Service Template is used to work out when every email inside this Reminder gets sent.

Inside each Reminder, you can add one or more **Email Templates**, each with:

- A toggle for whether this email should actually be sent when the real emails get created for a client (see "chosen emails" in the [Glossary](../../../Glossary.md#chosen-eg-chosen-email-chosen-service))
- **Subject** and **Body**
- An **offset** — how many days before or after the Trigger Date this email goes out

**Status:** Settings-side of Service Templates fully documented (Service Template, Task Template, Subtask Templates, Checklist Templates, Reminder Templates); Clients and Tasks sides pending.
