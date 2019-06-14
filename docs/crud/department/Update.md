[← Back](README.md)

## Request: 

```javascript
PATCH https://air.untill.com/api/air-bo/1/department HTTP/1.1
content-type: application/json

{
    "id": Number,
    "state": Number, // 0 | 1,
    "data": {
        ...
    }
}
```

`id` - required param
`state` - item new state
`data` - any of data fields described in [Create.md](Create.md)

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number //updated department id
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