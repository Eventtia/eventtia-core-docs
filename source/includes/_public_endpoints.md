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

`GET /v1/public/events/:event_uri/attendee_types/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>


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
  -X POST -d '{"recaptcha_token": "","email":"email@example.org", "uuid":"uuid"}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/public/events/<event_uri>/sessions", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: {
    recaptcha_token: "",
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

`POST /v1/public/events/:event_uri/sessions`

### Query Parameters

Parameter | Type | Description
--------- | ---- | -----------
email | string | email for attendee or member.
uuid | string | uuid for permitted entities (Orders, Tickets).

## Create Public Attendees

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/public/events/<event_uri>/attendees/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
    "data": {
      "type": "attendees",
      "attributes": {
        "attendee_type_id": 34,
        "first_name": "Mary",
        "last_name": "perez ossa",
        "email": "maryperez@email.com",
        telephone": "+56912345678",
        "updated_by_id": 192,
        "archived": false,
        "fields_data": {
          "f281": "george",
          "f282": "downtown"
        },
        "photo_url": "url_Image_file"
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/attendees/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your public token>',
  },
  body: {
    data: {
      type: "attendees",
      attributes: {
        attendee_type_id: 34,
        first_name: "Mary",
        last_name: "perez ossa",
        email: "maryperez@email.com",
        telephone: "+56912345678",
        updated_by_id: 192,
        archived: false,
        fields_data: {
          "f281": "george",
          "f282": "downtown"
        },
        photo_url: "url_Image_file"
      }
    }
  }
})
```

> Make sure you replace &lt;your public token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "6264284",
    "type": "attendees",
    "attributes": {
      "first_name": "Rosa Maria",
      "last_name": "Rosales Rojas",
      "email": "rosales@email.com",
      "telephone": "+56912345678",
      "updated_by_id": "10461",
      "archived": "false",
      "fields_data": {
        "f281": "george",
        "f282": "downtown"
      },
      "photo_url": "url_Image_file"
    }
  }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "email": [
      "already taken"
    ]
  }
}
```

This public endpoint create an attendee and return it
### HTTP Request

`POST /v1/public/events/:event_uri/attendees/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
first_name | string  | first name for attendee
last_name  | string  | last name for attendee
email      | string  | email for attendee
telephone  | integer | telephone for attendee
attendee_type_id | integer | attendee type id who created attendee belongs
fields_data | hash | key-value for custom fields data for created attendee
photo      |  file   | photo for attendee

## Update Public Attendee

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/public/events/<event_uri>/attendees/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
      "type": "attendees",
      "attributes": {
        "attendee_type_id": 34,
        "first_name": "Mary",
        "last_name": "perez ossa",
        "email": "maryperez@email.com",
        telephone": "+56912345678",
        "updated_by_id": 192,
        "archived": false,
        "fields_data": {
          "f281": "george",
          "f282": "downtown"
        },
        "photo_url": "url_Image_file"
      }
    }
}'

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/attendees/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your public token>',
  },
  body: {
    data: {
      type: "attendees",
      attributes: {
        attendee_type_id: 34,
        first_name: "Mary",
        last_name: "perez ossa",
        email: "maryperez@email.com",
        telephone: "+56912345678",
        updated_by_id: 192,
        archived: false,
        fields_data: {
          "f281": "george",
          "f282": "downtown"
        },
        photo_url: "url_Image_file"
      }
    }
  }
}
})
```

> Make sure you replace &lt;your public token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update.

> Make sure you replace &lt;id&gt; with the id for the attendee to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62527",
    "type": "attendees",
    "attributes": {
     "first_name": "Mary",
      "last_name": "perez ossa",
      "email": "maryperez@email.com",
      "telephone": "+56912345678",
      "updated_by_id": "192",
      "archived": "false",
      "fields_data": {
        "f281": "george",
        "f282": "downtown"
      },
      "photo_url": "url_Image_file"
    }
  }
}
```

>Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "email": [
      "already taken"
    ]
  }
}
```

This public endpoint update an attendee and return it

### HTTP Request

`PUT /v1/public/events/:event_uri/attendees/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
first_name | string  | first name for attendee
last_name  | string  | last name for attendee
email      | string  | email for attendee
telephone  | integer | telephone for attendee
attendee_type_id | integer | attendee type id who created attendee belongs
fields_data | hash | key-value for custom fields data for created attendee
photo      |  file   | photo for attendee



## List Public Tickets

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/public/events/<event_uri>/tickets" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/tickets', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your public token>',
  }
})
```

> Make sure you replace &lt;your public token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

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

This endpoint list public tickets and return it

### HTTP Request

`GET /v1/public/events/<event_uri>/tickets`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event

### Include Options

Value |  Type   | Description
----- | ------- | -----------
attendee| string | Include attendee relationships

## Get Public Ticket

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/public/events/<event_uri>/tickets/<ticket_uuid>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/tickets/<ticket_uuid>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your public token>',
  }
})
```

> Make sure you replace &lt;your public token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

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

This endpoint get a public ticket and return it

### HTTP Request

`GET /v1/public/events/<event_uri>/tickets/<ticket_uuid>`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
ticket_uuid  | string | ticket uuid to which ticket belongs

### Include Options

Value |  Type   | Description
----- | ------- | -----------
attendee| string | Include attendee relationships

## Assign Public Ticket

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/public/events/<event_uri>/tickets/assign" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
    "data": {
      "type": "tickets",
          "attributes": {
              "uuid": "c0b042d63b",
              "assigned_to": "email@eventtia.com"
          }
    }
  }'
```

```javascript
fetch('https://core.eventtia.com/v1/public/events/<event_uri>/tickets/assign', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your public token>',
  },
  body: {
    data: {
      type: "tickets",
      attributes: {
        uuid: "c0b042d63b",
        assigned_to: "pierre@eventtia.com"
      }
    }
}
})
```

> Make sure you replace &lt;your public token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event .

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
      {"error:code: 128"}
    ]
  }
}
```

This endpoint assign a public ticket and return it,

### HTTP Request

`POST /v1/public/events/:event_uri/tickets/assign`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
uuid | string  | uuid to which ticket belongs
assigned_to  | string | email to which ticket belongs
