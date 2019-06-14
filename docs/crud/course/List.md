[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/course
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/course?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/course?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/course?page=1&pagesize=50
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
            },
            "654": {
                "name": "Location 654",
            },
        },
        "data": {  //grouped by HQ_ID 
            "Frisdranken": { 
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
            },
            "Separate": { 
                "44": { // location id
                    "id": 345,
                    "state": 1,
                    "name": "Separate",
                    "hq_id": "Separate" | null,
                    "changable": 0,
                    "coursenumber": 0,
                    "separate": 0,
                    "ask_to_change": 0
                    "ml_name": Blob
                },

                "654": { // location id
                    "id": 456,
                    "state": 1,
                    "name": "Separate1",
                    "hq_id": "Separate" | null,
                    "changable": 0,
                    "coursenumber": 0,
                    "separate": 0,
                    "ask_to_change": 0
                    "ml_name": Blob
                }
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what course was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)