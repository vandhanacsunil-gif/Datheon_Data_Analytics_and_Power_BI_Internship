# Task 3: Customer Cohort & Churn Analytics

Customer retention analysis of the IBM Telco Customer Churn dataset (7,043 customers), built in Power BI. Customers are segmented by tenure cohort, contract type, internet service, payment method and monthly charges to quantify churn and identify high-risk segments.

## Files
| File | Description |
|---|---|
| `Churn_Analysis.pbix` | Interactive Power BI report (2 pages) |
| `Churn_Analysis_Dashboard.pdf` | PDF export of the dashboard |
| `Churn_Analysis_Report.docx` / `.pdf` | Written churn analysis and retention recommendations |
| `telco_customer_churn.csv` | Source dataset |

## Method
**Power Query**
- Converted `TotalCharges` to a decimal number and replaced errors (blank values for new customers) with 0.
- Added `Churn Flag` (1 if churned, else 0).
- Added `Tenure Cohort`: 0-12, 13-24, 25-36, 37-48, 49-60 and 61-72 months.
- Added `Monthly Charges Band`: under $35, $35-70, $70-90 and $90+.

**DAX measures**
| Measure | Definition |
|---|---|
| Total Customers | `COUNTROWS(Telco)` |
| Churned Customers | Customers where Churn = "Yes" |
| Churn Rate % | `DIVIDE([Churned Customers], [Total Customers], 0)` |
| Retention Rate % | `1 - [Churn Rate %]` |

## Dashboard Pages
**Churn Overview**
- KPI cards: Churn Rate %, Total Customers, Churned Customers, Retention Rate %
- Cohort retention heatmap: Tenure Cohort by Contract type
- Churn by Internet Service and Tech Support (internet customers only)
- Churn by Contract type and by Payment Method
- Slicers: Contract, gender, SeniorCitizen

**Retention & Pricing**
- Churn Rate by Monthly Charges band
- Retention curve by tenure (months)

## Key Findings
- Overall churn is **26.5%**, with retention of 73.5%.
- **Contract type is the strongest driver:** month-to-month customers churn at **42.7%**, versus 11.3% on one-year and 2.8% on two-year contracts.
- **New customers are most at risk:** month-to-month customers in their first 12 months churn at **51.4%**. Churn falls steadily with tenure.
- **High-risk segment:** Fiber optic customers without tech support churn at **49.4%**, versus 22.6% with tech support. DSL shows the same pattern (27.8% without, 9.7% with).
- **Electronic check** payers churn more than any other payment method.
- **Price sensitivity:** churn peaks in the $70-90 monthly charges band (about 38%).
- Retention rises from about 40% at the shortest tenures to over 90% for long-tenure customers.

## Recommendations
1. Offer incentives to move customers from month-to-month to one- or two-year contracts.
2. Run an onboarding and early-tenure programme for the first 12 months.
3. Bundle or discount tech support for Fiber optic customers.
4. Encourage automatic payments over electronic check.
5. Review pricing and retention offers for the $70-90 band.
6. Track churn by cohort monthly using the dashboard.

## How to Open
Open `Churn_Analysis.pbix` in Power BI Desktop. The PDFs are static copies of the dashboard and the written report.
