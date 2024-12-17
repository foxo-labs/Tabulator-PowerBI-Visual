# Overview
Tabulator allows you to sort the data in your table in any way you want either by clicking on column headers or by calling a number of sort functions on the table.

By default Tabulator will attempt to guess which sorter should be applied to a column based on the data contained in the first row. It can determine sorters for strings, numbers, alphanumeric sequences and booleans, anything else will be treated as a string.

To specify a sorter to be used on a column use the sorter property in the columns definition object

You can pass an optional additional property with sorter, sorterParams that should contain an object with additional information for configuring the sorter.

Tabulator Options: Column Options
```json
{ 
 "dateColumnName": 
    {
        "sorter":"datecustom", 
        "sorterParams":{"format":"dd/MM/yy"}
    }
}
```

### Params Lookup Function
If you want to dynamically generate the sorterParams at the time the sort is called you can pass a function into the property that should return the params object.

Tabulator Options: Column Options
```json
{ 
 "dateColumnName": 
    {
        "sorter":"datecustom", 
        "sorterParams":"function (column, dir){ return {param1:'green'};}"
    }
}
```

## Table of Contents
1. [Built In Sorters](#1-built-in-sorters)
2. Custom Sorters
3. Header Sorting
4. Initial Sort

## 1. Built In Sorters

Tabulator comes with a number of preconfigured sorters including:
> [String](#string)
> [Numeric](#numeric)
> [Alphanumeric](#alphanumeric)
> [Boolean](#boolean)
> [Field Exists](#field-exists)
> [Date : Date, Time & DateTime](#date-date-time--datetime)
> [Array](#array)

### String
The string sorter will sort columns as strings of characters
```json
{
"Region" : { "sorter":"string" }
}
```

### Numeric
The number sorter will sort column as numbers (integer or float, will also handle numbers using "," separators)
```json
{
    "Sales" : { 
        "sorter" :"number", 
        "sorterParams" :{
            "thousandSeparator":",",
            "decimalSeparator":",",
            "alignEmptyValues":"top"
        }
    }
}
```

### Alphanumeric
The alphanumeric sorter sorts columns in a way that treats mixed data (letters and numbers) in the order they appear. This is useful for sorting columns that contain both text and numerical data, such as item codes or identifiers.
```json
{
  "ProductCode": {
    "sorter": "alphanumeric"
  }
}
```

### Boolean
The boolean sorter sorts columns that contain boolean values (true or false). This is helpful when working with columns representing binary values or flags.
```json
{
  "Active": {
    "sorter": "boolean"
  }
}
```

### Field Exists
The field exists sorter sorts columns based on whether a value is present (i.e., whether the field exists or is null). This is useful when you want to prioritize rows with data over those with missing values.
```json
{
  "DataAvailable": {
    "sorter": "fieldExists"
  }
}
```
### Date: Date, Time & DateTime
The custom sorting syntax for Date and DateTime columns allows you to specify the date format in which your data is represented. This ensures that the dates are correctly parsed and sorted in ascending or descending order.
```json
{
  "PlannedDate": {
    "sorter": "datecustom",
    "sorterParams": {
      "format": "dd-mm-yyyy HH:mm:ss"
    }
  }
}
```
In the example above:

1. The PlannedDate column is configured to use the custom date sorter (datecustom).
2. The sorterParams contain the format option, specifying the format of the date (dd-mm-yyyy HH:mm:ss).
3. This format includes both the date and time components.

#### Common Date Formats
Luxon supports a variety of Date and DateTime formats. You can specify any of the following formats in the sorterParams object to ensure accurate sorting:

> d/m/yyyy – e.g., 6/1/2019
> mm/dd/yyyy – e.g., 01/06/2019
> yyyy-mm-dd – e.g., 2019-01-06
> MMM dd, yyyy – e.g., Jan 06, 2019
> MMMM dd, yyyy – e.g., January 06, 2019
> mm/dd/yy – e.g., 01/06/19
> dd-MMM-yyyy – e.g., 06-Jan-2019
> yyyy.mm.dd – e.g., 2019.01.06
> MMM-yy – e.g., Jan-19
> dd/mm/yyyy t – e.g., 06/01/2019 12:00 AM

These formats can be used in the sorterParams to indicate how the date values are formatted and should be interpreted by the sorting function.

For more sorterParams formatting options, please refer to the [Luxon Formatting Documentation](https://github.com/moment/luxon/blob/master/docs/formatting.md).

### Array
The array sorter sorts columns that contain arrays (i.e., multiple values in each cell). This sorter sorts based on the array's elements, allowing you to handle list-based data efficiently.
```json
{
  "Tags": {
    "sorter": "array"
  }
}
```

## 2. Custom Sorters
You can create custom sorters if the built-in ones do not meet your requirements. Custom sorters allow you to define your own sorting logic for specific columns.
To create a custom sorter, you can use a function. The function takes two parameters (the data from the two rows being compared) and must return a numerical value that determines the sort order.

```json
{
  "ProductName": {
    "sorter": "function(a, b) { return a.toLowerCase() < b.toLowerCase() ? -1 : 1; }"
  }
}
```

## 3. Header Sorting
By default all columns in a table are sortable by clicking on the column header, if you want to disable this behaviour, set the headerSort property to false.

This can be set per column in the column definition:
```json
{
  "Region": {
    "headerSort": false
  }
}
```
### Multi Column Sorting
By default you can sort by multiple columns at the same time by holding the `ctrl` or `shift` key when you click on the column headers.

if you wish to disable this behaviour, so only once column can be sorted at a time, you can set the columnHeaderSortMulti option to false under **Options** in Tabulator Options
```json
{
    "columnHeaderSortMulti":false
}
```

### Clickable Element
By default, header sorting is managed by clicking anywhere on the column header element. If you would prefer to restrict this to just the sort icon then you can configure this by setting the headerSortClickElement option to icon:
```json
{
    "headerSortClickElement":"icon"
}
```

### Initial Sort
When the table is first created it can be defined with an initial set of sorters. These can be set using the initialSort option.
```json
{
    "layout":"fitDataTable",
    "initialSort":[
            {"column":"Sales", "dir":"desc"},
            {"column":"Channels", "dir":"asc"} 
        ]
}
```
