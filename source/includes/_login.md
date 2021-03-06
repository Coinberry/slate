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

> The jwt token encodes the following data

```
{
  "user_id": 1,
  "display_name": "John",
  "email": "john.doe@example.com",
  "exp": 1521825916,
  "status": "verified",
  "referral_token": "W$34%34"
}
```

### HTTP Request

`POST http://example.com/api/auth/login`

### Query Parameters

Parameter | Description
--------- | -----------
email | Email
password | Password
