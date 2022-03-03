### Download Attendee Export

This endpoint downloads an attendee export and returns it progress

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

#### HTTP Request
`GET /v1/export_processes/:id/download`

#### Path Parameters

Parameter |  Type  | Description
--------- |  ----  | -----------
id | integer | The id for the desired attendee export




