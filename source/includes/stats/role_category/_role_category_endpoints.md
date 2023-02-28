## Role Category

### Events by Category

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/role_categories/total-events" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/role_categories/total-events', {
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
        "1": 10
    },
    {
        "3": 13
    },
    {
        "4": 11
    }
]
```

>Example of role category Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of events by role category

***HTTP Request***

`GET /v1/stats/role_categories/total-events`



### Users by Category

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/stats/role_categories/total-users" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/stats/role_categories/total-users', {
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
        "1": 1
    },
    {
        "3": 3
    },
    {
        "4": 2
    }
]
```

>Example of role category Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns total number of users by role category

***HTTP Request***

`GET /v1/stats/role_categories/total-users`
