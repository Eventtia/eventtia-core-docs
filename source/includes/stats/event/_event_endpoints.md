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
