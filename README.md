# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## what's new — v2.6 · august 2026

**Brush tracker** — a nightly dental habit tracker, tucked into the app behind the glowing 🗄️ in the data tab. Progresses through 7 habit-formation tiers (Initiation through Maintenance) over ~91 days of consistent nightly brushing, with contextual "science" messaging tied to your tier and slip streak, a weekly Sunday digest with confetti, a full achievements/milestones system, and a reference playbook with routine steps and countdown timers. Own 4-screen bottom nav (Dashboard / Science / Playbook / Awards) inside the tracker, with its own sync dot mirroring the main app's sync state. Fully independent from period data — resetting it doesn't touch your cycle history, and resetting to baseline doesn't touch it either. Synced via Supabase under a new `brush_tracker` column, same as the rest of the app. The confetti effect is bundled locally (`vendor/confetti.min.js`) rather than loaded from a CDN, so it still works offline.

**Unprotected sex log** — lives in the calendar tab as a simple date field + "logged" checkbox, defaulting to today but freely backfillable to any past date. Checking a date adds it to your log; unchecking removes it. A live status line in the same card shows fertility risk for whatever date is selected — before you log anything — so it works as a lookahead check, not just a record. Each logged date also shows up as a small dot on the calendar, colored by the same risk: red for "high risk" (fertile window: 5 days before your estimated ovulation day through 1 day after, the standard sperm/egg-viability window), lavender for "low risk" (everywhere else in your cycle). Risk is computed live from your current cycle settings rather than stored, so both the status line and the dots stay accurate if your average cycle length changes later. Synced via Supabase under a new `intimacy` column (a plain array of logged dates — no protected-sex tracking, no notes).

