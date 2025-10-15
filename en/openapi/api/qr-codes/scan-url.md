# QR Code Scanning (via URL)

This API allows users to upload or provide images containing QR codes. The API will decode the QR code in the image and extract the encoded information.

## Request Example

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/scan_url'

data = {
    'url': 'https://gstatic.clewm.net/caoliao-resource/250221/80bc7c_be831017.png',
}

headers = {
    'Authorization': 'Bearer <YourAPIKey>' // Replace with your API Key, e.g. 'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```

```yaml [OpenAPI V3 Schema]
openapi: 3.1.0
info:
  title: QR Code Scanning
  version: 1.0.0
  description: Decode content from QR codes

servers:
  - url: https://open.cli.im/api/v1

paths:
  /qrcode/scan_url:
    post:
      summary: Scan QR Code
      description: Scan a QR code from the given URL and return its content.
      operationId: scanQRCode
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                url:
                  type: string
                  format: uri
                  description: URL of the QR code image to be scanned
              required:
                - url
      responses:
        '200':
          description: Successful response containing QR code content
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: Status code (0 indicates success)
                    example: 0
                  message:
                    type: string
                    description: Response message
                    example: ok
                  data:
                    type: object
                    properties:
                      content:
                        type: string
                        description: Extracted content from the QR code
                        example: "https://cli.im"
                      provider:
                        type: string
                        description: QR code URL provider
                        example: "caoliao"
                        enum:
                          - Alipay
                          - WechatPay
                          - WechatOfficialAccountPost
                          - JD
                          - Caoliao
                          - Other
      security:
        - bearerAuth: [ ]

components:
  securitySchemes:
    bearerAuth:
      type: http
      scheme: bearer

```

:::

## Response Example

::: code-group

```json
{
  "code": 0,
  "message": "ok",
  "data": {
    "content": "https://cli.im",
    "provider": "caoliao"
  }
}
```

:::

## "Scan QR Code" Request

### JSON Body

`url` string Required

Image URL (must be publicly accessible)

--- 

## "Scan QR Code" Response

### JSON Body

`code` integer

Business status code (0 indicates success, non-zero indicates failure)

---

`message` string

Response message (typically used for error display)

---

`data` object

Response data

---

`data.content` string

Data extracted from the QR code

---

`data.provider` string

QR code URL provider (indicates the service that generated the QR code)

| Value                      | Description  |
|---------------------------|-------------|
| Alipay                   | Alipay       |
| WechatPay                | WeChat Pay   |
| WechatOfficialAccountPost | WeChat Official Account article |
| JD                       | JD.com       |
| Caoliao                  | CaoLiao dynamic QR code |
| Other                    | Other providers |

> Avoid using "Other" for business logic as enum values may expand with system updates.