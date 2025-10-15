# Quick Start

Learn how to get started with the CaoLiao QR Code API.

## Introduction

This article demonstrates how to quickly begin using the CaoLiao QR Code API with curl and common programming languages. For more detailed guidance, refer to the TODO Getting Started guide.

## Create an API Key

Before using the CaoLiao QR Code API, you need to create and obtain an API Key. You can [visit the Data API page](https://user.cli.im/opendata?withNav=1) to retrieve your API Key. For more detailed instructions, refer to [Authentication](./en/openapi/auth.md).

## Write Code to Call the API

Below are examples of calling the `Read Dynamic QR Code Content` API:

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'qrcodeUrl': 'https://qr61.cn/xxxxx/yyyyy'
}

headers = {
    'Authorization': 'Bearer <YourAPIKey>' // Replace with your API Key, e.g., 'Bearer abc123456'
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
                    .header("Authorization", "Bearer <YourAPIKey>") // Replace with your API Key, e.g., 'Bearer abc123456'
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
-H 'Authorization: Bearer <YourAPIKey>' \
-H 'Content-Type: application/json' \
-d '{"qrcodeUrl": "https://qr61.cn/xxxxx/yyyyy"}'
```

:::

For more details about this API, refer to [Read Dynamic QR Code Content (Markdown)](./en/openapi/api/activate-qr-codes/read-markdown.md) or [Read Dynamic QR Code Content (JSON)](./en/openapi/api/activate-qr-codes/read-json.md).