**Premature wrap registration bug fixed** — "register new wrap 🪷" was treating any period with an end date as eligible, including the most recent one. But a period and its cycle aren't the same thing: the cycle a period starts isn't complete until the *next* period begins, even after the period itself has ended (and it's still editable until then). The most recent period is now explicitly excluded from registration eligibility, and existing data self-heals on load — if the most recent period was already wrongly registered, it's automatically un-registered the next time the app loads, no manual cleanup needed.

**Calendar dot colors disambiguated** — illness dots and unprotected-sex "high risk" dots were both reddish/pink, and stress dots and unprotected-sex "low risk" dots were both a similar blue — easy to mix up at a glance. Illness is now teal, unprotected-low-risk is now lavender; stress (blue) and unprotected-high-risk (red) are unchanged and now clearly distinct from their former lookalikes. The calendar legend also now lists illness and high-stress dots, which it never documented before.

**Brush tracker calendar now matches the cycle app's** — circular day bubbles (was rounded squares), a large serif month label (was a tiny bold sans label), bordered square nav arrows (was flat borderless buttons), and the same day-of-week label sizing/header spacing as the main calendar. Own color palette and "today" outline-ring indicator stay as they were — this is about shape and scale reading as one app, not a palette swap.

---

## what's new — v2.5 · may 2026

**Event log** — tap 🗓️ in the calendar title to log illness or high stress events. Each event records a date range, phase context (calculated live, handles multi-phase spans), a fever flag for illness, and optional notes. Events appear as colored dots on the calendar grid and in an "events this cycle" section below it. Editable while the cycle is active; read-only once a new period starts. Surfaces in wrapped. Stored in Supabase under a new `events` column.

**Journal archive dates** — entries in the data tab now show the year for anything logged in a prior year. Current year stays clean.

**spottingInCycle bug fixed** — resolved a ReferenceError in wrapped rendering that could crash the wrapped detail view.

**wrapped registration order bug fixed** — "register new wrap 🪷" was registering the *most recent* eligible cycle instead of the oldest unregistered one, letting older cycles get skipped out of order. Registration now always picks the oldest completed, unregistered cycle first, keeping wraps chronological.

---

## what's new — v2.4 · may 2026

**Wrapped redesigned** — cycle summaries are now beautiful standalone HTML pages living in `/wraps/` in the repo, themed by month, built manually each cycle. Richer, more personal, and not limited by what an algorithm can infer. Each page includes: an opening observation, cycle stats and comparisons, a cycle map with energy curve, emotional texture anchored by your own journal quote, flow intensity bars, symptoms by phase, spotting with your notes verbatim, and a hormone arc — estrogen and progesterone inferred from your symptom pattern, annotated phase by phase.

**Wrapped archive** — tap the glowing 🩸 in the log tab to open your cycle archive. Each completed cycle shows period number, date range, and links out to its standalone page. The active period shows at the bottom as "in progress."

**Simplified registration** — when a new wrap is ready and pushed to GitHub, tap "register new wrap 🪷" in data → sync & backup. The period tints purple in the history list and the archive row appears. No Supabase involvement.

**History simplified** — flow-by-day pills removed from history entries. That detail lives inside each wrapped. History shows: dates, duration, period number. Border tints purple when a wrap exists for that period.

**Supabase `wraps` column removed** — wrapped data is no longer stored in the database. Wrap registration is stored in `settings.wrappedPeriods` alongside cycle and period length settings.

---

## what's new — v2.3 · may 2026

**Wrapped portal** — 🩸 in the log tab title glows softly, always tappable, opens the cycle archive. Nav dot on the log icon when wraps are registered.

**Period numbering** — history entries show period numbers throughout. "Cycle N" used for wrapped entries specifically.

---

## what's new — v2.2 · may 2026

**Wrapped** — when a new period starts, the previous cycle gets a summary. Spotting insights restructured. Symptoms by phase retired from insights tab — lives inside each wrapped instead.

---

## what's new — v2.1 · may 2026

**Spotting log** — accessible from the log tab in both active and inactive period states. Logs date, timing, color, and notes. No effect on cycle calculations.

**Spotting insights** — tap 🔮 in the insights title. Slides in as a full screen.

**Phase fix** — luteal holds past predicted end date until a period is actually logged.

**Edit lock** — only the most recent period is editable once a new cycle starts.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. Day-sensitive insight and lean into / go easy on lists. Journal prompt sits below — "what are you noticing today?" Optional, open text, stored against cycle day and phase.

**Period logging** — start a period, log daily flow, end it when done. Expecting state when past predicted start. Only the most recent period is editable.

**Spotting log** — accessible from the log tab in both active and inactive period states. Logs date, timing, color, and notes. No effect on cycle calculations.

**Event log** — tap 🗓️ in the calendar title. Log illness or high stress events with date range, fever flag (illness only), and notes. Phase context shown live as you pick dates. Events editable while the cycle is active, read-only once a new period starts. Full history always visible; current cycle events surface below the calendar grid.

**Wrapped** — one per completed cycle, written manually each month. Accessible via the glowing 🩸 in the log tab title. Standalone HTML pages in `/wraps/`, themed by month, with hormone arc and full cycle narrative.

**Symptom log** — 25 symptoms across four categories. Color-coded pills, navigable across the last 7 days.

**Journal** — open field on the today screen. Stored against cycle day and phase. Full archive in the data tab grouped by phase, with hormone table and science line per phase. Entries older than 3 days are read-only.

**Calendar** — full month view with phase colors, logged periods, predicted future cycles, and event dots (pink for illness, blue for stress). Monday-first.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, symptom patterns. Tap 🔮 for spotting insights.

**Data** — cloud sync via Supabase, local backup export, baseline reset, wrapped registration.

---

## data philosophy

**Predictive** (feeds cycle calculations): period start dates, period end dates, weighted averages for cycle and period length.

**Observational** (recorded, held, surfaces in wrapped — never touches calculations): symptoms, journal entries, spotting, events.

The app stays honest about what it knows vs what it's holding for you.

---

## event log lifecycle

- **While cycle is active** — full edit and delete access on any event from this cycle
- **When a new period starts** — events from the completed cycle lock and become read-only
- **In wrapped** — events are memorialized in the cycle narrative alongside spotting
- **All events page** — complete history across all cycles, always visible

Events spanning a cycle boundary are stored against the cycle they started in.

---

## wrapped workflow

Each cycle, when the next period starts:
1. Export a backup from data → sync & backup
2. Share it — we sit down together, review the data, write the wrap
3. A themed standalone HTML page gets built and named `cycle-N.html`
4. Push it to `/wraps/cycle-N.html` in the repo
5. In the app: data → sync & backup → tap "register new wrap 🪷"
6. Period entry tints purple in history, cycle appears in the archive

---

## repo structure

```
cycle/
├── index.html          ← the app
├── manifest.json
├── README.md
└── wraps/
    ├── cycle-1.html    ← may 2026
    ├── cycle-2.html    ← coming
    └── ...
```

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

**Columns:** `user_token`, `periods`, `symptoms`, `journal`, `spotting`, `events`, `brush_tracker`, `intimacy`, `active_period`, `settings`, `updated_at`

`settings` stores: `cycleLength`, `periodLength`, `wrappedPeriods` (array of period ids that have a standalone wrap file)

`brush_tracker` stores: `{ startDate, logs: { "YYYY-MM-DD": logType }, ss }` for the brush tracker feature — see "Brush tracker" above.

`intimacy` stores a flat array of `"YYYY-MM-DD"` strings — the dates unprotected sex was logged. See "Unprotected sex log" above.

**Both `brush_tracker` and `intimacy` must be added to the `cycle_data` table manually before use:**
```sql
alter table cycle_data add column brush_tracker jsonb;
alter table cycle_data add column intimacy jsonb;
```
PostgREST rejects the whole PATCH if the JSON body references a column that doesn't exist yet — so until these columns exist, **every save fails, not just the new features' data** (it silently falls back to the `cycleApp3` localStorage cache and lights up the sync-error dot). Run the migration above before using either feature.

---

## keep-alive

A GitHub Actions workflow (`supabase-ping.yml`) runs every Monday and Thursday to ping both the cycle and The Cloud Supabase projects, preventing free-tier pauses.

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

| app | repo | what it does |
|---|---|---|
| transitions | [leonnariley18-ui/transitions](https://github.com/leonnariley18-ui/transitions) | morning commute journal + night randomizer |
| The Cloud | [leonnariley18-ui/the-cloud](https://github.com/leonnariley18-ui/the-cloud) | private terpene journal |

---

## future

- Hormone chart in the app — estrogen and progesterone curves surfaced on the today screen, anchored to your actual cycle length with a marker showing where you are today
- Cycle × transitions integration — surface current phase on the transitions home screen
- Journal memory on today — surface what you wrote on this cycle day last month
- Wrapped comparisons across cycles — patterns that emerge across multiple wraps, including cycles where events were logged vs those where they weren't

---

*built entirely with [Claude](https://claude.ai) · single HTML file · no frameworks*
