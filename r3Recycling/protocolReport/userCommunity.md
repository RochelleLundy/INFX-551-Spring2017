## R<sup>3</sup> Recycling: User Community

### Potential User Community

Although narrow in scope, the topic of recycling is of potential interest to a broad range of individuals and organizations from the public, private, and academic sectors. Prospective users of a Washington-state recycling data repository include:

- Policy-makers and advocacy groups
  - Primarily entities at the municipal, county, and Washington state levels immediately affected by local recycling practices and policies
  - Entities at regional, national, and international levels interested in points of comparison for recycling programs and outcomes
- Academics and researchers
  - Scholars in environmental, urban planning, public policy, engineering, political science, and a variety of other fields touching on recycling-related issues
- Educators, students and interested members of the general public
  - Teachers and students at all educational levels undertaking recycling-related learning modules or research projects
  - Individuals and businesses who need to abide by local recycling rules and/or wish to use local recycling facilities and services
- Corporate entities with a relationship to the recycling or waste management industries
  - Entities that provide recycling or waste management services
  - Entities that produce or rely on recycled materials

### User Stories

User stories envisioning the potential goals of various stakeholders, including end-users from each of the categories noted above, as well as potential contributors seeking to deposit data with R<sup>3</sup>, provided a framework around which to design the repository's features and policies.

#### Users Seeking Data:

| **Goal** | **User Story** |
| --- | --- |
| Find comprehensive data about a subject | &quot;_As a policy maker in Seattle, I want to find all the relevant datasets about recycling glass bottles so that I can make informed decisions about what to suggest for our city.&quot;_ |
| Find comprehensive data about a place | &quot;_As someone who has recently moved from Portland to Seattle, I want to find all the relevant datasets on the recycling procedures in Seattle so that I know how to sort my refuse.&quot;_ |
| Find data about a time period | &quot;_As a professor of urban planning specializing in green infrastructure, I want to examine how Seattle&#39;s recycling participation rate has changed since 2010.&quot;_ |
| Find data compiled by a particular author | &quot;_As the CEO of a Spokane company accused of falsely claiming to use recycled materials, I want to find out who produced the dataset cited in the accusation.&quot;_ |
| Understand how data can be used | _&quot;As a Bellevue schoolteacher assigning a class project about recycling, I want to make sure that my students can legally copy and post parts of a dataset on their Facebook page.&quot;_ |
| Download data in an appropriate format | _&quot;As a non-profit organization on a limited budget, I can&#39;t afford to buy new software to work with data and want to the open recycling files I download with programs that come preinstalled on our office desktop computers.&quot;_ |


#### Users Contributing Data:

| **Goal** | **User Story** |
| --- | --- |
| Describe the author of a dataset | &quot;_As a government depositor to R<sup>3</sup> Recycling, I need to know whether there is a controlled vocabulary for Washington government entities that I should use when I indicate the producer of the dataset.&quot;_ |
| Understand what datasets are accepted for deposit | _&quot;As a county waste management agency, I want to find out whether my dataset is &#39;about&#39; recycling and can be deposited with R<sup>3</sup> even though it also involves landfill data.&quot;_ |
| Know how datasets will be stored and can be accessed over time | _&quot;As a city employee, I need to tell my manager whether depositing our data with R<sup>3</sup> means that we can delete it from our servers because you will always keep it available online.&quot;_ |


A key theme that emerged from these user stories is the need for &#39;findability&#39;, such that data about specific subjects, places, and time periods can be quickly and intuitively located by users with a range of technical and search expertise. This theme provided the backdrop for R<sup>3</sup>'s [metadata schema](metadata/metadataSchema.md), which addresses the specific user needs raised here in further detail, but also shaped decisions surrounding [repository infrastructure](repositorySoftware.md) in light of the impact of software choice on the visualization and mapping features R<sup>3</sup> can offer.

The end-user value on ease of access to data contributed to decisions regarding both what data types and formats would be accepted for [deposit](deposit/depositPolicy.md) and how it would be [transformed and presented](transformation/transformationPolicy.md). However, the stories also revealed that many users sought comprehensive access to data in order to obtain definitive information or guidance on a particular subject. While some users, such as the schoolteacher, are likely interested in finding any recycling dataset, it was easy to imagine many users, such as academic researchers or businesses needing to comply with recycling rules, for whom knowing they had found all relevant datasets was essential, which counseled in favor of flexibility if ease of access and comprehensive access conflict.

Stories relating to data depositors indicated that R<sup>3</sup> should establish clear guidelines regarding how datasets are [deposited](deposit/depositPolicy.md) and [ingested](ingestion/ingestionPolicy.md), particularly regarding how depositors must describe their datasets for [metadata](metadata/metadataSchema.md) purposes. Depositor user stories also suggested the importance of transparency in how and for how long datasets will be [preserved](deposit/depositPolicy.md).
