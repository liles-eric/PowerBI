---
title: KPI Measures Definitions
description: This document provides detailed definitions, explanations, and related information for the key performance indicators (KPIs) used in the Power BI model, specifically for tracking inventory, cost of goods sold (COGS), and their variations over time.
tags:
  - DAX
  - Power BI
  - KPIs
  - Business Intelligence
  - Time-Based Measures
created: 2024-11-11
updated: 2024-11-11
author: Eric Liles
version: 1.0
---

# KPI Measures Definitions

This document outlines the definitions, explanations, and dependencies for the key performance indicators (KPIs) used in the Power BI model. These KPIs focus on tracking inventory, cost of goods sold (COGS), and other performance metrics over time, providing valuable insights into business performance and trends.

---

# 1. Average COGS $ Year (Base KPI)

**DAX:**
Average COGS $ Year (Base KPI) =
CALCULATE(
    AVERAGEX(
        DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY),
        CALCULATE(SUM('TrxEntry'[Ext COGS $]))
    )
)

# Average COGS $ Year (Base KPI) Measure

## Definition
This measure calculates the average cost of goods sold (COGS) over the past year.

## Explanation
It computes the average of the `Ext COGS $` from the `TrxEntry` table, considering data from the last 365 days.

## Dependencies and Assumptions
- Assumes that the `TrxEntry` table contains a column `Ext COGS $` representing the cost of goods sold.
- The `DateDim` table must be marked as a date table for proper time-based calculations.

## Error Handling
- If the `TrxEntry` table is missing the necessary columns, this measure will return a blank value.
- If the `DateDim` table is not marked as a date table, the measure will not work correctly.

## Related Links
- [Average COGS $ Year (Base KPI) Definition](path/to/Average-COGS-Year-Base-KPI-Definition.md)

# 2. Average Inventory $ Year (Base KPI)

**DAX**
Average Inventory $ Year (Base KPI) =
CALCULATE(
    AVERAGEX(
        DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY),
        CALCULATE(SUM('Inventory History'[Inv_ExtPrice]))
    )
)

# Average Inventory $ Year (Base KPI) Measure

## Definition
This measure calculates the average inventory value over the past year.

## Explanation
It computes the average of the `Inv_ExtPrice` values from the `Inventory History` table, considering data from the last 365 days.

## Dependencies and Assumptions
- Assumes that the `Inventory History` table contains a column `Inv_ExtPrice` representing the inventory's extended price.
- The `DateDim` table must be marked as a date table for proper time-based calculations.

## Error Handling
- If the `Inventory History` table is missing the necessary columns, this measure will return a blank value.
- If the `DateDim` table is not marked as a date table, the measure will not work correctly.

## Related Links
- [Average Inventory $ Year (Base KPI) Definition](path/to/Average-Inventory-Year-Base-KPI-Definition.md)

# 3. WoW LW vs 2W # of Items % Var (KPI)

