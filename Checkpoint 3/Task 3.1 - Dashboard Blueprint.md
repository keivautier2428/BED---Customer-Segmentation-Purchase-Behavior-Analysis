# Task 3.1 — Dashboard Design Blueprint
Customer Segmentation & Purchase Behavior Analysis

This is the wireframe required *before* building the dashboard. Sketch/screenshot each page layout
below (or redraw by hand) as your submission — the actual dashboard is built afterward, following
`Power BI Build Guide.md`.

---

## Page 1 — Executive Summary
**Purpose:** One-glance answer to "how is the business doing overall?"

```
┌─────────────────────────────────────────────────────────────────┐
│  CUSTOMER SEGMENTATION & PURCHASE BEHAVIOR — EXECUTIVE SUMMARY   │
├───────────────┬───────────────┬───────────────┬─────────────────┤
│ TOTAL REVENUE │ TOTAL ORDERS  │ TOTAL CUSTOMERS│ AVG ORDER VALUE │
│  £106,185.83  │     271       │      207       │    £391.83      │
│   (KPI card)  │   (KPI card)  │   (KPI card)   │   (KPI card)    │
├───────────────┴───────────────┴───────────────┴─────────────────┤
│  Revenue by Country (bar chart, sorted descending)               │
│  ██████████████████████████████████  United Kingdom              │
│  ███ Germany   ██ France   █ EIRE   █ Norway  ...                │
├───────────────────────────────────────────────────────────────────┤
│  Top 10 Products by Revenue (horizontal bar chart)                │
└─────────────────────────────────────────────────────────────────┘
Slicer (top of page, applies to whole page): [ Country ▾ ]
```

- **KPI cards (4):** Total Revenue, Total Orders (completed only), Total Customers, Average Order Value.
- **Chart 1:** Bar chart — revenue by country.
- **Chart 2:** Horizontal bar chart — top 10 products by revenue.
- **Interactive element:** Country slicer at the top, filtering every visual on the page.

---

## Page 2 — Trend & Comparison Analysis
**Purpose:** When do sales happen, and how do categories compare?

```
┌─────────────────────────────────────────────────────────────────┐
│  TREND & COMPARISON ANALYSIS                                     │
├─────────────────────────────────────────────────────────────────┤
│  Order Count by Hour of Day (line chart)                         │
│      ╱\                                                           │
│     ╱  \___╱‾‾‾╲___                                              │
│   ╱╱          8AM      1PM      6PM                              │
├─────────────────────────────────────────────────────────────────┤
│  Revenue: Completed vs Cancelled Orders (clustered bar chart)     │
│   United Kingdom  ██████████ / ██                                │
│   Germany         ███ / █                                        │
│   France          ██ / █                                         │
└─────────────────────────────────────────────────────────────────┘
Slicer (top of page): [ Date/Hour range ▾ ]
```

- **Chart 1:** Line chart — order count by hour of day (intraday demand curve).
- **Chart 2:** Clustered bar chart — completed vs. cancelled revenue by country (two different chart
  types on one page, as required).
- **Interactive element:** a date/hour range slicer.

---

## Page 3 — Deep Dive / Customer Segmentation
**Purpose:** Who are our customers, and which few of them matter most?

```
┌─────────────────────────────────────────────────────────────────┐
│  CUSTOMER SEGMENTATION DEEP DIVE                                  │
├───────────────────────────────┬───────────────────────────────────┤
│  Customers by Segment (donut)  │  Revenue Share by Segment (donut) │
│   ● High-Value        2.1%     │   ● High-Value           27.2%    │
│   ● Mid-Value        56.1%     │   ● Mid-Value            59.4%    │
│   ● Low-Value/1-time 41.8%     │   ● Low-Value/1-time     13.4%    │
├───────────────────────────────┴───────────────────────────────────┤
│  Spend vs. Order Count by Customer, colored by segment            │
│  (scatter plot — see customer_segments_scatter.png)                │
├─────────────────────────────────────────────────────────────────┤
│  Customer detail table: ID | Country | Segment | Spend | Orders    │
└─────────────────────────────────────────────────────────────────┘
Slicer: [ Segment ▾ ]     Drill-through: click a segment → filtered customer table
```

- **Chart 1:** Donut chart — % of customers per segment.
- **Chart 2:** Donut chart — % of revenue per segment (the contrast between these two donuts *is* the
  insight — a small slice of customers, a large slice of revenue).
- **Chart 3 (the required clustering visual):** scatter plot of total spend vs. order count, colored
  by segment — this is `customer_segments_scatter.png` recreated as an interactive Power BI visual.
- **Interactive elements:** a Segment slicer, and drill-through from a segment into the detail table.

---

## Interactive Elements Summary (minimum 2 required)
1. **Country slicer** (Page 1) — filters KPIs and charts by country.
2. **Segment slicer + drill-through** (Page 3) — filters the customer detail table by segment.
3. *(bonus)* Date/hour range slicer (Page 2).
