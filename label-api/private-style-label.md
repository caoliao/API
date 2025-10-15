# 私有样式

## 一、功能说明

该接口文档适用于：调用账号下已保存的标签样式，在自有系统或网页中，批量生成不同内容的二维码标签。

对接后，可在自有系统里，批量生成二维码标签。无需导出数据在我们平台再导入数据生码。例如可对接产品、资产等管理系统，当有新增数据时，可根据规则自动拼接标签url，在系统里批量生成对应产品、资产标签。

![](https://blogcdnimg.clewm.net/2023/11/image-1698822211822_16988222124612.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 二、接口调用说明

### URL

```plaintext
https: //open-api.cli.im/cli-open-platform-service/v1/labelStyle/createWithKey
```

### HTTP请求方式

GET

### 请求参数

| 参数名称 | 是否必须 | 类型 | 说明 |
|---------|---------|------|------|
| cliT | 是 | string | 标签样式编号,例如D10 |
| cliD | 是 | string | 二维码动态内容 |
| api_key | 是 | string | 用户账号api key |
| sign | 是 | string | 签名，生成方式见加签方式 |
| return_file | 否 | string | 返回类型，不传时返回二进制图片流，base64-返回base64编码 |
| cliF | 否 | string | 根据我的样式需要传入的动态字段，**cliF表示普通文本字段**，cliP表示图片字段，按照字段展示顺序排列，例如我的样式有3个字段，全为文本字段，传入参数为：cliF1=xx&cliF2=xx&cliF3=xx |
| cliP | 否 | string | 根据我的样式需要传入的动态字段，**cliP表示图片字段，**图片需要公网可访问静态地址，例如我的样式有4个字段，第二个为图片字段，其余为文本字段，传入参数为：cliF1=xx&cliP2=xxcli3=xx&cliF4=xx |

### 加签方式

> 加签目的：使用MD5进行动态加签，通过在每次请求中生成新的签名，确保数据的安全性和完整性，防止数据被篡改或冒充，提高系统的安全性。
>
> 后台也可关闭动态加签，关闭后即可无需进行下方加签操作。

1、将请求参数按照key的字典序排列，然后用&拼接成字符串，例如使用以下请求参数。

| key | value |
|-----|--------|
| cliT | D10 |
| cliD | 测试数据单个制作标签 |
| return_file | |
| cliP1 | https://ncstatic.clewm.net/rsrc/2023/0331/11/823ace0e8a36e304ca8bfab683be6219.png |
| cliF2 | 京海市第一人民医院 |
| cliF3 | Jinghai First People's Hospital |
| cliF4 | 王菲菲 |
| cliF5 | 职务：助理护士 |
| cliF6 | 科室：住院部 |
| cliF7 | 编号：NO-GT-043 |
| api_key | CLb87ea759f877622c |

排序拼接后字符串为：

```plaintext
api_key=CLb87ea759f877622c&cliD=Test123&cliF2=京海市第一人民医院&cliF3=Jinghai First People's Hospital&cliF4=王菲菲&cliF5=职务：助理护士&cliF6=科室：住院部&cliF7=编号：NO-GT-043&cliP1=https://ncstatic.clewm.net/rsrc/2023/0331/11/823ace0e8a36e304ca8bfab683be6219.png&cliT=D11&return_file=
```

拼接系统提供的用户api secret到上述字符串最后，假设secret为ddb42b7299b90cb5e0fd6c41e154c15d，得到如下字符串：

```plaintext
api_key=CLb87ea759f877622c&cliD=Test123&cliF2=京海市第一人民医院&cliF3=Jinghai First People's Hospital&cliF4=王菲菲&cliF5=职务：助理护士&cliF6=科室：住院部&cliF7=编号：NO-GT-043&cliP1=https://ncstatic.clewm.net/rsrc/2023/0331/11/823ace0e8a36e304ca8bfab683be6219.png&cliT=D11&return_file=ddb42b7299b90cb5e0fd6c41e154c15d
```

**将以上字符串进行md5加密**，全部取小写，得到签名sign：

```plaintext
2f7ee4e4c678bde31a0345de23ea3d0e
```

### 返回参数

当return_file未传时，返回二进制图片

当return_file=base64时，返回base64图片编码，可用于嵌入网页或传输到系统中

请求示例：

```plaintext
https://open-api.cli.im/cli-open-platform-service/v1/labelStyle/createWithKey?api_key=CLb87ea759f877622c&cliT=D11&cliD=Test123&cliP1=https://ncstatic.clewm.net/rsrc/2023/0331/11/823ace0e8a36e304ca8bfab683be6219.png&cliF2=京海市第一人民医院&cliF3=Jinghai First People's Hospital&cliF4=王菲菲&cliF5=职务：助理护士&cliF6=科室：住院部&cliF7=编号：NO-GT-043&sign=2f7ee4e4c678bde31a0345de23ea3d0e&return_file=
```

### 返回示例

当return_file未传时，返回以下图片二进制流

当return_file=base64时，返回以下图片的base64编码，可用于嵌入网页或传输到系统中

![](https://blogcdnimg.clewm.net/2023/08/image-1692782280118_16927822806222.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 错误码

| 错误码 | 错误码取值 | 解决方案 |
|--------|------------|----------|
| 200 | 成功 | 成功 |
| 400 | 请求的数据格式不符！ | 请检查参数正确性 |
| 40000 | 系统繁忙，请稍后再试 | 系统可能维护升级中，等待后续功能恢复 |
| 40001 | 参数错误 | 检查传递参数是否按照文档规范 |

## 三、调用代码示例

在草料后台，【标签样式】目录下选择之前保存的我的标签样式，进入标签样式详情页，点击【调用API制作】，开启调用。

如果没有样式，可以先创建样式。标签制作页链接：[https://cli.im/label](https://cli.im/label)

![](https://blogcdnimg.clewm.net/2023/08/image-1692782453038_16927824537666.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

开通标签API对接，即可获取到APIkey和API_secret。还可设置调用范围，可选择公开或者指定IP域名可调用。

![](https://blogcdnimg.clewm.net/2023/10/image-1696665524987_16966655255518.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

例如调用的人员样式有7个固定字段,第1个为图片字段，其余为文本字段

所以API动态字段为cliP1到cliF7,以下为示例代码：

```java
package org.cli.platform.service.util;

import org.apache.commons.io.IOUtils;

import java.io.File;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.InputStream;
import java.net.HttpURLConnection;
import java.net.URL;
import java.net.URLEncoder;
import java.nio.charset.StandardCharsets;
import org.apache.commons.codec.digest.DigestUtils;
import org.apache.commons.io.IOUtils;
import org.springframework.web.util.UriUtils;

public class CliApiV1Demo {
    public static void main(String[] args) throws IOException {
        String cliD = "Test123";
        String cliP1 = "https://ncstatic.clewm.net/rsrc/2023/0331/11/823ace0e8a36e304ca8bfab683be6219.png";
        String cliF2 = "京海市第一人民医院";
        String cliF3 = "Jinghai First People's Hospital";
        String cliF4 = "王菲菲";
        String cliF5 = "职务：助理护士";
        String cliF6 = "科室：住院部";
        String cliF7 = "编号：NO-GT-043";
        String secret = "ddb42b7299b90cb5e0fd6c41e154c15d";

        Map<String, Object> params = new HashMap<>();
        params.put("api_key", "CLb87ea759f877622c");
        params.put("cliT", "D11");
        params.put("cliD", cliD);
        params.put("return_file", "");
        params.put("cliP1", cliP1);
        params.put("cliF2", cliF2);
        params.put("cliF3", cliF3);
        params.put("cliF4", cliF4);
        params.put("cliF5", cliF5);
        params.put("cliF6", cliF6);
        params.put("cliF7", cliF7);

        String data = params.entrySet().stream().sorted(Map.Entry.comparingByKey()).map(entry -> entry.getKey() + "=" + entry.getValue()).collect(Collectors.joining("&"));
        data += secret;
        String sign = DigestUtils.md5Hex(data);

        cliD = UriUtils.encode(cliD, StandardCharsets.UTF_8.name());
        cliP1 = UriUtils.encode(cliP1, StandardCharsets.UTF_8.name());
        cliF2 = UriUtils.encode(cliF2, StandardCharsets.UTF_8.name());
        cliF3 = UriUtils.encode(cliF3, StandardCharsets.UTF_8.name());
        cliF4 = UriUtils.encode(cliF4, StandardCharsets.UTF_8.name());
        cliF5 = UriUtils.encode(cliF5, StandardCharsets.UTF_8.name());
        cliF6 = UriUtils.encode(cliF6, StandardCharsets.UTF_8.name());
        cliF7 = UriUtils.encode(cliF7, StandardCharsets.UTF_8.name());

        //生成url请求
        String query = "https://open-api.cli.im/cli-open-platform-service/v1/labelStyle/createWithKey?cliT=D11&cliD=" + cliD + "&return_file=&cliP1=" + cliP1 + "&cliF2=" + cliF2 + "&cliF3=" + cliF3
                + "&cliF4=" + cliF4 + "&cliF5=" + cliF5 + "&cliF6=" + cliF6 + "&cliF7=" + cliF7 +
                "&api_key=CLb87ea759f877622c&sign=" + sign;

        URL url = new URL(query);
        HttpURLConnection connection = (HttpURLConnection) url.openConnection();
        connection.setDoOutput(true);
        connection.setRequestMethod("GET");
        connection.connect();

        InputStream stream = connection.getInputStream();
        try (FileOutputStream out = new FileOutputStream("test.png")) {
            IOUtils.copy(stream, out);
        }
    }
}
```

## 四、调用说明

1. Beta期间 开通API 的用户可长期免费调用；

2. API调用根据IP秒级并发30次，如需更高并发次数，可 [前往社区反馈](https://cli.im/community/minihome/mixflow/90)

3. 如果标签API调用流程、速度等方面问题，可以 [前往社区反馈](https://cli.im/community/minihome/mixflow/90) ，草料官方顾问和技术会定期查看并回复
