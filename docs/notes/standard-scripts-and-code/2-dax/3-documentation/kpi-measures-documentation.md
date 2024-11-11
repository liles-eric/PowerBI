---
id: kpi-measures-definitions
title: KPI Measures Definitions
desc: This document provides detailed definitions and explanations for key performance indicator (KPI) measures used in the Power BI model. It includes a set of DAX measures for tracking inventory, cost of goods sold (COGS), and other relevant performance metrics.
tags:
  - DAX
  - Power BI
  - KPI Measures
  - Business Intelligence
  - KPIs
created: 2024-11-11
updated: 2024-11-11
author: Eric Liles
version: 1.0
---

# Inventory and Cost Measures

## 1. Average COGS $ Year (Base KPI)

- **Business Explanation**: Calculates the average cost of goods sold (COGS) over the past year.
- **Explanation**: The `Average COGS $ Year (Base KPI)` measure calculates the average cost of goods sold by evaluating the sum of `Ext COGS $` from the `TrxEntry` table over the last 365 days.
- **Example Use Case**: 
  - **Report**: Financial Summary
  - **Purpose**: To analyze the average COGS over the past year to gauge profitability.
- **Recommended Visuals**:
  - **Line Chart**: Shows the trend of average COGS over time.
  - **KPI Visual**: Displays the average COGS for a quick assessment.

---

## 2. Average Inventory $ Year (Base KPI)

- **Business Explanation**: Calculates the average inventory value over the past year.
- **Explanation**: The `Average Inventory $ Year (Base KPI)` measure calculates the average inventory value by evaluating the sum of inventory over the past 365 days from the `Inventory History` table.
- **Example Use Case**: 
  - **Report**: Inventory Valuation Analysis
  - **Purpose**: To assess the average value of the inventory over the past year for better forecasting and stock management.
- **Recommended Visuals**:
  - **Bar Chart**: Displays the average inventory value over time.
  - **KPI Visual**: Highlights the total average inventory value.

---

## 3. WoW LW vs 2W # of Items % Var (KPI)

- **Business Explanation**: Calculates the percentage variance of the number of items between last week and two weeks ago.
- **Explanation**: The `WoW LW vs 2W # of Items % Var (KPI)` measure calculates the percentage change in the number of items by comparing the values from last week and two weeks ago.
- **Example Use Case**: 
  - **Report**: Inventory Performance Analysis
  - **Purpose**: To monitor changes in the inventory count between last week and two weeks ago.
- **Recommended Visuals**:
  - **Column Chart**: Displays the percentage change in the number of items.
  - **KPI Visual**: Highlights the percentage variance.

---

## 4. WoW LW vs 2W # of Items Var (Base KPI)

- **Business Explanation**: Calculates the variance in the number of items between last week and two weeks ago.
- **Explanation**: The `WoW LW vs 2W # of Items Var (Base KPI)` measure calculates the absolute difference in the number of items between last week and two weeks ago.
- **Example Use Case**: 
  - **Report**: Inventory Movement Analysis
  - **Purpose**: To track fluctuations in the number of items over a two-week period.
- **Recommended Visuals**:
  - **Column Chart**: Displays the variance in the number of items.
  - **KPI Visual**: Highlights the total variance in item count.

---

## 5. WoW LW vs 2W Total Inv $ % Var (KPI)

- **Business Explanation**: Calculates the percentage variance of the total inventory value between last week and two weeks ago.
- **Explanation**: The `WoW LW vs 2W Total Inv $ % Var (KPI)` measure calculates the percentage change in the total inventory value by comparing the values from last week and two weeks ago.
- **Example Use Case**: 
  - **Report**: Inventory Valuation Analysis
  - **Purpose**: To monitor inventory value changes between last week and two weeks ago.
- **Recommended Visuals**:
  - **Column Chart**: Displays the percentage change in total inventory value.
  - **KPI Visual**: Highlights the percentage variance in total inventory value.

---

## 6. WoW LW vs 2W Total Inv $ Var (Base KPI)

- **Business Explanation**: Calculates the variance in the total inventory value between last week and two weeks ago.
- **Explanation**: The `WoW LW vs 2W Total Inv $ Var (Base KPI)` measure calculates the absolute difference in the total inventory value between last week and two weeks ago.
- **Example Use Case**: 
  - **Report**: Inventory Valuation Analysis
  - **Purpose**: To track fluctuations in the total inventory value over the last two weeks.
- **Recommended Visuals**:
  - **Column Chart**: Displays the variance in total inventory value.
  - **KPI Visual**: Highlights the variance in inventory value for quick review.
