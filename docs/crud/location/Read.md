[← Back](README.md)

## Request: 

```javascript
GET https://air.untill.com/api/air-bo-view/locations?id=1
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