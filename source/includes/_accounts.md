# Accounts

## Stripe Onboarding

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/accounts/stripe-onboarding" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/accounts/stripe-onboarding', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```
> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "meta": {
      "url": "https://connect.stripe.com/setup/e/acct_1N1bJMCmji3XU9iA/eX7Ex5XHTWbR"
    }
}
```

> Example of Not Found y (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
      "error": "code: 128"
    }
}
```

This endpoint return a link of stripe onboarding

***HTTP Request***

`GET /v1/accounts/stripe-onboarding`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
callbacks_urls[success_url] | json | Send of key (success_url) and value (refresh_url)
callbacks_urls[cancel_url] | json | Send of key (cancel_url) and value (return_url)

## Details

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/accounts/details" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/accounts/details', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```
> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "3",
    "type": "accounts",
    "attributes": {
      "name": "VIP dos",
      "website": null,
      "ip": "172.0.0.0",
      "country": null,
      "latitude": null,
      "longitude": null,
      "uuid": "09e3fc66-e9f5-4915-b",
      "activation_code": "a1d20463-7caa-45c2-a",
      "activation_date": null,
      "active": true,
      "level": "paid",
      "payments_enabled": null
    }
  }
}
```

This endpoint return account details

***HTTP Request***

`GET /v1/accounts/details`
