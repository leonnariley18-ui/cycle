# leonnariley18-ui/cycle

*a personal period tracker built on real data, built with intention, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## what's new — v4 · november 2026

**Commitments** — a new tab (renamed from Playbook, which now lives further down the same page) for self-chosen, strict challenges. Pick a standard (Just Don't Skip, Brush, or Intentional Brushing) and a length, and the app holds you to it exactly — no grace, no pause, unlike the regular tier streak. Only one rule underneath it all: meet or exceed the standard's minimum every required night and you pass; drop below it once and you fail, immediately. Nights wait for you rather than auto-failing from silence — a commitment only resolves when you actually log the specific date it's waiting on, evaluated strictly in order even if you backfill out of sequence — except if an unresolved night ever gets swallowed into a Recommit's estimate, since that can never be a real log. Dashboard shows a short nudge naming the exact date still needed, plus a tappable active-commitment card between the calendar and stats. Commitment history lives as three collapsible groups, one per standard, each with every attempt's date, terms, and outcome. Five new achievements ship alongside it.

**Achievements page reworked** — every badge, locked or earned, is now tappable into a detail sheet. Locked badges show their existing requirement text; earned repeatables show their count once (no redundant restating); Cleanings and Recommits show their real dates, since that's genuinely new information the badge itself doesn't show. Milestones and achievements sections are now collapsible, reusing the same accordion already used in Playbook/Commitments, since the list has grown to 24 badges total.

**Simple Mode** — a toggle inside Data → sync & backup that collapses the app down to just the essentials: phase/period tracking, the calendar, spotting and unprotected-sex logging, and the brush tracker. Journal, symptom logging, insights, and wrapped stay fully intact underneath — nothing is deleted or touched — they're just tucked out of the way while the toggle is on. Nav shrinks to Home and Data; the real calendar card itself (not a shortcut) sits right on Home, instantly viewable, with quick shortcuts to Log and the brush tracker below it. Data tab shows only the sync & backup bubble — the journal-by-phase history is hidden too. Switches instantly, no reopening the app, and the setting is remembered like any other.

**Sunday digest now covers Commitments** — a commitment accepted, passed, or failed during the week gets its own "Commitments this week" line (standard, length, outcome).

**"Earned this week" is now actually complete** — it used to be a small hand-picked list (First Night, Week 1, Tier Up, Perfect Week) that silently missed everything else, including Cleanings, Recommits, long streaks, and the new commitment achievements. It now works by comparing your real achievement state at the start and end of the week, so every milestone and repeatable — old or new — shows up in the digest the week it's actually earned, with a ×N if a repeatable landed more than once.

---

## what's new — v3.1 · october 2026

**Recommit** — a button on Science for coming back after a real gap (9+ nights with nothing logged at all — not just missed nights, actual silence). Shows you the gap plainly and asks for one honest estimate ("out of these N nights, how many did you actually brush?") instead of making you backfill the calendar. The guess blends into your tier and baseline score like real nights would, but can never unlock a streak achievement on its own — only genuinely logged nights do that. Estimated nights are always visually distinct (a dashed ring on the calendar, a clearly labeled day-detail view) so a guess never reads back as a real memory. New permanent "Recommits" counter on Awards, two new achievements, and a quieter Sunday digest treatment for any week that included one — confetti still plays in full for a genuinely earned badge that week, with a soft glow following after, but a recommit on its own gets the glow alone, never fireworks. Recommit also now finds a big gap anywhere in your history, not just one still touching today — so logging recent nights no longer strands an older unresolved gap out of reach.

**CloSYS nights now pause your streak instead of breaking it** — reviewing real log data showed CloSYS-only/CloSYS+floss nights (real oral-care actions, already worth fewer points than a full brush) were resetting tier progress exactly like a true skipped night. Only logging nothing at all still breaks a streak; a CloSYS night now just holds it in place, and your next real brush night continues right where it left off. Points are untouched either way — this only changes what counts toward tier climbing and streak achievements (Streak: 7/14/30/66/90, Tier Up, The Comeback), which still only advance on genuine brush nights, never on a CloSYS night. The "nights without brushing" science messaging is deliberately unchanged — a CloSYS night is still honestly reported as not-brushing there, since that distinction is about biology, not tier progress.

---

## what's new — v3 · august 2026

**Brush tracker** — a nightly dental habit tracker behind the glowing 🗄️ in the data tab. 7 habit-formation tiers, tier/slip-based science messaging, weekly Sunday digest with confetti, achievements, and a routine playbook. Own bottom nav (Dashboard / Science / Playbook / Awards), visually aligned with the rest of the app (calendar shape, cards, buttons, headers, layout all match cycle's own conventions; own peach/mauve/lime palette kept). Independent from period data. Synced via Supabase under a new `brush_tracker` column; confetti is bundled locally so it works offline.

**Unprotected sex log** — a date field + "logged" checkbox in the calendar tab, backfillable to any past date. Shows a live fertility-risk line (before you log) and a colored calendar dot after: red for high risk (5 days before estimated ovulation through 2 days after), lavender for low risk. Synced via Supabase under a new `intimacy` column.

**Calendar dot colors disambiguated** — illness (now teal) and stress dots were too close to the new unprotected-sex risk colors. Legend now documents illness/stress dots too.

**Wrap registration bug fixed** — the most recent period could get wrapped/cycle-numbered before its cycle was actually complete (a period isn't the same as its cycle, which runs until the *next* period starts). Existing bad data self-heals on load.

**Evening date bug fixed** — `fmt()` built date strings via `toISOString()`, which converts to UTC first. In any timezone behind UTC, after roughly 8pm local the date would silently roll to tomorrow — most visibly, starting a period in the evening could pre-fill and save tomorrow's date, showing "day 0" and blocking flow logging until the date passed. Rewrote `fmt()` (and the brush tracker's equivalent `btFd()`) to build the string from local date parts instead. If you already have a period recorded with a start date one day ahead of when you actually started it, edit it back via Log → History → ✏️.

**Brush tracker fixes** — host nav bar no longer blocks the tracker's own nav; onboarding's deficit backfill no longer pre-logs tonight if your start date is very close; background lightened for contrast; playbook quick-reference cards restructured for readability; playbook timers now hold the screen awake and stay accurate through backgrounding; calendar now opens to the actual current month instead of resetting to your start month every time, and has a "today" button to jump back after browsing other months.

**Professional cleaning logging** — a button on Science tops off your baseline meter to your current tier's max, representing the real reset a dental scaling/cleaning gives your mouth (removes calculus that brushing alone can't touch). Doesn't touch your tier or streak — those track nightly consistency, not a dentist visit — and doesn't rewrite past nights. Comes with a milestone ("Professional Clean") and a repeatable achievement ("Deep Clean ×N").

**Tier grace mechanism** — a missed night used to send your tier all the way back to Tier 1, regardless of how long a streak preceded it. That's harsher than the research supports: habit-formation and lapse literature treats a single missed cue as a gradual step down in automaticity, not a full reset, and punishing it as one risks manufacturing the exact discouragement that causes real relapse. Deeper tiers now resist drops more, in line with the same literature — it takes progressively more consecutive missed nights to knock a level off the further along you are (a miss at Tier 1 still drops immediately; a miss at Tier 5 needs a full week of consecutive misses before it costs even one level). Tier climbs back only as you rebuild a real streak — no free recovery from a single make-up night. Your nightly points (the baseline meter within a tier) still take their usual hit on a missed night — this only changes the coarser tier classification, not the fine-grained score.

---

## what's new — v2 · may 2026

**Spotting** — a log (date, timing, color, notes — no effect on cycle calculations) accessible from the log tab in both active and inactive period states, plus a spotting-insights screen (🔮 in the insights title).

**Wrapped introduced, then redesigned** — a per-cycle summary when a new period starts, portal'd via a glowing 🩸 in the log tab. Quickly outgrew an algorithmic summary and became hand-built: standalone, month-themed HTML pages in `/wraps/`, each with an opening observation, cycle stats and comparisons, a cycle map with energy curve, emotional texture anchored by your own journal quote, flow intensity bars, symptoms by phase, spotting with your notes verbatim, and an inferred hormone arc. Registration simplified to one tap ("register new wrap 🪷" in data → sync & backup) once a page is pushed to the repo — no Supabase involvement; tracked instead in `settings.wrappedPeriods`. History entries show period numbers and tint purple once wrapped; "Cycle N" used for wrapped entries specifically. Symptoms-by-phase moved out of Insights and into wrapped.

**Event log** — tap 🗓️ in the calendar title to log illness or high stress events (date range, live phase context, a fever flag for illness, optional notes). Shows as colored calendar dots and in an "events this cycle" section; editable while the cycle is active, read-only once a new period starts; surfaces in wrapped.

**Smaller fixes** — luteal now holds past its predicted end date until a period is actually logged; only the most recent period is editable once a new cycle starts; journal archive entries show the year once they're from a prior year; a wrapped-rendering crash (`spottingInCycle` ReferenceError) was fixed; wrap registration now always picks the oldest completed, unregistered cycle first instead of the most recent, keeping wraps chronological.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. Day-sensitive insight and lean into / go easy on lists. Journal prompt sits below — "what are you noticing today?" Optional, open text, stored against cycle day and phase.

**Period logging** — start a period, log daily flow, end it when done. Expecting state when past predicted start. Only the most recent period is editable.

**Spotting log** — accessible from the log tab in both active and inactive period states. Logs date, timing, color, and notes. No effect on cycle calculations.

**Event log** — tap 🗓️ in the calendar title. Log illness or high stress events with date range, fever flag (illness only), and notes. Phase context shown live as you pick dates. Events editable while the cycle is active, read-only once a new period starts. Full history always visible; current cycle events surface below the calendar grid.

**Wrapped** — one per completed cycle, written manually each month. Accessible via the glowing 🩸 in the log tab title. Standalone HTML pages in `/wraps/`, themed by month, with hormone arc and full cycle narrative.

**Symptom log** — 25 symptoms across four categories. Color-coded pills, navigable across the last 7 days.

**Journal** — open field on the today screen. Stored against cycle day and phase. Full archive in the data tab grouped by phase, with hormone table and science line per phase. Entries older than 3 days are read-only.

**Calendar** — full month view with phase colors, logged periods, predicted future cycles, event dots (teal for illness, blue for stress), and unprotected-sex dots (red for fertile-window risk, lavender otherwise). Monday-first.

**Unprotected sex log** — date + "logged" checkbox in the calendar tab, backfillable to any past date. Live fertility-risk line before you log, colored calendar dot after.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, symptom patterns. Tap 🔮 for spotting insights.

**Data** — cloud sync via Supabase, local backup export, baseline reset, wrapped registration.

**Brush tracker** — a separate nightly dental habit tracker behind the glowing 🗄️ in the data tab. Own tiers, science messaging, achievements, and playbook — see "what's new" above. Fully independent of period data.

---

## data philosophy

**Predictive** (feeds cycle calculations): period start dates, period end dates, weighted averages for cycle and period length.

**Observational** (recorded, held, surfaces in wrapped — never touches calculations): symptoms, journal entries, spotting, events, unprotected sex log.

**Out of scope** (no relationship to cycle data at all): brush tracker — its own tiers, streaks, and habit data, tracked independently of period/cycle calculations.

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
├── vendor/
│   └── confetti.min.js ← bundled locally for the brush tracker, so it works offline
└── wraps/
    ├── cycle-1.html    ← may 2026
    ├── cycle-2.html    ← coming
    └── ...
```

---

## tech stack

| layer | tool |
|---|---|
| language | vanilla HTML/JS — single-file app, one small vendored library |
| database | Supabase (PostgreSQL) |
| auth | PIN-based (hashed token) |
| hosting | GitHub Pages |

---

## infrastructure

**Supabase project:** `sdvmycusfyavsuvsjvrv`
**Table:** `cycle_data`

**Columns:** `user_token`, `periods`, `symptoms`, `journal`, `spotting`, `events`, `brush_tracker`, `intimacy`, `active_period`, `settings`, `updated_at`

`settings` stores: `cycleLength`, `periodLength`, `wrappedPeriods` (array of period ids that have a standalone wrap file)

`brush_tracker` stores: `{ startDate, logs: { "YYYY-MM-DD": logType }, ss, cleanings, estimatedDates, recommits }` for the brush tracker feature — see "Brush tracker" above.

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
- Bedtime reminder for the brush tracker if tonight isn't logged yet (needs a service worker for real push notifications)
- Symptom correlation with fertile-window logging in insights, now that unprotected sex, illness, and stress are all timestamped against phase

---

*built entirely with [Claude](https://claude.ai) · single HTML file · no frameworks*
