# 🛒 Sales Analytics Report

## Sales Analytics Purpose: 
Empowering businesses to monitor, evaluate, and enhance their sales activities and outcomes by unveiling sales patterns, tracking essential performance indicators (KPIs) and driving informed decisions.

**Outcome:** Determine effective customer discounts, facilitate negotiations, and identify expansion opportunities in potential global markets.

---

## Reports List:
1. Customer Performance Report: Assessed Customer Net Sales performance across 2019, 2020, 2021 year period.
2. Market Performance vs Targets Report: Analyzed Market Net Sales performance against Net Sales Targets in 2021.
3. Top 10 Products Report: Identified Top 10 Products by Net Sales Increment % in 2021 vs 2020.
4. Division Report: Documented Divison level Net Sales performance across 2020 & 2021 with a focus on Net Sales Increment % in 2021 vs 2020.
5. Top & Bottom 5 Products Report: Identified the Top and Bottom 5 products by Qty sold across the 3 year period.
6. New Products 2021 Report: Assessed Net Sales performance of 16 new products launched in 2021.
7. Top 5 Country Report: Listed Top 5 countries leading Net Sales figures in 2021.

---

## Sales Analytics Reports Detailed Implementation:

### ETL:
1. Extract Data directly from the Sales folder containing 4 files: dim_customer.csv, dim_market.csv, dim_product.csv, fact_sales_monthly.csv (dim: Dimension/Lookup Table, fact: Fact Table). 
All files in the folder will be combined in Power Query. To separate them we’ll right click on main file and create references for all the individual files, this way if any data changes are done in the main file it will auto replicate in all the other files as well.
2. Data Cleaning: Check Data Quality: View → Enable Column Distribution & Column Quality. For Primary Keys (customer_code, product_code, market), Distinct and Unique values in column should be the same.
3. Data Transformation:
  i.] In dim_customer: Find and Replace values: AltiQ → AtliQ; Atliq → AtliQ
  ii.] In dim_market, when extracting region/subzone NA (North America) got interpreted as Not Available value: Find and Replace values: nan → NA
  iii.] In fact_sales_monthly, somewhere in the data pipeline negative values got introduced in the qty column: Column → Transform → Scientific → Absolute value
4. Data Load: Save & Load To all 4 files as Connection Only and load then to the Data Model.

### Business Report Design Components:
- Net Sales: We’ll get net_sales data from the fact_sales_monthly table from the net_sales_amount column.
- Year: We’ll extract year data from the fact_sales_monthly table from the date column.
- Division: We’ll get division data from the dim_product table from the division column.
- Country: We’ll get country data from the dim_market table from the market column.
- Region: We’ll get region data from the dim_market table from the region column.
- Customer: We’ll get customer data from the dim_customer table from the customer column.

### Data Modelling:
1. In Power Pivot Diagram View, Arrange the 4 tables in a Star Schema with the fact_sales_monthly table in the center. There will be Snowflake Schema between dim_customer and dim_market.
2. Configure Table Relationships:

|Primary Key| |Foreign Key|
|-|-|-|
|customer_code (PK, dim_customer)|→|customer_code (FK, fact_sales_monthly)|
|product_code (PK, dim_product)|→|product_code (FK, fact_sales_monthly)|
|market (PK, dim_market)|→|market (FK, dim_customer)|

### New dim_date table using Power Query:
- This will provide us with the Year data and an added advantage of implementing date hierarchy when required.
1. Power Query → New Query/New Source → Other Sources → Blank Query → Rename as dim_date → Add Query: = {Number.From(#date(2018,1,1))..Number.From(#date(2018,12,31))} → Edit Start Date as (2018,9,1) and End Date as (2021,8,1) as per the Sales data → Change column type to Date → Rename column to date → Extract Start of Month to new column, Rename to month → Extract Year to new column, Set Data type as text to avoid future aggregation
2. AtliQ Hardware follows a fiscal year that runs from September through August. If the Fiscal Year starts from Sep to Aug, then we need to convert the Calendar Year to the Fiscal year, to do this in this case we’ll have to add 4 months to the Calendar Date and the Year part of the new date will tell us the Fiscal year. E.g. Sep 2021 + 4 months = Jan 2022 → FY 22
3. We’ll add a custom column FY Month to dim_date to add the 4 months using DAX Formula: Date.AddMonths([month],4)
4. We’ll then add a custom column FY to get the Year part from the FY Month column using DAX Formula: Date.Year([FY Month]). This can also be done from Add Column Tab, Date → Year.
Remove year & FY Month column to avoid confusion.
5. In Power Pivot Data Model Diagram View, we’ll now configure the table relationship: date (PK, dim_date) → date (FK, fact_sales_monthly)

### Customer Sales Performance Report:
1. Insert Power Pivot from Insert Tab based on the Data Model created.
2. Add customer (from dim_customer) field to the Rows Area. Add region (from dim_market), market (from dim_market) & division (from dim_product) to Filters Area. Enable Select Multiple Items for Filters.
3. Create Net Sales Measure using DAX formula: SUM(fact_sales_monthly[net_sales_amount]) in the fact_sales_monthly table. Set data type as $ Currency with 2 decimal accuracy.
4. Now we’ll create separate Net Sales Measures for each FY. For this we’ll use the CALCULATE formulate to filter NetSales Measure in the Filter Context of FY column from dim_date table.

    Measure: NetSales2019 → =CALCULATE([NetSales], dim_date[FY]="2019")

    Measure: NetSales2020 → =CALCULATE([NetSales], dim_date[FY]="2020")

    Measure: NetSales2021 → =CALCULATE([NetSales], dim_date[FY]="2021")

    (Since we had set the FY column of type text to avoid aggregation we need to put them in double quotes as string.)

5. Add a comparison Measure NetSales2021vs2020 using DAX formula: =DIVIDE([NetSales2021], [NetSales2020],0) and format it as Number Percentage with 1 decimal accuracy.
6. Add the NetSales2019, NetSales2020, NetSales2021 & NetSales2021vs2020 Measures to the Values Area in Power Pivot.
7. To boost User Readability:

    i. Convert all NetSales Measures to Million denomination by changing the Value Field Number Format to Custom: $ #,##0.0,, "M" → This will give NetSales with 1 decimal accuracy in Million         Dollars.
   
    ii. Remove Gridlines and set Page Layout in View Tab along with Border setup.
   
8. Sort the Pivot Table by Descending NetSales 2021vs2020 Column values for best stakeholder experience in identifying Customers with high Sales Growth %. 
9. Configure Conditional Formatting:

    i. For all 3 NetSales Columns set Highlight Cell Formatting with 3 colour scale: White for low values, Light Yellow for average values and Dark Yellow for high values.
   
    ii. For the NetSales 2021vs2020 Column set Data Bar Formatting with Orange Gradient fill.
   
10. Add AtliQ Hardware Logo and “AtliQ Hardwares” as the Report Header Title. Add “Customer Net Sales Performance Report” as the Report Title.
