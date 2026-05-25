# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

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

**Spotting log** — log from the log tab anytime. Date, when, color with tap-to-explain dots, notes.

**Spotting insights** — tap 🔮 in the insights title. Slides in as a full screen.

**Phase fix** — luteal holds past predicted end date until a period is actually logged.

**Edit lock** — only the most recent period is editable once a new cycle starts.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. Day-sensitive insight, lean into and go easy on lists.

**Period logging** — start a period, log daily flow, end it when done. Expecting state when past predicted start. Only the most recent period is editable.

**Spotting log** — accessible from the log tab in both active and inactive period states. Logs date, timing, color, and notes. No effect on cycle calculations.

**Wrapped** — one per completed cycle, written manually each month. Accessible via the glowing 🩸 in the log tab title. Standalone HTML pages in `/wraps/`, themed by month, with hormone arc and full cycle narrative.

**Symptom log** — 25 symptoms across four categories. Color-coded pills, navigable across the last 7 days.

**Journal** — open field on the today screen. Stored against cycle day and phase. Full archive in the data tab grouped by phase.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, symptom patterns. Tap 🔮 for spotting insights.

**Data** — cloud sync via Supabase, local backup export, baseline reset, wrapped registration.

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

**Columns:** `user_token`, `periods`, `symptoms`, `journal`, `spotting`, `active_period`, `settings`, `updated_at`

`settings` stores: `cycleLength`, `periodLength`, `wrappedPeriods` (array of period ids that have a standalone wrap file)

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

- Hormone chart in the app — estrogen and progesterone curves surfaced on the today screen
- Cycle × transitions integration — surface current phase on the transitions home screen
- Journal memory on today — surface what you wrote on this cycle day last month
- Cycle length weighting — weight recent cycles more heavily than older data
- Wrapped comparisons across cycles — patterns that emerge across multiple wraps

---

*built entirely with [Claude](https://claude.ai) · single HTML file · no frameworks*
