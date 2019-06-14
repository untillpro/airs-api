[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/payment HTTP/1.1
content-type: application/json

{
    "state": 1,
    "data": {
        "number": Number,
        "name": String,
        "hq_id": String,
        "kind": Number,
        "id_currency": Number, // link to 'currency' entity
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number //created item id
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