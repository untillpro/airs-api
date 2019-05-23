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

**Specified order**
```http
GET https://api.air.untill.com/air-bo-view/category?order_by[name]=asc
```

**Multy ordering**
```http
GET https://api.air.untill.com/air-bo-view/category?order_by[name]=asc&order_by[location]=desc
```

**Specified status**
```http
GET https://api.air.untill.com/air-bo-view/category?show_deleted=1
```
In this case category with status 2 will be also returned

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
        "items": {  //grouped by HQ_ID (or NAME if HQ_ID)
            "Ace": { 
                "1": { // location id
                    "id": 123456,
                    "name": "Bar",
                    "hq_id": "Bar",
                    "state": 0,
                    "ml_name": {
                        "eng": "Bar",
                        "rus": "Бар",
                        ...
                    }
                },

                "44": { // location id
                    "id": 2334231,
                    "name": "Bar 1",
                    "hq_id": "Bar",
                    "state": 0,
                    "ml_name": {
                        "eng": "Bar 1",
                        "rus": "Бар 1",
                        ...
                    }
                }

                "654": { // location id
                    "id": 654321,
                    "name": "Bar 2",
                    "hq_id": "Bar",
                    "state": 1,
                    "ml_name": {
                        "eng": "Bar 2",
                        "rus": "Бар 2",
                        ...
                    }
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