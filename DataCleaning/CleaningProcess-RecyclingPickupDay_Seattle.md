### Filename:  RecyclingPickupDay_Seattle

#### Annotated Cleaning Narrative:

Remove special characters from column names
- Rename column ���OBJECTID to OBJECTID

Standardize case of column names
- Rename column Shape to SHAPE
- Rename column Shape_Length to SHAPE_LENGTH
- Rename column Shape_Area to SHAPE_AREA

Remove commas from numeric values
- Text transform on cells in column SHAPE_LENGTH using expression grel:value.replace(",", "")
- Text transform on cells in column SHAPE_AREA using expression grel:value.replace(",", "")

Remove parentheses from shape coordinate values
- Text transform on cells in column SHAPE using expression grel:value.replace("(","").replace(")","")

Split shape coordinate column into latitude and longitude columns
- Split column SHAPE by separator
- Rename column SHAPE 1 to SHAPE_LATITUDE
- Rename column SHAPE 2 to SHAPE_LONGITUDE

Check for and trim whitespaces from all values by column
- Text transform on cells in column OBJECTID using expression value.trim()
- Text transform on cells in column SHAPE_LATITUDE using expression value.trim()
- Text transform on cells in column SHAPE_LONGITUDE using expression value.trim()
- Text transform on cells in column ZONE using expression value.trim()
- Text transform on cells in column CONTRACTOR using expression value.trim()
- Text transform on cells in column CNTR_DESC using expression value.trim()
- Text transform on cells in column SUBZONE using expression value.trim()
- Text transform on cells in column FREQUENCY using expression value.trim()
- Text transform on cells in column PCKUP_DAY using expression value.trim()
- Text transform on cells in column ROUTE_ID using expression value.trim()
- Text transform on cells in column SHAPE_LENGTH using expression value.trim()
- Text transform on cells in column SHAPE_AREA using expression value.trim()

#### JSON Cleaning Script:
```
[
  {
    "op": "core/column-rename",
    "description": "Rename column ���OBJECTID to OBJECTID",
    "oldColumnName": "���OBJECTID",
    "newColumnName": "OBJECTID"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Shape to SHAPE",
    "oldColumnName": "Shape",
    "newColumnName": "SHAPE"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Shape_Length to SHAPE_LENGTH",
    "oldColumnName": "Shape_Length",
    "newColumnName": "SHAPE_LENGTH"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Shape_Area to SHAPE_AREA",
    "oldColumnName": "Shape_Area",
    "newColumnName": "SHAPE_AREA"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_LENGTH using expression grel:value.replace(\",\", \"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_LENGTH",
    "expression": "grel:value.replace(\",\", \"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_AREA using expression grel:value.replace(\",\", \"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_AREA",
    "expression": "grel:value.replace(\",\", \"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE using expression grel:value.replace(\"(\",\"\").replace(\")\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE",
    "expression": "grel:value.replace(\"(\",\"\").replace(\")\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-split",
    "description": "Split column SHAPE by separator",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE",
    "guessCellType": true,
    "removeOriginalColumn": true,
    "mode": "separator",
    "separator": ",",
    "regex": true,
    "maxColumns": 0
  },
  {
    "op": "core/column-rename",
    "description": "Rename column SHAPE 1 to SHAPE_LATITUDE",
    "oldColumnName": "SHAPE 1",
    "newColumnName": "SHAPE_LATITUDE"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column SHAPE 2 to SHAPE_LONGITUDE",
    "oldColumnName": "SHAPE 2",
    "newColumnName": "SHAPE_LONGITUDE"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column OBJECTID using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "OBJECTID",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_LATITUDE using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_LATITUDE",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_LONGITUDE using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_LONGITUDE",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column ZONE using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "ZONE",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column CONTRACTOR using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "CONTRACTOR",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column CNTR_DESC using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "CNTR_DESC",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SUBZONE using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SUBZONE",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column FREQUENCY using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "FREQUENCY",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column PCKUP_DAY using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "PCKUP_DAY",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column ROUTE_ID using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "ROUTE_ID",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_LENGTH using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_LENGTH",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column SHAPE_AREA using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "SHAPE_AREA",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  }
]
```
