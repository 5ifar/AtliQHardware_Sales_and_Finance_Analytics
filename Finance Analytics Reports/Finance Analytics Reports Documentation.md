# 💸 Finance Analytics Reports
---

## Table of Contents

---

## Finance Analytics Purpose:
Evaluating financial performance, aiding decision-making, and fostering stakeholder communication through benchmarking against industry peers, historical periods, and establishing the foundation for budgeting and forecasting.

**Outcome:** Aligning financial planning with strategic objectives and instilling confidence in the organization's financial outlook.

---

## Reports List:
1. P&L - Financial Years Report: Generated P&L reports categorized by markets and analyzed over metrics: NetSales, COGS, GrossMargin & GM% across financial years 2019, 2020 & 2021 with focus on Metric Increment in 2021 vs 2020.
2. P&L - Financial Months Report: Generated P&L reports analyzed over metrics: NetSales, COGS, GrossMargin & GM% across financial months cycle starting from Sep to Aug.
3. P&L - Markets Reports: Generated P&L reports categorized by markets and analyzed over metrics: NetSales, COGS, GrossMargin & GM% with a temporary filter context of FY 2021 (can be modified).
4. GM% - Financial Quarters Report: Analyzed GM% metric categorized by sub zones across financial quarters Q1 to Q4.

---

## Finance Analytics Reports Detailed Implementation:

### Import Finance Data:
1. Create New Query to import data thorugh CSV file fact_sales_monthly_with_cost.csv. Rename it to finance_ref. Configure Load as Connection Only and Add to Data Model.
2. Configure Table Relationships:

|Primary Key| |Foreign Key|
|-|-|-|
|customer_code (PK, dim_customer)|→|customer_code (FK, finance_ref)|
|product_code (PK, dim_product)|→|product_code (FK, finance_ref)|
|date (PK, dim_date)|→|date (FK, finance_ref)|

### P & L by Year Report:
1. Insert Power Pivot from Insert Tab based on the Data Model created.
2. Add NetSales Measure to the Values Area. Add region (from dim_market), market (from dim_market) & division (from dim_product) to Filters Area in Pivot table. Enable Select Multiple Items for Filters.
3. Add FY Measure from dim_date table to the Columns Area in Pivot table.
4. Create a new column total_cogs in the finance_ref Data Model table by adding both freight cost and manufacturing cost.
5. Create a new measure COGS in the finance_ref table referencing the total_cogs column using DAX formula: SUM(finance_ref[total_cogs]). Set data type as $ Currency with 2 decimal accuracy. Add this measure to the Values Area in Pivot table.
6. Create a new measure GrossMargin in the finance_ref table using the DAX formula: [NetSales] - [COGS]. Set data type as $ Currency with 2 decimal accuracy. Add this measure to the Values Area in Pivot table.
7. Create a new measure GM% in the finance_ref table using the DAX formula: DIVIDE([GrossMargin],[NetSales],0). Set data type as Number Percentage with 2 decimal accuracy. Add this Measure to the Values Area in Pivot table.
8. Convert the NetSales, COGS & GrossMargin measures to Million denomination by changing the Value Field Number Format to Custom: #,##0.0,, "M" → This will give measures with 1 decimal accuracy in Millions.
9. Configure Conditional Formatting:

    i. For NetSales, COGS, Gross Margin & GM% Metrics set Highlight Cell Formatting with 3 colour scale: White for low values, Yellow for average values and Dark Yellow for high values.
    ii. For the 2021vs2020 Column set Data Bar Formatting with Orange Gradient fill. Set Red Data bar for Negative values to be shown from cell midpoint.



