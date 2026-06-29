# EA / CoS Agent Skills — Starter Pack

A small, sanitized starter pack of **agent "skills"** for building Executive
Assistant / Chief of Staff style automations with agentic coding tools
(Claude Code, Cursor, etc.).

Each skill is just a markdown file the agent loads on demand. They describe
**when** the agent should act (triggers), **what** it needs (dependencies),
and **how** it behaves (workflow). Treat them as templates — copy, rename, and
adapt to your own stack, tools, and data stores.

> These are generic patterns. No client- or product-specific details are
> included. Wire them up to whatever calendar, task store, search, and
> messaging tools you use.

## The skills

### EA / CoS personas (`skills/`)
| Skill | What it does |
|-------|--------------|
| `daily-briefer` | Automated morning brief: calendar, tasks, news, markets, weather |
| `meeting-prep` | Pre-meeting brief (T-30) + post-meeting notes → action items |
| `relationship-manager` | Tracks contacts, follow-ups, birthdays, stale relationships |
| `project-coordinator` | Tasks, priorities, deadlines, overdue/milestone scans |
| `life-admin` | Recurring items: bills, appointments, renewals, bookings |
| `financial-tracker` | Portfolio/spend tracking, bill + tax deadlines, price alerts |
| `content-drafter` | Drafts in your voice with an explicit approval gate |
| `research-analyst` | Budgeted, source-cross-referenced research with TL;DR delivery |
| `ops-monitor` | Continuous health monitoring with auto-fix + escalation |
| `onboarding-guide` | One-shot first-boot setup, then hands off |

### Utility (`skills/`)
| Skill | What it does |
|-------|--------------|
| `connect-channel` | End-to-end Slack / Telegram / Discord / WhatsApp connection |

## See it in action

- **[Example output](examples/daily-briefer-output.md)** — what the
  `daily-briefer` actually posts each morning.
- **[Wiring guide](docs/wiring-guide.md)** — take `daily-briefer` from a
  markdown template to something that posts to you every day (channel,
  data sources, scheduler, context).

## How to use

1. Pick a skill, copy its folder into your agent's skills directory.
2. Replace the generic dependencies (calendar, task store, search, message
   tool) with the integrations you actually use.
3. Keep a per-user context/voice file so drafts come out "ready to send."
4. Start human-in-the-loop (draft, don't send). Automate end-to-end only once
   you trust a given workflow.

## Design principles

- **Triggers over chat history** — persist recurring items in a structured
  store (YAML/SQLite), never rely on conversation memory.
- **Adaptive** — only run the sections you have data sources for.
- **Approval gates** — never auto-send/post without explicit confirmation.
- **Budgets** — bound research/tool usage so the agent doesn't rabbit-hole.

## License

MIT — see [LICENSE](LICENSE).
