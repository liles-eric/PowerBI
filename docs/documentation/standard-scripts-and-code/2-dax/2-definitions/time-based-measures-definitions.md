---
title: Time-Based Measures Definitions
description: This document provides detailed definitions and explanations for time-based measures used in the Power BI model. It includes a set of DAX measures for tracking inventory, cost of goods sold (COGS), and other relevant time-series data.
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
# Time-Based Measures

## Overview

This document outlines time-based measures used in the Power BI model for tracking inventory, cost of goods sold (COGS), and other key performance indicators (KPIs) over time. These measures are essential for analyzing trends and variations in business metrics, particularly related to inventory and sales performance.

---

# 1. 2 Weeks Ago # of Items (Time)

**DAX**
 2 Weeks Ago # of Items (Time) = CALCULATE([# of Items (Base)], DATEADD(DateDim[Date], -14, DAY))

## Definition
The 2 Weeks Ago # of Items (Time) measure calculates the distinct number of items two weeks ago based on the current week number.

## Explanation
This measure calculates the number of unique items by using the `# of Items (Base)` measure in combination with a filter that restricts the date to two weeks ago.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `YearWeek` and `DayOfWeekNumber` columns, and the `Inventory History` table has an `ItemId` column.

## Error Handling
If the `DateDim` table or `Inventory History` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [# of Items (Base) Definition](path/to/Number-of-Items-Base-Definition.md)
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 2. 2 Weeks Ago Total Inventory $ (Time)

**DAX**
2 Weeks Ago Total Inventory $ (Time) = 
    CALCULATE([Total Inventory $ (Base)], 
    DATEADD(DateDim[Date], -14, DAY))

## Definition
The 2 Weeks Ago Total Inventory $ (Time) measure calculates the total inventory value two weeks ago.

## Explanation
This measure calculates the total inventory value by using the `Total Inventory $ (Base)` measure and applying a filter to restrict the date to two weeks ago.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column representing the inventory value.

## Error Handling
If the `Inventory History` table is missing the `Inv_ExtPrice` column, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 3. Last Week # of Items (Time)

**DAX**
Last Week # of Items (Time) = CALCULATE([# of Items (Base)], DATEADD(DateDim[Date], -7, DAY))

## Definition
The Last Week # of Items (Time) measure calculates the distinct number of items one week ago based on the current week number.

## Explanation
This measure calculates the number of unique items for the previous week using the `# of Items (Base)` measure combined with a filter that restricts the date to the last week.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `YearWeek` and `DayOfWeekNumber` columns, and the `Inventory History` table has an `ItemId` column.

## Error Handling
If the `DateDim` table or `Inventory History` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [# of Items (Base) Definition](path/to/Number-of-Items-Base-Definition.md)
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 4. LW Total Inventory $ (Time)

**DAX**
 LW Total Inventory $ (Time) = CALCULATE([Total Inventory $ (Base)], DATEADD(DateDim[Date], -7, DAY))

## Definition
The LW Total Inventory $ (Time) measure calculates the total inventory value from one week ago.

## Explanation
This measure calculates the total inventory value from last week using the `SUM` function combined with the `DATEADD` function to filter the date range.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column.

## Error Handling
If the `Inventory History` table is missing the `Inv_ExtPrice` column, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 5. Same Week LY Total Inv $ (Time)

**DAX**
 Same Week LY Total Inv $ (Time) = CALCULATE([Total Inventory $ (Base)], SAMEPERIODLASTYEAR(DateDim[Date]))

## Definition
The Same Week LY Total Inv $ (Time) measure calculates the total inventory value for the same week last year.

## Explanation
This measure calculates the total inventory value for the corresponding week from the previous year using the `Total Inventory $ (Base)` measure and filters for the same week last year.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `Year`, `WeekNum`, and `Date` columns, and the `Inventory History` table has an `Inv_ExtPrice` column.

## Error Handling
If the `DateDim` table or `Inventory History` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 6.  Same Week LY Total Inv Qty (Time)

**DAX**
 Same Week LY Total Inv Qty (Time) = CALCULATE([Total Inventory Qty (Base)], SAMEPERIODLASTYEAR(DateDim[Date]))

## Definition
The Same Week LY Total Inv Qty (Time) measure calculates the total inventory quantity for the same week last year.

## Explanation
This measure calculates the total inventory quantity for the corresponding week from the previous year using the `Total Inventory Qty (Base)` measure and filters for the same week last year.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `Year`, `WeekNum`, and `Date` columns, and the `Inventory History` table has an `Inv_Qty` column.

## Error Handling
If the `DateDim` table or `Inventory History` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [Total Inventory Qty (Base) Definition](path/to/Total-Inventory-Qty-Base-Definition.md)

# 7. 2 Weeks Ago Average COGS $ Year (Time)

**DAX**
 # 2 Weeks Ago Average COGS $ Year (Time) = CALCULATE([Average COGS $ Year (Base KPI)], DATEADD(DateDim[Date], -14, DAY))

## Definition
The 2 Weeks Ago Average COGS $ Year (Time) measure calculates the average cost of goods sold (COGS) for the same week two weeks ago.

## Explanation
This measure calculates the average COGS for two weeks ago using the `Average COGS $ Year (Base KPI)` measure in combination with a filter that restricts the date to two weeks ago.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `YearWeek` and `DayOfWeekNumber` columns, and the `TrxEntry` table has a `COGS` column.

## Error Handling
If the `DateDim` table or `TrxEntry` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [Average COGS $ Year (Base KPI) Definition](path/to/Average-COGS-Year-Base-KPI-Definition.md)

# 8. 2 Weeks Ago Average Inventory $ Year (Time)

**DAX**
 2 Weeks Ago Average Inventory $ Year (Time) = CALCULATE([Average Inventory $ Year (Base KPI)], DATEADD(DateDim[Date], -14, DAY))

## Definition
The 2 Weeks Ago Average Inventory $ Year (Time) measure calculates the average inventory value for the same week two weeks ago.

## Explanation
This measure calculates the average inventory value for two weeks ago using the `Average Inventory $ Year (Base KPI)` measure and filters for the same period.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column representing the inventory value.

## Error Handling
If the `Inventory History` table is missing the `Inv_ExtPrice` column, this measure will return a blank value.

## Related Links
- [Average Inventory $ Year (Base KPI) Definition](path/to/Average-Inventory-Year-Base-KPI-Definition.md)

# 9. LW Average COGS $ Year (Time)

**DAX**
 LW Average COGS $ Year (Time) = CALCULATE([Average COGS $ Year (Base KPI)], DATEADD(DateDim[Date], -7, DAY))

## Definition
The LW Average COGS $ Year (Time) measure calculates the average cost of goods sold (COGS) for the previous week.

## Explanation
This measure calculates the average COGS for the previous week using the `Average COGS $ Year (Base KPI)` measure in combination with a filter that restricts the date to last week.

## Dependencies and Assumptions
This measure assumes that the `DateDim` table contains the necessary `YearWeek` and `DayOfWeekNumber` columns, and the `TrxEntry` table has a `COGS` column.

## Error Handling
If the `DateDim` table or `TrxEntry` table is missing necessary columns, this measure will return a blank value.

## Related Links
- [Average COGS $ Year (Base KPI) Definition](path/to/Average-COGS-Year-Base-KPI-Definition.md)
