---
name: onboarding-guide
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Onboarding Guide

## Trigger
- **Event:** Instance first boot (no voice/identity file exists yet, or
  `onboarding_complete` flag is false)
- **Mode:** One-shot — runs once, then deactivates

## Dependencies
- A channel plugin must be active (Slack, Telegram, Discord, etc.)
- Write access to workspace context files (voice/identity, heartbeat, memory)

## Handoff
- On completion: sets `onboarding_complete: true` in instance config
- Logs connected channels + configured features to memory
- Main assistant takes over all subsequent interactions
