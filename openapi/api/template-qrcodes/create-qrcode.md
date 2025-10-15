# 创建子码

通过此API，你可以创建指定模版下的子码。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/createSubCode'

data = {
    "templateCode": "M16",
    "data": [
        {
            "fieldId": 1,
            "type": "text",
            "text": {
                "value": "openapi测试0303"
            }
        }
    ]
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.request("POST", url, headers=headers, data=data)
print(response.text)
```

:::

## 响应示例

```json
{
    "data": {
        "qrcodeSerialNumber": "M16-Z41",
        "qrcodeUrl": "https://qr46.cn/o6leQy/qyBVzC3",
        "qrcodeTagUrl": "https://qrapi.cliim.net/newqr/create?data=https%3A%2F%2Fqr46.cn%2Fo6leQy%2FqF19FPq&level=H&transparent=&bgcolor=%23ffffff&forecolor=%23000000&blockpixel=12&marginblock=2&logourl=&size=220&kid=bizcliim&time=1754554955&key=9b2c21895b9eb726efe08371209b8388"
    },
    "code": 0,
    "message": "ok"
}
```

## 请求详情

`templateCode` string *必填*

模版编号，eg：M16，可从批量活码模版页面获取。

---

`data` []CreateQrcodeField

创建子码组件列表，每一个是`CreateQrcodeField`对象，你可以通过 [模版子码组件(创建子码)](./openapi/api/template-qrcodes/qrcode-create-field.md) 了解组件字段的定义。


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

`data.qrcodeUrl` string

子码url

---

`data.qrcodeUrl` string

子码标签url

