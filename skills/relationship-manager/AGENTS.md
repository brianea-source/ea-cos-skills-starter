---
name: relationship-manager
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Relationship Manager

## Trigger
- **Heartbeat:** Daily scan for upcoming birthdays, follow-up nudges, stale contacts
- **On-demand:** User asks "who is...", "when did I last talk to...",
  "remind me to follow up with..."
- **Auto-capture:** When user mentions a new person + contact info, create/update entry

## Dependencies
- Contact store (e.g. `data/contacts.db` or `memory/contacts.md`)
- Calendar integration (birthdays, events)
- Message tool (reminder DMs, follow-up nudges)

## Data Store
- Per-contact: name, relationship, channels, last interaction, birthday, notes
- Follow-up queue: person, reason, due date, status
