# Users

## List Users

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/users/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/users/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
"data": [
    {
      "id": 1,
      "type": "users",
      "attributes": {
          "first_name": "first Name",
          "last_name": "last Name",
          "email": "user@eventtia.com",
          "phone": "777777777",
          "active": true,
          "account_name": "account"
      },
      "relationships": {
          "account": {
              "data": {
                  "id": "1",
                  "type": "users"
              }
          },
          "role": {
              "data": {
                  "id": "1",
                  "type": "roles"
              }
            }
        }
    }
  ]
}

```

This endpoint return a list of users

***HTTP Request***

`GET /v1/users/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
page | json | A page object as described <a href="#pagination">here</a>
email | string | Filters results by the user's email.

## Get User

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/users/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/users/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the user to get. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
    "id": "1",
    "type": "users",
    "attributes": {
        "first_name": "first Name",
        "last_name": "last Name",
        "email": "email@eventtia.com",
        "phone": "777777777",
        "active": true,
        "account_name": "eventtia"
    },
    "relationships": {
        "account": {
            "data": {
                "id": "1",
                "type": "users"
            }
        },
        "role": {
            "data": {
                "id": "1",
                "type": "roles"
            }
        }
    }
  }
}
```

>Example of User Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": "Couldn't find User"
}
```

This endpoint return an user

***HTTP Request***

`GET /v1/users/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | id for the desired user
## Create User

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/users/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
     "data": {
      "type": "users",
      "attributes":{
          "first_name": "first Name",
          "last_name": "last Name",
          "phone": 788965455,
          "password": "SecurePassword",
          "email": "user@eventtia.com",
          "is_admin": "false"
        },
          "relationships": {
          "role": {
              "data": {
                  "id": "1",
                  "type": "roles"
          }
        },
            "role_category": {
                "data": [{"type": "role_categories", "id": "1"}]
            }
      }
	}
}'
```

```javascript
fetch('https://core.eventtia.com/v1/users/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    {
    data: {
    type: "users",
    attributes:{
        first_name: "first Name",
        last_name: "last Name",
        phone: 788965455,
        password: "SecurePassword",
        email: "user@eventtia.com",
        is_admin: "false"
      },
        relationships: {
        role: {
            data: {
                id: "1",
                type: "roles"
          }
        }
      },
            role_category: {
                data: [{
                        id: "1",
                        type: "role_categories"
                        }]
            }
	}}
}
}
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "data": {
        "id": "1",
        "type": "users",
        "attributes": {
            "first_name": "first Name",
            "last_name": "last Name",
            "email": "email@eventtia.com",
            "phone": "777777777",
            "active": false,
            "account_name": "eventtia"
        },
        "relationships": {
            "account": {
                "data": {
                    "id": "1",
                    "type": "users"
                }
            }
        },
            "role": {
              "data": {
                  "id": "1",
                  "type": "roles"
                }
            }
      }
}
```

>Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
```

This endpoint create an user and return it

***HTTP Request***

`POST /v1/users/`

### Available settings

Parameter | Type | Description
--------- | ---- | -----------
first_name | string | The User's first name.
last_name | string | The User's last name.
email | string | The User's corporate email.
phone | string | The User's phone.
password | string | The User's password.
is_admin | bolean | Specifies whether the user you are creating is an administrator or not.

## Update User

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/users/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
     "data": {
      "type": "users",
      "attributes":{
          "first_name": "first Name",
          "last_name": "last Name",
          "phone": 788965455,
          "password": "SecurePassword",
          "email": "user@eventtia.com",
          "is_admin": "false"
        },
          "relationships": {
          "role": {
              "data": {
                  "id": "1",
                  "type": "roles"
          }
        },
            "role_category": {
                "data": [{
                  "id": "1",
                  "type": "role_categories"
                  }]
            }
      }
	}
}'
```

```javascript
fetch('https://core.eventtia.com/v1/users/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
    type: "users",
    attributes:{
        first_name: "first Name",
        last_name: "last Name",
        phone: 788965455,
        password: "SecurePassword",
        password_confirmation: "SecurePassword",
        email: "user@eventtia.com",
        is_admin: "false"
      },
        relationships: {
        role: {
          data: {
              id: "2",
              type: "roles"
          }
        },
            role_category: {
                data: [{
                  id: "1",
                  type: "role_categories"
                  }]
            }
      }
	}
}
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the user to update. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "data": {
        "id": "1",
        "type": "users",
        "attributes": {
            "first_name": "first Name",
            "last_name": "last Name",
            "email": "email@eventtia.com",
            "phone": "777777777",
            "active": true,
            "account_name": "eventtia"
        },
        "relationships": {
            "account": {
                "data": {
                    "id": "1",
                    "type": "users"
                }
            },
            "role": {
                "data": {
                    "id": "2",
                    "type": "roles"
                }
            }
        }
    }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
```

This endpoint update an user and return it

***HTTP Request***

`PUT /v1/users/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired user

### Available settings

Parameter | Type | Description
--------- | ---- | -----------
name | string | The User's name.
email | string | The User's corporate email.
phone | string | The User's phone.
password | string | The User's password.
is_admin | bolean | Specifies whether the user you are creating is an administrator or not.

## Destroy User

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/users/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/users/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the user to destroy. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "data": {
        "id": "1",
        "type": "users",
        "attributes": {
            "first_name": "first Name",
            "last_name": "last Name",
            "email": "email@eventtia.com",
            "phone": "777777777",
            "active": true,
            "account_name": "eventtia"
        },
        "relationships": {
            "account": {
                "data": {
                    "id": "1",
                    "type": "users"
                }
            }
        }
    }
}
```

This endpoint destroy a user and return it

***HTTP Request***

`DELETE /v1/users/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired user


## Current-User

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/users/retrieve" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/users/retrieve', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
"data": 
    {
      "id": 1,
      "type": "users",
      "attributes": {
          "first_name": "first Name",
          "last_name": "last Name",
          "email": "user@eventtia.com",
          "phone": "777777777",
          "active": true,
          "account_name": "account"
      },
      "relationships": {
          "account": {
              "data": {
                  "id": "1",
                  "type": "users"
              }
          },
          "role": {
              "data": {
                  "id": "1",
                  "type": "roles"
              }
            }
        }
    }
  
}

```

This endpoint return a current user

***HTTP Request***

`GET /v1/users/retrieve`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
page | json | A page object as described <a href="#pagination">here</a>

## Get User Categories

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/users/<id>/categories" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/users/<id>/categories', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate.

> Make sure you replace &lt;id&gt; for the user to get. 

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

>Example of User Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": "Couldn't find User"
}
```

This endpoint return user's categories

***HTTP Request***

`GET /v1/users/:id/categories`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | id for the desired user


