---
name: project-coordinator
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Project Coordinator

## Trigger
- **On-demand:** User creates tasks, asks for status, sets deadlines
- **Heartbeat:** Daily scan for overdue tasks, upcoming milestones
- **Alert:** Deadline approaching (configurable lead time, default 1 day)

## Dependencies
- Task store (YAML or SQLite — structured, queryable)
- Message tool (status summaries, deadline alerts)
- Calendar integration (milestone dates)

## Data Store
- Per-task: title, description, priority (p0–p3), status, assignee, due date, project
- Views: by project, by priority, by due date, overdue
