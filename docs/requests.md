# Introduction

This document describes a way to send modification/view requests to unTill Air cluster

# Queues

- Request always comes to a queue
- Queue types:

![](z-charts-queue-types.png)


Router has to be able to calculate `partition-number` for partitioned queues.

## Calculating Request `partition-number`

- Request has associated `partition-dividend` (e.g. restaurant number)
- Queue has associated `number-of-partitions` 
- `partition-number` = `partition-dividend` % `number-of-partitions` 
  - e.g. `35 = 635 % 100`
  - In other words `partition-number` is a remainder after `partition-dividend` by `number-of-partitions` division

![](z-charts-queue-types-ex.png)

# URL Path Segments

`<proto>://<site>/api/<queue-alias>/<partition-dividend>/<resource-name>/<resource-id>`

All parts are optional

`queue-alias`

- Omitted queue-name means request for list of possible queue aliases
  - Example `curl https://api.github.com`

`partition-dividend` 

- Contains only digits
- For non-party queues is not analyzed, everything after queue-alias passed to handler

`resource-name`

- The first character in `resource-name` must be an alphabet
- Missed `resource-name` means `help` request
- `help`
  - Without  `resource-id` returns list of resources
  - With `resource-id` describes given resource
- if resource becomes incompatible with previous version its name must be changed, say
  - `air.untill.com/api/airs-bp/678/articles`


# Requests Examples

## Configuring BO

  - New article: `POST air.untill.com/api/airs-bp/678`, id's below zero
```json
{
  "operations": [
    {
      "id": -1234123,
      "type": "category",
      "data": {
        "name": "Bar",
        "hq_id": "Bar",
        "state": 1
      }
    },
    {
      "id": -12431541254124,
      "type": "prices",
      "data": {
        "name": "prs1",
        "hq_id": "prs1",
        "state": 1
      }
    },
    {
      "id": -1243154432,
      "type": "prices",
      "data": {
        "name": "prs2",
        "hq_id": "prs3",
        "state": 1
      }
    },
    {
      "id": -1231231313,
      "type": "periods",
      "data": {
        "name": "per1",
        "hq_id": "per1",
        "state": 1
      }
    },
    {
      "id": -12312,
      "type": "periods",
      "data": {
        "name": "per2",
        "hq_id": "per2",
        "state": 1
      }
    },
    {
      "id": -1243,
      "type": "sales_area",
      "data": {
        "id_prices": 5000000000001,
        "bmanual": 12,
        "name": "sa",
        "hq_id": "sa",
        "state": 1
      }
    },
    {
      "id": -1243123,
      "type": "sales_area_exceptions",
      "parent_id": -1243,
      "parent_type": "sales_area",
      "doc_id": -1243,
      "doc_type": "sales_area",
      "data": {
        "id_prices": 5000000000001,
        "id_periods": 5000000000003,
        "id_sales_area": 5000000000005,
        "name": "sae1",
        "hq_id": "sae1",
        "state": 1
      }
    },
    {
      "id": -12431235,
      "type": "sales_area_exceptions",
      "parent_id": -1243,
      "parent_type": "sales_area",
      "doc_id": -1243,
      "doc_type": "sales_area",
      "data": {
        "id_prices": 5000000000001,
        "id_periods": 5000000000003,
        "id_sales_area": 5000000000005,
        "name": "sae2",
        "hq_id": "sae2",
        "state": 1
      }
    }
  ]
}
```
  - To edit article need to pass real IDs and changed fields  

## Viewing BO

  - Show first 20 articles from location 678 without deleted
    - `POST air.untill.com/api/air-bo-view/articles`
    ```json
    {"location":[678],"show_deleted":1,"page":1,"page_size":20}
    ```
  - Show article with ID=5000000158 from location 678
    - `POST air.untill.com/api/air-bo-view/articles`
    ```json
    {"entries":[{"id":5000000158,"location":678}]}
    ```

