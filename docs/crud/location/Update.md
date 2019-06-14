[← Back](README.md)

## Request: 

```javascript
PATCH https://air.untill.com/api/air-bo-view/locations HTTP/1.1
content-type: application/json

{
    "id": 1,
    "data": {
        "name": "New location name",
        ...
    }
}
```

## Result: 

If update succes returns location with updated data:

```javascript
{
    "name": "New location name",
    ...
}
```

Or if errors occurs will return errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)