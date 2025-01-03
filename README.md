# Tabulator-Custom-Visual Documentation

## Table of Contents
1. [Introduction](#1-introduction)
2. [Installation](#2-installation)
3. [Getting Started](#3-getting-started)
4. [Customization](#4-customization)
5. [Features](#5-features)
6. [Frequently Asked Questions](#6-frequently-asked-questions)
7. [Support](#7-support)

## 1. Introduction

The Tabulator Custom Visual is a powerful tool to enhance your Power BI reports. It allows you to transform your data into interactive Tabulator tables, making it easy to analyze and visualize your information. This custom visual offers seamless integration and user-friendly features, taking your data presentation to the next level and making insights accessible and actionable.

## 2. Installation

To begin utilizing the Tabulator Custom Visual, please follow these installation instructions:

1. Launch Power BI Desktop.
2. Access the Visualization Pane and click on the ellipsis (three dots).
3. Choose "Get More Visuals" from the menu.
4. Search for "tabulator-custom-visual."
5. Click on the "Install" button.
6. The Tabulator Custom Visual will be automatically integrated into your Power BI report.

## 3. Getting Started

After importing the Tabulator Custom Visual, you can begin using it to display your data in tabular format.

- **Adding Data**:
  - Drag and drop data columns into the "Category Data" and "Measure Data" fields in the visualizations pane.

- **Configuring Tabulator Options**:
  - In the formatting pane, you can configure various Tabulator options to customize the table's appearance and behavior. Edit the "Tabulator Options" and "Column Options" as needed.

- **Exploring Data**:
  - Interact with the table to explore your data visually. You can sort, filter, and perform other data operations within the table.

- **Adding Visualizations**:
  - The Tabulator Custom Visual works well with other Power BI visuals. You can add charts, graphs, and other visualizations to complement your table.

## 4. Customization

### Tabulator Options

The "Tabulator Options" property allows you to pass a JSON object with settings for the Tabulator table. These settings can control the layout, pagination, sorting, and more. Here's an example:

```json
{
    "layout": "fitDataStretch",
    "pagination": "local",
    "paginationSize": 10,
    "sortable": true
}
```
The default layout is set to fitDataTable, which ensures that the table adjusts automatically to fit the available space. This setting can be customized to other layout options such as fitDataStretch or fitDataFill, depending on your requirements. For more examples and further customization, visit this [link](https://appsource.microsoft.com/en-us/product/power-bi-visuals/foxolabsopcpvtltd1698255416379.tabulator-custom-visual?tab=overview).

Tabulator documentation provides general table-level settings like:
```javascript
var table = new Tabulator("#example-table", {
    height: "100%", // Sets the table height to 100% of its container
});
```

When configuring the Tabulator Custom Visual in Power BI, this setting would appear as below under **Options** in Tabulator Options:
```json
{
  "height": "100%"
}
```


### Column Options

The "Column Options" property lets you specify settings for individual columns in the Tabulator table, such as column width, responsiveness, and more. Here's an example:

```json
{
    "columnName": {
        "responsive": 0,
        "resizable": true
    }
}
```

Tabulator documentation provides general column-level settings like:
```javascript
var table = new Tabulator("#example-table", {
    layout:"fitColumns",
    columns:[
        {title:"Name", field:"name", width:100}, //column has a fixed width of 100px;
        {title:"Age", field:"age", widthGrow:1}, //column will be allocated 1/5 of the remaining space
        {title:"Color", field:"color", widthGrow:3}, //column will be allocated 3/5 of the remaining space
        {title:"location", field:"location"}, // column has a default widthGrow of 1 and will be allocated 1/5 of the remaining space
    ]
});
```
In the Power BI Tabulator Custom Visual, these settings are written as Column Options. The format is:
```json
{
  "Name": {
    "width": 100
  },
  "Age": {
    "widthGrow": 1
  },
  "Color": {
    "widthGrow": 3
  },
  // No configuration for Location as it uses default settings, and 'title' and 'field' properties are omitted in Column Options
}
```


### Adding Calculated Columns
Calculated columns allow you to create new data columns derived from existing data within your dataset. You can define calculated columns in the "Calculated Columns" property in the formatting pane. Here's an example of how to add a calculated column:
```json
{
  "TotalPrice": "function(rowData) { return rowData['UnitPrice'] * rowData['Quantity']; }"
}
```
In this example, a new column called TotalPrice is calculated based on existing columns UnitPrice and Quantity. You can write your own JavaScript functions to define more complex calculated columns as needed.

Once the calculated columns are defined, they will be automatically included in the Tabulator table with the same functionality as regular columns. The calculation is performed dynamically based on the row data, and any updates to the underlying data will automatically update the calculated columns.

## 5. Features

For a detailed overview of the features, please refer to the [Features Documentation](https://github.com/foxo-labs/Tabulator-PowerBI-Visual/blob/main/Features.md).

## 6. Frequently Asked Questions (FAQs)

**Q:** How do I change the appearance of my table?

**A:** You can customize the appearance by adjusting the "Tabulator Options" and "Column Options" properties in the formatting pane.

**Q:** Can I use this visual with my existing Power BI reports?

**A:** Yes, you can add the Tabulator Custom Visual to your existing reports by importing the .pbiviz file.

## 7. Support

For any questions or issues, please contact our support team at [inquiry@tekvo.io](mailto:inquiry@tekvo.io). We are here to assist you.



