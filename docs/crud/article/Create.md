[← Back](README.md)

## Request: 

```javascript
POST https://air.untill.com/api/air-bo/1/articles HTTP/1.1
content-type: application/json

{
    "data": {
        "name": String,
        "hq_id": String,
        "id_department": Number, // link to 'department' entity
        "id_course": Number, // link to 'course' entity
        "id_appearance": [
            ... //links to `appearance` entity //what is appearance?
        ],
        "id_option": [
            ... //links to `option` entity
        ],
        ...
    }
}
```

## Response: 

If success:

```javascript 
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": Number // created item id
}
```

In other case returns errors:

```javascript
{
    "Status": "Status Text",
    "StatusCode": 400, //status code
    "Data": String
}
```

[← Back](README.md)