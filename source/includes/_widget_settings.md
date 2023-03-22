# Widget Settings

## List Widget Settings

```shell
# Get your token for further authorization
curl -X GET "https://core.eventtia.com/v1/events/<event_uri>/widget_settings/" \
  -H 'Content-Type: application/json'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/widget_settings/', {
  method: 'GET',
  headers: {
    'Authorization': 'Bearer <your token>',
  }
})
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event.

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
 "data": {
        "id": "1",
        "type": "widget_settings",
        "attributes": {
            "access_button": {
                "en": "buy ticket"
            },
            "main_color": "#333333",
            "secondary_color": "#EEEEEE",
            "header_text_color": "#DDDDDD",
            "css": "body: {passing-left: 10px}",
            "logo": "url_file",
            "header_image": "url_file"
        },
        "relationships": {
            "event": {
                "data": {
                    "id": "54",
                    "type": "events"
                }
            }
        }
    }
}
```

This endpoint list widget settings belongs to event and return it

***HTTP Request***

`GET /v1/events/:event_uri/widget_settings/`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event.

## Update Widget Settings

```shell
# Get your token for further authorization
curl "https://core.eventtia.com/v1/events/<event_uri>/widget_settings/<id>" \
  -H 'Content-Type: application/json'\
   -X PUT -d '{
    "data": {
      "type": "widget_settings",
      "attributes": {
          "access_button": {
              "en": "cr7"
          },
          "main_color": "#333333",
          "secondary_color": "#EEEEEE",
          "header_text_color": "#DDDDDD",
          "css": "body: {passing-left: 10px}",
          "logo": logo file,
          "header_image": header background image file
      },
    }
}'
```

```javascript
fetch('https://core.eventtia.com/v1/events/<event_uri>/widget_settings/<id>', {
  method: 'PUT',
  headers: {
    'Authorization': 'Bearer <your token>',
  },
  body: {
    data: {
      type: "widget_settings",
      attributes: {
          access_button: {
              en: "cr7"
          },
          main_color: "#333333",
          secondary_color: "#EEEEEE",
          header_text_color: "#DDDDDD",
          css: "body: {passing-left: 10px}",
          logo: logo file,
          header_image: header background image file
      },
    }
  }
}
)
```

> Make sure you replace &lt;your token&gt; with the JWT you get when you authenticate. 

> Make sure you replace &lt;event uri&gt; with the event uri for the event to update. 

> Make sure you replace &lt;id&gt; with the id for the widget setting to update. 

> Example of a successful (200) response:

```http
HTTP/1.1 200 OK
{
    "data": {
        "id": "1",
        "type": "widget_settings",
        "attributes": {
            "access_button": {
                "en": "buy ticket"
            },
            "main_color": "#333333",
            "secondary_color": "#EEEEEE",
            "header_text_color": "#DDDDDD",
            "css": "body: {passing-left: 10px}",
            "logo": "url_file",
            "header_image": "url_file"
        },
        "relationships": {
            "event": {
                "data": {
                    "id": "54",
                    "type": "events"
                }
            }
        }
    }
}
```

>Example of Unprocessable Entity (422) response: 

```http
HTTP/1.1 422 Unprocessable Entity
{
  "message": {
    "error": [
      "code: 128"
    ]
  }
}
```

This endpoint update an widget setting and return it

***HTTP Request***

`PUT /v1/events/:event_uri/workshops/:id`

***Path Parameters***

Parameter |  Type   | Description
--------- | ------- | -----------
event_uri | string  | The event_uri for the desired event
   id     | integer | The id for the desired widget setting

***Body Parameters***

Parameter  |  Type  | Description
---------  | -------| -----------
access_button  | json | Keys belongs to available languages for event and its value, Example: {es: "comprar boleto", en: "buy ticket"}
main_color |  string  | main color for widget on Hexadecimal code
secondary_color |  string  | secondary color for widget on Hexadecimal code
header_text_color  | string | header_text_color for widget on Hexadecimal code
css  | string | css code for widget customization
logo | file | event logo file for widget
header_image   |  file  | header background image file for widget
