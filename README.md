# <img src="https://miro.medium.com/v2/resize:fit:1400/1*8bUjUiCWk0VhS8-lgAj0Og.png" width="4%" height="4%"> AtliQ Hardware - Sales & Finance Analytics

<img src="https://github.com/5ifar/AtliQHardwares_Sales_and_Finance_Analytics/blob/main/Assets/Project%20Repo%20Banner.png" width="100%" height="100%">

This repository serves as my documentation for the AtliQ Hardware Sales & Finance Analytics Excel Project.
It was created as a self-learning project for the course: [Excel: Mother of Business Intelligence](https://codebasics.io/courses/excel-mother-of-business-intelligence) by [Codebasics](https://codebasics.io/).

It showcases my competancy to work with Microsoft Excel and demonstrates my proficiency in essential Excel concepts like ETL with Power Query, Data Modelling, VLOOKUP/INDEX-MATCH/XLOOKUP Table Joining, Pivot Table, Power Pivot, DAX Measures, Conditional Formating etc.

The entire project has been implemented using Microsoft Excel 2016.

The project files have not been uploaded to this repository in compliance with Codebasics Data & Content Distribution Policy.

---

## Introduction:
**Domain:** FMCG | **Functions:** Sales & Finance

- AtliQ Hardwares is company that sells computer hardware and peripherals like PC, mouse, printer etc. to clients across the world.
- They have a major B2B business model wherein they sell to stores like Croma, Best Buy, Staples, Flipkart etc. who then sell it to the end users (consumers). These stores are their main customers.
- They sell through 3 channels: Retailer, Direct and Distributor.
- AtliQ Hardwares’s Customers are of two types. Both these Platforms are called Retailer channels.
  1. Brick & Mortar Customer: Actual physical stores e.g. Croma, Best Buy
  2. E-commerce Customer: Online websites E.g. Amazon, Flipkart
- AtliQ Hardwares also has a minor B2C business model wherein they own stores: AtliQ E-store and AtliQ Exclusive. These are called Direct channels.
- They also have Distributors in some countries with restricted trade. E.g. Neptune

## Problem Statement:
AtliQ Hardwares is facing significant losses in recent years. They have been relying on hand written reports for business decisions. They are in a dire need of insights for informed data driven decision making.

**Business Requirement:** AtliQ’s business users have tasked the Data Analyst team with preparing an Excel Analysis Report focused on Sales and Financial performance by analyzing data from multiple files with over 1.5 million records to help them derive data insights towards boosting business growth.

## Table of Contents:
Please find the resource links for the project below:
- [Introduction](#introduction)
  - [Problem Statement](#problem-statement)
- [AtliQ Hardware Compiled Report](https://github.com/5ifar/AtliQHardware_Sales_and_Finance_Analytics/blob/main/AtliQ%20Hardware%20Compiled%20Report.pdf)
- [Sales Analytics Reports](https://github.com/5ifar/Sales_and_Finance_Analytics_of_AtliQHardwares/tree/main/Sales%20Analytics%20Reports/Sales%20Analytics%20Reports%20Files)
  - [Sales Analytics Reports Documentation](https://github.com/5ifar/Sales_and_Finance_Analytics_of_AtliQHardwares/blob/main/Sales%20Analytics%20Reports/Sales%20Analytics%20Reports%20Documentation.md)
- [Finance Analytics Reports](https://github.com/5ifar/Sales_and_Finance_Analytics_of_AtliQHardwares/tree/main/Finance%20Analytics%20Reports/Finance%20Analytics%20Reports%20Files)
  - [Finance Analytics Reports Documentation](https://github.com/5ifar/Sales_and_Finance_Analytics_of_AtliQHardwares/blob/main/Finance%20Analytics%20Reports/Finance%20Analytics%20Reports%20Documentation.md)
- [AtliQ Hardware Report Presentation](https://github.com/5ifar/AtliQHardware_Sales_and_Finance_Analytics/blob/main/AtliQ%20Hardware%20Report%20Presentation.pptx)
- [Tools used & Methodologies implemented](#tools-used)
- [About the Dataset](#about-the-dataset)
  - [Data Integrity](#data-integrity)
- [Data Model - ERD](#data-model)
- [Analysis Insights](#analysis-insights)

## Tools used:
1. Microsoft Excel: for Data Cleaning, Data Analysis & Visualization
2. Microsoft Powerpoint: for creating Project Presentation
3. DataWrapper: for Insights Visuals
4. GitHub - for Documentation

## Skills & Methodologies implemented:
1. Data Cleaning: Power Query
2. Data Manipulation: DAX Measures & Columns
3. Data Modelling and Normalization
4. Data Visualization: Pivot Table, Power Pivot, Conditional Formatting
5. Documentation

## About the Dataset:
### Data Sources: Sales & Finance

![image](https://github.com/5ifar/AtliQHardwares/assets/146955609/fc7d37af-acbf-4596-83dc-8335ee737b0b)

- dim_customer: 189 records | 5 columns
- dim_market: 23 records | 3 columns
- dim_product: 298 records | 6 columns
- fact_sales_monthly: 799962 records | 5 columns
- ns_targets_2021: 276 records | 3 columns
- fact_sales_monthly_with_cost: 799962 records | 7 columns

### Data Dictionary:
-to be added-

## Data Integrity:
ROCCC Evaluation:
- Reliability: MED - The raw dataset is created and updated by Codebasics. It has 6 files.
- Originality: HIGH - First party provider (Codebasics)
- Comprehensiveness: MED - Total 6 CSV Files were provided. Dataset contains multiple parameters for Customers, Products & Markets as well as comprehensive Sales & Finance transaction data.
- Current: LOW - Dataset was updated upto 2021, almost 3 years old. So its obsolete & not very relevant.
- Citation: LOW - No official citation/reference available.

---

## Data Model:
### Entity Relationship Diagram (ERD):

<img src="https://github.com/5ifar/AtliQHardware_Sales_and_Finance_Analytics/blob/main/Assets/AtliQ%20Hardware%20Data%20Model%20ERD%20Final.JPG" width="100%" height="100%">

---

## Analysis Insights:
- Customer `Amazon` tops the charts by grossing Net Sales of `$ 82.1 Million` in `2021`, while experiencing the lowest sales increment rate of `120%`.

<img src="https://datawrapper.dwcdn.net/MYLHC/full.png" alt="" />

- Customer `Nova` comes out with the Lowest Net Sales of `$ 0.4 Million` in `2021`, while it experienced a sudden high surge in Sales with the Net Sales figure increasing almost `26.6` times from 2020 to 2021.

<img src="https://datawrapper.dwcdn.net/qU7i7/full.png" alt="" />

- `India` dominates as the forerunner with Net Sales at a staggering `$ 161.3 Million` in `2021`, while missing to meet its 2021 Net Sales Targets by `$ 9.6 Million (5.6%)`.

<img src="https://datawrapper.dwcdn.net/aLbnS/full.png" alt="" />

- Across the globe, `Poland` fails to meet its `2021` Net Sales Targets by the widest margin of around `-15%`.

<img src="https://datawrapper.dwcdn.net/qxZsY/full.png" alt="" />

- Top 3 customers: `Amazon`, `AtliQ Exclusive`, `AtliQ e-store` in `2021` with individual Net Sales over `$ 50 Million`.

<img src="https://datawrapper.dwcdn.net/j22dx/full.png" alt="" />

- Top Selling Product: `AQ Master wired x1 Ms` with over `4.2 Million` units sold from `2019` to `2021`.

<img src="https://datawrapper.dwcdn.net/Xj08J/full.png" alt="" />

- Top Surging Product: `AQ Mx NB` surges in demand almost `57` times from `2020` to `2021`.

<img src="https://datawrapper.dwcdn.net/OdCYE/full.png" alt="" />

- Top New Product: `AQ Qwerty` leading sales at `$ 22 Million` among the 16 new products introduced in `2021`.

<img src="https://datawrapper.dwcdn.net/mcbgG/full.png" alt="" />

- Gross Margin % takes the biggest hit of `-3.1%` in `2021` compared to `2020` for the `PC` region.
- Sales peak consistently during Festive season months from `October` to `December` across the globe following the trend across years.
