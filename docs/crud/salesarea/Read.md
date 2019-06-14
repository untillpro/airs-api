[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.

**Get course data with specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/salesarea?id=123456&location=1
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
                "id": 5000000081,
                "state": 1,
                "name": "Taverne",
                "hq_id": "Taverne",
                "bmanual": 0,
                "number": 1,
                "close_manualy": 0,
                "auto_accept_reservations": 0,
                "only_reserved": 0,
                "group_vat_level": 0,
                "price": {  // expanded from id_prices
                    "id": 5000000067,
                    "state": 1,
                    "name": "Normaal",
                    "hq_id": "Normal",
                    "number": 0
                }, // link to 'pricelevels' entity
                "price_original": null, // expanded from 'id_prices_original'
                "ml_name": null,
                "exception": [
                    {
                        "period": { // expanded from exception.id_periods
                            "id": 5000000023,
                            "name": "Happy Hour",
                            "hq_id": "Happy Hour",
                            "state": 0,
                            "ml_name": null
                        }, 
                        "price": { // expanded from exception.id_prices
                            "id": 5000000067,
                            "state": 1,
                            "name": "Normaal",
                            "hq_id": "Normal",
                            "number": 0
                        } 
                    },
                    ...
                ],
                "range": [
                    {
                        "range_from": 1,
                        "range_to": 100
                    },
                    ...
                ]
            },
            ...
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