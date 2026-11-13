# Service Templates

**Purpose:** How Service Templates work from a user's point of view — the feature that lets your firm set up a service once and have it automatically create the right tasks (and emails) for every client that needs it. Spans the **Settings**, **Clients**, and **Tasks** modules.

## How it works, end to end

1. **Settings** — you build a Service Template: what it's called, whether it's Internal or External, how often it runs, and exactly what task(s) it should create. → [Settings/Workflows.md](../Modules/Settings/Workflows.md)
2. **Clients** — you add the service to a client (**Services → Add Services**), choosing its frequency, estimated time, the service's own dates and details, and who does the work. This turns the blueprint into a real, active service for that client. → [Clients/Workflows.md](../Modules/Clients/Workflows.md)
3. **Tasks** — Remindoo creates the first task as soon as the service is saved on the client ("tasks created"), and further ones at the service's frequency. Each task carries the service and frequency (e.g. *Test (Daily)*), the client, the assignees you chose, the template's priority and estimated time, and deadlines calculated the way you configured in Settings. Pausing the service on the client stops new tasks.

## What you can configure in Settings (documented so far)

- Whether the template is **Internal** (a simple reusable building block for Custom Tasks) or **External** (a full service that runs automatically on clients).
- For External templates: which frequencies it can run on (Daily/Weekly/Fortnightly/Monthly/Quarterly/Yearly), any custom fields you want tracked (with one Date field marked as the Trigger Date), and whether a Document Sharing Portal folder should be created automatically.
- The task it creates: its name (which can pull in real client/task data via placeholders), priority, billable status, tags, description, and — for External templates — exactly when it's due internally and when it's due externally, per frequency.
- Any **subtasks** (milestones) and a **checklist** (final sign-off list) you want attached to the task.
- For External templates, **reminders** — automated emails to clients or your team, timed around the template's Trigger Date, optionally including a request for the client to upload documents (which land in the Document Sharing Portal).

Full detail: [Settings/Workflows.md](../Modules/Settings/Workflows.md).

**Status:** Settings side fully documented; Clients side and task creation walked through 13 Nov 2026. How each deadline option plays out on real tasks isn't verified yet.
