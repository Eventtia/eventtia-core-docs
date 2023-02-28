# Stats

## Account

### Total Resources

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/accounts/total-resources" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/accounts/total-resources', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
    {
        "feature": "included_users",
        "available": 500,
        "used": 1
    },
    {
        "feature": "included_registrations",
        "available": 3000,
        "used": 3025
    }
]
```

>Example of Account Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of resources for an account

***HTTP Request***

`GET /v1/stats/accounts/total-resources`



### Total Events

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/accounts/total-events" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/accounts/total-events', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
[
  {
    "events": 62
  }
]
```

>Example of Account Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of events for an account

***HTTP Request***

`GET /v1/stats/accounts/total-events`

