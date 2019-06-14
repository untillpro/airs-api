[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/paneltab
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/paneltab?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/paneltab?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/paneltab?page=1&pagesize=50
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
            "Payment": { 
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
            },
            ...  
        }
    }
}
```

- `location` object contains of all locations, for what option was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)