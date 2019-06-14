[← Back](README.md)

## Requests:

**All category request**
```javascript
GET https://air.untill.com/api/air-bo-view/payment
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/payment?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/payment?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/payment?page=1&pagesize=50
```
Used in case of serverside paggination.

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
                "name": "Location 44",
            }
        },
        "data": {  //grouped by HQ_ID 
            "Euro": { 
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
                    }, 
                },

                "44": { // location id
                    ...
                }
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what currency was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)