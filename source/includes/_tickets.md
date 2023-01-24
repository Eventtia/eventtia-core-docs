# Tickets

## List Tickets

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/orders/<order_uuid>/tickets" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/orders/<order_uuid>/tickets', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

> Make sure you replace &lt;order uuid&gt; with the uuid for the order .

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
        "id": "45",
        "type": "tickets",
        "attributes": {
            "assigned_to": "email@eventtia.com",
            "uuid": "c0b042d63b",
            "assigned_date": "2022-10-20T14:53:52.000Z",
            "assigned_by_id": 1,
            "archived": false
        }
    }
  ]
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "error": [
      "code: 128"
    ]
  }
}
```

This endpoint list tickets and return it

### HTTP Request

`GET /v1/events/<event_uri>/orders/<order_uuid>/tickets`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
order_uuid  | string | order uuid to which order belongs

## Get Ticket

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/orders/<order_uuid>/tickets/<ticket_uuid>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/orders/<order_uuid>/tickets/<ticket_uuid>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

> Make sure you replace &lt;order uuid&gt; with the uuid for the order .

> Make sure you replace &lt;ticket uuid&gt; with the uuid for the ticket .

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
      "id": "45",
      "type": "tickets",
      "attributes": {
          "assigned_to": "email@eventtia.com",
          "uuid": "c0b042d63b",
          "assigned_date": "2022-10-20T14:53:52.000Z",
          "assigned_by_id": 1,
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
    "error": [
      "code: 128"
    ]
  }
}
```

This endpoint get a ticket and return it

### HTTP Request

`GET /v1/events/<event_uri>/orders/<order_uuid>/tickets/<ticket_uuid>`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
order_uuid  | string | order uuid to which order belongs
ticket_uuid  | string | ticket uuid to which ticket belongs
