### Filename:  RecyclingOptions_KingCty

#### Annotated Cleaning Narrative (multiple operations of same type condensed into single items as noted):

Remove special characters from column names
- Rename column ÔªøProviderID to ProviderID

Facet, cluster, merge and perform to standardize column values and remove special characters and HTML tags

(Note: columns with variable, free-text entries, including 'Hours', 'Fees', and 'Restructions', were subject to some transformation for cleaning, but 
could not be effectively standardized given nature of values) 

- Mass edit cells in column Provider Name
- Mass edit cells in column Provider Address (multiple)
- Text transform on cells in column Provider Address using expression grel:value.replace(".","")
- Text transform on cells in column Provider Address using expression grel:value.replace("north","N")
- Text transform on cells in column Provider Address using expression grel:value.replace("North","N")
- Text transform on cells in column Provider Address using expression grel:value.replace("south","S")
- Text transform on cells in column Provider Address using expression grel:value.replace("South","S")
- Text transform on cells in column Provider Address using expression grel:value.replace("West","W")
- Text transform on cells in column Provider Name using expression grel:value.replace("west","W")
- Text transform on cells in column Provider Address using expression grel:value.replace("east","E")
- Text transform on cells in column Provider Address using expression grel:value.replace("East","E")
- Text transform on cells in column Provider Address using expression grel:value.replace("Road","Rd")
- Mass edit cells in column City
- Edit single cell on row 548, column Zip
- Text transform on cells in column Phone using expression null
- Mass edit cells in column Hours (multiple)
- Text transform on cells in column Hours using expression grel:value.replace("¬","")
- Text transform on cells in column Hours using expression grel:value.replace("a.m.","am").replace("p.m.","pm")
- Text transform on cells in column Service Description using expression grel:value.replace("¬","")
- Text transform on cells in column Service Description using expression grel:value.replace("<a href=","").replace("</a>","")
- Text transform on cells in column Service Description using expression grel:value.replace(">","")
- Text transform on cells in column Hours using expression grel:value.replace("<a href=","").replace("</a>","").replace(">","")
- Text transform on cells in column Restrictions using expression grel:value.replace("<a href=","").replace("</a>","").replace(">","")
- Text transform on cells in column Restrictions using expression grel:value.replace("¬","")
- Mass edit cells in column Restrictions (multiple)
- Mass edit cells in column Minimum Volume
- Text transform on cells in column Minimum Volume using expression grel:value.replace(".","")
- Text transform on cells in column Minimum Volume using expression grel:value.replace("pound","lb").replace("pounds","lbs")
- Mass edit cells in column Minimum Volume (multiple)
- Mass edit cells in column Maximum Volume (multiple)
- Mass edit cells in column Fee (multiple)
- Text transform on cells in column Fee using expression grel:value.replace("<a href=","").replace("</a>","").replace(">","")

Split Property Type column into two Boolean columns to avoid multiple values in cells
- Move column Property Type to position 14
- Create column Business Property Type at index 15 based on column Property Type using expression grel:value
- Rename column Property Type to Serves Residential
- Rename column Business Property Type to Serves Business
- Text transform on cells in column Serves Residential using expression grel:value.replace("Business, Residents","TRUE").replace("Residents","TRUE")
- Text transform on cells in column Serves Residential using expression grel:value.replace("Business","FALSE")
- Text transform on cells in column Serves Business using expression grel:value.replace("Business, Residents","TRUE").replace("Business","TRUE")
- Text transform on cells in column Serves Business using expression grel:value.replace("Residents","FALSE")

Remove duplicative address columns
- Remove column Location
- Remove column Mapping Location
- Remove column GeoLocation

Check for and trim whitespaces from text values by column
- Text transform on cells in column Provider Name using expression value.trim()
- Text transform on cells in column Provider Address using expression value.trim()
- Text transform on cells in column City using expression value.trim()
- Text transform on cells in column Phone using expression value.trim()
- Text transform on cells in column Hours using expression value.trim()
- Text transform on cells in column Material Handled using expression value.trim()
- Text transform on cells in column Service Description using expression value.trim()
- Text transform on cells in column Restrictions using expression value.trim()
- Text transform on cells in column Minimum Volume using expression value.trim()
- Text transform on cells in column Maximum Volume using expression value.toString()
- Text transform on cells in column Maximum Volume using expression value.trim()
- Text transform on cells in column Fee using expression value.trim()
- Text transform on cells in column Serves Residential using expression value.trim()
- Text transform on cells in column Serves Business using expression value.trim()
- Text transform on cells in column Pickup Allowed using expression value.trim()
- Text transform on cells in column Dropoff Allowed using expression value.trim()
- Text transform on cells in column Mail In Allowed using expression value.trim()
- Text transform on cells in column TIBN using expression value.trim()
- Text transform on cells in column eCycle using expression value.trim()
- Text transform on cells in column Provider URL using expression value.trim()
	
#### JSON Cleaning Script:

