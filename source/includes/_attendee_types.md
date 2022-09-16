# Attendee Types

## List Attendee Types

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/', {
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
      "type": "attendee_types",
      "attributes": {
        "name": "Attendee type name",
        "description": "attendee_type_description",
        "price": "34.2",
        "limit": 25,
        "confirmation_required": false,
        "allow_public_registration": false,
        "valid_if_no_payments": true,
        "updated_by_id": 192,
        "archived": false
      },
      "relationships": {
        "current_price": {
          "data": {
              "id": "6",
              "type": "pricing_tiers"
          }
        }
      }
    }
  ]
}
```

This endpoint list attendee types belongs to event and return it

### HTTP Request

`GET /v1/events/event_uri/attendee_types/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
page | json | A page object as described <a href="#pagination">here</a>
available_seats | boolean | activate an optional attribute (seats availability)


## Get Attendee Type

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/<id>', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the attendee type to obtain. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62527",
    "type": "attendee_types",
    "attributes": {
      "name": "Attendee type name",
      "description": "Attendee type description",
      "price": "34.2",
      "limit": 25,
      "confirmation_required": false,
      "allow_public_registration": false,
      "valid_if_no_payments": true,
      "updated_by_id": 192,
      "archived": false
    },
    "relationships": {
      "form_fields": {
        "data": [
            {
                "id": "24",
                "type": "form_fields"
            },
            {
                "id": "25",
                "type": "form_fields"
            }
        ]
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
    "message": "Couldn't find AttendeeType"
  }
}
```

This endpoint get an attendee type and return it

### HTTP Request

`GET /v1/events/event_uri/attendee_types/id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee type

### HTTP Request for optional include fields

`GET /v1/events/:event_uri/attendee_types/:id?include=value`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
include   | string  | this value gives informations for each relationships

### Include Options

Value |  Type   | Description
----- | ------- | -----------
fields | string | include fields relationships
current_price | string | include current price

## Create Attendee Type

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/', {
  method: 'POST',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    id: 62527
    type: "attendee_type",
    attributes: {
      name: { es:"Attendee type name", en: "Attendee type name"},
      description: { es:"Attendee type description", en: "Attendee type description"},
      price: 34.2,
      limit: 25,
      confirmation_required: false,
      allow_public_registration: false,
      valid_if_no_payments: true,
      archived: false
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
    "type": "attendee_types",
    "attributes": {
      "name": {"es": "Attendee type name", "en": "Attendee type name"},
      "description": {"es": "Attendee type description", "en": "Attendee type description"},
      "price": "34.2",
      "limit": 25,
      "confirmation_required": false,
      "allow_public_registration": false,
      "valid_if_no_payments": true,
      "updated_by_id": 192,
      "archived": false
    },
    "relationships": {
      "current_price": {
        "data": {
            "id": "12",
            "type": "pricing_tiers"
          }
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
    "price": [
      "must be a decimal"
    ]
  }
}
```

This endpoint create an attendee type and return it

### HTTP Request

`POST /v1/events/:event_uri/attendee_types/`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | json  | keys belongs to available languages for attendee type's event and its value, Example: {es: "Invitado", en: "Guest"}
description| json  | keys belongs to available languages for attendee type's event and its value, Example: {es: "descripcion de invitado", en: "Guest's description"}
price      | decimal | price for attendee type
limit      | integer | attendees limit for this attendee type
confirmation_required | boolean | confirmation required for attendee type
allow_public_registration | boolean | allow public registration for this attendee type
valid_if_no_payments | boolean | valid attendee type if no payments

## Update Attendee Type

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
  data: {
    type: "attendee_type",
    attributes: {
      name: "Attendee type name",
      description: "Attendee type description",
      price: 34.2,
      limit: 25,
      confirmation_required: false,
      allow_public_registration: false,
      valid_if_no_payments: true,
			allow_printing_without_payment: false
    }
  }
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update. 

> Make sure you replace &lt;id&gt; with the id for the attendee type to update. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62527",
    "type": "attendee_types",
    "attributes": {
      "name": "Attendee type name",
      "description": "Attendee type description",
      "price": "34.2",
      "limit": 25,
      "confirmation_required": false,
      "allow_public_registration": false,
      "valid_if_no_payments": true,
      "updated_by_id": 192,
      "archived": false
    },
    "relationships": {
      "current_price": {
        "data": {
            "id": "12",
            "type": "pricing_tiers"
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
    "price": [
      "must be an integer"
    ]
  }
}
```

This endpoint update an attendee type and return it

### HTTP Request

`PUT /v1/events/:event_uri/attendee_types/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee type

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
name       | string  | name for attendee type
description| string  | description for attendee type
price      | decimal | price for attendee type
limit      | integer | attendees limit for this attendee type
confirmation_required | boolean | confirmation required for attendee type
allow_public_registration | boolean | allow public registration for this attendee type
valid_if_no_payments | boolean | valid attendee type if no payments

## Destroy Attendee Type
```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': '<your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to destroy. 

> Make sure you replace &lt;id&gt; with the id for the attendee type to update. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "62528",
    "type": "attendee_types",
    "attributes": {
      "name": "Attendee type name",
      "description": "Attendee type description",
      "price": "545.0",
      "limit": 500,
      "confirmation_required": true,
      "allow_public_registration": true,
      "valid_if_no_payments": true,
      "archived": true
    },
    "relationships": {
      "current_price": {
          "data": {
              "id": "6",
              "type": "pricing_tiers"
          }
      }
    }
  }
}
```

This endpoint destroy an attendee type and return it

### HTTP Request

`DELETE /v1/events/:event_uri/attendee_types/:id`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee type


## Available Seats

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/attendee_types/<id>/available-seats', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Make sure you replace &lt;id&gt; with the id for the attendee type to obtain. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "meta: {
    "available: 999,
    "occupied": 5
  }
}
```

