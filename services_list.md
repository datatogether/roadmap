# Services list
Each of the following section breaks down an area in this diagram, listing the purpose of each service in that area.

![overview](https://github.com/edgi-govdata-archiving/overview/blob/proposed-services/proposed-services/diagrams/service-overview.png)


# Authentication
Services that manage users.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Identity**](https://github.com/qri-io/ident.archivers.space) | A central service for creating an account, login, logout, managing user info, etc. Other services can talk to the identity service to get information about a user. It's hosted [here](https://ident.archivers.space). Normal humans can create & manage accounts using the [archivers 2.0 webapp](https://alpha.archivers.space). | *alpha* | Go | @b5 |
| [**IdentityDB**](https://github.com/qri-io/ident.archivers.space) | Database of all user identities. Only way to talk to it is through the identity service. | *alpha* | Postgres | @b5 |


# Guidance
Services that guide Data Rescue efforts.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Agency Primers**](https://envirodatagov.org/agencyprimers/) | Spreadsheet of agencies & sub-agencies for archiving. | Google Sheets, Airtable | *in use* | @mayaad, @trinberg, Andrew Bergman |
| [**Chrome Extension**](https://github.com/edgi-govdata-archiving/eot-nomination-tool) | Chrome extension to nominate government data that needs to be preserved. |  **Javascript**, **Chrome Extension** | *in use* | @ates, @titaniumbones |
| **Uncrawlables Spreadsheet** | The chrome extension dumps it's output to a google sheet of uncrawlable content. | Google Sheets | *in use* | | 

# Reporting
Services for collecting & delivering platform-wide reports.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| **Stats** | Server that periodically collects key stats platform-wide & reports them for easy public consumption. This service will ideally just consume the JSON API's of all the other services & output a dashboard, there are lots of frameworks out in the wild that do this. We should research & pick one. | *planning to use an existing solution* | *not yet started* | |
| **Health** | Server that periodically polls all services on the platform & outputs a page that shows when a service is down / malfunctioning. Status check frameworks for this already exist. We should research & pick one. | *planning to use an existing solution* | *not yet started* | |


# Archiving 1.0
Current Services for downloading & storing content.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Archivers 1.0**](https://github.com/edgi-govdata-archiving/archivers.space) | App for volunteers to research urls, add metadata, and upload archived .zip's. | Javascript, MeteorJS, ReactJS | *in use* | @kmcculloch, @danielballan, @b5 |
| [**Archivers 1.0 DB**](https://github.com/edgi-govdata-archiving/archivers.space/imports/api) | Archivers Backing database | MongoDB | *in use* | @b5 |
| [**S3-Upload-Server**](https://github.com/edgi-govdata-archiving/s3-upload-server) | Server for making uploads to S3 buckets via browser or AWS CLI tokens |  *in use* | **Go** | @b5 |
| [**Zip-Starter**](https://github.com/edgi-govdata-archiving/zip-starter) | Server for generating base metadata zip archivers | *in use* | Go | @b5 |


# Archiving 2.0
New services for archiving & describing content.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Archivers 2.0**](https://github.com/qri-io/context) | Webapp for volunteers to add metadata to urls & content. | Javascript, ReactJS, Redux | *alpha* | @b5 |
| [**Patchbay**](https://github.com/qri-io/patchbay) | Backing service for archivers app, it coordinates realtime communication between users of the archivers 2.0 app, and does on-the-fly archiving of undiscovered urls. | Go | *alpha* | @b5 |
| [**Miru**](https://github.com/zsck/miru/) | A website monitoring tool that periodically checks a site for changes & running custom scripts. Miru takes user-contributed scripts capable of extracting uncrawlable content & executes them, recording their results in a uniform format. | Go | *beta* | @zsck |
| [**Miru DB**](https://github.com/zsck/miru/blob/master/models/queries.go) | Miru's backing database. | sqLite | *beta* | @zsck |
| [**Recipes**](https://github.com/datarescue-boston/harvesting-tools) | A collection of strategies (recipes) for dealing with various types of uncrawlable content. | **Various Languages** | *under construction* | @jeffreyliu |
| ArchiveDB | Database of archived content & metadata. Schema is outlined [here](https://github.com/qri-io/patchbay/blob/master/sql/schema.sql). | Postgres | *alpha* | |
| ArchiveContent S3 Bucket | A big S3 bucket to save & read content to. | S3 | *alpha* | |
| [**Sentry**](https://github.com/qri-io/sentry) | Sentry is a web that continually scans for pages that haven't been checked in a while (or ever), and generates snapshots of what it finds. | **Go** | *planned* | @b5 |


# Site Monitoring
Services for tracking changes to websites.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Web Monitoring DB**](https://github.com/edgi-govdata-archiving/web-monitoring-db) | Website Monitoring project: a more automated version of page monitoring with Versionista (proof of concept for now) | Ruby | *under construction* | @Mr0grog |
| [**Web Monitoring Differ**](https://github.com/edgi-govdata-archiving/web-monitoring-differ) | Diffing service for the website monitoring project | Javascript | *under construction* | @WestleyArgentum |
| [**Web Monitoring Processing**](https://github.com/edgi-govdata-archiving/web-monitoring-processing) | Website Monitoring project: data processing, PageFreezer integration, and (eventually) diff filtering and processing | Jupyter, Python | *under construction* | @danielballan | 
| [**Web Monitoring UI**](https://github.com/edgi-govdata-archiving/web-monitoring-ui) | Website Monitoring project: enable analysts to quickly assess changes to monitored government websites | Javascript | *under construction* | @lightandluck |
| [**PageFreezer**](http://pagefreezer.com) | Page freezing / archiving service | *external service* | *integrating* | @danielballan |
| [**Versionista**](https://versionista.com) | Page freezing / archiving service | *external service* | *in use* | @danielballan |

# Distribution
Services for disseminating content & data to others.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| **API** | JSON API to wrap & publish as many platform services as possible. This would include platform users, archived content, archived metadata, and web-monitoring diffs. | JSON | *planned* | |
| **Bag-Gen** | A server to generate bags for bag-oriented data hosting services (ckan, dataverse, etc).  This service is planned as a python wrapper around [python bagIt lib](https://pypi.python.org/pypi/bagit/) that turns it into a server can generate bags from archived content. | Python |  *planned* | |
| **IPFS-Node** | A Bundle of existing frameworks to publish & syncronize archived content with the [Inter-Planitary File System](https://ipfs.io). |  **Go** | *planned* | |
| **Dat-Gen** | Service for generating & hosting dat-data project packages. This is a planned lightweight node.js wrapper around the dat library, capabale of translating archived content to dat projects. | Javascript, Node.js | *planned* | |

# Coordination
Services for integrating with other services.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| **Coordinator** | Service that talks to other archiving services about content & metadata they have, using prewritten integrations for translating to each service. This service functions in a very similar fashion to the current Miru implementation. This service could be implemented either as another Miru instance, or a forked version (preference for implementing as an instance). | | *planned* | | 
| **Coordinator DB** |  Cache of data we've received from other services in a format that matches archiveDB. | | *planned* | |
| **Integrations** | Series of recipe-repos that map external data sources & destinations. | | *planned* | |

