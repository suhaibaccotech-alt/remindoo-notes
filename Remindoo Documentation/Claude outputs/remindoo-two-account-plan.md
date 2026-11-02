# Remindoo PM: two-account setup and the move to the new laptop

Plan written Nov 2, 2026. Status: **planned, nothing switched yet**. dev1's runs carry on as they are until the switch in Phase 7.

From the switch onwards, **dev2@remindoo.co** runs every scheduled Remindoo run on its own usage limits, on a new Windows laptop that stays on. **dev1@remindoo.co** stays on AT95 for your chats, approvals and the Command Center. Nothing changes for the team: dev2's Jira, Slack and Google connectors sign in as you, so cards, DMs and drafts still come from you. Your notes reach the laptop through a private GitHub repo, and dev2 reads them from the laptop's copy.

## Decisions (you, Nov 2, 2026)

| Question | Decision |
| --- | --- |
| Who uses the new laptop | You, signed into a second Claude seat, dev2@remindoo.co (same ACCOTAX org, same plan) |
| What each account does | dev2 = automation (every scheduled run). dev1 = your chats and approvals |
| Whose name the team sees | Yours. dev2's connectors sign into your Atlassian, Slack and Google (suhaib.accotech@gmail.com) accounts |
| The laptop | Windows, company-provisioned, no admin rights, stays on after hours |
| Notes sync | A private GitHub repo on your company-email GitHub account (Portable Git + Obsidian Git on both machines) |
| Where runs read notes | From the laptop's synced vault, through a task linked to the laptop |
| Joplin | Stays on AT95 only. It syncs to a Joplin folder inside the vault, and Git carries that to the laptop |
| Sweep cadence | Hourly light sweeps 1:52–7:52 pm, a full sweep at 8:52 pm |
| Models | Opus 5.5 for judgement runs (full sweep, weekly CEO draft, release and sprint runs). Sonnet 5.5 for the rest |
| Command Center buttons | They set a request flag, and dev2's next hourly run does the work |
| Command Center access | Opened to dev2 when the switch starts (Editor share, Editor-level database rules, to-dos moved to a shared collection) |
| Alerts | Slack DM to you, dev2's notification emails forwarded to dev1, and the Command Center. Note: the Slack DM is sent as you, so Slack won't notify you of it. The forwarded email is what notifies you |
| Switch | Dry runs first, then switch. dev1's runs are paused and kept as a backup |
| Backlog next | Release wave (2.1–2.3, 2.6), team channel (2.7, 2.8), reviews (3.4, 3.5), Capture tab (3.3) |

One design choice of mine on top of these: the hourly work is split in two. **Light sweeps** run in the cloud and **notes runs** run on the laptop. A task linked to a computer is put on hold when that computer can't be reached. That is what stopped the afternoon and evening sweeps on Oct 28–29. With the split, a laptop outage pauses only the notes runs. Slack, Gmail, sheets, Jira and the Dashboard keep running. A task on hold usually comes back by itself once its computer is reachable at the next run time: dev1's afternoon sweep did that on Nov 2. Every light sweep also checks dev2's task list and alerts you if the notes run stays on hold.

## How it fits together

| | AT95 (dev1) | New laptop (dev2) | Cloud |
| --- | --- | --- | --- |
| You write | Obsidian notes, Joplin drawings | (nothing day to day) | |
| Git | Obsidian Git pushes and pulls every 10 min | Obsidian Git pulls and pushes every 10 min | GitHub private repo |
| Claude | Chats, approvals, Command Center (owner) | Claude app signed in as dev2, kept open, vault folder connected | dev2's scheduled runs |
| Runs that touch it | None scheduled | Notes runs (read the vault and Joplin folder, write Jira keys back into notes) | Brief, light and full sweeps, weekly, weekend check |

Flow: you write a note on AT95. Within about 10 minutes it is on GitHub, and within about 10 more the laptop has pulled it. The next :22 notes run reads it, then cards or proposes it, and writes the key back into the note on the laptop. Obsidian Git pushes that line back, and AT95 pulls it.

## dev2's schedule after the switch

All times PKT, Mon–Fri unless shown. Each run skips dates in `config/settings.pausedDates`, except the weekend check.

