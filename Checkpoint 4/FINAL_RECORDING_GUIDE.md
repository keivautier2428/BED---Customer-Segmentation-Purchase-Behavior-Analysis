# Recording Guide & Voice-Over Script
### BED 106 Capstone — Customer Segmentation & Purchase Behavior Analysis
### Checkpoint 4 (Final Output): PowerPoint + Live Power BI Dashboard only

Record your screen while reading this script out loud. No camera needed — just screen + voice.
On screen the whole time: only the PowerPoint (slideshow mode) and the live Power BI dashboard.
Target length: about 14–17 minutes.

**Who says what**
| Member | Role | Speaks in |
|---|---|---|
| Jeziel Lea Mitch Credo | Project Lead / BI Developer | Parts 1, 4, 7 |
| Nicka Hinlayagan | Data Engineer | Parts 2, 6 |
| Jennilyn Manatad | Statistician / Modeler | Parts 3, 5 |

---

## 1. Before You Record

1. Open `Checkpoint 4 - Defense Slides.pptx` and start the slideshow (slide 1).
2. Open `Customer Segmentation Dashboard.pbix` in Power BI Desktop on Page 1 (or the published link). Keep it in a second window so you can switch with `Alt + Tab`.
3. Close everything else (no Excel, no phpMyAdmin, no other tabs, notifications off).

**Recording tool:** Windows Game Bar (`Win + G`) or OBS Studio. Each person records their own parts, then combine the clips in order with CapCut or Clipchamp.

**Reading tip:** read slowly; pause at `[pause]`. Practise the live Power BI clicks twice.

---

## 2. Flow

| Time | Part | Speaker | Screen |
|---|---|---|---|
| 0:00–2:00 | 1. Introduction & business problem | Jeziel | Slides 1–2 |
| 2:00–4:30 | 2. Data & SQL | Nicka | Slides 3–4 |
| 4:30–7:00 | 3. Statistical findings | Jennilyn | Slides 5–6 |
| 7:00–11:30 | 4. Live dashboard demo | Jeziel | Slides 7–8 → live Power BI |
| 11:30–15:00 | 5. Predictive model | Jennilyn | Slides 9–12 |
| 15:00–16:30 | 6. Ethics & governance | Nicka | Slide 13 |
| 16:30–17:30 | 7. Closing | Jeziel | Slide 13 / title slide |

---

## 3. The Script

### Part 1 — Introduction & Business Problem
**Jeziel** — *(Slide 1, then Slide 2)*

> "Good day, everyone. This is our Business Analytics final capstone: Customer Segmentation and
> Purchase Behavior Analysis for a UK online gift retailer.
> [pause]
> The business problem is that the store treats every customer the same way in its marketing and its
> stock decisions. Without knowing who its best customers are, marketing spend is not targeted, the
> most valuable customers are not specifically retained, and returned or cancelled products go
> unflagged.
> [pause]
> We set out to answer three questions: who are the most valuable customers, which products and
> countries drive the most revenue, and which products are cancelled or returned the most.
> [pause]
> We used a sample of the UCI Online Retail dataset from 1 to 3 December 2010 — 300 invoices and 207
> customers. Today we'll walk through the database, the statistics, the live dashboard and the
> predictive model, and finish with ethics and governance."

---

### Part 2 — Data & SQL
**Nicka** — *(Slide 3, then Slide 4)*

> "The raw data came as one flat file. During cleaning we removed 5,268 exact duplicates, 2,910
> non-product codes such as postage and bank charges, and 1,047 rows with invalid prices. We kept
> real cancellations, which start with the letter C.
> [pause — Slide 3, point to the ERD]
> The cleaned data was split into four connected tables in MySQL: customers, invoices, invoice items
> and products. In total that is 207 customers, 300 invoices — 271 completed — 5,129 order lines and
> 1,597 products.
> [pause — Slide 4]
> Our SQL queries answer the business questions directly. Query 3 groups completed revenue by
> country: the United Kingdom accounts for 84.9% of it — about £90,181 out of £106,186.
> Query 7 splits customers into High-Value, Repeat and One-Time groups using spend and order count.
> Query 8 looks at cancellations; 29 of the 300 invoices, or 9.7%, were cancelled. One large cancelled
> order can distort the product list in that query, and guest checkouts have no country."

---

### Part 3 — Statistical Findings
**Jennilyn** — *(Slide 5, then Slide 6)*

> "From our Checkpoint 2 Excel analysis, using the 5,055 completed order lines.
> [pause — Slide 5]
> The average quantity per line is 11.6 units, but the median is only 3, and the largest single line
> is 2,880 units. The average line total is £21.01 against a median of £10.20. The distribution is
> strongly right-skewed.
> [pause — Slide 6]
> Quantity and unit price have a correlation of minus 0.057 — essentially none. Items per invoice and
> invoice value have a correlation of 0.691 — a moderately strong positive relationship.
> The simple regression is: Invoice Value equals 217.49 plus 9.35 times items per invoice. R-squared
> is 0.478, the p-value is below 0.0001, and there are 271 invoices.
> We also tried a trend forecast on hourly revenue, but it was not significant — R-squared 0.047,
> p-value 0.31 — because the data covers only about three days."

