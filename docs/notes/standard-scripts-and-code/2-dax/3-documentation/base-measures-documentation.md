---
title: Base Measures
description: Definitions, DAX code, and explanations for the base measures used in the Power BI model.
created: 2024-11-11
modified: 2024-11-11
tags:
  - DAX
  - Power BI
  - Base Measures
  - Definitions
  - Calculations
  - Metrics
author: Eric Liles
version: 1.0
---
# Base Measures

**Purpose:** This document provides definitions and explanations for the base measures used in the Power BI model. For detailed information on how to use these measures, please refer to the README file.

---

## 1. # of Items (Base)

**DAX Code:**

# # of Items (Base) = DISTINCTCOUNT('Inventory History'[ItemId])

# # of Items

## Definition
The # of Items (Base) measure counts the distinct number of items in the inventory history.

## Explanation
This measure calculates the number of unique items by counting the distinct values in the `ItemId` column of the `Inventory History` table.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains an `ItemId` column with unique item identifiers.

## Error Handling
If the `Inventory History` table is empty or the `ItemId` column is missing, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)
- [Total COGS $ (Base) Definition](path/to/Total-COGS-Base-Definition.md)

## 2. Total Inventory (Base)

# Total Inventory $ (Base) = SUM('Inventory History'
[Inv_ExtPrice])

## Definition: The Total Inventory $ (Base) measure sums the Extended Price of all records in the inventory history.

## Explanation: This measure calculates the total inventory value by summing the Inv_ExtPrice column in the Inventory History table.

## Dependencies and Assumptions: This measure assumes that the Inventory History table contains an Inv_ExtPrice column with the extended price values of inventory items.

## Error Handling: If the Inventory History table is empty or the Inv_ExtPrice column is missing, this measure will return a blank value.

## Related Links:  [# of Items (Base) Definition](path/to/Number-of-Items-Base-Definition.md)
- [Total COGS $ (Base) Definition](path/to/Total-COGS-Base-Definition.md)

## 3. Total COGS (Base)

# Total COGS $ (Base) = SUM('TrxEntry'[Ext COGS $])

# Total COGS $ (Base) Measure

## Definition
The Total COGS $ (Base) measure sums the Extended Cost of Goods Sold (COGS) of all transaction entries.

## Explanation
This measure calculates the total COGS by summing the `Ext COGS $` column in the `TrxEntry` table.

## Dependencies and Assumptions
This measure assumes that the `TrxEntry` table contains an `Ext COGS $` column with the extended cost of goods sold values of transaction entries.

## Error Handling
If the `TrxEntry` table is empty or the `Ext COGS $` column is missing, this measure will return a blank value.

## Related Links
- [# of Items (Base) Definition](path/to/Number-of-Items-Base-Definition.md)
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)

# 4. Total Inventory Qty (Base)

# Total Inventory Qty (Base) = SUM('Inventory History'[Quantity])

# Total Inventory Qty (Base) Measure

## Definition
The Total Inventory Qty (Base) measure sums the quantity of all records in the inventory history.

## Explanation
This measure calculates the total inventory quantity by summing the `Quantity` column in the `Inventory History` table.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains a `Quantity` column with the quantity values of inventory items.

## Error Handling
If the `Inventory History` table is empty or the `Quantity` column is missing, this measure will return a blank value.

## Related Links
- [# of Items (Base) Definition](path/to/Number-of-Items-Base-Definition.md)
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)
- [Total COGS $ (Base) Definition](path/to/Total-COGS-Base-Definition.md)

# 5. Total Inventory $ Year (Base)

# Total Inventory $ Year (Base) =
CALCULATE(
    SUM('Inventory History'[Inv_ExtPrice]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

# Total Inventory $ Year (Base) Measure

## Definition
The Total Inventory $ Year (Base) measure sums the Extended Price of all records in the inventory history over the past year.

## Explanation
This measure calculates the total inventory value over the past year by summing the `Inv_ExtPrice` column in the `Inventory History` table within a one-year period.

## Dependencies and Assumptions
This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column with the extended price values of inventory items and that a `DateDim` table is present to provide date context.

## Error Handling
If the `Inventory History` table is empty or the `Inv_ExtPrice` column is missing, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)
- [Total COGS $ Year (Base) Definition](path/to/Total-COGS-Year-Base-Definition.md)

# 6. Total COGS $ Year (Base)

# Total COGS $ Year (Base) =
CALCULATE(
    SUM('TrxEntry'[Ext COGS $]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

# Total COGS $ Year (Base) Measure

## Definition
The Total COGS $ Year (Base) measure sums the Extended Cost of Goods Sold (COGS) of all transaction entries over the past year.

## Explanation
This measure calculates the total COGS over the past year by summing the `Ext COGS $` column in the `TrxEntry` table within a one-year period.

## Dependencies and Assumptions
This measure assumes that the `TrxEntry` table contains an `Ext COGS $` column with the extended cost of goods sold values of transaction entries and that a `DateDim` table is present to provide date context.

## Error Handling
If the `TrxEntry` table is empty or the `Ext COGS $` column is missing, this measure will return a blank value.

## Related Links
- [Total Inventory $ (Base) Definition](path/to/Total-Inventory-Base-Definition.md)
- [Total Inventory $ Year (Base) Definition](path/to/Total-Inventory-Year-Base-Definition.md)

# 7. Current WeekNum (Base)

# CurrentWeekNum = WEEKNUM(TODAY(), 1)

# CurrentWeekNum Measure

## Definition
The CurrentWeekNum measure calculates the current week number of the year.

## Explanation
This measure uses the `WEEKNUM` function to return the week number for the current date.

## Dependencies and Assumptions
This measure assumes that the model has access to the current date.

## Error Handling
If the current date cannot be accessed, this measure will return a blank value.

## Related Links
- [CurrentYear Definition](path/to/CurrentYear-Definition.md)
- [LastRefreshedDate Definition](path/to/LastRefreshedDate-Definition.md)

# 8. Current Year (Base)

# CurrentYear = YEAR(TODAY())

# CurrentYear Measure

## Definition
The CurrentYear measure calculates the current year.

## Explanation
This measure uses the `YEAR` function to return the current year based on today's date.

## Dependencies and Assumptions
This measure assumes that the model has access to the current date.

## Error Handling
If the current date cannot be accessed, this measure will return a blank value.

## Related Links
- [CurrentWeekNum Definition](path/to/CurrentWeekNum-Definition.md)
- [LastRefreshedDate Definition](path/to/LastRefreshedDate-Definition.md)

# 9. Last Refreshed Date (Base)

# LastRefreshedDate = MAX('Last Refresh Date'[Last Refresh])

# LastRefreshedDate Measure

## Definition
The LastRefreshedDate measure gets the last refresh date from the 'Last Refresh Date' table.

## Explanation
This measure returns the maximum date from the `Last Refresh Date` column in the `Last Refresh Date` table, indicating the most recent data refresh.

## Dependencies and Assumptions
This measure assumes that the `Last Refresh Date` table contains a `Last Refresh` column with date values.

## Error Handling
If the `Last Refresh Date` table is empty or the `Last Refresh` column is missing, this measure will return a blank value.

## Related Links
- [CurrentWeekNum Definition](path/to/CurrentWeekNum-Definition.md)
- [CurrentYear Definition](path/to/CurrentYear-Definition.md)
