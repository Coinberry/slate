# Withdrawals

## Create Withdrawal

This API call creates a Withdrawal order

> Creates a withdrawal order and returns it

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"withdrawal_order": { "from_currency_id": 1, "to_currency_id": 2, "amount_fractional": 0.01, "withdrawal_type": "eft", "eft_transfer_password": "123"}}'
"http://example.com/api/withdrawal_orders"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "4",
    "type": "withdrawal-orders",
    "attributes": {
      "amount": -1,
      "date": "Mar 19 2018 3:20PM",
      "type": "Sending",
      "currency-name": "CAD",
      "guid": "SbpD-ZzT",
      "rate": null,
      "status": "pending",
      "token": "ZWboCheYcCQ",
      "withdrawal-type": "eft",
      "withdrawal-wallet-address": null,
      "eft-transfer-password": "123",
      "amount-received": null,
      "tx-hash": null,
      "processed-at": null
    }
  }
}
```

### HTTP Request

`POST http://example.com/api/withdrawal_orders`

### Query Parameters

Parameter | Description |
--------- | ----------- |
from_currency_id | Source currency  |
to_currency_id | Target currency |
amount_fractional | Amount in either CAD, ETH or BTC |
withdrawal_type | Either eft or wallet
eft_transfer_password | Required for withdrawals of type eft
withdrawal_wallet_address | Required for withdrawals of type wallet




