[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/department HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "name": String,
        "hq_id": String,
        "dep_number": Number,
        "max_supp_quantity": Number,
        "max_cond_quantity": Number,
        "ml_name": Blob,
        "id_foodgroup": Number, // link to `foodgroup` entity
        "id_options_supplement": Number, // link to `option` entity
        "id_options_condiment": Number, // link to `option` entity
        "button": {
            "text": String,
            "color": Number,
            "font_color": Number,
        },
        "department_available": [ // array of `salesarea` entity ids
            Number 
        ],
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
    "Data": Number // new department id
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