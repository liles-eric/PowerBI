---
id: base-and-misc-measures
title: Base and Misc Measures
desc: This document provides detailed definitions and explanations of the DAX measures used in our Power BI projects, including both base and miscellaneous measures.
created: 2024-11-04
updated: 2024-11-04
author: Eric Liles
version: 1.0
---

# Base and Misc Measures

This document provides detailed definitions and explanations of the DAX measures used in our Power BI projects, including both base and miscellaneous measures.

## Base Measures

### 1. # of Items (Base)

No. of Items (Base) = DISTINCTCOUNT('Inventory History'[ItemId])

### 2. Total Inventory (Base)

Total Inventory $ (Base) = SUM('Inventory History'[Inv_ExtPrice])

### 3. Total COGS (Base)

Total COGS $ (Base) = SUM('TrxEntry'[Ext COGS $])

### 4. Total Inventory Qty (Base)

Total Inventory Qty (Base) = SUM('Inventory History'[Quantity])

### 5. Total COGS $ Year (Base)

Total COGS $ Year (Base) =
CALCULATE(
    SUM('TrxEntry'[Ext COGS $]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

### 6. Total Invetory $ Year (Base)

Total Inventory $ Year (Base) =
CALCULATE(
    SUM('Inventory History'[Inv_ExtPrice]),
    DATESINPERIOD('DateDim'[Date], LASTDATE('DateDim'[Date]), -365, DAY)
)

## Misc Measures

### 7. CurrentWeekNum

CurrentWeekNum = WEEKNUM(TODAY(), 1)

### 8. CurrentYear

CurrentYear = YEAR(TODAY())

### 9. LastRefreshedDate

LastRefreshedDate = MAX('Last Refresh Date'[Last Refresh])

### 10. Greeting

Greeting =
VAR CurrentUser = USERPRINCIPALNAME()
VAR CurrentDate = TODAY()
VAR YearStart = DATE(YEAR(CurrentDate), 1, 1)
VAR DayOfYear = DATEDIFF(YearStart, CurrentDate, DAY) + 1
VAR WeekNum = WEEKNUM(CurrentDate)
VAR UserPreferredName = LOOKUPVALUE(EmployeeDim[PreferredName], EmployeeDim[email], CurrentUser)
VAR IsUserFound = NOT(ISBLANK(UserPreferredName))
VAR LastRefresh = [LastRefreshedDate]
RETURN
IF(
    IsUserFound,
    "> Hello " & UserPreferredName & "! It's " & FORMAT(CurrentDate, "MM/dd/yyyy") & ", Work Week " & WeekNum & ", day " & DayOfYear & " of " & YEAR(CurrentDate) & ". Data last refreshed: " & FORMAT(LastRefresh, "MM/dd/yyyy"),
    "> Warning: Your login isn't in the system, Mysterious Stranger. If you're not an employee, kindly make your exit. If you are, sign into PowerBI!"
)



