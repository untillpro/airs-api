[← Back](README.md)

## Request: 

```http
GET https://api.air.untill.com/air-bo-view/locations?id=1
```

## Response:

If location exists will return its data:

```javascript
{
    "id": 1,
    "name": "Location 1",
    ...
}
```

In other case will returns errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)