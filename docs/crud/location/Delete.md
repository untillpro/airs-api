[← Back](README.md)

## Request: 

```javascript
DELETE https://air.untill.com/api/air-bo-view/locations HTTP/1.1
content-type: application/json

{
    "id": 1
}
```

## Response: 

If delete was success returns `id` of removed location:

```json
{
    "id": 1
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