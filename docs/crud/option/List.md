[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/option
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/option?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/option?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/option?page=1&pagesize=50
```
Used in case of serverside paggination.

##Response example

If success:

```javascript
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": {
        "locations": { //all selected locations
            "1": {
                "name": "Location 1"
            },
            "44": {
                "name": "Location 44",
            }
        },
        "data": {  //grouped by HQ_ID 
            "Optie Campari": { 
                "1": { // location id
                    "id": 5000000105,
                    "state": 1,
                    "name": "Optie Campari",
                    "hq_id": "Optie Campari",

                    ...,

                    "articles": [ // expanded from 'option_articles'; array of 'article' entity.
                        { ... },
                        { ... },
                        ...
                    ],
                    "available": [ // expanded from 'option_available'; array of 'salesarea' entity.
                        { ... },
                        { ... },
                        ...
                    ]
                },

                "44": { // location id
                    ...
                }
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what option was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)