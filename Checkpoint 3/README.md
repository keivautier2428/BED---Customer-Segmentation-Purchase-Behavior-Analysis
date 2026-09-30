# Checkpoint 3 — BI Dashboard Development
Semi-Final Period • Weeks 10–13 • 100 Points

## What's in this folder

| File | Task | Status |
|---|---|---|
| `Task 3.1 - Dashboard Blueprint.md` | 3.1 Dashboard Design Blueprint | Draft ready — review, then copy into your report |
| `Task 3.3 - Clustering & Segmentation.md` | 3.3 Data Mining: Clustering/Segmentation | **Done** — real analysis run on the Checkpoint 1 dataset |
| `Power BI Build Guide.md` | 3.2 Interactive BI Dashboard | Step-by-step instructions for building the actual `.pbix` |
| `customer_segments.csv` | supports 3.2 & 3.3 | 189 customers, each labeled with its segment |
| `segment_summary.csv` | supports 3.3 | One row per segment: size, spend, revenue share |
| `customer_segments_scatter.png` | supports 3.3 | The segmentation chart, ready to paste into your report |
| `powerbi_data/` | supports 3.2 | 5 clean CSVs (customers, products, invoices, invoice_items, customer_segments) — import these straight into Power BI |
| `customer_features.csv` | working file | Per-customer numbers before segment labels were assigned |

## Why CSVs instead of connecting Power BI to MySQL directly

Power BI can connect straight to MySQL, but that needs the MySQL ODBC connector installed on
whichever machine opens the `.pbix` — including the instructor's, during grading. Plain CSVs open
on any machine with zero setup, and the numbers are identical since they're exported straight from
the same cleaned Checkpoint 1 data. Use the `powerbi_data/` folder as your source.

## What's still on you (can't be done from here)

Power BI Desktop and Tableau are GUI applications — building the actual dashboard, taking the
blueprint screenshots, and doing the live in-class presentation (Task 3.4) has to happen on your own
machine. The `Power BI Build Guide.md` walks through every step and gives you the exact KPI/DAX
formulas to paste in, so it should mostly be clicking and copy-pasting rather than figuring things
out from scratch.

## Suggested order of work
1. Read `Task 3.1 - Dashboard Blueprint.md`, adjust anything you'd lay out differently, screenshot or
   redraw it as your submitted wireframe.
2. Follow `Power BI Build Guide.md` to build the 3-page dashboard using the files in `powerbi_data/`.
3. Read `Task 3.3 - Clustering & Segmentation.md` for the write-up — the numbers and chart are already
   final, just add the dashboard screenshot once page 3 is built.
4. Rehearse Task 3.4 using the same "who presents what" split as `RECORDING_GUIDE.md` in the project
   root — Nicka (data), Jeziel (dashboard/visuals), Jennilyn (segmentation numbers) — since the rubric
   requires every member to speak.
