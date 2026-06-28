# Business Insights

**Project:** Executive Sales & Profitability Dashboard
**Dataset:** `dashboard_sales_data.xlsx` — 4,200 orders, FY2024–FY2025
**Totals:** $217,017,651.92 in sales, $33,306,312.84 in profit, 15.35% blended profit margin

Each insight follows: **Observation → Data Evidence → Business Interpretation → Recommended Action / Follow-up Question.**

---

## 1. Sales Trend

**Observation:** Monthly sales are seasonal rather than steadily growing, with a visible mid-year dip.

**Data evidence:** Sales open the year around $17.9M in January, peak near $20.3M in February, and decline through subsequent months, with a low point around $15.2M before partially recovering later in the year (see the Sales Trend chart). Year-over-year, total sales grew from $106.24M in 2024 to $110.78M in 2025 — a 4.3% increase.

**Business interpretation:** Growth is real but modest, and the business has a recurring seasonal trough rather than consistent month-over-month growth. Demand planning should account for this dip rather than treating it as an anomaly.

**Recommended action / follow-up question:** Is the dip tied to a known seasonal factor (e.g. post-holiday slowdown, fiscal quarter timing)? Worth investigating with finance/sales leadership before setting next year's targets.

---

## 2. Regional Performance

**Observation:** Sales are reasonably balanced across regions, but margin quality is not uniform.

**Data evidence:** South leads on sales ($64.69M, 15.44% margin), followed by North ($54.56M, 15.24%), West ($48.91M, 15.14%), and East ($48.86M, 15.55%). East has the smallest sales footprint but the **highest margin** of all four regions; West has the **lowest margin**.

**Business interpretation:** No region is a clear underperformer on revenue, but West converts revenue to profit least efficiently. There may be a pricing, discounting, or cost-mix difference worth studying.

**Recommended action / follow-up question:** Compare West's discount levels and product mix against East's to identify what's driving the half-point margin gap, and consider whether West-specific pricing discipline is warranted.

---

## 3. Category / Sub-Category Profitability

**Observation:** Technology is the company's profit engine; Furniture is barely profitable despite strong sales.

**Data evidence:** Technology generated $153.90M in sales at an 18.22% margin and $28.04M profit — the large majority of total company profit. Furniture generated $51.64M in sales (24% of revenue) but only $3.56M profit, a 6.89% margin. Office Supplies sits in between at $11.48M sales* and 14.85% margin. Within Furniture, the worst sub-categories are Tables (5.67% margin) and Bookcases (5.71%), with Chairs (8.25%) and Furnishings (7.86%) only slightly better.

*Note: Office Supplies sales figure should be verified against the dashboard view, as it appears smaller than expected relative to its order count — worth a quick sanity check in Tableau before finalizing.

**Business interpretation:** Roughly a quarter of total revenue is processed at near break-even. The business is also concentration-dependent on Technology for the bulk of its profit.

**Recommended action / follow-up question:** Investigate re-pricing or discount caps specifically on Tables and Bookcases, and assess whether Technology's profit concentration represents an acceptable risk or needs deliberate diversification.

---

## 4. Customer Segment Behavior

**Observation:** The three customer segments perform similarly on sales and margin, with one segment standing out on returns.

**Data evidence:** Home Office leads on sales ($74.50M, 15.51% margin), followed by Consumer ($71.89M, 15.34%) and Corporate ($70.63M, 15.18%). Sales differ by under 6% across all three segments. Home Office has a return rate of 5.67%, noticeably higher than Consumer (3.91%) and Corporate (4.00%).

**Business interpretation:** Segment-level differentiation in this business is thin — leadership is not currently treating segments very differently, and the data doesn't show a strong reason for major imbalance. Home Office's elevated return rate is the one signal worth investigating.

**Recommended action / follow-up question:** Why does Home Office return more often than other segments — product fit, expectation mismatch, or something else? Worth a root-cause look before designing segment-specific offers.

---

## 5. Discount Impact on Profit

**Observation:** Profit margin declines sharply and predictably as discount level increases, with a clear loss-making threshold.

