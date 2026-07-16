# CLAUDE.md — Weekly Sales Summary

## About this project
We turn each week's raw sales export into one clean summary report — the same shape, every week.

## Conventions / rules
- Raw data lands in `data/` — ⚠️ **day unconfirmed**: previously said "Tuesday," but that can't be right now that the report ships Monday. See open task to confirm.
- Always write the summary using the **report_v2** template — adds a "week-over-week change" line at the top.
- Currency is USD; round to whole numbers.
- Drop empty rows before doing any totals.
- Database/pipeline access is self-serve (Sarah, who used to own it, left the team in March).
- Keep the summary to one page.
- The report ships **Monday morning** so it's ready for the Monday leadership call.

## House format for the summary
1. Headline number (total sales)
2. Top 3 products
3. Anything unusual (outliers)
4. One-line takeaway

## Memory
Team decisions, lessons, and data notes live in [`memory-index.md`](memory-index.md) — read that first. It points to topic files under `memory/` that only need opening when the task actually touches that topic.