| Run | When | Model | Where | Does | Replaces on dev1 |
| --- | --- | --- | --- | --- | --- |
| 1 pm brief | 12:52 | Sonnet | Cloud | As today, plus to-dos from the shared collection and the laptop's health | Brief (Haiku) |
| Notes run | Hourly 1:22–8:22 | Sonnet | Laptop | Vault and Joplin since the checkpoint, cards from notes, write-backs, vault-sync health | Vault/Joplin part of the evening sweep, and write-backs in Apply queued |
| Light sweep | Hourly 1:52–7:52 | Sonnet | Cloud | Request flags, Slack, both sheets, Sir Waqas's emails, Jira triage, design hand-offs | Afternoon sweep, on-demand sweep, Apply queued |
| Full sweep | 8:52 | Opus | Cloud | Everything cloud-side, QA queue and testers summary, full Dashboard, CEO pending check (Mon–Thu) | Evening sweep |
| Weekly CEO draft | Fri 8:44 pm | Opus | Cloud | As today: a Gmail draft, never sent, ready by 9 pm. It reads Jira directly, so it doesn't wait for the full sweep | Weekly (Sonnet) |
| Weekend check | Sat–Sun 10:07 am and 6:07 pm | Sonnet | Cloud | As today, plus a Slack DM to you on an alert | Weekend check (Haiku) |

That is 17 weekday runs. Most hourly runs end "quiet" after a few cheap checks. If dev2 hits its limits, the first lever is moving notes runs to every 2 hours.

