[← Back](README.md)

## Requests:

`id` - required. 
`location` - required.

**Get discount data with specified location:**

```
GET https://air.untill.com/api/air-bo-view/discount?id=123456&location=1
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
                "periods": [...], // array of 'period' entity in that location,
                "discount_reasons": [...], // array of 'discountreason' entity in that location,
                "departments": [...], // array of 'department' entity in that location,
                "foor_groups": [...], // array of 'foodgroup' entity in that location,
                "categories": [...], // array of 'category' entity in that location,
                "courses": [...], // array of 'course' entity in that location,
            },
            "44": {
                "name": "Location 44",
                "periods": [...], // array of 'period' entity in that location,
                "discount_reasons": [...], // array of 'discountreason' entity in that location,
                "departments": [...], // array of 'department' entity in that location,
                "foor_groups": [...], // array of 'foodgroup' entity in that location,
                "categories": [...], // array of 'category' entity in that location,
                "courses": [...], // array of 'course' entity in that location,
            }
        },
        "data" : {
            "1": { // location id
                "id": 123,
                    "state": 1,
                    "name": "selected elemens with 10%",
                    "hq_id": "discount #1",
                    "num": 0,

                    "discount_type": 1,
                    "value_type": 1,
                    "discount_value": 10,
                    "free_reason_type": 0,
                    "free_reason_text": "Free reason text",

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
                "state": 1,
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
    "Data": "Error text"
}
```

[← Back](README.md)