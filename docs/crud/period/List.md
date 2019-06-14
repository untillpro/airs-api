[← Back](README.md)

## Requests:

**All category request**
```javascript
GET https://air.untill.com/api/air-bo-view/period
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/period?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/period?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/period?page=1&pagesize=50
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
            "Happy Hour": { 
                "1": { // location id
                    "id": 5000000023,
                    "name": "Happy Hour",
                    "hq_id": "Happy Hour",
                    "state": 0,
                    "ml_name": null
                },

                "44": { // location id
                    "id": 5000000024,
                    "name": "Happy Hour 1",
                    "hq_id": "Happy Hour",
                    "state": 0,
                    "ml_name": null
                }

                "654": { // location id
                    "id": 5000000025,
                    "name": "Happy Hour 2",
                    "hq_id": "Happy Hour",
                    "state": 1,
                    "ml_name": null
                }
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what category was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)