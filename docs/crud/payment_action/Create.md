[← Back](README.md)

## Request: 

```http
POST https://air.untill.com/api/air-bo/1/payment_actions HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "num": 0,
        "name": "Pay cash",
        "hq_id": "Pay cash",
        "button_code": "pay_cash",
        "button_text": "Pay cash",
        "action_data": "",
        "type": 0,
        "ml_name": {...},
        
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": [ ... ] //created items id
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