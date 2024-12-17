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

Please refer to the documentation [here](Features/Sorting.md)

## 5. Context Menu

The Context Menu provides right-click functionality for rows and cells within the Tabulator table. It allows users to perform a variety of actions such as copying values, rows, and clearing selections or filters. These operations can be accessed by right-clicking on the table.
![Context Menu](ContextMenu.png)

### Key Features:
    1. Row and Cell Selection: Right-click functionality is available on both rows and cells.
    2. Copy Operations: The context menu provides options to copy values, rows, rows with headers, and selected rows.
    3. Clear Selections and Filters: Options are available to clear selections and filters applied to the table.
    4. Power BI Context Menu: A custom context menu is available for Power BI-specific operations.

When a user right-clicks on a cell or row, the following options are available in the context menu:

    1. Copy Value: Copies the value of the selected cell to the clipboard.
    2. Copy Row: Copies the entire row data in CSV format to the clipboard.
    3. Copy Row with Header: Copies the row data along with column headers in CSV format to the clipboard.
    4. Copy Table: Copies the entire table data (including headers) to the clipboard in CSV format.
    5. Copy Selected Rows: Copies the selected rows' data (including headers) to the clipboard.
    6. Clear Selections: Clears all selected rows.
    7. Clear All Filters: Clears all applied filters from the table.
    8. Power BI Menu: Opens a default Power BI context menu for additional options.

## 6. Cell Tooltips

Display additional data in tooltips on each table cell. This provides more information without overcrowding the table, enhancing the user experience.

## 7. Excel-Like Filtering

Include filter options directly within the table header. This functionality mimics Excel's filtering behavior, making it easy for users to filter rows based on specific values.


## 8. Dynamic Row Selection

Select multiple rows programmatically and interactively with built-in selection management. This feature is especially useful when dealing with large datasets or specific data operations.

## 9. Pagination

Customize pagination behavior to handle large datasets by displaying a set number of rows per page, making the data easier to navigate.
