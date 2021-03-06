[← Back](README.md)

## Requests:

**All articles request**
```javascript
GET https://air.untill.com/api/air-bo-view/articles
```

**With specified location:**

```javascript
GET https://air.untill.com/api/air-bo-view/articles?location=1
```

**With multy-location:**

```javascript
GET https://air.untill.com/api/air-bo-view/articles?location=1&location=44&location=654
```

**Specified page and pagesize**
```javascript
GET https://air.untill.com/api/air-bo-view/articles?page=1&pagesize=50
```

**Specified order**
```javascript
GET https://air.untill.com/api/air-bo-view/articles?order_by[name]=asc
```

**Multy ordering**
```javascript
GET https://air.untill.com/api/air-bo-view/articles?order_by[name]=asc&order_by[location]=desc
```

**Specified status**
```javascript
GET https://air.untill.com/api/air-bo-view/articles?show_deleted=1
```
In this case articles with status 2 will be also returned

##Response example

If success:

```javascript
    {
        "classifiers": { //all selected locations
            "1": {
                "name": "Location 1",
                "currency": { //all used currencies
                    "999991": {
                        "id": 999991,
                        "name": "Euro",
                        "code": "EUR",
                        "round": 2,
                        "symbol": "€",
                        "alignment": 0,
                        "round_down": 0,
                        "eurozone": 1
                    }
                },
                "course": {
                    "12345": {
                        "id": 12345,
                        "name": String,
                        "hq_id": String,
                        "changable": Number,
                        "coursenumber": Number,
                        "separate": Number,
                        "ask_to_change": Number
                        "ml_name": Blob
                    }
                },
                "department": {
                    "1000001": {
                        "id": 1000001,
                        "name": "Frisdranken"
                    }
                },
                "sales_area": {
                    "5000000081": {
                        "id": 5000000081,
                        "name": "Taverne",
                        "bmanual": 0,
                        ...
                    },
                    "15000024291": {
                        "id": 15000024291,
                        "name": "Terrace",
                        "bmanual": 0,
                        ...
                    },
                    "15000043077": {
                        ...
                    },
                    "15000043080": {
                        ...
                    },
                    "15000045151": {
                        ...
                    }
                }
            },
            "44": {
                "name": "Location 44",
                "currency": { //all used currencies
                    "999993": {
                        "id": 999993,
                        "name": "Euro",
                        "code": "EUR",
                        "round": 2,
                        "symbol": "€",
                        "alignment": 0,
                        "round_down": 0,
                        "eurozone": 1
                    },
                    ...
                },
                "course": {
                    "22222": {
                        "id": 22222,
                        "name": String,
                        "hq_id": String,
                        "changable": Number,
                        "coursenumber": Number,
                        "separate": Number,
                        "ask_to_change": Number
                        "ml_name": Blob
                    },
                    ...
                },
                "department": {
                    "1000001": {
                        "id": 1000001,
                        "name": "Frisdranken"
                    },
                    ...
                },
                "sales_area": {
                    "5000123123": {
                        "id": 5000123123,
                        "name": "Taverne",
                        "bmanual": 0,
                        ...
                    },
                    "15001234213": {
                        "id": 15001234213,
                        "name": "Terrace",
                        "bmanual": 0,
                        ...
                    },
                }
            },
            "654": {
                "name": "Location 654",
                "currency": { //all used currencies
                    "999992": {
                        "id": 999992,
                        "name": "US Dollars",
                        "code": "USD",
                        "round": 2,
                        "symbol": "$",
                        "alignment": 0,
                        "round_down": 0,
                        "eurozone": 0
                    },
                },
                "course": {
                    "33333": {
                        "id": 33333,
                        "name": String,
                        "hq_id": String,
                        "changable": Number,
                        "coursenumber": Number,
                        "separate": Number,
                        "ask_to_change": Number
                        "ml_name": Blob
                    }
                },
                "department": {
                    "1000001": {
                        "id": 1000001,
                        "name": "Frisdranken"
                    }
                },
                "sales_area": {
                    "12341234": {
                        "id": 12341234,
                        "name": "Some unique SA",
                        "bmanual": 0,
                        ...
                    }
                }
            },
        },
        "data": {  //grouped by HQ_ID 
            "Ace": { 
                "1": { // location id
                    "id": 123456,
                    "name": "Ace",
                    "hq_id": "Ace",
                    "number": 1,
                    "id_department": [1000001],
                    "prices": [
                        {
                            "id": 500001,
                            "id_price": 600001,
                            "name": "Normaal",
                            "value": 1.89,
                            "vat": 10,
                            "currency": 999991
                        },
                        {
                            "id": 500002,
                            "id_price": 600002,
                            "name": "Price2",
                            "value": 1.19,
                            "vat": 0,
                            "currency": 999991
                        },
                        {
                            "id": 500003,
                            "id_price": 600003,
                            "name": "Price3",
                            "value": 1.06,
                            "vat": 0,
                            "currency": 999991
                        }
                    ],
                    "id_sales_area": [
                        15000024292
                    ], //aggregated 
                    "course": 12345,
                    "status": 1
                },

                "654": { // location id
                    "id": 654321,
                    "name": "Ace 2",
                    "hq_id": "Ace",
                    "number": 2,
                    "id_department": [1000001],
                    "prices": [
                        {
                            "id": 500001,
                            "id_price": 600001,
                            "name": "Normaal",
                            "value": 2.5,
                            "vat": 10,
                            "currency": 999992
                        },
                        {
                            "id": 500002,
                            "id_price": 600002,
                            "name": "Price2",
                            "value": 2.2,
                            "vat": 0,
                            "currency": 999992
                        },
                        {
                            "id": 500003,
                            "id_price": 600003,
                            "name": "Price3",
                            "value": 2.1,
                            "vat": 0,
                            "currency": 999992
                        }
                    ],
                    "id_sales_area": [
                        5000000081,
                        15000024291
                    ],
                    "course": 33333,
                    "status": 2
                }
            },
            ...  
        }
    }
```

- `classifiers` object contains of all locations, for what articles was selected.
- each `classifiers` in list has all needed data, scpecified by location and that can be used to display `items` entities.

In other case returns errors:

```javascript
{
    "Status": "Bad request",
    "StatusCode": 400,
    "Data": String
}
```

[← Back](README.md)