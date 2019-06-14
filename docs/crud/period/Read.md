[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get period data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/period?id=123456&location=1
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
                "id": 5000000023,
                "name": "Happy Hour",
                "hq_id": "Happy Hour",
                "state": 1
            },

            "44": { // location id
                "id": 5000000024,
                "name": "Happy Hour 1",
                "hq_id": "Happy Hour",
                "state": 0
            }

            "654": { // location id
                "id": 5000000025,
                "name": "Happy Hour 2",
                "hq_id": "Happy Hour",
                "state": 1
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