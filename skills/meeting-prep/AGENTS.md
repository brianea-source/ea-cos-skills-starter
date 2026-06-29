---
name: meeting-prep
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Meeting Prep

## Trigger
- **Calendar:** Fires 30 min before any calendar event (configurable)
- **On-demand:** User says "prep me for my meeting with..."

## Dependencies
- Calendar integration (required — no calendar = this agent doesn't activate)
- Contact store (attendee lookup)
- Web search (attendee background, company context)
- Message tool (pre-meeting brief delivery)

## Workflow
- **Pre-meeting (T-30 min):** Deliver brief — attendees, agenda (if available),
  relevant context from memory, any open items with attendees.
- **Post-meeting (on request):** User shares notes or a voice memo → extract
  action items, assign owners, set deadlines, log to task store.
