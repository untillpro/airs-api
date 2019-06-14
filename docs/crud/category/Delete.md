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
    "Status": "Ok",
    "StatusCode": 200,
    "Data": [ ... ] // updated items id array
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