---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

#includes:
#  - errors

search: true
---

# Introduction

Welcome to the Coinberry Portal API.

# Registration

> To register an account, use this code:

```shell
curl 
  -X POST 
  -H "Content-Type: application/json"
  -d "email=john.doe@example.com&password=q1w2e3r4t5&confirmation_url=test.com" 
  "http://example.com/api/auth/register"
```

> The above command returns JSON structured like this:

```json
{
  "message": "Registration Successful"
},
```

### HTTP Request

`POST http://example.com/api/auth/register`

### Query Parameters

Parameter | Description
--------- | -----------
email | Email
password | Password
confirmation_url | This is the base url the user will receive in their email after registering

# Login

> To login a user and retrieve the JWT token, use this code:

```shell
curl 
  -X POST 
  -H "Content-Type: application/json"
  -d "email=john.doe@example.com&password=q1w2e3r4t5"
  "http://example.com/api/auth/login"
```

> The above command returns JSON structured like this:

```json
{
  "jwt": "eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs",
  "message": "Login Successful"
}
```

### HTTP Request

`POST http://example.com/api/auth/login`

### Query Parameters

Parameter | Description
--------- | -----------
email | Email
password | Password

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
    "crypto": [
      {
        "name": "Bitcoin",
        "balance": 0.00093112,
        "high": 15890,
        "low": 11352.9
      },
      {
        "name": "Ethereum",
        "balance": 0,
        "high": 1145.83,
        "low": 2890.15
      }
    ],
    "fiat": {
      "name": "CAD",
      "balance": 2500.01
    },
    "total_balance": 2516.77016
  }
}
```

# Orders

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
        "token": "oOtB8pniCGs"
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
        "token": "50bea7f7ac"
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
        "token": null
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
        "token": null
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
        "token": "420dddeee4"
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
