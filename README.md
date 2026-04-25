# AdventureWorks Sales Analytics Dashboard

End-to-end sales analytics project built with SQL Server, SSMS, and Power BI using the Microsoft AdventureWorks dataset.

## Project Overview

This project analyzes AdventureWorks sales performance across time, product, customer, and territory dimensions. The goal was to build a portfolio-ready BI solution that starts from an OLTP database, prepares a SQL reporting layer, models the data in Power BI, and delivers a multi-page dashboard with KPI tracking and time intelligence.

## Tools Used

- SQL Server
- SQL Server Management Studio (SSMS)
- Power BI Desktop
- SQL
- DAX

## Project Workflow

The project was developed in the following stages:

1. Database exploration in SSMS
2. Sales dataset preparation with SQL joins
3. Fact and dimension modeling for Power BI
4. Power BI connection and first report page
5. Advanced DAX and time intelligence
6. Dashboard design and storytelling
7. Dashboard expansion for portfolio presentation

## Dashboard Pages

### 1. Executive Summary
High-level business overview with core KPIs and summary visuals:

- Total Sales
- Total Orders
- Total Customers
- Total Quantity
- Average Order Value
- Sales by Year
- Sales by Territory
- Top Products
- Sales by Product Category

### 2. Sales Trend Analysis
Time-based performance analysis with advanced DAX:

- Previous Year Sales
- YoY Growth
- YoY Growth %
- YTD Sales
- Running Total Sales
- Monthly sales trend
- Year-over-year comparison matrix

### 3. Product Analysis
Product performance broken down by category, subcategory, and product:

- Sales by Product Category
- Sales by Product Subcategory
- Top Products by Sales
- Total Quantity

### 4. Customer Analysis
Customer contribution and segmentation analysis:

- Total Customers
- Sales by Customer Type
- Top Store Customers
- Top Individual Customers
- Customers by Territory

### 5. Territory Analysis
Geographic sales performance analysis:

- Sales by Territory Group
- Sales by Territory Name
- Territory performance matrix
- Total Orders and Total Customers by region

## Data Modeling Approach

Instead of connecting raw OLTP tables directly to Power BI, a reporting layer was built with SQL views.

Main reporting objects:

- `bi.vw_FactSales`
- `bi.vw_DimProduct`
- `bi.vw_DimCustomer`
- `bi.vw_DimTerritory`
- `bi.vw_DimDate`

The model follows a star-schema-like structure:

- `vw_FactSales` as the central fact table
- Product, Customer, Territory, and Date as dimension tables

This approach improves:

- model clarity
- DAX reliability
- dashboard scalability
- interview/project explanation quality

## Key KPIs

### Basic KPIs

- Total Sales
- Total Orders
- Total Customers
- Total Quantity
- Average Order Value

### Advanced KPIs

- Previous Year Sales
- YoY Growth
- YoY Growth %
- YTD Sales
- Running Total Sales
- Previous Year Orders
- YoY Orders Growth %

## Sample DAX Measures

```dax
Total Sales = SUM(vw_FactSales[LineTotal])

Previous Year Sales =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(vw_DimDate[DateKey])
)

YoY Growth % =
DIVIDE(
    [YoY Growth],
    [Previous Year Sales]
)
```

## Key SQL Work

The SQL layer includes:

- schema and table exploration
- order header and order detail joins
- product, category, customer, and territory enrichment
- reporting views for Power BI
- date dimension generation for time intelligence

## Business Value

This dashboard helps answer questions such as:

- How much did the company sell?
- How is sales performance changing over time?
- Which products drive revenue?
- Which customers contribute most?
- Which territories perform best?
- Is performance improving compared to the previous year?

## Technical Focus

This project emphasizes:

- reporting-layer design on top of an OLTP source
- fact and dimension modeling for analytics
- Power BI semantic modeling
- DAX time-intelligence measures
- KPI design and business reporting
- multi-page dashboard storytelling

## Interview Summary

Short version:

I built an end-to-end sales analytics dashboard on top of the AdventureWorks dataset using SQL Server and Power BI. I started by exploring the OLTP database in SSMS, created a reporting layer with fact and dimension views, modeled the data in Power BI, built KPI and time-intelligence measures with DAX, and expanded the report into five focused pages covering executive summary, sales trends, product, customer, and territory analysis.

## Next Improvements

Possible future enhancements:

- profit and margin analysis
- customer segmentation
- map visuals for regional performance
- drill-through pages
- bookmarks and tooltip pages
