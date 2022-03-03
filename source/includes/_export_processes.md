# Export Processes

## Create Export Process

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
            entity_type: '<entity type>',
            process_params: {
                locale: '<locale>'
            }
        }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;entity type&gt; with a string containing the name of the desired entity associated to export process to create.

> Make sure you replace &lt;locale&gt; with a string containing the desired language for the export process to create.

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
      "type": "EventExportProcess",
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

This endpoint create an export process and return it

### HTTP Request

`POST /v1/export_processes/`

### Body Parameters

Parameter  |  Type  | Description
---------  |  ----  | -----------
entity_type| string | name of the entity
local | string | language of the export process

## Download Export Process

```javascript
fetch('https://core.eventtia.com/v1/export_processes/<id>/download', {
  method: 'GET',
  headers: {
    'Authorization': '<your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "progress": 0
}
```

This endpoint downloads an export process and returns it progress

### HTTP Request
`GET /v1/export_processes/:id/download`

### Path Parameters

Parameter |  Type  | Description
--------- |  ----  | -----------
id | integer | The id for the desired export process
