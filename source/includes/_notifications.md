# Notifications

## List Notifications

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/notifications/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/', {
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
      "id": "62527",
      "type": "notifications",
      "attributes": {
        "name": "Welcome to Ticketing",
        "description": "description for a notification",
        "model": null,
        "entity_type": "User",
        "action": "account_created",
        "conditions": null
      },
    "relationships": {
      "events": {
        "data": {
            "id": "54",
            "type": "events"
          }
      },
      "created_by": {
        "data": {
            "id": "2",
            "type": "users"
          }
      }
    }
    }
  ]
}
```

This endpoint list notifications belongs to event and return it

***HTTP Request***

`GET /v1/events/:event_uri/notifications/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>


## Get Notification

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
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
      "description": "description for a notification",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "conditions": null
    },
    "relationships": {
      "events": {
        "data": {
            "id": "54",
            "type": "events"
          }
      },
      "created_by": {
        "data": {
            "id": "2",
            "type": "users"
          }
      }
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

***HTTP Request***

`GET /v1/events/:event_uri/notifications/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification


## Create Notification

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/notifications/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
   "data": {
    "type": "notification",
    "attributes": {
      "name": "Welcome to Ticketing",
      "description": "description for a notification",
      "entity_type": "User",
      "mass_notification": false,
      "action": "account_created"
    }
  }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  data: {
    type: "notification",
    attributes: {
      name: "Welcome to Ticketing",
      description: "description for a notification",
      entity_type: "User",
      mass_notification: false,
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
      "description": "description for a notification",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "conditions": null,
      "type": "SingleNotification"
    },
    "relationships": {
      "events": {
        "data": {
            "id": "54",
            "type": "events"
          }
      },
      "created_by": {
        "data": {
            "id": "2",
            "type": "users"
          }
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
    "name": [
      "must be a string"
    ]
  }
}
```

This endpoint create an notification and return it

***HTTP Request***

`POST /v1/events/:event_uri/notifications/`

***Body Parameters***

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | string  | Name for notification
description | string | Description for notification
entity_type| string  | Entity type for notification
action     | string | Notification action [account_created, recover_password, attendee_created, attendee_rejected, attendee_confirmed, welcome_email]
conditions  | json | Conditions for notifications
mass_notification  | boolean | Flag to identify if the notification that is going to be created is massive

## Update Notification

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
   "data": {
    "type": "notification",
    "attributes": {
      "name": "Welcome to Ticketing",
      "description": "description for a notification",
      "entity_type": "User",
      "mass_notification": false,
      "action": "account_created"
    },    
    "relationships": {
      "user": {
      "data": [
        {"type": "User", id: 1},
        {"type": "User", id: 2}
        ]
      }
    }
  }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  data: {
    type: "notification",
    attributes: {
      name: "Welcome to Ticketing",
      description: "description for a notification",
      entity_type: "User",
      mass_notification: false,
      action: "account_created"
    },
    relationships: {
      user: {
      data: [
        {type: "User", id: 1},
        {type: "User", id: 2}
        ]
      }
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
      "description": "description for a notification",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "conditions": null,
      "type": "SingleNotification"
    },
    "relationships": {
      "events": {
        "data": {
            "id": "54",
            "type": "events"
          }
      },
      "created_by": {
        "data": {
            "id": "2",
            "type": "users"
          }
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
    "name": [
      "must be a string"
    ]
  }
}
```

This endpoint update an notification and return it

***HTTP Request***

`PUT /v1/events/:event_uri/notifications/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification

***Body Parameters***

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | string  | Name for notification
description | string | Description for notification
entity_type| string  | Entity type for notification
action      | string | Notification action [account_created, recover_password, attendee_created, attendee_rejected, attendee_confirmed, welcome_email]
conditions  | json | Conditions for notifications
mass_notification  | boolean | Flag to identify if the notification that is going to be created is massive
attendee_types  | hash | Attendee_types ids for this notification
users  | hash | User ids ids for this notification
members  | hash | Member ids for this role


## Destroy Notification

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
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
      "description": "description for a notification",
      "model": null,
      "entity_type": "User",
      "action": "account_created",
      "conditions": null,
      "type": "SingleNotification"
    },
    "relationships": {
      "events": {
        "data": {
            "id": "54",
            "type": "events"
          }
      },
      "created_by": {
        "data": {
            "id": "2",
            "type": "users"
          }
      }
    }
  }
}
```

This endpoint destroy an notification and return it

***HTTP Request***

`DELETE /v1/events/:event_uri/notifications/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification



## Send Notification

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>/deliver" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>/deliver', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
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
  "status": 200
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

This endpoint sends mass notification and return it

***HTTP Request***

