# Authentication

This document explains how to complete authentication in API requests.

## Creating an API Key

Before using the CaoLiao QR Code API, you need to create and obtain an API Key.

**Creation steps:**

1. [Visit the Data API page](https://user.cli.im/opendata?withNav=1) to create your API Key
2. Click `Add Configuration`, locate `OpenAPI`, and click `Enable`
3. Enter a `name` for your API Key and click `Save`
4. Find your newly created configuration in the list and click the `Copy` icon to obtain your Key

> Typically, the API Key name is used to distinguish between different applications

## Authentication Methods

OpenAPI currently only supports Bearer Token authentication.

### Bearer Token

Add an `Authorization` field to the request header with the value `Bearer <API KEY>`

For example, if your API Key is `Abc123456`, the header should be:

```
Authorization: Bearer Abc123456
```

### Code Examples

:::code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/qrcode/read_markdown'

data = {
    'url': 'https://qr61.cn/o2eikt/qWX2f5B',
    'format': 'markdown',
}

headers = {
    'Authorization': 'Bearer <YourAPIKey>'  # Replace with your API Key, e.g. 'Bearer abc123456'
}

response = requests.post(url, json=data, headers=headers)
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
                    .header("Authorization", "Bearer <YourAPIKey>")  // Replace with your API Key, e.g. 'Bearer abc123456'
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

$apiKey = '<YourAPIKey>';
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
-H 'Authorization: Bearer <YourAPIKey>' \
-H 'Content-Type: application/json' \
-d '{"url": "https://qr61.cn/xxxxx/yyyyy"}'
```

:::