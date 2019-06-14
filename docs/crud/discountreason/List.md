[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/discountreason
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/discountreason?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/discountreason?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/discountreason?page=1&pagesize=50
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
            }
        },
        "data": {  //grouped by HQ_ID 
            "discount #1": { 
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
                    "state": 0,
                    "name": "Too cold",
                    "hq_id": "Too cold",
                    "number": 0,
                    "r_type": 0,
                    "ml_name": Blob
                }
            },

            ...  
        }
    }
}
```

- `location` object contains of all locations, for what reason was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)