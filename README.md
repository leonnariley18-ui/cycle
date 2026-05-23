# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## what's new — v2.2 · may 2026

**Wrapped** — when a new period starts, the previous cycle gets a summary. Slides in from the log tab. Contains: an opening observation about what made the cycle notable, stats with meaningful comparisons to recent cycles, how this cycle compared (spotting patterns, luteal length drift, period weight), emotional texture anchored by your own journal quote, flow intensity bars, your journal entries as a narrative arc (one per phase, chronologically ordered), symptoms by phase, and spotting events with notes and vibe tags from those days. Ends with 🌙. Unviewed wraps show a small pulsing dot on the log nav and a nudge line at the top of the history list. A backfill button in data → sync & backup generates wraps for any eligible past periods.

**Spotting insights restructured** — the spotting page now leads with your events organized by *when they happened* (before my period, mid-cycle, after my period) — the same card structure as journal phase entries in the data tab. Each event shows date, color, your written note, and the symptoms you logged that day as colored pills. The original insight cards (gap to period, color breakdown, where in your cycle) follow below.

**Symptoms by phase retired from insights** — it now lives inside each wrapped, where it's contextually meaningful. Symptom patterns (the cumulative, cross-cycle version) stays on insights permanently.

**Period numbering** — history entries now show period numbers (period 22, period 23) instead of cycle numbers. Terminology corrected throughout.

---

## what's new — v2.1 · may 2026

**Spotting log** — a whole new logging surface, separate from flow. Log from the log tab anytime — active period or not. Record the date (retroactively if needed), when it's happening (before your period, mid-cycle, or after), color, and notes. Color dots come with a brief explanation of what each means on tap.

**Spotting insights** — tap the 🔮 in the insights title to open a dedicated spotting page. Slides in as a full new screen. Gets smarter the more you log.

**Phase fix** — the calendar and journal phase labels no longer flip to a new cycle when your period is late. If no period has been logged, luteal holds and keeps counting. The app now waits for you to actually log a period before flipping the calendar forward.

**Edit lock** — only the most recent period is editable in the log tab. Once a new cycle starts, previous entries are sealed and read-only.

**Turned off** — moved to sit with the other blue mood pills where it belongs visually.

**Label fixes** — "Cycles tracked" → "Periods tracked." "Cycle N" → "Period N" throughout.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. A day-sensitive insight tells you what's happening right now, not just what phase you're in. Lean into and go easy on lists give you something actionable.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date. Only the most recent period is editable — previous entries are locked once a new one starts.

**Spotting log** — accessible from the log tab in both active and inactive period states. Logs date, timing, color, and notes as a discrete event. Color dots explain what each color means on tap. No effect on cycle calculations.

**Wrapped** — generates automatically when a new period starts. One per completed app-logged cycle. Tappable from the history list. A narrative summary of the cycle just finished — stats, comparisons, emotional texture, journal arc, symptoms by phase, spotting. Lives in the log tab.

**Symptom log** — 25 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days.

**Journal** — a small open field on the today screen. Entries stored against your exact cycle day and phase. The data tab holds your full archive grouped by phase — each section leads with a hormone readout and a science line.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first. Luteal correctly extends past predicted end date when no period has been logged yet.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, symptom patterns. Tap 🔮 to open the spotting insights page.

**Data** — cloud sync via Supabase, local backup export, baseline reset, and wrapped backfill for eligible past periods.

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

Data is stored as a JSON blob per user — periods, symptoms, settings, journal entries, spotting events, and wraps all in one document. PIN is hashed client-side before being used as a token. Supabase never sees the raw PIN.

**Columns:** `user_token`, `periods`, `symptoms`, `journal`, `spotting`, `wraps`, `active_period`, `settings`, `updated_at`

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
- Cycle × transitions integration — surface current phase on the transitions home screen so morning journaling is informed by where you are hormonally
- Journal memory on today — surface what you wrote on this cycle day last month
- Cycle length weighting — weight recent cycles more heavily than older data
- Wrapped comparisons across wraps — "this cycle you logged anxious in luteal, same as the last 3 cycles"
- Friend version — a clean blank version with no TempDrop baseline for sharing

---

*built entirely with [Claude](https://claude.ai) · single HTML file · no frameworks*
