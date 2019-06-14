[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get price level data with specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/pricelevel?id=123456&location=1
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
                "id": 5000000067,
                "state": 1,
                "name": "Normaal",
                "hq_id": "Normal",
                "number": 0
            },

            "44": { // location id
                "id": 5000000068,
                "state": 1,
                "name": "Normal",
                "hq_id": "Normal",
                "number": 0
            }

            "654": { // location id
                "id": 5000000069,
                "state": 1,
                "name": "Common",
                "hq_id": "Normal",
                "number": 0
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