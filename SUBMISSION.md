# The Memory Tune-Up — submission

All five tasks from [`ASSESSMENT.md`](ASSESSMENT.md), one per video. Each entry gives the
one-line ask, the artifact Claude produced, and how it was checked.

> **On the "what I asked" lines:** tasks 1–5 were carried out across earlier sessions
> (2026-07-02 and 2026-07-16). The exact prompts weren't recorded at the time, so the lines
> below are reconstructed from what the work actually did, as documented in
> [`session-notes.md`](session-notes.md). They're accurate summaries of the ask, not verbatim quotes.

---

## 1. Weekly review · *(Weekly Maintenance)*

**What I asked:** "Review `CLAUDE.md`, `memory.md` and `tasks.md` — flag anything that's no longer true, close any task that's already finished, and show me what to cut. Then apply it."

**Produced:** edits to [`CLAUDE.md`](CLAUDE.md) and [`tasks.md`](tasks.md); reasoning recorded in [`session-notes.md`](session-notes.md) (session 2026-07-02).

### Stale / no-longer-true — found and fixed

| # | Item | Problem | Change made |
|---|------|---------|-------------|
| 1 | "Raw data arrives every **Tuesday** morning" | Contradicts the report shipping Monday — data can't land the day *after* it's needed | Replaced with a flagged `⚠️ day unconfirmed` placeholder; **not** guessed |
| 2 | "Always write the summary using the **report_v1** template" | The file's own Random notes said the team switched to v2 after the March mix-up | Now states **report_v2**, incl. the week-over-week line |
| 3 | "For database access, **ask Sarah** — she owns the data pipeline" | Sarah left the team in March | Now "self-serve" |
| 4 | Monday shipping was missing from the rules | The actual shipping day was buried in "Random notes" instead of being a rule | Promoted into Conventions / rules |

### Cut

| # | Item | Why |
|---|------|-----|
| 5 | "Coffee fund is Ali's desk drawer" | Irrelevant — the file itself said "(no idea why this is in here)" |
| 6 | "Reminder: set up a Monday-morning ping" | Duplicate of an existing `tasks.md` item |
| 7 | The whole "Random notes (added over time)" section | Dissolved once its true content was promoted and its junk cut — it was a dumping ground, which is what let items 1–3 go stale unnoticed |

### Finished task closed

| # | Item | Evidence |
|---|------|----------|
| 8 | "Migrate the team notes into this repo" | `memory.md` states outright: *"Migrating the team notes into this repo is **done** — finished last month."* Closed on corroboration, not on vibes. |

### Added

| # | Item |
|---|------|
| 9 | New `tasks.md` entry to confirm what day raw data actually arrives — the open question behind item 1 |

**Left open deliberately:** the Monday reminder, the week-42 summary, the April outlier re-check, and the design chart colours are all real work nobody has done. Ticking them to make the repo look finished would be inventing work.

---

## 2. Save, then start fresh · *(Fresh Sessions)*

**What I asked:** "Before I start a new session, write the key decisions and lessons from this work into a notes file so nothing is lost when the context resets."

**Produced:** [`session-notes.md`](session-notes.md) — two sessions, newest last.

It records decisions *with their reasoning* rather than a bare changelog, so a fresh session
can tell **why** a call was made and not silently reverse it. Load-bearing examples: the
data-arrival day was left flagged rather than guessed, and `memory.md` must stay deleted
because that deletion is the task-3 deliverable.

---

## 3. Split the memory · *(Lazy Loading)*

**What I asked:** "`memory.md` is one long jumbled file. Split it into a short index plus one file per topic — decisions, lessons, data — and make only the index load by default."

**Produced:**
- [`memory-index.md`](memory-index.md) — the one-page index
- [`memory/decisions.md`](memory/decisions.md) · [`memory/lessons.md`](memory/lessons.md) · [`memory/data.md`](memory/data.md)
- `memory.md` deleted
- [`CLAUDE.md`](CLAUDE.md) § Memory now points at the index

**Check:** the split was diffed against the original `memory.md`. Its three sections map 1:1
onto the three topic files — 4, 3 and 4 bullets respectively — with **nothing dropped and
nothing invented**. The index names each file *and* says when to open it, which is what makes
the loading actually lazy rather than just tidy.

---

## 4. Write a skill file · *(The Skill File)*

**What I asked:** "Turn 'clean & summarise the dataset' into a skill file — name, when to use it, the steps, and one worked example."

**Produced:** [`.claude/skills/clean-and-summarise-dataset/SKILL.md`](.claude/skills/clean-and-summarise-dataset/SKILL.md)

All four required parts present, scoped to that one job (it states outright that the chart and
email come later). Each step carries the reason it exists, cross-referenced to the incident in
`memory/lessons.md` that caused it.

**Check — the worked example was recomputed independently from [`data/week-42-raw.csv`](data/week-42-raw.csv):**

```
Notebook 300 · Pen 200 · Desk Lamp 270 · Marker 72 · Whiteboard 135 · Sticky Notes 250
Stapler  → FLAGGED (units missing, unit_price 4.0 → not computable)
(blank row) → dropped
HEADLINE = 1227
```

Matches the skill's stated $1,227 headline and its top 3 (Notebook $300, Desk Lamp $270,
Sticky Notes $250) exactly. Re-verify if the sample data ever changes.

---

## 5. Skill or agent? · *(Skills vs. Agents)*

**What I asked:** "Sort the three repeated tasks in the README as skill or agent with one line of reasoning each, then build one of them."

**Produced:** the sort in [`skills-vs-agents.md`](skills-vs-agents.md); the agent built at [`.claude/agents/report-pack.md`](.claude/agents/report-pack.md).

| Repeated task | Verdict | Why |
|---|---|---|
| Clean & summarise the dataset | **Skill** | Fixed recipe; steps don't branch on what the data says |
| Build the weekly bar chart | **Skill** | One fixed output, same shape weekly, no judgment calls |
| Produce the full report pack | **Agent** | Chains the others *and* must decide mid-task — note a flagged row and proceed, or stop and escalate? |

**Rule of thumb used:** *does this task have to make a decision partway through that changes
what it does next?* No → skill. Yes → agent.

The agent was chosen over the chart skill because the skill half of the distinction was
already demonstrated by task 4 — the two together show both sides. Its two guardrails sit
exactly where judgment is required: an unrecomputable row must be explicitly noted-and-passed
or escalated (never silently dropped or guessed), and the email is **drafted but never sent**,
because sending is externally visible and hard to undo.

Structurally, the agent *calls* the task-4 skill for its first stage instead of restating those
steps — the recipe lives in one place, the agent supplies only the judgment. That separation is
the point the task is testing.

---

## Status

All five deliverables complete and committed. The remaining open items in
[`tasks.md`](tasks.md) are real team to-dos needing a human — chiefly confirming the actual
data-arrival day, which is still flagged unconfirmed in `CLAUDE.md`.
