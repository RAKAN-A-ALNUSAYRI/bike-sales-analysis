# Bike Sales Analysis

![preview](preview.jpg)

A bike retailer's order history — 60,919 rows — cleaned up and turned into a
dashboard that answers one question: where does the money actually come from?

## What I found

| | |
|---|---|
| Revenue | $81.0M |
| Orders | 60,919 |
| Units sold | 214,516 |
| Average order | $1,330 |

Bikes bring in 83% of the revenue, and North America brings in 84.4% of that.
So the business is really two bets, not a diversified catalogue. Accessories and
clothing look busy in the order count but barely register in revenue.

If I were handing this to an owner, that concentration is the first slide, not
the growth number.

## What I did

Started in Excel. The raw export had a row where the Region column said "Total"
and the Year column said 122021530 — a summary line that had been pasted into
the data. Left in, it inflates every total. I removed it and re-checked the
column types before doing anything else.

From there: pivot tables by category, region, model and colour, then a dashboard
on top of them.

Later I rebuilt the same numbers outside Excel. `backend/etl.py` reads the
workbook into SQLite, and `backend/api.py` serves the aggregates over HTTP, so
the same figures can drive a web page instead of living in one file. Both are
standard library only — no pip install.

## Run it

```bash
python backend/etl.py     # workbook -> SQLite
python backend/api.py     # serves http://localhost:8000/api/...
```

## Files

```
data/sales-dashboard.xlsx   the cleaned workbook and the dashboard
backend/etl.py              reads the workbook into SQLite
backend/api.py              serves the aggregated numbers
```

## Tools

Excel (pivot tables, Power Query), SQL, Python, SQLite

---
Rakan Ahmed Al-Nusayri — [github.com/RaKaN-DaTa](https://github.com/RaKaN-DaTa)
