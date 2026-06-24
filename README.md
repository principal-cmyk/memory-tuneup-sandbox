# Weekly Sales Summary — practice project

This is the little project Ali's team uses to turn each week's raw sales numbers into one clean summary report. **You've just taken over maintaining it** — and, like most real projects, its notes have gotten messy over time.

Your task (Part B of the module) is to use **Claude Code** to tidy how this project remembers things, and to capture the work the team repeats every week. You don't fix any of this by hand — you tell Claude what you want and let it do the work.

## What the project does
Every week a raw sales export (`data/week-NN-raw.csv`) lands. The team turns it into one clean summary in the house format, makes a chart, and emails it to the team.

## Tasks the team repeats every single week
1. **Clean & summarise the dataset** — drop empty rows, recompute the totals, flag anything that looks off, then write the summary in the house format.
2. **Build the weekly bar chart** from the cleaned numbers.
3. **Produce the full report pack** — clean → chart → write-up → email the team, deciding what to do as it goes.

## Files in this project
- `CLAUDE.md` — the project's rules & context for the AI (it's grown messy).
- `memory.md` — everything the team has learned and decided, all in one long file.
- `tasks.md` — the running to-do list.
- `data/week-42-raw.csv` — a sample raw export to work on.

## How to start
1. Open this folder in Claude Code.
2. Work through the five tasks in `ASSESSMENT.md` (or your facilitator's brief), one per video.
3. Submit what Claude produced for each.
