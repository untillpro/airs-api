[← Back](README.md)

## Request: 

```http
PATCH https://air.untill.com/api/air-bo/1/department HTTP/1.1
content-type: application/json

{
    "id": 123,
    "state": 0 | 1,
    "data": {
        [ data ]
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
    "Data": 123456 //updated department id
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