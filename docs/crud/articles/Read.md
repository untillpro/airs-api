[← Back](README.md)

## Requests:

`id` - is required parameter. If `id` param is not specified, request will follow [list request](List.md) logic.

**Get article data for all available locations**
```
GET https://air.untill.com/api/air-bo-view/articles?id=123456
```

**Get article data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/articles?id=123456&location=1
```

**Get article data with multy-location:**

```
GET https://air.untill.com/api/air-bo-view/articles?id=123456&location[]=1&location[]=44&location[]=654
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
        "prev": "123456", //prev item id
        "next": "654321", //next item id
        "data" : {
            "1": {
                // data
            },
            "44": {
                // data
            },
            "654": {
                // data
            },
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