# Orders

## List Orders by events or Entity

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/orders/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/orders/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> (Optional) Make sure you include &lt;entity_type&gt; and &lt;entity_id&gt; if you prefer get a list for orders by permitted entities ('Attendee', 'Account', 'Member').

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "51",
    "type": "orders",
    "attributes": {
        "description": "Description for Order",
        "entity_type": "Member",
        "entity_id": 2,
        "total_tax": null,
        "total_amount": "155.0",
        "status": "completed",
        "archived": false,
        "log_info": null,
        "source": "external",
        "event_id": 94,
        "uuid": "8989528989",
        "locale": "en"
    }
        },
}
```

This endpoint list orders belongs to event and return it

***HTTP Request***

`GET /v1/events/:event_uri/orders/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event.
page | json | A page object as described <a href="#pagination">here</a>
entity_type | string | entity type from order, include this parameter if you prefer get a list of orders by entity
entity_id | string | entity id from order, include this parameter if you prefer get a list of orders by entity

## Create Order

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/orders/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
  "data": {
    "type": "orders",
    "attributes": {
      "member": {
          "first_name": "Nombre",
          "last_name": "Name",
          "phone": 55898989,
          "email": "email@eventtia.com"
          },
      "order_items": [
          {
              "description": "description for first item",
              "quantity": 1,
              "entity_type": "AttendeeType",
              "entity_id": 94,
              "unit_amount": 10.0
          },
          {
              "description": "description for second item",
              "quantity": 1,
              "entity_type": "AttendeeType",
              "entity_id": 57,
              "unit_amount": 20.0
          }
      ]
    }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/orders/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    "data": {
    "type": "orders",
    "attributes": {
      "member": {
          "first_name": "Nombre",
          "last_name": "Name",
          "phone": 55898989,
          "email": "email@eventtia.com"
          },
      "order_items": [
          {
              "description": "description for first item",
              "quantity": 1,
              "entity_type": "AttendeeType",
              "entity_id": 94,
              "unit_amount": 10.0
          },
          {
              "description": "description for second item",
              "quantity": 1,
              "entity_type": "AttendeeType",
              "entity_id": 57,
              "unit_amount": 20.0
          }
      ]
    }
    }
  }
}
)
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event .  


> 
> Example of a successful (200) response if your total Amount on your order is 0:

```http
HTTP/1.1 200 OK
{
   "data": {
    "id": "51",
    "type": "orders",
    "attributes": {
        "description": "Description for Order",
        "entity_type": "Member",
        "entity_id": 2,
        "total_tax": null,
        "total_amount": "155.0",
        "status": "completed",
        "archived": false,
        "log_info": null,
        "source": "external",
        "event_id": 94,
        "uuid": "8989528989",
        "locale": "en"
    }
    },
}
```

Example of a successful (200) response if your order requires a payment:

https://checkout.stripe.com/c/pay/9TjB9VUx0NTVtZjNfTUJiRicpJ2N3amhWYHdzY
>Example of Unprocessable Entity (400) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "error": [
            {
          "member": [ "Email code: 328"]
            }
        ]
  }
}
```

This endpoint create an order and return it unless your order requires a payment.

***HTTP Request***

`GET /v1/events/:event_uri/orders/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event

### Member Parameters

Parameter  |  Type  | Description
---------  | -------| -----------
first_name       | string | first name for member
last_name |  string  | last_name for member
phone    | integer | phone for member
email  | string| email for member

### Order Items Parameters

Parameter  |  Type  | Description
---------  | -------| -----------
description  | string | description for order item
quantity |  integer | quantity for order item
entity_type |  string | entity type belongs to order item (Attendee, Account, Member)
entity_id   | integer| entity type belongs to order item
unit_amount | float | prize for order item