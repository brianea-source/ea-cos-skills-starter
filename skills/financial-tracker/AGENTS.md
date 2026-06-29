---
name: financial-tracker
kind: agent-persona
version: 1.0.0
---
# AGENTS.md — Financial Tracker

## Trigger
- **Schedule:** Daily market check (user-configured time or market open)
- **On-demand:** User asks about portfolio, spending, upcoming bills
- **Alert:** Significant price movement (configurable threshold, default ±5%)

## Dependencies
- Web search (market data, financial news)
- Structured memory (portfolio positions, cost basis, alerts)
- Message tool (alerts, summaries)

## Data Store
- e.g. `data/finance.yaml` or `data/finance.db`
- Tracks: positions, cost basis, alert thresholds, bill due dates, tax deadlines
