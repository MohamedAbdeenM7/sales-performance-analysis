# Sales Performance Analysis — Project Documentation

## 1. Project Background

The project analyzes retail transaction data to understand the company's sales and profitability performance.

The goal is to transform transactional data into meaningful business information through data preparation, modeling, DAX calculations, and interactive Power BI visualizations.

---

# 2. Project Objectives

The project aims to:

- Measure overall sales performance.
- Evaluate profitability.
- Identify high-performing products and categories.
- Analyze customer contribution.
- Compare regional performance.
- Analyze sales trends over time.
- Measure year-over-year performance.
- Evaluate shipping performance.

---

# 3. Analytical Approach

The project follows the following workflow:

```text
Raw Data
    ↓
Data Cleaning
    ↓
Data Transformation
    ↓
Data Modeling
    ↓
DAX Measures
    ↓
Exploratory Analysis
    ↓
Dashboard Development
    ↓
Business Insights
```

---

# 4. Data Preparation

Power Query is used to prepare the dataset before analysis.

### Data Quality Checks

The following checks are performed:

- Missing values
- Duplicate records
- Incorrect data types
- Invalid dates
- Numerical inconsistencies
- Category inconsistencies

### Data Types

Dates:

```text
Order Date → Date
Ship Date → Date
```

Numerical fields:

```text
Sales → Decimal
Profit → Decimal
Quantity → Whole Number
Discount → Decimal
```

Categorical fields:

```text
Category
Sub-Category
Region
State
City
Segment
Ship Mode
```

---

# 5. Data Model

The model uses a Date dimension connected to the Orders table.

```text
                 DateTable
                    │
                    │ 1 : *
                    ▼
                  Orders
```

Relationship:

```text
DateTable[Date]
        ↓
Orders[Order Date]
```

This structure allows the report to use DAX time-intelligence functions such as:

```text
SAMEPERIODLASTYEAR()
```

---

# 6. KPI Definitions

## Total Sales

Measures the total revenue generated from orders.

```DAX
Total Sales =
SUM(Orders[Sales])
```

## Total Profit

Measures the total profit generated.

```DAX
Total Profit =
SUM(Orders[Profit])
```

## Profit Margin

Measures profit as a percentage of sales.

```DAX
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

## Total Orders

Counts unique orders.

```DAX
Total Orders =
DISTINCTCOUNT(Orders[Order ID])
```

## Total Customers

Counts unique customers.

```DAX
Total Customers =
DISTINCTCOUNT(Orders[Customer ID])
```

## Average Order Value

Measures the average revenue generated per order.

```DAX
Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)
```

---

# 7. Dashboard Design

## Executive Overview

The first page provides a high-level summary of the business.

### Main KPIs

```text
Total Sales
Total Profit
Profit Margin
Total Orders
Total Customers
Average Order Value
```

### Main Visuals

```text
Sales Trend
Sales by Category
Profit by Category
Sales by Region
Sales vs Profit
```

---

## Product Analysis

The second page focuses on products.

### Main Questions

- Which products generate the highest sales?
- Which products generate the highest profit?
- Which sub-categories perform well?
- Are high-sales products also highly profitable?

### Main Visuals

```text
Top 10 Products by Sales
Top 10 Products by Profit
Sales by Sub-Category
Profit Margin by Sub-Category
```

---

## Customer & Regional Analysis

The third page focuses on customers and geographic performance.

### Main Questions

- Which customers generate the most sales?
- Which customer segments contribute the most revenue?
- Which regions perform best?
- Which states and cities contribute to regional performance?

### Main Visuals

```text
Top Customers
Sales by Segment
Profit by Segment
Regional Performance Matrix
```

---

# 8. Time Intelligence

Year-over-year analysis is implemented using the Date table.

### Sales Previous Year

```DAX
Sales LY =
CALCULATE(
    [Total Sales],
    SAMEPERIODLASTYEAR(DateTable[Date])
)
```

### Sales YoY %

```DAX
Sales YoY % =
DIVIDE(
    [Total Sales] - [Sales LY],
    [Sales LY],
    0
)
```

The same approach is used to analyze profit performance.

---

# 9. Business Analysis

The analysis should focus on relationships between:

```text
Sales
Profit
Products
Customers
Regions
Time
Shipping
```

For example:

A category with high sales but relatively low profit margin requires different business attention from a category with moderate sales and strong profitability.

Therefore, the project does not evaluate performance using revenue alone.

---

# 10. Final Insights

Final business insights will be added after completing the dashboard.

Each insight should follow this structure:

```text
Observation
    ↓
Evidence
    ↓
Business Meaning
    ↓
Possible Action
```

Example structure:

> **Observation:** A specific category generated a large share of sales but showed weaker profitability.

> **Evidence:** Sales and Profit Margin measures from the dashboard.

> **Business Meaning:** High revenue does not necessarily translate into strong profitability.

> **Possible Action:** Investigate discount levels, product costs, and pricing strategy.

The final version will replace this example with insights calculated from the actual dataset.

---

# 11. Limitations

The analysis is based on the available fields in the dataset.

The project does not include:

- Marketing expenditure
- Inventory levels
- Product costs beyond the available profit field
- Customer acquisition cost
- Employee information
- External economic factors

Therefore, conclusions should be limited to the information available in the dataset.

---

# 12. Future Improvements

Potential improvements include:

- Adding a dedicated Calendar table with fiscal periods.
- Adding customer segmentation.
- Adding RFM analysis.
- Adding profitability analysis by discount level.
- Adding advanced shipping analysis.
- Adding drill-through pages.
- Adding tooltip pages.
- Adding dynamic titles.
- Adding bookmarks for navigation.
- Connecting Power BI to a SQL database instead of a flat file.