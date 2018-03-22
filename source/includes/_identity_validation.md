# Identity Validation

## Create validation

This API call submits a validation to Equifax with personal details

> Creates a fund order and returns it

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"identity_validation": { "first_name": "John", "last_name": "Doe", "dob": "1982-11-11", "address_1": "123 Main St.", "city": "Toronto", "postal": "M2M2J2", "country": "Canada", "province": "ON" }}'
"http://example.com/api/identity_validation"
```

> The above command returns JSON structured like this:

```json
{
  "status": "valid"
}  
```

### HTTP Request

`POST http://example.com/api/identity_validation`

### Query Parameters

Parameter | Description |
--------- | ----------- |
first_name | First name |
last_name | Last name |
address_1 | Address including street number |
address_2 | Optional |
province | Province code (ie. ON) |
city | City |
postal | Postal code |
dob | Date of birth |




