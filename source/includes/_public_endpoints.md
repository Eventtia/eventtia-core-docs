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


## List Public Widget Settings

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/widget_settings/<widget_setting_id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/widget_settings/<widget_setting_id>', {
  method: 'GET'
})
```

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;widget setting id&gt; with the widget id for the event.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
 "data": {
        "id": "1",
        "type": "widget_settings",
        "attributes": {
            "access_button": {
                "en": "buy ticket"
            },
            "main_color": "#333333",
            "secondary_color": "#EEEEEE",
            "header_text_color": "#DDDDDD",
            "css": "body: {passing-left: 10px}",
            "logo": "url_file",
            "header_image": "url_file"
        },
        "relationships": {
            "event": {
                "data": {
                    "id": "54",
                    "type": "events"
                }
            }
        }
    }
}
```

This endpoint list widget settings belongs to event and return it

### HTTP Request

`GET /v1/events/:event_uri/widget_settings/:widget_setting_id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event.
widget_seting_id | integer  | The widget_setting_id for the desired widget_setting.



## Public Authentication

> To authenticate, use this code:

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/public/events/<event_uri>/sessions" \
  -H 'Content-Type: application/json' \
  -X POST -d '{"email":"email@example.org", "uuid":"uuid"}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/public/events/<event_uri>/sessions", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: {
    email: "email@example.org",
    uuid: "uuid"
  }
})
```

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{"token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJjbGFzcyI6IlVzZXIiLCJhdXRoZW50aWNhdGlvbl9rZXkiOiJ0ZXN0QGV2ZW50dGlhLmNvbSVyaSI6InRlc3QtZXZlbnQiLCJleHAiOjE1MjAzNTY1MDB9.s0m351gn4tuRe4sdF_qw3rTleleWh4TTTt35f1n4lLy"}
```

> Example of a 404 response:

```http
HTTP/1.1 404 Not Found
{"message":"Incorrect email or uuid."}
```

You can get an authorization token for a Member or Attendee with this endpoint. Tokens issued by Eventtia are valid for 1 day.

### HTTP Request

`POST /v1/public/events/event_uri/sessions`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
email | string | email for attendee or member.
uuid | string | uuid for permitted entities (Orders, Tickets).

