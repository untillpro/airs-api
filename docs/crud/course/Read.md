[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.

**Get course data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/course?id=123456&location=1
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
                "id": 123,
                "state": 1,
                "name": "Frisdranken",
                "hq_id": "Frisdranken" | null,
                "changable": 0,
                "coursenumber": 0,
                "separate": 0,
                "ask_to_change": 0
                "ml_name": Blob
            },

            "44": { // location id
                "id": 234,
                "state": 1,
                "name": "Frisdranken1",
                "hq_id": "Frisdranken" | null,
                "changable": 0,
                "coursenumber": 0,
                "separate": 0,
                "ask_to_change": 0
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