>Example of Not Found (404) response: 

```http
HTTP/1.1 404 Not Found
{
  {
    "message": "Couldn't find AttendeeType"
  }
}
```

This endpoint get an attendee type and return his available seats

### HTTP Request

`GET /v1/events/event_uri/attendee_types/id/available_seats`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired attendee type


## Form Fields
### Index form fields
```javascript
fetch('https://core.eventtia.com/v1/events/:event_uri/attendee_types/:entity_id/fields', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Make sure you replace &lt;entity_id&gt; with the id for the entity. 

> Example of a successful (200) response:

```shell


```
```http
HTTP/1.1 200 OK
{
    "data": [
    {
      "id": "24",
      "type": "form_fields",
      "attributes": {
          "id": 24,
          "order": 1
      },
      "relationships": {
        "field": {
            "data": {
              "id": "52",
              "type": "fields"
              }
          },
          "entity": {
            "data": {
              "id": "6",
              "type": "attendee_types"
          }
       }
      }
    ]
}
```

> Example of a 404 response:

```http
HTTP/1.1 404 Not Found
{
    
  "message": "Couldn't find Event"
        
}
```
This endpoint list all the available fields associated with the given attendee type.
### HTTP Request

`GET v1/events/:event_uri/attendee_types/:entity_id/fields`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
entity_id | integer  | The id for the desired attendee type

## Add Form Field
This endpoint allows you to associate a new field to the given attendee type form.

> To relate a new field to an entity, use this code:

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/:event_uri/attendee_types/:entity_id/fields" \
  -H 'Content-Type: application/json' \
  -X POST -d '{
  "data": {
    "type": "form_fields",
    "attributes": {
      "order": 1,
      "entity_type": "AttendeeType"
    },
    "relationships":{
      "field": {
        "data": {"id": 52, "type": "field"}
      },
      "entity": {
        "data": {"id": 6, "type": "attendee_type"}
      }
    }
  }
}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/events/:event_uri/attendee_types/:entity_id/fields", {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
  body: {
    data: {
    type: "form_fields",
    attributes: {
      order: 0,
      entity_type: "AttendeeType"
    },
    relationships: {
      field: {
        data: {"id": 52, "type": "field"}
      },
      entity: {
        data: {"id": 6, "type": "attendee_type"}
      }
    }
  }
  }
  
})
```
> Example of a successful (200) response:
### HTTP Request

`POST /v1/events/:event_uri/attendee_types/:entity_id/fields`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
entity_id | integer | The id for the desired attendee type

### Body Parameters
Parameter | Type | Description
--------- | ---- | -----------
order | integer | Field order in the form.
entity_type | string | AttendeeType.

## Delete Form Field
### Destroy Form Fields

> To update destroy, use this code:


```javascript
fetch("https://core.eventtia.com/v1/events/:event_uri/attendee_types/:entity_id/fields/:id<id>", {
  method: 'DELETE',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
})
```
This endpoint allows you to unassociated a field to the given attendee type form.

### HTTP Request

`DELETE v1/events/:event_uri/attendee_types/:entity_id/fields/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
entity_id | integer | The id for the desired attendee type
id | integer | The id for the field
## Change Form Field Order
### Change Order Form Fields
>

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/:event_uri/:entity_type/:entity_id/fields/change-order<id>" \
  -H 'Content-Type: application/json' \
  -X PUT -d '{
    "ordered_ids": {"20":3,"44":2}
}'
```

```javascript
// Get your token for further authorization
fetch("https://core.eventtia.com/v1/events/:event_uri/attendee_type/:entity_id/fields/change-order/<id>", {
  method: 'PUT',
  headers: {
    'Content-Type': 'application/json',
    'Authorization': '<your token>'
  },
  {
    ordered_ids: '<{"20":3,"44":2}>'
  }
})
```

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "status": 200
}
```

> Example of a 422 response:

```http
HTTP/1.1 422 Unprocessable Entity
{
    
    "message": "ExceptionHandler::RecordInvalid"
        
}
```
This endpoint allows you to change the order in which the fields are displayed in the registration form.

### HTTP Request

`PUT /v1/events/:event_uri/attendee_types/:entity_id/fields/change-order`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event.
entity_id | string | The id for the desired attendee type

### Body Parameters
Parameter | Type | Description
--------- | ---- | -----------
ordered_ids | json | Send of key (field_id) and value (order), example {"31":10, "32":9}