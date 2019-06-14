[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get payment data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/payment?id=123456&location=1
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
                "name": "Location 1",
                "currencies": [...], // array of 'currency' entity in that location,
            },
            "44": {
                "name": "Location 44",
                "currencies": [...], // array of 'currency' entity in that location,
            }
        },
        "data" : {
            "1": { // location id
                "state": 1,
                "id": 5000000021,
                "number": 1,
                "name": "Cash",
                "hq_id": "Cash",
                "kind": 0,
                "currency": { // expanded from 'id_currency'
                    "state": 1,
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
                }
            },

            "44": { // location id
                ...
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