---
id: common-dax-measures
title: Examples Common DAX Measures
desc: A collection of common DAX measures used in Power BI reports and dashboards, including brief business explanations and corresponding code examples.
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

# Common DAX Measures

This document contains a collection of common DAX measures used in Power BI reports and dashboards, along with brief business explanations and the corresponding code. This is a group of examples to demonstrate the structure and layout of the scripts and serves as a starting point if needed to see how everything works.

## 1. Total Sales

### Business Explanation
Calculates the total revenue generated from sales transactions.

#### Code

Total Sales = SUM(Sales[Amount])

## 2. Sales by Customer

### Business Explanation
Summarizes the total sales amount for each customer.

#### Code

Sales by Customer =
SUMMARIZE(
    Sales,
    Customers[CustomerName],
    "Total Sales", [Total Sales]
)

## 3. Sales by Supplier

### Business Explanation
Summarizes the total sales amount for each supplier.

#### Code

Sales by Supplier =
SUMMARIZE(
    Sales,
    Suppliers[SupplierName],
    "Total Sales", [Total Sales]
)

## 4. Year-to-Date Sales

### Business Explanation
Calculates the total sales from the beginning of the year to the current date.

#### Code

YTD Sales =
CALCULATE(
    [Total Sales],
    DATESYTD(Calendar[Date])
)

## 5. Sales Growth

### Business Explanation
Calculates the growth of sales compared to the previous period.

#### Code

Sales Growth =
DIVIDE(
    [Total Sales] - [Previous Period Sales],
    [Previous Period Sales]
)



