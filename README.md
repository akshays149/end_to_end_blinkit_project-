# Blinkit End-to-End Sales Analysis

<img width="1416" height="752" alt="Gemini_Generated_Image_x2krimx2krimx2kr" src="https://github.com/user-attachments/assets/9d71d2fe-30f5-43c3-a868-5c5765b9c5dd" />



An end-to-end retail analytics project built on Blinkit sales data using **Excel for exploratory data analysis**, **SQL Server for data cleaning and KPI analysis**, and **Power BI for interactive dashboarding**.

## Project Objective

The objective of this project is to analyze Blinkit’s sales performance, customer satisfaction, and inventory distribution to uncover meaningful insights and support business decision-making.

## Business Problem

Blinkit wants to understand:
- Which product categories generate the highest sales.
- How fat content affects sales performance.
- How outlet size, location, and type influence revenue.
- What patterns exist across customer ratings and item visibility.
- Which business segments contribute most to overall performance.

## Tools Used

- Microsoft Excel
- SQL Server
- Power BI
- Data Visualization
- Business Intelligence

## Dataset Overview

The dataset includes sales and outlet-related attributes such as:
- Item Type
- Item Fat Content
- Total Sales
- Rating
- Item Visibility
- Outlet Type
- Outlet Size
- Outlet Location Type
- Outlet Establishment Year

## Project Workflow

### 1. Excel EDA
Excel was used for the initial exploratory data analysis to understand:
- Data structure.
- Category distribution.
- Sales patterns.
- Basic trends before SQL transformation.

### 2. SQL Data Cleaning and Analysis
SQL was used to clean the dataset and calculate business KPIs.

#### Data Cleaning
The `Item_Fat_Content` field was standardized to improve consistency in reporting and analysis.

```sql
UPDATE blinkit_data
SET Item_Fat_Content =
    CASE
        WHEN Item_Fat_Content IN ('LF', 'low fat') THEN 'Low Fat'
        WHEN Item_Fat_Content = 'reg' THEN 'Regular'
        ELSE Item_Fat_Content
    END;
```

To verify the update:

```sql
SELECT DISTINCT Item_Fat_Content
FROM blinkit_data;
```

#### KPI Queries
- Total Sales
- Average Sales
- Number of Items
- Average Rating

#### Analytical Queries
- Total Sales by Fat Content
- Total Sales by Item Type
- Fat Content by Outlet for Total Sales
- Total Sales by Outlet Establishment
- Percentage of Sales by Outlet Size
- Sales by Outlet Location
- All Metrics by Outlet Type

### 3. Power BI Dashboard
A Power BI dashboard was built to visualize the key findings and make the analysis interactive.

#### Dashboard Components
- KPI cards for Total Sales, Average Sales, Number of Items, and Average Rating.
- Bar charts for sales by item type.
- Donut or pie charts for sales by fat content.
- Clustered bar charts for outlet-wise analysis.
- Trend visuals for outlet establishment year.
- Filters and slicers for dynamic exploration.

## Key Insights

- Fruits and Vegetables, Snack Foods, and Household items were among the top-selling item types.
- Tier 3 outlets generated the highest sales among outlet locations.
- Medium-sized outlets contributed the largest share of sales.
- Supermarket Type1 performed strongly across overall metrics.
- Low Fat products contributed more to total sales than Regular products.

## SQL Summary

### KPI Calculation
```sql
SELECT CAST(SUM(Total_Sales) / 1000000.0 AS DECIMAL(10,2)) AS Total_Sales_Million
FROM blinkit_data;

SELECT CAST(AVG(Total_Sales) AS INT) AS Avg_Sales
FROM blinkit_data;

SELECT COUNT(*) AS No_of_Orders
FROM blinkit_data;

SELECT CAST(AVG(Rating) AS DECIMAL(10,1)) AS Avg_Rating
FROM blinkit_data;
```

### Business Analysis
- Sales by fat content.
- Sales by item type.
- Sales by outlet location.
- Sales by outlet size.
- Sales by outlet type.
- Sales by establishment year.



## Deliverables

- Excel EDA workbook.
- SQL cleaning and analysis queries.
- Power BI dashboard.
- Presentation and documentation files.


## Learning Outcome

This project demonstrates how raw business data can be transformed into actionable insights using Excel, SQL, and Power BI. It also shows practical retail analytics skills useful for data analyst and business analyst roles.

## Future Scope

- Add forecasting for sales trends.
- Include time-series analysis.
- Build drill-through dashboard pages in Power BI.
- Extend analysis using Python for deeper statistical insights.
