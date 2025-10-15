# 获取子码内容

通过此API，你可以获取指定子码的内容。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/getQrcodeMsg?qrcodeSerialNumber=M2-Z6'

data = {}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.request("GET", url, headers=headers, data=data)
print(response.text)
```

:::

## 响应示例

```json
{
    "data": {
        "qrcodeSerialNumber": "M16-Z36",
        "codeName": "openapi测试0303",
        "url": "https://qr46.cn/o6leQy/qM36jri",
        "fields": [
            {
                "fieldId": 163185,
                "type": "text",
                "title": "示例编号",
                "text": {
                    "value": "openapi测试0303"
                }
            }
        ],
        "states": [
            {
                "title": "设备状态",
                "value": "损坏"
            }
        ]
    },
    "code": 0,
    "message": "ok"
}
```

## 请求详情

`qrcodeSerialNumber` string *必填*

子码编号，eg：M16-Z36，可从子码列表页面获取。

## 响应详情

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

响应的内容

---

`data.qrcodeSerialNumber` string

子码编号

---

`data.codeName` string

子码名称

---

`data.url` string

子码URL

---

`data.fields` []QrcodeField

组件列表, 每一个是`QrcodeField`对象, 你可以通过 [模版子码组件(获取子码内容)](./openapi/api/template-qrcodes/template-qrcode-form.md) 了解组件字段的定义。

---

`data.states` []QrcodeState

状态列表, 每一个是`QrcodeState`对象

`data.states[].title` string

状态标题

`data.states[].value` string

状态值

