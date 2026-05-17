# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## what it is

cycle is a private period and phase tracker built on 21 cycles of real TempDrop data. It tracks symptoms, logs flow, journals against cycle day and phase, and gets more accurate with every month. Built for one person. Not designed to scale.

**Live at:** `https://leonnariley18-ui.github.io/cycle/`

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. A day-sensitive insight tells you what's happening right now, not just what phase you're in. Lean into and go easy on lists give you something actionable.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date.

**Symptom log** — 19 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days.

**Journal** — a small open field on the today screen. Entries stored against your exact cycle day and phase. The data tab holds your full archive grouped by phase — each section leads with a hormone readout and a science line. Edit window is today plus three days back. After that, entries are sealed and read-only.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, and symptom patterns that build over time.

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

Data is stored as a JSON blob per user — periods, symptoms, settings, and journal entries all in one document. PIN is hashed client-side before being used as a token. Supabase never sees the raw PIN.

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
