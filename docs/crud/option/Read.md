[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.


**Get option data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/option?id=123456&location=1
```

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
                "name": "Location 44"
            }
        },
        "data" : {
            "1": { // location id
                "id": 5000000105,
                "state": 1,
                "name": "Optie Campari",
                "hq_id": "Optie Campari",
                "opt_number": 10,
                "option_type": 0,
                "has_parent_articles": 0,
                "single_prep": 0,
                "ml_name": null,
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
        }
    }
}
```

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)