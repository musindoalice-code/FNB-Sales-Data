# 📈 Sales Performance & Price Elasticity Analysis

<p align="center">
  <img src="assets/Image.png" alt="Sales Performance and Price Elasticity Analysis Banner" width="100%">
</p>

<p align="center">
  <strong>Driving Insights. Optimizing Profitability.</strong>
</p>

<p align="center">

![SQL](https://img.shields.io/badge/SQL-Databricks-red?logo=databricks\&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-DAX-F2C811?logo=powerbi\&logoColor=black)
![Excel](https://img.shields.io/badge/Excel-Dashboard-217346?logo=microsoft-excel\&logoColor=white)
![Data Analysis](https://img.shields.io/badge/Data-Analysis-blue)
![Status](https://img.shields.io/badge/Status-Completed-success)

</p>

---

# 🎯 Project Overview

This project delivers an end-to-end analysis of **sales performance, profitability, pricing, promotions, and Price Elasticity of Demand** using transactional sales data.

The objective was not simply to report sales figures, but to answer an important business question:

> **Does selling more units and reducing prices actually create value for the business?**

Using **SQL, Excel, Power BI, and business analysis techniques**, this project investigates how changes in selling price influence customer demand and whether increased sales volume translates into improved profitability.

---

# 🏆 Executive Summary

The analysis revealed an important business challenge:

| KPI                            |                 Result |
| :----------------------------- | ---------------------: |
| 💰 Total Sales                 |    **R186.91 Million** |
| 📦 Total Quantity Sold         | **5.28 Million Units** |
| 💵 Gross Profit                |     **-R7.12 Million** |
| 📉 Gross Profit Margin         |             **-3.81%** |
| 🏷️ Average Unit Selling Price |             **R35.40** |

## 🚨 Key Finding

Despite generating substantial revenue and selling millions of units, the product recorded an **overall gross loss**.

This demonstrates a critical business principle:

> **High sales volume does not automatically mean high profitability.**

The analysis also suggests that customers are highly responsive to changes in price, meaning that promotions can increase demand—but potentially at the expense of profitability.

---

# 📂 Dataset Information

Each record represents sales activity for a specific day.

| Column           | Description                           |
| :--------------- | :------------------------------------ |
| 📅 Date          | Day on which sales occurred           |
| 💰 Sales         | Total Rand value of sales             |
| 💵 Cost Of Sales | Total Rand cost associated with sales |
| 📦 Quantity Sold | Total number of units sold            |

### Dataset Summary

* **Period:** December 2013 – November 2016
* **Granularity:** Daily
* **Records:** 1,053
* **Focus:** Sales, pricing, demand and profitability

---

# ❓ Business Questions

The project was designed to answer the following questions:

### 💰 Pricing Analysis

1. What is the daily sales price per unit?
2. What is the average selling price of the product?
3. How does price change over time?

### 📈 Profitability Analysis

4. What is the daily gross profit percentage?
5. What is the gross profit generated per unit?
6. Are high sales periods also profitable?

### 🏷️ Promotion Analysis

7. Which periods show evidence of promotional pricing?
8. How does customer demand respond to lower prices?
9. Does the product perform better or worse during promotional periods?

### 🧠 Advanced Business Analysis

10. What is the Price Elasticity of Demand?
11. Is demand elastic or inelastic?
12. What recommendations can improve sustainable profitability?

---

# 🧮 Key Metrics & Calculations

## 🏷️ Daily Sales Price per Unit

```text
Sales Price per Unit = Total Sales ÷ Quantity Sold
```

This metric measures the effective selling price of one unit on a particular day.

---

## 💰 Average Unit Sales Price

```text
Average Unit Sales Price = Total Sales ÷ Total Quantity Sold
```

A weighted calculation was used to ensure that high-volume days have the appropriate influence on the overall average.

---

## 💵 Gross Profit

```text
Gross Profit = Sales − Cost of Sales
```

---

## 📊 Gross Profit Margin

```text
Gross Profit % = Gross Profit ÷ Sales × 100
```

---

## 📦 Gross Profit per Unit

```text
Gross Profit per Unit = Gross Profit ÷ Quantity Sold
```

This metric helps determine whether each additional unit sold is contributing positively to profitability.

---

## 📉 Price Elasticity of Demand

Price Elasticity of Demand measures how strongly customer demand responds to changes in price.

```text
Price Elasticity of Demand =
% Change in Quantity Demanded ÷ % Change in Price
```

### Interpretation

| Elasticity | Meaning                                                      |
| :--------- | :----------------------------------------------------------- |
| `> 1`      | 🔥 Elastic demand – customers are highly responsive to price |
| `< 1`      | 🧱 Inelastic demand – customers are less responsive to price |
| `= 1`      | ⚖️ Unit elastic                                              |
| Negative   | Normal when price and demand move in opposite directions     |

---

# 🔍 Analytical Approach

The project followed a structured data analytics workflow:

```text
Raw Data
   ↓
Data Validation & Cleaning
   ↓
Exploratory Data Analysis
   ↓
Pricing & Profitability Metrics
   ↓
Promotion Identification
   ↓
Price Elasticity Analysis
   ↓
Business Insights & Recommendations
   ↓
Interactive Dashboards
```

---

# 🛠️ Tech Stack

| Tool                   | Purpose                                                    |
| :--------------------- | :--------------------------------------------------------- |
| 🗄️ SQL / Databricks   | Data extraction, transformation and analysis               |
| 📊 Power BI            | Data modelling, DAX measures and interactive dashboards    |
| 📗 Excel               | Calculations, exploratory analysis and executive dashboard |
| 🐍 Python *(Optional)* | Further validation and advanced analysis                   |

---

# 💻 SQL Analysis

SQL was used to calculate the core business metrics and analyse trends.

### Key SQL Concepts Used

* `SELECT`
* `WHERE`
* `ORDER BY`
* `GROUP BY`
* Aggregate Functions (`SUM`, `AVG`, `COUNT`)
* `CASE WHEN`
* Common Table Expressions (CTEs)
* Window Functions
* `LAG()`
* Date Functions

### Example: Unit Sales Price

```sql
SELECT
    Date,
    Sales,
    `Quantity Sold`,
    ROUND(
        Sales / NULLIF(`Quantity Sold`, 0),
        2
    ) AS Daily_Sales_Price_Per_Unit
FROM sales_master
ORDER BY Date;
```

### Example: Gross Profit Margin

```sql
SELECT
    Date,
    Sales - `Cost Of Sales` AS Gross_Profit,

    ROUND(
        (Sales - `Cost Of Sales`)
        / NULLIF(Sales, 0) * 100,
        2
    ) AS Gross_Profit_Percentage
FROM sales_master
ORDER BY Date;
```

---

# 📊 Power BI & DAX

Power BI was used to transform the analysis into an interactive business dashboard.

### Core DAX Measures

#### Total Sales

```DAX
Total Sales =
SUM('Sales Master'[Sales])
```

#### Total Quantity Sold

```DAX
Total Quantity Sold =
SUM('Sales Master'[Quantity Sold])
```

#### Gross Profit

```DAX
Gross Profit =
SUM('Sales Master'[Sales])
-
SUM('Sales Master'[Cost Of Sales])
```

#### Gross Profit %

```DAX
Gross Profit % =
DIVIDE(
    [Gross Profit],
    [Total Sales],
    0
)
```

#### Average Unit Sales Price

```DAX
Average Unit Sales Price =
DIVIDE(
    [Total Sales],
    [Total Quantity Sold],
    0
)
```

#### Gross Profit per Unit

```DAX
Gross Profit Per Unit =
DIVIDE(
    [Gross Profit],
    [Total Quantity Sold],
    0
)
```

---

# 📈 Dashboard Preview

The dashboard was designed to tell a clear business story:

### 1️⃣ What happened?

Sales performance and demand trends.

### 2️⃣ Was it profitable?

Gross profit, margins and unit economics.

### 3️⃣ How did customers respond to pricing?

Price trends, promotional periods and demand response.

### Key Dashboard Visuals

📈 **Monthly Sales Trend**
📦 **Monthly Quantity Sold Trend**
💵 **Gross Profit Performance**
🏷️ **Average Unit Price Trend**
📉 **Price vs Quantity Relationship**
🔥 **Promotion Performance Analysis**
📊 **Price Elasticity Analysis**

> 📌 Add your dashboard screenshot here once uploaded:

```markdown
![Sales Dashboard](visuals/dashboard_screenshot.png)
```

---

# 💡 Key Insights

## 🚨 High Sales Volume Did Not Translate Into Profitability

The product generated approximately **R186.91 million in sales**, but recorded an overall gross loss.

### Business implication:

> Revenue growth should never be evaluated independently from profitability.

---

## 📉 Customers Appear Price Sensitive

The analysis identified periods where lower selling prices were associated with stronger demand.

This suggests that customers are responsive to promotional pricing and that demand may be relatively elastic.

### Business implication:

> Pricing is a powerful lever for driving demand, but promotions should be carefully designed to protect margins.

---

## 🔥 Promotions Can Drive Volume—but Not Always Value

A successful promotion should not be measured solely by the number of units sold.

The business should evaluate promotional campaigns using:

* Incremental Sales
* Incremental Quantity
* Gross Profit
* Gross Profit Margin
* Profit per Unit

### Recommended approach:

> **Optimise promotions for profitable growth, not simply volume growth.**

---

## 💰 Profitability Should Be the North-Star Metric

The analysis highlights the importance of moving beyond vanity metrics such as total sales.

A stronger decision-making framework should focus on:

> **Revenue + Volume + Margin + Profitability**

---

# 🎯 Business Recommendations

Based on the analysis, I recommend the following:

### 1. Review Pricing Strategy 🏷️

Ensure that the selling price consistently covers the cost of sales and supports sustainable margins.

### 2. Optimise Promotional Pricing 🔥

Test promotional prices that stimulate demand without creating losses.

### 3. Monitor Unit Economics 📦

Track Gross Profit per Unit alongside sales volume.

### 4. Prioritise Profitable Growth 💰

Avoid strategies that increase revenue while worsening profitability.

### 5. Build a Pricing Performance Dashboard 📊

Continuously monitor price, quantity, margin and elasticity to support faster decisions.

---

# 🗂️ Repository Structure

```text
sales-performance-price-elasticity-analysis/
│
├── data/
│   └── Sales_Master.xlsx
│
├── sql/
│   ├── 01_daily_metrics.sql
│   ├── 02_monthly_analysis.sql
│   └── 03_price_elasticity.sql
│
├── powerbi/
│   └── Sales_Performance_Dashboard.pbix
│
├── excel/
│   └── Sales_Performance_Dashboard.xlsx
│
├── visuals/
│   └── dashboard_screenshot.png
│
├── assets/
│   └── Sales-Performance-Banner.png
│
└── README.md
```

---

# 🚀 How to Explore This Project

### Step 1️⃣ — Explore the Dataset

Review the raw sales data and understand the available measures.

### Step 2️⃣ — Run the SQL Analysis

Use the SQL scripts to reproduce the calculations and insights.

### Step 3️⃣ — Explore the Excel Dashboard

Open the Excel dashboard to investigate sales, pricing and profitability trends.

### Step 4️⃣ — Explore Power BI

Interact with the Power BI dashboard and compare KPIs across different periods.

### Step 5️⃣ — Draw Business Conclusions

Use the analysis to evaluate whether pricing and promotions are creating sustainable business value.

---

# 🌟 Why This Project Stands Out

This project demonstrates more than technical calculations.

It shows the ability to:

✅ Translate raw data into business questions
✅ Build meaningful KPIs
✅ Analyse pricing and profitability
✅ Apply Price Elasticity of Demand concepts
✅ Use SQL for analytical problem-solving
✅ Build calculations using DAX
✅ Create executive-ready dashboards
✅ Communicate insights and recommendations clearly

> **The goal of a Data Analyst is not just to find numbers—it is to explain what those numbers mean and help the business make better decisions.**

---

# 👩🏽‍💻 Author

**Data Analyst Portfolio Project**

### Skills Demonstrated

`SQL` • `Excel` • `Power BI` • `DAX` • `Data Analysis` • `Business Intelligence` • `Data Visualisation` • `Pricing Analytics` • `Business Insights`

---

<p align="center">
  ⭐ If you found this project interesting, feel free to explore the analysis and dashboards.
</p>

<p align="center">
  <strong>Turning Data into Insights. Turning Insights into Action. 📊</strong>
</p>



