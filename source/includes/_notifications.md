# Notifications

## List Notifications

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
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
      "id": "62527",
      "type": "notifications",
      "attributes": {
        "name": "Welcome to Ticketing",
        "model": null,
        "entity_type": "User",
        "action": "account_created",
        "event_id": 54,
        "conditions": null
      }
    }
  ]
}
```

This endpoint list notifications belongs to event and return it

### HTTP Request

`GET /v1/events/event_uri/notifications/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>


## Get Notification

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the notification to obtain. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62527",
    "type": "notifications",
    "attributes": {
      "name": "Welcome to Ticketing",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "event_id": 54,
      "conditions": null
    }
  }
}
```

>Example of Not Found (404) response: 

```http
HTTP/1.1 404 Not Found
{
  {
    "message": "Couldn't find Notification"
  }
}
```

This endpoint get an notification and return it

### HTTP Request

`GET /v1/events/event_uri/notifications/id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification


## Create Notification

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/', {
  method: 'POST',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "notification",
    attributes: {
      name: "Welcome to Ticketing",
      entity_type: "User",
      action: "account_created"
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
    "id": "62527",
    "type": "notifications",
    "attributes": {
      "name": "Welcome to Ticketing",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "event_id": 54,
      "conditions": null
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
      "must be a string"
    ]
  }
}
```

This endpoint create an notification and return it

### HTTP Request

`POST /v1/events/:event_uri/notifications/`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | string  | Name for notification
entity_type| string  | Entity type for notification
action     | string | Notification action [account_created, recover_password, attendee_created, attendee_rejected, attendee_confirmed, welcome_email]
conditions  | json | Conditions for notifications

## Update Notification

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "notification",
    attributes: {
      name: "Welcome to Ticketing",
      entity_type: "User",
      action: "account_created"
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update.

> Make sure you replace &lt;id&gt; with the id for the notification to update.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62527",
    "type": "notifications",
    "attributes": {
      "name": "Welcome to Ticketing",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "event_id": 54,
      "conditions": null
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
      "must be a string"
    ]
  }
}
```

This endpoint update an notification and return it

### HTTP Request

`PUT /v1/events/:event_uri/notifications/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | string  | Name for notification
entity_type| string  | Entity type for notification
action      | string | Notification action [account_created, recover_password, attendee_created, attendee_rejected, attendee_confirmed, welcome_email]
conditions  | json | Conditions for notifications

## Destroy Notification
```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': '<your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy.

> Make sure you replace &lt;id&gt; with the id for the notification to update.

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62528",
    "type": "notifications",
    "attributes": {
      "name": "Welcome to Ticketing",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "event_id": 54,
      "conditions": null
    }
  }
}
```

This endpoint destroy an notification and return it

### HTTP Request

`DELETE /v1/events/:event_uri/notifications/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification



## Notification Languages
## Index Notification Languages
```javascript
fetch('https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Make sure you replace &lt;notification_id&gt; with the id for the notification. 

> Example of a successful (200) response:

```shell


```
```http
HTTP/1.1 200 OK
{
    "data": [
    {
            "id": "1",
            "type": "notification_languages",
            "attributes": {
                "locale": "en",
                "subject": "Email created",
                "body": "<div class= 'body'> Hello${name}</div>"
            }
        }
    ]
}
```

> Example of a 404 response:

```http
HTTP/1.1 404 Not Found
{

  "message": "Couldn't find notification language"

}
```
This endpoint list all the available notification language associated with the given notification.
### HTTP Request

`GET v1/events/:event_uri/notifications/:notification_id/notification_languages`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer  | The id for the desired notification

## Get Notification Languages
```javascript
fetch('https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_language/:id', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Make sure you replace &lt;notification_id&gt; with the id for the notification. 

> Make sure you replace &lt;id&gt; with the id for the notification language. 

> Example of a successful (200) response:

```shell


```
```http
HTTP/1.1 200 OK
{
    "data":
    {
            "id": "1",
            "type": "notification_languages",
            "attributes": {
                "locale": "en",
                "subject": "Email created",
                "body": "<div class= 'body'> Hello${name}</div>"
            }
        }
    
}
```

> Example of a 404 response:

```http
HTTP/1.1 404 Not Found
{

  "message": "Couldn't find notification language"

}
```
This endpoint get the available notification language associated with the given notification.
### HTTP Request

`GET v1/events/:event_uri/notifications/:notification_id/notification_language/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer  | The id for the desired notification
id | integer  | The id for the desired notification language

## Create Notification Language
This endpoint allows you to create a new notification language to the given notification.

> To create a new notification language to a notification, use this code:

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages" \
  -H 'Content-Type: application/json' \
  -X POST -d '{
  "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>"
        }
  }
}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
  body: {
    "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>"
        }
  }
  }
})
```
> Example of a successful (200) response:
### HTTP Request

`POST /v1/events/:event_uri/notifications/:notification_id/notification_languages`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification

### Body Parameters
Parameter | Type | Description
--------- | ---- | -----------
locale | string | Supported locales ['es', 'en', 'fr', 'it', 'de', 'ru']
subject | string | Subject for notification.
body    | string | Body for notification.

## Update Notification Language
This endpoint allows you to update a new notification language to the given notification.

> To updatea new notification language to a notification, use this code:

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages/:id" \
  -H 'Content-Type: application/json' \
  -X PUT -d '{
  "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>"
        }
  }
}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages/:id", {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
  body: {
    "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>"
        }
  }
  }
})
```
> Example of a successful (200) response:
### HTTP Request

`PUT /v1/events/:event_uri/notifications/:notification_id/notification_languages/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification
id | integer  | The id for the desired notification language

### Body Parameters
Parameter | Type | Description
--------- | ---- | -----------
locale | string | Supported locales ['es', 'en', 'fr', 'it', 'de', 'ru']
subject | string | Subject for notification.
body    | string | Body for notification.


## Delete Notification Language

> To destroy notification language, use this code:

```javascript
fetch("https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages/:id", {
  method: 'DELETE',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy.

> Make sure you replace &lt;notification_id&gt; with the id for the notification.

> Make sure you replace &lt;id&gt; with the id for the  language to update.

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
   {
    "id": "1",
    "type": "notification_languages",
    "attributes": {
        "locale": "en",
        "subject": "Email created",
        "body": "<div class= 'body'> Hello${name}</div>"
    }
    }
  }
}
```

### HTTP Request

`DELETE v1/events/:event_uri/notifications/:notification_id/notification_languages/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification
id | integer | The id for the notification langauge