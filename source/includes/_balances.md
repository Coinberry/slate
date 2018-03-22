# Balances

> Returns balances summaries

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
  "data": {
    "btc": {
      "balance": "0.01093112",
        "high": 15890,
        "low": 11352.9
    },
      "eth": {
        "balance": 0,
        "high": 1145.83,
        "low": 2890.15
      },
      "fiat": {
        "name": "CAD",
        "balance": 2370.01
      },
      "total_balance": 2566.77016
  }
}
```
