# cycle ✨

*a personal period and phase tracker, built for one person*

No account. No subscription. No ads. No data sharing. Just your cycle, your symptoms, and your patterns — getting more personal with every month.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. Tap the hero card to expand a full phase ring: four colored arcs built from your actual cycle lengths, with today marked on the ring.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date.

**Symptom log** — 19 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days. Every tap syncs instantly.

**Phase insights** — day-sensitive context that knows day 2 of luteal feels different from day 11. Collapsible deep-dive with hormonal info, energy tendencies, and what to lean into or go easy on.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first, obviously.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, and symptom patterns that build over time as you log.

---

## under the hood

Built on 21 cycles of real TempDrop data as the baseline. Averages update automatically as new cycles are logged. PIN-protected, cloud-synced via Supabase, hosted on GitHub Pages.

Built entirely with [Claude](https://claude.ai). Single HTML file. No frameworks.

---

## future updates

**Data-aware phase insights** — instead of generic phase descriptions, pull from logged symptom history to surface personal patterns. "last time you were in luteal you logged brain fog and intense cramps around day 11."

**Hormone chart** — a visual of estrogen, progesterone, LH, and FSH rising and falling across the cycle, embedded in the "about this phase" section. Educational and beautiful.

**Cycle length weighting** — weight recent cycles more heavily than older ones when calculating averages, so the predictions stay responsive to how your body is behaving right now rather than being anchored to older data.

**Phase transition animation** — a more ceremonial moment when you cross into a new phase. Currently a banner drop, could be something more immersive.

**Friend version** — a clean blank version of the app (no TempDrop baseline, default 28-day cycle) hosted on its own repository for sharing.

**Printed calendar companion** — a monthly printable tracker to run alongside the app for the slowdown, paper-based version of the same data.
