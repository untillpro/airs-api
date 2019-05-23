[← Back](README.md)

## Request: 

```http
PATCH https://api.air.untill.com/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "id": 123456,
    "data": {
        "name": "New Bar",
        "state": 1
    }
}
```

`id` - required param
`[data fields]` - any of data fields described in [Create.md](Create.md)

## Response: 

If success:

```javascript 
    {
        "id": 123456 //updated category id
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