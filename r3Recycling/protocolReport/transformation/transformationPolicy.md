## R<sup>3</sup> Recycling: Transformation Policy

### Format Conversion

- Where possible without data loss, datasets of the listed types will be converted to the preferred open, machine-readable file formats indicated below, for both storage and distribution to repository users:
  - Tabular:  TSV
  - Text:  Plain text

- Tabular data contained within non-tabular datasets, such as charts or tables embedded in text documents, will be individually extracted and saved in the preferred tabular file format.
  - Open-source tool Tabula will be used to extract and convert tabular data from datasets provided in PDF file formats (Tabula, 2017)
  - R<sup>3</sup> will store and make the dataset available in its original, single-file format and as multiple files containing each subset of tabular data extracted from the original, with files of tabular data named pursuant to the file-naming conventions for derivative files set forth in this policy

- If a dataset cannot be converted to one of the above preferred formats without data loss:
  - If data loss does not impair meaningful reuse of the dataset, the dataset will be stored and made available to users in both its original format and the converted format
    - Example:  If conversion of an XLSX spreadsheet to a TSV format retains the results of dynamic functions as static content but results in loss of the underlying formulas, the dataset will be stored and made available to users in both the original XLSX format and the converted TSV format
  - If data loss impairs meaningful reuse of the dataset, the dataset will be stored and made available only in its original format
    - Example:  If conversion of a PDF-embedded table to a TSV format results in loss of unique symbol images used as cell values, the dataset will be stored and made available to users in only the original PDF format
  - Where the impact of data loss on meaningful reuse of the dataset cannot be assessed, the dataset will be made available only in its original format, but stored in both its original format and the converted format for preservation purposes
- All datasets stored and/or made available in proprietary file formats will be accompanied by an explanatory &#39;ReadMe&#39; file that documents the name, version, and manufacturer of the software used to generate the file, as reported by the data contributor

### Data Cleaning

- All tabular datasets will be subject to cleaning prior to being made available through the repository
- Cleaning will include, as appropriate to each dataset:
  - Removal of special characters
  - Removal of blank rows and columns
  - Standardization of case across column names and values
  - Splitting of multi-value columns
  - Standardization of recurring values within columns through faceting, clustering, and merging, including standardization of missing values as blank cells
  - Removal of commas and other punctuation marks or symbols (i.e. &quot;%&quot;, &quot;$&quot;) from numeric values
  - Trimming of whitespaces from text values
- When necessary, tabular data extracted from non-tabular datasets or spreadsheet files containing extensive formatting will be subject to additional cleaning in order to ensure appropriate conversion, including, as needed:
  - Transformation of subdividing/subheader rows to column values to ensure clarity and machine-readability
  - Removal of footnotes and other explanatory text
- Formatting of certain value types will be standardized across all repository datasets:
  - Dates
    - Dates will be consolidated into a single column, with values taking the format YYYY-MM-DD (omitting the month and/or day elements when unavailable)
  - Addresses
    - Address components will be standardized into separate values across the following columns:
      - Street Address
      - City
      - State
      - Zip Code
  - Geospatial Coordinates
    - Geospatial coordinates will be standardized for display as both:
      - Tuples (&quot;(Latitude, Longitude)&quot;) in a &quot;Location&quot; column
      - Individual coordinates in separate &quot;Latitude&quot; and &quot;Longitude&quot; columns
- Specific cleaning procedures applied to each dataset will be documented
  - R<sup>3</sup> will maintain files reflecting the detailed cleaning history of each published dataset, which will be made available upon request
  - Dataset version metadata will include a summary of data cleaning
- Standardized cleaning templates and scripts will be developed for repeated application to serially-produced, uniformly-formatted datasets relevant to the repository, such as annual or quarterly reports

### File Naming Conventions

- Filenames will not include special characters or spaces
- Multi-word filename elements will utilize camel-casing
  - Example: `RecycleRate` for Recycle Rate
- Filename elements will be separated by underscore characters
  - Example: `RecycleRate_2017` for Recycle Rate 2017 or Recycle Rate, 2017

- Filenames will not exceed 64 characters
- Filenames will be descriptive of file content, including, where applicable and in the specified order, an element that reflects each of the following:
  - 1 - Subject matter of the dataset (mandatory)
  - 2 - Geographic scope of the dataset (mandatory)
    - States will be referenced by official USPS state codes (United States Census Bureau, n.d.)
      - Example: `WA` for Washington
    - Counties will be referenced by the county name in conjunction with the abbreviation &#39;Cty&#39;
      - Example: `PierceCty` for Pierce County
    - Cities will be referenced by city name
      - Example: `Seattle` for Seattle
  - 3 - Temporal scope of the dataset (where applicable)
      - A date element will be included in the filename where the dataset collects observations from a defined time period
      - Dates will be referenced as YYYY-MM-DD (omitting the month and day elements when unavailable)
      - Date ranges will be referenced as YYYY-MM-DD-YYYY-MM-DD (omitting the month and date elements when unavailable)
  
  - Examples:
      - `RecycleReport_Tacoma_2013`
      - `RecyclingOptions_KingCty`
      - `ElectronicPoundsCollected_WA_2017-04`

- Files that contain tabular data extracted from text documents shall be given the name of the &#39;master&#39; file from which the data was extracted with the addition of an element that indicates the type and identifying label of the figure or table from which the tabular data was obtained
  - Example: `ElectronicPoundsCollected_WA_2017-04_Table4`
  - If tables and figures are not labeled in the master file, the additional element should identify the figure type and, following an underscore, the page number on which the figure appears preceded by &#39;p&#39;
    - Example: `RecyclingOptions_KingCty_Table_p7`
  - If multiple unlabeled tables or figures appear on the same page, lowercase letters should be used to differentiate figures, with letters applied in alphabetical order to tables and/or figures beginning from the top left of each relevant page in the master file
    - Example: `RecyclingOptions_KingCty_Table_p7a`
- Files that contain tabular data converted from multi-sheet spreadsheet files shall be given the name of the &#39;master&#39; file from which the data was extracted with the addition of an element that indicates the number of the sheet from which the tabular data was obtained, with numbers applied beginning with the leftmost sheet tab
  - Example: `RecycledMarketReport_Seattle_Sheet2`
- Any explanatory files (i.e. &#39;Read Me&#39; files) shall be named with the filename given to the master file to which they apply, with the addition of a &#39;ReadMe&#39; element to the file name
  - Example:`RecycleReport_Tacoma_2013_ReadMe`

### Versioning

- Changes to datasets, including format conversions and other transformations, will be reflected by updating the `dct:modified` metadata field, which will provide the date on which a dataset was most recently altered
- Version history will be provided for any datasets not made available in their original, unaltered format, with versions identified by the date value in the `dct:modified` field upon completion of changes creating the new version
- Version history documentation will include:
  - Identification of parties other than R<sup>3</sup> initiating the change to the dataset
  - Nature of the changes made, including, but not limited to:
    - Conversion of file formats
      - Example:  File converted from .XLS to .TSV
    - Cleaning or normalization of data, with description of particular transformations applied
      - Example:  White spaces trimmed from values; variable names refined for consistency.
    - Substantive updates or other revisions to data
      - Example:  Variables &#39;Glass (Tons)&#39; and &#39;Metal (Tons)&#39; removed at request of data author.
    - Addition or modification of explanatory documentation accompanying the dataset
      - Example:  .ReadMe file updated to include coding legend.
- Prior versions of datasets will be stored but made available to users only upon request
