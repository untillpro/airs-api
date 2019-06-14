[← Back](README.md)

## Request:

```javascript
PUT https://air.untill.com/api/air-bo/1/pricelevel HTTP/1.1
content-type: application/json

{
    "id": [ Number ]
}
```

## Response: 

If success:

```javascript
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": [ Number ] // updated items id array
}
```

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)