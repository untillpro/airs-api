# Introduction

This document describes a way to send modification/view requests to unTill Air cluster

# Queues

- Request always comes to a queue
- Queue types:

![](z-charts-queue-types.png)


Router has to be able to calculate `partition-number` for partitioned queues.

## Calculating Request `partition-number`

- Request has associated `partition-dividend` (e.g. restaurant number)
- Queue has associated `number-of-partitions` 
- `partition-number` = `partition-dividend` % `number-of-partitions` 
  - e.g. `35 = 635 % 100`
  - In other words `partition-number` is a remainder after `partition-dividend` by `number-of-partitions` division

![](z-charts-queue-types-ex.png)

# URL Path Segments

`<proto>://<site>/<queue-alias>/<partition-dividend>/<resource-name>/<resource-id>`

All parts are optional

`queue-alias`

- Omitted queue-name means request for list of possible queue aliases
  - Example `curl https://api.github.com`

`partition-dividend` 

- Contains only digits
- For non-party queues is not analyzed, everything after queue-alias passed to handler

`resource-name`

- The first character in `resource-name` must be an alphabet
- Missed `resource-name` means `help` request
- `help`
  - Without  `resource-id` returns list of resources
  - With `resource-id` describes given resource
- if resource becomes incompatible with previous version its name must be changed, say
  - `api.air.untill.com/air-bo/678/articles.v2`
  - `api.air.untill.com/air-bo/678/articles2`


# Requests Examples

## Configuring BO

  - New/Edit article: `POST/PATCH api.air.untill.com/air-bo/678/articles`
    - id is always passsed as a part of body
  - Doing something special with article: `POST api.air.untill.com/air-bo/678/articles.doSpecial`
    - id is always passsed as a part of body    

## Viewing BO

  - Get all articles from location 678
    - `GET api.air.untill.com/air-bo-view/678/articles`
    - `GET api.air.untill.com/air-bo-view/articles?location=678`
  - Get article with ID=5000002361 from location 678
    - `GET api.air.untill.com/air-bo-view/678/articles?id=5000002361`
    - `GET api.air.untill.com/air-bo-view/articles?location=678&id=5000002361`
  - Get special representation of article with ID=5000002361 from location 678
    - `GET api.air.untill.com/air-bo-view/678/articles/special?id=5000002361`
  - Get articles from locations 1 and 2 where name contains coca
    - `GET api.air.untill.com/air-bo-view/articles/?location[]=1&location[]=2&where[name][contains]=coca`
  - *Get list of resources from location 678* (?)
    - `GET api.air.untill.com/air-bo-view/678`

## Registering Sales

  - `POST air.untill.com/air-pos/678/journal`

## Password Authentication

- `GET/POST api.air.untill.com/registry/auth?usr=<user-name>&pwd=<password>`

## Modifying Registry

Registry is a single-party queue, so workspace is not specified

- `POST/PATCH api.air.untill.com/registry/workspaces`
- `POST/PATCH api.air.untill.com/registry/users`
- `POST/PATCH api.air.untill.com/registry/devices`
- `POST/PATCH api.air.untill.com/registry/applications`

## Available Modules

- Get list of available module manifests
  - `GET api.air.untill.com/modules/manifests`
- Get module index.html
  - `GET api.air.untill.com/modules/content/untillpro.md-mermaid-renderer/index.html`


## Module Config

- Get config, JSON
  - `GET api.air.untill.com/users-view/config/untillpro.md-mermaid-renderer`
- Save config, JSON
  - `POST api.air.untill.com/users/config/<module-id>`

# Links

- https://www.moesif.com/blog/technical/api-design/REST-API-Design-Filtering-Sorting-and-Pagination
  - `?filters[date][gte]=2018-04-01&filters[date][lte]=2018-04-31&filters[status][eq]=active`
- https://restfulapi.net/resource-naming/
  - Do not use underscores ( _ )
- https://restdb.io/docs/querying-with-the-api
- https://en.wikipedia.org/wiki/Representational_state_transfer
