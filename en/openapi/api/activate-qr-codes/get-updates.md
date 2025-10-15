# Get Dynamic Data

Through this API, you can retrieve the dynamic data list of a specified QR code. Dynamic data comes in different types, consistent with the `record types` in CaoLiao QR Code's `Data Management` feature.

You can visit [CaoLiao QR Code/Data Management](https://console.cliim.net/data-management) to view dynamic data types.

## Dynamic Data Type Reference Table

| Type | Type Constant | Attributes Used |  
|------|--------------|-----------------|
| Form Submission | 1 | recordSubmit |  
| Status Change | 2 | stageChange |  
| Document Review | 3 | fileRead |  
| Member Join | 4 | memberJoin |  
| Bottom Collaboration | 5 | comment |  
| QR Code Content Modification | 6 | qrcodeChange |  

## Request Example

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/get_updates'

data = {
    'type': 0,  // 0 indicates all types
    'qrcodeUrl': 'https://qr61.cn/xxxxx/yyyyy'
}

headers = {
    'Authorization': 'Bearer <YourAPIKey>' // Replace with your API Key, e.g., 'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```

:::

## Response Example

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
            "recorder": "Zhang San",
            "addTime": "2025-01-01 00:00:00",
            "text": "Comment content",
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

## Request Details

`type` integer *Required*

Dynamic data type. Refer to the [Dynamic Data Type Reference Table](#dynamic-data-type-reference-table).

If set to `0`, it retrieves all types.

---

`qrcodeUrl` string *Required*

QR code URL.

---

`pageToken` string *Optional*

Pagination token. Use the `pageToken` from the previous response to fetch the next page of data.

---

`startTime` string *Optional*

Start time, formatted as `2025-01-01 00:00:00`.

---

`endTime` string *Optional*

End time, formatted as `2025-01-01 00:00:00`.

---

`formSerialNumber` string *Optional*

Form serial number. When combined with `type=1` and `qrcodeUrl`, it functions similarly to fetching form data.

---

## Response Details

`code` integer

Business status code. `0` indicates success; non-zero indicates failure.

---

`message` string

Response message, typically used for error display.

---

`data` object

---

`data.total` integer

Total count of dynamic data entries.

---

`data.pageToken` string

Pagination token for the next page.

---

`data.list` []UpdateData

List of dynamic data entries, each being an `UpdateData` object.