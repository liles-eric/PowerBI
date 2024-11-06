---
id: base-measures-definitions
title: Base-Measures-Definitions
desc: This document provides detailed definitions and explanations of the DAX time-based measures used in our Power BI project, including error handling.
created: 2024-11-04
updated: 2024-11-04
---

# DAX Definitions for Sales Measures

This document offers concise definitions and explanations for DAX measures used in our business intelligence projects, sourced from transaction and dimension tables for analysis in Power BI and Excel PowerPivot.

## 1. # of Items (Base)

# of Items (Base) = DISTINCTCOUNT('Inventory History'[ItemId])

**Definition:** The `# of Items (Base)` measure counts the distinct number of items in the inventory history.

**Explanation:** This measure calculates the number of unique items by counting the distinct values in the `ItemId` column of the `Inventory History` table.

**Dependencies and Assumptions:** This measure assumes that the `Inventory History` table contains an `ItemId` column with unique item identifiers.

**Error Handling:** If the `Inventory History` table is empty or the `ItemId` column is missing, this measure will return a blank value.

**Related Links:**
- [Total Inventory $ (Base) Definition](dendron://dax.definitions.base_measures#2-total-inventory--base)
- [Total COGS $ (Base) Definition](dendron://dax.definitions.base_measures#3-total-cogs--base)

## 2. Total Inventory $ (Base)

Total Inventory $ (Base) = SUM('Inventory History'[Inv_ExtPrice])

**Definition:** The `Total Inventory $ (Base)` measure sums the Extended Price of all records in the inventory history.

**Explanation:** This measure calculates the total inventory value by summing the `Inv_ExtPrice` column in the `Inventory History` table.

**Dependencies and Assumptions:** This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column with the extended price values of inventory items.

**Error Handling:** If the `Inventory History` table is empty or the `Inv_ExtPrice` column is missing, this measure will return a blank value.

**Related Links:**
- [# of Items (Base) Definition](dendron://dax.definitions.base_measures#1--of-items-base)
- [Total COGS $ (Base) Definition](dendron://dax.definitions.base_measures#3-total-cogs--base)

## 3. Total COGS $ (Base)

Total COGS $ (Base) = SUM('TrxEntry'[Ext COGS $])

**Definition:** The `Total COGS $ (Base)` measure sums the Extended Cost of Goods Sold (COGS) of all transaction entries.

**Explanation:** This measure calculates the total COGS by summing the `Ext COGS $` column in the `TrxEntry` table.

**Dependencies and Assumptions:** This measure assumes that the `TrxEntry` table contains an `Ext COGS $` column with the extended cost of goods sold values of transaction entries.

**Error Handling:** If the `TrxEntry` table is empty or the `Ext COGS $` column is missing, this measure will return a blank value.

**Related Links:**
- [# of Items (Base) Definition](dendron://dax.definitions.base_measures#1--of-items-base)
- [Total Inventory $ (Base) Definition](dendron://dax.definitions.base_measures#2-total-inventory--base)

## Total Inventory Qty (Base)

Total Inventory Qty (Base) = SUM('Inventory History'[Quantity])

**Definition:** The `Total Inventory Qty (Base)` measure sums the quantity of all inventory items.

**Explanation:** This measure calculates the total quantity by summing the `Quantity` column in the `Inventory History` table.

**Dependencies and Assumptions:** This measure assumes that the `Inventory History` table contains a `Quantity` column with the quantities of inventory items.

**Error Handling:** If the `Inventory History` table is empty or the `Quantity` column is missing, this measure will return a blank value.

**Related Links:**
- [Total Inventory $ (Base) Definition](dendron://dax.definitions.base_measures#2-total-inventory--base)
- [Total COGS $ (Base) Definition](dendron://dax.definitions.base_measures#3-total-cogs--base)

## 5. Total Inventory $ Year (Base)

Total Inventory $ Year (Base) =
CALCULATE(
    SUM('Inventory History'[Inv_ExtPrice]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

**Definition:** The `Total Inventory $ Year (Base)` measure sums the Extended Price of all records in the inventory history over the past year.

**Explanation:** This measure calculates the total inventory value over the past year by summing the `Inv_ExtPrice` column in the `Inventory History` table within a one-year period.

**Dependencies and Assumptions:** This measure assumes that the `Inventory History` table contains an `Inv_ExtPrice` column with the extended price values of inventory items and that a `DateDim` table is present to provide date context.

**Error Handling:** If the `Inventory History` table is empty or the `Inv_ExtPrice` column is missing, this measure will return a blank value.

**Related Links:**
- [Total Inventory $ (Base) Definition](dendron://dax.definitions.base_measures#2-total-inventory--base)
- [Total COGS $ Year (Base) Definition](dendron://dax.definitions.base_measures#6-total-cogs--year-base)

## 6. Total COGS $ Year (Base)

Total COGS $ Year (Base) =
CALCULATE(
    SUM('TrxEntry'[Ext COGS $]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

**Definition:** The `Total COGS $ Year (Base)` measure sums the Extended Cost of Goods Sold (COGS) of all transaction entries over the past year.

**Explanation:** This measure calculates the total COGS over the past year by summing the `Ext COGS $` column in the `TrxEntry` table within a one-year period.

**Dependencies and Assumptions:** This measure assumes that the `TrxEntry` table contains an `Ext COGS $` column with the extended cost of goods sold values of transaction entries and that a `DateDim` table is present to provide date context.

**Error Handling:** If the `TrxEntry` table is empty or the `Ext COGS $` column is missing, this measure will return a blank value.

**Related Links:**
- [Total Inventory $ (Base) Definition](dendron://dax.definitions.base_measures#2-total-inventory--base)
- [Total Inventory $ Year (Base) Definition](dendron://dax.definitions.base_measures#5-total-inventory--year-base)

## 7. CurrentWeekNum

WeekNum = WEEKNUM(TODAY(), 1)

**Definition:** The `CurrentWeekNum` measure calculates the current week number of the year.

**Explanation:** This measure uses the `WEEKNUM` function to return the week number for the current date.

**Dependencies and Assumptions:** This measure assumes that the model has access to the current date.

**Error Handling:** If the current date cannot be accessed, this measure will return a blank value.

**Related Links:**
- [CurrentYear Definition](dendron://dax.definitions.base_measures#8-currentyear)
- [LastRefreshedDate Definition](dendron://dax.definitions.base_measures#9-lastrefresheddate)

## 8. CurrentYear

CurrentYear = YEAR(TODAY())

**Definition:** The `CurrentYear` measure calculates the current year.

**Explanation:** This measure uses the `YEAR` function to return the current year based on today's date.

**Dependencies and Assumptions:** This measure assumes that the model has access to the current date.

**Error Handling:** If the current date cannot be accessed, this measure will return a blank value.

**Related Links:**
- [CurrentWeekNum Definition](dendron://dax.definitions.base_measures#7-currentweeknum)
- [LastRefreshedDate Definition](dendron://dax.definitions.base_measures#9-lastrefresheddate)

## 9. LastRefreshedDate

LastRefreshedDate = MAX('Last Refresh Date'[Last Refresh])

**Definition:** The `LastRefreshedDate` measure gets the last refresh date from the 'Last Refresh Date' table.

**Explanation:** This measure returns the maximum date from the `Last Refresh Date









