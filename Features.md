# Tabulator-Custom-Visual Features

## Table of Contents
1. [Interactive Table](#1-interactive-table)
2. [Custom Layouts](#2-custom-layouts)
3. [Calculated Columns](#3-calculated-columns)
4. [Custom Sorting](#4-custom-sorting)
5. [Context Menu](#5-context-menu)
6. [Cell Tooltips](#6-cell-tooltips)
7. [Excel-Like Filtering](#7-excel-like-filtering)
8. [Dynamic Row Selection](#8-dynamic-row-selection)
9. [Pagination](#9-pagination)

## 1. Interactive Table

Display and interact with data in a table format with features like sorting, filtering, and pagination. The table is highly customizable and provides users with a seamless data exploration experience.

## 2. Custom Layouts

Control the table layout using the `Tabulator Options`, including the ability to adjust column widths and set fixed or auto-fit table layouts. This enables a flexible presentation of your data depending on the space available.

Please refer to the documentation [here](Features/Table%20Layouts.md)

## 3. Calculated Columns

Add calculated columns that derive values based on other columns in the dataset. These calculations are dynamic and update automatically when the data changes.

### Tabulator Options: Calculated Columns
Calculated Columns can be defined in the Calculated Columns section. You can write functions that derive values based on existing data.

Example for a calculated column:
```json
{
  "TotalPrice": "function(rowData) { return rowData['UnitPrice'] * rowData['Quantity']; }"
}
```

## 4. Custom Sorting

Implement custom sorting behavior, such as sorting by date, using built-in or user-defined functions. This allows for more sophisticated data organization within the table.

## 5. Context Menu

Right-click context menu functionality is available for row and cell selection, offering additional operations and interactions that are customizable.

## 6. Cell Tooltips

Display additional data in tooltips on each table cell. This provides more information without overcrowding the table, enhancing the user experience.

## 7. Excel-Like Filtering

Include filter options directly within the table header. This functionality mimics Excel's filtering behavior, making it easy for users to filter rows based on specific values.

## 8. Dynamic Row Selection

Select multiple rows programmatically and interactively with built-in selection management. This feature is especially useful when dealing with large datasets or specific data operations.

## 9. Pagination

Customize pagination behavior to handle large datasets by displaying a set number of rows per page, making the data easier to navigate.
