# Events

## List Events

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
      id: "21",
      "type": "events",
      "attributes": {
        "name": "Event name",
        "description": "description of an event",
        "start_date": "2020-04-13 15:54:37 -0500",
        "end_date": "2020-04-15 15:54:57 -0500",
        "active_modules": "[8]",
        "fields_data": "{}",
        "attendance_mode": "online",
        "is_template": false,
        "event_uri": "event_uri",
        "timezone": "America/Bogota",
        "location": {
          "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
          "address": "Event address",
          "country": "Colombia.",
          "city": "Medellín",
        },
        "virtual_timezone": "America/Bogota",
        "total_attendees": 0,
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
  ]
}
```

This endpoint return a list of events

***HTTP Request***

`GET /v1/events/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
page | json | A page object as described <a href="#pagination">here</a>
name | string | Filters results by the event's name.
created_by_id | integer | Filters results by the event's user.
template| integer | Filters results by The id of a specific template to get all the events cloned from it
templates | boolean | Send true if you want to get only template events.
start_date_upper_bound | datetime | Filters results by event's start_date before this bound date ej 2020-07-16 23:00.
start_date_lower_bound | datetime | Filters results by event's start_date after this bound date ej 2020-07-16 23:00.
end_date_upper_bound | datetime | Filters results by event's end_date before this bound date ej 2020-07-16 23:00.
end_date_lower_bound | datetime | Filters results by event's end_date after this bound date ej 2020-07-16 23:00.
active_status | boolean | Send true if you want to get only active events.

## Get Event

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update. 

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
      "active_modules": "[0, 1]",
      "fields_data": "{}",
      "attendance_mode": "online",
      "is_template": false,
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "total_attendees": 0,
      "cloned_from_id": "2",
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

***HTTP Request***

`GET /v1/events/:event_uri`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


***HTTP Request*** for optional include settings

`GET /v1/events/:event_uri/include=settings`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
include   | string | the value settings gives informations for each relationships (settings or attendees)
 

