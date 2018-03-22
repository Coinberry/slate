# Currencies

> Returns all currencies

```shell
curl 
  -X GET 
  -H "Content-Type: application/json"
  -H "Accept: application/vnd.coinberry.v1+json"
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
  "http://example.com/api/currencies"
```

> The above command returns JSON structured like this:

```json
{
  "data": [
  {
    "id": "1",
      "type": "currencies",
      "attributes": {
        "name": "CAD",
        "unit": "$"
      }
  },
  {
    "id": "2",
    "type": "currencies",
    "attributes": {
      "name": "BTC",
      "unit": "BTC"
    }
  },
  {
    "id": "3",
    "type": "currencies",
    "attributes": {
      "name": "ETH",
      "unit": "ETH"
    }
  }
  ]
}
```

Currency ids are required for creating Orders.
