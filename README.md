# Data Together Technical Roadmap & Service Overview

[![GitHub](https://img.shields.io/badge/project-Data_Together-487b57.svg?style=flat-square)](http://github.com/datatogether)
[![Slack](https://img.shields.io/badge/slack-Archivers-b44e88.svg?style=flat-square)](https://archivers-slack.herokuapp.com/)

![services list](diagrams/services-list.png)

** **
## Looks great! How are you progressing?

Awww, thanks. We track progress in our [`roadmap`](./docs/roadmap.md), go check it out.

** **
## What's a service?

When we say _service_, we actually mean a _microservice server running in concert with other services_. All of the services that we define end up being run as a cluster of networked containers. Each of our services have a few common characteristics:

### `server.go` defines `main()`
The best place to start reading about any service is to open its `server.go` file. All go programs (that aren't packages) define `func main()` as their starting point, and for us that's always defined in `server.go`. Often you'll see a function called `NewServerRoutes` that defines any and all outward-facing http endpoints. These endpoints define what the service can do, and working backward from there is a great way to understand a service.

### `config.go` determines config via ENV variables, using the `config` package
All services support at least some degree of configuration via a `config` struct defined in a file called `config.go`. Services use the config package to extract the values of this configuration from environment variables, mapping `config.FieldName` in the service to an all-caps-snake-case `FIELD_NAME` environment variable. More info can be found in the [config package](https://github.com/datatogether/config).

### logging with `logrus` package
[Logrus](https://github.com/sirupsen/logrus) is our logger of choice. We follow [Dave Cheney's Advice](https://dave.cheney.net/2015/11/05/lets-talk-about-logging) when it comes to logging, using only `log.info` and `log.debug` commands.

### vendored dependencies via `godep`
We support the idea of reproducible builds, and as such _vendor_ (that is, write copies) all of our dependencies into version control. This means that it should be possible to rewind git history to any point in time, run `go build` and get a functioning binary (presuming the build process worked at that point in time). [godep](https://github.com/tools/godep) is what we're currently using, but we're keeping a close eye on [dep](https://github.com/golang/dep), as a potential replacement.

### Containerized
Services are always shipped as docker images.

### Shipped via passing CI tests merged into master
The last step of a passing CI test is to build & push a new docker image to docker hub with the `latest` tag.

### `request` & `handler` patterns
To perform the work of handling a request, all servers register a "handler" function that often delegates the majority of their work to a "request" function to actually to the thing in question. This pattern is for a few reasons, first & foremost, each request defines whatever parameters it accepts as a struct, giving clear documentaiton of ways to modify the request. Secondly request functions satisfy the form specified by the `rpc` package. By isolating business logic in request functions, we provide strong garuntees that behaviour will be the same for http handlers & rpc requests, while also providing a clear abstraction for testing.

### Communicates with other services via RPC
Services need to talk to each other, they do so via a package called `rpc` that allows us to call go functions on another service without having to worry about

### Use go-datastore interface for storing data
When storing information, we often go to great lengths to accept the ipfs-datastore interface as a point of storage, this is intended as future-proofing for an eventual transition to distributed versions of these same services, and allowing interchangability of the underlying datastore.


** ** 
## Production

We use [kubernetes](https://kubernetes.io) in production to orchestrate containers. Contact [b5](https://github.com/b5) if you'd like to chat production details.


** **
## Running The Data Together platform locally

The best way to get data together running locally is to clone the [context repo](https://github.com/datatogether/context) and use `docker-compose` to spin up all the necessary backend services. `docker-compose up` will download all the necessary data together images in a single terminal, hook them together via networking, and will spin up a dev version of the webapp to interact with the platform. Many other services come with `docker-compose.yml` files that outline the miniumum number of other services needed to make a sensible working version of the host service.


** **
## Repo Links
Each repository should carry with it its own roadmap, defined by milestones. Check each repo's `README.md` for details

* [**api**](https://github.com/datatogether/api)
* [**archive**](https://github.com/datatogether/archive)
* [**archivertools**](https://github.com/datatogether/archivertools)
* [**cdxj**](https://github.com/datatogether/cdxj)
* [**config**](https://github.com/datatogether/config)
* [**content**](https://github.com/datatogether/content)
* [**coverage**](https://github.com/datatogether/coverage)
* [**extract_href**](https://github.com/datatogether/extract_href)
* [**ffi**](https://github.com/datatogether/ffi)
* [**identity**](https://github.com/datatogether/identity)
* [**ipfs**](https://github.com/ipfs/go-ipfs)
* [**linked_data**](https://github.com/datatogether/linked_data)
* [**patchbay**](https://github.com/datatogether/patchbay)
* [**postgres**](https://github.com/postgres/postgres)
* [**rabbitmq**](https://github.com/rabbitmq/rabbitmq-server)
* [**redis**](https://github.com/antirez/redis)
* [**sentry**](https://github.com/datatogether/sentry)
* [**sql_datastore**](https://github.com/datatogether/sql_datastore)
* [**sql_util**](https://github.com/datatogether/sql_util)
* [**task-mgmt**](https://github.com/datatogether/mgmt)
* [**warc**](https://github.com/datatogether/warc)