## Create Event

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
   "data": {
    "id": "21",
    "type": "events",
    "attributes": {
      "name": "Event name",
      "description": "description of an event",
      "start_date": "2020-04-13 15:54:37 -0500",
      "end_date": "2020-04-15 15:54:57 -0500",
      "active_modules": "[0, 1]",
      "fields_data": "{}",
      "attendance_mode": "online",
      "is_template": false,
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "settings": {
        "time_format": "hours_24",
        "date_format": "mm/dd/yyyy",
        "available_languages": {
            "available": ["en", "es"],
            "default": "en"
        }        },
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "banner": {
        "filename": "file_name",
        "thumb": "url_image",
        "small":  "url_image",
        "medium": "url_image",
        "large": "url_image",
      },
      "logo: {
        "filename": "file_name",
        "thumb": "url_image",
        "small": "url_image",
        "medium": "url_image",
        "large": "url_image",
      }
    },
      "relationships": {
          "role_category": {
              "data": {
                  "id": "1",
                  "type": "role_categories"
          }
        }
      }
  }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  data: {
    id: "21",
    type: "events",
    attributes: {
      name: "Event name",
      description: "description of an event",
      start_date: "2020-04-13 15:54:37 -0500",
      end_date: "2020-04-15 15:54:57 -0500",
      active_modules: "[0, 1]",
      fields_data: "{}",
      attendance_mode: "online",
      is_template: false,
      event_uri: "event_uri",
      timezone: "America/Bogota",
      settings: {
        "time_format": "hours_24",
        "date_format": "mm/dd/yyyy",
        "available_languages": {
            "available": ["en", "es"],
            "default": "en"
        }        },
      location: {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      virtual_timezone: "America/Bogota",
      banner: {
        filename: "file_name",
        thumb: "url_image",
        small:  "url_image",
        medium: "url_image",
        large: "url_image",
      },
      logo: {
        filename: "file_name",
        thumb: "url_image",
        small: "url_image",
        medium: "url_image",
        large: "url_image",
      }
    }
  },
      relationships: {
          role_category: {
              data: {
                  id: "1",
                  type: "role_categories"
          }
        }
      }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

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
      "active_modules": "[0, 1]",
      "fields_data": "{}",
      "attendance_mode": "online",
      "is_template": false,
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "total_attendees": 0,
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

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "start_date": [
      "is beyond the end date."
    ],
    "name": [
      "is already in use"
    ]
  }
}
```

This endpoint create an event and return it

***HTTP Request***

`POST /v1/events/`

### Available settings

Parameter | Type | Description
--------- | ---- | -----------
name | string | name of event. 
description | string | description of event.
start_date | date | starting date for event, must be before end date of event.
is_template | boolean | this event is a template.
cloned_from_id | integer | event id from this event was cloned
attendance_mode | string | event attendance mode ['offline', 'mixed', 'online']. 
event_uri| string | event uri must be an unique name.
logo | file | logo for this event.
banner_image | file | banner image for this event.
currency | string | your event currency for payments and invoices ['COP', 'USD', 'EUR', 'ARS', 'BRL', 'CLP', 'MXN', 'PEN', 'GBP', 'JOD', 'UYU', 'PYG', 'AED', 'CAD', 'VND', 'PHP', 'AUD', 'BOB', 'TND', 'SGD', 'CHF', 'CFA', 'ZAR', 'INR']
date_format | string | event date format ['dd/mm/yyyy', 'mm/dd/yyyy']. 
time_format | string | event time format ['hours_24', 'am_pm'].
available_languages | json | includes available key ( array with availables languages for event ) and default key ( a string with a single required language, included in available languages array)


## Update Event

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
   "data": {
    "id": "21",
    "type": "events",
    "attributes": {
      "name": "Event name",
      "description": "description of an event",
      "start_date": "2020-04-13 15:54:37 -0500",
      "end_date": "2020-04-15 15:54:57 -0500",
      "active_modules": "[0, 1]",
      "fields_data": "{}",
      "attendance_mode": "online",
      "is_template": false,
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "settings": {
        "time_format": "hours_24",
        "date_format": "mm/dd/yyyy",
        "available_languages": {
            "available": ["en", "es"],
            "default": "en"
        }        },
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "banner": {
        "filename": "file_name",
        "thumb": "url_image",
        "small":  "url_image",
        "medium": "url_image",
        "large": "url_image",
      },
      "logo: {
        "filename": "file_name",
        "thumb": "url_image",
        "small": "url_image",
        "medium": "url_image",
        "large": "url_image",
      }
    },
      "relationships": {
          "role_category": {
              "data": {
                  "id": "1",
                  "type": "role_categories"
          }
        }
      }
  }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  data: {
    type: "events",
    attributes: {
      name: "Event name",
      description: "description of an event",
      start_date: "2020-04-13 15:54:37 -0500",
      end_date: "2020-04-15 15:54:57 -0500",
      active_modules: "[0, 1]",
      fields_data: "{}",
      attendance_mode: "online",
      is_template: false,
      event_uri: "event_uri",
      timezone: "America/Bogota",
      settings: {
        "time_format": "hours_24",
        "date_format": "mm/dd/yyyy",
        "available_languages": {
            "available": ["en", "es"],
            "default": "en"}
             },
      location: {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      virtual_timezone: "America/Bogota",
      cloned_from_id: "12",
      banner: {
        filename: "file_name",
        thumb: "url_image",
        small:  "url_image",
        medium: "url_image",
        large: "url_image",
      },
      logo: {
        filename: "file_name",
        thumb: "url_image",
        small: "url_image",
        medium: "url_image",
        large: "url_image",
      }
    },
    relationships: {
      settings: {
        data: {
          id: "108",
          type: "settings"
        }
      }
    },
      relationships: {
          role_category: {
              data: {
                  id: "1",
                  type: "role_categories"
          }
        }
      }
  }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "type": "events",
    "attributes": {
      "name": "Event name",
      "description": "description of an event",
      "start_date": "2020-04-13 15:54:37 -0500",
      "end_date": "2020-04-15 15:54:57 -0500",
      "active_modules": "[0, 1]",
      "fields_data": "{}",
      "attendance_mode": "virtual",
      "is_template": "false",
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "total_attendees": 0,
      "cloned_from_id": "1",
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

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "start_date": [
      "is beyond the end date."
      ],
    "name": [
      "is already in use" 
    ]
  }
}
```

This endpoint update an event and return it

***HTTP Request***

`PUT /v1/events/:event_uri`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event

### Available settings

Parameter | Type | Description
--------- | ---- | -----------
name | string | name of event. 
description | string | description of event.
start_date | date | starting date for event, must be before end date of event.
is_template | boolean | this event is a template.
cloned_from_id | integer | event id from this event was cloned
attendance_mode | string | event type ['offline', 'mixed', 'online']. 
event_uri| string | event uri must be an unique name.
logo | file | logo for this event.
banner_image | file | banner image for this event.
currency | string | your event currency for payments and invoices ['COP', 'USD', 'EUR', 'ARS', 'BRL', 'CLP', 'MXN', 'PEN', 'GBP', 'JOD', 'UYU', 'PYG', 'AED', 'CAD', 'VND', 'PHP', 'AUD', 'BOB', 'TND', 'SGD', 'CHF', 'CFA', 'ZAR', 'INR']
date_format | string | event date format ['dd/mm/yyyy', 'mm/dd/yyyy']. 
time_format | string | event time format ['hours_24', 'am_pm'].
available_languages | json | includes available key ( array with availables languages for event ) and default key ( a string with a single required language, included in available languages array)

## Destroy Event

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/events/<event_uri>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy. 

>Example of a successful (200) response:

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
      "active_modules": "[8]",
      "fields_data": "{}",
      "attendance_mode": "virtual",
      "is_template": false,
      "event_uri": "event_uri",
      "timezone": "America/Bogota",
      "location": {
        "coordinates": { "lat": 6.2518400, "lng": -75.5635900 },
        "address": "Event address",
        "country": "Colombia.",
        "city": "Medellín",
      },
      "virtual_timezone": "America/Bogota",
      "total_attendees": 0,
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

