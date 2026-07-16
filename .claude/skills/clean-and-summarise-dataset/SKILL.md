---
name: clean-and-summarise-dataset
description: Clean this week's raw sales export and write the summary in the house format. Use whenever a new data/week-NN-raw.csv lands and needs turning into the weekly report.
---

# Clean & summarise the dataset

## When to use it
Every week, as soon as a new `data/week-NN-raw.csv` export lands and needs turning into the weekly summary report. This is the first stage of the report pack — chart-building and the write-up/email happen after this.

## Steps
1. Load the week's raw export from `data/week-NN-raw.csv`.
2. Drop fully empty rows before doing anything else — a blank row once silently threw off the totals (see `memory/lessons.md`, March).
3. Recompute `total` for every remaining row as `units × unit_price`. Don't trust the export's own `total` column even when it's filled in — recompute all of them the same way.
4. Flag anything that looks off instead of guessing or silently dropping it — e.g. a row missing `units` or `unit_price` so it can't be recomputed, or a total that's wildly out of line with the rest (see `memory/lessons.md`, April: a missed outlier once threw off the headline number).
5. Round every dollar figure to a whole number, USD.
6. Write the summary in the house format from `CLAUDE.md`: headline total, top 3 products, anything unusual, one-line takeaway. Keep it to one page.

## Example
Input: `data/week-42-raw.csv`
```
product,units,unit_price,total
Notebook,120,2.5,300
Pen,400,0.5,
Stapler,,4.0,
Desk Lamp,15,18.0,270
,,,
Marker,60,1.2,72
Whiteboard,3,45.0,
Sticky Notes,250,1.0,250
```

Clean & recompute:
- Drop the fully empty row.
- Recompute totals: Notebook $300, Pen $200, Desk Lamp $270, Marker $72, Whiteboard $135, Sticky Notes $250.
- Flag **Stapler** — `units` is missing so its total can't be recomputed; excluded from the headline number until someone fills it in.

Resulting summary:
1. **Headline number:** $1,227 (sum of the six computable rows)
2. **Top 3 products:** Notebook ($300), Desk Lamp ($270), Sticky Notes ($250)
3. **Anything unusual:** Stapler row is missing a units figure — can't be totalled, needs a follow-up with whoever exported it
4. **Takeaway:** Steady week led by Notebook; one row needs a data fix before it's fully counted
