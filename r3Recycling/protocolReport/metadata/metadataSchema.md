## R<sup>3</sup> Recycling: Metadata Schema

R<sup>3</sup> Recycling utilizes the Data Catalog Vocabulary (“DCAT”) metadata schema (W3C, 2014). All metadata elements in use by the Repository are listed below, with complete information, including an the element class, optionality, cardinality, vocabulary restrictions, notes on R<sup>3</sup>'s choice of this element, and an example of the element as applied to a repository dataset provided in the table available [here](metadataElementsTable.xlsx).

#### R<sup>3</sup> DCAT Metadata Elements:
- `dcat:accessURL` 
- `dct:issued `
- `dct:modified` 
- `dcat:distribution` 
- `dct:rights` 
- `dct:license` 
- `dcat:byteSize` 
- `dct:identifier` 
- `dct:title` 
- `dct:description` 
- `dct:publisher` 
- `dcat:contactPoint` 
- `dct:temporal` 
- `dcat:landingPage` 
- `dcat:keyword` 
- `dcat:theme` 
- `dct:accrualPeriodicity` 
- `dct:spatial` 
- `dct:hasVersion` 
- `dct:creator` 

#### Controlled Vocabularies
 
Three metadata elements, `dcat:keyword`, `dcat:theme`, and `dct:spatial`, are restricted to controlled vocabularies. The `dct:spatial` controlled vocabulary permits only vocabulary that specifies a jurisdiction within Washington state, including city names, municipality names, county names, and state names. Vocabulary will be written following the geographic abbreviations set forth in R<sup>3</sup>’s [file-naming policy](../transformation/).

More complex custom controlled vocabularies were prototyped for the `dcat:keyword` and `dcat:theme` elements per the table below. The vocabularies are intended to be extensible, such that they can expand as the repository expands to include additional datasets.

| dcat:keyword | dcat:theme |
| --- | --- |
| Glass | Recycling routes |
| Paper | Recycling facilities |
| Cardboard | Recyling policies |
| Aluminum | Recycling rates |
| Electronic |   |
| Wood |   |
| Metal |   |
| Oil |   |
| Textile |   |
| Mixed |   |
