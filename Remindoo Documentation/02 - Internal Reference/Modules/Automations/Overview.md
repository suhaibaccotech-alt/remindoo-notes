# Automations — Overview (internal)

**Purpose:** Functional notes on **Automations** for the team.

## Page
- `/settings/automations` ("Automations Rules"). Tabs with rule counts: Leads, Proposals, Tasks (sub-tabs **Status (n)** and **Deadlines (n)**), Clients, Services.
- Rules are rows in an inline-editable grid, saved together with **Save Automations**. **Add Rule** appends a paused row; nothing persists until save. Rules have no names (SCRUM-1130).
- Columns: status / condition, After, Then do / action, Email template (or Template / details), Send / assign to, Active, Actions. The Services grid adds Service, Task, Subtasks ("All n subtasks") and When.
- Footer: "n total rules, n active, n paused".

## Semantics (from the in-app help text)
- Status rules: "Runs when a <record> enters this status — not on ones already sitting in it. Once per entry, and only if it is still there when the wait is up."
- Task deadline rules: "Emails a set time before or after each task's own internal or external deadline, for tasks in the statuses you choose. Sent once per deadline; complete, archived and snoozed tasks are never reminded. Day-based reminders go out at 09:00 UTC."
- Deadline row fields: statuses (multi-select: All open statuses, Not started, In-Progress, Awaiting Feedback), Internal/External deadline, number + unit (days), Before/After, action, template.
- Actions seen: **Send Email**, **Change Status** (Clients: Archive → Frozen). A rule whose template was deleted shows "Deleted template — choose another" but can still be Active.
- Switching on a rule that moves tasks backwards shows a "reopen" confirmation (SCRUM-1130). "See how this rule runs" is a diagram, not a run log.

## Visual builder
- **Build visually** → "Build an automation": scope chips (Leads, Proposals, Tasks, Task deadlines, Clients, Services), a TRIGGER palette, a canvas ("Add a trigger"), "Active on save", Cancel, **Add to grid**, Save automations.
- Fit View does nothing and Zoom In overshoots (SCRUM-1185).

## Test data to be aware of (preprod, 13 Nov)
- Michael Eldred Clark's tenant: active rules on Leads (New Lead → Send Email), Tasks (Queries Raised with Client → Send Email), Clients (Archive → Frozen; Frozen → Send Email with a deleted template) and Services (two subtask rules with deleted templates). Creating a lead there sends an email.
- Tenant 1: Tasks "Complete → Send Email" is active (12 Nov).

**Not verified:** the full action list, a rule actually firing, and timing.

**Status:** First draft (12 Nov 2026), rewritten 13 Nov 2026 from a preprod walk-through.
