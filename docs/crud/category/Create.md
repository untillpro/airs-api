[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/category HTTP/1.1
content-type: application/json

{
    "state": Number, // 1 | 0
    "data": {
        "name": String,
        "hq_id": String,
        "ml_name": Blob
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number // updated item id
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