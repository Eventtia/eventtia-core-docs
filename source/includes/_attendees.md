# Attendees

## List Attendees

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/attendees/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendees/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
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
  ]
}
```

This endpoint list attendees belongs to event and return it

***HTTP Request***

`GET /v1/events/:event_uri/attendees/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>
first_name | string | Filters results by the attendee's first name.
last_name | string | Filters results by the attendee's last name.
email | string | Filters results by the attendee's email.
telephone | string | Filters results by the attendee's telephone.
attendee_type_id | integer | Filters results by attendee type.
event_id | integer | Filters results by event
user_id | integer | Filters results by user


## Get Attendee

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the attendee to obtain.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
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
  ]
}
```

>Example of Not Found (404) response: 

```http
HTTP/1.1 404 Not Found
{
  {
    "message": "Couldn't find Attendee"
  }
}
```

This endpoint get an attendee and return it

***HTTP Request***

`GET /v1/events/:event_uri/attendees/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee

## Create Attendee

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/attendees/" \
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
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendees/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
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

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

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

This endpoint create an attendee and return it
***HTTP Request***

`POST /v1/events/:event_uri/attendees/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event

***Body Parameters***

Parameter  |  Type   | Description
---------  | ------- | -----------
first_name | string  | first name for attendee
last_name  | string  | last name for attendee
email      | string  | email for attendee
telephone  | integer | telephone for attendee
attendee_type_id | integer | attendee type id who created attendee belongs
fields_data | hash | key-value for custom fields data for created attendee
photo      |  file   | photo for attendee

## Update Attendee

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>" \
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
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
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

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

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

This endpoint update an attendee and return it

***HTTP Request***

`PUT /v1/events/:event_uri/attendees/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee

***Body Parameters***

Parameter  |  Type   | Description
---------  | ------- | -----------
first_name | string  | first name for attendee
last_name  | string  | last name for attendee
email      | string  | email for attendee
telephone  | integer | telephone for attendee
attendee_type_id | integer | attendee type id who created attendee belongs
fields_data | hash | key-value for custom fields data for created attendee
photo      |  file   | photo for attendee

## Destroy Attendee

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>" \
  -H 'Content-Type: application/json'
```


```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendees/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy. 

> Make sure you replace &lt;id&gt; with the id for the attendeeto update. 

>Example of a successful (200) response:

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
      "archived": "true",
      "fields_data": {
        "f281": "george",
        "f282": "downtown"
      },
      "photo_url": "url_Image_file"
    }
  }
}
```

This endpoint destroy an attendee and return it

***HTTP Request***

`DELETE /v1/events/:event_uri/attendees/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee

