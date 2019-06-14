[← Back](README.md)

## Requests:

`id` - required.
`location` - required.

**Get department data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/department?id=123456&location=1
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
                "foodgroup": [...], // array of 'foodgroups' in that location
                "options": [...] // array of 'options' in that location
            },
            "44": {
                "name": "Location 44",
                "foodgroup": [...], // array of food groups in that location
                "options": [...] // array of 'options' in that location
            }
        },
        "data" : {
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