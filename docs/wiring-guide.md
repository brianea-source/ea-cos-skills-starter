# Wiring guide — `daily-briefer` end to end

A concrete walkthrough of how to take the `daily-briefer` skill from a markdown
template to something that actually posts to you every morning. The same pattern
applies to the other skills — swap the trigger, dependencies, and data sources.

This guide is **tool-agnostic** but uses a common stack as the example:

- **Agent runtime:** Claude Code / Cursor agent (anything that can load a skill
  file and call tools)
- **Channel:** Slack (see `skills/connect-channel/SKILL.md`)
- **Scheduler:** cron / a scheduled CI job / a hosted scheduler
- **Task store:** a simple `tasks.yaml` (or SQLite)

---

## 1. Drop the skill in

Copy the skill folder into wherever your agent loads skills from:

```bash
cp -r skills/daily-briefer /path/to/your-agent/skills/
```

The agent reads `AGENTS.md` to learn **when** to run and **what** it needs.

## 2. Connect a channel (so it can talk to you)

Follow `skills/connect-channel/SKILL.md`. For Slack you need:

- An app created from a manifest with the right scopes + bot events
- Socket Mode enabled
- Both tokens available to the agent as env vars:

```bash
export SLACK_APP_TOKEN="xapp-..."   # app-level
export SLACK_BOT_TOKEN="xoxb-..."   # bot
```

Verify with a real test message before moving on.

## 3. Wire the data sources

The skill is **adaptive** — only the sources you connect will appear in the
brief. Connect what you have:

| Section  | Connect this                          |
|----------|---------------------------------------|
| Meetings | Calendar API (Google/Microsoft) or an `.ics` feed |
| Tasks    | `tasks.yaml` / SQLite / your task tool |
| News     | Web search tool                        |
| Markets  | A finance API or web search            |
| Weather  | A weather API or web search            |

Minimal `tasks.yaml`:

```yaml
- title: Finalize board deck
  priority: p0
  due: 2026-06-29
  status: open
- title: Submit expense report
  priority: p2
  due: 2026-06-30
  status: open
```

## 4. Schedule the trigger

The skill's trigger is "daily at a configured time." Implement that with
whatever scheduler you have. With cron, invoking your agent headless:

```bash
# 08:00 every day — run the daily-briefer skill
0 8 * * * /path/to/agent run --skill daily-briefer >> ~/briefer.log 2>&1
```

(With a CI scheduler, use a cron-scheduled workflow that runs the same command.)

## 5. Keep it human-in-the-loop first

Start by having the agent **post the brief only**. Once you trust it, layer on
the action skills (e.g. let `meeting-prep` draft follow-ups, but keep the
"don't auto-send" approval gate from `content-drafter`).

## 6. Add context for quality

The single biggest quality lever: give the agent a **context/voice file** and a
small **living memory** of priorities, key people, and recurring projects. The
output quality jumps when the agent knows what matters to you.

---

## Adapting to other skills

| Skill              | Change the trigger to…            | Key dependency           |
|--------------------|-----------------------------------|--------------------------|
| `meeting-prep`     | calendar event T-30               | calendar + contact store |
| `relationship-manager` | daily heartbeat scan          | contact store            |
| `project-coordinator`  | on-demand + deadline alerts   | task store               |
| `financial-tracker`    | market open                   | finance data             |
| `content-drafter`      | on-demand                     | voice file + approval gate |

The structure is always the same: **Trigger → Dependencies → Workflow**, with a
structured store instead of chat history for anything recurring.
