# 二维码扫描(通过URL)

通过此API，用户可以上传或提供包含二维码的图像，API将解析图像中的二维码，提取其中编码的信息。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/scan_url'

data = {
    'url': 'https://gstatic.clewm.net/caoliao-resource/250221/80bc7c_be831017.png',
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
  title: 扫描二维码
  version: 1.0.0
  description: 解析二维码中的内容

servers:
  - url: https://open.cli.im/api/v1

paths:
  /qrcode/scan_url:
    post:
      summary: 扫描二维码
      description: 从给定的 URL 扫描二维码并返回二维码的内容。
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
                  description: 需要扫描的二维码图片的 URL
              required:
                - url
      responses:
        '200':
          description: 成功响应，包含二维码内容
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: 响应的状态代码, 0表示成功
                    example: 0
                  message:
                    type: string
                    description: 响应的消息
                    example: ok
                  data:
                    type: object
                    properties:
                      content:
                        type: string
                        description: 从二维码中提取的内容
                        example: "https://cli.im"
                      provider:
                        type: string
                        description: 二维码URL服务商
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

## 响应示例

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

## "扫描二维码"的请求

### JSON Body

`url` string 必选

图像URL, 请确保可以外网访问

--- 

## "扫描二维码"的响应

### JSON Body

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

接口响应的数据

---

`data.content` string

二维码中的数据

---

`data.provider` string

二维码URL提供商, 用于判断该二维码来自哪一个服务。

| 值                         | 说明         |
|---------------------------|------------|
| Alipay                   | 支付宝        |
| WechatPay                | 微信支付       |
| WechatOfficialAccountPost | 微信公众号文章    |
| JD                       | 京东         |
| Caoliao                  | 草料活码       |
| Other                    | 其他         |

> 尽量避免使用"Other"用于业务判断, 因为枚举值可能随着系统升级而增加。
