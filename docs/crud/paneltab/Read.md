[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.


**Get tab data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/paneltab?id=123456&location=1
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
                "id": 25000097493,
                "state": 1,
                "name": "Payment",
                "hq_id": "Payment",
                "num": 2,
                "ml_name": Blob,
                "buttons": [
                    {
                        "button_code": "pay",
                        "button_text": "Payment",
                        "action_data": null,
                        "num": 0,
                        "type": null,
                        "ml_name": null,
                    },
                    {
                        "button_code": "discount",
                        "button_text": "Discount",
                        "action_data": null,
                        "num": 1,
                        "type": null,
                        "ml_name": null,
                    },
                ]
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