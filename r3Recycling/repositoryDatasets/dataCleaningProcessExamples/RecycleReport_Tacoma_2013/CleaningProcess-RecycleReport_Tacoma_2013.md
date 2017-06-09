### Filename:  RecycleReport_Tacoma_2013

#### Annotated Cleaning Narrative:

Correct spelling errors and capitalization inconsistencies in individual cells based on text faceting
- Mass edit cells in column ﻿Material
- Mass edit cells in column ﻿Material
- Mass edit cells in column ﻿Material

Remove "." character from text values in Material column
- Text transform on cells in column ﻿Material using expression grel:value.replace(".","")

Check for and trim whitespaces from values by column
- Text transform on cells in column ﻿Material using expression value.trim()
- Text transform on cells in column Tons using expression value.trim()

#### JSON Cleaning Script:

```
[
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column ﻿Material",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Compresor Oil"
        ],
        "to": "Compressor Oil"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column ﻿Material",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Wood WASTE"
        ],
        "to": "Wood Waste"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column ﻿Material",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "LDPE FOAM"
        ],
        "to": "LDPE Foam"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column ﻿Material using expression grel:value.replace(\".\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "grel:value.replace(\".\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column ﻿Material using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Tons using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Tons",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  }
]
```
