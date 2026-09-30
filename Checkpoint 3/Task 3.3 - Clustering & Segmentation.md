# Task 3.3 — Data Mining: Clustering / Segmentation
Customer Segmentation & Purchase Behavior Analysis

## Method

Every customer with at least one completed (non-cancelled, non-guest-checkout) order in the
Checkpoint 1 dataset was reduced to three numbers: **total spend**, **number of orders**, and
**average order value**. This covers 189 of the 207 customers in the dataset — 18 customers had no
completed order (only cancellations or guest checkouts) and were excluded.

Because spend and order count are heavily right-skewed (a few customers buy far more than everyone
else — the same pattern found in Checkpoint 2's descriptive statistics), each value was
log-transformed and standardized before clustering, so the algorithm isn't dominated purely by the
biggest spenders.

**K-Means clustering** was run for k = 2 through 5 to check how many segments the data actually
supports:

| k | Silhouette score |
|---|---|
| 2 | 0.553 |
| **3** | **0.437** |
| 4 | 0.487 |
| 5 | 0.463 |

k = 2 scores slightly higher, but it only splits customers into "big spenders" vs. "everyone else" —
not useful for targeting. **k = 3** was chosen because it's the smallest number of clusters that
produces genuinely different, actionable groups, matching the task's requirement of 2–3 segments.

## The Three Segments

| Segment | Customers | % of Customers | Avg. Spend | Avg. Orders | Avg. Order Value | Revenue Share |
|---|---|---|---|---|---|---|
| **High-Value Customers** | 4 | 2.1% | £6,413.81 | 12.5 | £1,022.76 | **27.2%** |
| **Mid-Value Shoppers** | 106 | 56.1% | £528.88 | 1.1 | £477.57 | 59.4% |
| **Low-Value / One-Time Customers** | 79 | 41.8% | £159.88 | 1.1 | £147.54 | 13.4% |

*(Full numbers in `segment_summary.csv`; every customer's individual label is in
`customer_segments.csv`. Chart: `customer_segments_scatter.png`.)*

### High-Value Customers
Just 4 customers — 2% of the customer base — but they generate **over a quarter of total revenue**.
They also order far more often (12.5 times on average, vs. ~1 for everyone else) even within this
3-day sample, which is the clearest signal that these are repeat or possibly wholesale-style
accounts, not casual shoppers.
**Business action:** these customers should be individually tracked and retained — a lost account
here has an outsized revenue impact. Consider dedicated account contact or loyalty perks.

### Mid-Value Shoppers
The largest group (56% of customers) and the largest revenue contributor overall (59%). Their orders
tend to be moderate-to-large in value even though most only ordered once in this window.
**Business action:** this is the group most worth targeting with cross-sell and upsell campaigns —
Checkpoint 2's regression already showed that adding items per order is the strongest lever for
raising order value, and this segment is the natural target for that kind of promotion.

### Low-Value / One-Time Customers
42% of customers, but only 13% of revenue. Small, single, low-value orders.
**Business action:** low-cost, automated re-engagement (email promos, discount codes) makes more
sense here than high-touch retention efforts — the per-customer revenue doesn't justify heavier
spend on this group.

## Limitation

The dataset only spans 3 calendar days (Dec 1–3, 2010). "Order count" as a frequency signal is
naturally compressed — most customers can only realistically place 1 order in that window regardless
of how loyal they actually are. The High-Value segment stands out so clearly (12.5 average orders in
3 days) that it's a reliable signal, but the Mid vs. Low split is really driven by **spend per order**,
not true purchase frequency. A longer time window (the full source dataset runs through
2011-12-09) would let a future iteration segment on real repeat-purchase behavior, not just
order size.
