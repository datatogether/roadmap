# Metadata

As a basis for metadata & attribution for datasets & content, we propose implementing a subset of the project-open-data **data.json dataset spec**.

### Reading & Resources:
* [data.json Metadata Resources](https://project-open-data.cio.gov/v1.1/metadata-resources/)
* [Project Open Data data.json Schema](https://project-open-data.cio.gov/v1.1/schema/)

### Dataset Fields

| Field | Label | Definition | Required |
|-------|-------|------------|----------|
| **@type** | Metadata Type |  IRI for the [JSON-LD](https://www.w3.org/TR/json-ld/#specifying-the-type) data type. This should be `dcat:Dataset` for each Dataset. | No |
| **title** | Title | Human-readable name of the asset. Should be in plain English and include sufficient detail to facilitate search and discovery. | **Always** |
| **description** | Description | Human-readable description (e.g., an abstract) with sufficient detail to enable a user to quickly understand whether the asset is of interest. | **Always** |
| **keyword** | Tags | Tags (or keywords) help users discover your dataset; please include terms that would be used by technical and non-technical users. | **Always** |
| **modified** |  Last Update | Most recent date on which the dataset was changed, updated or modified. | **Always** |
| **publisher** | Publisher | The publishing entity and optionally their parent organization(s). | **Always** |
| **contactPoint** |  Contact Name and Email | Contact person’s name and email for the asset. | **Always** |
| **identifier** | Unique Identifier | A unique identifier for the dataset or API as maintained within an Agency catalog or database. | **Always** |
| **accessLevel** | Public Access Level |  The degree to which this dataset **could** be made publicly-available, *regardless of whether it has been made available*. Choices: public (Data asset is or could be made publicly available to all without restrictions), restricted public (Data asset is available under certain use restrictions), or non-public (Data asset is not available to members of the public). | **Always** |
| **bureauCode**[(USG)](https://project-open-data.cio.gov/v1.1/schema/#USG-note) | Bureau Code | Federal agencies, combined agency and bureau code from OMB Circular A-11, Appendix C ([PDF](https://www.whitehouse.gov/sites/default/files/omb/assets/a11_current_year/app_c.pdf), [CSV](https://project-open-data.cio.gov/data/omb_bureau_codes.csv)) in the format of `015:11`. | **Always** |
| **programCode**[(USG)](https://project-open-data.cio.gov/v1.1/schema/#USG-note)| Program Code | Federal agencies, list the primary program related to this data asset, from the Federal Program Inventory. Use the format of `015:001`. | **Always** |
| **license** | License | The license or non-license (i.e. Public Domain) status with which the dataset or API has been published. See [Open Licenses](https://project-open-data.cio.gov/open-licenses/) for more information. | If-Applicable |
| **rights** |  Rights | This may include information regarding access or restrictions based on privacy, security, or other policies. This should also serve as an explanation for the selected “accessLevel” including instructions for how to access a restricted file, if applicable, or explanation for why a “non-public” or “restricted public” data asset is not “public,” if applicable. Text, 255 characters. | If-Applicable |
| **spatial** | Spatial | The range of spatial applicability of a dataset. Could include a spatial region like a bounding box or a named place. | If-Applicable |
| **temporal** | Temporal | The range of temporal applicability of a dataset (i.e., a start and end date of applicability for the data).  | If-Applicable |
| **distribution** |  Distribution | A container for the array of Distribution objects. See Dataset [Distribution Fields](https://project-open-data.cio.gov/v1.1/schema/#dataset-distribution-fields) below for details. | If-Applicable |
| **accrualPeriodicity** | Frequency | The frequency with which dataset is published.  | No |
| **conformsTo** |  Data Standard | URI used to identify a standardized specification the dataset conforms to.  | No |
| **dataQuality**[(USG)](https://project-open-data.cio.gov/v1.1/schema/#USG-note) |  Data Quality |  Whether the dataset meets the agency’s Information Quality Guidelines (true/false). | No |
| **describedBy** | Data Dictionary | URL to the data dictionary for the dataset. Note that documentation other than a data dictionary can be referenced using Related | Documents | (`references`).  | No |
| **describedByType** | Data Dictionary Type | The machine-readable file format (IANA Media Type also known as MIME Type) of the dataset’s Data Dictionary (` describedBy`).  | No |
| **isPartOf** | Collection | The collection of which the dataset is a subset.  | No |
| **issued** | Release Date | Date of formal issuance.  | No |
| **language** |  Language | The language of the dataset.  | No |
| **landingPage** | Homepage URL |  This field is not intended for an agency’s homepage (e.g. www.agency.gov), but rather if a dataset has a human-friendly hub or landing page that users can be directed to for all resources tied to the dataset.  | No |
| **primaryITInvestmentUII**[(USG)](https://project-open-data.cio.gov/v1.1/schema/#USG-note) | Primary IT | Investment UII For linking a dataset with an IT Unique Investment Identifier (UII).  | No |
| **references** |  Related Documents | Related documents such as technical information about a dataset, developer documentation, etc.  | No |
| **systemOfRecords** | System of Records | If the system is designated as a system of records under the Privacy Act of 1974, provide the URL to the System of Records Notice related to this dataset.  | No |
| **theme** | Category | Main thematic category of the dataset.  | No |

### Distribution Fields
| Field | Label | Definition | Required |
|-------|-------|------------|----------|
| **@type** | Metadata Type |  IRI for the [JSON-LD](https://www.w3.org/TR/json-ld/#specifying-the-type) data type. This should be `dcat:Dataset` for each Dataset. | No |
| **accessURL** | Access URL | URL providing indirect access to a dataset, for example via API or a graphical interface. | If-Applicable |
| **conformsTo** | Data Standard | URI used to identify a standardized specification the distribution conforms to. | No |
| **describedBy** | Data Dictionary | URL to the data dictionary for the distribution found at the downloadURL. Note that documentation other than a data dictionary can be referenced using Related Documents as shown in the expanded fields. | No |
| **describedByType** | Data Dictionary Type | The machine-readable file format (IANA Media Type or MIME Type) of the distribution’s describedBy URL. | No |
| **description** | Description | Human-readable description of the distribution. No
| **downloadURL** | Download URL | URL providing direct access to a downloadable file of a dataset. | If-Applicable |
| **format** | Format |  A human-readable description of the file format of a distribution. | No |
| **mediaType** | Media Type |  The machine-readable file format (IANA Media Type or MIME Type) of the distribution’s downloadURL. | If-Applicable |
| **title** | Title | Human-readable name of the distribution. | No | 


### Example:

```json
{
  "conformsTo": "https://project-open-data.cio.gov/v1.1/schema",
  "dataset": [
    {
      "accessLevel": "public",
      "bureauCode": [
        "018:10"
      ],
      "contactPoint": {
        "fn": "Jane Doe",
        "hasEmail": "mailto:jane.doe@agency.gov"
      },
      "description": "This dataset provides national statistics on the production of widgets",
      "distribution": [
        {
          "downloadURL": "https://data.agency.gov/datasets/widgets-statistics/widgets.csv",
          "mediaType": "text/csv"
        },
        {
          "downloadURL": "https://data.agency.gov/datasets/widgets-statistics/widgets-all.zip",
          "mediaType": "application/zip"
        },
        {
          "downloadURL": "http://www.agency.gov/feeds/widgets-all.json",
          "mediaType": "application/json"
        },
        {
          "accessURL": "https://data.agency.gov/api/widgets-statistics/"
        }
      ],
      "identifier": "http://dx.doi.org/10.7927/H45X26V8",
      "keyword": [
        "widget",
        "manufacturing",
        "factory"
      ],
      "modified": "2011-11-19T12:00:00Z",
      "programCode": [
        "018:001"
      ],
      "publisher": {
        "name": "Widget Services",
        "subOrganizationOf": {
          "name": "Office of Citizen Services and Innovative Technologies",
          "subOrganizationOf": {
            "name": "General Services Administration",
            "subOrganizationOf": {
              "name": "U.S. Government"
            }
          }
        }
      },
      "title": "U.S. Widget Manufacturing Statistics"
    },
    {
      "accessLevel": "public",
      "bureauCode": [
        "018:10"
      ],
      "contactPoint": {
        "fn": "James Doe",
        "hasEmail": "mailto:james.doe@agency.gov"
      },
      "description": "This dataset provides ranges on widget phase modulation",
      "identifier": "http://dx.doi.org/10.7927/H4K64G12",
      "keyword": [
        "widget",
        "modulation"
      ],
      "modified": "2011-11-19T12:00:00Z",
      "programCode": [
        "018:001"
      ],
      "publisher": {
        "name": "Widget Modulation Program",
        "subOrganizationOf": {
          "name": "Office of Citizen Services and Innovative Technologies",
          "subOrganizationOf": {
            "name": "General Services Administration",
            "subOrganizationOf": {
              "name": "U.S. Government"
            }
          }
        }
      },
      "title": "U.S. Widget Phase Modulation Ranges"
    },
    {
      "accessLevel": "public",
      "bureauCode": [
        "018:10"
      ],
      "contactPoint": {
        "fn": "James Doe",
        "hasEmail": "mailto:james.doe@agency.gov"
      },
      "description": "This dataset provides ranges on widget phase modulators for 2011",
      "distribution": [
        {
          "downloadURL": "https://data.agency.gov/datasets/widgets-modulator-ranges.csv",
          "mediaType": "text/csv"
        }
      ],
      "identifier": "http://dx.doi.org/10.7927/H49P2ZKM",
      "keyword": [
        "widget",
        "modulation"
      ],
      "modified": "2011-11-19T12:00:00Z",
      "programCode": [
        "018:001"
      ],
      "publisher": {
        "name": "Widget Modulation Program",
        "subOrganizationOf": {
          "name": "Office of Citizen Services and Innovative Technologies",
          "subOrganizationOf": {
            "name": "General Services Administration",
            "subOrganizationOf": {
              "name": "U.S. Government"
            }
          }
        }
      },
      "title": "U.S. Widget Phase Modulation Ranges for 2011"
    }
  ]
}
```