**Backlog runs** (Phase 8, each after its own skill and a dry run): next-sprint draft (Thursdays, 2:07 pm, Opus, skips non-release weeks), the release Friday run (7:22 pm, Opus: reconciliation, release email and Hamna's Sales email as drafts, sprint-end report), and the weekly review (Mondays, 2:07 pm, Sonnet). The team channel posts and the Knowledge Desk ride inside the light and full sweeps, and the Capture tab is a Command Center page change.

## What changes in the Command Center (at the switch, from a dev1 session)

1. Share it with dev2@remindoo.co as **Editor**. Check that the only Editors are dev1 and dev2.
2. Change the database rules from `owner` to `admin` (Editor level) on both paths, including the Dashboard's write rule. Today they are `owner`, so only dev1 can read or write the Inbox, Activity, state, settings or the Dashboard. Dashboard reads stay open to viewers.
3. Move to-dos into a shared `todos` collection and copy the existing ones across. Today they live in your private per-account space (`data/users/<you>`), which dev2 can never see, and a dev2 run adding a to-do would land in dev2's own space.
4. The buttons stop starting tasks. Refresh sets `sweepRequestedAt`. Apply queued still applies Jira, Slack and Gmail items in the page, and sets `applyRequestedAt` for the rest. The page says when the next run picks it up: the next :52 between 1:52 and 8:52 pm on a working day, otherwise 1:52 pm the next working day. A per-item "recheck now" also waits for the next light sweep. Remove the `fire_trigger` permission from the page.
5. Add these fields to `config/settings` (Appendix A): `automationAccount`, `device`, `schedule`, `alertSlackDm`, `automationTasks`. Set `sweepTriggerId` and `applyTriggerId` to null.

Steps 1–2 happen first (Phase 5), so dev2 can do its dry runs. Steps 3–5 happen at the switch itself (Phase 7).

## Moving AT95's local pieces

| Item | On AT95 | On the laptop | How |
| --- | --- | --- | --- |
| Obsidian vault (with Remindoo Documentation inside) | `Desktop\Notes` | `Desktop\Notes` (a Git clone) | The notes repo |
| Obsidian settings and plugins | `.obsidian\` in the vault | Same, through Git | Per-device files are already in `.gitignore` |
| Obsidian app | Portable copy in the vault's `Obsidian\` folder (not pushed) | Per-user install, or copy that folder over | Installer or USB/OneDrive |
| Joplin | `.config\joplin-desktop` (live), `JoplinBackup` (backups). `joplin-desktop-alt1` was last used Oct 9 | Not installed. The sync folder `Desktop\Notes\Joplin` arrives through Git | Joplin → File system sync into the vault |
| opencode + DeepSeek | `.config\opencode` (config, `commands\remindoo-refresh.md`, an older `skills\remindoo-jira-cards` copy) | `%USERPROFILE%\.config\opencode` | Copy by USB/OneDrive, never through Git. Sign in to DeepSeek and Atlassian again (Appendix C) |
| Board snapshot | `Remindoo\command-center-snapshot.html` | `%USERPROFILE%\Remindoo\` | Copy |
| `Claude` folder | Empty | Nothing to move | |
| Project, skills, artifacts, memory | dev1's account | Shared to dev2 or re-saved (Phase 4) | See below |

What doesn't move by itself between accounts: **skills** (dev2 saves its own copies from `claude/skills-next/` in the Project), **scheduled tasks** (dev2 creates its own through the bootstrap prompt), **connectors** (dev2 signs in again, as you), and **memory** (per account). dev2 doesn't need dev1's memory: its runs work from the skills, `config/settings` and the Reference doc.

## Phases

### Phase 1 — done today (dev1)
- [x] This plan, and the dev2 bootstrap prompt (`claude/dev2-bootstrap-prompt.md`), in the Project
- [x] Updated skill versions staged in `claude/skills-next/`. They aren't saved on either account yet, because dev1's live runs still use today's versions. Today's versions are kept in `claude/skills-prev/` for rollback.
- [x] An independent review of the plan, the task prompts and the skill edits, with its findings fixed
- [x] Reference doc: Decision log entry, a Two-account move section in the Automation backlog, and a note in Systems and conventions

### Phase 2 — AT95: finish the notes repo (you, about an hour)
Follow `claude/prompt-notes-repo-setup.md` (paste it into a chat), with these additions:
- [ ] **Before the first push**, clean the vault. Two notes that shouldn't go to GitHub:
    - `Notes/Credentials Used for Tenant Onboarding Testing on 16-6-2026.md`: move the logins to Google Password Manager and delete the note.
    - A note at the vault root with an HR-related title: move it into `Private/`.
    - Then scan the `git status` list for anything else like them.
- [ ] Do step 9 (Joplin) **before** the first commit. In Joplin on AT95: Tools → Options → Synchronisation → target **File system**, folder `C:\Users\AccoTech-95\Desktop\Notes\Joplin`, auto-sync every 10 minutes, encryption off.
- [ ] In Obsidian: Settings → Files and links → Excluded files → add `Joplin/`, so Joplin's sync files don't show up as notes.
- [ ] Add to `.gitignore` the folders the sweeps never open: `Notes/Testing Logs/`, `Notes/Neo Testing Logs/`, `Notes/Dumpster Fires/` and `Notes/-Team-/`. They stay on AT95, and nothing that might hold a login leaves the PC.
- [ ] Decide on Obsidian Git's settings file. If `.obsidian/plugins/obsidian-git/data.json` holds the Git path, add it to `.gitignore`, so each machine keeps its own path.
- [ ] Obsidian Git on AT95: auto commit-and-sync every 10 min, pull on startup.

### Phase 3 — the new laptop (you)
1. [ ] **Power.** Plugged in, with sleep set to Never when plugged in and closing the lid set to "Do nothing" (Settings → System → Power). Set Windows Update active hours to 1 pm–10 pm. If company policy forces sleep, ask IT for an exception. After a restart someone has to sign in to Windows, because the Claude app only runs inside a signed-in session.
2. [ ] **Portable Git**, from steps 2–3 of the repo prompt, in `%USERPROFILE%\PortableGit`.
3. [ ] **Clone the vault:** in git-bash, `git clone <repo URL> "$USERPROFILE/Desktop/Notes"`. The first time, sign in to GitHub with your company account in the browser window. If the laptop's Desktop is redirected into OneDrive (company laptops often are), clone to `%USERPROFILE%\Notes` instead, because a Git folder inside OneDrive breaks.
4. [ ] **Obsidian:** install it per user, or copy the `Obsidian\` folder from AT95. Open the vault. Set Obsidian Git's custom Git path to this laptop's `PortableGit\cmd\git.exe`, with auto pull and auto commit-and-sync every 10 min and pull on startup. Put an Obsidian shortcut in `shell:startup` so it opens at sign-in. **Obsidian must stay open**, because it's what keeps the laptop's copy in sync.
5. [ ] **Claude desktop app:** install it, sign in as **dev2@remindoo.co**, and turn on "open at login" if the app offers it.
6. [ ] **opencode:** see Appendix C.
7. [ ] Copy `Remindoo\command-center-snapshot.html` to the laptop's home folder.

### Phase 4 — dev2's account (you, in claude.ai signed in as dev2)
- [ ] Connectors, signed in **as you**: Atlassian MCP (your Atlassian login), Slack (your Slack user), and Gmail, Google Calendar, Drive, Docs and Sheets (suhaib.accotech@gmail.com, the same Google account dev1 uses). **Don't** connect Remindoo MCP, Trello or Linear.
- [ ] **Mail forward (required):** in dev2@remindoo.co's mailbox, forward Claude's notification emails to dev1@remindoo.co (a filter on the sender). This is how you get notified. The Slack DMs are sent as you, so Slack shows them but doesn't notify you. If the admin blocks forwarding, sign in to dev2 in the Claude phone app instead, so its pushes reach you.
- [ ] From dev1 in claude.ai: share the **Remindoo Project** with dev2 (can edit), and the **Remindoo PM — Reference** doc as Editor.

### Phase 5 — open the Command Center to dev2 (a dev1 chat: say "start the switch")
- [ ] Share the Command Center with dev2 as Editor (you, in its Share menu). Then in chat I republish it with the rules changed from `owner` to `admin`, without touching anything else, and check that dev2 can read `config/settings`.

### Phase 6 — dev2 bootstrap and dry runs (on the laptop, in a dev2 Cowork chat in the Remindoo Project, with `Desktop\Notes` connected)
- [ ] Paste `claude/dev2-bootstrap-prompt.md` (Part 1). It checks that every connector is acting as you and that dev2 can write to the Command Center. It checks the vault and Joplin folder, saves the 8 skills from `claude/skills-next/`, writes `config/settings.device`, and creates the 6 tasks **without schedules**. It sets each cloud task's model. You set the notes run's model in the app, and switch any task not on automatic approval to "Automatically approve". Then it fires each one as a **DRY RUN**: read-only, over the last 3 working days, writing only a `dry-run` runs record, and summarises them for you.
- [ ] You check each dry run (your go-live rule).

### Phase 7 — the switch
1. [ ] **dev1 chat on AT95, "do the switch":** first a "sweep now" if the evening sweep hasn't run lately (a catch-up from Oct 28 was done on Nov 2). Then pause dev1's brief, weekly, weekend, Apply queued and on-demand sweep tasks, which stay as a backup. Switch the afternoon and evening sweeps off explicitly: a task on hold can come back by itself, as the afternoon sweep did on Nov 2. Copy the to-dos into `todos`. Republish the Command Center with the shared to-dos and flag-only buttons. Update `config/settings` (Appendix A). You then save the 8 `skills-next` skills on dev1 from the review cards, and I move them to `claude/skills/` in the Project.
2. [ ] **dev2 chat, bootstrap Part 2 ("go live"):** reset the vault and Joplin checkpoints to now, so the laptop's clone times don't count as changes. Then set each task's schedule, check the next run times and approval settings, and write the task ids to `config/settings.automationTasks`.
3. [ ] Next working day: the 1 pm brief arrives by Slack DM. Check its Health line shows the notes runs and the laptop's last pull.
4. [ ] Replace the Project instructions with Appendix B.

### Phase 8 — backlog on dev2 (one at a time, each with a skill, a dry run and your OK)
1. Release wave: the remindoo-release skill (2.1), Thursday next-sprint draft (2.2), release Friday run (2.3), with Hamna's Sales email (2.6) and the sprint-end report (3.5) inside it.
2. Team channel: you create #remindoo-updates and #remindoo-ask. Change posts, tick reminders and the Current plan canvas (2.7) go in the full sweep. The Knowledge Desk (2.8) answers new #remindoo-ask questions in the light sweeps. Messages wait for approval until their template has gone two weeks without edits (H4).
3. Reviews: the Monday weekly review (3.4).
4. Capture tab (3.3): a Command Center page change, plus a `capture` collection the light sweeps read.

## Risks and how they're handled

| Risk | What happens | Handling |
| --- | --- | --- |
| Laptop off, asleep or signed out | Notes runs go on hold. Light and full sweeps carry on | The light sweeps' watchdog flags missing notes runs. You wake or sign in to the laptop, and the next notes run catches up from its checkpoint |
| Obsidian closed on the laptop | The vault stops pulling, so notes runs see old notes and write-backs aren't pushed | Each notes run checks `.git/FETCH_HEAD`. Older than 2 hours opens a "vault sync" alert |
| The same note edited on both machines within 10 minutes | Git merge conflict | Write-backs skip notes modified in the last 15 minutes. Obsidian Git shows the conflict, and you keep your version |
| Obsidian Git's Git path differs per machine | Sync fails on one machine | If the setting syncs through Git, add `.obsidian/plugins/obsidian-git/data.json` to `.gitignore` and set it on each machine |
| A connector on dev2 signed in as the wrong person | Cards or DMs come from someone else | The bootstrap checks the Atlassian accountId, the Slack user id and the Gmail address before creating anything |
| Pushes and emails go to dev2 | You miss alerts | The forwarded email notifies you (or dev2 on your phone). The Slack DM and the Command Center keep a record, but Slack doesn't notify you of messages sent as you |
| A computer-linked task goes on hold | Notes runs stop while the laptop can't be reached. dev1's sweeps were on hold Oct 29–Nov 2, and the afternoon one came back by itself on Nov 2 | Every light sweep checks dev2's task list and alerts you if a task stays on hold |
| Scheduler delays from 7 to 10 pm PKT | Runs in that window can start late (the weekly started 35 minutes late on Oct 30) | No run depends on another finishing first. The weekly may arrive after 9 pm |
| A merge conflict on the laptop | Notes stop syncing | Notes runs alert on `.git/MERGE_HEAD` and stop writing back until it's resolved |
| Skills drift between the two accounts | Runs and chats follow different rules | The Project's `claude/skills/` is the master copy. Every skill change is saved on both accounts (backlog 4.6) |
| dev2's usage limits | Late runs get cut off | Most hourly runs are quiet. Notes runs can move to every 2 hours. Opus is used only where judgement matters |

## Rollback
If dev2's set-up misbehaves after the switch:
1. Pause dev2's tasks in the dev2 chat.
2. Switch dev1's brief, weekly, weekend, Apply queued and on-demand sweep tasks back on.
3. Save `claude/skills-prev/` on dev1.
4. Republish the Command Center with buttons that fire `trig_01Gj7oDZD68PaXDuLwizbQ4W` and `trig_01EMvUooGZHZDTNBNC39KSLS`, and put those ids back in `config/settings`.

The afternoon and evening sweeps still need AT95 on, as before.

## Things only you can do
- [ ] Phase 2 (vault clean-up, repo, Joplin sync) on AT95
- [ ] Phase 3 laptop set-up, and Phase 4 connector sign-ins on dev2
- [ ] Share the Project, the Reference doc and the Command Center with dev2
- [ ] Approve: the Command Center republish, the dry runs, saving skills on both accounts, and the switch

## Appendix A — `config/settings` additions

```json
{
  "automationAccount": "dev2@remindoo.co",
  "device": {
    "name": "<laptop device name, from the bootstrap>",
    "vault": "C:\\Users\\<laptop user>\\Desktop\\Notes",
    "joplinSync": "C:\\Users\\<laptop user>\\Desktop\\Notes\\Joplin"
  },
  "schedule": {
    "brief": "Mon-Fri 12:52",
    "notes": "Mon-Fri hourly 13:22-20:22",
    "light": "Mon-Fri hourly 13:52-19:52",
    "full": "Mon-Fri 20:52",
    "weekly": "Fri 20:44",
    "weekend": "Sat-Sun 10:07, 18:07"
  },
  "alertSlackDm": true,
  "automationTasks": {},
  "sweepTriggerId": null,
  "applyTriggerId": null
}
```

The bootstrap (Phase 6) writes `automationAccount`, `device`, `schedule` and `alertSlackDm`. dev1's runs ignore these fields. The switch (Phase 7.1) sets `sweepTriggerId` and `applyTriggerId` to null, and go-live (Phase 7.2) fills in `automationTasks`.

## Appendix B — Project instructions: paste over the current text at the switch

The current instructions also stop mid-sentence ("Every card needs: … an assignee, exactly"). This version keeps everything else and adds the two-account part.

```
# Remindoo PM: project instructions

You are the product/project-management assistant for Remindoo, a CRM for UK accounting firms, built by AccoTech (part of ACCOTAX). The user is Suhaib Osmani, Product/Project Manager (the "PM seat", dev1@remindoo.co). He reports to Umair Saeed (Team Lead), who reports to the CEO, Sir Waqas.

## Two accounts (since Nov 2026)
- dev1@remindoo.co on AT95: Suhaib's chats and approvals. Owner of the Command Center.
- dev2@remindoo.co on the automation laptop: every scheduled run (brief, notes runs, light and full sweeps, weekly CEO draft, weekend check, release runs). Its connectors act as Suhaib.
- Notes: written on AT95 (Obsidian, Joplin), synced to the laptop by a private GitHub repo. Laptop paths are in config/settings.device.
- A chat on either account follows the same rules. Skills are saved on both accounts from claude/skills/ in this Project.

## Read first
- The Remindoo PM Reference doc (link in claude_remindoo-reference.md; ids in config/settings.refDoc): current facts, the Decision log (newest wins) and the Automation backlog.
- config/settings in the Command Center (https://claude.ai/artifact/LQJwA1tFaSyQiCvpb7t9Y8).
- claude/skills/*.md: the master copy of each workflow's rules.
- claude/remindoo-two-account-plan.md: how the two accounts split the work.
If two sources disagree, the most recent dated decision wins. Mention the conflict to Suhaib.

## Use the skill for the job
- Jira cards → remindoo-jira-cards · PRDs → remindoo-prd · CEO emails → remindoo-ceo-email · Notes sweep → remindoo-notes-sweep · Command Center → remindoo-command-center · 1 pm brief → remindoo-brief · QA queue → remindoo-qa · Design hand-offs → remindoo-design-handoff

## Approval rules
- When Suhaib tells you in chat to do something in Jira, do it at once. Ask only when you'd have to choose something he didn't specify (which cards, owner or sprint).
- Supervise, not orchestrate (decision 26 Oct 2026): act on clear-cut work the way Suhaib would and log it in Command Center Activity. Auto-apply and auto-send what config/settings allows (autoApplyTypes, autoSendMessages).
- Ask Suhaib only for what config/settings.escalate lists: anything to Sir Waqas or Umair, client or money decisions, and anything where the owner or meaning would be a guess.
- Always ask first for sprint closes, deletions, design hand-offs and every email. He approves the final text.
- Never delete Jira issues: merged or duplicate cards move to the "Delete" status. Never send the CEO email: leave it as a Gmail draft.
- Never use the Remindoo app connector (Remindoo MCP) unless Suhaib asks.

## Jira essentials
Site accotech.atlassian.net, project SCRUM, cloudId 13750557-1e50-47c7-b206-d3a31297d5f8. Every card needs a title "Module – Short problem", an assignee, exactly one module label plus one src- label, a description with context, and a sprint (see remindoo-jira-cards).
```

## Appendix C — opencode on the laptop
1. On AT95, run `where opencode` in a terminal to find the program (probably under `%USERPROFILE%\.local\bin`). Copy it to the same place on the laptop.
2. Copy `%USERPROFILE%\.config\opencode\` to the laptop: `opencode.jsonc`, `commands\` and `skills\`. Copy `service.json` (opencode's own password) by USB only, or let opencode make a new one.
3. Sign in again to DeepSeek and to the Atlassian MCP (`https://mcp.atlassian.com/v2/mcp`). Don't copy `.local\share\opencode\auth.json` between machines.
4. In `commands\remindoo-refresh.md`, change the output path to the laptop's `Remindoo\command-center-snapshot.html`. Its card cap says **15**, but `config/settings.cardCap` is **20**: pick one and make them match.
5. `skills\remindoo-jira-cards` is the Oct 16 copy. Refresh it from `claude/skills/remindoo-jira-cards.md` after the switch.
6. Keep your rule: opencode previews every Jira change and waits for your OK.
