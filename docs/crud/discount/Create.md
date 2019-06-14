[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/discount HTTP/1.1
content-type: application/json

{
    "state": 1 | 0,
    "data": {
        "name": String,
        "hq_id": String,
        "num": Number,

        "discount_type": Number,
        "value_type": Number,
        "discount_value": Number,
        "free_reason_type": Number,
        "free_reason_text": String,

        "id_periods": Number, // link to 'courses' entity
        "id_discount_reasons": Number, // link to 'discountreason' entity

        "check_type": Number,
        "id_department": Number, // link to 'department' entity
        "id_foor_group": Number, // link to 'foodgroup' entity
        "id_category": Number, // link to 'category' entity
        "id_courses": Number, // link to 'courses' entity

        "color": Number,
        "font_color": Number,
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