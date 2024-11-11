---
id: base-measures-definitions
title: Base Measures Definitions
desc: This document provides detailed definitions and explanations for the base DAX measures used in Power BI projects. It includes business explanations, measure explanations, example use cases, and recommended visuals for each base measure.
tags:
  - DAX
  - Power BI
  - Base Measures
  - Business Intelligence
  - KPIs
created: 2024-11-11
updated: 2024-11-11
author: Eric Liles
version: 1.0
---

# Base Measures Definitions

This document provides detailed definitions and explanations for the base DAX measures used in our Power BI projects. It includes business explanations, measure explanations, example use cases, and recommended visuals for each base measure.

## 1. # of Items (Base)

### Business Explanation:
This measure calculates the distinct number of items in the inventory history.

### Measure Explanation:
The `# of Items (Base)` measure counts the number of unique items based on the `ItemId` column in the `Inventory History` table.

### Example Use Case:
- **Report**: Inventory Overview
- **Purpose**: To understand the diversity of items in the inventory and track changes in inventory size.

### Recommended Visuals:
- **Column Chart**: Displays the number of distinct items in the inventory.
- **KPI Visual**: Highlights the total number of distinct items.

---

## 2. Total Inventory (Base)

### Business Explanation:
This measure calculates the total inventory value by summing the extended price of inventory items.

### Measure Explanation:
The `Total Inventory (Base)` measure sums up the `Inv_ExtPrice` values in the `Inventory History` table to calculate the total dollar amount of inventory.

### Example Use Case:
- **Report**: Inventory Valuation
- **Purpose**: To track the overall value of inventory at any given time.

### Recommended Visuals:
- **Stacked Column Chart**: Displays total inventory value over time.
- **KPI Visual**: Highlights the total value of inventory for quick overview.

---

## 3. Total COGS (Base)

### Business Explanation:
This measure calculates the total cost of goods sold (COGS) by summing the extended COGS values from transaction entries.

### Measure Explanation:
The `Total COGS (Base)` measure calculates the total cost of goods sold by summing the `Ext COGS $` values from the `TrxEntry` table.

### Example Use Case:
- **Report**: Profitability Analysis
- **Purpose**: To measure the total cost of goods sold during a specific period, providing insights into cost management and profitability.

### Recommended Visuals:
- **Line Chart**: Displays COGS trends over time.
- **KPI Visual**: Highlights the total COGS for a specific period.

---

## 4. Total Inventory Qty (Base)

### Business Explanation:
This measure calculates the total quantity of items in inventory.

### Measure Explanation:
The `Total Inventory Qty (Base)` measure sums the `Quantity` values in the `Inventory History` table to calculate the total quantity of inventory items.

### Example Use Case:
- **Report**: Inventory Level Monitoring
- **Purpose**: To track the total number of units in inventory, assisting in stock management and forecasting.

### Recommended Visuals:
- **Bar Chart**: Displays the total inventory quantity by category or location.
- **KPI Visual**: Highlights the total inventory quantity for immediate analysis.

---

## 5. Total COGS $ Year (Base)

### Business Explanation:
This measure calculates the total COGS over the past year.

### Measure Explanation:
The `Total COGS $ Year (Base)` measure sums the `Ext COGS $` values from the `TrxEntry` table over the past 365 days, using the `DATESINPERIOD` function to filter the dates.

### Example Use Case:
- **Report**: Annual Profit and Loss Analysis
- **Purpose**: To understand the total cost of goods sold for the past year, aiding in year-over-year financial analysis.

### Recommended Visuals:
- **Column Chart**: Displays total COGS over the past year, helping to compare monthly or quarterly trends.
- **KPI Visual**: Highlights the total COGS for the past year for quick insights.

---

## 6. Total Inventory $ Year (Base)

### Business Explanation:
This measure calculates the total inventory value over the past year.

### Measure Explanation:
The `Total Inventory $ Year (Base)` measure sums the `Inv_ExtPrice` values from the `Inventory History` table over the past 365 days, using the `DATESINPERIOD` function to filter the dates.

### Example Use Case:
- **Report**: Yearly Inventory Valuation
- **Purpose**: To track the total value of inventory for the past year, providing insights into inventory management and financial performance.

### Recommended Visuals:
- **Stacked Column Chart**: Displays total inventory value over time for comparison across different periods.
- **KPI Visual**: Highlights the total inventory value for the past year.

---

## Misc Measures

---

## 7. CurrentWeekNum

### Business Explanation:
This measure calculates the current week number of the year.

### Measure Explanation:
The `CurrentWeekNum` measure returns the week number based on the current date.

### Example Use Case:
- **Report**: Weekly Activity Tracker
- **Purpose**: To track and compare data on a weekly basis, highlighting trends in performance.

### Recommended Visuals:
- **Card Visual**: Displays the current week number for quick reference.
- **Bar Chart**: Displays weekly data trends with the week number on the axis.

---

## 8. CurrentYear

### Business Explanation:
This measure returns the current year.

### Measure Explanation:
The `CurrentYear` measure returns the year part of today's date, making it useful for time-based comparisons.

### Example Use Case:
- **Report**: Yearly Data Comparison
- **Purpose**: To filter or highlight data that is relevant to the current year, ensuring the user is working with up-to-date information.

### Recommended Visuals:
- **Card Visual**: Displays the current year as a reference.
- **Line Chart**: Displays current year data trends in comparison to previous years.

---

## 9. LastRefreshedDate

### Business Explanation:
This measure displays the last refresh date of the data model.

### Measure Explanation:
The `LastRefreshedDate` measure returns the maximum date from the `Last Refresh Date` table, which indicates the last time the data was updated.

### Example Use Case:
- **Report**: Data Freshness Indicator
- **Purpose**: To ensure the data displayed in reports is current and reflects the latest updates.

### Recommended Visuals:
- **Card Visual**: Displays the last refresh date for user awareness.
- **KPI Visual**: Highlights the data freshness and updates the user on when the data was last refreshed.

---

## 10. Greeting

### Business Explanation:
This measure generates a personalized greeting message for the user, along with some contextual information.

### Measure Explanation:
The `Greeting` measure uses the current user's login and the current date to generate a custom message, including the day of the year, week number, and last refresh date.

### Example Use Case:
- **Report**: Personalized Dashboards
- **Purpose**: To welcome the user, providing relevant data context, such as the current date and the last time data was refreshed.

### Recommended Visuals:
- **Text Box**: Displays the personalized greeting message for the user.
- **Card Visual**: Highlights key user-specific information like current week and date.

---

