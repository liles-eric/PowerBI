---
id: time-based-measures
title: Time-Based Measures
desc: This document provides detailed definitions and explanations of the DAX time-based measures used in our Power BI project, including error handling.
created: 2024-11-04
updated: 2024-11-04
author: Eric Liles
version: 1.0
---
# KPI Measures

This document provides detailed definitions and explanations of the DAX time based measures measures used in our Power BI projects, including error handling information.

## 1. 2 Weeks Ago # of Items (Time)

2 Weeks Ago # of Items (Time) =
IF(
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [# of Items (Base)],
        FILTER(
            ALL(DateDim),
            DateDim[YearWeek] = MAX(DateDim[YearWeek]) - 2 &&
            DateDim[DayOfWeekNumber] <= MAX(DateDim[DayOfWeekNumber]) &&
            DateDim[Date] <= TODAY() - 14
        )
    ),
    BLANK()
)

- **Description**: This calculates the number of distinct items two weeks ago based on the current week number.
- **Reference**: [2 Weeks Ago # of Items (Time) Definition](dendron.dax.definitions#2-weeks-ago-items-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 2. 2 Weeks AGo Total Inventory $ (Time)

2 Weeks Ago Total Inventory $ (Time) =
CALCULATE(
    SUM('Inventory History'[Inv_ExtPrice]),
    DATEADD('DateDim'[Date], -14, DAY)
)

- **Description**: This calculates the total inventory value from two weeks ago.
- **Reference**: [2 Weeks Ago Total Inventory $ (Time) Definition](dendron.dax.definitions#2-weeks-ago-total-inventory-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 3. Last Week # of Items

Last Week # of Items (Time) =
IF(
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [# of Items (Base)],
        FILTER(
            ALL(DateDim),
            DateDim[YearWeek] = MAX(DateDim[YearWeek]) - 1 &&
            DateDim[DayOfWeekNumber] <= MAX(DateDim[DayOfWeekNumber]) &&
            DateDim[Date] <= TODAY() - 7
        )
    ),
    BLANK()
)

- **Description**: This calculates the number of distinct items one week ago based on the current week number.
- **Reference**: [Last Week # of Items (Time) Definition](dendron.dax.definitions#last-week-items-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 4. LW Total Inventory $ (Time)

LW Total Inventory $ (Time) =
CALCULATE(
    SUM('Inventory History'[Inv_ExtPrice]),
    DATEADD('DateDim'[Date], -7, DAY)
)

- **Description**: This calculates the total inventory value from one week ago.
- **Reference**: [LW Total Inventory $ (Time) Definition](dendron.dax.definitions#lw-total-inventory-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 5. Same Week LY Total Inv $ (Time)

Same Week LY Total Inv $ (Time) =
VAR CurrentYear = MAX(DateDim[Year])
VAR CurrentWeekNum = MAX(DateDim[WeekNum])
VAR LastYear = CurrentYear - 1
VAR LastYearEndDate = TODAY() - 365

RETURN
IF (
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [Total Inventory $ (Base)],
        FILTER(
            ALL(DateDim),
            DateDim[Year] = LastYear &&
            DateDim[WeekNum] = CurrentWeekNum &&
            DateDim[Date] <= LastYearEndDate
        )
    ),
    BLANK()
)

- **Description**: This calculates the total inventory value for the same week last year.
- **Reference**: [Same Week LY Total Inv $ (Time) Definition](dendron.dax.definitions#same-week-ly-total-inv-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 6. Same Week LY Total Inv Qty (Time)

Same Week LY Total Inv Qty (Time) =
VAR CurrentYear = MAX(DateDim[Year])
VAR CurrentWeekNum = MAX(DateDim[WeekNum])
VAR LastYear = CurrentYear - 1
VAR LastYearEndDate = TODAY() - 365

RETURN
IF (
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [Total Inventory Qty (Base)],
        FILTER(
            ALL(DateDim),
            DateDim[Year] = LastYear &&
            DateDim[WeekNum] = CurrentWeekNum &&
            DateDim[Date] <= LastYearEndDate
        )
    ),
    BLANK()
)

- **Description**: This calculates the total inventory quantity for the same week last year.
- **Reference**: [Same Week LY Total Inv Qty (Time) Definition](dendron.dax.definitions#same-week-ly-total-inv-qty-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 7. 2 Weeks Ago Average COGS $ Year (Time)

2 Weeks Ago Average COGS $ Year (Time) =
IF(
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [Average COGS $ Year (Base KPI)],
        FILTER(
            ALL(DateDim),
            DateDim[YearWeek] = MAX(DateDim[YearWeek]) - 2 &&
            DateDim[DayOfWeekNumber] <= MAX(DateDim[DayOfWeekNumber]) &&
            DateDim[Date] <= TODAY() - 14
        )
    ),
    BLANK()
)

- **Description**: This calculates the average cost of goods sold (COGS) for the same week two weeks ago.
- **Reference**: [2 Weeks Ago Average COGS $ Year (Time) Definition](dendron.dax.definitions#2-weeks-ago-average-cogs-year-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `TrxEntry` table is missing necessary columns, this measure will return a blank value.

## 8. 2 Weeks Ago Average Inventory $ Year (Time)  

2 Weeks Ago Average Inventory $ Year (Time) =
IF(
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [Average Inventory $ Year (Base KPI)],
        FILTER(
            ALL(DateDim),
            DateDim[YearWeek] = MAX(DateDim[YearWeek]) - 2 &&
            DateDim[DayOfWeekNumber] <= MAX(DateDim[DayOfWeekNumber]) &&
            DateDim[Date] <= TODAY() - 14
        )
    ),
    BLANK()
)

- **Description**: This calculates the average inventory value for the same week two weeks ago.
- **Reference**: [2 Weeks Ago Average Inventory $ Year (Time) Definition](dendron.dax.definitions#2-weeks-ago-average-inventory-year-time)

- **Error Handling**:
  - If the `DateDim` table is missing necessary columns, this measure will return a blank value.
  - If the `Inventory History` table is missing necessary columns, this measure will return a blank value.

## 9. LW Average COGS $ Year (Time)

LW Average COGS $ Year (Time) =
IF(
    ISINSCOPE(DateDim[WeekNum]),
    CALCULATE(
        [Average COGS $ Year (Base KPI)],
        FILTER(
            ALL(DateDim),
            DateDim[YearWeek] = MAX(DateDim[YearWeek]) - 1 &&
            DateDim[DayOfWeekNumber] <= MAX(DateDim[DayOfWeekNumber]) &&
            DateDim[Date] <= TODAY() - 7
        )
    ),
    BLANK()
)

- **Description**: This calculates the average cost of goods sold (COGS) for the same week last week.
- **Reference**: [LW Average COGS $

- **Error Handling** - If the `DateDim` table is missing necessary columns, this measure will return a blank value. If the `TrxEntry` table is missing necessary columns, this measure will return a blank value.


