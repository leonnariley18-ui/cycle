# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## what's new — v2.1 · may 2026

**Spotting log** — a whole new logging surface, separate from flow. Log from the log tab anytime — active period or not. Record the date (retroactively if needed), when it's happening (before your period, mid-cycle, or after), color, and notes. Color dots come with a brief explanation of what each means on tap.

**Spotting insights** — tap the 🔮 in the insights title to open a dedicated spotting page. Slides in as a full new screen. Shows when it happens, your average gap between spotting and period start broken down cycle by cycle, color breakdown from your actual data, and where in your cycle spotting tends to land. Gets smarter the more you log.

**Cycle numbering** — every period in your history now has a cycle number. Cycle 1 is your earliest TempDrop entry. The current period is cycle 23. Shows in the history tab and in spotting insights.

**Phase fix** — the calendar and journal phase labels no longer flip to a new cycle when your period is late. If no period has been logged, luteal holds and keeps counting. The app now waits for you to actually log a period before flipping the calendar forward.

**Turned off** — moved from the mood category (blue) to physical (pink). Makes more sense where it lives.

**Edit lock** — only the most recent period is editable in the log tab. Once a new cycle starts, previous entries are sealed and read-only.

**Label fix** — "Cycles tracked" corrected to "Periods tracked."

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. A day-sensitive insight tells you what's happening right now, not just what phase you're in. Lean into and go easy on lists give you something actionable.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date. Only the most recent period is editable — previous entries are locked.

**Spotting log** — accessible from the log tab via a secondary button below the start period form. Available anytime, including during an active period. Logs date, timing, color, and notes as a discrete event — no effect on your cycle calculations.

**Symptom log** — 25 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days.

**Journal** — a small open field on the today screen. Entries stored against your exact cycle day and phase. The data tab holds your full archive grouped by phase — each section leads with a hormone readout and a science line. Edit window is today plus three days back. After that, entries are sealed and read-only.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first. Luteal phase now correctly extends past predicted end date when a period hasn't been logged yet.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, and symptom patterns that build over time. Tap 🔮 to open the spotting insights page.

**Data** — cloud sync via Supabase, local backup export, and a baseline reset.

---

## tech stack

| layer | tool |
|---|---|
| language | vanilla HTML/JS — single file |
| database | Supabase (PostgreSQL) |
| auth | PIN-based (hashed token) |
| hosting | GitHub Pages |

---

## infrastructure

**Supabase project:** `sdvmycusfyavsuvsjvrv`
**Table:** `cycle_data`

Data is stored as a JSON blob per user — periods, symptoms, settings, journal entries, and spotting events all in one document. PIN is hashed client-side before being used as a token. Supabase never sees the raw PIN.

**Columns:** `user_token`, `periods`, `symptoms`, `journal`, `spotting`, `active_period`, `settings`, `updated_at`

---

## keep-alive

A GitHub Actions workflow (`supabase-ping.yml`) runs every Monday and Thursday to ping both the cycle and The Cloud Supabase projects, preventing free-tier pauses. No manual intervention needed.

---

## installing on device

**Android (Chrome)**
1. Open Chrome → navigate to the app URL
2. Tap ⋮ menu → Add to Home Screen → Add

**iPhone/iPad (Safari only)**
1. Open Safari → navigate to the app URL
2. Tap Share → Add to Home Screen → Add

---

## related apps

All built by the same person, same stack, same philosophy:

| app | repo | what it does |
|---|---|---|
| transitions | [leonnariley18-ui/transitions](https://github.com/leonnariley18-ui/transitions) | morning commute journal + night randomizer |
| The Cloud | [leonnariley18-ui/the-cloud](https://github.com/leonnariley18-ui/the-cloud) | private terpene journal |

---

## future

- Hormone chart — estrogen, progesterone, LH, FSH as overlapping curves across the full cycle, with journal entries surfaced at the point they were written
- Cycle-aware energy forecast — a "this week" view that translates phase position into capacity
- Journal memory on today — surface what you wrote on this cycle day last month
- Cycle length weighting — weight recent cycles more heavily than older data
- Friend version — a clean blank version with no TempDrop baseline for sharing

---

*built entirely with [Claude](https://claude.ai) · single HTML file · no frameworks*
