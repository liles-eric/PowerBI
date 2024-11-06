---
id: kpi-measures
title: KPI Measures
desc: This document provides detailed definitions and explanations of the DAX KPI measures used in our Power BI projects, including error handling information.
created: 2024-11-04
updated: 2024-11-04
---

# KPI Measures

This document provides detailed definitions and explanations of the DAX KPI measures used in our Power BI projects, including error handling information.

## 1. Average COGS $ Year (Base KPI)

Average COGS $ Year (Base KPI) =
CALCULATE(
    AVERAGEX(
        DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY),
        CALCULATE(SUM('TrxEntry'[Ext COGS $]))
    )
)

- **Description**: This calculates the average cost of goods sold (COGS) over the past year.
- **Reference**: [Average COGS $ Year (Base KPI) Definition](dendron.dax.definitions#average-cogs-year-base-kpi)

- **Error Handling**:
  - If the `TrxEntry` table is missing necessary columns, this measure will return a blank value.
  - If the `DateDim` table is not marked as a date table, this measure will not work correctly.



## 2. Average Inventory $ Year (Base KPI)

- **Description**: This calculates the average inventory value over the past year.
- **Reference**: [Average Inventory $ Year (Base KPI) Definition](dendron.dax.definitions#average-inventory-year-base-kpi)

- **Error Handling**:
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.
  - If the `DateDim` table is not marked as a date table, this measure will not work correctly.

## 3. WoW LW vs 2W # of Items % Var (KPI)

WoW LW vs 2W # of Items % Var (KPI) =
IF(
    ISBLANK([Last Week # of Items (Time)]) || ISBLANK([2 Weeks Ago # of Items (Time)]),
    BLANK(),
    DIVIDE([WoW LW vs 2W # of Items Var (Time)], [Last Week # of Items (Time)], 0)
)

- **Description**: This calculates the percentage variance of the number of items between last week and two weeks ago.
- **Reference**: [WoW LW vs 2W # of Items % Var (KPI) Definition](dendron.dax.definitions#wow-lw-vs-2w-items-percent-var-kpi)

- **Error Handling**:
  - If either `Last Week # of Items (Time)` or `2 Weeks Ago # of Items (Time)` is blank, this measure will return a blank value.

## 4. WoW LW vs 2W # of Items Var (Base KPI)

WoW LW vs 2W # of Items Var (Base KPI) =
IF(
    ISBLANK([Last Week # of Items (Time)]) || ISBLANK([2 Weeks Ago # of Items (Time)]),
    BLANK(),
    [Last Week # of Items (Time)] - [2 Weeks Ago # of Items (Time)]
)

- **Description**: This calculates the variance of the number of items between last week and two weeks ago.
- **Reference**: [WoW LW vs 2W # of Items Var (Base KPI) Definition](dendron.dax.definitions#wow-lw-vs-2w-items-var-base-kpi)

- **Error Handling**:
  - If either `Last Week # of Items (Time)` or `2 Weeks Ago # of Items (Time)` is blank, this measure will return a blank value.

## 5. WoW LW vs 2W Total Inv $ % Var (KPI)

WoW LW vs 2W Total Inv $ % Var (KPI) =
IF(
    ISBLANK([LW Total Inventory $ Year (Time)]) || ISBLANK([2 Weeks Ago Total Inventory $ (Time)]),
    BLANK(),
    DIVIDE([WoW LW vs 2W Total Inv $ Var (Time)], [LW Total Inventory $ (Time)], 0)
)

- **Description**: This calculates the percentage variance of the total inventory value between last week and two weeks ago.
- **Reference**: [WoW LW vs 2W Total Inv $ % Var (KPI) Definition](dendron.dax.definitions#wow-lw-vs-2w-total-inv-percent-var-kpi)

- **Error Handling**:
  - If either `LW Total Inventory $ Year (Time)` or `2 Weeks Ago Total Inventory $ (Time)` is blank, this measure will return a blank value.

## 6. WoW LW vs 2W Total Inv $ Var (Base KPI)

WoW LW vs 2W Total Inv $ Var (Base KPI) =
IF(
    ISBLANK([LW Total Inventory $ (Time)]) || ISBLANK([2 Weeks Ago Total Inventory $ (Time)]),
    BLANK(),
    [LW Total Inventory $ (Time)] - [2 Weeks Ago Total Inventory $ (Time)]
)

- **Description**: This calculates the variance of the total inventory value between last week and two weeks ago.
- **Reference**: [WoW LW vs 2W Total Inv $ Var (Base KPI) Definition](dendron.dax.definitions#wow-lw-vs-2w-total-inv-var-base-kpi)

- **Error Handling**:
  - If either `LW Total Inventory $ (Time)` or `2 Weeks Ago Total Inventory $ (Time)` is blank, this measure will return a blank value.
