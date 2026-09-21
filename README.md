# 📊 Power BI Sales Analytics Dashboard

![Power BI Dashboard](screenshots/01-exec-dashboard.jpg)

## 📌 Project Overview

This project showcases an end-to-end **Business Intelligence and Data Analytics workflow** using Microsoft Power BI. The objective was to transform raw sales data into an interactive analytical solution that enables stakeholders to monitor business performance, identify trends, and make data-driven decisions.

The project demonstrates practical skills in:

- Data Extraction & Transformation (ETL)
- Data Modeling
- DAX Calculations
- Business KPI Development
- Interactive Dashboard Design
- Data Storytelling & Visualization

The final dashboard provides insights into **sales performance, profitability, customer behavior, product analysis, and geographic distribution**.

---

# 🎯 Business Objectives

The dashboard was designed to answer key business questions:

- How is overall sales and profit performance trending?
- Which products generate the highest revenue and profit?
- Which customer segments contribute the most sales?
- What is the return rate and its impact on profitability?
- How does sales performance vary across regions?
- Are business targets being achieved?

---

# 🔄 Data Preparation & ETL Process

A complete ETL pipeline was developed using **Power Query** to transform raw data into a structured analytical dataset.

## 1. Data Extraction

Raw data was imported from CSV files and folder-based sources.

Key activities:

- Imported multiple raw datasets into Power Query
- Combined multiple files into unified tables
- Prepared data sources for transformation and modeling

---

## 2. Data Transformation & Cleaning

Data cleaning and preparation steps included:

✔ Removed errors and unnecessary empty rows  
✔ Eliminated duplicate records  
✔ Handled missing values  
✔ Standardized column names  
✔ Corrected data types  
✔ Split and merged columns where required  
✔ Created additional calculated columns for analysis  
✔ Extracted useful business attributes from existing fields  

### Calendar Table Development

A dedicated Calendar Table was created to support time intelligence analysis.

Additional date attributes included:

- Year
- Month
- Week
- Start of Year
- Start of Quarter
- Date hierarchy

---

## 3. Data Loading

The transformed datasets were loaded into Power BI for:

- Data modeling
- DAX calculations
- Dashboard development
- Interactive reporting

---

# 🧩 Data Modeling

A structured **Snowflake Schema data model** was created to improve performance, scalability, and reporting accuracy.

## Modeling Techniques Applied:

✔ Established relationships using Primary and Foreign Keys  
✔ Created one-to-many relationships between tables  
✔ Maintained single-direction filtering to avoid ambiguity  
✔ Optimized table structure using normalization principles  
✔ Hidden unnecessary fields to prevent incorrect filtering  
✔ Created a dedicated Measure Table for centralized DAX management  

### Data Model Architecture

![Data Model](screenshots/data-model.png)

---

# 🧠 DAX Development

DAX (Data Analysis Expressions) was used to create dynamic business calculations and analytical measures.

A separate **Measure Table** was created to organize all calculations and improve maintainability.

## Key Measures Created

### 📦 Sales Performance Metrics

**Total Orders**  
- Calculates total number of orders generated.

**Total Revenue**  
- Measures overall sales performance.

**Total Profit**  
- Tracks business profitability.

---

### 📈 Trend & Time Intelligence

**Previous Month Profit**

Analyzes month-over-month profitability changes.

**90 Days Rolling Profit**

Tracks moving profit performance over the last 90 days.

```DAX
90 Days Rolling Profit =
CALCULATE(
    [Total Profit],
    DATESINPERIOD(
        'Calendar Lookup'[Date],
        MAX('Calendar Lookup'[Date]),
        -90,
        DAY
    )
)
