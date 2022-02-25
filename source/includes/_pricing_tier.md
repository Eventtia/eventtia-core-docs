# Pricing Tier

## List Pricing Tiers

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/pricing_tiers/?entity_id=<entity_id>&entity_type=<entity_type>', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to pricing tier to list.

> Make sure you replace &lt;entity type> as string with the name of the entity associated to pricing tier to list.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "pricing_tiers",
    "attributes": {
      "price": "99.0",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "entity_id": 62523,
      "entity_type": "AttendeeType",
      "archived": false
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "price": [
      "must be an integer"
    ]
  }
}
```

This endpoint list pricing tiers and return it

### HTTP Request

`GET /v1/events/:event_uri/pricing_tiers/?entity_id=:entity_id&entity_type=:entity_type`

### Path Parameters

| Parameter   | Type    | Description                               |
| ----------- | ------- | ----------------------------------------- |
| event_uri   | string  | The event_uri for the desired event       |
| entity_id   | integer | entity id to which pricing tier belongs   |
| entity_type | string  | entity type to which pricing tier belongs |

## Get Pricing Tier

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/pricing_tiers/<id>', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the pricing tier to get.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "pricing_tiers",
    "attributes": {
      "price": "99.0",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "entity_id": 62523,
      "entity_type": "AttendeeType",
      "archived": false
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "price": [
      "must be an integer"
    ]
  }
}
```

This endpoint get a pricing tier and return it

### HTTP Request

`GET /v1/events/:event_uri/pricing_tiers/:id`

### Path Parameters

| Parameter | Type    | Description                         |
| --------- | ------- | ----------------------------------- |
| event_uri | string  | The event_uri for the desired event |
| id        | integer | The id for the desired pricing tier |

## Create Pricing Tier

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/pricing_tiers/', {
  method: 'POST',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "pricing_tier",
    attributes: {
      entity_id: <entity id>,
      entity_type: <entity type>,
      start_date: "2013-03-03",
      end_date: "2013-03-23",
      price: 99
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to pricing tier to create.

> Make sure you replace &lt;entity type> as integer with the number for the entity associated to pricing tier to create.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "pricing_tiers",
    "attributes": {
      "price": "99.0",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "entity_id": 62523,
      "entity_type": "AttendeeType",
      "archived": false
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "price": [
      "must be an integer"
    ]
  }
}
```

This endpoint create a pricing tier and return it, , Entities supported : AttendeeType.

### HTTP Request

`POST /v1/events/:event_uri/pricing_tiers/`

### Body Parameters

| Parameter   | Type    | Description                               |
| ----------- | ------- | ----------------------------------------- |
| entity_id   | integer | entity id to which pricing tier belongs   |
| entity_type | string  | entity type to which pricing tier belongs |
| start_date  | date    | start date for pricing tier               |
| end_date    | date    | end date for pricing tier                 |
| price       | float   | price for pricing tier                    |

## Update Pricing Tier

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/pricing_tiers/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "pricing_tier",
    attributes: {
      entity_id: <entity id>,
      entity_type: <entity type>,
      start_date: "2013-03-03",
      end_date: "2013-03-23",
      price: 99
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update.

> Make sure you replace &lt;id&gt; with the id for the pricing tier to update.

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to pricing tier to update.

> Make sure you replace &lt;entity type> as integer with the nunmber for the entity associated to pricing tier to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "pricing_tiers",
    "attributes": {
      "price": "99.0",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "entity_id": 62523,
      "entity_type": "AttendeeType",
      "archived": false
    }
  }
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "price": [
      "must be an integer"
    ]
  }
}
```

This endpoint update a pricing tier and return it, Entities supported : AttendeeType.

### HTTP Request

`PUT /v1/events/:event_uri/pricing_tiers/:id`

### Path Parameters

| Parameter | Type    | Description                         |
| --------- | ------- | ----------------------------------- |
| event_uri | string  | The event_uri for the desired event |
| id        | integer | The id for the desired pricing tier |

### Body Parameters

| Parameter   | Type    | Description                               |
| ----------- | ------- | ----------------------------------------- |
| entity_id   | integer | entity id to which pricing tier belongs   |
| entity_type | string  | entity type to which pricing tier belongs |
| start_date  | date    | start date for pricing tier               |
| end_date    | date    | end date for pricing tier                 |
| price       | float   | price for pricing tier                    |

## Destroy Pricing Tier

```javascript
fetch("https://core.eventtia.com/v1/events/<event_uri>/pricing_tiers/<id>", {
  method: "DELETE",
  headers: {
    Authorization: "<your token>",
  },
});
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy.

> Make sure you replace &lt;id&gt; with the id for the pricing tier to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36453",
    "type": "pricing_tiers",
    "attributes": {
      "price": "24.0",
      "start_date": "2013-02-08T19:00:00.000-05:00",
      "end_date": "2013-02-11T19:00:00.000-05:00",
      "entity_id": 62523,
      "entity_type": "AttendeeType",
      "archived": true
    }
  }
}
```

This endpoint destroy a pricing tier and return it

### HTTP Request

`DELETE /v1/events/:event_uri/pricing_tiers/:id`

### Path Parameters

| Parameter | Type    | Description                         |
| --------- | ------- | ----------------------------------- |
| event_uri | string  | The event_uri for the desired event |
| id        | integer | The id for the desired pricing tier |
