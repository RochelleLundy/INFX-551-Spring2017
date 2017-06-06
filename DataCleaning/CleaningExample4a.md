### Filename:  ElectronicPoundsCollected_WA_2017-04_Table_p1a

#### Annotated Cleaning Narrative:

Rename columns with variable names
- Rename column Column to Covered Electronics Product Type
- Rename column Pounds by CEP* type to Estimated Quantity in Pounds by CEP Type Collected April

Split third column by space regex, remove extra columns created, and rename columns with variable names 
- Split column Estimated Quantity in Pounds by CEP Type Collected April by separator
- Remove column Estimated Quantity in Pounds by CEP Type Collected April 4
- Remove column Estimated Quantity in Pounds by CEP Type Collected April 5
- Rename column Estimated Quantity in Pounds by CEP Type Collected April 3 to Percent of Total Pounds by CEP Type YTD
- Rename column Estimated Quantity in Pounds by CEP Type Collected April 2 to YTD Pounds

Star and remove rows into which variable names initially parsed
- Star row 1
- Star row 2
- Star row 3
- Star row 4
- Star row 5
- Star row 6
- Star row 7
- Remove rows
- Remove rows
	
Standardize case in text
- Text transform on cells in column Covered Electronics Product Type using expression value.toTitlecase()

Remove commas and percentage signs from numbers 
- Text transform on cells in column Estimated Quantity in Pounds by CEP Type Collected April 1 using expression grel:value.replace(",","")
- Text transform on cells in column YTD Pounds using expression grel:value.replace(",","")
- Text transform on cells in column Percent of Total Pounds by CEP Type YTD using expression grel:value.replace("%","")

#### JSON Cleaning Script:

```
[
  {
    "op": "core/column-rename",
    "description": "Rename column Column to Covered Electronics Product Type",
    "oldColumnName": "Column",
    "newColumnName": "Covered Electronics Product Type"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Pounds by CEP* type to Estimated Quantity in Pounds by CEP Type Collected April",
    "oldColumnName": "Pounds by CEP* type",
    "newColumnName": "Estimated Quantity in Pounds by CEP Type Collected April"
  },
  {
    "op": "core/column-split",
    "description": "Split column Estimated Quantity in Pounds by CEP Type Collected April by separator",
    "engineConfig": {
      "mode": "record-based",
      "facets": []
    },
    "columnName": "Estimated Quantity in Pounds by CEP Type Collected April",
    "guessCellType": true,
    "removeOriginalColumn": true,
    "mode": "separator",
    "separator": "\\s",
    "regex": true,
    "maxColumns": 0
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Estimated Quantity in Pounds by CEP Type Collected April 4",
    "columnName": "Estimated Quantity in Pounds by CEP Type Collected April 4"
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Estimated Quantity in Pounds by CEP Type Collected April 5",
    "columnName": "Estimated Quantity in Pounds by CEP Type Collected April 5"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Estimated Quantity in Pounds by CEP Type Collected April 3 to Percent of Total Pounds by CEP Type YTD",
    "oldColumnName": "Estimated Quantity in Pounds by CEP Type Collected April 3",
    "newColumnName": "Percent of Total Pounds by CEP Type YTD"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Estimated Quantity in Pounds by CEP Type Collected April 2 to YTD Pounds",
    "oldColumnName": "Estimated Quantity in Pounds by CEP Type Collected April 2",
    "newColumnName": "YTD Pounds"
  },
  {
    "op": "core/row-removal",
    "description": "Remove rows",
    "engineConfig": {
      "mode": "record-based",
      "facets": [
        {
          "omitError": false,
          "expression": "row.starred",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": true,
                "l": "true"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Starred Rows",
          "omitBlank": false,
          "type": "list",
          "columnName": ""
        }
      ]
    }
  },
  {
    "op": "core/row-removal",
    "description": "Remove rows",
    "engineConfig": {
      "mode": "record-based",
      "facets": [
        {
          "omitError": false,
          "expression": "isBlank(value)",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": true,
                "l": "true"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Estimated Quantity in Pounds by CEP Type Collected April 1",
          "omitBlank": false,
          "type": "list",
          "columnName": "Estimated Quantity in Pounds by CEP Type Collected April 1"
        }
      ]
    }
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Covered Electronics Product Type using expression value.toTitlecase()",
    "engineConfig": {
      "mode": "record-based",
      "facets": []
    },
    "columnName": "Covered Electronics Product Type",
    "expression": "value.toTitlecase()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated Quantity in Pounds by CEP Type Collected April 1 using expression grel:value.replace(\",\",\"\")",
    "engineConfig": {
      "mode": "record-based",
      "facets": []
    },
    "columnName": "Estimated Quantity in Pounds by CEP Type Collected April 1",
    "expression": "grel:value.replace(\",\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column YTD Pounds using expression grel:value.replace(\",\",\"\")",
    "engineConfig": {
      "mode": "record-based",
      "facets": []
    },
    "columnName": "YTD Pounds",
    "expression": "grel:value.replace(\",\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Percent of Total Pounds by CEP Type YTD using expression grel:value.replace(\"%\",\"\")",
    "engineConfig": {
      "mode": "record-based",
      "facets": []
    },
    "columnName": "Percent of Total Pounds by CEP Type YTD",
    "expression": "grel:value.replace(\"%\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  }
]
```