## Registering Sales

  - `POST air.untill.com/airs-bp/678`
  ```json
  {
  "type": "pbill",
  "data": {
    "id": 0,
    "id_bill": 1,
    "id_untill_users": 2,
    "number": 3,
    "failurednumber": 4,
    "suffix": "str5",
    "pdatetime": "str6",
    "id_sales_area": 7,
    "pcname": "str8",
    "service_charge": 9,
    "real_datetime": "str10",
    "tips": 11,
    "id_clients": 12,
    "pbill_index": 13,
    "split_parts": 14,
    "id_real_untill_user": 15,
    "reopen_type": 16,
    "external_id": "str17",
    "covers": 18,
    "hht": "str19",
    "super_dx": 20,
    "c_tips": 21,
    "id_currency": 22,
    "bill": {
      "id": 0,
      "tableno": 1,
      "id_untill_users": 2,
      "table_part": "str3",
      "id_courses": 4,
      "id_clients": 5,
      "name": "str6",
      "proforma": 7,
      "modified": "str8",
      "open_datetime": "str9",
      "close_datetime": "str10",
      "number": 11,
      "failurednumber": 12,
      "suffix": "str13",
      "pbill_number": 14,
      "pbill_failurednumber": 15,
      "pbill_suffix": "str16",
      "hc_foliosequence": 17,
      "hc_folionumber": "str18",
      "tip": 19,
      "qty_persons": 20,
      "isdirty": 21,
      "reservationid": "str22",
      "id_alter_user": 23,
      "service_charge": 24,
      "number_of_covers": 25,
      "id_user_proforma": 26,
      "bill_type": 27,
      "locker": 28,
      "id_time_article": 29,
      "timer_start": "str30",
      "timer_stop": "str31",
      "isactive": 32,
      "table_name": "str33",
      "group_vat_level": 34,
      "comments": "str35",
      "id_cardprice": 36,
      "discount": 37,
      "discount_value": 38,
      "id_discount_reasons": 39,
      "hc_roomnumber": "str40",
      "ignore_auto_sc": 41,
      "extra_fields": "Kg==",
      "id_bo_service_charge": 43,
      "free_comments": "str44",
      "id_t2o_groups": 45,
      "service_tax": 46,
      "sc_plan": "Lw==",
      "client_phone": "str48",
      "age": "str49",
      "description": "Mg==",
      "sdescription": "str51",
      "vars": "NA==",
      "take_away": 53,
      "fiscal_number": 54,
      "fiscal_failurednumber": 55,
      "fiscal_suffix": "str56",
      "id_order_type": 57,
      "not_paid": 58,
      "total": 59
    },
    "bill_reprints": [
      {
        "id": 0,
        "id_pbill": 1,
        "datetime": "str2",
        "id_untill_users": 3
      }
    ],
    "bill_split_rest": [
      {
        "id": 0,
        "id_bill": 1,
        "is_active": 2,
        "split_data": "Aw==",
        "datetime": "str4",
        "id_pbill": 5
      }
    ],
    "complete_meal": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_untill_users": 2,
        "cm_datetime": "str3",
        "cm_pcname": "str4",
        "cm_quantity": 5,
        "cm_price": 6
      }
    ],
    "neg_pbill": [
      {
        "id": 0,
        "id_pbill": 1,
        "r_type": 2,
        "pdatetime": "str3",
        "id_pbill_close": 4
      }
    ],
    "open_discounts": [
      {
        "id": 0,
        "id_pbill": 1,
        "amount": 2,
        "vat_percent": 3,
        "vat": 4
      }
    ],
    "pbill_balance": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_clients": 2,
        "id_accounts": 3,
        "pre_balance": 4,
        "pre_balance_common": 5
      }
    ],
    "pbill_cleancash_info": [
      {
        "id": 0,
        "id_pbill": 1,
        "clean_cash_trnumber": 2,
        "clean_cash_signature": "str3",
        "manufacturing_code": "str4",
        "control_timestamp": "str5",
        "ticket_counter": "str6",
        "vsc_id": "str7",
        "plu_data_hash": "str8",
        "id_bill": 9,
        "ccdatetime": "str10",
        "kind": 11,
        "production_nr": "str12",
        "extra1": "str13",
        "extra2": "str14"
      }
    ],
    "pbill_email": [
      {
        "id": 0,
        "id_pbill": 1,
        "pemail_email": "str2",
        "pemail_body": "Aw==",
        "pemail_dt": "str4",
        "pemail_state": 5
      }
    ],
    "pbill_item": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_untill_users": 2,
        "tableno": 3,
        "rowbeg": 4,
        "kind": 5,
        "quantity": 6,
        "id_articles": 7,
        "price": 8,
        "text": "str9",
        "id_prices": 10,
        "with_without": 11,
        "id_courses": 12,
        "pdatetime": "str13",
        "purchase_price": 14,
        "vat_sign": "str15",
        "vat": 16,
        "id_menu": 17,
        "menu_quantity": 18,
        "original_price": 19,
        "id_discount_reasons": 20,
        "discount_type": 21,
        "chair_number": 22,
        "separated": 23,
        "negative": 24,
        "vat_percent": 25,
        "chair_name": "str26",
        "id_option_article": 27,
        "start_delay_minutes": 28,
        "pua": 29,
        "no_price": 30,
        "orig_pbill_id": 31,
        "parts_id": 32,
        "full_paid": 33,
        "weight": 34,
        "splitted_coef": 35,
        "split_id": 36,
        "free_comments": "str37",
        "id_smartcards": 38,
        "has_allergens": 39,
        "id_article_options": 40,
        "order_item_allergens": [
          {
            "id": 0,
            "id_order_item": 1,
            "id_menu_item": 2,
            "id_allergens": 3,
            "text": "str4",
            "id_pbill_item": 5
          }
        ],
        "order_item_extra": [
          {
            "id": 0,
            "id_order_item": 1,
            "id_menu_item": 2,
            "id_pbill_item": 3,
            "id_article_barcodes": 4
          }
        ],
        "order_item_sizes": [
          {
            "id": 0,
            "id_order_item": 1,
            "id_menu_item": 2,
            "id_pbill_item": 3,
            "id_articles": 4,
            "price": 5,
            "original_price": 6,
            "vat": 7,
            "id_size_modifier_item": 8
          }
        ],
        "pbill_hash": [
          {
            "id": 0,
            "id_pbill_item": 1,
            "id_untill_users": 2
          }
        ],
        "pbill_item_bookp": [
          {
            "id": 0,
            "id_pbill_item": 1,
            "id_bookkeeping_turnover": 2,
            "id_bookkeeping_vat": 3
          }
        ]
      }
    ],
    "pbill_item_refund": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_untill_users": 2,
        "tableno": 3,
        "rowbeg": 4,
        "kind": 5,
        "quantity": 6,
        "id_articles": 7,
        "id_department": 8,
        "id_food_group": 9,
        "id_category": 10,
        "price": 11,
        "text": "str12",
        "id_prices": 13,
        "with_without": 14,
        "id_courses": 15,
        "pdatetime": "str16",
        "purchase_price": 17,
        "vat_sign": "str18",
        "vat": 19,
        "id_menu": 20,
        "menu_quantity": 21,
        "ref_type": 22
      }
    ],
    "pbill_payments": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_payments": 2,
        "price": 3,
        "customer_amount": 4,
        "c_price": 5,
        "c_customer_amount": 6,
        "vat": 7,
        "id_driver_discount": 8,
        "accounts_payments": [
          {
            "id": 0,
            "datetime": "str1",
            "id_clients": 2,
            "id_untill_users": 3,
            "tableno": 4,
            "tablepart": "str5",
            "number": 6,
            "suffix": "str7",
            "name": "str8",
            "tr_datetime": "str9",
            "bill_number": "str10",
            "parts_count": 11,
            "part_index": 12,
            "discount": 13,
            "id_sales_area": 14,
            "total": 15,
            "account_type": 16,
            "payer_name": "str17",
            "id_pbill_payments": 18
          }
        ],
        "account_payment_data": [
          {
            "id": 0,
            "id_pbill_payments": 1,
            "account_type": 2
          }
        ],
        "payments_hash": [
          {
            "id": 0,
            "id_payments": 1,
            "id_untill_users": 2
          }
        ],
        "pbill_card_payments_info": [
          {
            "id": 0,
            "id_pbill_payments": 1,
            "masked_pan": "str2",
            "pan": "str3",
            "expire": "str4",
            "auth_number": "str5",
            "acquier_code": "str6",
            "field1": "str7",
            "field2": "str8",
            "field3": "str9",
            "field4": "str10",
            "field5": "str11",
            "track2data": "str12",
            "loyaltyamount": 13,
            "controlno": "str14",
            "chargetype": 15,
            "cardname": "str16",
            "cardnoentertype": 17,
            "terminalid": "str18",
            "aid": "str19",
            "tvr": "str20",
            "tsi": "str21",
            "account_type": "str22",
            "customer_receipt": "str23",
            "merchant_receipt": "str24",
            "tip_approvement": 25,
            "prepaid_pan": "str26",
            "misc_data": "Gw==",
            "field6": "str28",
            "field7": "str29",
            "field8": "str30",
            "field9": "str31",
            "field10": "str32",
            "merchant_id": "str33",
            "cashback_amount": 34,
            "field11": "str35",
            "field12": "str36",
            "field13": "str37",
            "field14": "str38",
            "field15": "str39"
          }
        ],
        "pbill_payer": [
          {
            "id": 0,
            "id_pbill_payments": 1,
            "payer_name": "str2"
          }
        ],
        "pbill_payments_bookp": [
          {
            "id": 0,
            "id_pbill_payments": 1,
            "id_bookkeeping": 2
          }
        ],
        "pbill_zapper_payments_info": [
          {
            "id": 0,
            "id_pbill_payments": 1,
            "id_zapper_proformas": 2,
            "zapper_id": "str3",
            "misc_data": "BA=="
          }
        ],
        "psp_tips": [
          {
            "id": 0,
            "id_pbill": 1,
            "amount": 2,
            "id_pbill_payments": 3
          }
        ],
        "smartcards_turnover": [
          {
            "id": 0,
            "datetime": "str1",
            "id_smartcards": 2,
            "id_untill_users": 3,
            "kind": 4,
            "amount": 5,
            "p_amount": 6,
            "id_pbill_payments": 7,
            "id_payments": 8,
            "is_initial_value": 9,
            "card_data": "Cg==",
            "deposit_number": 11,
            "deposit_suffix": "str12",
            "pcname": "str13",
            "new_balance": 14
          }
        ],
        "voucher_payments": [
          {
            "id": 0,
            "id_vouchers": 1,
            "id_pbill_payments": 2,
            "used_dt": "str3"
          }
        ],
        "voucher_pbill_payments": [
          {
            "id": 0,
            "id_voucher_pbill": 1,
            "price": 2,
            "id_vouchers": 3,
            "id_payments": 4,
            "id_pbill_payments": 5
          }
        ]
      }
    ],
    "pbill_return": [
      {
        "id": 0,
        "id_pbill": 1,
        "ref_type": 2,
        "id_void_reason": 3,
        "void_text": "str4"
      }
    ],
    "psp_tips": [
      {
        "id": 0,
        "id_pbill": 1,
        "amount": 2,
        "id_pbill_payments": 3
      }
    ],
    "sold_articles": [
      {
        "id": 0,
        "id_pbill": 1,
        "id_order_item": 2,
        "quantity": 3,
        "parts_id": 4,
        "sa_coef": 5,
        "split_id": 6
      }
    ],
    "sold_articles_wm": [
      {
        "id": 0,
        "id_order_item": 1,
        "id_pbill": 2,
        "quantity": 3,
        "sa_coef": 4
      }
    ],
    "stock_doc": [
      {
        "id": 0,
        "id_orders": 1,
        "id_pbill": 2,
        "id_stock_invoice": 3,
        "id_stock_adjustment": 4,
        "id_stock_cost_correction": 5
      }
    ],
    "stock_pbill_queue": [
      {
        "id": 0,
        "id_pbill": 1,
        "pdatetime": "str2"
      }
    ]
  }
}
  ```

## Password Authentication

- Create user: `POST air.untill.com/api/user/new`
  ```json
  {"login": "abc", "password": "abcdefg"}
  ```
- Login: `POST air.untill.com/api/user/login`
  ```json
  {"login": "abc", "password": "abcdefg"}
  ```
  
## Available Modules

- Get list of available module manifests
  - `GET air.untill.com/api/modules`

# Links

- https://www.moesif.com/blog/technical/api-design/REST-API-Design-Filtering-Sorting-and-Pagination
  - `?filters[date][gte]=2018-04-01&filters[date][lte]=2018-04-31&filters[status][eq]=active`
- https://restfulapi.net/resource-naming/
  - Do not use underscores ( _ )
- https://restdb.io/docs/querying-with-the-api
- https://en.wikipedia.org/wiki/Representational_state_transfer
