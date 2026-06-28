# Chart Selection Justification

**Project:** Executive Sales & Profitability Dashboard
**Dataset:** `dashboard_sales_data.xlsx` (4,200 orders, FY2024–FY2025)

For each major chart on the dashboard: the question it answers, why the chart type fits, the fields used for each visual encoding, the design principle applied, and the mistake avoided.

---

## 1. Sales Trend — Line Chart

**Question answered:** How are sales changing over time, and is there a recognizable seasonal pattern?

**Why this chart type:** A line chart is the standard way to show a continuous measure (sales) against continuous time (order date by month). It makes the shape of the trend — rises, dips, and the overall trajectory — immediately visible in a way a table of monthly numbers would not.

**Fields used:** Columns = `MONTH(Order Date)`; Rows = `SUM(Sales)`; color/tooltip carries `SUM(Profit)` for additional context on hover.

**Design principle applied:** Continuous date axis with a zero-based y-axis, so the line's slope is not visually exaggerated.

**Mistake avoided:** Did not use a bar chart per month, which would have made the overall trend harder to read at a glance compared to a connected line.

---

## 2. Regional Performance — Horizontal Bar Chart

**Question answered:** Which region generates the most sales, and how do regions compare to one another?

**Why this chart type:** With only four regions, a sorted horizontal bar chart gives the most precise, easy-to-compare ranking. Horizontal orientation leaves room for region labels and long value labels without crowding.

**Fields used:** Rows = `Region`; Columns = `SUM(Sales)`; color intensity reflects `SUM(Profit)`, giving a secondary read on profit alongside the primary sales ranking.

**Design principle applied:** Bars sorted in descending order by sales, with a zero-based axis, so length comparisons are honest.

**Mistake avoided:** Did not use a pie chart — with four regions of broadly similar size (all between roughly $48M and $65M), a pie would make the actual ranking hard to judge by eye.

---

## 3. Category Profitability — Stacked Bar Chart (Profit / Sales / Margin by Category and Sub-Category)

**Question answered:** Which categories and sub-categories drive profit, and which are dragging margin down?

**Why this chart type:** Stacked bars let each category's sub-category composition be seen at once across three aligned metrics (profit, sales, and margin), so the viewer can connect "Furniture is large on sales" with "Furniture is small on profit" in a single glance across the rows.

**Fields used:** Columns = `Category`; Rows = `SUM(Profit)`, `SUM(Sales)`, `AGG(Profit Margin)`; Color = `Sub-Category`.

**Design principle applied:** Consistent category ordering and color-coding for sub-category across all three stacked rows, so the same color always means the same sub-category no matter which metric row you're looking at.

**Mistake avoided:** Did not collapse this into a single profit-only bar chart, which would have hidden the sales-vs-margin disconnect that is the actual insight (Furniture: high sales, low margin).

---

## 4. Customer Segment — Bar Chart

**Question answered:** How do Consumer, Corporate, and Home Office customers compare on sales?

**Why this chart type:** Only three segments with sales values close to one another — a simple sorted bar chart is the clearest, most honest comparison for values this close together.

**Fields used:** Columns = `Customer Segment`; Rows = `SUM(Sales)`.

**Design principle applied:** Equal bar widths and a shared baseline so small percentage differences (under 6% apart) are still visually legible without exaggeration.

**Mistake avoided:** Did not use a pie chart — three nearly equal slices would be close to indistinguishable by eye, hiding rather than revealing the (small) real differences.

---

## 5. Shipping Performance — Bar Chart (Delivery Days by Ship Mode)

**Question answered:** How does delivery speed vary across shipping modes?

**Why this chart type:** Ship modes are a small set of discrete categories, not a time series, so a bar chart comparing average delivery days per mode is the right comparison tool — precise and uncluttered.

**Fields used:** Rows = `Ship Mode`; Columns = `Delivery Days`.

**Design principle applied:** Sorted by delivery speed so the fastest and slowest modes are immediately visible at opposite ends.

**Mistake avoided:** Did not use a line chart, which would have implied a false continuous order or progression between categorical shipping modes.

---

## 6. Discount vs Profit — Scatter Plot

**Question answered:** How does discount level relate to order-level profit?

**Why this chart type:** A scatter plot shows the raw relationship between two continuous measures (discount and profit/sales) at the order level, making the downward trend and the loss-making cluster at high discount levels visible without pre-aggregating away the underlying spread.

**Fields used:** X-axis = `Discount`; Y-axis/size = `Sales`; color = `Customer Segment` or `Category` (for filtering context); detail = individual orders.

**Design principle applied:** A zero-reference line implied by the axis so orders that cross into negative profit are visually distinguishable from profitable ones.

**Mistake avoided:** Did not rely on a single aggregate number (e.g. "average margin"), which would have hidden the cliff-like decline visible once discounts pass roughly 20–30%.

---

## 7. Return Analysis — Bar Chart (Returns by Category)

**Question answered:** Which category has the highest return rate, and how does it compare to the others?

**Why this chart type:** A bar chart of return rate (not raw return count) by category gives a fair, denominator-adjusted comparison across categories with different order volumes.

**Fields used:** Columns = `Category`; Rows = `Return Flag` (aggregated as a rate via the Return Rate calculated field).

**Design principle applied:** Used a rate rather than a raw count, since categories have different total order volumes and a raw count would conflate "more orders" with "more return-prone."

**Mistake avoided:** Did not show return counts alone — Furniture's 88 returns out of 1,147 orders (7.67%) is the meaningful figure, not the count in isolation, which could mislead if categories had very different volumes.

---

## Cross-Cutting Design Principles Applied

| Principle | How it's applied across the dashboard |
|---|---|
| One question per chart | Each sheet is scoped to a single, clearly stated business question |
| Right encoding for the task | Length/position for precise ranking comparisons; color reserved for a secondary dimension (margin, sub-category, segment) |
| Honest scales | Zero-based axes throughout; no truncation used to exaggerate differences |
| Rates over raw counts | Return Rate and Profit Margin are used as calculated rate fields rather than raw counts, so comparisons across groups of different sizes stay fair |
| Minimal clutter | No 3D effects, no decorative chart types, gridlines kept light |
| Filterable consistency | Region, Category, and Customer Segment filters apply across the dashboard so every chart can be sliced the same way |

## Common Mistakes Deliberately Avoided

- Pie charts for categories or segments with three-to-four near-equal-sized groups, where ranking is hard to judge visually.
- Showing raw return counts without a denominator, which would conflate order volume with return propensity.
- Truncated or non-zero-based axes that would visually exaggerate small differences.
- Implying a false sequence (e.g. a line chart) across unordered categorical fields like ship mode or customer segment.
