### Filename:  MaterialRecoveryAndDisposal_WA_1986-2014

#### Annotated Cleaning Narrative:

Create new column to capture material type information from subdividing rows in original XLSX format
- Rename column Column to Material Type
- Edit single cell on row 1, column Material Type

Create column of row index numbers in order to use numeric faceting to fill down cell values in new column
- Create column Index at index 1 based on column Material Type using expression grel:rowIndex+1
- Move column Index to position 0
- Fill down cells in column Material Type

Use fill down to fill values in new column and manually fill between facet ranges 
- Edit single cell on row 30, column Material Type
- Edit single cell on row 31, column Material Type
- Edit single cell on row 32, column Material Type
- Edit single cell on row 33, column Material Type
- Edit single cell on row 34, column Material Type
- Edit single cell on row 35, column Material Type
- Edit single cell on row 36, column Material Type
- Edit single cell on row 39, column Material Type
- Edit single cell on row 40, column Material Type
- Fill down cells in column Material Type
- Edit single cell on row 70, column Material Type
- Edit single cell on row 71, column Material Type
- Edit single cell on row 72, column Material Type
- Edit single cell on row 73, column Material Type
- Edit single cell on row 77, column Material Type
- Edit single cell on row 78, column Material Type
- Edit single cell on row 79, column Material Type
- Edit single cell on row 80, column Material Type
- Fill down cells in column Material Type

Relabel column with 'Material' variable name instead of subdividing header
- Rename column MSW Materials Recovered for Recycling (tons): to Material

Remove blank rows and columns using faceting
- Remove rows
- Remove rows
- Remove column Column 31
- Remove column Column 32

Rename each column to remove decimal in year and facet for all non-numeric values (N/A, N/C) and replace with blank values
- Rename column 1986.0 to 1986
- Text transform on cells in column 1986 using expression null
- Text transform on cells in column 1986 using expression null
- Rename column 1988.0 to 1988
 Text transform on cells in column 1988 using expression null
- Text transform on cells in column 1988 using expression null
- Rename column 1989.0 to 1989
- Text transform on cells in column 1989 using expression null
- Rename column 1990.0 to 1990
- Text transform on cells in column 1990 using expression null
- Rename column 1991.0 to 1991
- Text transform on cells in column 1991 using expression null
- Rename column 1992.0 to 1992
- Text transform on cells in column 1992 using expression null
- Rename column 1993.0 to 1993
- Text transform on cells in column 1993 using expression null
- Rename column 1994.0 to 1994
- Text transform on cells in column 1994 using expression null
- Rename column 1995.0 to 1995
- Text transform on cells in column 1995 using expression null
- Rename column 1996.0 to 1996
- Text transform on cells in column 1996 using expression null
- Rename column 1997.0 to 1997
- Text transform on cells in column 1997 using expression null
- Rename column 1998.0 to 1998
- Text transform on cells in column 1998 using expression null
- Rename column 1999.0 to 1999
- Text transform on cells in column 1999 using expression null
- Rename column 2000.0 to 2000
- Text transform on cells in column 2000 using expression null
- Rename column 2001.0 to 2001
- Text transform on cells in column 2001 using expression null
- Rename column 2002.0 to 2002
- Text transform on cells in column 2002 using expression null
- Rename column 2003.0 to 2003
- Text transform on cells in column 2003 using expression null
- Rename column 2004.0 to 2004
- Rename column 2005.0 to 2005
- Rename column 2006.0 to 2006
- Rename column 2007.0 to 2007
- Rename column 2008.0 to 2008
- Rename column 2009.0 to 2009
- Rename column 2010.0 to 2010
- Rename column 2011.0 to 2011
- Rename column 2012.0 to 2012
- Rename column 2013.0 to 2013
- Rename column 2014.0 to 2014

Remove whitespace in text value columns
- Text transform on cells in column Material Type using expression value.trim()
- Text transform on cells in column Material using expression value.trim()

Remove temporary index column created for editing
- Remove column Index

#### JSON Cleaning Script:

