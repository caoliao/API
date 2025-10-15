# API Demo

Taking sub-code creation as an example, here are calling demos for various programming languages.

## CURL Command

```
curl --location 'app-openapi-web.dev.cli0.cn/api/v1/createSubCode' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer Xs8UuJ4Ap4ZH7T2fZPzuBwAgLZL9U0v9qFW6Tv5tt9M=' \
--data '{
    "templateUid": "30728",
    "data": [
        {
            "fieldId": "163185",
            "type": "text",
            "text": {
                "value": "openapi test 1211"
            }
        },
        {
            "fieldId": "163188",
            "type": "textarea",
            "multilineText": {
                "value":"openapi test 1211\nopenapi test 1211"
            }
        },
        {
            "fieldId": "163189",
            "type": "number",
            "number": {
                "value":"20241211"
            }
        },
        {
            "fieldId": "163190",
            "type": "date",
            "date": {
                "value":"2024-12-11"
            }
        },
        {
            "fieldId": "163191",
            "type": "radio",
            "radio": {
                "optionId":5074778
            }
        },
        {
            "fieldId": "163192",
            "type": "checkbox",
            "checkbox": {
                "optionCreateDataList":[
                    {
                        "optionId":1317744
                    },
                    {
                        "optionId":5074779,
                        "otherValue":"openapi test 1227"
                    }
                ]
            }
        },
        {
            "fieldId": "163194",
            "type": "image",
            "image": {
                "images":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png"
                }
                ]
            }
        },
        {
            "fieldId": "163195",
            "type": "file",
            "file": {
                "files":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png",
                "name":"WeCom_screenshot_fa4224c9-0cbf-4476-ad81-929f321db2dd.png"}
                ]
            }
        }
    ]
}'
```

## HTTP Request

```http
POST /api/v1/createSubCode HTTP/1.1
Host: app-openapi-web.dev.cli0.cn
Content-Type: application/json
Authorization: Bearer Xs8UuJ4Ap4ZH7T2fZPzuBwAgLZL9U0v9qFW6Tv5tt9M=
Content-Length: 1952

{
    "templateUid": "30728",
    "data": [
        {
            "fieldId": "163185",
            "type": "text",
            "text": {
                "value": "openapi test 1211"
            }
        },
        {
            "fieldId": "163188",
            "type": "textarea",
            "multilineText": {
                "value":"openapi test 1211\nopenapi test 1211"
            }
        },
        {
            "fieldId": "163189",
            "type": "number",
            "number": {
                "value":"20241211"
            }
        },
        {
            "fieldId": "163190",
            "type": "date",
            "date": {
                "value":"2024-12-11"
            }
        },
        {
            "fieldId": "163191",
            "type": "radio",
            "radio": {
                "optionId":5074778
            }
        },
        {
            "fieldId": "163192",
            "type": "checkbox",
            "checkbox": {
                "optionCreateDataList":[
                    {
                        "optionId":1317744
                    },
                    {
                        "optionId":5074779,
                        "otherValue":"openapi test 1227"
                    }
                ]
            }
        },
        {
            "fieldId": "163194",
            "type": "image",
            "image": {
                "images":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png"
                }
                ]
            }
        },
        {
            "fieldId": "163195",
            "type": "file",
            "file": {
                "files":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png",
                "name":"WeCom_screenshot_fa4224c9-0cbf-4476-ad81-929f321db2dd.png"}
                ]
            }
        }
    ]
}
```

## Java Implementation

```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
MediaType mediaType = MediaType.parse("application/json");

RequestBody body = RequestBody.create(mediaType, "{\n    \"templateUid\": \"30728\",\n    \"data\": [\n        {\n            \"fieldId\": \"163185\",\n            \"type\": \"text\",\n            \"text\": {\n                \"value\": \"openapi test 1211\"\n            }\n        },\n        {\n            \"fieldId\": \"163188\",\n            \"type\": \"textarea\",\n            \"multilineText\": {\n                \"value\":\"openapi test 1211\\nopenapi test 1211\"\n            }\n        },\n        {\n            \"fieldId\": \"163189\",\n            \"type\": \"number\",\n            \"number\": {\n                \"value\":\"20241211\"\n            }\n        },\n        {\n            \"fieldId\": \"163190\",\n            \"type\": \"date\",\n            \"date\": {\n                \"value\":\"2024-12-11\"\n            }\n        },\n        {\n            \"fieldId\": \"163191\",\n            \"type\": \"radio\",\n            \"radio\": {\n                \"optionId\":5074778\n            }\n        },\n        {\n            \"fieldId\": \"163192\",\n            \"type\": \"checkbox\",\n            \"checkbox\": {\n                \"optionCreateDataList\":[\n                    {\n                        \"optionId\":1317744\n                    },\n                    {\n                        \"optionId\":5074779,\n                        \"otherValue\":\"openapi test 1227\"\n                    }\n                ]\n            }\n        },\n        {\n            \"fieldId\": \"163194\",\n            \"type\": \"image\",\n            \"image\": {\n                \"images\":[\n                    {\n                \"url\":\"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png\"\n                }\n                ]\n            }\n        },\n        {\n            \"fieldId\": \"163195\",\n            \"type\": \"file\",\n            \"file\": {\n                \"files\":[\n                    {\n                \"url\":\"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png\",\n                \"name\":\"WeCom_screenshot_fa4224c9-0cbf-4476-ad81-929f321db2dd.png\"}\n                ]\n            }\n        }\n    ]\n}");

Request request = new Request.Builder()
  .url("app-openapi-web.dev.cli0.cn/api/v1/createSubCode")
  .method("POST", body)
  .addHeader("Content-Type", "application/json")
  .addHeader("Authorization", "Bearer Xs8UuJ4Ap4ZH7T2fZPzuBwAgLZL9U0v9qFW6Tv5tt9M=")
  .build();
Response response = client.newCall(request).execute();
```

