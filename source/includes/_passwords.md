# Passwords

## Request Recovery Password

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/en/v1/passwords" \
  -H 'Content-Type: application/json'\
   -X POST -d '{
    "recaptcha_token": "",
    "data": {
      "type": "users",
      "attributes": {
        "email": '<your email>'
        "locale": '<locale>'
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/en/v1/passwords', {
  method: 'POST',
  body: {
    recaptcha_token: "",
    data: {
      type: "users",
      attributes: {
        email: '<your email>'
        locale: '<locale>'
      }
    }
  }
})
```

> Make sure you replace &lt;your email&gt; with your email.

> Make sure you replace &lt;locale&gt; with the desired language

> Example of a successfull (200) response:

```http
HTTP/1.1 200 OK
{
  "recover_token": "P7V3G9C4pry6VMXgHomr"
  "message": "300, <your email>"
}
```

This endpoint request the reset password token and return it

### HTTP Request

`POST en/v1/passwords`


### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
email  | string | your email
locale  | string | desired language e.g. "en", "es" or "fr"

## Update Password

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/en/v1/passwords" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
      "type": 'users',
      "attributes": {
        "reset_password_token": '<your token>',
        "password": '<your new password>',
        "password_confirmation": '<your new password>'
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/en/v1/passwords', {
  method: 'PUT',
  body: {
    data: {
      type: 'users',
      attributes: {
        reset_password_token: '<your token>',
        password: '<your new password>',
        password_confirmation: '<your new password>'
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the given reset password token.

> Make sure you replace &lt;your new password&gt; with your new password.

> Example of successful (200) response:

```http
HTTP/1.1 200 OK
{
    "message": 301
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "reset_password_token": [
      106
    ]
  }
}
```

This endpoint updates the password of the user

### HTTP Request

`PUT en/v1/passwords`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
reset_password_token | string | recover password token
password | string | your new password
confirmation_password | string | your new password

## Activate Password

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/en/v1/passwords/activate" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
      "type": 'users',
      "attributes": {
        "reset_password_token": '<your token>',
        "password": '<your new password>',
        "password_confirmation": '<your new password>'
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/en/v1/passwords/activate', {
  method: 'PUT',
  body: {
    data: {
      type: 'users',
      attributes: {
        reset_password_token: '<your token>',
        password: '<your new password>',
        password_confirmation: '<your new password>'
      }
    }
  }
})
```

> Make sure you replace &lt;your token&gt; with the given reset password token.

> Make sure you replace &lt;your new password&gt; with your new password.

> Example of successful (200) response:

```http
HTTP/1.1 200 OK
{
    "message": 301
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "reset_password_token": [
      106
    ]
  }
}
```

This endpoint updates the password of the user

### HTTP Request

`PUT en/v1/passwords/activate`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
reset_password_token | string | recover password token
password | string | your new password
confirmation_password | string | your new password


## Change Password

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/en/v1/passwords/change" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
      "type": 'users',
      "attributes": {
        "current_password": '<your token>',
        "new_password": '<your new password>',
        "new_password_confirmation": '<your new password>'
      }
    }
}'
```

```javascript
fetch('https://core.eventtia.com/en/v1/passwords/change', {
  method: 'PUT',
  body: {
    data: {
      type: 'users',
      attributes: {
        current_password: '<your token>',
        new_password: '<your new password>',
        new_password_confirmation: '<your new password>'
      }
    }
  }
})
```
> Make sure you replace &lt;your current password&gt; with your current password.

> Make sure you replace &lt;your new password&gt; with your new password.

> Example of successful (200) response:

```http
HTTP/1.1 200 OK
{
    "message": 301
}
```

> Example of Unprocessable Entity (422) response:

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "current_password": [
      106
    ]
  }
}
```

This endpoint changes the password of the user

### HTTP Request

`PUT en/v1/passwords/change`

### Body Parameters

Parameter  |  Type   | Description
---------  | ------- | -----------
current_password | string | current password
new_password | string | your new password
new_confirmation_password | string | your new password