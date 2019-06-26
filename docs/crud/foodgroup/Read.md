[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.

**Get food group data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/foodgroup?id=123456&location=1
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
                "name": "Location 1",
                "categories": [...], // array of 'category' entity in that location, //why you need this here?
            },
            "44": {
                "name": "Location 44",
                "categories": [...], // array of 'category' entity in that location, //why you need this here?
            }
        },
        "data" : {
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
                "state": 1,
                ...,
                "category" : { // expanded from 'id_category'
                    "id": Number,
                    "state": Number,
                    "name": String,
                    "hq_id": String,
                    "ml_name": Blob
                },
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