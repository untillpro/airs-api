[← Back](README.md)

## Request: 

```javascript
GET https://air.untill.com/api/air-bo-view/locations
```

## Response: 

```json
{
    "items": [
        {
            "id": 123,
            "name": "Location 1"
        },
        {
            "id": 321,
            "name": "Location 2"
        },
        {
            "id": 234,
            "name": "Location 3"
        }
    ]
}
```

If locations not specified will return object with empty `items` field:

```json
{
    "items": []
}
```

[← Back](README.md)