```
[
  {
    "op": "core/column-rename",
    "description": "Rename column ÔªøProviderID to ProviderID",
    "oldColumnName": "ÔªøProviderID",
    "newColumnName": "ProviderID"
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Location",
    "columnName": "Location"
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Name",
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
                "v": "Call2Recycle¬Æ (multiple locations)",
                "l": "Call2Recycle¬Æ (multiple locations)"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Name",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Name"
        }
      ]
    },
    "columnName": "Provider Name",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call2Recycle¬Æ (multiple locations)"
        ],
        "to": "Call2Recycle (multiple locations)"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "11110 Mukilteo Speedway Ste. 202",
                "l": "11110 Mukilteo Speedway Ste. 202"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "11110 Mukilteo Speedway Ste. 202"
        ],
        "to": "11110 Mukilteo Spdwy, Ste 202"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "Call for location",
                "l": "Call for location"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for location"
        ],
        "to": "Call for locations"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "Mail-in program only",
                "l": "Mail-in program only"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mail-in program only"
        ],
        "to": "Mail-in service only"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "See Web site for locations",
                "l": "See Web site for locations"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "See Web site for locations"
        ],
        "to": "See website for locations"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "See call2recycle.org for drop-off locations",
                "l": "See call2recycle.org for drop-off locations"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "See call2recycle.org for drop-off locations"
        ],
        "to": "See website for locations"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "9607 Aurora Ave. North - scrap yard",
                "l": "9607 Aurora Ave. North - scrap yard"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "9607 Aurora Ave. North - scrap yard"
        ],
        "to": "9607 Aurora Ave. North"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\".\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\".\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"north\",\"N\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"north\",\"N\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"North\",\"N\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"North\",\"N\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"south\",\"S\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"south\",\"S\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"South\",\"S\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"South\",\"S\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"West\",\"W\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"West\",\"W\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Name using expression grel:value.replace(\"west\",\"W\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Name",
    "expression": "grel:value.replace(\"west\",\"W\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"east\",\"E\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"east\",\"E\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"East\",\"E\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"East\",\"E\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Provider Address",
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
                "v": "15835 Wminster Way N",
                "l": "15835 Wminster Way N"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Provider Address",
          "omitBlank": false,
          "type": "list",
          "columnName": "Provider Address"
        }
      ]
    },
    "columnName": "Provider Address",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "15835 Wminster Way N"
        ],
        "to": "15835 Westminster Way N"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression grel:value.replace(\"Road\",\"Rd\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "grel:value.replace(\"Road\",\"Rd\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column City",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "City",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "LGrange",
          "LaGrange"
        ],
        "to": "LaGrange"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Phone using expression null",
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
                "v": "()",
                "l": "()"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Phone",
          "omitBlank": false,
          "type": "list",
          "columnName": "Phone"
        }
      ]
    },
    "columnName": "Phone",
    "expression": "null",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "varies by drop-off location",
                "l": "varies by drop-off location"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "varies by drop-off location"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Varies by location",
                "l": "Varies by location"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Varies by location"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Varies by location, see website",
                "l": "Varies by location, see website"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Varies by location, see website"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Varies with season - 7 days a week",
                "l": "Varies with season - 7 days a week"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Varies with season - 7 days a week"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "varies, check website",
                "l": "varies, check website"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "varies, check website"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "<strong>Station hours</strong> <span style=\"color:#F00\">(different from recycle area hours listed below)</span>:  Mon-Thurs:  24 hours a day  Fri: 12 a.m. ¬ñ 11:30 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.  <strong>Recycle area hours</strong> <span style=\"color:#F00\">(different from station hours listed above)</span>:  Mon-Fri 6:00 a.m. ¬ñ 8:00 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.    The following materials are accepted <strong>only</strong> during <em>Recycle area hours</em>:  <ul><li><a href=\"/solidwaste/facilities/documents/commingled-recycling-guide-facilities.pdf\" title=\"guide to commingled recyclable materials (PDF)\">Commingled recyclable materials</a></li><li>Appliances</li><li>Mercury-containing light bulbs and tubes</li><li>Textiles</li><li>Yard waste</li></ul><p>For more information, see <a href=\"#services\" title=\"jump to Recycling services\">Recycling services</a>.</p><p>This facility is closed on Thanksgiving, Christmas, and New Year¬ís Day",
                "l": "<strong>Station hours</strong> <span style=\"color:#F00\">(different from recycle area hours listed below)</span>:  Mon-Thurs:  24 hours a day  Fri: 12 a.m. ¬ñ 11:30 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.  <strong>Recycle area hours</strong> <span style=\"color:#F00\">(different from station hours listed above)</span>:  Mon-Fri 6:00 a.m. ¬ñ 8:00 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.    The following materials are accepted <strong>only</strong> during <em>Recycle area hours</em>:  <ul><li><a href=\"/solidwaste/facilities/documents/commingled-recycling-guide-facilities.pdf\" title=\"guide to commingled recyclable materials (PDF)\">Commingled recyclable materials</a></li><li>Appliances</li><li>Mercury-containing light bulbs and tubes</li><li>Textiles</li><li>Yard waste</li></ul><p>For more information, see <a href=\"#services\" title=\"jump to Recycling services\">Recycling services</a>.</p><p>This facility is closed on Thanksgiving, Christmas, and New Year¬ís Day"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "<strong>Station hours</strong> <span style=\"color:#F00\">(different from recycle area hours listed below)</span>:  Mon-Thurs:  24 hours a day  Fri: 12 a.m. ¬ñ 11:30 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.  <strong>Recycle area hours</strong> <span style=\"color:#F00\">(different from station hours listed above)</span>:  Mon-Fri 6:00 a.m. ¬ñ 8:00 p.m.  Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m.    The following materials are accepted <strong>only</strong> during <em>Recycle area hours</em>:  <ul><li><a href=\"/solidwaste/facilities/documents/commingled-recycling-guide-facilities.pdf\" title=\"guide to commingled recyclable materials (PDF)\">Commingled recyclable materials</a></li><li>Appliances</li><li>Mercury-containing light bulbs and tubes</li><li>Textiles</li><li>Yard waste</li></ul><p>For more information, see <a href=\"#services\" title=\"jump to Recycling services\">Recycling services</a>.</p><p>This facility is closed on Thanksgiving, Christmas, and New Year¬ís Day"
        ],
        "to": "Mon-Fri 6:00 a.m. ¬ñ 8:00 p.m. Sat and Sun: 8:30 a.m. ¬ñ 5:30 p.m."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "24 hrs per day, 365 days per year",
                "l": "24 hrs per day, 365 days per year"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "24 hrs per day, 365 days per year"
        ],
        "to": "24 hrs"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "24/7 phone service",
                "l": "24/7 phone service"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "24/7 phone service"
        ],
        "to": "24-hour phone service"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "7am - 7pm Mon-Fri  Special hours available on weekends",
                "l": "7am - 7pm Mon-Fri  Special hours available on weekends"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "7am - 7pm Mon-Fri  Special hours available on weekends"
        ],
        "to": "7am - 7pm Mon-Fri"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "varies by location",
                "l": "varies by location"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "varies by location"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "All stores open 7 days a week, closed Thanksgiving and Christmas.  Hours vary by location ¬ñ see website.",
                "l": "All stores open 7 days a week, closed Thanksgiving and Christmas.  Hours vary by location ¬ñ see website."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "All stores open 7 days a week, closed Thanksgiving and Christmas.  Hours vary by location ¬ñ see website."
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Always Open",
                "l": "Always Open"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Always Open"
        ],
        "to": "24 hours"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "By appointment only.",
                "l": "By appointment only."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "By appointment only."
        ],
        "to": "By appointment"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Daily 10am - 6pm",
                "l": "Daily 10am - 6pm"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Daily 10am - 6pm"
        ],
        "to": "10am - 6pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "daily, by appointment",
                "l": "daily, by appointment"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "daily, by appointment"
        ],
        "to": "By appointment"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Daily: 9am - 6pm  ",
                "l": "Daily: 9am - 6pm  "
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Daily: 9am - 6pm  "
        ],
        "to": "9am - 6pm  "
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Drop-off: 1st and 3rd Tuesday of every month from 9am - 2pm. Appointment suggested.",
                "l": "Drop-off: 1st and 3rd Tuesday of every month from 9am - 2pm. Appointment suggested."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Drop-off: 1st and 3rd Tuesday of every month from 9am - 2pm. Appointment suggested."
        ],
        "to": "Drop-off 1st and 3rd Tuesday of every month from 9am - 2pm. Appointment suggested."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Drop-off: 2nd Thursday of every month from 9am - 2pm.  Appointment suggested.",
                "l": "Drop-off: 2nd Thursday of every month from 9am - 2pm.  Appointment suggested."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Drop-off: 2nd Thursday of every month from 9am - 2pm.  Appointment suggested."
        ],
        "to": "Drop-off 2nd Thursday of every month from 9am - 2pm. Appointment suggested."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Flexible",
                "l": "Flexible"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Flexible"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Hours vary by location",
                "l": "Hours vary by location"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Hours vary by location"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Hours vary by location.",
                "l": "Hours vary by location."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Hours vary by location."
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Always available on-line.",
                "l": "Always available on-line."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Always available on-line."
        ],
        "to": "24-hour website"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Mail back program.",
                "l": "Mail back program."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mail back program."
        ],
        "to": "Mail-in program"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Mail-in",
                "l": "Mail-in"
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mail-in"
        ],
        "to": "Mail-in program"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
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
                "v": "Mail-in program.",
                "l": "Mail-in program."
              }
            }
          ],
          "selectError": false,
          "invert": false,
          "name": "Hours",
          "omitBlank": false,
          "type": "list",
          "columnName": "Hours"
        }
      ]
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mail-in program."
        ],
        "to": "Mail-in program"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon - Fri 9am-5pm PST"
        ],
        "to": "Mon - Fri 9am-5pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon - Fri: 7am - 7pm EST  "
        ],
        "to": "Mon - Fri: 7am - 7pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon - Fri: 9am - 3pm walk-in service"
        ],
        "to": "Mon - Fri: 9am - 3pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Fri: 8am - 5pm Eastern"
        ],
        "to": "Mon-Fri: 8am - 5pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Fri: 8am - 5pm EST"
        ],
        "to": "Mon-Fri: 8am - 5pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Fri: 8am -5pm PST"
        ],
        "to": "Mon-Fri: 8am-5pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Fri: 9am - 8pm   Sat: 10am - 6pm   Sun: 11am - 6pm  206-246-7389"
        ],
        "to": "Mon-Fri: 9am - 8pm   Sat: 10am - 6pm   Sun: 11am - 6pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Sat hours vary by season"
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon-Sat: 7:30am - 4pm at the A.R.C."
        ],
        "to": "Mon-Sat: 7:30am - 4pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon, Tues, Fri, Sat & Sun: 9 a.m. ¬ñ 5 p.m. (<span class=\"colorred\">closed Wed & Thu</span>)"
        ],
        "to": "Mon, Tues, Fri, Sat & Sun: 9 a.m. ¬ñ 5 p.m"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon, Wed, Fri, Sat & Sun: 9 a.m. ¬ñ 5 p.m. (<span class=\"colorred\">closed Tue & Thu</span>)"
        ],
        "to": "Mon, Wed, Fri, Sat & Sun: 9 a.m. ¬ñ 5 p.m"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon: 10am - 6pm  Tues-Fri: 10am - 8pm  Sat: 10am -7pm  Sun: Closed"
        ],
        "to": "Mon: 10am - 6pm  Tues-Fri: 10am - 8pm  Sat: 10am -7pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Mon: 8am - 6pm  Tues-Sat: 8am - 8pm  Closed Sunday"
        ],
        "to": "Mon: 8am - 6pm  Tues-Sat: 8am - 8pm"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Online 24/7"
        ],
        "to": "24-hour website"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Open 7 days a week. Call for hours."
        ],
        "to": "Varies"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Phones operated 24/7"
        ],
        "to": "24-hour phone service"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Please call to make arrangements."
        ],
        "to": "By appointment"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Recycling Bin available 24 hours"
        ],
        "to": "24-hour recycling bin"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Hours",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "(Mar-Oct) Mon-Fri: 7am - 5pm and Sat: 8am - 4pm;  (Nov-Feb) Mon-Fri: 7am - 4pm."
        ],
        "to": "Mar-Oct Mon-Fri: 7am - 5pm and Sat: 8am - 4pm;  Nov-Feb Mon-Fri: 7am - 4pm."
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Hours using expression grel:value.replace(\"¬\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "grel:value.replace(\"¬\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Hours using expression grel:value.replace(\"a.m.\",\"am\").replace(\"p.m.\",\"pm\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "grel:value.replace(\"a.m.\",\"am\").replace(\"p.m.\",\"pm\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Service Description using expression grel:value.replace(\"¬\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Service Description",
    "expression": "grel:value.replace(\"¬\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Service Description using expression grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Service Description",
    "expression": "grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Service Description using expression grel:value.replace(\">\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Service Description",
    "expression": "grel:value.replace(\">\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Hours using expression grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Restrictions using expression grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Restrictions using expression grel:value.replace(\"¬\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "grel:value.replace(\"¬\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "-None-"
        ],
        "to": "None"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "*No asbestos containing material."
        ],
        "to": "No asbestos containing material."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "<span class=\"colorred\"Maximum 30 gallons of gasoline</span   Business waste amounts and types are restricted. See the \"http://www.lhwmp.org/home/BHW/sqg.aspx\"  Local Hazardous Waste Management Program Business page for complete details.     For information on items that are not acceptable, please visit the http://www.lhwmp.org/home/HHW/whattobring.aspxLocal Hazardous Waste Management Program site and scroll down to <strongWhat Not To Bring.</strong        For Everyone's Safety:   Store products away from the passenger compartment of your vehicle and keep them separate from items you wish to retain "
        ],
        "to": "Maximum 30 gallons of gasoline. Business waste amounts and types are restricted. See the \"http://www.lhwmp.org/home/BHW/sqg.aspx\"  Local Hazardous Waste Management Program Business page for complete details. For information on items that are not acceptable, please visit the http://www.lhwmp.org/home/HHW/whattobring.aspx Local Hazardous Waste Management Program site and scroll down to What Not To Bring. For Everyone's Safety: Store products away from the passenger compartment of your vehicle and keep them separate from items you wish to retain "
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Working equipment only.  Call first."
        ],
        "to": "Working equipment only"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Working equipment only.  Please, call first."
        ],
        "to": "Working equipment only"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Working equipment only. Call first."
        ],
        "to": "Working equipment only"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "1 Cubic yard"
        ],
        "to": "1 cubic yard"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "2 ton minimum"
        ],
        "to": "2 ton"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "5 barrel min."
        ],
        "to": "5 barrels"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "n/a"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "N/A"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "no minimum"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No Minimum",
          "No minimum",
          "NO MINIMUM"
        ],
        "to": "No Minimum"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for minimums on specific glass types",
          "Call for minimums on specific glass types."
        ],
        "to": "Call for minimums on specific glass types"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "500 pounds",
          "500 pounds."
        ],
        "to": "500 pounds"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bags minimum for free pick-up",
          "Three bags minimum for free pick-up."
        ],
        "to": "Three bags minimum for free pick-up"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "None",
          "none"
        ],
        "to": "None"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for quote on quantity limitations",
          "Call for quote on quantity limitations."
        ],
        "to": "Call for quote on quantity limitations"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No limit",
          "No Limit"
        ],
        "to": "No limit"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "3 bags minimum for pickup",
          "3 bags minimum for free pickup"
        ],
        "to": "3 bags minimum for pickup"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Minimum Volume using expression grel:value.replace(\".\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "grel:value.replace(\".\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Minimum Volume using expression grel:value.replace(\"pound\",\"lb\").replace(\"pounds\",\"lbs\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "grel:value.replace(\"pound\",\"lb\").replace(\"pounds\",\"lbs\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Any"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bags minimum"
        ],
        "to": "Three bag minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bags minimum for free pick-ups"
        ],
        "to": "Three bags minimum for free pick-up"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "17 cubic yd Container"
        ],
        "to": "17 cubic yard container"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for current limitations on your material"
        ],
        "to": "Call for minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for details"
        ],
        "to": "Call for minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for quote on quantity limitations"
        ],
        "to": "Call for minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Contact for information"
        ],
        "to": "Call for minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for minimums on specific glass types"
        ],
        "to": "Call for minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No limit"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bags minimum for free pick-up"
        ],
        "to": "Three bag minimum for free pick-up"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "THREE BAGS MINIMUN FOR FREE PICK-UP"
        ],
        "to": "Three bag minimum for free pick-up"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No minimum donations"
        ],
        "to": "No minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No Minimum"
        ],
        "to": "No minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bag minimum"
        ],
        "to": "3 bag minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three bag minimum for free pick-up"
        ],
        "to": "3 bag minimum for free pick-up"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three box minimum"
        ],
        "to": "3 box minimum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Minimum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "3 bags minimum for pickup"
        ],
        "to": "3 bag minimum for pickup"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "no maximum",
          "No maximum",
          "No Maximum",
          "NO MAXIMUM"
        ],
        "to": "No maximum"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "None",
          "none",
          "-None-"
        ],
        "to": ""
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No limit.",
          "No Limit",
          "No limit"
        ],
        "to": ""
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "3 units per load",
          "3 units per load."
        ],
        "to": "3 units per load"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Ten lamps per customer.",
          "Ten lamps per customer"
        ],
        "to": "Ten lamps"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "unlimited",
          "Unlimited"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for quote on quantity limitations",
          "Call for quote on quantity limitations."
        ],
        "to": "Call for maximum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for maximum",
          "Call for maximum volumes"
        ],
        "to": "Call for maximum"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "larger donations accepted upon prior arrangements.",
          "larger donations accepted with prior arrangements."
        ],
        "to": "larger donations accepted upon prior arrangements."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No maximum",
          "No amximum"
        ],
        "to": "No maximum"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "N/A",
          "No"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "10 tons ok"
        ],
        "to": "10 tons"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "8,000 lb load limit per haul."
        ],
        "to": "8,000 lbs per load hauled"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "8k load limit on this type of material"
        ],
        "to": "8,000 lbs per load hauled"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Any"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "As space is available. Call first."
        ],
        "to": "As space allows"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for current limitations on your material."
        ],
        "to": "Call for maximum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Limit 10 bulbs and tubes"
        ],
        "to": "10 bulbs and tubes"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Limit 30 gallons total liquid hazardous waste per customer per day; no containers over 5 gallons."
        ],
        "to": "30 gallons total liquid hazardous waste per customer per day; no containers over 5 gallons."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Limit 50 gallons total liquid hazardous waste per customer per day; no containers over 5 gallons."
        ],
        "to": "50 gallons total liquid hazardous waste per customer per day; no containers over 5 gallons."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Limit 6 items per customer per day"
        ],
        "to": "6 items per customer per day"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Limit ten"
        ],
        "to": "10"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No Maximum Volume"
        ],
        "to": "No maximum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Ten lamps"
        ],
        "to": "10 lamps"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Three cubic yards or one ton."
        ],
        "to": "3 cubic yards or one ton."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "-All amounts accepted-"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "(No Maximum) Large loads hauled in 40yd Containers"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "1 gal"
        ],
        "to": "1 gallon"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "100 one gallon containers, call with questions"
        ],
        "to": "100 1-gallon containers"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "55 gallon barrel"
        ],
        "to": "55-gallon barrel"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Load limit of 8,000 pounds."
        ],
        "to": "8,000 lbs per load hauled"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Contact for information"
        ],
        "to": "Call for maximum"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Five items per person, per day"
        ],
        "to": "Five items per person per day"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Five items per person per day"
        ],
        "to": "5 items per person per day"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Maximum of five vehicle batteries"
        ],
        "to": "5 vehicle batteries"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Maximum Weight ( 24000 lbs/12.0 tons) per container load"
        ],
        "to": "24000 lbs or 12.0 tons per container load"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "no limits on Colume"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No maximum"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Maximum Volume",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No maximum donations"
        ],
        "to": ""
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Service Description",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Service Description",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "http://www.acemetalco.com/Services.htmlhttp://www.acemetalco.com/Services.html"
        ],
        "to": "http://www.acemetalco.com/Services.html"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Restrictions",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "http://www.acemetalco.com/Services.htmlhttp://www.acemetalco.com/Services.html"
        ],
        "to": "http://www.acemetalco.com/Services.html"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Free",
          "Free.",
          "FREE",
          "Free.  ",
          "Free.   ",
          "free  "
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.     <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  ",
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.    <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  ",
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.  <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  "
        ],
        "to": "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.     <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  "
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No charge.",
          "no charge",
          "No Charge."
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.",
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.   ",
          "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.  "
        ],
        "to": "We offer pickups for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us about $84. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups.",
          "FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups.     ",
          "FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups.  "
        ],
        "to": "FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.    <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  ",
          "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.  <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  "
        ],
        "to": "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.    <a href=http://www.svdpseattle.org> http://www.svdpseattle.org</a>  "
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We are a no cost recycling service. Please see us at www.saspcrecycling.com",
          "We are a no cost recycling service. Please see us at www.saspcrecycling.com  "
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Please Call -pricing is based on your specific job-site location, access issues and volume of material.",
          "Please call - pricing is based on your specific job-site location, access issues, and volume of material."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No charge for drop off.",
          "No charge for drop off"
        ],
        "to": "Free drop off"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "$.48 per pound, $30.00 minimum charge",
          "$.48 per pound, $30.00 minimum charge  "
        ],
        "to": "$.48 per pound, $30.00 minimum charge"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for pricing.",
          "Call for pricing"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for prices.",
          "Call for prices"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "For commercial rates please call 206-332-7700. For current residential rates select your city or service area on our <a href=http://www.rabanco.com>Web site</a> or call us at 206-332-7700.",
          "For commercial rates please call 206-332-7700. For current residential rates select your city or service area on our <a href=http://www.rabanco.com>Web site</a> or call us at 206-332-7700.  "
        ],
        "to": "For commercial rates please call 206-332-7700. For current residential rates select your city or service area on our <a href=http://www.rabanco.com>Web site</a> or call us at 206-332-7700."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No fees.",
          "No Fees"
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We prefer donors to drop off donations at any of our store locations: Aurora, Burien, Kenmore, Kent, and Renton. Trucks are used mostly for pick ups from business, larger items, elderly, or disabled donors.",
          "We prefer donors to drop off donations at any of our store locations: Aurora, Burien, Kenmore, Kent, and Renton. Trucks are used mostly for pick ups from business, larger items, elderly, or disabled donors.  "
        ],
        "to": "We prefer donors to drop off donations at any of our store locations: Aurora, Burien, Kenmore, Kent, and Renton. Trucks are used mostly for pick ups from business, larger items, elderly, or disabled donors."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for rates.",
          "Call for rates"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Free to drop off.  $25 flat-rate pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County.",
          "Free to drop off. $25 flat-rate pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County."
        ],
        "to": "Free drop off.  $25 flat-rate pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "See GreenDisk Web site for fee information.",
          "See GreenDisk Web site for fee information.     "
        ],
        "to": "See GreenDisk Web site for fee information."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for information.",
          "Call for information"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.",
          "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible.  "
        ],
        "to": "We offer pickups (please call or schedule online) for gently-used furniture, as well as for large donations of clothing and household goods. Every donation pickup we do costs us. To ensure that we are maximizing our limited funds to help our neighbors in need, if you are able, we hope that you can drop off your donations at a Donation Center near you. Your donations to St. Vincent de Paul are tax-deductible."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Free recycling.  Pickup services available for businesses. Please visit <a href=http://www.AmericanEcycling.com>http://www.AmericanEcycling.com</a> for more information",
          "Free recycling.  Pickup services available for businesses. Please visit <a href=http://www.AmericanEcycling.com>http://www.AmericanEcycling.com</a> for more information."
        ],
        "to": "Free"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call",
          "Call."
        ],
        "to": "Call"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No charge.  May pay for material.  Call for details.",
          "No charge. May pay for material. Call for details."
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We provide free recycling to everyone !",
          "We provide free recycling to everyone."
        ],
        "to": "Free"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Fees for all items, call for more information.",
          "Fees for all items. Call for more information."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call (800) 322-8284  ",
          "Call (800) 322-8284."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "$1.50 per pound",
          "$1.50 per pound."
        ],
        "to": "$1.50 per pound"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Accepts materials at no cost. Does not pay for materials.",
          "Accepts materials at no cost.  Does not pay for materials."
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Donation only.",
          "Donation only"
        ],
        "to": "Donation only"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "None",
          "None."
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for more information.",
          "Call for more information"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "There is no fee to consumers for the covered LG-brand products; other brands will be accepted, but a fee may be charged by Waste Management for non-LG brands.   ",
          "There is no fee to consumers for the covered LG-brand products; other brands will be accepted, but a fee may be charged by Waste Management for non-LG brands."
        ],
        "to": "Free to consumers for the covered LG-brand products; other brands will be accepted, but a fee may be charged by Waste Management for non-LG brands.   "
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "$75 per ton with a minimum fee of $12 per entry.  The entry fee covers the first 320 pounds.",
          "$75 per ton with a minimum fee of $12 per entry. The entry fee covers the first 320 pounds."
        ],
        "to": "$75 per ton with a minimum fee of $12 per entry.  The entry fee covers the first 320 pounds."
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Volume Load <a href=http://buzz-bee.net/pricing.html>Rates</a>:  1/2 Cubic Yard............................$60.00    1 Cubic Yard..............................$120.00    1.5 Cubic Yards...........................$180.00    2 Cubic Yards.............................$240.00    2.5 Cubic Yards...........................$300.00    3 Cubic Yards.............................$360.00    3.5 Cubic Yards...........................$420.00    4 Cubic Yards (Full Load).................$480.00",
          "Volume Load <a href=http://buzz-bee.net/pricing.html>Rates</a>:  1/2 Cubic Yard............................$60.00    1 Cubic Yard..............................$120.00    1.5 Cubic Yards...........................$180.00    2 Cubic Yards.............................$240.00    2.5 Cubic Yards...........................$300.00    3 Cubic Yards.............................$360.00    3.5 Cubic Yards...........................$420.00    4 Cubic Yards (Full Load).................$480.00  "
        ],
        "to": "Volume Load <a href=http://buzz-bee.net/pricing.html>Rates</a>:  1/2 Cubic Yard............................$60.00    1 Cubic Yard..............................$120.00    1.5 Cubic Yards...........................$180.00    2 Cubic Yards.............................$240.00    2.5 Cubic Yards...........................$300.00    3 Cubic Yards.............................$360.00    3.5 Cubic Yards...........................$420.00    4 Cubic Yards (Full Load).................$480.00"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Visit website for updated rates <a href=http://www.pcrecycle.net/items-accept-pricing/>http://www.pcrecycle.net/items-accept-pricing/</a>",
          "Visit website for updated rates <a href=http://www.pcrecycle.net/items-accept-pricing/>http://www.pcrecycle.net/items-accept-pricing/</a>  "
        ],
        "to": "Visit website for updated rates <a href=http://www.pcrecycle.net/items-accept-pricing/>http://www.pcrecycle.net/items-accept-pricing/</a>"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Quote given at time of service.",
          "Quote given at time of service"
        ],
        "to": "Quote given at time of service."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call to confirm.",
          "Call to confirm"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for details.",
          "Call for details"
        ],
        "to": "Call"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Pays for cans",
          "Pays for cans."
        ],
        "to": "Pays for cans"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Monitors=FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups.",
          "Monitors=FREE for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups.      "
        ],
        "to": "Monitors free for E-Cycle Washington eligible groups including residents, small businesses (< 50 employees corporate-wide), school districts (no colleges or universities), charities and non-profit groups."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "No charge for CFLs  $0.25 per foot for fluorescent tubes.  $1.00 each for U-tubes and circular tubes.  $1.50 for High Pressure Sodium, Metal Halide and Mercury Vapor.  ",
          "No charge for CFLs.  $0.25 per foot for fluorescent tubes.  $1.00 each for U-tubes and circular tubes.  $1.50 for High Pressure Sodium, Metal Halide and Mercury Vapor."
        ],
        "to": "Free CFLs  $0.25 per foot for fluorescent tubes.  $1.00 each for U-tubes and circular tubes.  $1.50 for High Pressure Sodium, Metal Halide and Mercury Vapor.  "
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Free to drop off.  $25.00 flat-rate pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County.",
          "Free to drop off.  $25.00 flat-rate pickup fee for electronics and appliances for Seattle, the Eastside, and Snohomish County.",
          "Free to drop off.  $25.00 flat-fee pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County.    ",
          "Free to drop off.  $25.00 flat-rate pick up service for electronics and appliances for Seattle, the Eastside, and Snohomish County.",
          "Free to drop off.  $25.00 flat-rate pickup fee for elctronics and appliances for Seattle, the Eastside, and Snohomish County.    ",
          "Free to drop off.  $25.00 flat-rate pickup fee for eletronics and appliances for Seattle, the Eastside, and Snohomish County.",
          "Free to drop off.  $25.00 flat-rate pickup for electronics and appliances for Seattle, the Eastside, and Snohomish County."
        ],
        "to": "Free to drop off.  $25.00 flat-rate pickup service for electronics and appliances for Seattle, the Eastside, and Snohomish County."
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for pricing, email us at <a href=mailto:sales@pacifictopsoils.com>sales@pacifictopsoils.com</a>, or see our website at <a href=http://www.pacifictopsoils.com>www.pacifictopsoils.com</a> for more information.",
          "Call for price information.",
          "Call for pricing information.",
          "Call for pricing based on your specific location, job-site access, and volume of material.",
          "Call for pricing--will fax information.",
          "Call for pricing. $30 minimum charge."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Please Call - Pricing based on your specific job-site location and total volume of material you will be removing.",
          "Please Call - Pricing is based on your specific job-site location and the total volume of material to be removed",
          "Please Call - pricing based on jobsite location and total volume of materials to be hauled.",
          "Please Call -pricing is based on your specific job-site location, access and volume of material.",
          "Please call - Pricing is based on your specific job-site and the total volume of material to be hauled.",
          "Please call - Pricing is based on your specific job-site location and total volume of material to be hauled away."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call (206) 767-3835 for information",
          "Call for information regarding prices.",
          "Call for information. Flat rate for drop box and hauling up to 6 tons.",
          "Call for information. Hauling fees may apply.",
          "Call for information. No cash paid. No on-site checks paid.  Account set-up required for payment.  Minimum weights for payment required."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call",
          "Call 1(800)322-8284.",
          "Call 800-322-8284"
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Please call 206-772-4745 for a quote.",
          "Please call for quote before delivering."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Call for prices and restrictions.",
          "Call for prices and to confirm."
        ],
        "to": "Call"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "We are a no cost recycle service. For details, see http://www.saspcrecycling.com",
          "We are a no cost recycling service. Please visit our website.  "
        ],
        "to": "Free"
      },
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Price structured according to sizes--call for prices.",
          "Price structured according to amounts--call for prices."
        ],
        "to": "Call"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "$0.00 "
        ],
        "to": "Free"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "Recycling fee. Call for details."
        ],
        "to": "Call"
      }
    ]
  },
  {
    "op": "core/mass-edit",
    "description": "Mass edit cells in column Fee",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value",
    "edits": [
      {
        "fromBlank": false,
        "fromError": false,
        "from": [
          "There is no fee to have your unwanted vehicle picked up."
        ],
        "to": "Free"
      }
    ]
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Fee using expression grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "grel:value.replace(\"<a href=\",\"\").replace(\"</a>\",\"\").replace(\">\",\"\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-move",
    "description": "Move column Property Type to position 14",
    "columnName": "Property Type",
    "index": 14
  },
  {
    "op": "core/column-addition",
    "description": "Create column Business Property Type at index 15 based on column Property Type using expression grel:value",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "newColumnName": "Business Property Type",
    "columnInsertIndex": 15,
    "baseColumnName": "Property Type",
    "expression": "grel:value",
    "onError": "set-to-blank"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Property Type to Serves Residential",
    "oldColumnName": "Property Type",
    "newColumnName": "Serves Residential"
  },
  {
    "op": "core/column-rename",
    "description": "Rename column Business Property Type to Serves Business",
    "oldColumnName": "Business Property Type",
    "newColumnName": "Serves Business"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Residential using expression grel:value.replace(\"Business, Residents\",\"TRUE\").replace(\"Residents\",\"TRUE\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Residential",
    "expression": "grel:value.replace(\"Business, Residents\",\"TRUE\").replace(\"Residents\",\"TRUE\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Residential using expression grel:value.replace(\"Business\",\"FALSE\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Residential",
    "expression": "grel:value.replace(\"Business\",\"FALSE\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Business using expression grel:value.replace(\"Business, Residents\",\"TRUE\").replace(\"Business\",\"TRUE\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Business",
    "expression": "grel:value.replace(\"Business, Residents\",\"TRUE\").replace(\"Business\",\"TRUE\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Business using expression grel:value.replace(\"Residents\",\"FALSE\")",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Business",
    "expression": "grel:value.replace(\"Residents\",\"FALSE\")",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/column-removal",
    "description": "Remove column Mapping Location",
    "columnName": "Mapping Location"
  },
  {
    "op": "core/column-removal",
    "description": "Remove column GeoLocation",
    "columnName": "GeoLocation"
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Name using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Name",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider Address using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider Address",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column City using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "City",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Phone using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Phone",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Hours using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Hours",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Material Handled using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Material Handled",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Service Description using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Service Description",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Restrictions using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Restrictions",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Minimum Volume using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Minimum Volume",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Maximum Volume using expression value.toString()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value.toString()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Maximum Volume using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Maximum Volume",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Fee using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Fee",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Residential using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Residential",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Serves Business using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Serves Business",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Pickup Allowed using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Pickup Allowed",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Dropoff Allowed using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Dropoff Allowed",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Mail In Allowed using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Mail In Allowed",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column TIBN using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "TIBN",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column eCycle using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "eCycle",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  },
  {
    "op": "core/text-transform",
    "description": "Text transform on cells in column Provider URL using expression value.trim()",
    "engineConfig": {
      "mode": "row-based",
      "facets": []
    },
    "columnName": "Provider URL",
    "expression": "value.trim()",
    "onError": "keep-original",
    "repeat": false,
    "repeatCount": 10
  }
]
```
