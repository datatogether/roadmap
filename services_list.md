# Services list
Each of the following section breaks down an area in this diagram, listing the purpose of each service in that area.

![overview](https://github.com/edgi-govdata-archiving/overview/blob/proposed-services/proposed-services/diagrams/service-overview.png)


# Authentication
Services that manage users.

| Service | Description | Technologies | Status | Key Contributors |
|---------|-------------|--------------|--------|------------------|
| [**Identity**](https://github.com/qri-io/ident.archivers.space) | A central service for creating an account, login, logout, managing user info, etc. Other services can talk to the identity service to get information about a user. It's hosted [here](https://ident.archivers.space). Normal humans can create & manage accounts using the [archivers 2.0 webapp](https://alpha.archivers.space). | *alpha* | **Go** | @b5 |
| [**IdentityDB**](https://github.com/qri-io/ident.archivers.space) | Database of all user identities. Only way to talk to it is through the identity service. | *alpha* | **Postgres** | @b5 |


# Guidance
Services that guide Data Rescue efforts.

### Agency Primers
Project Page: [Edgi Website](https://envirodatagov.org/agencyprimers/)
Status: *in use*

Spreadsheet of agencies & sub-agencies for archiving.

Key Contributors:
* Maya An D. | Github: @mayaad
* Toly Rinberg | Github: @trinberg
* Andrew Bergman

### Chrome Extension
Project Page: [github](https://github.com/edgi-govdata-archiving/eot-nomination-tool)
Technologies: **Javascript** **Chrome Extension**
Status: *in use*

Chrome extension to nominate government data that needs to be preserved.

Key Contributors:
* Matt Price | Github: @titaniumbones
* Ates Goral | Github: @ates

### Uncrawlables Spreadsheet
Satus: *in use*

The chrome extension dumps it's output to a google sheet of uncrawlable content.

# Reporting
Services for collecting & delivering platform-wide reports.

### Stats
Status: *planning to use an existing solution*

Server that periodically collects key stats platform-wide & reports them for easy public consumption.

This service will ideally just consume the JSON API's of all the other services & output a dashboard, there are lots of frameworks out in the wild that do this. We should research & pick one.

### Health
Status: *planning to use an existing solution*

Server that periodically polls all services on the platform & outputs a page that shows when a service is down / malfunctioning.

Status check frameworks for this already exist. We should research & pick one.

# Archiving 1.0
Current Services for downloading & storing content.

### Archivers 1.0
Project Page: [github](https://github.com/edgi-govdata-archiving/archivers.space)
Technologies: **Javascript** **MeteorJS** **ReactJS**
Status: *in use*

App for volunteers to research urls, add metadata, and upload archived .zip's.

Key Contributors:
* Kevin McCulloch | Github: @kmcculloch

### Archivers 1.0 DB
Project Page: [github](https://github.com/edgi-govdata-archiving/archivers.space/imports/api)
Status: *in use*

MongoDB Instance

### DataRefuge S3 Bucket
Status: *in use*


# Archiving 2.0
New services for archiving & describing content.

### Archivers 2.0
Project Page: [github](https://github.com/qri-io/context)
Technologies: **Javascript** **ReactJS** **Redux**
Status: *alpha*

Webapp for volunteers to add metadata to urls & content.

### Patchbay
Project Page: [github](https://github.com/qri-io/patchbay)
Technologies: **Go**
Status: *alpha*

Backing service for archivers app, it coordinates realtime communication between users of the archivers 2.0 app, and does on-the-fly archiving of undiscovered urls.

### Miru
Project Page: [github](https://github.com/zsck/miru/)
Technologies: **Go**
Status: *beta*

A website monitoring tool that periodically checks a site for changes & running custom scripts. Miru takes user-contributed scripts capable of extracting uncrawlable content & executes them, recording their results in a uniform format.

Key Contributors:
* Zack Mullaly | Github: @zsck

### Miru DB
Project Page: [github](https://github.com/zsck/miru/blob/master/models/queries.go)
Technologies: **sqLite**
Status: *beta*

Miru's backing database.

### Recipes
Project Page: [github](https://github.com/datarescue-boston/harvesting-tools)
Technologies: **Various Languages**
Status: *under construction*

A collection of strategies (recipes) for dealing with various types of uncrawlable content.

Key Contributors:
Jeff Liu | Github: @jeffreyliu

### ArchiveDB
Technologies: **Postgres**
Status: *alpha*

Database of archived content & metadata. Schema is outlined [here](https://github.com/qri-io/patchbay/blob/master/sql/schema.sql).

### ArchiveContent S3 Bucket
Technologies: **S3**
Status: *alpha*

A big S3 bucket to save & read content to.

### Sentry
Project Page: [github](https://github.com/qri-io/sentry)
Technologies: **Go**
Status: *planned*

Sentry is a web that continually scans for pages that haven't been checked in a while (or ever), and generates snapshots of what it finds.


# Site Monitoring
Services for tracking changes to websites.

### PageFreezer
Project Page: [pagefreezer](http://pagefreezer.com)
Status: *external service*

### Versionista 
Project Page: [versionista](https://versionista.com)
Status: *external service*


### Web-Cli

# Distribution
Services for disseminating content & data to others.

### API
Technologies: **JSON**
Status: *planned*

JSON API for as many platform services as possible. This would include platform users, archived content, archived metadata, and web-monitoring diffs.

### Bag-Gen
Technologies: **Python**
Status: *planned*

A server to generate bags for bag-oriented data hosting services (ckan, dataverse, etc). 

This service is planned as a python wrapper around [python bagIt lib](https://pypi.python.org/pypi/bagit/) that turns it into a server can generate bags from archived content.

### IPFS-Node
Technologies: **Go**
Status: *planned*

A Bundle of existing frameworks to publish & syncronize archived content with the [Inter-Planitary File System](https://ipfs.io).

### Dat-Gen
Technologies: **Javascript** **Node.js**
Status: *planned*

Service for generating & hosting dat-data project packages.

This is a planned lightweight node.js wrapper around the dat library, capabale of translating archived content to dat projects.

# Coordination
Services for integrating with other services.

### Coordinator
Status: *planned*

Service that talks to other archiving services about content & metadata they have, using prewritten integrations for translating to each service.

This service functions in a very similar fashion to the current Miru implementation. This service could be implemented either as another Miru instance, or a forked version (preference for implementing as an instance).

### Coordinator DB
Status: *planned*

Cache of data we've received from other services in a format that matches archiveDB.

### Integrations
Status: *planned*

Series of recipe-repos that map external data sources & destinations.

