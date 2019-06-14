[← Back](README.md)

## Request: 

```http
POST https://air.untill.com/api/air-bo/1/department HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "name": "Alcohols",
        "hq_id": "Alcohols",
        "dep_number": 10,
        "max_supp_quantity": 5,
        "max_cond_quantity": 5,
        "ml_name": { ... },
        "id_foodgroup": 1234567,
        "id_options_supplement": 2345678,
        "id_options_condiment": 3456789,
        "button": {
            "text": "Alcohols",
            "color": <Number>,
            "font_color": <Number>,
        },
        "available": [
            <sales area ids>
        ]
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": 1234 // new department id
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