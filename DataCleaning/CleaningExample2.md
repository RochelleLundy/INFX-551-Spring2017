### Filename:  RecycleReport_Tacoma_2013

#### Annotated Cleaning Narrative:
- Mass edit cells in column ﻿Material
- Mass edit cells in column ﻿Material
- Mass edit cells in column ﻿Material
- Text transform on cells in column ﻿Material using expression grel:value.replace("/", " or ")
- Edit single cell on row 28, column ﻿Material
- Text transform on cells in column ﻿Material using expression grel:value.replace(".","")
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
    "description": "Text transform on cells in column ﻿Material using expression grel:value.replace(\"/\", \" or \")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "﻿Material",
    "expression": "grel:value.replace(\"/\", \" or \")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
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