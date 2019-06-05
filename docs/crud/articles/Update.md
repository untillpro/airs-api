[← Back](README.md)

## Request: 

```http
PATCH https://air.untill.com/api/air-bo/1/articles HTTP/1.1
content-type: application/json

{
    "id": [number],
    "data": {
        [data fields]
    }
}
```

`id` - required param
`location` - if empty all articles grouped by `HQ_ID` or `NAME` will be updated
`[data fields]` - any of data fields described in [Create.md](Create.md)

## Response: 

If success:

```javascript 
    {
        "id": [ "???" ] //updated articles id or read-like data?
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