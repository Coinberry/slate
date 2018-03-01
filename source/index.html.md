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
