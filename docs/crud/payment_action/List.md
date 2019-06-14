[← Back](README.md)

## Requests:

**All payment_actions request**
```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?page=1&pagesize=50
```

**Specified order**
```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?order_by[name]=asc
```

**Multy ordering**
```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?order_by[name]=asc&order_by[location]=desc
```

**Specified status**
```javascript
GET https://air.untill.com/api/air-bo-view/payment_actions?show_deleted=1
```

##Response example

If success:

```javascript
    {
        {
            "Status": "Ok",
            "StatusCode": 200,
            "Data": {
                "locations": { //all selected locations
                    "1": {
                        "name": "Location 1",
                    },
                    "4": {
                        "name": "Location 4",
                    },
                    "7": {
                        "name": "Location 7",
                    }
                },
                "data": {  //grouped by HQ_ID
                    "Pay cash": { 
                        "1": { // location id
                            "id": 123,
                            "state": 1,
                            "num": 0,
                            "name": "Pay",
                            "hq_id": "Pay cash",
                            "button_code": "pay_cash",
                            "button_text": "Pay",
                            "action_data": "",
                            "type": 0,
                            "ml_name": null
                        },

                        "4": { // location id
                            "id": 234,
                            "state": 1,
                            "num": 0,
                            "name": "Pay with cash",
                            "hq_id": "Pay cash",
                            "button_code": "pay_cash",
                            "button_text": "Pay cash",
                            "action_data": "",
                            "type": 0,
                            "ml_name": null
                        }
                    },
                    "Split by part": { 
                        "1": { // location id
                            "id": 321,
                            "state": 1,
                            "num": 0,
                            "name": "Split",
                            "hq_id": "Split by part",
                            "button_code": "split_by_part",
                            "button_text": "Split",
                            "action_data": "",
                            "type": 0,
                            "ml_name": null
                        },

                        "7": { // location id
                            "id": 543,
                            "state": 1,
                            "num": 0,
                            "name": "Split",
                            "hq_id": "Split by part",
                            "button_code": "split_by_part",
                            "button_text": "Split",
                            "action_data": "",
                            "type": 0,
                            "ml_name": null
                        }
                    },
                    ...
                }
            }
        }
    }
```

- `location` object contains of all locations, for what payment actions was selected.
- each `location` in list has all needed data, scpecified by location and that can be used to display `data` entities. In result above this is `name` prop.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)