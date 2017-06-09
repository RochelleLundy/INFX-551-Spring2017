## R<sup>3</sup> Recycling: Ingestion Policy

### Upload

- R<sup>3</sup> utilizes CKAN's FileStore feature to allow for upload of datasets via API with authentication credentials that will be provided to depositors upon approval of a proposed deposit (CKAN, n.d.-c)
  - Uploads will be scanned for viruses and other quality issues using CKAN features and extension packages
  - Alternative upload procedures may be determined on a case-by-case basis in relation to depositor and dataset needs
- Upon upload, datasets will be assigned an internally unique identifier that will be used for reference within the repository
- Following upload, depositors will receive email confirmation of submission, including the assigned internally unique identifier and the expected timeline of the publication process

### Pre-Publication

- Although depositors will be asked to confirm on their deposit form that the dataset does not contain any personally identifying, confidential, or otherwise sensitive information, all datasets will be reviewed for such information prior to publication
  - R<sup>3</sup> will develop a list of 'red flag' criteria for reference by staff and incorporation into an automated content review system for identification of potentially sensitive information
  - Depositors of datasets raising confidentiality, personal identification, or sensitivity concerns will be asked to remove, redact, anonymize or otherwise recode the relevant data, and resubmit it along with documentation of the modifications made
    - R<sup>3</sup> cannot accommodate or take responsibility for modification of submitted datasets to address sensitivity concerns
    - However, upon individual consultation and agreement with depositors as to appropriate modifications, R<sup>3</sup> may perform or assist in the redaction, removal or recoding of small amounts (comprising less than 5% of dataset values) of sensitive data
  - R<sup>3</sup> is unable to support user-access restrictions and will not host datasets that cannot be made publicly available
- Persistent, universally unique identifiers will be obtained from the DataCite DOI service and assigned to datasets using a corresponding CKAN extension (U.K. Natural History Museum, n.d.)
- Prior to publication, depositors will review and provide written confirmation of the accuracy of the descriptive information supplied on their initial deposit form, and promptly respond to any inquiries from R<sup>3</sup> regarding deposit information
- Prior to publication, depositors will complete a deposit and license agreement reaffirming their grant of permission to publish the dataset, representation that they have authority to grant permission to publish the data under the license to be applied, and acknowledgement of the repository's terms of use
- Metadata will be generated pursuant to R<sup>3</sup>'s [metadata schema](../metadata/metadataSchema.md), drawing information from the submissions form and generating additional required elements
