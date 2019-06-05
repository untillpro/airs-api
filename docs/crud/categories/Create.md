[← Back](README.md)

## Request: 

```http
POST https://air.untill.com/api/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "state": 1 | 0,
    "data": {
        "name": "Bar",
        "hq_id": "Bar" | null,
        "ml_name": { ... }
    }
}
```

## Response: 

If success:

```javascript 
    {
        "id": 1234567 //created category id
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

curl -v -d {\"state\":1,\"abcd\":{\"name\":\"Bar2\",\"hq_id\":\"Bar\",\"ml_name\":{\"eng\":\"Bar\"}}} -H "Content-type: application/json" http://kvvw10:8822/air-bo/1/category