[← Back](README.md)

## Requests:

**All course request**
```javascript
GET https://air.untill.com/api/air-bo-view/discount
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/discount?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/discount?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/discount?page=1&pagesize=50
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
            "discount #1": { 
                "1": { // location id
                    "id": 123,
                    "state": 1,
                    
                    ...

                    "period": { // expanded from 'id_periods'
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                    } | null, 
                    "discount_reason": { // expanded from 'id_discount_reasons
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                        "number": Number,
                        "r_type": Number,
                    } | null, 

                    "check_type": 1,
                    "department": { // expanded from 'id_department
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                        "dep_number": Number,
                        "max_supp_quantity": Number,
                        "max_cond_quantity": Number,
                        "ml_name": Blob,
                        "id_foodgroup": Number, // link to `foodgroup` entity
                        "id_options_supplement": Number, // link to `option` entity
                        "id_options_condiment": Number, // link to `option` entity
                        "button": {
                            "text": String,
                            "color": Number,
                            "font_color": Number,
                        },
                        "department_available": [ // array of `salesarea` entity ids
                            Number 
                        ],
                        "ml_name": Blob
                    } | null, 
                    "foor_group": { // expanded from 'id_foor_group
                        "id": Number,
                        "state": Number,
                        "name": "Alcohols",
                        "hq_id": "Alcohols",
                        "gr_number": 10,
                        "id_category" : 123456
                        "group_vat": 0,
                        "group_vat_sign": "",
                        "sec_group_vat": 0,
                        "sec_group_vat_sign": "",
                        "group_type": 0,
                        "ml_name": Blob
                    } | null, 
                    "category": { // expanded from 'id_category
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                        "ml_name": Blob
                    } | null, 
                    "course": { // expanded from 'id_courses
                        "id": Number,
                        "state": Number,
                        "name": String,
                        "hq_id": String,
                        "changable": Number,
                        "coursenumber": Number,
                        "separate": Number,
                        "ask_to_change": Number
                        "ml_name": Blob
                    } | null, 

                    "color": 14477173,
                    "font_color": 16020339,
                    "ml_name": null
                },

                "44": { // location id
                    "id": 234,
                    "state": 0,
                    ...
                }
            },

            ...  
        }
    }
}
```

- `location` object contains of all locations, for what discount was selected.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": "Error text"
}
```

[← Back](README.md)