# 批量新增或编辑成员

通过此API，你可以批量新增或编辑成员信息。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/member/addMember'

data = {
    "list": [
        {
            "phone": "13800138000",
            "name": "张三"
        },
        {
            "phone": "13800138001",
            "name": "李四"
        }
    ]
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.request("POST", url, headers=headers, data=data)
print(response.text)
```

```bash [cURL]
curl -X POST "https://open.cli.im/api/member/addMember" \
  -H "Authorization: Bearer <你的APIKey>" \
  -H "Content-Type: application/json" \
  -d '{
    "list": [
      {
        "phone": "13800138000",
        "name": "张三"
      },
      {
        "phone": "13800138001",
        "name": "李四"
      }
    ]
  }'
```

:::

## 响应示例

### 成功响应

```json
{
    "data": {
        "successCount": 2,
        "failedCount": 0,
        "totalCount": 2,
        "failedMessages": null
    },
    "code": 0,
    "message": "ok"
}
```

### 部分失败响应

```json
{
    "data": {
        "successCount": 1,
        "failedCount": 1,
        "totalCount": 2,
        "failedMessages": [
            "第2条数据：mobile或name不能为空"
        ]
    },
    "code": 0,
    "message": "ok"
}
```

## 请求详情

`list` array *必填*

成员列表，每个成员包含以下字段：

- `phone` string *必填*: 手机号，必须符合中国大陆手机号格式（1开头的11位数字），eg：13800138000
- `name` string *必填*: 姓名，不能为空，eg：张三

## 校验规则

1. **成员列表校验**：成员列表不能为空
2. **手机号校验**：
    - 不能为空
    - 必须符合中国大陆手机号格式：以1开头，第二位是3-9，总共11位数字
    - 正则表达式：`^1[3-9]\\d{9}$`
3. **姓名校验**：
    - 不能为空
    - 不能只包含空白字符

**注意**：所有校验都在Controller层通过注解自动完成，如果校验失败会返回400错误。

## 响应详情

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

响应的内容，包含以下字段：

- `successCount` integer: 成功数量
- `failedCount` integer: 失败数量
- `totalCount` integer: 总数量
- `failedMessages` array: 失败消息列表，仅在有失败时返回

## 错误码

| 状态码code | 状态信息message | 说明 |
| ---------- | --------------- | ---- |
| 0 | 请求成功 | 批量处理成功 |
| 403 | 鉴权失败！未上送鉴权参数Authorization | 鉴权失败，请走鉴权流程 |
| 400 | 请求的数据格式不符 | 请求参数上送有误 |
| 500 | 未知异常 | 未知异常，请联系开发 |
| 1023 | 批量操作成员出错 | 批量处理成员失败，具体错误信息在message中 |
