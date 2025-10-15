# 鉴权

该文档将说明如何在API请求中完成鉴权。

## 创建 API Key

在使用草料二维码API之前，您需要创建和获取API Key。

**创建方式如下**

1. [访问数据API页面](https://user.cli.im/opendata?withNav=1)，来创建您的API Key
2. 点击 `添加配置` 找到 `OpenAPI` 并点击 `开通`
3. 输入API Key的`名称`，点击`保存`
4. 在列表中找到您新创的配置，点击 `复制` 图标来得到您的Key

> 通常API Key的名称用于区分不同的应用

## 接口鉴权方式

OpenAPI鉴权当前仅支持Bearer Token方式

### Bearer Token

在请求头(Header)中添加`Authorization`字段，值为`Bearer <API KEY>`

例如创建的API Key是Abc123456，此时携带的Header为

```
Authorization: Bearer Abc123456
```

### 代码示例

:::code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'url': 'https://qr61.cn/o2eikt/qWX2f5B',
    'format: 'markdown',
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)
```


```java [Java + HttpClient]
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpHeaders;
import java.net.http.HttpRequest.BodyPublishers;
import java.net.http.HttpResponse.BodyHandlers;
import java.util.HashMap;
import java.util.Map;
import com.fasterxml.jackson.databind.ObjectMapper;

public class QRCodeReader {
    public static void main(String[] args) {
        try {
            String url = "https://open.cli.im/api/v1/qrcode/read_markdown";

            Map<String, String> data = new HashMap<>();
            data.put("url", "https://qr61.cn/xxxxx/yyyyy");

            ObjectMapper objectMapper = new ObjectMapper();
            String json = objectMapper.writeValueAsString(data);

            HttpClient client = HttpClient.newHttpClient();

            HttpRequest request = HttpRequest.newBuilder()
                    .uri(URI.create(url))
                    .header("Authorization", "Bearer <你的APIKey>") // 请替换为你的API Key, 例如'Bearer abc123456'
                    .header("Content-Type", "application/json")
                    .POST(BodyPublishers.ofString(json))
                    .build();

            HttpResponse<String> response = client.send(request, BodyHandlers.ofString());

            System.out.println(response.body());
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

```php [PHP]
<?php

$apiKey = '<你的APIKey>';
$url = 'https://qr61.cn/xxxxx/yyyyy';
$apiUrl = 'https://open.cli.im/api/v1/qrcode/read_markdown';

$data = [
    'url' => $url,
    'format' => 'markdown'
];

$ch = curl_init($apiUrl);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    'Authorization: Bearer ' . $apiKey,
    'Content-Type: application/json'
]);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

$response = curl_exec($ch);
curl_close($ch);

echo $response;
```



```bash [curl]
curl -X POST 'https://open.cli.im/api/v1/qrcode/read_markdown' \
-H 'Authorization: Bearer <你的APIKey>' \
-H 'Content-Type: application/json' \
-d '{"url": "https://qr61.cn/xxxxx/yyyyy"}'
```

:::