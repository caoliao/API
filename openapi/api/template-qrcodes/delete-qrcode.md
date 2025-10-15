# 删除子码

通过此API，你可以删除一个已有的子码。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/deleteSubCode'

data = {
    "qrcodeSerialNumbers":["M16-Z40","M16-Z41"]
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
    "data": "删除子码成功",
    "code": 0,
    "message": "ok"
}
```

## 请求详情

`qrcodeSerialNumbers` []string *必填*

子码编号列表，eg：M16-Z36，可从子码列表页面获取。


## 响应详情

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

响应的内容

