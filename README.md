# 📊 Sales Analysis with Power BI  

## 📑 Table of Contents  
1. [Project Overview](#project-overview)  
2. [Data Sources](#data-sources)  
3. [Data Transformation](#data-transformation and ETL)  
   - [Power Query](#power-query)  
   - [Data Modeling](#data-modeling)  
   - [DAX Calculations](#dax-calculations)  
4. [Dashboards](#dashboards)  
5. [Results & Insights](#results--insights)  
6. [Limitations & Improvements](#limitations--improvements)  

---

## 🚀 Project Overview  
This project focuses on analyzing **Sales, Profit, and Budget** data using **Power BI**.  
The goal is to build interactive dashboards that help track performance across **categories, time, and geography**, while also comparing actual results to budgets and prior years.  

---

## 📂 Data Sources  
- **Sales dataset**: Transactions including sales, profit, quantity, customer, region, and category.  
- **Budget dataset**: Yearly and monthly budget allocations by category.  
- **Calendar table**: Date dimension created in Power Query for time intelligence.  

---

## 🔄 Data Transformation and ETL  

### 🔹 Power Query  
I performed several transformation steps to prepare the data for analysis:  
- Cleaned and standardized sales data (removed nulls, renamed columns).  
- Created a **Date Table** for time-based analysis.  
- Merged sales and budget datasets.  
- Changed data types and applied filters for valid transactions.  

### 🔹 Data Modeling  
The project follows a **Star Schema** approach:  
- **Fact Table**: Sales  
- **Dimension Tables**: Date, Product, Customer, Region, Category  
- Relationships were created to ensure accurate aggregations and filtering.  
- Added hierarchies (Year → Quarter → Month).  

📌 Data Model:  

![Data Model](datamodel.png)  

### 🔹 DAX Calculations  
I created multiple measures in DAX for KPIs and analysis. Some examples:  

```DAX
-- Total Sales
Total Sales = SUM(Sales[Sales])

-- Total Profit
Total Profit = SUM(Sales[Profit])

-- Sales vs Prior Year
Sales Prior Year = CALCULATE([Total Sales], DATEADD('Date'[Date], -1, YEAR))

-- Sales Variance %
Sales % Variance = 
DIVIDE([Total Sales] - [Sales Prior Year], [Sales Prior Year], 0)

-- Budget Achievement %
Budget Achievement = DIVIDE([Total Sales], [Total Budget], 0)



