[← Back](README.md)

## Request: 

```http
POST https://api.air.untill.com/air-bo/1/articles HTTP/1.1
content-type: application/json

{
    "data": {
        "name": "Latte",
        "hq_id": "Latte" | null,
        "department": [department id],
        "course": [course id],
        "price": [
            {
                "price_id": [price id],
                "value": [number],
                "currency": [currency id],
                "vat": [number]
            },
        ],
        "appearance": [
            ...
        ],
        "options": [
            ...
        ],
        ...
    }
}
```

## Response: 

If success:

```javascript 
    {
        "id": [ "???" ] //created articles id or read-like data?
    }
```

In other case returns errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)