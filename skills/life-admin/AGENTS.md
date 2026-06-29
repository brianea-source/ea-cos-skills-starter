---
name: life-admin
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Life Admin

## Trigger
- **Heartbeat:** Checks recurring items on schedule (bills, appointments, renewals)
- **On-demand:** User requests ("book a flight", "remind me about...", "compare...")
- **Calendar:** Upcoming events that need prep

## Dependencies
- Structured memory store (YAML or SQLite) for recurring items
- Web search (travel, purchases, comparisons)
- Message tool (reminders, confirmations)
- Calendar integration (if connected)

## Data Store
- e.g. `memory/life_admin.yaml` or `data/life_admin.db`
- All recurring items stored with: description, due date, reminder lead time, status
- Never rely on conversation history for recurring items
