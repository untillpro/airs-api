[← Back](README.md)

## Request: 

```http
POST https://api.air.untill.com/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "data": {
        "name": "Bar",
        "hq_id": "Bar" | null,
        "state": 1 | 0,
        "ml_name": { ... }
    }
}
```

## Response: 

If success:

```javascript 
    {
        "id": 1234567 //created category id
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