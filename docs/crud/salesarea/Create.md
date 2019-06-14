[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/salesarea HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "name": String,
        "hq_id": String,
        "bmanual": Number,
        "number": Number,
        "close_manualy": Number,
        "auto_accept_reservations": Number,
        "only_reserved": Number,
        "group_vat_level": Number,
        "id_prices": Number, // link to 'pricelevels' entity
        "id_prices_original": Number, // link to 'pricelevels' entity
        "ml_name": Blob
        "exception": [
            {
                "id_periods": Number, // link to 'period' entity
                "id_prices": Number // link to 'pricelevel' entity
            },
            ...
        ],
        "range": [
            {
                "range_from": Number,
                "range_to": Number
            },
            ...
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
    "Data": Number // created sales area id
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