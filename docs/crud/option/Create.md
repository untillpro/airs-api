[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/option HTTP/1.1
content-type: application/json

{
    "state": Number // 1 | 0,
    "data": {
        "name": String,
        "hq_id": String,
        "opt_number": Number,
        "option_type": Number,
        "has_parent_articles": Number,
        "single_prep": Number,
        "ml_name": Blob,
        "option_articles": [ // array of 'article' entity ids
            Number
        ],
        "option_available": [ // array of 'salesarea' entity ids
            Number
        ]
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number // created option id
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