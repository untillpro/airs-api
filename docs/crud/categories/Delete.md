[← Back](README.md)

## Request:

```http
PUT https://api.air.untill.com/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "id": [number],
    "state": 0 | 1 | 2
}
```

## Response: 

If success:

```javascript
{
    "id": 123456 // updated item id
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