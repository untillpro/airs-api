[← Back](README.md)

## Requests:

**All category request**
```javascript
GET https://air.untill.com/api/air-bo-view/pricelevel
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/pricelevel?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/pricelevel?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/pricelevel?page=1&pagesize=50
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
            "Normal": { 
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
            },

            "Weekend": {
                ...
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what price level was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)