# 快速开始

了解如何开始使用草料二维码API。

## 介绍

本文将介绍如何使用curl和常用的开发语言快速开始使用草料二维码API。有关更详细的指南，请参阅 TODO 入门。

## 创建 API Key

在使用草料二维码API之前，您需要创建和获取API Key。 您可以 [访问数据API页面](https://user.cli.im/opendata?withNav=1)，获取您的API Key。有关更详细的指南，请参阅[鉴权](./openapi/auth.md)

## 编写代码调用

以下是调用`读取活码内容`的示例：

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'qrcodeUrl': 'https://qr61.cn/xxxxx/yyyyy'
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
            data.put("qrcodeUrl", "https://qr61.cn/xxxxx/yyyyy");

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

```bash [curl]
curl -X POST 'https://open.cli.im/api/v1/qrcode/read_markdown' \
-H 'Authorization: Bearer <你的APIKey>' \
-H 'Content-Type: application/json' \
-d '{"qrcodeUrl": "https://qr61.cn/xxxxx/yyyyy"}'
```

:::

关于该API的更多描述请参阅 [读取活码内容(Markdown)](./openapi/api/activate-qr-codes/read-markdown.md) 或 [读取活码内容(JSON)](./openapi/api/activate-qr-codes/read-json.md)