## Go Implementation

```go
package main

import (
  "fmt"
  "strings"
  "net/http"
  "io"
)

func main() {

  url := "app-openapi-web.dev.cli0.cn/api/v1/createSubCode"
  method := "POST"

  payload := strings.NewReader(`{
    "templateUid": "30728",
    "data": [
        {
            "fieldId": "163185",
            "type": "text",
            "text": {
                "value": "openapi test 1211"
            }
        },
        {
            "fieldId": "163188",
            "type": "textarea",
            "multilineText": {
                "value":"openapi test 1211\nopenapi test 1211"
            }
        },
        {
            "fieldId": "163189",
            "type": "number",
            "number": {
                "value":"20241211"
            }
        },
        {
            "fieldId": "163190",
            "type": "date",
            "date": {
                "value":"2024-12-11"
            }
        },
        {
            "fieldId": "163191",
            "type": "radio",
            "radio": {
                "optionId":5074778
            }
        },
        {
            "fieldId": "163192",
            "type": "checkbox",
            "checkbox": {
                "optionCreateDataList":[
                    {
                        "optionId":1317744
                    },
                    {
                        "optionId":5074779,
                        "otherValue":"openapi test 1227"
                    }
                ]
            }
        },
        {
            "fieldId": "163194",
            "type": "image",
            "image": {
                "images":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png"
                }
                ]
            }
        },
        {
            "fieldId": "163195",
            "type": "file",
            "file": {
                "files":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png",
                "name":"WeCom_screenshot_fa4224c9-0cbf-4476-ad81-929f321db2dd.png"}
                ]
            }
        }
    ]
}`)

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
    return
  }
  req.Header.Add("Content-Type", "application/json")
  req.Header.Add("Authorization", "Bearer Xs8UuJ4Ap4ZH7T2fZPzuBwAgLZL9U0v9qFW6Tv5tt9M=")

  res, err := client.Do(req)
  if err != nil {
    fmt.Println(err)
    return
  }
  defer res.Body.Close()

  body, err := io.ReadAll(res.Body)
  if err != nil {
    fmt.Println(err)
    return
  }
  fmt.Println(string(body))
}
```

## PHP Implementation

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => 'app-openapi-web.dev.cli0.cn/api/v1/createSubCode',
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => '',
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => 'POST',
  CURLOPT_POSTFIELDS =>'{
    "templateUid": "30728",
    "data": [
        {
            "fieldId": "163185",
            "type": "text",
            "text": {
                "value": "openapi test 1211"
            }
        },
        {
            "fieldId": "163188",
            "type": "textarea",
            "multilineText": {
                "value":"openapi test 1211\\nopenapi test 1211"
            }
        },
        {
            "fieldId": "163189",
            "type": "number",
            "number": {
                "value":"20241211"
            }
        },
        {
            "fieldId": "163190",
            "type": "date",
            "date": {
                "value":"2024-12-11"
            }
        },
        {
            "fieldId": "163191",
            "type": "radio",
            "radio": {
                "optionId":5074778
            }
        },
        {
            "fieldId": "163192",
            "type": "checkbox",
            "checkbox": {
                "optionCreateDataList":[
                    {
                        "optionId":1317744
                    },
                    {
                        "optionId":5074779,
                        "otherValue":"openapi test 1227"
                    }
                ]
            }
        },
        {
            "fieldId": "163194",
            "type": "image",
            "image": {
                "images":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png"
                }
                ]
            }
        },
        {
            "fieldId": "163195",
            "type": "file",
            "file": {
                "files":[
                    {
                "url":"https://ncstatic.clewm.net/rsrc/2024/1220/11/aa41c8b612eafeac06ed90ae0ce53092.png",
                "name":"WeCom_screenshot_fa4224c9-0cbf-4476-ad81-929f321db2dd.png"}
                ]
            }
        }
    ]
}',
  CURLOPT_HTTPHEADER => array(
    'Content-Type: application/json',
    'Authorization: Bearer Xs8UuJ4Ap4ZH7T2fZPzuBwAgLZL9U0v9qFW6Tv5tt9M='
  ),
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```