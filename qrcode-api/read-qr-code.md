# 二维码解码

## GET方式

通过GET请求携带图像URL来解码/读取二维码内容

发起一个GET请求来解码

```text
https://api.2dcode.biz/v1/read-qr-code?file_url=<URLEncode后的图像文件URL>
```

你可以直接访问以下 URL 直接在浏览器中进行测试：

```text
https://api.2dcode.biz/v1/read-qr-code?file_url=https%3A%2F%2Fgstatic.clewm.net%2Fcaoliao-resource%2F250408%2F80bc7c_bd33d499.png
```

### 示例代码

:::code-group

```python
import requests
from urllib.parse import quote

r = requests.get("https://api.2dcode.biz/v1/read-qr-code?file_url=" + quote("https://gstatic.clewm.net/caoliao-resource/250408/80bc7c_bd33d499.png"))
print(r.json()["data"]["contents"][0])
```

```php
$result = json_decode(file_get_contents("https://api.2dcode.biz/v1/read-qr-code?file_url=".urlencode("https://gstatic.clewm.net/caoliao-resource/250408/80bc7c_bd33d499.png")), true);
echo $result["data"]["contents"][0];
```

```javascript
fetch("https://api.2dcode.biz/v1/read-qr-code?file_url="+encodeURIComponent("https://gstatic.clewm.net/caoliao-resource/250408/80bc7c_bd33d499.png"))
  .then(r=>r.json())
  .then(d=>console.log(d.data.contents[0]));
```

:::


## POST方式

可以通过表单请求的方式携带图像URL来解码/读取二维码内容

### 示例代码


:::code-group

```python
import requests

# 准备请求参数
url = 'https://api.2dcode.biz/v1/read-qr-code'
files = {
    'file': ('qrcode.png', open('qrcode.png', 'rb'))  # 上传本地二维码图片
}

# 发送POST请求
response = requests.post(url, files=files)

# 解析响应
result = response.json()
contents = result['data']['contents']
  print('识别到的二维码内容:', contents)
```

:::

## 响应说明

### 响应示例

```json
{
  "code": 0,
  "message": "ok",
  "data": {
    "contents": [
      "Example"
    ]
  }
}
```

### 响应参数

| 参数名      | 类型    | 说明                                                           |
|-------------|---------|--------------------------------------------------------------|
| code        | number  | 状态码, 0表示成功, 其他表示失败                               |
| message     | string  | 返回信息                                                       |
| data        | object  | 返回数据对象                                                   |
| ├─ contents  | array   | 二维码内容数组, 返回识别到的所有二维码内容, 图中没有二维码时返回空数组 |

