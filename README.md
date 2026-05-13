# cycle ✨

*a personal period and phase tracker, built for one person*

No account. No subscription. No ads. No data sharing. Just your cycle, your symptoms, and your patterns — getting more personal with every month.

---

## what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. A day-sensitive insight tells you what's happening right now, not just what phase you're in. Lean into and go easy on lists give you something actionable, not just informational.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date.

**Symptom log** — 19 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days. Every tap syncs instantly.

**Journal** — a small open field on the today screen: *"what are you noticing today?"* Write a line or two when something stands out, skip it when nothing does. Entries are stored against your exact cycle day and phase. The data tab holds your full archive, grouped by phase — each section leads with a clinical hormone readout and a science line, so your words sit alongside the biology that likely drove them. Edit window is today plus three days back. After that, entries are sealed and read-only.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first, obviously.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, and symptom patterns that build over time as you log.

**Data** — cloud sync via Supabase, local backup export, and a baseline reset. All tucked into a collapsible so the journal stays front and center.

---

## under the hood

Built on 21 cycles of real TempDrop data as the baseline. Averages update automatically as new cycles are logged. Phase day ranges in the journal tab are calculated dynamically from your actual average cycle length — so they're always yours, not generic. PIN-protected, cloud-synced via Supabase, hosted on GitHub Pages.

Built entirely with [Claude](https://claude.ai). Single HTML file. No frameworks.

---

*built with intention · used with consistency · trusted over time*

---

## future updates

**Hormone chart** — a visualization of estrogen, progesterone, LH, and FSH as overlapping curves across your full cycle. Anchored to your actual cycle length, with a marker showing where you are today. Soft colors matching the phase palette, more art book than medical textbook. The journal connection is the interesting part: tap a point on the curve and see what you wrote that day, or what the app told you. A timeline of your body and your experience of it simultaneously.

**Cycle-aware energy forecast** — a simple "this week" view that translates your phase position into an energy and capacity read. Not what phase you're in, but what that means for how you might want to structure your days.

**Journal memory on today** — once a few cycles of entries accumulate, surface a quiet line on the today screen: *"last cycle on this day you wrote: —"* Pattern discovery in the moment, not just in the archive.

**Cycle length weighting** — weight recent cycles more heavily than older ones when calculating averages, so predictions stay responsive to how your body is behaving right now rather than being anchored to older data.

**Phase transition animation** — a more ceremonial moment when you cross into a new phase. Currently a banner drop, could be something more immersive.

**Friend version** — a clean blank version of the app (no TempDrop baseline, default 28-day cycle) hosted on its own repository for sharing.

**Printed calendar companion** — a monthly printable tracker to run alongside the app for the slowdown, paper-based version of the same data.
