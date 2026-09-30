# Power BI Build Guide — Task 3.2
Follow these steps in order in Power BI Desktop. Everything you need to paste in is included —
mostly copy-paste and click, following the layout from `Task 3.1 - Dashboard Blueprint.md`.

---

## Step 1 — Load the data

1. Open Power BI Desktop → **Get Data** → **Folder**.
2. Point it at the `powerbi_data/` folder (next to this guide). It contains 5 CSVs:
   `customers.csv`, `products.csv`, `invoices.csv`, `invoice_items.csv`, `customer_segments.csv`.
3. If it offers "Combine & Transform," don't — instead use **Get Data → Text/CSV** and load each of
   the 5 files individually, so you get 5 separate tables.
4. In Power Query Editor, confirm column types: `invoice_date` → Date/Time, `unit_price` /
   `line_total` / `total_spend` / `avg_order_value` → Decimal Number, `is_cancelled` → Whole Number.
   Click **Close & Apply**.

## Step 2 — Build relationships (Model view)

Match the ERD from Checkpoint 1, plus one link for the segments table:

| From | To | Cardinality |
|---|---|---|
| `customers[customer_id]` | `invoices[customer_id]` | 1 → many |
| `invoices[invoice_no]` | `invoice_items[invoice_no]` | 1 → many |
| `products[stock_code]` | `invoice_items[stock_code]` | 1 → many |
| `customers[customer_id]` | `customer_segments[customer_id]` | 1 → 1 |

Power BI usually auto-detects these — go to **Model** view and check the lines match the table
above; drag to connect any it missed.

## Step 3 — Create the KPI measures

Go to `invoice_items` table → **New Measure**, and add each of these one at a time:

```dax
Total Revenue =
CALCULATE(
    SUMX(invoice_items, invoice_items[quantity] * invoice_items[unit_price]),
    invoices[is_cancelled] = 0
)
```

```dax
Total Orders =
CALCULATE(
    DISTINCTCOUNT(invoices[invoice_no]),
    invoices[is_cancelled] = 0
)
```

```dax
Total Customers = DISTINCTCOUNT(customers[customer_id])
```

```dax
Avg Order Value = DIVIDE([Total Revenue], [Total Orders])
```

```dax
Cancelled Order Rate =
DIVIDE(
    CALCULATE(COUNTROWS(invoices), invoices[is_cancelled] = 1),
    COUNTROWS(invoices)
)
```

Expected values (for checking your work once built): Total Revenue ≈ **£106,185.83**, Total Orders =
**271**, Total Customers = **207**, Avg Order Value ≈ **£391.83**, Cancelled Order Rate ≈ **9.7%**.

## Step 4 — Page 1: Executive Summary

1. Add a **Card** visual for each of: Total Revenue, Total Orders, Total Customers, Avg Order Value.
2. Add a **Clustered Bar Chart**: Axis = `customers[country]`, Value = `[Total Revenue]`. Sort
   descending.
3. Add a **Bar Chart**: Axis = `products[description]`, Value = `[Total Revenue]`, filter to Top N =
   10 (right-click the field well → Top N).
4. Add a **Slicer**: field = `customers[country]`. Place it at the top of the page.

## Step 5 — Page 2: Trend & Comparison Analysis

1. Add a **Line Chart**: Axis = `invoices[invoice_date]` (set to Hour granularity via the field's
   drill level), Value = `Total Orders`.
2. Add a **Clustered Column Chart**: Axis = `customers[country]`, Values = `Total Revenue` split by
   `invoices[is_cancelled]` (drag `is_cancelled` into Legend).
3. Add a **Slicer** on `invoices[invoice_date]`, set to "Between" (a date/time range slicer).

## Step 6 — Page 3: Deep Dive / Segmentation

1. Add a **Donut Chart**: Legend = `customer_segments[segment]`, Value = Count of
   `customer_segments[customer_id]`.
2. Add a second **Donut Chart**: Legend = `customer_segments[segment]`, Value = Sum of
   `customer_segments[total_spend]`.
3. Add a **Scatter Chart**: X = `customer_segments[order_count]`, Y = `customer_segments[total_spend]`,
   Legend = `customer_segments[segment]`. In Format → Y-axis / X-axis, turn on **Logarithmic scale**
   (matches `customer_segments_scatter.png`, since spend is heavily skewed).
4. Add a **Table**: columns = `customer_id`, `country`, `segment`, `total_spend`, `order_count`.
5. Add a **Slicer** on `customer_segments[segment]`.
6. Right-click the segment slicer or donut → **Add drill-through**: set the table visual's page as the
   drill-through target, filtered by `segment`.

## Step 7 — Polish & export

- Give every page a title (Insert → Text box) and every visual a clear chart title (Format pane →
  General → Title).
- Use one consistent color per segment across every visual on Page 3 (Format → Data colors) — e.g.
  red for High-Value, blue for Mid-Value, grey for Low-Value, matching the scatter PNG.
- **File → Export → Export to PDF** — this is your required exported PDF submission.
- **Save As** → keep the `.pbix` file — this is your required dashboard file submission.

## Step 8 — Rehearse Task 3.4 (live presentation)

Practice narrating all 3 pages start to finish, including clicking the country slicer (Page 1) and
segment slicer (Page 3) live, before your scheduled Week 12/13 presentation. Every member must speak —
see `RECORDING_GUIDE.md` in the project root for a script format you can adapt for this presentation.