This endpoint destroy a event and return it

***HTTP Request***

`DELETE /v1/events/:event_uri`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


## Settings

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/settings" \
  -H 'Content-Type: application/json'\
   -X PATCH -d '{
   "data": {
      "type": "event_settings",
      "attributes": {
        "payment_method": "credit card",
        "paypal_production_key": "12345ABCDE",
        "paypal_sandbox_key": "ABCDEHGIKN",
        "paypal_test_mode": false,
        "stripe_secret_api_key": "1A2G3R4FTT",
        "stripe_publishable_api_key": "LA778GHGD6",
        "pay_u_api_key": "99IIOYNTRE",
        "pay_u_merchant_id": "12",
        "pay_u_account_id": "13",
        "pay_u_api_login": "33445ABCDE",
        "pay_u_test_mode": false,
        "currency": 4,
        "tax_alias": "Recaudo",
        "tax_value": 19.0,
        "date_format": "dd/mm/yyyy",
        "time_format": "am_pm",
        "google_analytics_tracking_code": "A78Y55ABCD",
        "google_tag_manager_code": "11223ABCDE",
        "available_languages": {
                              "available": ["en", "es"],
                              "default": "en"}
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/settings', {
  method: 'PATCH',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
      type: "event_settings",
      attributes: {
        payment_method: "credit card",
        paypal_production_key: "12345ABCDE",
        paypal_sandbox_key: "ABCDEHGIKN",
        paypal_test_mode: false,
        stripe_secret_api_key: "1A2G3R4FTT",
        stripe_publishable_api_key: "LA778GHGD6",
        pay_u_api_key: "99IIOYNTRE",
        pay_u_merchant_id: "12",
        pay_u_account_id: "13",
        pay_u_api_login: "33445ABCDE",
        pay_u_test_mode: false,
        currency: 4,
        tax_alias: "Recaudo",
        tax_value: 19.0,
        date_format: "dd/mm/yyyy",
        time_format: "am_pm",
        google_analytics_tracking_code: "A78Y55ABCD",
        google_tag_manager_code: "11223ABCDE",
        available_languages: {
                              "available": ["en", "es"],
                              "default": "en"}
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "3",
    "type": "event_settings",
    "attributes": {
      "payment_method": "credit card",
      "paypal_production_key": "12345ABCDE",
      "paypal_sandbox_key": "12345ABCDE",
      "paypal_test_mode": false,
      "stripe_secret_api_key": "12345ABCDE",
      "stripe_publishable_api_key": "12345ABCDE",
      "pay_u_api_key": "12345ABCDE",
      "pay_u_merchant_id": "12",
      "pay_u_account_id": "13",
      "pay_u_api_login": "33445ABCDE",
      "pay_u_test_mode": false,
      "currency": 4,
      "tax_alias": "Recaudo",
      "tax_value": 19.0,
      "date_format": "dd/mm/yyyy",
      "time_format": "am_pm",
      "google_analytics_tracking_code": "33445ABCDE",
      "google_tag_manager_code": "11223ABCDE",
      "available_languages": {
                              "available": ["en", "es"],
                              "default": "en"},
    },
    "relationships": {
      "event": {
        "data": {
          "id": "2195",
          "type": "event"
        }
      }
    }
  }
}
```

> Example of a 500 response:

```http
HTTP/1.1 500
{
  "message": {
    "payment_method": [
      "must be one of these: stripe, payu, and paypal"
    ]
  }
}
```
This endpoint allows you modify your event settings

***HTTP Request***

`PATCH /v1/events/:event_uri/settings`


***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event

### Available settings

Parameter | Type | Description
--------- | ---- | -----------
payment_method | string | payment platform to collect money online ['stripe', 'payu', 'paypal']. 
paypal_production_key | string | paypal production key obtained from paypal dashboard.
paypal_sandbox_key | string | paypal sandbox key obtained from paypal dashboard
paypal_test_mode | boolean | when testing your payments won't be any charge to your cards
stripe_secret_api_key | string | stripe secret api key obtained from stripe dashboard
stripe_publishable_api_key | string | stripe secret publishable api key obtained from stripe dashboard
pay_u_api_key | string | pay u api key obtained from pay u dashboard
pay_u_merchant_id | string | pay u merchand id obtained from pay u dashboard
pay_u_account_id | string | pay u account id obtained from pay u dashboard
pay_u_api_login | string | pay u api login obtained from pay u dashboard
pay_u_test_mode | boolean | when testing your payments won't be any charge to your cards
currency | string | your event currency for payments and invoices ['COP', 'USD', 'EUR', 'ARS', 'BRL', 'CLP', 'MXN', 'PEN', 'GBP', 'JOD', 'UYU', 'PYG', 'AED', 'CAD', 'VND', 'PHP', 'AUD', 'BOB', 'TND', 'SGD', 'CHF', 'CFA', 'ZAR', 'INR']
tax_alias | string | how do you want to call your vat value
tax_value | integer/float | Your event tax value
available_languages | json | includes available key ( array with availables languages for event ) and default key ( a string with a single required language, included in available languages array)


