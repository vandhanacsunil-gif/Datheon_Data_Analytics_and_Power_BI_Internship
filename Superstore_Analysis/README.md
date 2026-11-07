# Superstore Retail Sales: Exploratory Data Analysis

## Overview
Exploratory analysis of four years of Superstore retail orders (Jan 2015 to Dec 2018), covering customer purchase volume, monthly seasonality, category-wise revenue and discount sensitivity.

## Dataset
- 9,994 order lines and 21 columns after cleaning
- Source: Superstore Sales dataset (file: `superstore_sales.csv`)
- Total sales: $2.30M. Total profit: $286K (12.5% margin)

## Tools
Python (Pandas, NumPy, Matplotlib, Seaborn), Jupyter Notebook in VS Code

## Data Cleaning
- The CSV contained 806 non-sales rows (the People and Returns tables from other workbook sheets). I separated them from the sales data.
- Filled 1 missing Postal Code (Burlington, VT).
- Parsed order and ship dates, and converted `Row_ID` and `Quantity` to integers.
- Created `Year`, `Month` and `Year_Month` columns.
- Final data: 9,994 rows, 0 missing values, 0 duplicates.

## Key Findings
1. **Discounts above 20% destroy profit.** Average profit per line is +$26.50 at 1-20% discount, but -$77.86 at 21-40% and -$106.71 above 40%. The 1,393 lines discounted 30% or more lost $135K, about 47% of net profit.
2. **Sales peak strongly in Q4.** November, December and September are the strongest months on average. January and February are the weakest.
3. **Furniture is high revenue but low profit.** It earns a 2.5% margin against about 17% for Technology and Office Supplies. Tables lose $17.7K and Bookcases $3.5K.
4. **The Central region underperforms.** Its margin is 7.9% against 14.9% for West and 13.5% for East.
5. **Growth is strong, but profit is not keeping pace.** Sales grew 29.5% in 2017 and 20.4% in 2018, but the margin slipped from 13.4% to 12.7% in 2018. Consumer, the largest segment, has the lowest margin (11.5%).

## Customer Purchase Volume
- 793 customers placed a median of 6 orders each over four years (range 1 to 17).
- The top 10 customers account for only 6.7% of sales, so revenue does not depend on a few large accounts.
- Highest sales does not mean highest profit: the top customer by revenue, Sean Miller ($25,043), generated a net loss of $1,981.

## Recommendations
- Cap discounts at 20% unless there is a clear volume case.
- Plan inventory and marketing around the Q4 peak, and use promotions to lift the slow early-year months.
- Review Furniture pricing and discount rules, starting with Tables.
- Investigate why the Central region's margin is so low.
- Protect margin while growing, and shift Consumer promotions toward higher-margin categories.

## How to Run
1. Create a virtual environment and install the libraries: `pip install pandas numpy matplotlib seaborn ipykernel`
2. Place `superstore_sales.csv` in the project folder.
3. Open `superstore_eda.ipynb`, select the `.venv` kernel and click **Run All**.

## Files
- `superstore_eda.ipynb`: full analysis with annotated findings
- `README.md`: project summary