# Ticker

## Get Ticker

This API call returns the exchange rate between two given currencies

> Gets the ticker for CAD to BTC exchange

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
"http://example.com/api/ticker/cad/btc"
```

> The above command returns JSON structured like this:

```json
{
  "from_currency_name": "CAD",
  "to_currency_name": "BTC",
  "bid": "11358.0",
  "ask": "11497.3",
  "updated_at": "2018-02-27 02:12:54"
}
```

### HTTP Request

`GET http://example.com/api/ticker/:from_currency_name/:to_currency_name`

### Query Parameters

Parameter          | Description                       |
------------------ | --------------------------------- |
from_currency_name | Source currency three letter code |
to_currency_name   | Target currency three letter code |




