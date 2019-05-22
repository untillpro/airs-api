[← Back](README.md)

## Request: 

```http
POST https://api.air.untill.com/air-bo-view/locations HTTP/1.1
content-type: application/json

{
    "data": {
        "name": "New location 1",
        "timezone": "MSK",
        ...
    }
}
```

## Response: 

Will return `id` of new location if creation was success:

```json
{
    "id": 1234
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