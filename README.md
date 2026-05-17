# leonnariley18-ui/cycle

*two personal apps, one repo — built with intention, used with consistency, trusted over time*

No accounts. No subscriptions. No ads. No data sharing. PIN-protected, cloud-synced, hosted on GitHub Pages.

---

## apps in this repo

### cycle ✨ — `index.html`

A personal period and phase tracker built on 21 cycles of real TempDrop data. Tracks symptoms, logs flow, journals against cycle day and phase, and gets more accurate with every month.

**Live at:** `https://leonnariley18-ui.github.io/cycle/`

### transitions 🚇 — `transitions.html`

A morning commute journal. Built for the train ride between your private world and the performance of the day. Vibe check → question selection → writing space. Anchor question every morning, one more question pulled from the bank based on how you're arriving, free-form writing with full formatting tools.

**Live at:** `https://leonnariley18-ui.github.io/cycle/transitions.html`

---

## cycle — what it does

**Today** — greets you by time of day, shows your current phase and where you are within it. A day-sensitive insight tells you what's happening right now, not just what phase you're in. Lean into and go easy on lists give you something actionable.

**Period logging** — start a period, log daily flow, end it when done. An expecting state appears when you're past your predicted start date.

**Symptom log** — 19 symptoms across four categories (physical, energy, mood, and the good stuff). Color-coded pills, navigable across the last 7 days.

**Journal** — a small open field on the today screen. Entries stored against your exact cycle day and phase. The data tab holds your full archive grouped by phase — each section leads with a hormone readout and a science line. Edit window is today plus three days back. After that, entries are sealed and read-only.

**Calendar** — full month view with phase colors, logged periods, and predicted future cycles. Monday-first.

**Insights** — cycle stats, phase length breakdown, upcoming predictions, and symptom patterns that build over time.

**Data** — cloud sync via Supabase, local backup export, and a baseline reset.

---

## transitions — what it does

**Home** — anchor question front and center with its full reasoning paragraph, so you remember why you're here before you even begin. Entry count (not a streak — no pressure). Collapsible library of past entries below.

**Vibe check** — how are you arriving today? Scattered (too much in the present), heavy (something already landed), anxious (bracing for what's coming), clear (present and ready), or okay (just here). Your vibe shapes which questions surface first.

**Question selection** — anchor always loads first. One more question from the bank, surfaced by vibe, with an info button that explains exactly what each question is doing for your nervous system. Cap of anchor + one — enough for a commute, never overwhelming.

**Writing space** — free-form contenteditable field with full formatting: text font switcher (Playfair, Montserrat, DM Sans, Poppins, Raleway, Merriweather, Roboto Slab), display font switcher for titles (Playfair, Oswald, Bebas Neue, Chewy, Bagel Fat One, Dancing Script), bold, italic, bullet list, font size, text color, and highlight. Toolbar collapses and pulls out with one tap.

**Save draft** — mid-entry save that preserves everything (vibe, question, title, writing, font choices) so you can lock your phone, switch trains, or get interrupted and come back exactly where you left off. Discard button on the home screen clears it with one confirmation tap.

**Library** — search by keyword, filter by vibe and category, read past entries in full (read-only). Export to .txt for sharing and pattern analysis.

**Auto-generated entry context** — every entry logs "arrived heavy · wrote through protection + release" so when you read it back months later the full picture is there without any extra effort.

---

## question bank

The transitions question bank has 8 questions across 7 categories, surfaced by vibe. The anchor question lives outside the bank — it appears every single morning automatically, before anything else.

**anchor — every morning, always:**
*What do I want to protect about my energy today?* — category: protection

**second question — picked from the bank based on your vibe:**

| # | question | category | surfaces for |
|---|---|---|---|
| Q1 | What would good enough look like today? | self-compassion | scattered · heavy · okay |
| Q2 | What's one thing I'm bringing my full attention to today? | intention | scattered · clear |
| Q3 | What do I want to leave at the door before I walk in? | boundary | anxious · okay |
| Q4 | How do I want to feel by the time I arrive? | body scan | anxious |
| Q5 | What moment today am I most looking forward to? | presence | clear · okay |
| Q6 | Where am I most likely to lose myself today, and can I stay a little more present there? | awareness | clear |
| Q7 | What's one thing already in place today that I don't have to figure out? | grounding | scattered · anxious |
| Q8 | Is there anything I'm carrying from yesterday that isn't mine to carry today? | release | heavy |

---

## shared infrastructure

Both apps live in the same GitHub repo and share the same Supabase project. They use separate tables and never touch each other's data.

| | cycle | transitions |
|---|---|---|
| file | `index.html` | `transitions.html` |
| manifest | `manifest.json` | `transitions-manifest.json` |
| icons | `icon-192.png` · `icon-512.png` | `transitions-icon-192.png` · `transitions-icon-512.png` |
| Supabase table | `cycle_data` | `transitions_data` |
| auth | PIN → hashed token | same PIN → same token |

**Supabase project:** `sdvmycusfyavsuvsjvrv`

Both apps use the same PIN. Same PIN, same token derivation, same user across both apps. One PIN unlocks everything.

---

## installing on device

**Android (Chrome)**
1. Open Chrome → navigate to the app URL
2. Tap ⋮ menu → Add to Home Screen → Add

**iPhone/iPad (Safari only)**
1. Open Safari → navigate to the app URL
2. Tap Share → Add to Home Screen → Add

---

## tech stack

Both apps: vanilla HTML/JS · no frameworks · single file each · Supabase (PostgreSQL) · GitHub Pages

---

## future

**cycle**
- Hormone chart — estrogen, progesterone, LH, FSH as overlapping curves across the full cycle, with journal entries surfaced at the point you wrote them
- Cycle-aware energy forecast — a "this week" view that translates phase position into capacity
- Journal memory on today — surface what you wrote on this cycle day last month
- Cycle length weighting — weight recent cycles more heavily than older data
- Friend version — a clean blank version with no TempDrop baseline for sharing

**transitions**
- Anchor rotation — anchor question revisits seasonally based on what patterns emerge in the writing
- Pattern insights — over time, surface which vibes cluster on which days, which question categories you reach for most
- cycle × transitions connection — surface your current phase on the transitions home screen so the morning practice is informed by where you are in your cycle
- Morning question bank expansion — new questions added as the practice evolves

---

*built entirely with [Claude](https://claude.ai) · single HTML files · no frameworks*
