---
title: API Reference

language_tabs:
  - shell
  - javascript

includes:
  - errors

search: true
---

# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.


# Users

## Create User (Registration)

```javascript
// Install required node modules
// npm install --save yayson node-fetch

var Presenter = require('yayson')().Presenter;
var fetch = require('node-fetch');

class RegisterPresenter extends Presenter {};
RegisterPresenter.prototype = 'users';

var register = {
  email: 'john.doe@email.com',
  password: 'q1w2e3r4t5',
  password_confirmation: 'q1w2e3r4t5'
};

var register_data = RegisterPresenter.render(register);

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

```shell
curl -d "email": "test2@test.com" \
        "password": "testpassword1" \
        "password_confirmation": "testpassword1" \ 
        http://localhost:3000/auth
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

`POST http://example.com/auth`

### Body Parameters

Parameter | Default 
--------- | -------
email | yes
password | yes
password_confirmation | yes

## Confirm User

```shell
curl http://localhost:3000/auth/confirmation?confirmation_token=token
```

> The above command returns JSON structures like this:

```json
{
  "data": []
}
```

This endpoint confirms a new user.

### HTTP Request

`GET http://example.com/auth/confirmation?confirmation_token=token`

### Query Parameters

Parameter | Required 
--------- | -------
confirmation_token | yes

## Login User

```shell
curl -d "email":"test@test.com" \
        "password":"q1w2e3r4t5" \
        http://localhost:3000/auth/sign_in
```

> The above command returns JSON structures like this:

```json
{
  "data":
    {
      "id":9,
      "type":"users",
      "attributes": {
        "email":"test2@test.com",
        "provider":"email",
        "uid":"test2@test.com",
      }
    }
}
```

> In addition the following HTTP Headers are returned:

```shell
access-token  = _CYUpiyEDRYLy1Q2qFLlAw
token-type    = Bearer
client        = WRclOjBHDtgch7qdYvy_jg
expiry        = 1501596921
uid           = test2@test.com
```

This endpoint logs in a user.

### HTTP Request

`DELETE http://example.com/auth/sign_out`

## Logout User

```shell
curl -X "DELETE"  \
  -H "uid: test2@test.com" \
  -H "client: WRclOjBHDtgch7qdYvy_jg" 
  -H "access-token: _CYUpiyEDRYLy1Q2qFLlA" \ 
  http://example.com/auth/sign_out
```

> The above command returns JSON structures like this:

```json
{
  "data": []
}
```

This endpoint logs out a user.

### HTTP Request

`DELETE http://example.com/auth/sign_out`

### HTTP HEAD Parameters

Parameter | Required 
--------- | -------
uid | yes
client | yes
access-token | yes
