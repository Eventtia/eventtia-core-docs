# Public Endpoints

## Get Event

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

### HTTP Request

`GET /v1/events/:event_uri`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### HTTP Request for optional include settings

`GET /v1/events/:event_uri/include=settings`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
include   | string | the value settings gives informations for each relationships (settings or attendees)
 
