# Introduction

This document describes a way to send modification/view requests to unTill Air cluster

# Site Structure

- /
  - Air Shell
- /api
  - Queues
- /plugins
  - Air Shell plugins

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

`<proto>://<site>/api/<queue-alias>/<partition-dividend>/<resource-name>/<resource-id>`

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
  - `air.untill.com/api/air-bo/678/articles.v2`
  - `air.untill.com/api/air-bo/678/articles2`


# Requests Examples

## Configuring BO

  - New/Edit article: `POST air.untill.com/api/airs-bp/678/conf`
    - ID is always passsed as a part of body
    - Negative ID means `insert` operation
  - Add POS operation: `POST air.untill.com/api/airs-bp/678/ops`
  - Special operation: `POST air.untill.com/api/airs-bp/678/<operation>`

## Viewing BO

```json
POST /api/air-bo-view/articles
content-type: application/json

{"location":[2],"show_deleted":1,"page":1,"page_size":20}
```

```json
POST /api/air-bo-view/articles
content-type: application/json

{"entries":[{"id":5000000158,"location":2}]}
```

## Available Modules

- Get list of available module manifests
  - `GET air.untill.com/api/modules/manifests`
- Get module index.html
  - `GET air.untill.com/api/modules/content/untillpro.md-mermaid-renderer/index.html`


## Module Config

- Get config, JSON
  - `GET air.untill.com/api/users-view/config/untillpro.md-mermaid-renderer`
- Save config, JSON
  - `POST air.untill.com/api/users/config/<module-id>`

# Links

- https://www.moesif.com/blog/technical/api-design/REST-API-Design-Filtering-Sorting-and-Pagination
  - `?filters[date][gte]=2018-04-01&filters[date][lte]=2018-04-31&filters[status][eq]=active`
- https://restfulapi.net/resource-naming/
  - Do not use underscores ( _ )
- https://restdb.io/docs/querying-with-the-api
- https://en.wikipedia.org/wiki/Representational_state_transfer
