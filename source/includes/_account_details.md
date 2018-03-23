# Account Details

## Get account details

This API call returns the account details of the currently logged in user

> Returns the account details of the user id present in the JWT (currently logged in)

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"order": { "from_currency_id": 1, "to_currency_id": 2, "amount_fractional": 0.01, "type": "BuyOrder"}}'
"http://example.com/api/account_details"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "attributes": {
      "first-name": "John",
      "last-name": "Doe",
      "address-1": "123 Main St",
      "address-2": null,
      "city": "Toronto",
      "postal": "L1v2N5",
      "province": "ON",
      "dob": "1983-12-12"
    },
    "type": "account_details"
  }
}
```

### HTTP Request

`POST http://example.com/api/account_details`


## Create validation

This API call submits a validation to Equifax with personal details

> Creates a fund order and returns it

```shell
curl 
-X POST
-H "Content-Type: application/json"
-H "Accept: application/vnd.coinberry.v1+json"
-H "Authorization: Bearer eyJhbGciOiJIUzI1NiJ9.eyJ1c2VyX2lkIjoxLCJleHAiOjE1MTk5NDkyMDR9.MAPyjxWmxGndSP6U0R5j7LMjnXAKTE7gYge61beJngs"
-d '{"account_detail": { "first_name": "John", "last_name": "Doe", "dob": "1982-11-11", "address_1": "123 Main St.", "city": "Toronto", "postal": "M2M2J2", "country": "Canada", "province": "ON" }}'
"http://example.com/api/account_details"
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "attributes": {
      "status": "valid"
    },
    "type": "account_details"
  }
}
```

### HTTP Request

`POST http://example.com/api/account_details`

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
