# Sales Performance Analysis

## 📊 Project Overview

This project analyzes retail sales data to understand sales performance, profitability, customer behavior, product performance, and regional trends.

The project uses **Power BI** to transform raw sales data into an interactive business intelligence dashboard that helps answer key business questions and identify performance patterns.

---

## 🎯 Business Objective

The main objective is to analyze sales and profit performance and provide clear insights that can support business decision-making.

The analysis focuses on:

- Sales performance over time
- Profitability and profit margin
- Product and category performance
- Customer performance
- Regional performance
- Order and quantity trends
- Shipping performance

---

## ❓ Business Questions

The dashboard answers the following questions:

1. What are the total sales and total profit?
2. How are sales changing over time?
3. Which product categories generate the most sales?
4. Which categories and sub-categories are the most profitable?
5. Which products generate the highest sales and profit?
6. Which regions and customers contribute the most revenue?
7. How does profitability vary across categories and regions?
8. What is the average order value?
9. How many customers and orders does the business have?
10. How does sales performance compare with the previous year?
11. How does shipping performance vary by shipping mode?

---

## 🛠️ Tools & Technologies

- **Power BI**
- **DAX**
- **Power Query**
- **Microsoft Excel / CSV**
- **Data Modeling**
- **Time Intelligence**
- **Git & GitHub**

---

## 📁 Dataset

The project uses the **Sample Superstore** retail dataset.

The dataset contains information related to:

- Orders
- Customers
- Products
- Categories
- Regions
- Sales
- Profit
- Quantity
- Discounts
- Shipping

### Main Columns

```text
Order ID
Order Date
Ship Date
Ship Mode
Customer ID
Customer Name
Segment
Country
City
State
Region
Product ID
Category
Sub-Category
Product Name
Sales
Quantity
Discount
Profit
```

---

## 🔄 Data Preparation

The data was prepared using Power Query.

Main preparation steps included:

- Checking column data types
- Converting date fields to Date format
- Checking missing values
- Checking duplicate records
- Validating numerical columns
- Standardizing categorical fields
- Preparing the dataset for analysis

---

## 🧩 Data Model

A dedicated Date table was created to support time-based analysis and DAX time intelligence.

### Model Structure

```text
DateTable
    │
    │ 1 : *
    │
    ▼
 Orders
```

The relationship is based on:

```text
DateTable[Date]
        ↓
Orders[Order Date]
```

The relationship uses:

- Cardinality: **One-to-Many**
- Cross-filter direction: **Single**

---

## 📅 Date Table

The Date table contains:

```text
Date
Year
Month Number
Month
Month Short
Quarter
Year Month
```

It is used for:

- Monthly analysis
- Yearly analysis
- Quarterly analysis
- Year-over-year comparison
- Time-series visualization

---

## 📐 Key DAX Measures

### Total Sales

```DAX
Total Sales =
SUM(Orders[Sales])
```

### Total Profit

```DAX
Total Profit =
SUM(Orders[Profit])
```

### Total Orders

```DAX
Total Orders =
DISTINCTCOUNT(Orders[Order ID])
```

### Total Customers

```DAX
Total Customers =
DISTINCTCOUNT(Orders[Customer ID])
```

### Total Quantity

```DAX
Total Quantity =
SUM(Orders[Quantity])
```

### Profit Margin

```DAX
Profit Margin =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

### Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Sales],
    [Total Orders],
    0
)
```

### Previous Year Sales

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

### Previous Year Profit

```DAX
Profit LY =
CALCULATE(
    [Total Profit],
    SAMEPERIODLASTYEAR(DateTable[Date])
)
```

### Profit YoY %

```DAX
Profit YoY % =
DIVIDE(
    [Total Profit] - [Profit LY],
    [Profit LY],
    0
)
```

### Average Shipping Days

```DAX
Average Shipping Days =
AVERAGEX(
    Orders,
    DATEDIFF(
        Orders[Order Date],
        Orders[Ship Date],
        DAY
    )
)
```

---

# 📊 Dashboard Structure

## Page 1 — Executive Overview

The Executive Overview provides a high-level view of business performance.

### KPI Cards

- Total Sales
- Total Profit
- Profit Margin
- Total Orders
- Total Customers
- Average Order Value

### Visualizations

- Sales Trend Over Time
- Sales by Category
- Profit by Category
- Sales by Region
- Sales vs. Profit

### Filters

- Year
- Region
- Category
- Sub-Category
- Segment
- Ship Mode

---

## Page 2 — Product Analysis

This page focuses on product and category performance.

### Visualizations

- Top 10 Products by Sales
- Top 10 Products by Profit
- Sales by Sub-Category
- Profit Margin by Sub-Category

The purpose is to identify high-performing products and categories and compare revenue generation with profitability.

---

## Page 3 — Customer & Regional Analysis

This page focuses on customer and geographic performance.

### Visualizations

- Top Customers
- Sales by Segment
- Profit by Segment
- Regional Performance Matrix

The matrix allows users to analyze:

```text
Region
   ↓
State
   ↓
City
```

with:

- Sales
- Profit
- Profit Margin
- Orders

---

## 📸 Dashboard Preview

Dashboard screenshots will be added to:

```text
screenshots/
```

Recommended files:

```text
executive_overview.png
product_analysis.png
customer_region_analysis.png
```

---

## 📂 Project Structure

```text
sales-performance-analysis/
│
├── data/
│   └── sales_data.csv
│
├── powerbi/
│   └── Sales_Analysis.pbix
│
├── screenshots/
│   ├── executive_overview.png
│   ├── product_analysis.png
│   └── customer_region_analysis.png
│
├── documentation/
│   ├── data_dictionary.md
│   └── project_documentation.md
│
└── README.md
```

---

## 💡 Key Insights

The final insights will be documented after completing the analysis.

Examples of insight categories include:

- Sales growth or decline over time
- Most important product categories
- Most profitable sub-categories
- Regional performance differences
- Customer contribution
- Relationship between sales and profit
- Shipping performance

> Insights should be based on the actual analysis results rather than assumptions.

---

## 🚀 Skills Demonstrated

This project demonstrates practical experience in:

- Data Cleaning
- Data Transformation
- Exploratory Data Analysis
- Business Analysis
- Data Modeling
- DAX
- Time Intelligence
- KPI Development
- Data Visualization
- Dashboard Design
- Business Storytelling
- Git & GitHub

---

## 👤 Author

**Mohamed Abdeen**

Data Analyst | Power BI Developer

- GitHub: github.com/MohamedAbdeenM7
- LinkedIn: linkedin.com/in/mohamed-abdeen-m7
- Portfolio: mohamedabdeenm7.github.io/Portfolio