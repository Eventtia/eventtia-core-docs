# Account Subscriptions

## List Account Subscriptions

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/account_subscriptions/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/', {
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
  "data": [
    {
      "id": "43",
      "type": "account_subscriptions",
      "attributes": {
        "subscription_date": null,
        "stripe_identifier": "stripe_identifier_1",
        "settings": null,
        "status": "processing",
        "stripe_url": null,
        "cancel_at": null,
        "updated_by_id": 1,
        "archived": false,
        "card_number": "8001"
      },
      "relationships": {
        "commercial_plan": {
          "data": {
            "id": "45",
            "type": "commercial_plans"
          }
        }
      }
    }
  ],
  "links": {
    "first": "https://dev-api.eventtia.com/es/v1/account_subscriptions?page=1",
    "last": "https://dev-api.eventtia.com/es/v1/account_subscriptions?page=1",
    "prev": null,
    "next": null
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "plan_id": [
    "must be a string"
  ]
}
```

This endpoint return a list of account subscriptions

***HTTP Request***

`GET /v1/account_subscriptions/`

## Get Account Subscription

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/account_subscriptions/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;id&gt; with the id for the account_subscription to get.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "43",
    "type": "account_subscriptions",
    "attributes": {
      "subscription_date": null,
      "stripe_identifier": "stripe_identifier_1",
      "settings": null,
      "status": "processing",
      "stripe_url": null,
      "cancel_at": null,
      "updated_by_id": 1,
      "archived": false,
      "card_number": "8001"
    },
    "relationships": {
      "commercial_plan": {
        "data": {
          "id": "45",
          "type": "commercial_plans"
        }
      }
    }
  }
}
```

> Example of Account Subscription Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": "Couldn't find AccountSubscription"
}
```

This endpoint return an account subscription

***HTTP Request***

`GET /v1/account_subscriptions/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired account subscription

## Create Account Subscription

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/account_subscriptions/<id>" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
  "data": {
      "type": "account_subscriptions",
      "attributes": {
        "price_id": "<price_id>"
      }
      "relationships": {
        "plan": {
          "data": {
            "id": '<plan_id>',
            "type": 'commercial_plans'
          }
        }
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
      type: "account_subscriptions",
      attributes: {
        price_id: "<price_id>"
      }
      relationships: {
        plan: {
          data: {
            id: '<plan_id>',
            type: 'commercial_plans'
          }
        }
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;plan_id&gt; with the id of the desired commercial plan.

> Make sure you replace &lt;price_id&gt; with the id of the desired price.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "34234",
    "type": "account_subscriptions",
    "attributes": {
      "price_id": "price_1KEwkLHCxGs6xkptcLXtbBlV"
    },
    "relationships": {
      "plan": {
        "data": {
          "id": "43234",
          "type": "commercial_plans"
        }
      }
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "plan_id": [
    "must be a string"
  ]
}
```

This endpoint create an account subscription and return it

***HTTP Request***

`POST /v1/account_subscriptions/`

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
plan_id | string | commercial plan id for this account subscription.
price_id | string | price id for this account subscription.

## Update Account Subscription

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/account_subscriptions/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
  "data": {
      "type": "account_subscriptions",
      "attributes": {
        "price_id": "<price_id>",
        "callbacks_urls": {
          "success_url": "www.success_url.com",
          "cancel_url": "www.cancel_url.com"
        }
      }
      "relationships": {
        "plan": {
          "data": {
            "id": '<plan_id>',
            "type": 'commercial_plans'
          }
        }
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
      type: "account_subscriptions",
      attributes: {
        price_id: "<price_id>",
        callbacks_urls: {
          success_url: "www.success_url.com",
          cancel_url: "www.cancel_url.com"
        }
      }
      relationships: {
        plan: {
          data: {
            id: '<plan_id>',
            type: 'commercial_plans'
          }
        }
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;plan_id&gt; with the id of the desired commercial plan.

> Make sure you replace &lt;price_id&gt; with the id of the desired price.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "34234",
    "type": "account_subscriptions",
    "attributes": {
      "price_id": "price_1KEwkLHCxGs6xkptcLXtbBlV"
    },
    "relationships": {
      "plan": {
        "data": {
          "id": "4343",
          "type": "commercial_plans"
        }
      }
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "plan_id": [
    "must be a string"
  ]
}
```

This endpoint update an account subscription and return it

***HTTP Request***

`PUT /v1/account_subscriptions/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired account subscription

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
plan_id | string | commercial plan id for this account subscription.
price_id | string | price id for this account subscription.
callbacks_urls | json | The stripe success and cancel URL.

## Destroy Account Subscriptions

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/account_subscriptions/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;id&gt; with the id for the account subscription to destroy.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "34234",
    "type": "account_subscriptions",
    "attributes": {
      "price_id": "price_1KEwkLHCxGs6xkptcLXtbBlV"
    },
    "relationships": {
      "plan": {
        "data": {
          "id": "4343",
          "type": "commercial_plans"
        }
      }
    }
  }
}
```

This endpoint destroy a account subscription and return it

***HTTP Request***

`DELETE /v1/account_subscriptions/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired account subscription.

## Change Payment Method

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/account_subscriptions/<id>/change-payment-method" \
  -H 'Content-Type: application/json'\
  -X PUT -d '{
  "data": {
      "type": "account_subscriptions",
      "attributes": {
        "callbacks_urls": {
          "success_url": "www.success_url.com",
          "cancel_url": "www.cancel_url.com"
        }
      }
    }
}'  
```

```javascript
fetch('https://core.eventtia.com/v1/account_subscriptions/<id>/change-payment-method', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
      type: "account_subscriptions",
      attributes: {
        callbacks_urls: {
          success_url: "www.success_url.com",
          cancel_url: "www.cancel_url.com"
        }
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.
> Make sure you replace &lt;id&gt; with the id for the account subscription to change payment method.


> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "session_url": "https://checkout.stripe.com/c/pay/cs_test_c1aP9uiu3067CGjrH0fOfM6UZeMTWzQukO1VY8Wfo9B3Er77oTWVVleudS#fidkdWxOYHwnPyd1blpxYHZxWjA0SUxgRE1GZGZpbndIfzxTYktJYFRdamczPHE3bG9QU3ZAdF1xT1VQM3EyPWxhZ0BdQFRySkk9QnVkMmd2V0pmN21vV0Z0dGdBSlFUUVFnST1VZElnbHxSNTUxX1xOM0NOMycpJ2N3amhWYHdzYHcnP3F3cGApJ2lkfGpwcVF8dWAnPyd2bGtiaWBaZmppcGhrJyknYGtkZ2lgVWlkZmBtamlhYHd2Jz9xd3BgeCUl"
}
```

> Example of Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
      "error": "code: 128"
  }
}
```

This endpoint creates and returns a stripe session URL which allows the user to change his payment method.

***HTTP Request***

`PUT /v1/account_subscriptions/:id/change-payment-method`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired account subscription

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
callbacks_urls | json | The stripe success and cancel URL.
