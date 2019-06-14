[← Back](README.md)

## Requests:

`id` - is required parameter. If `id` param is not specified, request will follow [list request](List.md) logic.

**Get department data for all available locations**
```
GET https://air.untill.com/api/air-bo-view/department?id=123456
```

**Get department data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/department?id=123456&location=1
```

**Get department data with multy-location:**

```
GET https://air.untill.com/api/air-bo-view/department?id=123456&location[]=1&location[]=44&location[]=654
```

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
                "name": "Location 44"
            }
        },
        "data" : {
            "1": { // location id
                "id": 123,
                "state": 1,
                "name": "Frisdranken",
                "hq_id": "Frisdranken" | null,
                "changable": 0,
                "departmentnumber": 0,
                "separate": 0,
                "ask_to_change": 0
                "ml_name": { ... }
            },

            "44": { // location id
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
        }
    }
}
```

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)