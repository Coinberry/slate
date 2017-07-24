---
title: API Reference

language_tabs:
  - javascript
  - shell

includes:
  - errors

search: true
---

# Introduction

This REST API follow the JsonAPI specification. You can find out more about this on the [official page](http://jsonapi.org/). 

The examples contain shell (curl) and javascript (node) example requests.

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
curl -H "Content-Type: application/vnd.api+json" \ 
  -d  "email": "test2@test.com" \
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

`POST http://example.com/registrations`

### Body Parameters

Parameter | Default 
--------- | -------
email | yes
password | yes
password_confirmation | yes

## Login User

```javascript
// Install required node modules
// npm install --save yayson node-fetch

var Presenter = require('yayson')().Presenter;
var fetch = require('node-fetch');

class LoginPresenter extends Presenter {};
LoginPresenter.prototype = 'users';

var login = {
  email: 'john.doe@email.com',
  password: 'q1w2e3r4t5',
};

var login_data = LoginPresenter.render(login);

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

```shell
curl -H "Content-Type: application/vnd.api+jsonm" \
  -d  "email":"test@test.com" \
      "password":"q1w2e3r4t5" \
      https://nameless-falls-59972.herokuapp.com/login
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

