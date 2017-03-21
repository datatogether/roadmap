# Service Story

In the beginning we needed to archive content (things like datasets, pdfs, databases, image collections, etc) as quickly as possible, so we started with a [chrome extension]() to nominate to the Internet Archive (IA). We needed to know what sites to look at, so we build a set of [agency primers]() to help prioritize our work. Primers were made by researching agency offices & the urls they lived at.

Then we realized there was a lot of stuff the IA couldn't get to, "uncrawlable content" so [DataRefuge]() was created as both a place to store data and a workflow for archiving. We worked from spreadsheets to target & identify content that needed archiving by tracking a url that lead to collections of content. Volunteers would download that content, document it, and upload it to DataRefuge. Shortly after, we built an [app]() to help manage the DataRefuge archiving process.

Along the way we realized that the sites we were looking at were changing, and we needed to track these changes. So website monitoring was born to compare snapshots of web pages at different points in time, looking for shifts in language.

Soon we realized that if we recorded the code that volunteers are writing to do this archiving in a uniform way, we could repeat it later to keep current records, and so [Miru]() was created to automate the execution of this volunteer-contributed archiving code.

At this point we started to look for ways to coordinate our efforts with other projects that are archiving content as well. In order to coordinate with other projects, we'd have to change the way we archive content, this time recording the relationship between a url & the content that it represented. [Archivers 2.0]() was created to capture this url-to-content relationship, record metadata about that content, and to publish the work our volunteers are doing to as many places as possible. 

In order to properly coordinate, archivers 2.0 needs to map the websites it's pulling content from. We realized that the website monitoring project needs these same maps & HTML to generate it's diffs, so we stared to integrate those projects.

While we were at it, it made sense to break the larger archivers app into smaller pieces for long-term maintenance & deduplication. [Identity]() was the first service created with this in mind to avoid having to create accounts everywhere.

This brings us to now.