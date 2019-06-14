[← Back](README.md)

## Request: 

```http
POST https://air.untill.com/api/air-bo/1/course HTTP/1.1
content-type: application/json

{
    "state": 1 | 0,
    "data": {
        "name": "Bar",
        "hq_id": "Bar" | null,
        "changable": 0,
        "coursenumber": 0,
        "separate": 0,
        "ask_to_change": 0
        "ml_name": { ... }
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": 1234 // created item id
}
```

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)