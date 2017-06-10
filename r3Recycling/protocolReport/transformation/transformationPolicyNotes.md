## R<sup>3</sup> Recycling: Transformation Policy Notes

### Format Conversion Notes
 
In accordance with the W3C’s *Data on the Web Best Practices Use Cases and Requirements*, datasets will be converted to a set of standardized, open, machine-readable formats (W3C, 2015). Converging on a suite of preferred formats of this type will facilitate accessing, analyzing, and combining recycling-related datasets, as well as provide an opportunity to eliminate proprietary and non-machine-readable formats that may create additional barriers to preservation and reuse (Open Knowledge International, n.d.; Stanford Libraries, n.d.-a).
 
The preferred open formats will be used for storage, as they maximize preservation possibilities, and for distribution to end users, as the interoperability offered by a standardized set of open formats will encourage and facilitate data reuse. Moreover, the selected formats are likely to be accessible to users with varying levels of technical comfort, as they can be easily opened with common software applications. However, R<sup>3</sup> will continue to reevaluate user needs over the life of the repository in order to assess whether making data available in other formats would add value to repository users.
 
Examination of publicly available datasets relevant to R<sup>3</sup> suggests that a number of recycling-related datasets, particularly those provided as heavily-formatted PDF or Excel files,  may experience data loss upon conversion to open, machine-readable file formats, even when subject to data normalization and cleaning procedures. As such, provisions governing how such loss should affect file formatting are included in R<sup>3</sup>’s transformation policy. Although open, machine-readable, standardized formats are strongly preferred, datasets that cannot be converted to these formats in a way that permits meaningful reuse will nevertheless be hosted by R<sup>3</sup> in order to maximize the repository’s domain coverage and fulfill R<sup>3</sup>’s goal of centralizing recycling data access.

### Data Cleaning Notes
 
Cleaning policy and procedures were derived from suggestions for best practices, (School of Data, n.d.; Van Hooland, S., Verbough, R., & De Wilde, M., 2013), through review of the post-file-conversion cleaning needs of the datasets identified for inclusion in the repository, and test-cleaning of five datasets. 
 
In order to assess how variation across datasets may impact cleaning needs, the five test-cleaned datasets included:
- 3 datasets available at source in TSV file format; 1 PDF file from which tabular data were extracted to TSV format; 1 XLSX file converted to TSV format
- 3 datasets published by open data portals; 2 datasets published by government entity websites
- 2 datasets at the municipal level; 1 at the county level; 2 at the state level
 
Cleaning procedures were applied using open-source tool OpenRefine, (OpenRefine, n.d.), which allowed for extraction and subsequent annotation of [cleaning transcripts and code](../../repositoryDatasets/dataCleaningProcessExamples/).
 
As expected, datasets converted to TSV format from another file format often required splitting of columns to properly separate values. However, extraction of tabular data from PDFs using Tabula resulted in data that was generally ‘cleaner’ than data made available in other formats, even data obtained in tabular form from open data portals. By contrast, datasets originally made available in Excel, particularly those with significant appearance-based formatting, resulted in ‘messy’ data upon conversion that called for more extensive transformation.
 
Test-cleaning also revealed that it may prove difficult to standardize values in some datasets without input from data producers. For instance, the ‘Material’ column of the [dataset](../../repositoryDatasets/dataCleaningProcessExamples/RecycleReport_Tacoma_2013/) `RecycleReport_Tacoma_2013` contains a mix of uppercase and lowercase terms, some even within the same cell. While some terms can be easily interpreted as common recycling abbreviations that should remain in uppercase (i.e. “HDPE” for ‘high-density polyethylene’), others may represent either typographical errors or producer-specific abbreviations (i.e. “GREASE”, “Wood WASTE”). Similarly, test-cleaning made clear that where values were collected and entered in an unstructured, ‘free-text’ manner, such as in the `RecyclingOptions_KingCty` [dataset](../../repositoryDatasets/dataCleaningProcessExamples/RecyclingOptions_KingCty/), standardization would require significant staff time and potentially lead to qualitative data loss. 

### File Naming Convention Notes
 
Generating filenames from a group of ordered elements will ensure a consistent filename structure that will permit R<sup>3</sup> users to quickly ascertain a dataset’s substantive, geographic and temporal scope, even when the filename is viewed outside the context of its R<sup>3</sup> landing page and associated metadata. Linking filenames for derivative and/or otherwise related files will clearly reflect data provenance, and encourage automatic grouping of files with the same origin on user devices following download. File-naming conventions were adapted from guidance from a variety of sources on naming best practices (Frazer, 2013; Stanford Libraries, n.d.-b; The University of Edinburgh, n.d.).

### Versioning Notes
 
Providing clear documentation of changes made to datasets over time will increase user confidence in data provenance, promoting reliance and reuse, and accords with the W3C’s *Data on the Web Best Practices Use Cases and Requirements* (W3C, 2015). Marking dataset changes by date of last update was selected over explicit versioning in order to simplify dataset titles and filenames, and to make the recency of updates immediately apparent to users.


