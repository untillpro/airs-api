[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/foodgroup
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/foodgroup?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/foodgroup?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/foodgroup?page=1&pagesize=50
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
            "Zonder Alcohol": { 
                "1": { // location id
                    "id": 123,
                    "state": 1,
                    ...,
                    "category" : { // expanded from 'id_category'
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                        "ml_name": Blob
                    },
                },

                "44": { // location id
                    "id": 234,
                    "state": 0,
                    
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