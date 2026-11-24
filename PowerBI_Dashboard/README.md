# Task 2: Interactive Power BI Executive Sales & Profit Dashboard

Executive dashboard built in Power BI Desktop from the Superstore dataset (Jan 2015 to Dec 2018), with KPI cards, dynamic slicers, a monthly trend, a category treemap and a product profitability matrix.

## Files
| File | Description |
|---|---|
| `Superstore_Dashboard.pbix` | Interactive Power BI report (2 pages) |
| `Superstore_Dashboard.pdf` | PDF export of both pages |

## Data Model
Star schema: `Fact_Orders` connected to `Dim_Customer`, `Dim_Product` and `Dim_Date`. Relationships run from each dimension to the fact table (one-to-many).

## DAX Measures
| Measure | Definition |
|---|---|
| Total Sales | Sum of sales |
| Total Profit | Sum of profit |
| Profit Margin % | `DIVIDE([Total Profit], [Total Sales], 0)` |
| Total Orders | Distinct count of orders |
| Sales LY | Sales for the same period last year |
| YoY Sales Growth % | `DIVIDE([Total Sales] - [Sales LY], [Sales LY], 0)` |

## Dashboard Pages
**Executive Overview**
- Five KPI cards: Total Sales, Total Profit, Total Orders, Profit Margin %, YoY Sales Growth %
- Year range slider and Region slicer
- Monthly sales trend against the previous year
- Category and sub-category treemap
- Profitability matrix with colour-coded profit margin

**Regional Analysis**
- Sales by region and state (treemap)
- Total profit by region (bar chart)
- Year and Region slicers synced with page 1

## Key Findings
- Total sales **$2.30M**, profit **$286K**, **5K** orders, profit margin **12.5%**.
- 2018 sales grew **20.4%** over 2017.
- **West** is the most profitable region ($108K), followed by East ($92K), South ($47K) and Central ($40K).
- Technology (17.4%) and Office Supplies (17.0%) carry healthy margins. Furniture earns only **2.5%**.
- Loss-making sub-categories: **Tables (-8.6%)**, **Bookcases (-3.0%)** and **Supplies (-2.5%)**.
- Sales peak strongly in November and December every year.

## Recommendations
- Review pricing and discounts on Tables, Bookcases and Supplies.
- Plan inventory and promotions around the Q4 peak.
- Investigate why South and Central lag behind West and East.

## How to Open
Open `Superstore_Dashboard.pbix` in Power BI Desktop. Use the Year and Region slicers to filter every visual. The PDF is a static copy of the full dashboard.
