[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get currency data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/currency?id=123456&location=1
```


##Response example

If success:

```javascript
{
    "Status": "Ok",
    "StatusCode": 200,
    "Data": {
        "locations": { //all selected locations
            "1": {
                "name": "Location 1"
            },
            "44": {
                "name": "Location 44"
            }
        },
        "data" : {
            "1": { // location id
                "id": 5000000021,
                "name": "Euro",
                "hq_id": "Euro",
                "code": "EUR",
                "round": 2,
                "eurozone": 1,
                "rate": 1,
                "symbol": '$',
                "sym_alignment": 0,
                "digcode": 978,
                "round_down": 0
            },

            "44": { // location id
                "id": 5000000022,
                "name": "EU",
                "hq_id": "Euro",
                "code": "EUR",
                "round": 2,
                "eurozone": 1,
                "rate": 1,
                "symbol": '#',
                "sym_alignment": 0,
                "digcode": 978,
                "round_down": 0
            }
        }
    }
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