[← Back](README.md)

## Requests:

`id` - is required parameter. If `id` param is not specified, request will follow [list request](List.md) logic.

**Get category data for all available locations**
```
GET https://api.air.untill.com/air-bo-view/category?id=123456
```

**Get category data with specified location:**

```
GET https://api.air.untill.com/air-bo-view/category?id=123456&location=1
```

**Get category data with multy-location:**

```
GET https://api.air.untill.com/air-bo-view/category?id=123456&location[]=1&location[]=44&location[]=654
```

##Response example

If success:

```javascript
    {
        "locations": { //all selected locations
            "1": {
                "name": "Location 1"
            },
            "44": {
                "name": "Location 44"
            },
            "654": {
                "name": "Location 654"
            },
        },
        "data" : {
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
        }
    }
```

In other case returns errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)