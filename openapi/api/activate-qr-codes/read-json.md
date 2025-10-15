# 读取活码内容(Markdown)

通过此API，用户可以读取活码中的信息，以JSON的形式展示。

> 通过该API读取的必须是自己账户下的活码

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_json'

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
  /qrcode/read_json:
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
      responses:
        '200':
          description: 成功响应
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: 状态码, 0表示成功, 其他表示失败
                    example: 0
                  message:
                    type: string
                    description: 状态消息, 成功时为"ok", 失败时为错误消息
                    example: ok
                  data:
                    type: object
                    properties:
                      meta:
                        type: object
                        properties:
                          url:
                            type: string
                            description: 活码URL
                          title:
                            type: string
                            description: 活码名称
                          orgCode:
                            type: string
                            description: 企业ID
                          coding:
                            type: string
                            description: 活码编号(URL Path的最后一部分)
                      contents:
                        type: array
                        items:
                          type: object
                          properties:
                            type:
                              type: string
                              enum: [text, image, audio, video, contact, file]
                              description: 模块类型
                            text:
                              type: object
                              properties:
                                value:
                                  type: string
                                  description: 文本内容
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
                                        description: 图片URL
                            audio:
                              type: object
                              properties:
                                url:
                                  type: string
                                  description: 音频URL
                                title:
                                  type: string
                                  description: 音频名称
                            video:
                              type: object
                              properties:
                                url:
                                  type: string
                                  description: 视频URL
                                title:
                                  type: string
                                  description: 视频标题
                                coverUrl:
                                  type: string
                                  description: 视频封面
                            contact:
                              type: object
                              properties:
                                wechatName:
                                  type: string
                                  description: 微信名称
                                phone:
                                  type: string
                                  description: 电话
                                email:
                                  type: string
                                  description: 邮箱
                                address:
                                  type: string
                                  description: 地址
                                workTime:
                                  type: string
                                  description: 工作时间
                            file:
                              type: object
                              properties:
                                title:
                                  type: string
                                  description: 文件名
                                url:
                                  type: string
                                  description: 文件URL
                      states:
                        type: array
                        description: 活码的状态列表
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: 状态编号
                            title:
                              type: string
                              description: 状态标题
                            value:
                              type: string
                              description: 状态值
                            valueID:
                              type: string
                              description: 状态值ID
                      forms:
                        type: array
                        description: 活码关联的表单列表
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: 表单编号
                            title:
                              type: string
                              description: 表单标题
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
        "title": "状态",
        "value": "开启",
        "valueID": "10111"
      }
    ],
    "forms": [
      {
        "serialNumber": "F1",
        "title": "表单1"
      }
    ]
  }
}
```

### JSON响应详情

`code` integer

状态码, 0表示成功, 其他表示失败。

---

`message` string

状态消息, 成功时为"ok", 失败时为错误消息。

---

`data` object

响应的数据

---

`data.meta` object

活码元数据

`data.meta.url` string

活码URL

`data.meta.title` string

活码名称

`data.meta.orgCode` string

企业ID

`data.meta.coding` string

活码编号(URL Path的最后一部分)

---

`data.contents` []ContentModule

活码的富文本内容是一个ContentModule数组, 活码内容有多个模块构成。例如文本、图片、音频、视频、联系方式等。

你可以通过 [二维码富文本模块ContentModule](./openapi/api/activate-qr-codes/qrcode-content-schema.md) 了解富文本模块的定义。

---

**活码状态**

`data.states` []object

活码的状态列表

`data.states[].serialNumber` string

状态编号

`data.states[].title` string

状态标题

`data.states[].value` string

状态值

`data.states[].valueID` string

状态值ID

---

**活码关联的表单**

`data.forms` []object

活码关联的表单列表

`data.forms[].serialNumber` string

表单编号

`data.forms[].title` string

表单标题

