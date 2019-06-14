[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/foodgroup HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "name": String,
        "hq_id": String,
        "gr_number": Number,
        "id_category" : Number // link to `category` entity
        "group_vat": Number,
        "group_vat_sign": String,
        "sec_group_vat": Number,
        "sec_group_vat_sign": String,
        "group_type": Number,
        "ml_name": Blob
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number // created item id
}
```

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)