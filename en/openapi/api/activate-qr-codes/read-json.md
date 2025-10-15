# Read Dynamic QR Code Content (Markdown)

This API allows users to read information from dynamic QR codes and display it in JSON format.

> The API can only read dynamic QR codes under your own account.

## Request Example

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_json'

data = {
    'qrcodeUrl': 'https://qr61.cn/xxx/yyy',
}

headers = {
    'Authorization': 'Bearer <YourAPIKey>' // Replace with your API Key, e.g., 'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```

```yaml [OpenAPI V3 Schema]
openapi: 3.1.0
info:
  title: Dynamic QR Code Content Reading
  description: API for reading dynamic QR code content and returning it in Markdown or JSON format.
  version: 1.0.0
servers:
  - url: https://open.cli.im/api/v1

paths:
  /qrcode/read_json:
    post:
      summary: Read Dynamic QR Code Content
      description: Read information from a dynamic QR code and return it in the specified format.
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                qrcodeUrl:
                  type: string
                  description: Dynamic QR Code URL
                  example: https://qr61.cn/xxx/yyy
              required:
                - qrcodeUrl
      responses:
        '200':
          description: Successful response
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: Status code, 0 for success, others for failure.
                    example: 0
                  message:
                    type: string
                    description: Status message, "ok" for success, error message for failure.
                    example: ok
                  data:
                    type: object
                    properties:
                      meta:
                        type: object
                        properties:
                          url:
                            type: string
                            description: Dynamic QR Code URL
                          title:
                            type: string
                            description: Dynamic QR Code name
                          orgCode:
                            type: string
                            description: Enterprise ID
                          coding:
                            type: string
                            description: Dynamic QR Code ID (last part of the URL path)
                      contents:
                        type: array
                        items:
                          type: object
                          properties:
                            type:
                              type: string
                              enum: [text, image, audio, video, contact, file]
                              description: Module type
                            text:
                              type: object
                              properties:
                                value:
                                  type: string
                                  description: Text content
                            image:
                              type: object
                              properties:
                                items:
                                  type: array
                                  items:
                                    type: object
                                    properties:
                                      url:
                                        type: string
                                        description: Image URL
                            audio:
                              type: object
                              properties:
                                url:
                                  type: string
                                  description: Audio URL
                                title:
                                  type: string
                                  description: Audio name
                            video:
                              type: object
                              properties:
                                url:
                                  type: string
                                  description: Video URL
                                title:
                                  type: string
                                  description: Video title
                                coverUrl:
                                  type: string
                                  description: Video cover URL
                            contact:
                              type: object
                              properties:
                                wechatName:
                                  type: string
                                  description: WeChat name
                                phone:
                                  type: string
                                  description: Phone number
                                email:
                                  type: string
                                  description: Email address
                                address:
                                  type: string
                                  description: Physical address
                                workTime:
                                  type: string
                                  description: Working hours
                            file:
                              type: object
                              properties:
                                title:
                                  type: string
                                  description: File name
                                url:
                                  type: string
                                  description: File URL
                      states:
                        type: array
                        description: List of statuses for the dynamic QR code
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: Status ID
                            title:
                              type: string
                              description: Status title
                            value:
                              type: string
                              description: Status value
                            valueID:
                              type: string
                              description: Status value ID
                      forms:
                        type: array
                        description: List of forms associated with the dynamic QR code
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: Form ID
                            title:
                              type: string
                              description: Form title
        '400':
          description: Bad Request
        '401':
          description: Unauthorized
      security:
        - bearerAuth: []

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer
```

:::

## Response Example

**header**

```text
Content-Type: application/json
```

**body**

```json
{
  "code": 0,
  "message": "ok",
  "data": {
    "meta": {
      "url": "https://qr61.cn/xxx/yyy",
      "title": "Hello World",
      "orgCode": "oZ4v6123",
      "coding": "yyy"
    },
    "contents": [
      {
        "type": "text",
        "text": "Hello World"
      },
      {
        "type": "image",
        "image": {
          "items": [
            {
              "url": "https://qr61.cn/xxx/yyy"
            }
          ]
        }
      }
    ],
    "states": [
      {
        "serialNumber": "S1",
        "title": "Status",
        "value": "Active",
        "valueID": "10111"
      }
    ],
    "forms": [
      {
        "serialNumber": "F1",
        "title": "Form 1"
      }
    ]
  }
}
```

### JSON Response Details

`code` integer

Status code, 0 for success, others for failure.

---

`message` string

Status message, "ok" for success, error message for failure.

---

`data` object

Response data.

---

`data.meta` object

Dynamic QR code metadata.

`data.meta.url` string

Dynamic QR code URL.

`data.meta.title` string

Dynamic QR code name.

`data.meta.orgCode` string

Enterprise ID.

`data.meta.coding` string

Dynamic QR code ID (last part of the URL path).

---

`data.contents` []ContentModule

The rich text content of the dynamic QR code is an array of ContentModules, composed of multiple modules such as text, images, audio, video, contact information, etc.

Refer to [QR Code Rich Text Module ContentModule](./en/openapi/api/activate-qr-codes/qrcode-content-schema.md) for details on rich text module definitions.

---

**Dynamic QR Code Status**

`data.states` []object

List of statuses for the dynamic QR code.

`data.states[].serialNumber` string

Status ID.

`data.states[].title` string

Status title.

`data.states[].value` string

Status value.

`data.states[].valueID` string

Status value ID.

---

**Forms Associated with Dynamic QR Code**

`data.forms` []object

List of forms associated with the dynamic QR code.

`data.forms[].serialNumber` string

Form ID.

`data.forms[].title` string

Form title.