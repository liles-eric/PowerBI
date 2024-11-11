---
id: h56zdrh2kxgb603hpemq2bl
title: Time Based Measures Definitions
desc: ''
updated: 1730754988004
created: 1730754988004
---
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

## Overview

This document outlines a set of DAX measures used for time-based analysis in Power BI. These measures are designed to track and compare performance across various time periods such as the current week, two weeks ago, and the same week last year. The measures calculate values such as inventory levels, cost of goods sold (COGS), and item quantities based on the specified time filters.

### Prerequisites
- Ensure that you have a marked date table in your Power BI model.
- For more details on setting up a date table, refer to the [Date Table Definition and Setup](dendron://dax.documentation#date-table-setup).

### Time-Based Measures

1. **2 Weeks Ago # of Items (Time)**
2. **2 Weeks Ago Total Inventory $ (Time)**
3. **Last Week # of Items (Time)**
4. **LW Total Inventory $ (Time)**
5. **Same Week LY Total Inv $ (Time)**
6. **Same Week LY Total Inv Qty (Time)**
7. **2 Weeks Ago Average COGS $ Year (Time)**
8. **2 Weeks Ago Average Inventory $ Year (Time)**
9. **2 Weeks Ago Total COGS $ Year (Time)**
10. **LW Average COGS $ Year (Time)**

### Related Links
- [Last Week # of Items (Time) Definition](dendron://dax.definitions.time_based_measures#3-last-week--of-items-time)
- [2 Weeks Ago # of Items (Time) Definition](dendron://dax.definitions.time_based_measures#1-2-weeks-ago--of-items-time)
- [Date Table Setup](dendron://dax.documentation#date-table-setup)
---

### Notes
- Each measure assumes that the respective tables (`DateDim`, `Inventory History`, `TrxEntry`, etc.) are structured correctly and that necessary columns (such as `YearWeek`, `Inv_ExtPrice`, and `Ext COGS $`) are available.
- If there are any missing or incorrect columns, the measure will return a blank value.

# DAX Definitions for Time-Based-Measures

This document offers concise definitions and explanations for DAX measures used in our business intelligence projects, sourced from transaction and dimension tables for analysis in Power BI and Excel PowerPivot.
