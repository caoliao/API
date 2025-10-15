# 记录凭证核销

通过此API，你可以对记录核销凭证进行核销操作，支持两种核销方式：切换到指定状态或切换到下一个状态。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/certificate/verification'

data = {
    "certificateCode": "https://qr46.cn/oEuE2E/vJ9AgZUD",
    "actionType": "set_certificate_status",
    "toCertificateStatus": "已核销",
    "fromCertificateStatus": "待核销",
    "recordTplId": 0,
    "recordCodeId": 0
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.request("POST", url, headers=headers, data=data)
print(response.text)
```

```bash [cURL]
curl -X POST "https://open.cli.im/api/v1/certificate/verification" \
  -H "Authorization: Bearer <你的APIKey>" \
  -H "Content-Type: application/json" \
  -d '{
    "certificateCode": "https://qr46.cn/oEuE2E/vJ9AgZUD",
    "actionType": "set_certificate_status",
    "toCertificateStatus": "已核销",
    "fromCertificateStatus": "待核销"
  }'
```

:::

## 响应示例

### 成功响应

```json
{
    "data": {
        "ownerRecordNumber": "L1271755",
        "recordId": 2498984,
        "orgId": 94910252,
        "recordAddTime": "2025-08-06 13:39:59",
        "certificateStatus": "已核销"
    },
    "code": 0,
    "message": "ok"
}
```

### 失败响应

```json
{
    "data": null,
    "code": 1021,
    "message": "无效二维码"
}
```

## 请求详情

`certificateCode` string *必填*

核销码内容，通常是核销码的URL地址，eg：https://qr46.cn/oEuE2E/vJ9AgZUD

---

`actionType` string *必填*

核销动作类型，支持两种值：
- `set_certificate_status`: 切换到指定状态
- `set_next_certificate_status`: 切换到下一个状态

---

`toCertificateStatus` string *条件必填*

切换到凭证状态，当 `actionType` 为 `set_certificate_status` 时必填，eg：已核销

---

`fromCertificateStatus` string *条件必填*

当前凭证状态，当 `actionType` 为 `set_certificate_status` 时必填，eg：待核销

---

`recordTplId` integer *可选*

核销指定表单的凭证，如果不传递则没有限制，eg：123

---

`recordCodeId` integer *可选*

核销指定码的凭证，如果不传递则没有限制，eg：456

## 响应详情

`code` integer

响应的业务状态码，0表示成功，非0表示失败

---

`message` string

响应的消息，通常用作错误的消息展示

---

`data` object

响应的内容，成功时包含以下字段：

- `ownerRecordNumber` string: 记录编号，eg：L1271755
- `recordId` integer: 记录ID，eg：2498984
- `orgId` integer: 企业ID，eg：94910252
- `recordAddTime` string: 记录添加时间，eg：2025-08-06 13:39:59
- `certificateStatus` string: 凭证状态，eg：已核销

## 错误码

| 状态码code | 状态信息message | 说明 |
| ---------- | --------------- | ---- |
| 0 | 请求成功 | 核销成功 |
| 403 | 鉴权失败！未上送鉴权参数Authorization | 鉴权失败，请走鉴权流程 |
| 400 | 请求的数据格式不符 | 请求参数上送有误 |
| 500 | 未知异常 | 未知异常，请联系开发 |
| 1021 | 记录凭证核销出错 | 核销操作失败，具体错误信息在message中 |
| 1022 | 凭证核销参数错误 | 参数验证失败，如必填参数缺失 |
