# Public Endpoints

## Get Public Event

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/public/events/<event_uri>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>', {
  method: 'GET'})
```
> Make sure you replace &lt;event uri&gt; with the event uri for the event to get

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    id: "21",
    "type": "events",
    "attributes": {
      "name": "Event name",
      "description": "description of an event",
      "start_date": "2020-04-13 15:54:37 -0500",
      "end_date": "2020-04-15 15:54:57 -0500",
      "attendance_mode": "online",
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "banner": {
        "filename": "file_name",
        "thumb": "url_image",
        "small":  "url_image",
        "medium": "url_image",
        "large": "url_image",
      },
      logo: {
       "filename": "file_name",
        "thumb": "url_image",
        "small":  "url_image",
        "medium": "url_image",
        "large": "url_image",
      }
    },
    "relationships": {
      "settings": {
        "data": {
          "id": "108",
          "type": "settings"
        }
      }
    }
  }
}
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": "Couldn't find Event"
}
```

This endpoint return an event

### HTTP Request

`GET /v1/public/events/:event_uri`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### HTTP Request for optional include settings

`GET /v1/events/:event_uri/include=settings`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
include   | string | The value settings gives informations for each relationships (settings or attendees)


## List Public Attendee Types

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/public/events/<event_uri>/attendee_types/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/attendee_types/', {
  method: 'GET',
})
```
> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
      "id": "62527",
      "type": "attendee_types",
      "attributes": {
        "name": {"en": "Attendee type name"},
        "description": {"en": "attendee_type_description"},
        "price": 34.2,
        "limit": 25,
        "allow_public_registration": false,
      }
    }
  ]
}
```

This endpoint list attendee types belongs to event and available for public registration.

### HTTP Request

`GET /v1/public/events/event_uri/attendee_types/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>
available_seats | boolean | Activate an optional attribute (seats availability)