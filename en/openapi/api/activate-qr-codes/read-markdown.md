# Read Dynamic QR Code Content (Markdown)

This API allows users to read information from dynamic QR codes and display it in Markdown or JSON format.

> The API can only read dynamic QR codes under your own account.

## Request Example

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'qrcodeUrl': 'https://qr61.cn/xxx/yyy',
}

headers = {
    'Authorization': 'Bearer <Your_APIKey>' // Replace with your API Key, e.g., 'Bearer abc123456'
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
  /qrcode/read_markdown:
    post:
      summary: Read Dynamic QR Code Content
      description: Retrieve information from a dynamic QR code and return it in the specified format
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                qrcodeUrl:
                  type: string
                  description: Dynamic QR code URL
                  example: https://qr61.cn/xxx/yyy
              required:
                - qrcodeUrl
                - format
      responses:
        '200':
          description: Successful response
          content:
            text/plain:
              schema:
                type: string
                example: |
                  ---
                  Title: Hello World
                  QR Code URL: https://qr61.cn/xxx/yyy

                  ---

                  # Hello World

                  Foo Bar
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

### Markdown

**header**

```text
Content-Type: text/plain
```

**body**

```text
---

Title: Hello World
QR Code URL: https://qr61.cn/xxx/yyy

---

# Hello World

Foo Bar
```