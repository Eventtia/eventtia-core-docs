# Email Settings
## List Email Settings

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/email_settings/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/email_settings/', {
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
            "id": "1",
            "type": "email_settings",
            "attributes": {
                "sender_name": "pedro",
                "sender_email": "sender_test@eventtia.com"
            },
            "relationships": {
                "role_category": {
                    "data": {
                        "id": "1",
                        "type": "role_categories"
                    }
                }
            }
        }
    ],
}
```

This endpoint returns a list of email_settings that your account have configured

***HTTP Request***

`GET /v1/email_settings/`

***Path Parameters***


Parameter |  Type   | Description
--------- | ------- | -----------
page | json | A page object as described <a href="#pagination">here</a>

## Get Email Settings

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/email_settings/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/email_settings/<id>', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the email_setting to get. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
        "id": "1",
        "type": "email_settings",
        "attributes": {
            "sender_name": "pedrito",
            "sender_email": "pierre@eventtia.com"
        },
        "relationships": {
            "role_category": {
                "data": {
                    "id": "1",
                    "type": "role_categories"
                }
            }
        }
    }
}
```
>Example of Email Setting Not Found (404) response:

```http
HTTP/1.1 404 Not Found
{
  "message": {
    "error": "code: 128"
  }
}
```

This endpoint returns a email_setting given an id

***HTTP Request***

`GET /v1/email_settings/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | Id for the desired email_setting

## Create Email Setting

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/email_settings/" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
   "data": {
        "type": "email_settings",
        "attributes": {
            "sender_name": "Juan Bolivar",
            "sender_email": "sender_test@email.com"
        },
        "relationships": {
            "role_category": {
                "data": {
                    "id": "1",
                    "type": "role_categories"
                }
            }
        }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/email_settings/', {
  method: 'POST',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    {
    data: {
        type: "email_settings",
        attributes: {
            sender_name: "Juan Bolivar",
            sender_email: "sender_test@email.com"
        },
        relationships: {
            role_category: {
                data: {
                    id: "1",
                    type: "role_categories"
                }
            }
        }
    }
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
        "type": "email_settings",
        "attributes": {
            "sender_name": "pedrito",
            "sender_email": "pierre@eventtia.com"
        },
        "relationships": {
            "role_category": {
                "data": {
                    "id": "1",
                    "type": "role_categories"
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

This endpoint creates a email_settings and return it

***HTTP Request***

`POST /v1/email_settings/`

***Body Parameters***

Parameter | Type | Description
--------- | ---- | -----------
name | string | Email setting's name.


## Destroy Email Setting

```shell
# Get your token for further authorization
curl -X DELETE "https://core.eventtia.com/v1/email_settings/<id>" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/email_settings/<id>', {
  method: 'DELETE',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;id&gt; for the email_setting to destroy. 

>Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
  "data": {
        "id": "1",
        "type": "email_settings",
        "attributes": {
            "sender_name": "pedro",
            "sender_email": "senter_test@eventtia.com"
        },
        "relationships": {
            "role_category": {
                "data": {
                    "id": "1",
                    "type": "role_categories"
                }
            }
        }
    }
}
```

This endpoint destroys a email setting and return it

***HTTP Request***

`DELETE /v1/email_settings/:id`

***Path Parameters***

Parameter | Type | Description
--------- | ---- | -----------
id | integer | The id for the desired email_setting
