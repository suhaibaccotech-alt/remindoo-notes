# Dashboard — Overview (internal)

- Tabs: Tasks, Timesheet, Capacity Planning, Leads, Proposals, Employee & Services, Client Summary.
- Tasks tab: the old "Team capacity – Account" panel (SCRUM-1183) is gone. The new **Outstanding work by team & stage** grid (teams × 5 stages, bottleneck, shared/unowned row, heat legend 1–4 / 5–19 / 20–99 / 100+) appears to replace it. Asked Hammad, 5 Nov.
- Capacity Planning and Employee & Services open on **last week** (26–30 Oct when viewed on Thu 5 Nov). The Capacity Planning cards disagree (Capacity Load 114 hrs / 28 tasks vs Hours Allocated 1 hr / 6 active). Proposed card for Hammad. Related SCRUM-1122.

## Changes seen 6–12 Nov 2026
- History tab: snapshots by period, up to the previous day (SCRUM-1380). Dates are year-first even when the tenant uses DD/MM/YYYY (SCRUM-1383). The period figures don't always add up (e.g. open at start 835, open at end 97, 79 created, 2 completed), probably from deleted test tasks.
- "Current work by team" chart renders (SCRUM-1372). The team filter applies to the cards and grid, and card counts matched list counts (QA Team B Info Requested, Internal Overdue).
- Total Hours = employees × 1,800, counting archived employees (SCRUM-287 question).
- "What's new" is a docked tab with a red dot and slide-out (SCRUM-1376).

**Status:** First draft (5 Nov 2026), updated 12 Nov 2026 from QA runs.
