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

