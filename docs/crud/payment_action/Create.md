[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/payment_actions HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "num": Number,
        "name": String,
        "hq_id": String,
        "button_code": String,
        "button_text": String,
        "action_data": String,
        "type": Number,
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
    "Data": [ Number ] //created items id
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