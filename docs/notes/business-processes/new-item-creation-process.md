---
id: new-item-creation-process
title: New Item Creation Process
desc: Process for setting up new items in the system following best practices for Master Data Management (MDM).
created: {{date:2024-11-04}}
updated: {{date:2024-11-04}}
author: Eric Liles
version: 1.0
---

# New Item Creation Process

This document outlines the process for setting up new items in the system following best practices for Master Data Management (MDM). The process starts with a request from a Category Manager and continues through item creation and validation in the system.

**Link to Decision Tree:** [Decision Tree - New Item Creation](../DecisionTree/New-Item-Creation-Decision-Tree.md)

## Prerequisites

Before starting the setup process, ensure that the following prerequisites are met:

- [ ] The initial item setup request has been received via the MDM email inbox from a Category Manager.
- [ ] Access to the TA Wholesale system (or applicable Master Data/ERP system) with the required permissions.
- [ ] Vendor's item information spreadsheet is available.
- [ ] Knowledge of system-specific configurations (e.g., categories, item types).
- [ ] Familiarity with the MSA code and other system documentation.

### Vendor and Category Management

- Vendors and items are generally assigned to one Category Manager. However, exceptions can occur. If there is a key point of contact for a specific vendor, the process should reflect that.
- Discuss with the Category Managers whether all items should be set up together or if there are any priorities.

## Process Overview

### 1. Receiving the Request

1. **Initial Request**: Ensure the request comes from a Category Manager (or equivalent role).
2. **Verify Related Emails**: Check for any related emails in the MDM inbox to ensure all relevant details are accounted for before proceeding. If the item request is incomplete, consolidate information from all related emails before continuing.
3. **Validate Information**: Confirm that the vendor's item information spreadsheet is attached and complete. This includes essential item data such as UPC, item descriptions, price, and packaging details.
4. **Determine Template Use**: Decide whether to generate the **New Item Template for easier data entry**. If yes, generate the template using this link: [New Item Template Documentation](https://github.com/eliles-ghra/GHRA-Data-Projects/blob/main/Codespaces%20-%20Primary%20Root%20Location%20for%20Everything/vault/BusinessProcessees/Templates/MDM/Internal-New-Item-Template.md).

### 2. Logging Into the TA Wholesale System
   (or applicable Master Data/ERP system)

1. Log into the system using your credentials.
2. Navigate to the "Inventory" section and select "Item Browser."
3. Click on "New Item (Quick)" to open the item creation panel.

### 3. Inputting Basic Item Information

1. **Item Lookup Code (UPC)**: Enter the **Master Case UPC** from the vendor's item information spreadsheet into the item lookup code. Ensure that this is the case UPC, not the unit UPC.
2. **Item Description**: Follow the format `Vendor Name > Item Type > Flavor/Color > Quantity/Amount`. Example:
   - Case: `FEBREZE AIR BRY&BRMBLE 6-8.8oz`
   - Single: `FEBREZE AIR BRY&BRMBLE 8.8oz`
3. **Price**: On the quick item entry screen, calculate the price using the following methods:
   - **Option 1**: Find similar items of the same size from the same vendor and use their pricing as a reference.
   - **Option 2**: If no similar item exists, calculate the price based on the sought margin and market standards, using a margin calculator if necessary. Ask the Master Data team for approval/verification if unsure.
4. **MSA Units**: The MSA count is based on the **Master Case quantity** from the vendor's item information spreadsheet. For example, if the case contains six units, input `6`.
5. **Item Tax Status**: Note that almost all items are non-taxable, with exceptions for items intended for store use.

### 4. Configuring Additional Item Attributes

1. **Extended Description**: Enter a longer, more detailed description in the "Extended Description" field.
2. **Supplier Cost**: Set up the supplier cost (negotiated invoice cost) based on the information provided by the Category Manager. Confirm this with the vendor's item information spreadsheet or the vendor's ordering website.
3. **Master Pack Quantity (MPQ)**: The Master Pack Quantity should be set as `1` if the item is set up to sell as a case. Refer to the vendor’s item information spreadsheet if unsure.
4. **Dimensions**: On the second screen, input dimensions for the **Master Case**, not the pallet.
5. **Buyer**: Set up the buyer based on the supply planner's information.
6. **MSA Category Code**: Use the MSA category code from a similar item. The size of the item does not affect the MSA code.
7. **Item Sell Type**: Set the sell type to "New Item."
8. **Packaging Type**: Set the packaging type to "Case" if the item is sold as a case. Ensure the packaging type reflects how the item is intended to be sold.

### 5. Completing and Validating the Item Setup

1. **Warehouse Dimensions**: Enter the item's dimensions (height, width, depth) and weight, based on whether it is sold as a case or a single item.
2. **Shelf Life**: Set the shelf life based on the vendor's specifications.
3. **EDI/Other Tab**: Enter the consumer description, retail UPC, and unit dimensions.
4. **Supplier Tab**: Ensure all relevant supplier information, such as MOQ and item conversion factor, is filled out.

### 6. Generating the Product Code

1. After saving the initial item details, go to the "Inventory" menu and select "General Item Code for New Items."
2. Generate a 5-digit product code and input this into the "Product Code" field under the "General" tab for the new item.

### 7. Final Validation and Publishing

1. Review all the information entered for accuracy.
2. Submit the item for approval if necessary.
3. Publish the item to make it live in the system once approved.

## Error Handling and Common Issues

*Placeholder section for documenting potential errors, troubleshooting steps, and solutions to common problems encountered during the item setup process.*

**Link to Decision Tree:** [Decision Tree - New Item Creation](../DecisionTree/New-Item-Creation-Decision-Tree.md)

## Checklist for Setting Up New Items

- [ ] Received request from a Category Manager.
- [ ] Vendor’s item information spreadsheet reviewed.
- [ ] Logged into the TA system (or applicable Master Data/ERP system).
- [ ] Entered item UPC, description, and price.
- [ ] Configured metadata, attributes, and dimensions.
- [ ] Set up supplier and MSA category information.
- [ ] Generated and added product code.
- [ ] Submitted item for approval and published.
