## R<sup>3</sup> Recycling: Metadata Schema

R<sup>3</sup> Recycling utilizes the Data Catalog Vocabulary (“DCAT”) metadata schema (W3C, 2014). The table below describes each metadata element in use by the repository:

| **Element** | **Element Definition (W3C, 2014)** | **Rationale** | **Example (generated for the dataset &#39;What do I do With…&#39; (King County (2016, July 20))** |
| --- | --- | --- | --- |
| dcat:accessURL | &quot;A landing page, feed, SPARQL endpoint or other type of resource that gives access to the distribution of the dataset&quot; | Element will include the DOI-based URL associated with datasets published in this repository; chosen over dcat:landingPage in order to point to the data itself | &lt;dcat:accessURL&gt;http://dx.doi.org/10.1000/xyz123&lt;/dcat:accessURL&gt; |
| dct:issued | &quot;Date of formal issuance (e.g., publication) of the distribution.&quot; | Describes the date that the dataset was submitted to the repository (not the date of issuance of the dataset itself) | &lt;dct:issued&gt;2010-10-21&lt;/dct:issued&gt; |
| dct:modified | &quot;Most recent date on which the distribution was changed, updated or modified.&quot; | Describes dates of modification to dataset; although defined to include the &quot;most recent date,&quot; it will be unbounded in order to retain a full record of data modifications | &lt;dct:modified&gt;2016-07-20&lt;/dct:modified&gt; |
| dcat:distribution | &quot;Represents a specific available form of a dataset. Each dataset might be available in different forms, these forms might represent different formats of the dataset or different endpoints. Examples of distributions include a downloadable CSV file, an API or an RSS feed&quot; | Indicates formats in which a dataset is available; in light of repository&#39;s flexible deposit policy with regard to format, element will allow users to quickly identify formats suitable for their needs | &lt;dcat:distribution&gt;TSV&lt;/dcat:distribution&gt; |
| dct:rights | &quot;Information about rights held in and over the distribution.&quot; | Repository policy emphasizes provision of rights and licensing information to users to remove uncertainty with regard to reuse | &lt;dct:rights&gt;Public Domain&lt;/dct:rights&gt; |
| dct:license | &quot;This links to the license document under which the distribution is made available.&quot; |  Repository policy emphasizes provision of rights and licensing information to users to remove uncertainty with regard to reuse | &lt;dct:license&gt;https://creativecommons.org/publicdomain/zero/1.0/&lt;/dct:license&gt; |
| dcat:byteSize | &quot;The size of a distribution in bytes.&quot; |  This element describes the size of the file; as we anticipate many non-technical users, it will be useful to provide information about the size of potential file downloads | &lt;dcat:byteSize&gt;1153433.6&lt;/dcat:byteSize&gt; |
| dct:identifier | &quot;A unique identifier of the dataset.&quot; |  Used to describe the identification number assigned to the dataset at the time of submission, which is internally unique to the repository | &lt;dct:identifier&gt;R3\_1&lt;/dct:identifier&gt; |
| dct:title | &quot;A name given to the record.&quot; (alternately: &quot;A name given to the catalog.&quot;) |  Each dataset is titled according to our naming conventions | &lt;dct:title&gt;RecyclingOptions\_KingCty&lt;/dct:title&gt; |
| dct:description | &quot;Free-text account of the record.&quot; (alternately: &quot;A free-text account of the catalog.&quot;) |  This element allows for the submitter to describe the dataset, in 600 characters or fewer; staff will determine whether this description should be altered to better describe the dataset | &lt;dct:description&gt;The &quot;What do I do with...?&quot; site provides King County citizens with recycling and proper disposal options for over 100 products and materials. The site lists over 400 businesses (mostly local) that accept products and materials for recycling or proper disposal. Business details include location (with mapping), contact information, hours of operation, restrictions, fees and more. The goal is to reduce the volume of reusable or recyclable items being added to the waste-stream, thereby reducing the environmental impact of those items while extending the lifespan of our landfills.&lt;/dct:description&gt; |
| dct:publisher | &quot;An entity responsible for making the dataset available.&quot; (alternately: &quot;The entity responsible for making the catalog online.&quot;) |  This element describes the person or company submitting the dataset to the repository. If the identity of depositors to the repository remains consistent over time, an extensible controlled vocabulary may be developed for this element to standardize naming conventions for government and other entities | &lt;dct:publisher&gt;King County Solid Waste Division&lt;/dct:publisher&gt; |
| dcat:contactPoint | &quot;Link a dataset to relevant contact information which is provided using VCard&quot; |  In addition to knowing the publisher and author information, this element offers contact information for someone who bears some responsibility towards the dataset outside of the repository. This element is optional; submitters do not have to provide public contact information. | &lt;dcat:contactPoint&gt;Jay Beach&lt;/dcat:contactPoint&gt; |
| dct:temporal | &quot;The temporal period that the dataset covers.&quot; |  Provides a date or range of dates to indicate the time period to which the dataset applies | &lt;dct:temporal&gt;2010-present&lt;/dct:temporal&gt; |
| dcat:landingPage | &quot;A Web page that can be navigated to in a Web browser to gain access to the dataset, its distributions and/or additional information.&quot; |  Element location where file can be dowloaded from repository | &lt;dcat:landingPage&gt;https://r3repository.org/RecyclingOptions\_KingCty&lt;/dcat:landingPage&gt; |
| dcat:keyword | &quot;A keyword or tag describing the dataset.&quot; |  Intended to enhance findability through use of custom controlled vocabulary (see below) | &lt;dcat:keyword&gt;recycling&lt;/dcat:keyword&gt;
&lt;dcat:keyword&gt;policy&lt;/dcat:keyword&gt;
&lt;dcat:keyword&gt;education&lt;/dcat:keyword&gt;
&lt;dcat:keyword&gt;solid waste&lt;/dcat:keyword&gt; |
| dcat:theme | &quot;The main category of the dataset. A dataset can have multiple themes.&quot; |  Designed to differentiate datasets of different types for easier browsing; this element includes a controlled vocabulary (see below). | &lt;dcat:theme&gt;recycling policies&lt;/dcat:theme&gt; |
| dct:accrualPeriodicity | &quot;The frequency at which dataset is published.&quot; |  Indicates how frequently the content of a dataset is updated; units of time are initially set as years, but may shifted to smaller units depending on characteristics of collected datasets | &lt;dct:accrualPeriodicity&gt;16&lt;/dct:accrualPeriodicity&gt; |
| dct:spatial | &quot;Spatial coverage of the dataset.&quot; |  Element indicates geographic scope of a dataset, which is highly relevant to recycling data and to repository users; unbounded to allow for metadata that includes all relevant geographic levels; element includes a controlled vocabulary (see below) | &lt;dct:spatial&gt;Seattle&lt;/dct:spatial&gt;
&lt;dct:spatial&gt;KingCty&lt;/dct:spatial&gt;
&lt;dct:spatial&gt;WA&lt;/dct:spatial&gt; |
| dct:hasVersion | &quot;A related resource that is a version, edition, or adaptation of the described resource.&quot; (Purl.org. (2008, January 14) | We have a number of resources that are versions of or derivative of each other; this element is provided to indicate the versioning of these items | &lt;dct:hasVersion&gt;false&lt;/dct:hasVersion&gt; |
| dct:creator | &quot;An entity primarily responsible for making the resource.&quot;( Purl.org. (2010, October 1)) |  Describes the original author of the data set, which may or may not be the same as the publisher, because this information may not be provided on the dataset itself, provision by the depositor will be emphasized on deposit forms | &lt;dct:creator&gt;Jay Beach&lt;/dct:creator&gt; |



#### Controlled Vocabularies
 
Three metadata elements, `dcat:keyword`, `dcat:theme`, and `dct:spatial`, are restricted to controlled vocabularies. The `dct:spatial` controlled vocabulary permits only vocabulary that specifies a jurisdiction within Washington state, including city names, municipality names, county names, and state names. Vocabulary will be written following the geographic abbreviations set forth in R<sup>3</sup>’s file-[naming policy](../transformation/).

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
