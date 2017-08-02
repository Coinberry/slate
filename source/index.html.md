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

## Retrieve User

```javascript
// Install required node modules
// npm install --save node-fetch

var fetch = require('node-fetch');

fetch('https://nameless-falls-59972.herokuapp.com/users/mack-daddy-email-com', {
  method: 'GET',
  headers: {
  	 'Accept': 'application/vnd.api.v1+json',
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
        "id": "1",
        "type": "users",
        "attributes": {
            "email": "mack.daddy@email.com",
            "slug": "mack-daddy-email-com",
            "first-name": "Mack",
            "last-name": "Daddy"
        },
        "relationships": {
            "purchases": {
                "data": [
                    {
                        "id": "1",
                        "type": "purchases"
                    }
                ]
            },
            "loyalty-points": {
                "data": [
                    {
                        "id": "1",
                        "type": "loyalty-points"
                    }
                ]
            },
            "stats": {
                "data": [
                    {
                        "id": "1",
                        "type": "stats"
                    }
                ]
            },
            "games": {
                "data": [
                    {
                        "id": "1",
                        "type": "games"
                    }
                ]
            }
        }
    }
}
```

This endpoint retrieves a user

### HTTP Request

`GET http://nameless-falls-59972.herokuapp.com/users/mack-daddy-email-com`

### Body Parameters

Parameter | Default | Accepted values
--------- | ------- | ---------------
include | empty | stats, games, purchases, loyalty_points


### HEADERS 

Name | Value
---- | -----
Content-Type | application/vnd.api+json
Accept | application/vnd.api.v1+json

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
