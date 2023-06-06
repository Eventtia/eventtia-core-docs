## Event

### Total Attendees

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/total-attendees" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/total-attendees', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "attendees": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of active attendees for an event

***HTTP Request***

`GET /v1/stats/events/:event_uri/total-attendees`

 ***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event



### Total Orders

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/total-orders" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/total-orders', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "orders": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of orders for an event

***HTTP Request***

`GET /v1/stats/events/:event_uri/total-orders`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event



### Amount Collected

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/amount-collected" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/amount-collected', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "amount": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total amount collected for an event.

***HTTP Request***

`GET /v1/stats/events/:event_uri/amount-collected`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### Tickets Purchased

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/tickets-purchased" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/tickets-purchased', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "tickets": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total tickets purchased for an event.

***HTTP Request***

`GET /v1/stats/events/:event_uri/tickets-purchased`

***Path Parameters***
Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### Tickets by Attendee Type

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/tickets-by-attendee-type" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/tickets-by-attendee-type', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "54": 62
  },
  {
    "34": 13
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total tickets by attendee type for an event.

***HTTP Request***

`GET /v1/stats/events/:event_uri/tickets-by-attendee-type`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### Total Confirmed

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/total-confirmed" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/total-confirmed', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "attendees_confirmed": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of active attendees for an event

***HTTP Request***

`GET /v1/stats/events/:event_uri/total-confirmed`

 ***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event

### Total Checked

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/total-checked" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/total-checked', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "attendees_checked": 62
  }
]
```

>Example of Event Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of active attendees for an event

***HTTP Request***

`GET /v1/stats/events/:event_uri/total-confirmed`

 ***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event


### Timeline for Checked Attendees

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/events/<event_uri>/timeline-checked" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/events/<event_uri>/timeline-checked', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
     "2023-06-06": {
            "00": 0,
            "01": 0,
            "02": 0,
            "03": 0,
            "04": 0,
            "05": 0,
            "06": 0,
            "07": 0,
            "08": 0,
            "09": 0,
            "10": 0,
            "11": 0,
            "12": 0,
            "13": 0,
            "14": 0,
            "15": 1,
            "16": 1,
            "17": 0,
            "18": 0,
            "19": 0,
            "20": 0,
            "21": 0,
            "22": 0,
            "23": 0
        }
  }
]
```

>Example of Bad Request (400) response:

```http
HTTP/1.1 400 Not Found
{
  "message": {
    "error": "code: 359"
  }
}
```

This endpoint returns timeline for checked attendees, requires a valid date.

***HTTP Request***

`GET /v1/stats/events/:event_uri/timeline-checked`

 ***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
event_uri | string | The event_uri for the desired event

 ***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
timeline_date | string | date for the timeline  desired , example: "2023-06-06"

