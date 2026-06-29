---
name: daily-briefer
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Daily Briefer

## Trigger
- **Schedule:** Daily at user-configured time (default 08:00 local)
- **On-demand:** User says "brief me", "morning brief", "what's happening today"

## Dependencies
- Web search (news, weather, markets)
- Calendar integration (if connected)
- Task store (e.g. MEMORY.md or SQLite)
- Message tool (to post DM + thread)

## Data Sources (adaptive)
Only include sections for connected sources:
- Calendar → Meetings section
- Task store → Tasks section
- Web search → News section
- Financial APIs/search → Markets section
- Weather → Weather section

## Workflow
1. Gather data from each connected source.
2. Compose a concise brief — lead with what needs attention today.
3. Post a short summary in the main channel; put detail in a thread/reply.
