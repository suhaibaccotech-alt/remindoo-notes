# Service Templates

**Purpose:** Consolidated technical/functional documentation for Service Templates — the mechanism that lets the firm define reusable service/task blueprints in Settings, apply them to individual clients, and have the Task module automatically generate the resulting tasks (and, for external templates, dynamic emails) at the right time. Spans the **Settings**, **Clients**, and **Tasks** modules.

## Lifecycle

1. **Settings** — a Service Template (and its children: Task Template, Subtask Templates, Reminder Templates, Checklist Templates) is defined. This is the "cast" — nothing exists on any client yet. → [Settings/Workflows.md](../Modules/Settings/Workflows.md)
2. **Clients** — *(not yet documented)* — a Service Template is applied to a specific client profile, creating an actual service instance for that client.
3. **Tasks** — *(not yet documented)* — the Task module generates the real task(s) from that service instance, applying the Internal/External Deadline logic and token substitution configured in the Task Template.

## Settings: summary

- A **Service Template** is `Internal` or `External`. Internal templates are simple building blocks for Custom Tasks (no custom fields, trigger date, frequencies, or folder automation). External templates carry the full configuration (custom fields incl. a mandatory Trigger Date, frequencies, folder automation) and drive automatic task + dynamic email creation on clients.
- Each Service Template has exactly one **Task Template**, with a Task Details section (name w/ token placeholders, priority, billable, tags, description) and — for External templates — a Frequency Settings section defining how the Internal Deadline and External Deadline are calculated per frequency. A frequency is only usable on a client once its Frequency Settings have been saved.
- **Subtask Templates** break the task down into milestone-level subtasks (title, estimated time, steps).
- **Checklist Templates** provide one sign-off list (text items + overall estimated time) shared by the worker, their supervisor, and an executive.
- **Reminder Templates** (External only) define automated emails sent to Clients or Employees (assignees/service managers/partners), timed off the Trigger Date; a Reminder can optionally request documents from an external user via a **document checklist**, which lands in a Document Sharing Portal folder — see [Document Sharing Portal/Cross-Module Features.md](../Modules/Document%20Sharing%20Portal/Cross-Module%20Features.md).

Full detail: [Settings/Workflows.md](../Modules/Settings/Workflows.md).

**Status:** Settings-side fully documented; Clients and Tasks sides pending.
