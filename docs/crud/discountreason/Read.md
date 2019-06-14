[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.

**Get reason data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/discountreason?id=123456&location=1
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
                "name": "Location 1",
            },
            "44": {
                "name": "Location 44",
            }
        },
        "data" : {
            "1": { // location id
                "id": 123,
                "state": 1,
                "name": "Too cold",
                "hq_id": "Too cold",
                "number": 0,
                "r_type": 0,
                "ml_name": Blob
            },

            "44": { // location id
                "id": 234,
                "state": 1,
                "name": "Too cold",
                "hq_id": "Too cold",
                "number": 0,
                "r_type": 0,
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
    "Data": "Error text"
}
```

[← Back](README.md)