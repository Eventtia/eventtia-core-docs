# Speakers

## List Speaker

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/speakers/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/speakers/', {
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
  "data": {
  "id": "14",
  "type": "speakers",
    "attributes": {
      "name": "Mary",
      "last_name": "Perez Ossa",
      "email": "mary@email.com",
      "biography": "biography Mary",
      "twitter": "Twitter Mary",
      "website": "Website Mary",
      "photo": "url_img_file"
      }
    }
}
```

This endpoint list speakers belongs to event and return it

***HTTP Request***

`GET /v1/events/:event_uri/speakers/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>

***Body Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
name | string  | Filters results by the speaker name.
last_name | string  | Filters results by the speaker last_name.
email | string  | Filters results by the speaker email.
fullname | string  | Filters results by the speaker concat name and last_name.
keywords | string  | Filters results by the speaker match name ,last_name and email.

## Get Speaker

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the speaker to obtain. 

> Example of a successful (200) response:


```http
HTTP/1.1 200 OK
{
  "data": {
  "id": "14",
  "type": "speakers",
    "attributes": {
      "name": "Mary",
      "last_name": "Perez Ossa",
      "email": "mary@email.com",
      "biography": "biography Mary",
      "twitter": "Twitter Mary",
      "website": "Website Mary",
      "photo": "url_image_file"
      }
    }
}
```

>Example of Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  {
    "message": "Couldn't find Speaker"
  }
}
```

This endpoint get a speaker and return it

***HTTP Request***

`GET /v1/events/:event_uri/speaker/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired speaker


## Create Speaker

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/speakers/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
   "data": {
        "type": "speakers",
        "attributes": {
          "name": "Mary",
          "last_name": "Perez Ossa",
          "email": "mary@email.com",
          "biography": "biography Mary",
          "twitter": "Twitter Mary",
          "website": "Website Mary",
          "photo": "url_image_file"
        }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/speakers/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
        type: "speakers",
        attributes: {
          name: "Mary",
          last_name: "Perez Ossa",
          email: "mary@email.com",
          biography: "biography Mary",
          twitter: "Twitter Mary",
          website: "Website Mary",
          photo: "url_image_file"
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
    "id": "14",
    "type": "speakers",
    "attributes": {
      "name": "Mary",
      "last_name": "Perez Ossa",
      "email": "mary@email.com",
      "biography": "biography Mary",
      "twitter": "Twitter Mary",
      "website": "Website Mary",
      "photo": "url_image_file"
      }
    }
}
```

>Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "name": [
      "can't be blank"
    ],
    "email": [
      "can't be blank"
    ]
    }
}
```

This endpoint create a speaker and return it

***HTTP Request***

`POST /v1/events/:event_uri/speakers`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
name      | string | name of speaker.
last_name | string | last name of speaker.
email     | string | email of speaker.
biography | text | biography of speaker.
twitter   | string | speaker twitter account.
website   | string| speaker website.
photo     | file | image for this speaker.

## Update Speaker

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
   "data": {
        "type": "speakers",
        "attributes": {
          "name": "Mary",
          "last_name": "Perez Ossa",
          "email": "mary@email.com",
          "biography": "biography Mary",
          "twitter": "Twitter Mary",
          "website": "Website Mary",
          "photo": "url_image_file"
        }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  body: {
    data: {
        type: "speakers",
        attributes: {
          name: "Mary",
          last_name: "Perez Ossa",
          email: "mary@email.com",
          biography: "biography Mary",
          twitter: "Twitter Mary",
          website: "Website Mary",
          photo: "url_image_file"
        }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update.

> Make sure you replace &lt;id&gt; with the id for the speaker to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  {
  "data": {
    "id": "14",
    "type": "speakers",
    "attributes": {
      "name": "Mary",
      "last_name": "Perez Ossa",
      "email": "mary@email.com",
      "biography": "biography Mary",
      "twitter": "Twitter Mary",
      "website": "Website Mary",
      "photo": "url_image_file"
      }
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
      "invalid email format"
    ]
  }
}
```

This endpoint update a speaker and return it

***HTTP Request***

`PUT /v1/events/:event_uri/speakers/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired speaker

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
name      | string | name of speaker.
last_name | string | last name of speaker.
email     | string | email of speaker.
biography | text | biography of speaker.
twitter   | string | speaker twitter account.
website   | string| speaker website.
photo     | file | image for this speaker.

## Destroy Speaker

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/speakers/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy.

> Make sure you replace &lt;id&gt; with the id for the speaker to update.

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "14",
    "type": "speakers",
    "attributes": {
      "name": "Mary",
      "last_name": "Perez Ossa",
      "email": "mary@email.com",
      "biography": "biography Mary",
      "twitter": "Twitter Mary",
      "website": "Website Mary",
      "photo": "url_image_file"
      }
    }
}
```

This endpoint destroy a speaker and return it

***HTTP Request***

`DELETE /v1/events/:event_uri/speakers/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired speaker
