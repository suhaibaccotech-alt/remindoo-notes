# Automations — Overview (internal)

**Purpose:** Functional notes on **Automations** for the team.

- Reached from **Settings → Automations**. Separate rule lists per module (Leads and Tasks seen in Tenant 1).
- Each row has an **Active** toggle. Rules have no names (SCRUM-1130).
- Opening a rule shows the visual builder: a canvas with the trigger and steps, zoom controls and Fit View. New steps come into view and existing rules open centred; Fit View does nothing and Zoom In overshoots (SCRUM-1185).
- Actions seen: **Send Email** (recipient options include employees, "Email leads" and "Email clients", SCRUM-1100) and a delayed status change (e.g. Complete → after 1 day → Not started).
- Switching on a rule that moves tasks backwards shows a "reopen" confirmation (SCRUM-1130).
- "See how this rule runs" is an explanation diagram. There's no run log.
- Tenant 1 test rules: Tasks "Complete → Send Email" (template "tasks tokens", to Zain and Hammad) is **active**; the backwards rule and the Leads rule are paused. Completing a task in Tenant 1 therefore sends an email.

**Not verified by QA:** the full trigger and action lists, an email actually reaching a lead or client, and rule execution timing.

**Status:** First draft (12 Nov 2026), from QA runs of 9–12 Nov on preprod.
