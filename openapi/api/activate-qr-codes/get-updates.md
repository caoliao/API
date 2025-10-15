# 获取动态数据

通过此API，你可以获取指定二维码的动态数据列表。动态数据存在不同的类型，与草料二维码`数据管理`功能中的`记录类型`一致。

您可以访问[草料二维码/数据管理](https://console.cliim.net/data-management) 查看动态数据的类型。

## 动态数据类型对照表

| 类型 ｜ type常量 | 使用的属性 | 
|------ | ----- | ------ |
| 表单填写 | 1 | recordSubmit |
| 状态变更 | 2 | stageChange |
| 文件签阅 | 3 | fileRead |
| 成员加入 | 4 | memberJoin |
| 底部协作 | 5 | comment |
| 码内容修改 | 6 | qrcodeChange |

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/get_updates'

data = {
    'type': 0,  // 0表示全部类型
    'qrcodeUrl': 'https://qr61.cn/xxxxx/yyyyy'
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```

:::

## 响应示例

```json
{
  "code": 0,
  "message": "ok",
  "data": {
    "total": 100,
    "pageToken": "d29ybGQ=",
    "list": [
      {
        "type": "comment",
        "comment": {
            "qrcodeCoding": "qc10Dg",
            "recorder": "张三",
            "addTime": "2025-01-01 00:00:00",
            "text": "评论内容",
            "image": {
                "images": [
                    {
                        "url": "https://gstatic.clewm.net/caoliao-resource/250221/80bc7c_be831017.png"
                    }
                ]
            }
        }
      }
    ]
  }
}
```

## 请求详情

`type` integer *必填*

动态数据类型, 请参考[动态数据类型对照表](#动态数据类型对照表)

如果填`0`，则表示获取全部类型。

---

`qrcodeUrl` string *必填*

二维码URL

---

`pageToken` string **可选**

分页Token,可以使用上一次请求响应的pageToken来获取下一页的数据。

---

`startTime` string **可选**

开始时间, 格式如 `2025-01-01 00:00:00`

---

`endTime` string **可选**

结束时间, 格式如 `2025-01-01 00:00:00`

---

`formSerialNumber` string **可选**

表单编号, 当同时填写表单编号, type=1时, qrcodeUrl时作用和获取表单数据一致。

---

## 响应详情

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

---

`data.total` integer

动态数据的总数

---

`data.pageToken` string

分页Token, 下一页的pageToken

---

`data.list` []UpdateData

动态数据列表, 每一个是`UpdateData`对象

