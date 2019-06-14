Что я хочу получать с сервера (в таком же виде буду отдавать на сервер для адпейта или записи):
```javascript
{
    "id": Number,
    "state": Number,
    "name": String,
    "hq_id": String,
    "gr_number": Number,
    "category": {
        "id": Number,
        "name": String
    },
    "group_vat": Number,
    "group_vat_sign": String,
    "sec_group_vat": Number,
    "sec_group_vat_sign": String,
    "group_type": Number,
    "ml_name": Blob
}
```

Что я передаю на сервер:

```javascript
{
    "id": Number,
    "state": Number,
    "data": {
        "name": String,
        "hq_id": String,
        "gr_number": Number,
        "category": {
            "id": Number,
            "name": String
        },
        "group_vat": Number,
        "group_vat_sign": String,
        "sec_group_vat": Number,
        "sec_group_vat_sign": String,
        "group_type": Number,
        "ml_name": Blob
    }
}
```

В каком виде это должно храниться в блобе:
```javascript
{
    "name": String,
    "hq_id": String,
    "gr_number": Number,
    "id_category": Number, // <-- 
    "group_vat": Number,
    "group_vat_sign": String,
    "sec_group_vat": Number,
    "sec_group_vat_sign": String,
    "group_type": Number,
    "ml_name": Blob
}
```

То есть весь блок `category` из блоба убирается и добаялвется `id_category: category.id`