`GET /v1/events/:event_uri/notifications/:id/deliver`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired notification


## Stats Notification

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>/stats" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/<id>/stats', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
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
  "meta": {
    "status": "sent",
    "stats": {
        "sent": 1,
        "error_logs": 0,
        "total_recipients": null
    },
    "error_logs": [
        "error proccessing recipient: 1, error SMTP To address may not be blank: []",
        "error proccessing recipient: 2, error SMTP To address may not be blank: []"
    ]
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
This endpoint allows you to obtain the progress and stats of a massive notification after the user sent it.

***HTTP Request***

`GET /v1/events/:event_uri/notifications/:id/stats`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | event_uri for the desired event
   id     | integer | The id for the desired notification

## Tags Notification

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/notifications/tags" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/notifications/tags', {
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
        "id": "tags for notifications event id",
        "type": "tags",
        "attributes": {
            "event_tags": {
                "default": [
                    "event-name",
                    "event-description",
                    "event-start_date",
                    "event-end_date",
                    "event-timezone",
                    "event-location"
                ],
                "fields": []
            },
            "attendee_type_tags": {
                "default": [
                    "attendee_type-name",
                    "attendee_type-description"
                ],
                "fields": []
            },
            "attendee_tags": {
                "default": [
                    "attendee-first_name",
                    "attendee-last_name",
                    "attendee-email",
                    "attendee-alternative_email",
                    "attendee-telephone",
                    "attendee-company",
                    "attendee-birthdate"
                ],
                "fields": [
                    "attendee-f653",
                    "attendee-f654",
                    "attendee-f655"
                ]
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
    "error": [
      "code: 128"
    ]
  }
}
```
This endpoint allows you to obtain the available tags for notification

***HTTP Request***

`GET /v1/events/:event_uri/notifications/stats`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | event_uri for the desired event



## Notification Languages
## Index Notification Languages

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
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
                "body": "<div class= 'body'> Hello${name}</div>",
                "design": "{\"padding\":\"0px\"}"
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
***HTTP Request***

`GET v1/events/:event_uri/notifications/:notification_id/notification_languages`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer  | The id for the desired notification

## Get Notification Languages

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_language/:id" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_language/:id', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
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
                "body": "<div class= 'body'> Hello${name}</div>",
                "design": "{\"padding\":\"0px\"}"
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
***HTTP Request***

`GET v1/events/:event_uri/notifications/:notification_id/notification_language/:id`

***Path Parameters***

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
          "body": "<div class='body'> Hello ${name}</div>",
          "design": "{\"padding\":\"0px\"}"
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
    'Authorization': 'Bearer <your token>'
  },
  body: {
    "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>",
          "design": "{\"padding\":\"0px\"}"
        }
  }
  }
})
```
> Example of a successful (200) response:
***HTTP Request***

`POST /v1/events/:event_uri/notifications/:notification_id/notification_languages`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification

***Body Parameters***
Parameter | Type | Description
--------- | ---- | -----------
locale | string | Supported locales ['es', 'en', 'fr', 'it', 'de', 'ru']
subject | string | Subject for notification.
body    | string | Body for notification.
design | json | json object with notifications data

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
          "body": "<div class='body'> Hello ${name}</div>",
          "design": "{\"padding\":\"0px\"}"
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
    'Authorization': 'Bearer <your token>'
  },
  body: {
    "data": {
    "type": "notifications",
    "attributes": {
          "locale": "en",
          "subject": "Email created",
          "body": "<div class='body'> Hello ${name}</div>",
          "design": "{\"padding\":\"0px\"}"
        }
  }
  }
})
```
> Example of a successful (200) response:
***HTTP Request***

`PUT /v1/events/:event_uri/notifications/:notification_id/notification_languages/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification
id | integer  | The id for the desired notification language

***Body Parameters***
Parameter | Type | Description
--------- | ---- | -----------
locale | string | Supported locales ['es', 'en', 'fr', 'it', 'de', 'ru']
subject | string | Subject for notification.
body    | string | Body for notification.
design  | json | json object for notifications data


## Delete Notification Language

> To destroy notification language, use this code:

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages/:id" \
  -H 'Content-Type: application/json'
```

```javascript
fetch("https://core.eventtia.com/v1/events/:event_uri/notifications/:notification_id/notification_languages/:id", {
  method: 'DELETE',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': 'Bearer <your token>'
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
        "body": "<div class= 'body'> Hello${name}</div>",
        "design": "{\"padding\":\"0px\"}"
    }
    }
  }
}
```

***HTTP Request***

`DELETE v1/events/:event_uri/notifications/:notification_id/notification_languages/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
notification_id | integer | The id for the desired notification
id | integer | Id for the desired notification language
