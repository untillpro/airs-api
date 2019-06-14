[← Back](README.md)

## Requests:

**All department request**
```http
GET https://air.untill.com/api/air-bo-view/department
```

**With specified location:**

```http
GET https://air.untill.com/api/air-bo-view/department?location=1
```

**With multy-location:**

```http
GET https://air.untill.com/api/air-bo-view/department?location=1&location=44&location=654
```

**Specified page and pagesize**
```http
GET https://air.untill.com/api/air-bo-view/department?page=1&pagesize=50
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
            "4": {
                "name": "Location 4",
            }
        },
        "data": {  //grouped by HQ_ID (or NAME if HQ_ID)
            "Frisdranken": { 
                "1": { // location id
                    "id": 123,
                    "state": 1,
                    ...,
                    "available": [ //
                        {
                            n
                        },
                    ]
                },

                "4": { // location id
                    "id": 234,
                    "state": 1,
                    "name": "Frisdranken1",
                    "hq_id": "Frisdranken" | null,
                    "changable": 0,
                    "departmentnumber": 0,
                    "separate": 0,
                    "ask_to_change": 0
                    "ml_name": { ... }
                }
            },
            ...
        }
    }
}
```

- `location` object contains of locations, for what department was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)