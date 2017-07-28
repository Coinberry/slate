---
title: API Reference

language_tabs:
  - javascript

search: true
---

# Introduction

This REST API follow the JsonAPI specification. You can find out more about this on the [official page](http://jsonapi.org/). 

The examples contain javascript (node) example requests.

# Users

## Create User (Registration)

```javascript
// Install required node modules
// npm install --save node-fetch

var fetch = require('node-fetch');

var register_data = {
  data: {
    type: "users",
    attributes: {
      email: "john.doe@email.com",
      password: "q1w2e3r4t5",
      password_confirmation: "q1w2e3r4t5"
    }
  }
};

fetch('https://nameless-falls-59972.herokuapp.com/registrations', {
  method: 'POST',
  body: JSON.strigify(register_data),
  headers: {
    'Content-Type': 'application/vnd.api+json'
  }
})
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.log(err));

```

> The above command returns JSON structures like this:

```json
{
  "data": {
    "id": "8",
    "type": "users",
    "attributes": {
      "email": "john.doe@email.com"
    }
  }
}
```

This endpoint creates a new user.

### HTTP Request

`POST http://nameless-falls-59972.herokuapp.com/registrations`

### Body Parameters

Parameter | Default 
--------- | -------
email | yes
password | yes
password_confirmation | yes

### HEADERS 

Name | Value
---- | -----
Content-Type | application/vnd.api+json

## Login User

```javascript
// Install required node modules
// npm install --save node-fetch

var fetch = require('node-fetch');

var login_data = {
  data: {
    type: "users",
    attributes: {
      email: 'john.doe@email.com',
      password: 'q1w2e3r4t5',
    }
  }
};

fetch('https://nameless-falls-59972.herokuapp.com/login', {
  method: 'POST',
  body: JSON.strigify(login_data),
  headers: {
    'Content-Type': 'application/vnd.api+json'
  }
})
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.log(err));

```

> The above command returns JSON structures like this:

```json
{
  "data":
    {
      "type": "sessions",
      "attributes": {
        "email": "john.doe@email.com",
        "auth_token": "zvcU9DL4D48To5PiknCSf72C"
      }
    }
}
```

This endpoint creates a new login session.

### HTTP Request

`POST http://nameless-falls-59972.herokuapp.com/login`

### Body Parameters

Parameter | Default 
--------- | -------
email | yes
password | yes

### HEADERS 

Name | Value
---- | -----
Content-Type | application/vnd.api+json

# Payments

## Create Payment Token

```javascript
var fetch = require('node-fetch');

var payment_token_data = {
  "data": {
    "type": "payment_tokens",
    "attributes": {
      "country": "CA"
    }
  }
}

fetch('https://nameless-falls-59972.herokuapp.com/orders', {
  method: 'POST',
  body: JSON.strigify(payment_token_data),
  headers: {
    'Accept': 'application/vnd.api.v1+json',
    'Content-Type': 'application/vnd.api+json',
    'X-Auth-Token': 'FnNupcwL74zMVnQiV6BCKihp',
    'X-User-Email': 'john.doe@email.com'
  }
})
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.log(err));

```
> The above command returns JSON structures like this:

```json
{
    "data": {
        "type": "payment_tokens",
        "attributes": {
            "token": {
                "token": "4SsHztNryM67dZuSbTsX0Uu7ZbagTuAx"
            }
        }
    }
}
```
This endpoint creates a payment token for the currently logged in user

### HTTP Request

`POST http://nameless-falls-59972.herokuapp.com/payment_tokens`

### HEADERS 

Name | Value
---- | -----
Accept | application/vnd.api.v1+json
X-Auth-Token | FnNupcwL74zMVnQiV6BCKihp
X-User-Email | john.doe@email.com
Content-Type | application/vnd.api+json

# Orders

## Create Order

```javascript
// Install required node modules
// npm install --save node-fetch

var fetch = require('node-fetch');

var order_data = {
  data: {
    type: "orders",
    attributes: {
      total: 1500
    },
    relationships: {
      game_tokens: {
        data: [
          {
            type: "game_tokens",
            attributes: {
              price: 500
            }
          },
          {
            type: "game_tokens",
            attributes: {
              price: 500
            }
          },
          {
            type: "game_tokens",
            attributes: {
              price: 500
            }
          }
        ]
      }
    }
  }
};

fetch('https://nameless-falls-59972.herokuapp.com/orders', {
  method: 'POST',
  body: JSON.strigify(order_data),
  headers: {
    'Accept': 'application/vnd.api.v1+json',
    'Content-Type': 'application/vnd.api+json',
    'X-Auth-Token': 'FnNupcwL74zMVnQiV6BCKihp',
    'X-User-Email': 'john.doe@email.com'
  }
})
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.log(err));

```

> The above command returns JSON structures like this:

```json
{
    "data": {
        "id": "2",
        "type": "orders",
        "attributes": {
            "date": null,
            "total": 1500
        },
        "relationships": {
            "order-items": {
                "data": [
                    {
                        "id": "4",
                        "type": "order-items"
                    },
                    {
                        "id": "5",
                        "type": "order-items"
                    },
                    {
                        "id": "6",
                        "type": "order-items"
                    }
                ]
            },
            "user": {
                "data": {
                    "id": "1",
                    "type": "users"
                }
            }
        }
    }
}
```

This endpoint creates an order for a user.

### HTTP Request

`POST http://nameless-falls-59972.herokuapp.com/orders`

### HEADERS 

Name | Value
---- | -----
Accept | application/vnd.api.v1+json
X-Auth-Token | FnNupcwL74zMVnQiV6BCKihp
X-User-Email | john.doe@email.com
Content-Type | application/vnd.api+json

## Show Order

```javascript
// Install required node modules
// npm install --save node-fetch

var fetch = require('node-fetch');

fetch('https://nameless-falls-59972.herokuapp.com/orders/1', {
  method: 'GET',
  headers: {
    'Accept': 'application/vnd.api.v1+json',
    'Content-Type': 'application/vnd.api+json',
    'X-Auth-Token': 'FnNupcwL74zMVnQiV6BCKihp',
    'X-User-Email': 'john.doe@email.com'
  }
})
  .then(res => res.json())
  .then(json => console.log(json))
  .catch(err => console.log(err));

```

> The above command returns JSON structures like this:

```json

{
    "data": {
        "id": "1",
        "type": "orders",
        "attributes": {
            "date": null,
            "total": 7500
        },
        "relationships": {
            "order-items": {
                "data": [
                    {
                        "id": "1",
                        "type": "order-items"
                    },
                    {
                        "id": "2",
                        "type": "order-items"
                    },
                    {
                        "id": "3",
                        "type": "order-items"
                    }
                ]
            },
            "user": {
                "data": {
                    "id": "1",
                    "type": "users"
                }
            }
        }
    },
    "included": [
        {
            "id": "1",
            "type": "order-items",
            "relationships": {
                "order": {
                    "data": {
                        "id": "1",
                        "type": "orders"
                    }
                },
                "game-token": {
                    "data": {
                        "id": "1",
                        "type": "game-tokens"
                    }
                }
            }
        },
        {
            "id": "2",
            "type": "order-items",
            "relationships": {
                "order": {
                    "data": {
                        "id": "1",
                        "type": "orders"
                    }
                },
                "game-token": {
                    "data": {
                        "id": "2",
                        "type": "game-tokens"
                    }
                }
            }
        },
        {
            "id": "3",
            "type": "order-items",
            "relationships": {
                "order": {
                    "data": {
                        "id": "1",
                        "type": "orders"
                    }
                },
                "game-token": {
                    "data": {
                        "id": "3",
                        "type": "game-tokens"
                    }
                }
            }
        }
    ]
}
```

This endpoint retrieves an order for a user by Order ID

### HTTP Request

`GET http://nameless-falls-59972.herokuapp.com/orders/1`

### HEADERS 

Name | Value
---- | -----
Accept | application/vnd.api.v1+json
X-Auth-Token | FnNupcwL74zMVnQiV6BCKihp
X-User-Email | john.doe@email.com
Content-Type | application/vnd.api+json
