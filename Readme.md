# Product Revenue, Volume & Growth Analysis

## Objective
Analyse product sales performance over a three-month period (April–June 2025) to identify revenue trends, distinguish high-performing products from underperforming ones, and provide actionable insights for inventory management and sales optimization.  
The analysis tracks growth patterns and highlights opportunities for strategic decision-making.

---

## Data Cleaning Process Documentation

### Project: Product Performance Analysis

### 1. Data Source & Structure
- **Source:** Raw datasets extracted from operational database  
- **Format:** Excel workbooks (.xlsx)

**Tables:**
- Products table  
- Orders table  

**File Organization:**
```📁 Project Folder
├── 01_raw_data_uncleaned.xlsx
│ ├── Products_raw
│ └── Orders_raw
├── 02_cleaned_data.xlsx
│ ├── Products_clean
│ └── Orders_clean
├── 03 My_SQL Project
└── 04 Power BI Dashboard 
```


The raw dataset was duplicated to create a cleaned version, preserving the original data for transparency and reference.

---

### 2. Data Quality Issues Identified
- **Duplicate Records:** Checked – No duplicates found  
- **Null/Missing Values:** Checked – No null values found  
- **DateTime Format:** Date and time combined in a single column  
- **Column Headers:** Inconsistent or unclear naming  
- **Product Names:** Formatting inconsistencies  
- **Irrelevant Columns:** Extra/unnecessary columns present  

---

### 3. Data Cleaning Steps Performed
- Removed duplicates (none found)
- Verified absence of null values
- Standardized DateTime columns to date-only format (YYYY-MM-DD)
- Standardized column headers and product names:
  - Fixed capitalization inconsistencies  
  - Trimmed extra whitespaces  
- Removed irrelevant ID column  

---

## SQL Analysis

The dataset was analysed using **SQL Server Management Studio (SSMS)**.  
Orders and Products tables were used to derive insights related to sales performance, order behaviour, and product trends.

### Analytical Tasks Completed:
1. Duplicate detection to ensure data integrity  
2. Top 3 best-selling products per day  
3. Daily order volume analysis  
4. Average order value per order_id  
5. Highest revenue-generating product  
6. Top 5 most frequently ordered products (regardless of quantity)  
7. Stored procedure to return total sales by product for a selected date range  
8. Identification of products never ordered  
9. Count of distinct products per order_id  

---

## Power BI

### 1. Data Import & Preparation
- Cross-checked column data types  
- Verified table relationships  
- Confirmed error-free data load  
- Validated record counts against source files  
- Checked for import warnings or errors  

---

### 2. Data Modelling
- Star schema implemented  
- Quantity used as fact table  
- Relationships established between Orders and Products  
- Relationship type: Many-to-One  

---

### 3. Dashboard Structure
The dashboard consists of **three pages** designed to provide comprehensive insights into product performance during Q2 2025:

1. Executive Overview  
2. Product Trend Analysis (Top & Declining Products)  
3. Revenue Growth & Distribution  

---

### 4. Key Performance Indicators (KPIs)
- Total Revenue  
- Total Orders  
- Total Products Sold  
- Average Order Value  
- Total Products  

---

### 5. Visualizations & Charts

#### Page 1: Executive Overview
- **Chart 1:** Top 10 Products by Revenue  
  - Visual Type: Clustered Bar Chart (Horizontal)  
  - Colour: Green  
  - Sort: Descending by revenue  

- **Chart 2:** Bottom 10 Products by Revenue  
  - Visual Type: Clustered Bar Chart (Horizontal)  
  - Colour: Red  
  - Sort: Ascending by revenue  

- **Chart 3:** Total Orders by Month  
  - Visual Type: Clustered Bar Chart  

- **Chart 4:** Total Revenue by Year, Quarter, and Day  
  - Visual Type: Line Chart  

- **Chart 5:** Revenue by Month  
  - Visual Type: Line Chart  

---

#### Page 2: Product Trend Analysis
- **Chart 6:** Product Revenue Trends by Month (Top Products)  
  - Visual Type: Multi-Line Chart  

- **Chart 7:** Total Orders of Top 10 Products  
  - Visual Type: Clustered Bar Chart  

- **Chart 8:** Product Revenue Trends by Month (Bottom Products)  
  - Visual Type: Multi-Line Chart  

- **Chart 9:** Total Orders of Bottom 10 Products  
  - Visual Type: Clustered Bar Chart  

---

#### Page 3: Revenue Distribution
- **Chart 10:** Revenue Growth by Month  
  - Visual Type: Table  

- **Chart 11:** Total Revenue by Product  
  - Visual Type: Pie / Donut Chart  

- **Chart 12:** MoM Growth % of Products  
  - Visual Type: Waterfall Chart  
  - Colour: Green (Increase), Red (Decrease)  

---

### 6. Slicers
- Month  
- Product Name  
- Date Range  

---

### 7. DAX Measures
```DAX
Total Revenue = SUM(Orders[total])
Total Orders = DISTINCTCOUNT(Orders[order_id])
Total Quantity = SUM(Orders[quantity])
Average Order Value = DIVIDE([Total Revenue], [Total Orders], 0)
MoM Growth % = DIVIDE([Total Revenue] - [Previous Month Revenue], [Previous Month Revenue], "N/A")
```

# 📊 Project Dashboard Overview

## 📌 Executive Overview
![Executive Overview](Executive%20Overview.PNG)

This section provides a high-level summary of the project performance, highlighting key metrics and overall business insights.

---

## 📈 Product Trend
![Product Trend](Product_Trend.PNG)

This visualization shows product performance trends over time, helping to identify demand patterns and top-performing categories.

---

## 💰 Revenue Growth
![Revenue Growth](Revenue_Growth.PNG)

This chart presents revenue performance across periods, showing growth trends and overall financial progress.

---

### 8. Insights

Revenue from April–June 2025 was highly volatile, with low activity in April–May and an isolated spike in late May, ending the quarter in decline.

Core products such as Chaii, Lunch Normal, Fruit, Coffee, and Idli/Sambar Bada drive the majority of revenue and volume.

Executive Lunch reflects premium pricing, while Chach shows underpricing despite high volume.

Bottom products reveal pricing failures and complete underperformance across revenue and quantity.

Products selling ≤29 units show structurally weak demand.

Revenue growth is concentrated in a few core products, with limited contribution from the long tail.

### 9. Recommendations

Investigate and validate the May revenue spike to understand key drivers.

Build customer loyalty programs to reduce revenue volatility.

Optimize pricing for underpriced items and introduce bundle offers.

Discontinue loss-making products and correct severe underpricing immediately.

Shift focus toward high-revenue core products and rationalize the product mix.

Avoid treating low-base MoM spikes as true growth signals; prioritize sustainable profitability.







