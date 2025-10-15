# 生成二维码

通过此API，你可以快速生成不同样式、尺寸、格式的二维码图像。您也可以开始将其嵌入到您自己的 Web 应用程序中，例如二维码生成器。我们的网站 [cli.im](https://cli.im) 也在使用此API。

## 使用规范

API请求没有限制，但为了保护服务质量和安全，我们会对以下行为的请求进行拒绝。

* 恶意或滥用性质的请求（如疑似DoS攻击等异常行为）
* 涉嫌用于非法或违规活动的请求

*如果您的正常请求被误判，请及时联系我们。*

## 快速入门

发起一个GET请求来生成二维码

```text
https://api.2dcode.biz/v1/create-qr-code?data=[URL编码文本]&size=[像素]x[像素]
```

你可以直接访问以下 URL 直接在浏览器中进行测试：

```text
https://api.2dcode.biz/v1/create-qr-code?data=Example&size=128x128
```

您也可以使用`<img>`标签可以轻松地将二维码嵌入HTML 文档中。 

**标签示例**

```html
<img src="https://api.2dcode.biz/v1/create-qr-code?data=Example&size=128x128" alt="" title="" />
```
生成/显示如下二维码图像

![](https://api.2dcode.biz/v1/create-qr-code?data=Example&size=128x128)

## 代码示例

:::code-group

```python
import requests

with open('qrcode.png', 'wb') as f:
    f.write(requests.get('https://api.2dcode.biz/v1/create-qr-code?data=Example').content)
```

```php
file_put_contents('qrcode.png', file_get_contents('https://api.2dcode.biz/v1/create-qr-code?data=Example'));
```

```javascript
const https = require('https');
const fs = require('fs');

https.get('https://api.2dcode.biz/v1/create-qr-code?data=Example', (res) => {
  res.pipe(fs.createWriteStream('qrcode.png'));
});
```

:::


## 参数

该API支持使用多个参数来配置二维码的创建, 只需在请求中添加 `&参数名称=参数值` 即可使用额外的参数。

### data(数据参数<必选>)

存储在二维码中的文本内容

**最小字符数**

1

**最大字符数**

具体容量取决于纠错级别(ecc参数)和其他因素。纠错级别越高,二维码能容纳的字符就越少。由于涉及的因素较多,这里不做详细说明。一般情况下,建议内容不超过900个字符。

### size(尺寸参数)

指定要生成的二维码图像的大小(当前仅对位图图像格式有效，如png)。

**格式**
* [整数]x[整数]
* [整数]

*两种格式均可，第二个格式会生成宽高相同的矩形图像*

**默认值**

`256x256`

**最小值**

不限制, 但当指定的图像宽高小于二维码矩阵需要的大小, 会以最小的二维码矩阵宽高输出

*通常而言至少要提供41x41像素的图像来满足二维码矩阵*

### format(格式)

**默认值**

`png`

**可选格式**

| 格式 | 类型 |
| -- | -- |
| png | 位图 |
| svg | 矢量 | 

### error_correction(错误矫正级别)

**默认值**

`M`

**可选值**

| 值 | 描述 |
| -- | -- |
| L | 低级别(7%) |
| M | 中级别(15%) |
| Q | 较高级别(25%) |
| H | 最高级别(30%) |

### border

二维码边框宽度(以码点为单位), 假设每个码点大小为10px, border=2, 则边框宽度就是20px

**默认值**

`2`

**最小值**

0

