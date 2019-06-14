[← Back](README.md)

## Request: 

```http
PATCH https://air.untill.com/api/air-bo/1/payment_actions HTTP/1.1
content-type: application/json

{
    "id": [number],
    "state": Number
    "data": {
        [data fields]
    }
}
```

`id` - required param
`state` - new state of item
`[data fields]` - any of data fields described in [Create.md](Create.md)

## Response: 

If success:

```javascript 
    {
        "id": [ ... ] //updated payment actions id 
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