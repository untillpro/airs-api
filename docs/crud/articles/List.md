[← Back](README.md)

## Requests:

**All articles request**
```http
GET https://api.air.untill.com/air-bo-view/articles
```

**With specified location:**

```http
GET https://api.air.untill.com/air-bo-view/articles?location=1
```

**With multy-location:**

```http
GET https://api.air.untill.com/air-bo-view/articles?location[]=1&location[]=44&location[]=654
```

**Specified page and pagesize**
```http
GET https://api.air.untill.com/air-bo-view/articles?page=1&pagesize=50
```

**Specified order**
```http
GET https://api.air.untill.com/air-bo-view/articles?order_by[name]=asc
```

**Multy ordering**
```http
GET https://api.air.untill.com/air-bo-view/articles?order_by[name]=asc&order_by[location]=desc
```

**Specified status**
```http
GET https://api.air.untill.com/air-bo-view/articles?show_deleted=1
```
In this case articles with status 2 will be also returned

##Response example

If success:

```javascript
    {
        "locations": { //all selected locations
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
                    ,"15000043080": {
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
                    }
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
        "items": {  //grouped by HQ_ID (or NAME if HQ_ID)
            "Ace": { 
                "1": { // location id
                    "id": 123456,
                    "name": "Ace",
                    "hq_id": "Ace",
                    "number": 1,
                    "department": [
                        {
                            "id": 1000001,
                            "name": "Frisdranken"
                        }
                    ],
                    "prices": [
                        {
                            "id": 500001,
                            "price_id": 600001,
                            "name": "Normaal",
                            "value": 1.89,
                            "vat": 10,
                            "currency": 999991
                        },
                        {
                            "id": 500002,
                            "price_id": 600002,
                            "name": "Price2",
                            "value": 1.19,
                            "vat": 0,
                            "currency": 999991
                        },
                        {
                            "id": 500003,
                            "price_id": 600003,
                            "name": "Price3",
                            "value": 1.06,
                            "vat": 0,
                            "currency": 999991
                        }
                    ],
                    "sales_area": [
                        15000024292
                    ], //aggregated 
                    "course": "Fastrunners",
                    "status": 1
                },

                "654": { // location id
                    "id": 654321,
                    "name": "Ace 2",
                    "hq_id": "Ace",
                    "number": 2,
                    "department": [
                        {
                            "id": 1000002,
                            "name": "Fastrunnerz"
                        }
                    ],
                    "prices": [
                        {
                            "id": 500001,
                            "price_id": 600001,
                            "name": "Normaal",
                            "value": 2.5,
                            "vat": 10,
                            "currency": 999992
                        },
                        {
                            "id": 500002,
                            "price_id": 600002,
                            "name": "Price2",
                            "value": 2.2,
                            "vat": 0,
                            "currency": 999992
                        },
                        {
                            "id": 500003,
                            "price_id": 600003,
                            "name": "Price3",
                            "value": 2.1,
                            "vat": 0,
                            "currency": 999992
                        }
                    ],
                    "sales_area": [
                        5000000081,
                        15000024291
                    ],
                    "course": "Changable1",
                    "status": 2
                }
            },
            ...  
        }
    }
```

- `location` object contains of locations, for what articles was selected.
- each `location` in list has all needed data, scpecified by location and that can be used to display `items` entities. In result above this is `currency` and `sales_area` entities.

In other case returns errors:

```javascript
{
    "errors": [
        String | Object
    ]
}
```

[← Back](README.md)