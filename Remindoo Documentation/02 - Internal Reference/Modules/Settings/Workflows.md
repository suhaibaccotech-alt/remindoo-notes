# Settings — Workflows

**Purpose:** Internal walkthrough of the Settings module's business logic and workflows: how data flows through the system, state transitions, validations, and edge cases.

## Service Templates

Also see the cross-module feature page: [Service Templates](../../Features/Service%20Templates.md).

### What a Service Template represents

A Service Template is the reusable blueprint ("cast") that forms the basis for actual services and tasks created on client profiles, under varying circumstances.

### Creating a Service Template

Fields on the Service Template itself:

- **Name** — alphanumeric.
- **Type** — `Internal` or `External`:
  - **Internal** — templates meant to be imported into Custom Tasks, to prevent manual work recreating duplicate subtasks. Internal templates have **no** custom fields, **no** trigger date, **no** frequencies, and **no** folder automation.
  - **External** — templates meant to create services on client profiles that automatically create tasks and dynamic emails at the appropriate time. External templates have the full field set below.
- **Estimated time to completion** — hours and minutes.
- **Active** — boolean.
- **Frequencies** *(External only)* — multi-select from a predefined list: `Daily`, `Weekly`, `Fortnightly`, `Monthly`, `Quarterly`, `Yearly`. All can be selected at once, so multiple frequency variants of the same template can be made available for later use.
- **Custom fields** *(External only)* — a list of fields, each with a **name** and a **type**: `Text`, `Number`, `Date`, or `Dropdown` (Dropdown requires at least one option). At least one custom field must be of type `Date`, and one such Date field must be designated as the **Trigger Date** for the template — this is the anchor date the rest of the template's date logic is calculated from.
- **Folder automation** *(External only)* — boolean. When enabled, creating a service from this template on a client profile automatically creates a matching folder in the Document Sharing Portal.

### Children templates

Once a Service Template is created, its children templates can be configured:

- **Task Template** — exactly one per Service Template.
- **Subtask Templates**
- **Reminder Templates**
- **Checklist Templates**

Availability depends on the parent Service Template's type:

- **External** — full functionality across all four children template types.
- **Internal** — no Reminder Templates; the Task Template has limited/reduced options (see below).

#### Subtask Templates

Purpose: define a list of significant milestones for completing a task.

Each Subtask Template has:

- **Title**
- **Estimated time** — hours and minutes.
- **Steps** — a list that breaks the subtask down into its most base-level steps.

#### Checklist Templates

Purpose: a final, single list for control/QA purposes — meant to be used by the person who did the work, their direct supervisor, and an executive, as a shared sign-off list when reviewing completed work.

A Checklist Template has:

- **Items** — each with just **text**.
- **Estimated time** — hours and minutes, for the checklist as a whole (not per item).

#### Reminder Templates

Purpose: set up lists of automated emails sent to clients, assignees, service managers, and/or partners, based on the configuration below. *(External Service Templates only — see "Children templates" above.)*

A **Reminder** is the container that holds the actual Email Templates to be sent. It has:

- **Title**
- **Document checklist** (boolean) — an addition introduced with the Document Sharing Portal. When enabled, the reminder can send an email that requests a list of documents from an external user; anything they upload is placed into a specific folder in the Document Sharing Portal. See also: [Document Sharing Portal](../Document%20Sharing%20Portal/Cross-Module%20Features.md).
- **Audience type** (binary) — whether the Reminder's child emails are sent to **Clients** (external communication) or to **Employees**, i.e. assignees, service managers, and/or partners (internal communication).
- **Trigger date** — inherited from the parent Service Template; used to calculate the send date for every child email.

**Email Templates** (children of a Reminder), each with:

- **Include toggle** — whether this Email Template is included when the Reminder is instantiated into real emails on a client (i.e. when "chosen emails" are created — see [Glossary](../../../Glossary.md#chosen-eg-chosen-email-chosen-service)).
- **Subject**
- **Body**
- **Offset** — how many days before/after the Trigger Date this email is sent, once it's created as a chosen email.

### Task Template

Each Service Template can have only **one** Task Template. Its structure differs by the parent Service Template's type:

- **External** — two sections: **Task Details** and **Frequency Settings**.
- **Internal** — **Task Details** section only (no Frequency Settings).

#### Task Details section

- **Name** — supports token placeholders written as `::FieldName::`. At task-creation time, the system substitutes the actual value of that field, if available for that instance.
- **Priority** — dropdown: `High`, `Medium`, `Low`.
- **Billable** — boolean.
- **Tags** — a list/array of alphanumeric strings.
- **Description** — multiline text.

#### Frequency Settings section *(External only)*

Two subsections: **Internal Deadline Settings** and **External Deadline Settings**.

**Internal Deadline** — set one of two ways:

1. **Trigger Date + offset** (in days).
2. **Dynamic, via Task Progress Status** — select a Task Progress Status to key off. Task Progress Status is a standard field on any task in the Task module, and defaults to `Info Requested`.
   - Behavior: the Internal Deadline is left **empty** when the task is created. The system waits for a user to change the task's Task Progress Status to the selected status. When that happens, the system takes the exact date the status was set to that value on the actual task, and adds the configured day offset on top — that result populates the Internal Deadline.
   - *Example:* if `Info Received` is the selected status, the Internal Deadline is empty at task creation. Once someone sets the task's status to `Info Received`, the system takes that date and adds the offset to populate the Internal Deadline.

**External Deadline** — up to 4 possible settings; which ones are available depends on the frequency selected on the parent Service Template (see table below):

1. **Same as Internal Deadline** — mirrors the Internal Deadline's value. If the Internal Deadline was empty at the time the task was created, the External Deadline waits for the Internal Deadline to populate, then takes that value. Any manual changes made to the Internal Deadline after that point (before *or* after the initial copy) do **not** propagate to the External Deadline.
2. **Set Offset** — takes the Trigger Date and applies an offset in months and days.
3. **Set Custom Day** — takes the month and year from the Trigger Date, and sets the day to a selected value.
4. **Set Custom Month & Day** — takes the year from the Trigger Date, and uses the selected Month and Day values.

**Available External Deadline settings by frequency:**

| Frequency | Same as Internal Deadline | Set Offset | Set Custom Day | Set Custom Month & Day |
|---|---|---|---|---|
| Daily | ✓ | ✓ | | |
| Weekly | ✓ | ✓ | | |
| Fortnightly | ✓ | ✓ | | |
| Monthly | ✓ | ✓ | ✓ | |
| Quarterly | ✓ | ✓ | ✓ | |
| Yearly | ✓ | ✓ | ✓ | ✓ |

Once a frequency's Frequency Settings have been saved, that frequency variant of the Task Template becomes usable to create an actual service on a client profile. A frequency selected on the Service Template that has **no** saved Frequency Settings configuration **cannot** be used to create a service on a client.

**Status:** Settings-side of Service Templates fully documented (Service Template, Task Template, Subtask Templates, Checklist Templates, Reminder Templates); Clients and Tasks sides pending.
