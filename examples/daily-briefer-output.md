# Example — `daily-briefer` output

This is what the agent posts when the `daily-briefer` skill fires (here at 08:00
local). The short summary goes in the main channel; the detail goes in a thread.

> Sample data only — illustrative, not real.

---

**Main message:**

> ☀️ **Morning brief — Mon, Jun 29**
> 3 meetings today · 2 tasks due · markets up · ☁️ 19°C, light rain pm
> Top focus: **board deck due 5pm** — still missing Q2 numbers.
> Full brief in thread 👇

**Thread reply 1 — Meetings:**

> 🗓️ **Today's meetings**
> - **09:30** Standup (15m) — eng
> - **11:00** Investor sync — Jane Doe (Acme Ventures). _Prep packet sent at 10:30._
> - **15:00** 1:1 — Sam. Open item: hiring plan sign-off.

**Thread reply 2 — Tasks:**

> ✅ **Due today**
> - p0 — Finalize board deck (missing Q2 numbers) — **5:00pm**
> - p2 — Reply to legal re: contract redlines
>
> ⏰ **Due tomorrow:** Submit expense report

**Thread reply 3 — News & markets:**

> 📰 **In your space**
> - Competitor X announced a Series B ($40M) — [source]
> - New model release relevant to your stack — [source]
>
> 📈 **Markets:** S&P +0.6% · NASDAQ +0.9% · your watchlist: NVDA +1.4%, watch AAPL (earnings Thu)

**Thread reply 4 — Weather:**

> ☁️ **Weather:** 19°C, cloudy. Light rain after 3pm — umbrella for the 5pm.

---

## Why this shape

- **Lead with what needs attention** ("board deck due 5pm") so the exec gets
  signal in the first line.
- **Summary in main, detail in thread** keeps channels clean.
- **Adaptive:** if calendar/markets/weather aren't connected, those sections are
  simply omitted (see the skill's "Data Sources (adaptive)" section).
