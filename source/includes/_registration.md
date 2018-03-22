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
