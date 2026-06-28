# Dashboard Story — Executive Sales & Profitability Dashboard

**Audience:** CEO / Sales Director / Operations Head
**Period covered:** FY2024–FY2025 (4,200 orders)

---

## Executive Summary

The business generated **$217.0M in sales and $33.3M in profit** over the two-year period, a healthy 15.35% blended margin. Revenue grew 4.3% year-over-year. On the surface, this is a stable, growing business — but the dashboard reveals that the growth and the profit are not evenly distributed, and a specific, identifiable pattern is quietly eating into margin. The good news is that this pattern is narrow enough to be fixed without disrupting the parts of the business that are working well.

## What Is Performing Well

Technology is carrying the business: it generates the majority of total profit at an 18.22% margin, well above the company average. Regional performance is broadly balanced — no single region is a clear laggard on revenue, and the East region in particular converts sales to profit more efficiently than the rest. Shipping speed and quality move together in a useful way: Same Day delivery has the lowest return rate of any shipping mode, suggesting that faster fulfillment is a genuine lever for customer satisfaction, not just a cost center.

## What Is Underperforming

Furniture is the clear outlier. It accounts for roughly a quarter of total sales but returns only a 6.89% margin — well below Technology's 18.22% and Office Supplies' 14.85%. Within Furniture, Tables and Bookcases are the weakest sub-categories, both sitting around 5.7% margin. Furniture is also the most-returned category at 7.67%, compared to roughly 3% for the other two categories — so the same category that drags down margin is also generating disproportionate customer dissatisfaction.

## Risks Visible in the Data

The clearest risk is concentrated, not systemic: 288 orders across the two years lost money outright, and 93% of those loss-making orders are Furniture. The mechanism is visible in the discount data — average margin falls steadily as discount level rises, turning negative (−4.95%) once discounts exceed 30%. Furniture also carries the highest average discounting of any category, which is very likely the direct cause of its weak margin. A second, smaller risk: blended margin slipped slightly from 15.51% to 15.20% year-over-year even as sales grew, meaning the business is converting revenue to profit slightly less efficiently each year.

## Opportunities Visible in the Data

Because the problem is concentrated in one category and one lever (discount depth), the fix is narrow and measurable. Capping discounts on Furniture, or specifically on Tables and Bookcases, should recover meaningful margin without affecting Technology or Office Supplies at all. On the shipping side, the link between faster delivery and lower returns suggests a low-risk pilot: upgrading shipping for higher-value or historically return-prone orders and measuring whether returns drop enough to justify the added cost.

## Recommended Business Actions

1. **Cap discounts on Furniture**, particularly Tables and Bookcases, at or below roughly 20% pending a pricing review — this is where almost all loss-making orders originate.
2. **Set a 2026 margin-recovery target** (e.g. back above 15.5%) explicitly tied to the Furniture discount fix, and track it quarterly.
3. **Investigate Furniture's elevated return rate** specifically — packaging, in-transit damage, or product description mismatches are the most likely causes given the category's combination of low margin and high returns.
4. **Pilot faster shipping on a sample of high-value or return-prone orders** to test whether the lower return rate seen with Same Day delivery generalizes when deliberately applied.
5. **Study West's lower regional margin** against East's higher one to see whether a transferable practice (pricing, discount discipline, product mix) explains the gap.

## Limitations of the Dashboard

This dashboard reflects two years of order-level data with no itemized cost breakdown — profit is taken as given in the source data, not decomposed into COGS, logistics, or overhead. `delivery_days` measures the order-to-ship lead time, not full last-mile delivery time, so it likely understates the customer's actual wait. A small number of records (about 1.3% of rows) are missing `customer_rating` or `campaign_channel` values; these are excluded from the relevant averages rather than imputed. The dataset's regional and channel figures have not been cross-validated against any external finance system.

## Suggested Next Analysis

A natural follow-up would be a cohort or customer lifetime value analysis to see whether the patterns observed here (e.g. Home Office's higher return rate) hold at the individual customer level, and a price-elasticity study specifically for Furniture sub-categories to find the discount level that maximizes profit rather than just avoiding losses.
