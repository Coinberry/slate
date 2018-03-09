# Orders

## Get all orders

This API call is paginated. The result will always contain a links object. If there is only one page of results the 'next' property will be null.

> Returns a list of orders

```shell
curl 
-X GET 
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
"http://example.com/api/balances"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
  {
    "id": "1008",
      "type": "withdrawal-orders",
      "attributes": {
        "amount": -30000,
        "date": "Feb 27 2018 8:54PM",
        "type": "Sending",
        "currency-name": "CAD",
        "guid": "6BFKWkdS",
        "rate": null,
        "status": "pending",
        "token": "oOtB8pniCGs",
        "withdrawal-type": "eft",
        "withdrawal-wallet-address": null,
        "eft-transfer-password": "bad67d62",
        "amount-received": null,
        "tx-hash": null
      }
  },
  {
    "id": "1007",
    "type": "fund-orders",
    "attributes": {
      "amount": 280000,
      "date": "Feb 27 2018 8:38PM",
      "type": "Received",
      "currency-name": "CAD",
      "guid": "2L_M3eIs",
      "rate": 0.933333333333333,
      "status": "completed",
      "token": "50bea7f7ac",
      "withdrawal-type": null,
      "withdrawal-wallet-address": null,
      "eft-transfer-password": null,
      "amount-received": null,
      "tx-hash": null
    }
  },
  {
    "id": "852",
    "type": "buy-orders",
    "attributes": {
      "amount": 93112,
      "date": "Jan 30 2018 12:13PM",
      "type": "Buy",
      "currency-name": "BTC",
      "guid": "dCBU4JsK",
      "rate": 14112.03,
      "status": "completed",
      "token": null,
      "withdrawal-type": null,
      "withdrawal-wallet-address": null,
      "eft-transfer-password": null,
      "amount-received": null,
      "tx-hash": null
    }
  },
  {
    "id": "851",
    "type": "sell-orders",
    "attributes": {
      "amount": -100000,
      "date": "Jan 30 2018 12:12PM",
      "type": "Sell",
      "currency-name": "BTC",
      "guid": "KbDrDm-3",
      "rate": 13148.35,
      "status": "completed",
      "token": null,
      "withdrawal-type": null,
      "withdrawal-wallet-address": null,
      "eft-transfer-password": null,
      "amount-received": null,
      "tx-hash": null
    }
  },
  {
    "id": "543",
    "type": "fund-orders",
    "attributes": {
      "amount": 100000,
      "date": "Jan 2 2018 7:35PM",
      "type": "Received",
      "currency-name": "BTC",
      "guid": "S0zp-IrZ",
      "rate": null,
      "status": "completed",
      "token": "420dddeee4",
      "withdrawal-type": null,
      "withdrawal-wallet-address": null,
      "eft-transfer-password": null,
      "amount-received": 100000,
      "tx-hash": null
    }
  }
  ],
  "links": {
    "self": "http://localhost:3000/api/orders?page%5Bnumber%5D=1&page%5Bsize%5D=10",
    "first": "http://localhost:3000/api/orders?page%5Bnumber%5D=1&page%5Bsize%5D=10",
    "prev": null,
    "next": null,
    "last": "http://localhost:3000/api/orders?page%5Bnumber%5D=1&page%5Bsize%5D=10"
  }
}
```

### HTTP Request

`GET http://example.com/api/orders`

### Query Parameters

Parameter | Description | Optional | Default |
--------- | ----------- | -------- | ------- |
page[number] | Current page of results | yes | - |
page[size] | Number of orders per page | yes | 10|

## Create Orders

This API call creates a Buy or Sell order

> Returns a list of orders

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"order": { "from_currency_id": 1, "to_currency_id": 2, "amount_fractional": 0.01, "type": "BuyOrder"}}'
"http://example.com/api/orders"
```

> The above command returns JSON structured like this:

```json
{
    "data": {
        "id": "27",
        "type": "buy-orders",
        "attributes": {
            "amount": 1000000,
            "date": "Mar 9 2018 8:50AM",
            "type": "Buy",
            "currency-name": "BTC",
            "guid": "vKV810AY",
            "rate": 18000,
            "status": "completed",
            "token": "jBSBa2CAakw",
            "withdrawal-type": null,
            "withdrawal-wallet-address": null,
            "eft-transfer-password": null,
            "amount-received": null,
            "tx-hash": null,
            "processed-at": 1520603438
        }
    }
}
```

### HTTP Request

`POST http://example.com/api/orders`

### Query Parameters

All parameters are required

Parameter | Description |
--------- | ----------- |
from_currency_id | Source currency  |
to_currency_id | Target currency |
amount_fractional | Amount in either ETH or BTC |
type | Type of order (BuyOrder or SellOrder) |


