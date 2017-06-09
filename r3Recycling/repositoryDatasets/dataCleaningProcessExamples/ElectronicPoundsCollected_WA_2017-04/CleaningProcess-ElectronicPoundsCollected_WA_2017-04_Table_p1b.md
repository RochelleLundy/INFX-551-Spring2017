### Filename:  ElectronicPoundsCollected_WA_2017-04_Table_p1b

#### Annotated Cleaning Narrative:

Remove commas and percentage signs from numbers
- Text transform on cells in column Estimated quantity in pounds by WA State county April using expression grel:value.replace(",","")
- Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression grel:value.replace(",","")
- Text transform on cells in column Percent of total pound by county YT April using expression grel:value.replace("%","")

Change values to number type for numeric facet
- Text transform on cells in column Estimated quantity in pounds by WA State county April using expression value.toNumber()
- Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression value.toNumber()

Identify non-numeric values (NR) with numeric facet and blank out
- Text transform on cells in column Estimated quantity in pounds by WA State county April using expression null

Check for and trim whitespaces from values by column
- Text transform on cells in column WA State County using expression value.trim()
- Text transform on cells in column Estimated quantity in pounds by WA State county April using expression value.trim()
- Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression value.trim()
- Text transform on cells in column Percent of total pound by county YT April using expression value.trim()

#### JSON Cleaning Script:
```
[
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county April using expression grel:value.replace(\",\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county April",
    "expression": "grel:value.replace(\",\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression grel:value.replace(\",\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county YTD April",
    "expression": "grel:value.replace(\",\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Percent of total pound by county YT April using expression grel:value.replace(\"%\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Percent of total pound by county YT April",
    "expression": "grel:value.replace(\"%\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county April using expression value.toNumber()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county April",
    "expression": "value.toNumber()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression value.toNumber()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county YTD April",
    "expression": "value.toNumber()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county April using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": true,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "Estimated quantity in pounds by WA State county April",
          "from": 0,
          "to": 2700000,
          "type": "range",
          "columnName": "Estimated quantity in pounds by WA State county April"
        }
      ]
    },
    "columnName": "Estimated quantity in pounds by WA State county April",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column WA State County using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "WA State County",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county April using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county April",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Estimated quantity in pounds by WA State county YTD April using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Estimated quantity in pounds by WA State county YTD April",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Percent of total pound by county YT April using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Percent of total pound by county YT April",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  }
]
```
