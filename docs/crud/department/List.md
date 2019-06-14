[← Back](README.md)

## Requests:

**All department request**
```javascript
GET https://air.untill.com/api/air-bo-view/department
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/department?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/department?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/department?page=1&pagesize=50
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
            "4": {
                "name": "Location 4",
            }
        },
        "data": {  //grouped by HQ_ID 
            "Frisdranken": { 
                "1": { // location id
                    "id": 123,
                    "state": 1,

                    ...,
                    
                    "available": [ // expanded from department_available
                        {
                            "id": 8888888,
                            "state": 1,
                            "name": "Taverne",
                            "hq_id": "Taverne",
                            "bmanual": 0,
                            "number": 10,
                            "close_manualy": 0,
                            "auto_accept_reservations": 0,
                            "only_reserved": 0,
                            "group_vat_level": 10,
                            "id_prices": 9999999,
                            "id_prices_original": 8888888,
                            "ml_name": { ... }
                            
                        },
                        ...
                    ],
                    "foodgroup": { //expaned from id_foodgroup
                        "id": 123456,
                        "state": 1,
                        "name": "Alcohols",
                        "hq_id": "Alcohols",
                        "gr_number": 10,
                        "id_category" : 123456 
                        "group_vat": 0,
                        "group_vat_sign": "",
                        "sec_group_vat": 0,
                        "sec_group_vat_sign": "",
                        "group_type": 0,
                        "ml_name": {...}
                    },
                    "options_supplement": { // expaned from id_options_supplement
                        "id": 234567,
                        "state": 1,
                        "name": "Beer plugins",
                        "hq_id": "Beer plugins",
                        "opt_number": 10,
                        "option_type": 0,
                        "has_parent_articles": 0,
                        "single_prep": 0,
                        "ml_name": { ... },
                        "option_articles": [ ... ], //array of IDs
                        "option_available": [ ... ] //array of IDs
                    },
                    "options_condiment": { // expaned from id_options_condiment
                        "id": 3456576,
                        "state": 1,
                        "name": "Optie Bieren",
                        "hq_id": "Optie Bieren",
                        "opt_number": 10,
                        "option_type": 0,
                        "has_parent_articles": 0,
                        "single_prep": 0,
                        "ml_name": { ... },
                        "option_articles": [ ... ], //array of IDs
                        "option_available": [ ... ] //array of IDs
                    }
                },
                ...
            },
            ...
        }
    }
}
```

- `location` object contains of all locations, for what department was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)