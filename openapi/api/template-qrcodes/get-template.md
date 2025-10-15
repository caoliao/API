# 获取模版组件

通过此API，你可以获取指定模版的可变内容组件。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/getTemplateMeta?templateCode=M16'

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
        "templateName": "全组件模版测试",
        "fields": [
            {
                "fieldId": 163185,
                "type": "text",
                "title": "示例编号"
            }
        ]
    },
    "code": 0,
    "message": "ok"
}
```

## 请求详情

`templateCode` string *必填*

模版编号，eg：M16，可从批量活码模版页面获取。


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

`data.templateName` string

模版名称

---

`data.fields` []TemplateField

模版组件列表, 每一个是`TemplateField`对象, 你可以通过 [模版组件](./openapi/api/template-qrcodes/template-form.md) 了解组件字段的定义。

