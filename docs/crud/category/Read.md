[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get category data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/category?id=123456&location=1
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
            },
            "654": {
                "name": "Location 654"
            },
        },
        "data" : {
            "1": { // location id
                "id": 123456,
                "name": "Bar",
                "hq_id": "Bar",
                "state": 0,
                "ml_name": Blob
            },

            "44": { // location id
                "id": 2334231,
                "name": "Bar 1",
                "hq_id": "Bar",
                "state": 0,
                "ml_name": Blob
            }

            "654": { // location id
                "id": 654321,
                "name": "Bar 2",
                "hq_id": "Bar",
                "state": 1,
                "ml_name": Blob
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