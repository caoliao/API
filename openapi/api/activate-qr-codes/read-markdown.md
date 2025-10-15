# 读取活码内容(Markdown)

通过此API，用户可以读取活码中的信息，以Markdown或JSON的形式展示。

> 通过该API读取的必须是自己账户下的活码

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'qrcodeUrl': 'https://qr61.cn/xxx/yyy',
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```

```yaml [OpenAPI V3 Schema]
openapi: 3.1.0
info:
  title: 活码内容读取
  description: API 读取活吗内容并以 Markdown 或 JSON 格式返回。
  version: 1.0.0
servers:
  - url: https://open.cli.im/api/v1

paths:
  /qrcode/read_markdown:
    post:
      summary: 读取活码内容
      description: 从活码读取信息并以指定的格式返回
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                qrcodeUrl:
                  type: string
                  description: 活码URL
                  example: https://qr61.cn/xxx/yyy
              required:
                - qrcodeUrl
                - format
      responses:
        '200':
          description: 成功响应
          content:
            text/plain:
              schema:
                type: string
                example: |
                  ---
                  标题：Hello World
                  二维码URL: https://qr61.cn/xxx/yyy

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

## 响应示例

### Markdown

**header**

```text
Content-Type: text/plain
```

**body**

```text
---

标题：Hello World
二维码URL: https://qr61.cn/xxx/yyy

---

# Hello World

Foo Bar
```
