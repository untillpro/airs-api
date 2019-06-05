[← Back](README.md)

## Requests:

**All category request**
```http
GET https://api.air.untill.com/air-bo-view/category
```

**With specified location:**

```http
GET https://api.air.untill.com/air-bo-view/category?location=1
```

**With multy-location:**

```http
GET https://api.air.untill.com/air-bo-view/category?location[]=1&location[]=44&location[]=654
```

**Specified page and pagesize**
```http
GET https://api.air.untill.com/air-bo-view/category?page=1&pagesize=50
```
Used in case of serverside paggination.

##Response example

If success:

```javascript
    {
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
        "total": 47,
        "items": {  //grouped by HQ_ID (or NAME if HQ_ID)
            "Bar": { 
                "1": { // location id
                    "id": 123456,
                    "name": "Bar",
                    "hq_id": "Bar",
                    "state": 0,
                    "ml_name": {...}
                },

                "44": { // location id
                    "id": 2334231,
                    "name": "Bar 1",
                    "hq_id": "Bar",
                    "state": 0,
                    "ml_name": {...}
                }

                "654": { // location id
                    "id": 654321,
                    "name": "Bar 2",
                    "hq_id": "Bar",
                    "state": 1,
                    "ml_name": {...}
                }
            },
            ...  
        }
    }
```

- `location` object contains of locations, for what category was selected.

In other case returns errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)