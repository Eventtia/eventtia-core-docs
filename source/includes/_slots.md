# Slots

## List Slots

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/slots/?entity_id=<entity_id>&entity_type=<entity_type>', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event . 

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to slots to list. 

> Make sure you replace &lt;entity type&gt; with the name of the entity associated to slots to list.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "slots",
    "attributes": {
      "entity_id": 62523,
      "entity_type": "Workshop",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "limit": 20,
      "archived": false
    }
  }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "limit": [
      "must be an integer"
    ]
  }
}
```

This endpoint list pricing tiers and return it

### HTTP Request

`GET /v1/events/:event_uri/slots/?entity_id=:entity_id&entity_type=:entity_type`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
entity_id  | integer | entity id to which slots belongs
entity_type| string  | entity type to which slots belongs

## Create Slots

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/slots/', {
  method: 'POST',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "slot",
    attributes: {
      entity_id: <entity id>,
      entity_type: <entity type>,
      start_date: "2013-03-03T19:00:00.000-05:00", 
      end_date: "2013-03-23T19:30:00.000-05:00", 
      limit: 99
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event . 

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to slots to create. 

> Make sure you replace &lt;entity type> as integer with the number for the entity associated to slots to create.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "slots",
    "attributes": {
      "entity_id": 62523,
      "entity_type": "Workshop",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "limit": 20,
      "archived": false
    }
  }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "limit": [
      "must be an integer"
    ]
  }
}
```

This endpoint create a slots and return it, , Entities supported : Workshop.

### HTTP Request

`POST /v1/events/:event_uri/slots/`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
entity_id  | integer | entity id to which slots belongs
entity_type| string  | entity type to which slots belongs
start_date | date    | start date for slot
end_date   | date    | end date for slot
limit      | integer  | price for slot

## Update Slots

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/slots/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "slot",
    attributes: {
      entity_id: <entity id>,
      entity_type: <entity type>,
      start_date: "2013-03-03T19:00:00.000-05:00", 
      end_date: "2013-03-23T19:00:00.000-05:00", 
      limit: 99
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update. 

> Make sure you replace &lt;id&gt; with the id for the slots to update. 

> Make sure you replace &lt;entity id&gt; with the id for the entity associated to slot to update. 

> Make sure you replace &lt;entity type> as integer with the nunmber for the entity associated to slot to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36457",
    "type": "slots",
    "attributes": {
      "entity_id": 62523,
      "entity_type": "Workshop",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "limit": 20,
      "archived": false
    }
  }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "limit": [
      "must be an integer"
    ]
  }
}
```

This endpoint update a slots and return it, Entities supported : Workshop.

### HTTP Request

`PUT /v1/events/:event_uri/slots/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired slots
### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
entity_id  | integer | entity id to which slots belongs
entity_type| string  | entity type to which slots belongs
start_date | date    | start date for slots
end_date   | date    | end date for slots
limit      | integer   | limit for slots

## Destroy Slots
```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/slots/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': '<your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy. 

> Make sure you replace &lt;id&gt; with the id for the slots to update. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "36453",
    "type": "slots",
    "attributes": {
      "entity_id": 62523,
      "entity_type": "Workshop",
      "start_date": "2013-03-02T19:00:00.000-05:00",
      "end_date": "2013-03-22T19:00:00.000-05:00",
      "limit": 20,
      "archived": true
    }
  }
}
```

This endpoint destroy a slots and return it

### HTTP Request

`DELETE /v1/events/:event_uri/slots/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired slots

