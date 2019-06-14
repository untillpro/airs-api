[← Back](README.md)

## Requests:

`id` - required. If `id` param is not specified, request will follow [list request](List.md) logic.
`location` - required. 

**Get payment action data for all available locations**

```
GET https://air.untill.com/api/air-bo-view/payment_actions?id=123456&location=1
```

##Response example

If success:

```javascript
    {
        "locations": { //all selected locations
            "1": {
                "name": "Location 1"
            },
            "44": {
                "name": "Location 44"
            },
            "654": {
                "name": "Location 654"
            },
        },
        "data" : {
            "1": {
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
            "44": {
                "id": 234,
                "state": 1,
                "num": 0,
                "name": "Pay",
                "hq_id": "Pay cash",
                "button_code": "pay_cash",
                "button_text": "Pay cash",
                "action_data": "",
                "type": 0,
                "ml_name": null
            },
            "654": {
                "id": 345,
                "state": 0,
                "num": 0,
                "name": "Pay",
                "hq_id": "Pay cash",
                "button_code": "pay_cash",
                "button_text": "Pay with cash",
                "action_data": "",
                "type": 0,
                "ml_name": null
            },
        }
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