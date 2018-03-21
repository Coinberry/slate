# Funds

## Create Fund

This API call creates a Fund order

> Creates a fund order and returns it

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"fund_order": { "from_currency_id": 1, "to_currency_id": 2, "amount_fractional": 0.01, "funding_type": "btc"}}'
"http://example.com/api/fund_orders"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "fund-orders",
    "attributes": {
      "amount": -1,
      "date": "Mar 19 2018 3:20PM",
      "type": "Sending",
      "currency-name": "BTC",
      "guid": "ZJzJafkf",
      "rate": null,
      "status": "pending",
      "token": "ZWboCheYcCQ",
      "fund-type": "eft",
      "fund-wallet-address": null,
      "eft-transfer-password": null,
      "amount-received": null,
      "tx-hash": null,
      "processed-at": null,
      "wallet": "muszEWphc8wCAbCaZZKtQ2yo5WaZM433A4"
    }
  }
}
```

### HTTP Request

`POST http://example.com/api/fund_orders`

### Query Parameters

Parameter | Description |
--------- | ----------- |
from_currency_id | Source currency  |
to_currency_id | Target currency |
amount | Amount as integer in either CAD cents or BTC satoshi |
amount_fractional | Amount in either CAD or BTC |
funding_type | Either btc or "EFT/e-Transfer"




