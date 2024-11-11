---
id: time-based-measures-definitions
title:  Time-Based Measures Definitions
desc: This document provides detailed definitions and explanations for time-based measures used in the Power BI model. It includes a set of DAX measures for tracking inventory, cost of goods sold (COGS), and other relevant time-series data.
tags:
  - DAX
  - Power BI
  - Time-Based Measures
  - Business Intelligence
  - KPIs
created: 2024-11-11
updated: 2024-11-11
author: Eric Liles
version: 1.0
---

# Time-Based Measures Definitions

This document provides detailed definitions and explanations of the DAX measures used in our Power BI projects for time-based analysis, including inventory, cost of goods sold (COGS), and other relevant time-series KPIs.

## 1. [Average COGS $ Year (Base KPI)](#1-average-cogs-year-base-kpi)

### Business Explanation:
Calculates the average cost of goods sold (COGS) over the past year.

### Explanation:
The `Average COGS $ Year (Base KPI)` measure calculates the average cost of goods sold over the last 365 days, using the `TrxEntry[Ext COGS $]` column and the `DateDim[Date]` table to filter the data for the relevant period.

### Example Use Case:
- **Report**: COGS Analysis
- **Purpose**: To assess the average cost of goods sold over the past year to monitor profitability and trends.

### Recommended Visuals:
- **Line Chart**: Displays the average COGS over the past year.
- **KPI Visual**: Highlights the average COGS for quick insights.

## 2. [Average Inventory $ Year (Base KPI)](#2-average-inventory-year-base-kpi)

### Business Explanation:
Calculates the average inventory value over the past year.

### Explanation:
The `Average Inventory $ Year (Base KPI)` measure calculates the average inventory value over the past 365 days, using data from the `Inventory History` table and the `DateDim[Date]` table.

### Example Use Case:
- **Report**: Inventory Management
- **Purpose**: To understand trends in inventory value over the last year and help with stock planning.

### Recommended Visuals:
- **Line Chart**: Displays the average inventory value over the past year.
- **KPI Visual**: Highlights the average inventory value for performance tracking.

## 3. [WoW LW vs 2W # of Items % Var (KPI)](#3-wow-lw-vs-2w-items-percent-var-kpi)

### Business Explanation:
Calculates the percentage variance of the number of items between last week and two weeks ago.

### Explanation:
The `WoW LW vs 2W # of Items % Var (KPI)` measure calculates the percentage variance of the number of items, comparing the counts from last week and two weeks ago. It uses `Last Week # of Items (Time)` and `2 Weeks Ago # of Items (Time)`.

### Example Use Case:
- **Report**: Sales Trend Analysis
- **Purpose**: To monitor fluctuations in the number of items between last week and the previous week.

### Recommended Visuals:
- **Column Chart**: Displays the percentage variance of items over the past two weeks.
- **KPI Visual**: Shows the percentage change for easy comparison.

## 4. [WoW LW vs 2W # of Items Var (Base KPI)](#4-wow-lw-vs-2w-items-var-base-kpi)

### Business Explanation:
Calculates the variance of the number of items between last week and two weeks ago.

### Explanation:
The `WoW LW vs 2W # of Items Var (Base KPI)` measure calculates the difference in the number of items between last week and two weeks ago using `Last Week # of Items (Time)` and `2 Weeks Ago # of Items (Time)`.

### Example Use Case:
- **Report**: Inventory Analysis
- **Purpose**: To analyze the changes in item count between two consecutive weeks.

### Recommended Visuals:
- **Bar Chart**: Displays the variance in the number of items between the two weeks.
- **KPI Visual**: Highlights the variance to help spot large fluctuations.

## 5. [WoW LW vs 2W Total Inv $ % Var (KPI)](#5-wow-lw-vs-2w-total-inv-percent-var-kpi)

### Business Explanation:
Calculates the percentage variance of the total inventory value between last week and two weeks ago.

### Explanation:
The `WoW LW vs 2W Total Inv $ % Var (KPI)` measure calculates the percentage variance in the total inventory value, comparing the total inventory values from `LW Total Inventory $ Year (Time)` and `2 Weeks Ago Total Inventory $ (Time)`.

### Example Use Case:
- **Report**: Inventory Valuation Analysis
- **Purpose**: To monitor inventory value changes between last week and two weeks ago.

### Recommended Visuals:
- **Column Chart**: Displays the percentage change in total inventory value.
- **KPI Visual**: Highlights the percentage change for easy evaluation.

## 6. [WoW LW vs 2W Total Inv $ Var (Base KPI)](#6-wow-lw-vs-2w-total-inv-var-base-kpi)

### Business Explanation:
Calculates the variance of the total inventory value between last week and two weeks ago.

### Explanation:
The `WoW LW vs 2W Total Inv $ Var (Base KPI)` measure calculates the difference in the total inventory value between last week and two weeks ago, comparing `LW Total Inventory $ (Time)` and `2 Weeks Ago Total Inventory $ (Time)`.

### Example Use Case:
- **Report**: Inventory Valuation Changes
- **Purpose**: To analyze fluctuations in total inventory value between two weeks.

### Recommended Visuals:
- **Bar Chart**: Displays the variance in total inventory value.
- **KPI Visual**: Highlights the variance to identify significant changes.

















