# Bike Sales Analysis Dashboard

تحليل مبيعات درّاجات — 60,919 طلبًا، من التنظيف حتى لوحة تفاعلية.

![preview](preview.jpg)

**The question:** Where does the revenue actually come from — and where is
it dangerously concentrated?

**What I did:**
- Cleaned 60,919 raw order rows in Excel (found and removed a stray "Total"
  summary row mixed into the raw data — a common real-world data-quality bug)
- Built pivot tables by category, region, model, and colour
- Rebuilt the dashboard from scratch with a Python ETL script + a small
  local API (`backend/`, standard library only) so the same numbers can
  power a live web dashboard, not just a static Excel sheet
- The live, filterable version of this exact dashboard is embedded in my portfolio site (not yet published — coming soon)

**What I found:**
| Metric | Value |
|---|---|
| Total revenue | $81.0M |
| Orders | 60,919 |
| Units sold | 214,516 |
| Average order | $1,330 |

Bikes alone carry **83% of total revenue**, and North America accounts for
**84.4%** of it — growth is currently riding on two narrow bets (one product
line, one region), which is the headline risk worth flagging to a business
owner reading this dashboard.

**Tools:** Excel (Pivot Tables, Power Query), Python (stdlib `sqlite3`),
SQL, a small self-built HTTP API

## Run it yourself

```bash
python backend/etl.py     # builds the SQLite database from the Excel file
python backend/api.py     # serves it at http://localhost:8000/api/...
```

No dependencies — pure Python standard library.

## Files

```
data/sales-dashboard.xlsx   the cleaned workbook with the rebuilt dashboard
backend/etl.py               reads the Excel file into SQLite
backend/api.py                small local API serving the aggregated numbers
```

---
Rakan Ahmed Al-Nusayri · [portfolio](https://github.com/RaKaN-DaTa) · rakanalnsyry8@gmail.com
