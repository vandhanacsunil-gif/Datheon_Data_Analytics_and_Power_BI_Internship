# Task 4: Corporate Financial & Margin Performance Dashboard

Financial KPI dashboard built in Power BI from the Microsoft Financial Sample dataset. It models the income statement (Gross Sales, Discounts, Net Sales, COGS, Profit), compares actual sales against budget by segment, country and product, and includes scenario sliders for forecasting.

## Files
| File | Description |
|---|---|
| `Financial_Dashboard.pbix` | Interactive Power BI report (3 pages) |
| `Financial_Dashboard.pdf` | PDF export of all pages |
| `financial_sample.xlsx` | Source dataset |

## Important Assumption: Budget
The dataset contains **no budget data**. For the variance analysis, budget was assumed as actual sales plus a segment-level uplift target, stored in a `Budget` table and related to the data by Segment:

| Segment | Assumed uplift |
|---|---|
| Government | 5% |
| Midmarket | 8% |
| Channel Partners | 3% |
| Enterprise | 10% |
| Small Business | 6% |

All variance figures reflect this assumption, not real company targets.

## Method
**Power Query:** trimmed text columns, renamed columns, set data types, and added `Quarter` and `Year-Quarter` columns.

**DAX measures**
| Measure | Definition |
|---|---|
| Net Sales, Profit Total, COGS Total | Sums of the sales, profit and COGS columns |
| Gross Sales Total, Discounts Total | Sums of gross sales and discounts |
| Gross Profit % | `DIVIDE([Profit Total], [Net Sales], 0)` |
| COGS Ratio | `DIVIDE([COGS Total], [Net Sales], 0)` |
| Discount % | `DIVIDE([Discounts Total], [Gross Sales Total], 0)` |
| Segment Margin | `DIVIDE([Profit Total], [Net Sales], 0)` |
| Budget Sales | Actual sales multiplied by (1 + the segment uplift) |
| Variance, Variance % | Net Sales minus Budget Sales, and that gap as a share of budget |
| Scenario Gross Sales, Discounts, Net Sales, COGS, Profit, Margin % | Recalculated using the three scenario parameters |

**Scenario parameters:** Volume Growth (-20% to +20%), Discount Change (-10 to +10 points) and COGS Change (-10% to +10%).

## Dashboard Pages
**Executive Overview**
- KPI cards: Gross Profit %, Profit, Net Sales, Gross Sales, Discounts, Discount %, COGS Ratio, Scenario Profit, Variance vs Budget %
- Waterfall chart: Gross Sales to Discounts to COGS to Profit, driven by the scenario sliders
- Income Statement Summary table
- Three scenario sliders

**Variance Analysis**
- Actual vs Budget by Segment and by Country
- Variance vs Budget by Product (matrix with colour-coded Variance %)
- Quarterly Net Sales and Profit trend
- Slicers: Year, Segment, Country

**Cost & Margin**
- Manufacturing Cost (COGS) by Product
- Segment Margin by Segment

## Key Findings
- Gross sales **$127.9M**, discounts **$9.2M**, net sales **$118.7M**, COGS **$101.8M**, profit **$16.9M**.
- Gross profit margin is **14.2%**. COGS takes **85.8%** of net sales, and discounts are **7.2%** of gross sales.
- Net sales are about **5.85%** below the assumed budget, and the shortfall is similar across products (-5.7% to -6.1%).
- Segment margins differ widely: Channel Partners **73.1%**, Midmarket 27.7%, Government 21.7%, Small Business 9.8%, and **Enterprise -3.1%**.
- **Paseo** has the highest manufacturing cost ($28.2M), followed by VTT ($17.5M).

## Recommendations
- Investigate Enterprise, the only segment with a negative margin, starting with its pricing and discounts.
- Reduce the COGS ratio, since small cost improvements have a large effect on a 14.2% margin.
- Use the scenario sliders to test discount and volume changes before setting targets.
- Replace the assumed budget with real targets when available.

## How to Open
Open `Financial_Dashboard.pbix` in Power BI Desktop. Move the three sliders on Executive Overview to see the waterfall and Scenario Profit change. The PDF is a static copy of all pages.
