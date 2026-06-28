# Executive Sales & Profitability Dashboard — Tableau

**Student:** Devang Agarwal
**Student ID:** bitsom_ba_2511137
**Assignment:** Part 4 — Tableau Executive Dashboard & Data Storytelling

---

## Business Problem Summary

Leadership lacks a single, trustworthy view of how the retail business is performing and why. Sales are healthy overall, but profit quality, discounting discipline, shipping speed, and returns are not visible in one place — so margin leakage can go unnoticed. This dashboard gives leadership one place to answer: **how is the business doing, where, and what is quietly hurting profit?**

## Dataset Description

`data/dashboard_sales_data.xlsx` — 4,200 rows × 20 columns, one row per order, covering FY2024–FY2025. A second sheet, `data_dictionary`, documents every field.

| Group | Fields |
|---|---|
| IDs | `order_id`, `customer_id` |
| Dates | `order_date`, `ship_date` |
| Customer / Geography | `customer_segment`, `region`, `state`, `city` |
| Product | `category`, `sub_category`, `product_name` |
| Order facts | `ship_mode`, `sales`, `quantity`, `discount`, `profit`, `return_flag`, `delivery_days`, `customer_rating`, `campaign_channel` |

**Data quality:** 0 duplicate rows, 0 duplicate order IDs. 56 missing cells total — `customer_rating` (32 missing) and `campaign_channel` (24 missing), out of 4,200 rows each (under 1%). No negative sales, no negative delivery days.

## Tableau Workbook Description

`tableau/executive_dashboard.twbx` is a packaged workbook (data embedded) containing:
- 3 KPI card sheets (Total Sales, Total Profit, Profit Margin)
- 7 analysis sheets (Sales Trend, Regional Performance, Category Profitability, Customer Segment, Shipping Performance, Discount vs Profit, Return Analysis)
- 1 assembled dashboard (`ExecutiveDashboard`) combining all of the above

## Calculated Fields Created

| Field | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `IF SUM([sales]) = 0 THEN 0 ELSE SUM([profit]) / SUM([sales]) END` | Profit as a share of sales; guarded against divide-by-zero |
| **Cost** | `[sales] - [profit]` | Implied cost per order, since profit is given as net |
| **Average Order Value** | `SUM([sales]) / COUNTD([order_id])` | Average revenue per distinct order |
| **Return Rate** | `SUM([return_flag]) / COUNTD([order_id])` | Share of orders returned, as a true percentage |
| **Shipping Delay Bucket** | `IF [delivery_days] <= 2 THEN "Fast (0-2 Days)" ELSEIF [delivery_days] <= 5 THEN "Standard (3-5 Days)" ELSE ... END` | Groups delivery days into business-meaningful speed tiers |

**Note on Return Rate:** an earlier version of this field used `INT(SUM([return_flag]) / COUNT([order_id]))`, which truncated the result to 0 since the true return rate (4.55%) is under 1. This was corrected to remove the `INT()` wrapper and use `COUNTD` for a distinct order count, so the field now correctly reports the rate as a percentage.

## Dashboard Components

- **KPI cards:** Total Sales, Total Profit, Profit Margin
- **Sales Trend:** monthly sales line chart
- **Regional Performance:** sales by region, bar chart
- **Category Profitability:** profit, sales, and margin by category and sub-category
- **Customer Segment:** sales comparison across Consumer, Corporate, Home Office
- **Shipping Performance:** average delivery days by ship mode
- **Discount vs Profit:** order-level relationship between discount and profitability
- **Return Analysis:** return rate by category

## Filters and Interactions Used

- **Filters applied dashboard-wide:** Region, Category, Customer Segment (set to apply to all worksheets using the data source)
- **Action:** clicking a bar on Regional Performance filters all other dashboard views to the selected region (Filter action, run on Select)

## Key Business Insights

Full detail in `outputs/business_insights.md`. Headlines:
- Technology runs an 18.22% margin and generates the large majority of total profit; Furniture runs only 6.89% margin despite being roughly a quarter of total sales.
- Average margin falls steadily as discount increases, turning negative (−4.95%) once discounts exceed 30%.
- 93% of all loss-making orders (269 of 288) are Furniture orders.
- Furniture has the highest return rate of any category (7.67% vs ~3% for the others), and returned orders carry a lower average customer rating (3.66 vs 4.08).
- Same Day shipping has the lowest return rate (2.49%) of any shipping mode, while Standard Class — the slowest mode — is also the most common, used by 58% of orders.

## Dashboard Story Summary

Full narrative in `outputs/dashboard_story.md`. In short: the business is healthy and growing (sales +4.3% year-over-year, 15.35% blended margin) but is quietly losing margin through one specific, identifiable pattern — deep discounting concentrated in the Furniture category, which is also the most return-prone category. Because the problem is narrowly scoped, a targeted discount cap and Furniture pricing review are likely to recover meaningful margin without affecting the rest of the business.

## Assumptions and Limitations

- `discount` is treated as a fraction (e.g. 0.15 = 15% discount).
- `profit` is treated as net profit, so `Cost = Sales − Profit`.
- `delivery_days` is the order-to-ship lead time, not full last-mile delivery time — it likely understates the customer's actual wait.
- `return_flag` is recorded at the order level (1 = returned, 0 = not returned).
- Missing values in `customer_rating` and `campaign_channel` (under 1% of rows each) are left as-is and excluded from relevant averages rather than imputed.
- This is a two-year snapshot with no itemized cost breakdown behind the `profit` figure; figures have not been validated against any external finance system.

## Screenshots Included

Located in `screenshots/`:
- `full_dashboard.png` — complete executive dashboard
- `sales_trend_view.png` — Sales Trend sheet
- `regional_performance_view.png` — Regional Performance sheet
- `category_profitability_view.png` — Category Profitability sheet
- `filter_interaction_view.png` — dashboard with an active filter selection, showing the interaction

## How to Open

1. Install Tableau Desktop, or use the free Tableau Public Desktop app.
2. Open `tableau/executive_dashboard.twbx` — the data is embedded, so no additional setup is required.
3. To inspect or rebuild from source, connect to `data/dashboard_sales_data.xlsx` directly.