**DAX**
WoW LW vs 2W # of Items % Var (KPI) =
IF(
    ISBLANK([Last Week # of Items (Time)]) || ISBLANK([2 Weeks Ago # of Items (Time)]),
    BLANK(),
    DIVIDE([WoW LW vs 2W # of Items Var (Time)], [Last Week # of Items (Time)], 0)
)

# Percentage Variance of # of Items (Last Week vs. 2 Weeks Ago) Measure

## Definition
This measure calculates the percentage variance of the number of items between last week and two weeks ago.

## Explanation
It compares the number of items in inventory from last week (`Last Week # of Items (Time)`) and two weeks ago (`2 Weeks Ago # of Items (Time)`), returning the variance as a percentage.

## Dependencies and Assumptions
- Assumes that the measures `Last Week # of Items (Time)` and `2 Weeks Ago # of Items (Time)` exist.

## Error Handling
- If either `Last Week # of Items (Time)` or `2 Weeks Ago # of Items (Time)` is blank, this measure will return a blank value.

## Related Links
- [Last Week # of Items (Time) Definition](path/to/Last-Week-Items-Time-Definition.md)
- [2 Weeks Ago # of Items (Time) Definition](path/to/2-Weeks-Ago-Items-Time-Definition.md)

# 4. WoW LW vs 2W # of Items Var (Base KPI)

**DAX**
WoW LW vs 2W # of Items Var (Base KPI) =
IF(
    ISBLANK([Last Week # of Items (Time)]) || ISBLANK([2 Weeks Ago # of Items (Time)]),
    BLANK(),
    [Last Week # of Items (Time)] - [2 Weeks Ago # of Items (Time)]
)

# Variance in # of Items (Last Week vs. 2 Weeks Ago) Measure

## Definition
This measure calculates the variance in the number of items between last week and two weeks ago.

## Explanation
It calculates the difference between the number of items from last week (`Last Week # of Items (Time)`) and two weeks ago (`2 Weeks Ago # of Items (Time)`).

## Dependencies and Assumptions
- Assumes that the measures `Last Week # of Items (Time)` and `2 Weeks Ago # of Items (Time)` exist.

## Error Handling
- If either `Last Week # of Items (Time)` or `2 Weeks Ago # of Items (Time)` is blank, this measure will return a blank value.

## Related Links
- [WoW LW vs 2W # of Items Var (Base KPI) Definition](path/to/WoW-LW-vs-2W-Items-Var-Base-KPI-Definition.md)

# 5. WoW LW vs 2W Total Inv $ % Var (KPI)

**DAX**
WoW LW vs 2W Total Inv $ % Var (KPI) =
IF(
    ISBLANK([LW Total Inventory $ Year (Time)]) || ISBLANK([2 Weeks Ago Total Inventory $ (Time)]),
    BLANK(),
    DIVIDE([WoW LW vs 2W Total Inv $ Var (Time)], [LW Total Inventory $ (Time)], 0)
)

# Percentage Variance in Total Inventory $ (Last Week vs. 2 Weeks Ago) Measure

## Definition
This measure calculates the percentage variance of the total inventory value between last week and two weeks ago.

## Explanation
It compares the total inventory value for last week (`LW Total Inventory $ Year (Time)`) and two weeks ago (`2 Weeks Ago Total Inventory $ (Time)`), calculating the variance as a percentage.

## Dependencies and Assumptions
- Assumes that the measures `LW Total Inventory $ Year (Time)` and `2 Weeks Ago Total Inventory $ (Time)` exist.

## Error Handling
- If either `LW Total Inventory $ Year (Time)` or `2 Weeks Ago Total Inventory $ (Time)` is blank, this measure will return a blank value.

## Related Links
- [WoW LW vs 2W Total Inv $ % Var (KPI) Definition](path/to/WoW-LW-vs-2W-Total-Inv-Percent-Var-KPI-Definition.md)

# 6. WoW LW vs 2W Total Inv $ Var (Base KPI)

**DAX**
WoW LW vs 2W Total Inv $ Var (Base KPI) =
IF(
    ISBLANK([LW Total Inventory $ (Time)]) || ISBLANK([2 Weeks Ago Total Inventory $ (Time)]),
    BLANK(),
    [LW Total Inventory $ (Time)] - [2 Weeks Ago Total Inventory $ (Time)]
)

# Variance in Total Inventory $ (Last Week vs. 2 Weeks Ago) Measure

## Definition
This measure calculates the variance in the total inventory value between last week and two weeks ago.

## Explanation
It computes the difference between the total inventory value for last week (`LW Total Inventory $ (Time)`) and two weeks ago (`2 Weeks Ago Total Inventory $ (Time)`).

## Dependencies and Assumptions
- Assumes that the measures `LW Total Inventory $ (Time)` and `2 Weeks Ago Total Inventory $ (Time)` exist.

## Error Handling
- If either `LW Total Inventory $ (Time)` or `2 Weeks Ago Total Inventory $ (Time)` is blank, this measure will return a blank value.

## Related Links
- [WoW LW vs 2W Total Inv $ Var (Base KPI) Definition](path/to/WoW-LW-vs-2W-Total-Inv-Var-Base-KPI-Definition.md)






