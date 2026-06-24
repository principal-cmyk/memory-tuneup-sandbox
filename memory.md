# Team memory — everything in one place

(This file has grown over months. Decisions, lessons, and notes about the data are all jumbled together.)

## Why we do things the way we do
- We chose the one-page house format because managers only read the top of the report.
- We moved the report to **Monday** so it's ready for the Monday leadership call.
- We always drop empty rows first, because a single blank row once threw off the totals.
- We recompute every `total` ourselves instead of trusting the export's `total` column.

## Things that have gone wrong before
- **March:** a report showed wrong totals — the cause was empty rows we forgot to drop. That's now rule #1.
- **April:** we missed a huge outlier (a returned bulk order) and the headline number was way off. Always eyeball the top 3 before sending.
- We once emailed *last* week's chart by mistake — always rebuild the chart from this week's file.

## Where the numbers live
- Raw exports: `data/week-NN-raw.csv`
- Columns: `product`, `units`, `unit_price`, `total` (the `total` column is often blank — recompute it as units × unit_price).
- The house template (v2) lives in the team drive under `Templates/`.
- Migrating the team notes into this repo is **done** — finished last month.
