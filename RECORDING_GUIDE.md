# Recording Guide & Voice-Over Script
### BED 106 Capstone — Customer Segmentation & Purchase Behavior Analysis
### Covers Checkpoint 1 (SQL/Database) + Checkpoint 2 (Spreadsheet/Statistics)

Record your screen while reading this script out loud. No camera needed — just screen + voice.
Short sentences, simple words, easy to read on camera. Target length: **~7–8 minutes**.

**Who says what**
| Member | Role | Speaks in |
|---|---|---|
| Jeziel Lea Mitch Credo | Project Lead / BI Developer | Parts 1, 3, 5 |
| Nicka Hinlayagan | Data Engineer | Part 2 |
| Jennilyn Manatad | Statistician | Part 4 |

---

## 1. Before You Record

**Recording tool (pick one):**
- Windows Game Bar — `Win + G`, click record. Easiest option.
- OBS Studio — more control if you want it.

**Have these open, in order, before you press record:**
1. phpMyAdmin with the `retail_customer_analytics` database open (tables + one query result).
2. Excel file: `Checkpoint 2 - Spreadsheet & Statistical Analysis.xlsx`, tabs ready: Pivot Charts, Descriptive Statistics, Correlation Analysis, Regression.

**How to record:** Each person records their own part separately, on their own screen. Then combine
the three video clips in order using CapCut or Clipchamp (both free). This is easier than getting all
three of you on one call.

**Reading tip:** Read slowly. Pause where you see `[pause]`. It's fine to pause the recording between
parts and resume — you don't need to say everything in one breath.

---

## 2. Flow

| Time | Part | Speaker | Show on screen |
|---|---|---|---|
| 0:00–1:00 | Intro & the problem | Jeziel | Nothing yet / title |
| 1:00–3:30 | Database & SQL | Nicka | phpMyAdmin |
| 3:30–4:30 | Charts | Jeziel | Excel — Pivot Charts |
| 4:30–7:00 | Statistics | Jennilyn | Excel — Stats/Correlation/Regression |
| 7:00–8:00 | Wrap-up | Jeziel | Anything from above |

---

## 3. The Script

The speaker names in bold are just a guide for who reads which part — don't say your own name out
loud mid-script. Speak like you're presenting the *project*, not introducing yourself.

### Part 1 — Project Overview
**Jeziel** — *(title screen or nothing on screen yet)*

> "Good day, everyone. This is our Business Analytics capstone project: Customer Segmentation and
> Purchase Behavior Analysis for an online retail store.
> [pause]
> The problem we're solving is this — the store currently treats every customer the same way. But in
> reality, some customers spend a lot and order often, while others buy once and never return. Without
> knowing the difference, marketing budget gets wasted and slow-moving products keep piling up in
> inventory.
> [pause]
> Our goal is to answer three questions: who are the most valuable customers, which products and
> countries drive the most revenue, and which products get returned or cancelled the most.
> [pause]
> We'll walk through this in two parts — first, how the data was structured and queried, then what the
> numbers reveal."

---

### Part 2 — Database & SQL Analysis
**Nicka** — *(show phpMyAdmin: tables, then one or two queries)*

> "Let's start with the data itself. We worked with 300 orders and about 5,000 order lines from
> December 2010. Before any analysis could happen, the raw data had to be cleaned — duplicate rows
> removed, missing product names fixed, and invalid prices taken out.
> [pause — show the 4 tables]
> The cleaned data was then organized into four connected tables: Customers, Products, Invoices, and
> Invoice Items. Structuring it this way lets us ask questions that span across customers, orders, and
> products all at once, instead of digging through one flat spreadsheet.
> [pause — show one query result]
> With that structure in place, a set of SQL queries was written to answer the business questions
> directly. This one sorts customers into three groups — High-Value Customers who spend the most,
> Repeat Customers who order frequently, and One-Time Customers. This is the first concrete step
> toward knowing exactly who the business's best customers are.
> [pause — show another query]
> This next query breaks down revenue by country — the United Kingdom leads by a wide margin, with
> Germany and France as smaller but distinct markets. And this last one flags the products that get
> cancelled or returned most often, so the business can act on it before it affects margins.
> [pause]
> With the database and queries covered, let's move to what the numbers actually tell us."

---

### Part 3 — Sales & Trend Charts
**Jeziel** — *(show Excel: Pivot Charts tab)*

> "To make these patterns easier to see, the data was also turned into charts.
> [pause — show the charts one by one]
> This chart shows total sales by country. This one ranks the top 15 best-selling products. And this
> one shows what time of day most orders come in — activity builds up in the morning, peaks around
> midday, then tapers off by evening.
> [pause]
> Together, these give a quick, visual read on where the revenue is coming from and when the business
> is busiest. Next, let's look closer at the statistics behind these numbers."

---

### Part 4 — Statistical Findings
**Jennilyn** — *(show Excel: Descriptive Statistics, then Correlation, then Regression)*

> "Digging deeper into the numbers, three findings stand out.
> [pause — Descriptive Statistics tab]
> First, on order size: most orders are small, just 1 to 3 items. But a handful of very large bulk
> orders pull the average much higher than what's typical. This matters for inventory planning — stock
> should be planned around the typical small order, not the inflated average.
> [pause — Correlation tab]
> Second, on what drives order value: price alone barely affects how much a customer buys. What matters
> more is the number of items in the order — the more items added, the higher the order's total value,
> and that relationship is fairly strong.
> [pause — Regression tab]
> Building on that, a simple prediction formula was created: for every extra item added to an order,
> the order's value increases by about 9 pounds, and this pattern is statistically solid, not
> coincidence. The takeaway for the business is clear — encouraging customers to add more items per
> order matters more than adjusting prices.
> [pause]
> With the data, the queries, and the statistics all pointing in the same direction, let's bring it all
> together."

---

### Part 5 — Summary & Next Steps
**Jeziel**

> "To summarize what this analysis shows:
> [pause]
> Customers can already be sorted into high-value, repeat, and one-time buyers. Growing the number of
> items per order matters more than the price of any single item. And sales are heavily concentrated in
> the UK, with specific products now flagged for frequent returns.
> [pause]
> This covers the work completed so far. The next steps are to turn this into an interactive dashboard,
> then add predictive analytics and a data ethics review for the final defense.
> [pause]
> Thank you for watching."

---

## 4. After Recording
- Trim the silence at the start/end of each clip.
- Put them in order: Jeziel → Nicka → Jeziel → Jennilyn → Jeziel.
- Watch the whole thing once before submitting — check the volume sounds even across all three voices.
- Export as .mp4 and submit.

## 5. Later: Checkpoints 3 & 4
Once the dashboard (Checkpoint 3) and predictions/ethics (Checkpoint 4) are done, add:
- A dashboard walkthrough (anyone can present, but everyone must speak on camera at least once).
- A short part on the prediction model and one on data ethics — give these to whoever spoke least above.
