---
name: connect-channel
description: "End-to-end Slack, Telegram, Discord, and WhatsApp connection: conversational setup, tokens, manifest, events, Socket Mode, verification, and self-troubleshooting with web research."
---
# Connect Channel

When the user wants Slack, Telegram, Discord, or WhatsApp connected — or reports
channel issues — follow this skill.

## Slack (manifest-first)
- Create the app from a manifest (not the UI click-path).
- Set scopes and **all** required bot events.
- Enable Socket Mode; you need both an app-level token (`xapp-`) and a bot
  token (`xoxb-`).
- Align App Home settings so DMs work.
- Save events explicitly — unsaved events are a common failure.

## Self-troubleshooting
Diagnose → **web search** the official docs → fix one step at a time.

Common issues:
- manifest/UI desync
- lost or unsaved tokens
- unsaved events
- reinstall token rotation
- config truncation
- invalid keys

Do **not** shorten the Slack path to "create app and paste token" — manifest,
events, Save, and both tokens are required for reliable DMs and threads.

## Verification
Send a real test message on the live channel before marking setup complete.
