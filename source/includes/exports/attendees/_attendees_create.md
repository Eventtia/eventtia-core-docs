### Create Attendee Export

This endpoint create an attendee export and return it

```javascript
fetch('https://core.eventtia.com/v1/export_processes/', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  },
  body: {
    data: {
        type: 'export_processes',
        attributes: {
            entity_type: 'attendees',
            process_params: {
                locale: '<locale>'
            }
        }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;locale&gt; with a string containing the desired language for attendee export to create.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "11",
    "type": "export_processes",
    "attributes": {
      "created_by_id": 1,
      "error": null,
      "type": "AttendeeExportProcess",
      "status": null,
      "progress": null,
      "process_params": {
        "locale": "es"
      },
      "excel_file": null
    }
  }
}
```

> Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "locale": [
      "must be a string"
    ]
  }
}
```

#### HTTP Request

`POST /v1/export_processes/`

#### Body Parameters

Parameter  |  Type  | Description
---------  |  ----  | -----------
locale | string | language of the attendee export

