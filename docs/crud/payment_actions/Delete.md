[← Back](README.md)

## Request:

```http
PUT https://air.untill.com/api/air-bo/1/payment_actions HTTP/1.1
content-type: application/json

{
    "id": [number],
}
```

## Response: 

If success:

```javascript
{
    {
        "Status": "Ok",
        "StatusCode": 200,
        "Data": [ 123, 4324, 5435 ] //array of ids of removed items
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