**Data evidence:** Average margin by discount band: 0% discount → 20.56% margin; 1–10% → 17.01%; 11–20% → 13.63%; 21–30% → 8.05%; 31%+ → **−4.95% (loss-making on average)**. The 31%+ discount band contains only 64 orders but loses money collectively (~$102K).

**Business interpretation:** Discounting beyond roughly 20% is, on average, value-destroying for this business — the extra volume doesn't compensate for the margin given away.

**Recommended action / follow-up question:** Consider a default discount ceiling around 20%, with senior approval required above it. Audit the 64 orders in the 31%+ band to understand why they were approved.

---

## 6. Shipping / Delivery Performance

**Observation:** Faster shipping modes are associated with meaningfully lower return rates, but most orders ship on the slowest mode.

**Data evidence:** Same Day shipping averages 0.40 delivery days with a 2.49% return rate — the fastest and lowest-return mode. Standard Class averages 4.71 days with a 4.60% return rate, and is the dominant mode by volume (2,435 of 4,200 orders, 58%). First Class (1.77 days, 5.08% return rate) and Second Class (2.68 days, 4.59%) fall in between.

**Business interpretation:** The shipping mode most customers actually receive is also the slowest, and slower shipping tracks with a higher return rate, though First Class is a mild exception worth a closer look rather than a clean trend.

**Recommended action / follow-up question:** Pilot upgrading a sample of high-value or historically return-prone orders to faster shipping and measure whether the return rate improves enough to offset the added shipping cost.

---

## 7. Return Pattern

**Observation:** Returns are modest overall but concentrated in one category and linked to lower customer satisfaction.

**Data evidence:** Overall return rate is 4.55% (191 of 4,200 orders). Furniture returns at 7.67%, clearly above Technology (3.03%) and Office Supplies (3.65%). Returned orders carry an average customer rating of 3.66, compared to 4.08 for non-returned orders. Returned orders represent $8.76M in sales and roughly $1.07M in profit.

**Business interpretation:** Furniture is both the least profitable category and the most return-prone — these two problems likely compound each other (e.g. damage in transit, sizing/expectation mismatches, or quality issues depressing both margin and satisfaction).

**Recommended action / follow-up question:** Root-cause Furniture returns specifically — packaging, product description accuracy, or in-transit damage are the most likely candidates to investigate first.

---

## 8. Business Risk / Opportunity Summary

**Observation:** Margin erosion is real but narrowly scoped, which makes it both a risk and a fixable opportunity.

**Data evidence:** 288 orders (6.86%) are loss-making overall. Of those, **269 (93.4%) are Furniture orders**, with only 5 from Technology and 14 from Office Supplies. Blended margin slipped slightly year-over-year, from 15.51% (2024) to 15.20% (2025), even as sales grew 4.3%.

**Business interpretation:** The business isn't facing a broad profitability crisis — the problem is concentrated almost entirely in one category combined with deep discounting. That concentration is actually good news: it means a small number of targeted fixes (discount caps + Furniture pricing review) could meaningfully move the needle on overall margin without requiring company-wide changes.

**Recommended action / follow-up question:** Set a 2026 margin-recovery target (e.g. back to 15.5%+) explicitly tied to fixing Furniture discounting and pricing, and track it quarterly.

---

## Insight Summary Table

| # | Theme | Headline metric | Signal |
|---|---|---|---|
| 1 | Sales trend | +4.3% YoY, seasonal mid-year dip | Mixed |
| 2 | Regional performance | East highest margin (15.55%), West lowest (15.14%) | Mixed |
| 3 | Category profitability | Furniture 6.89% margin vs Technology 18.22% | Risk |
| 4 | Customer segment | <6% sales spread; Home Office 5.67% returns | Mixed |
| 5 | Discount impact | Margin falls from 20.56% to −4.95% as discount rises | Risk / Lever |
| 6 | Shipping performance | Same Day 2.49% returns vs Standard 4.60% | Opportunity |
| 7 | Return pattern | Furniture 7.67% returns; rating 3.66 vs 4.08 | Risk |
| 8 | Risk/opportunity | 93% of loss-making orders are Furniture | Risk (fixable) |