---

### Part 4 — Live Dashboard Demo
**Jeziel** — *(Slides 7–8 as a short intro, then `Alt + Tab` to live Power BI)*

> "Now the dashboard, built in Power BI with three pages. Let me switch to it.
> [pause — switch to Power BI, Page 1: Executive Summary]
> The four KPI cards show total revenue of £106.19K, 271 completed orders, 207 customers, and an
> average order value of £391.83. Below them are revenue by country and the top ten products.
> [LIVE — click a country in the slicer; show the cards and charts change; then clear it]
> [pause — Page 2: Trend & Comparison]
> This page shows orders by hour of day, and completed versus cancelled orders by country. The
> cancelled-order rate is 9.7%.
> [LIVE — drag the date slicer; show the hourly chart change]
> [pause — Page 3: Customer Segmentation]
> For segmentation we used K-Means clustering on 189 customers, using total spend, number of orders
> and average order value, log-scaled. We compared two to five clusters using silhouette scores —
> 0.553, 0.437, 0.487 and 0.463 — and chose three, the smallest number that gave distinct segments.
> The High-Value group has 4 customers — 2.1% of customers — but 27.2% of revenue.
> The Mid-Value Shoppers are 56.1% of customers and 59.4% of revenue.
> The Low-Value and One-Time group is 41.8% of customers and 13.4% of revenue.
> [LIVE — click the segment slicer on High-Value; show the customer table filter; then clear it]
> [pause — switch back to the slides]
> One limit: the sample covers only three days, so the difference between Mid-Value and Low-Value
> reflects spend per order rather than loyalty over time."

---

### Part 5 — Predictive Model
**Jennilyn** — *(Slides 9, 10, 12, 11 — all on the slideshow)*

> "For predictive analytics we extended the simple regression into a multiple regression, built in
> Excel. The output is invoice value, and the two predictors are the number of product lines on the
> invoice and the total quantity.
> [pause — Slide 9]
> The fitted equation is: Invoice Value equals 52.65 plus 7.20 times lines, plus 0.946 times
> quantity. R-squared is 0.802 and adjusted R-squared is 0.800, up from 0.478 in the simple model.
> The standard error is about £299, and the F-statistic is 542 with a significance well below 0.0001.
> Both predictors are significant. We also tested adding average unit price, and R-squared improved
> by only 0.0009.
> [pause — Slide 10]
> For a typical basket of 11 lines and 106 units, the model predicts £232.15. Adding five more lines
> raises the prediction to £268.16. A large basket of 30 lines and 400 units is predicted at £647.13.
> The typical error is about £152.
> [pause — Slide 12]
> The model has limits. The sample is only 3 days and 271 invoices. The approximate range around any
> prediction is plus or minus £586. 13 of the 271 invoices — 4.8% — miss by more than two standard
> errors. And because invoice value is quantity times price, quantity is partly built into the
> output.
> [pause — Slide 11]
> In the model, one extra product line adds about £7.20 to an invoice and one extra unit adds about
> £0.95, while average unit price adds almost nothing. From the dashboard, the 4 High-Value customers
> generate 27.2% of revenue and the Mid-Value shoppers generate 59.4%."

---

### Part 6 — Ethics & Governance
**Nicka** — *(Slide 13)*

> "On ethics and governance. The dataset contains only a numeric customer ID, a country and
> transaction details — there are no names or addresses. In the raw file, 24.9% of the rows are guest
> checkouts with no customer ID.
> [pause]
> The segment labels, such as High-Value and Low-Value, describe spending in this sample. The sample
> covers only three days and is dominated by UK customers.
> [pause]
> The data is public and licensed under Creative Commons Attribution 4.0, so it can be used with
> credit to the source.
> [pause]
> In the Philippines, personal data is protected by Republic Act 10173, the Data Privacy Act of 2012.
> The retailer is UK-based, so the GDPR concept of profiling and data minimisation also applies."

---

### Part 7 — Closing
**Jeziel** — *(Slide 13 or the title slide)*

> "To wrap up, we went from a raw flat file to a four-table database, then to statistics, a three-page
> dashboard with three customer segments, and a predictive model that explains about 80% of invoice
> value. Thank you for watching."

---

## 4. After Recording
- Trim silence at the start and end of each clip.
- Order: Jeziel → Nicka → Jennilyn → Jeziel → Jennilyn → Nicka → Jeziel.
- Watch the whole video once; check the volume is even across all three voices.
- Check that every member speaks at least once.
- Export as .mp4 and submit with the report, Excel files, Power BI file and slides.
