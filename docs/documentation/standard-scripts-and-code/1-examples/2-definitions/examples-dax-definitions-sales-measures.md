---
id: dax-definitions-sales-measures
title: DAX Definitions for Sales Measures
desc: This document provides detailed definitions and explanations related to the DAX measures used in our Power BI projects, focusing on sales metrics.
tags:
  - DAX
  - Power BI
  - Base Measures
  - Business Intelligence
  - KPIs
created: {{date:2024-11-04}}
updated: {{date:2024-11-04}}
author: Eric Liles
version: 1.0
---

# DAX Definitions for Sales Measures

This document provides detailed definitions and explanations related to the DAX measures used in our Power BI projects. The primary source data is from the transaction and transaction entry tables in the `GHRAWarehouse` SQL Server, with appropriate dimension tables, ETL'd for specific use cases in Power BI or Excel PowerPivot reports.

## 1. Total Sales

### Definition:
Total Sales represents the sum of all sales amounts recorded in the transaction entry table. This measure provides a snapshot of the total revenue generated over a specified period.

### Data Source:
- **Table**: `TransactionEntry`
- **Calculated Column**: `Amount` (calculated as `Ext Price`, which is `price * qty`)

### Calculation:
The sum of all `Amount` values in the `TransactionEntry` table:
- `Total Sales = SUM(price * qty)`

---

## 2. Sales by Customer

### Definition:
Sales by Customer aggregates the total sales amount for each customer. This measure helps identify the contribution of individual customers to the overall sales.

### Data Source:
- **Fact Table**: `TransactionEntry`
- **Dimension Table**: `Customers`
- **Join Condition**: `TransactionEntry.CustomerID = Customers.CustomerID`

### Calculation:
The sum of `Amount` for each `CustomerID` in the `TransactionEntry` table, grouped by customer name from the `Customers` dimension table:
- `Sales by Customer = SUM(Amount) GROUP BY CustomerID`

---

## 3. Sales by Supplier

### Definition:
Sales by Supplier aggregates the total sales amount for each supplier. This measure helps understand the contribution of individual suppliers to the overall sales.

### Data Source:
- **Fact Table**: `TransactionEntry`
- **Dimension Table**: `Suppliers`
- **Join Condition**: `TransactionEntry.SupplierID = Suppliers.SupplierID`

### Calculation:
The sum of `Amount` for each `SupplierID` in the `TransactionEntry` table, grouped by supplier name from the `Suppliers` dimension table:
- `Sales by Supplier = SUM(Amount) GROUP BY SupplierID`

---

## 4. Year-to-Date Sales

### Definition:
Year-to-Date (YTD) Sales represents the cumulative total sales from the beginning of the year to the current date. This measure is useful for tracking performance within the current fiscal year.

### Data Source:
- **Fact Table**: `TransactionEntry`
- **Dimension Table**: `DateDim`
- **Join Condition**: `TransactionEntry.Date = DateDim.Date`

### Calculation:
The sum of `Amount` for all dates in the `TransactionEntry` table from the start of the year to the current date:
- `YTD Sales = SUM(Amount) WHERE Date >= Start of Year AND Date <= Current Date`

---

## 5. Sales Growth

### Definition:
Sales Growth measures the percentage change in sales compared to the previous period. This measure is crucial for understanding sales trends and evaluating growth over time.

### Data Source:
- **Fact Table**: `TransactionEntry`
- **Dimension Table**: `DateDim`
- **Join Condition**: `TransactionEntry.Date = DateDim.Date`

### Calculation:
Sales Growth is calculated as the difference between the current period's sales and the previous period's sales, divided by the previous period's sales, then multiplied by 100 to get a percentage:
- `Sales Growth = ((Current Period Sales - Previous Period Sales) / Previous Period Sales) * 100`

### Example Calculation:
If the total sales for the current month are $120,000 and the total sales for the previous month are $100,000, the Sales Growth is calculated as follows:
- `Sales Growth = ((120000 - 100000) / 100000) * 100`
- `Sales Growth = 20%`

---

This document provides clear and concise definitions and explanations for each DAX measure, based on data from the `GHRAWarehouse` SQL Server, ensuring clarity and understanding for business users, data analysts, and programmers.
