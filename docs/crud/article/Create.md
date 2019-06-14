[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/articles HTTP/1.1
content-type: application/json

{
    "data": {
        "name": String,
        "hq_id": String,
        "id_department": Number, // link to 'department' entity
        "id_course": Number, // link to 'course' entity
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