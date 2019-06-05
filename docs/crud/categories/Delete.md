[← Back](README.md)

## Request:

```http
PUT https://air.untill.com/api/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "id": [number]
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