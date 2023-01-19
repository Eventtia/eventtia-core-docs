# Role Categories
## List Role Categories

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/role_categories/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/role_categories/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```
> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": [
    {
      "id": "4",
      "type": "role_categories",
      "attributes": {
        "id": 4,
        "name": "grupo 1"
      }
    }
  ]
}

```
This endpoint allows you to list the role categories you have associated with your account.

### HTTP Request

`GET /v1/role_categories/`

### Path Parameters

Parameter |  Type   | Description
--------- | ------- | -----------
page | json | A page object as described <a href="#pagination">here</a>

## Get Role Category

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/role_categories/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/role_categories/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the role category to get. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "4",
    "type": "role_categories",
    "attributes": {
      "id": 4,
      "name": "grupo 1"
    },
          "relationships": {
          "user": {
              "data": {
                  "id": "1",
                  "type": "users"
          }
        }}
  }
}
```
>Example of role_categories Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns a role category given an id

### HTTP Request

`GET /v1/role_categories/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | Id for the desired role category

## Create Role Category

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/account_subscriptions/<id>" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
    "data": {
        "type": "role_categories",
        "attributes": {
            "name": "grupo 5"
        },
          "relationships": {
          "user": {
              "data": {
                  "id": "1",
                  "type": "users"
          }
        }}
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/role_categories/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
  {
    data: {
        type: "role_categories",
        attributes: {
            name: "grupo 5"
        },
          relationships: {
          user: {
              data: {
                  id: "1",
                  type: "users"
          }
        }}
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
    "id": "6",
    "type": "role_categories",
    "attributes": {
        "id": 6,
        "name": "grupo 5"
    }
  }
}
```
>Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
```

This endpoint creates a role category and returns it

### HTTP Request

`POST /v1/role_categories/`

### Body Parameters

Parameter | Type | Description
--------- | ---- | -----------
name | string | Role category name.

## Update Role Category

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/role_categories/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
        "type": "role_categories",
        "attributes": {
            "name": "grupo 5"
        },
          "relationships": {
          "user": {
              "data": {
                  "id": "1",
                  "type": "users"
          }
        }}
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/role_categories/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    "data": {
        "type": "roles",
        "attributes": {
            "name": "grupo 10"
        },
          "relationships": {
          "user": {
              "data": {
                  "id": "1",
                  "type": "users"
          }
        }}
    }
  }
})

```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the role_category to update. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "5",
    "type": "role_categories",
    "attributes": {
        "id": 5,
        "name": "grupo 10"
    }
  }
}
```
>Example Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
      "error": "code: 128"
  }
}
```

This endpoint updates a role category and return it

### HTTP Request

`PUT /v1/role_categories/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | Id for the desired role category

### Body Parameters

Parameter | Type | Description
--------- | ---- | -----------
name | string | Role category name.

## Destroy Role Category

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/role_categories/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/role_categories/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the role category to destroy. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "5",
    "type": "role_categories",
    "attributes": {
        "id": 5,
        "name": "grupo 10"
      }
  }
}
```

This endpoint destroys a role category and returns it

### HTTP Request

`DELETE /v1/role_categories/:id`

### Path Parameters

Parameter | Type | Description
--------- | ---- | -----------
id | integer | Id for the desired role category