# Workflow Changes
The following is a list of high level changes to the way the archivers.space app will work for archiving data.

The actual implementation of these changes will be spread across a number of services, but the goal will be
to present a unified user experience that covers any of the necessary workflows.

### No more download/upload
To guarantee digital provenance & prevent deduplication, volunteers no longer directly download content.
Instead we will provide tools for automatically archiving content that is web-crawlable.

A large number of urls that arrive at archivers.space are archivable by a web crawler. By archiving this
content automatically, we will cut down on the amount of content that's labelled uncrawlable.

Currently we ask users to both write & execute code for uncrawlable content. We will still ask volunteers
to write code that extracts uncrawlable content, but two things will change:
  1. We will now ask that volunteers put additional checks on their code to match digital provenance standards.
  2. We will execute the code they've written, recording the results.

By moving code execution onto our servers, we make gains on quality control, repeatability, and attribution.
This will solve the problem of a download taking longer than an event, and will mean volunteers won't have to
pay for virtual machine time & storage.

### Continuous, automated content crawling
By enforcing strict digial provenance & archiving repeatability, we can now automatically monitor &
update our records in response to changing content. Once a url is added to the platform, we can
continually monitor for changes, and issue updates accordingly.

By switching to having our servers execute custom code, this will allow us to re-run the same code 
to check for changes, dramatically increasing the value of volunteer-contributed code.

### Primer-Driven Archiving
Because the new app will track individual URLS, there will be _many_ more URLS on the platform,
too many to warrent working from a full-fledged list. 

To generate lists of content to work on at events, we will use primers to determine which urls need attention.
Showing both lists of already-archived content that needs research & metadata, as well as urls that have been
flagged as uncrawlable.

### User-Attributed contributions
All contributions (writing metadata, creating a collection of content, etc) will now be connected to a user
profile, backed by a keypair. This will enable adknowledging a user's contributions, abuse prevention, 
and selective filtering of metadata based on contributors.

### Cross-Project Coordination
We will coordinate with peer archiving projects, allowing users to write metadata on our service that
may have been archived elsewhere, pushing these contributions back to the greater community.

### Institutions as First-Class Contributors
As an example, data.gov publishes metadata about its content. If we archive data.gov content.
This metadata will be visible, and properly attributed to data.gov.

### User-Contributed Data Collections
Domain experts often work with data that comes from a number of different sources. We will now support
Users creating collections that tie these disparate sources together, allowing users to add metadata that
describes the contents & purpose of a collection of data. These collections can then be exported as Bags
& Packages.

### Automated, Selective Bag & Package Creation
A new service will automate the process of exporting collections of data in a number of formats, as well as
tracking updates to these collections. The first supported format will be automatically generated Bag-It Bags
(our current standard), with planned support for Dat data packages, & the Open Knowledge Foundation Data Package
Format.