```
[
  {
    "op": "core/column-rename",
    "description": "Rename column Column to Material Type",
    "oldColumnName": "Column",
    "newColumnName": "Material Type"
  },
  {
    "op": "core/column-addition",
    "description": "Create column Index at index 1 based on column Material Type using expression grel:rowIndex+1",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "newColumnName": "Index",
    "columnInsertIndex": 1,
    "baseColumnName": "Material Type",
    "expression": "grel:rowIndex+1",
    "onError": "set-to-blank"
  },
  {
    "op": "core/column-move",
    "description": "Move column Index to position 0",
    "columnName": "Index",
    "index": 0
  },
  {
    "op": "core/fill-down",
    "description": "Fill down cells in column Material Type",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": true,
          "expression": "value",
          "selectBlank": true,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "Index",
          "from": 0,
          "to": 30,
          "type": "range",
          "columnName": "Index"
        }
      ]
    },
    "columnName": "Material Type"
  },
  {
    "op": "core/fill-down",
    "description": "Fill down cells in column Material Type",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": true,
          "expression": "value",
          "selectBlank": true,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "Index",
          "from": 40,
          "to": 70,
          "type": "range",
          "columnName": "Index"
        }
      ]
    },
    "columnName": "Material Type"
  },
  {
    "op": "core/fill-down",
    "description": "Fill down cells in column Material Type",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": true,
          "expression": "value",
          "selectBlank": true,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "Index",
          "from": 80,
          "to": 110,
          "type": "range",
          "columnName": "Index"
        }
      ]
    },
    "columnName": "Material Type"
  },
  {
    "op": "core/row-removal",
    "description": "Remove rows",
    "engineConfig": {
      "mode": "row-based",
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
          "name": "Material Type",
          "omitBlank": false,
          "type": "list",
          "columnName": "Material Type"
        }
      ]
    }
  },
  {
    "op": "core/row-removal",
    "description": "Remove rows",
    "engineConfig": {
      "mode": "row-based",
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
          "name": "MSW Materials Recovered for Recycling (tons):",
          "omitBlank": false,
          "type": "list",
          "columnName": "MSW Materials Recovered for Recycling (tons):"
        }
      ]
    }
  },
  {
    "op": "core/column-rename",
    "description": "Rename column MSW Materials Recovered for Recycling (tons): to Material",
    "oldColumnName": "MSW Materials Recovered for Recycling (tons):",
    "newColumnName": "Material"
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Column 31",
    "columnName": "Column 31"
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Column 32",
    "columnName": "Column 32"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1986.0 to 1986",
    "oldColumnName": "1986.0",
    "newColumnName": "1986"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1986 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "omitError": false,
          "expression": "value",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": "N/A",
                "l": "N/A"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "1986",
          "omitBlank": false,
          "type": "list",
          "columnName": "1986"
        }
      ]
    },
    "columnName": "1986",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1986 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "omitError": false,
          "expression": "value",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": "N/C",
                "l": "N/C"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "1986",
          "omitBlank": false,
          "type": "list",
          "columnName": "1986"
        }
      ]
    },
    "columnName": "1986",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1988.0 to 1988",
    "oldColumnName": "1988.0",
    "newColumnName": "1988"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1988 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "omitError": false,
          "expression": "value",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": "N/A",
                "l": "N/A"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "1988",
          "omitBlank": false,
          "type": "list",
          "columnName": "1988"
        }
      ]
    },
    "columnName": "1988",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1988 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "omitError": false,
          "expression": "value",
          "selectBlank": false,
          "selection": [
            {
              "v": {
                "v": "N/C",
                "l": "N/C"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "1988",
          "omitBlank": false,
          "type": "list",
          "columnName": "1988"
        }
      ]
    },
    "columnName": "1988",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1989.0 to 1989",
    "oldColumnName": "1989.0",
    "newColumnName": "1989"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1989 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1989",
          "from": 0,
          "to": 5600000,
          "type": "range",
          "columnName": "1989"
        }
      ]
    },
    "columnName": "1989",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1990.0 to 1990",
    "oldColumnName": "1990.0",
    "newColumnName": "1990"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1990 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1990",
          "from": 0,
          "to": 5700000,
          "type": "range",
          "columnName": "1990"
        }
      ]
    },
    "columnName": "1990",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1991.0 to 1991",
    "oldColumnName": "1991.0",
    "newColumnName": "1991"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1991 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1991",
          "from": 0,
          "to": 5800000,
          "type": "range",
          "columnName": "1991"
        }
      ]
    },
    "columnName": "1991",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1992.0 to 1992",
    "oldColumnName": "1992.0",
    "newColumnName": "1992"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1992 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1992",
          "from": 0,
          "to": 6100000,
          "type": "range",
          "columnName": "1992"
        }
      ]
    },
    "columnName": "1992",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1993.0 to 1993",
    "oldColumnName": "1993.0",
    "newColumnName": "1993"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1993 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1993",
          "from": 0,
          "to": 6500000,
          "type": "range",
          "columnName": "1993"
        }
      ]
    },
    "columnName": "1993",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1994.0 to 1994",
    "oldColumnName": "1994.0",
    "newColumnName": "1994"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1994 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1994",
          "from": 0,
          "to": 7700000,
          "type": "range",
          "columnName": "1994"
        }
      ]
    },
    "columnName": "1994",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1995.0 to 1995",
    "oldColumnName": "1995.0",
    "newColumnName": "1995"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1995 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1995",
          "from": 0,
          "to": 7700000,
          "type": "range",
          "columnName": "1995"
        }
      ]
    },
    "columnName": "1995",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1996.0 to 1996",
    "oldColumnName": "1996.0",
    "newColumnName": "1996"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1996 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1996",
          "from": 0,
          "to": 7500000,
          "type": "range",
          "columnName": "1996"
        }
      ]
    },
    "columnName": "1996",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1997.0 to 1997",
    "oldColumnName": "1997.0",
    "newColumnName": "1997"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1997 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1997",
          "from": 0,
          "to": 8000000,
          "type": "range",
          "columnName": "1997"
        }
      ]
    },
    "columnName": "1997",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1998.0 to 1998",
    "oldColumnName": "1998.0",
    "newColumnName": "1998"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1998 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1998",
          "from": 0,
          "to": 7800000,
          "type": "range",
          "columnName": "1998"
        }
      ]
    },
    "columnName": "1998",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 1999.0 to 1999",
    "oldColumnName": "1999.0",
    "newColumnName": "1999"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 1999 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "1999",
          "from": 0,
          "to": 9400000,
          "type": "range",
          "columnName": "1999"
        }
      ]
    },
    "columnName": "1999",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2000.0 to 2000",
    "oldColumnName": "2000.0",
    "newColumnName": "2000"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 2000 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "2000",
          "from": 0,
          "to": 12000000,
          "type": "range",
          "columnName": "2000"
        }
      ]
    },
    "columnName": "2000",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2001.0 to 2001",
    "oldColumnName": "2001.0",
    "newColumnName": "2001"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 2001 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "2001",
          "from": 0,
          "to": 12000000,
          "type": "range",
          "columnName": "2001"
        }
      ]
    },
    "columnName": "2001",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2002.0 to 2002",
    "oldColumnName": "2002.0",
    "newColumnName": "2002"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 2002 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "2002",
          "from": 0,
          "to": 13000000,
          "type": "range",
          "columnName": "2002"
        }
      ]
    },
    "columnName": "2002",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2003.0 to 2003",
    "oldColumnName": "2003.0",
    "newColumnName": "2003"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column 2003 using expression null",
    "engineConfig": {
      "mode": "row-based",
      "facets": [
        {
          "selectNumeric": false,
          "expression": "value",
          "selectBlank": false,
          "selectNonNumeric": true,
          "selectError": true,
          "name": "2003",
          "from": 0,
          "to": 13000000,
          "type": "range",
          "columnName": "2003"
        }
      ]
    },
    "columnName": "2003",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2004.0 to 2004",
    "oldColumnName": "2004.0",
    "newColumnName": "2004"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2005.0 to 2005",
    "oldColumnName": "2005.0",
    "newColumnName": "2005"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2006.0 to 2006",
    "oldColumnName": "2006.0",
    "newColumnName": "2006"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2007.0 to 2007",
    "oldColumnName": "2007.0",
    "newColumnName": "2007"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2008.0 to 2008",
    "oldColumnName": "2008.0",
    "newColumnName": "2008"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2009.0 to 2009",
    "oldColumnName": "2009.0",
    "newColumnName": "2009"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2010.0 to 2010",
    "oldColumnName": "2010.0",
    "newColumnName": "2010"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2011.0 to 2011",
    "oldColumnName": "2011.0",
    "newColumnName": "2011"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2012.0 to 2012",
    "oldColumnName": "2012.0",
    "newColumnName": "2012"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2013.0 to 2013",
    "oldColumnName": "2013.0",
    "newColumnName": "2013"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column 2014.0 to 2014",
    "oldColumnName": "2014.0",
    "newColumnName": "2014"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Material Type using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Material Type",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Material using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Material",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Index",
    "columnName": "Index"
  }
]
```
