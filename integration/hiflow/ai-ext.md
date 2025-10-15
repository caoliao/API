# AI功能扩展

## 场景简介

腾讯轻联应用中心内置丰富的智能AI应用，可自动识别图片、语音等数据，进一步提高工作效率。

**可对接的应用:**
身份证OCR，防疫健康码识别，银行卡，发票，表格图片解析，语音转文字等。

**适用场景:**
防疫记录自动识别、劳务人员上报银行卡等。

![file](//blogcdnimg.clewm.net/2022/09/image-1662541984660_16625419862039.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 实操体验

扫码以下二维码，填写防疫信息后，[查看防疫登记表](https://docs.qq.com/sheet/DU25QUENVem5IV0tl?tab=BB08J2)。
*注意，别忘记删除自己提交的那行数据，其它数据不要动。

![file](//blogcdnimg.clewm.net/2023/03/image-1680057762745_16800577631522.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 操作教程：

以防疫登录为例，自动识别健康码，并且识别结果同步到腾讯文档，并且将异常情况提醒到企业微信群。

> 注意：当前轻联的AI组件升级中，相同的AI应用有两个，选择带**V2**的版本，另一个无法使用

### 准备工作：

1. 创建疫情二维码或者自己场景二维码，[示例模板](https://cli.im/share/7NpigkN)
2. 在个人腾讯文档中创建个报名表格，并编辑好表头，[示例表格](https://docs.qq.com/sheet/DU25QUENVem5IV0tl?tab=BB08J2)

### 1. 创建流程

登录[腾讯轻联后台](https://ipaas.cloud.tencent.com/login)，【新建流程】

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229830275_17032298308771.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 配置草料应用

- **添加草料二维码应用，选择触发方式为**：新表单提交；

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229894502_17032298949209.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **授权配置**

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229907792_17032299082049.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **参数配置**
点击执行预览，下面会出现监听地址，复制该地址，配置到表单的数据API中。

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229995917_17032299966761.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **配置webhook地址**
复制腾讯轻联推送地址到草料后台的webhook推送地址。在【表单设置】>【设置】>【数据API】里添加，或在导航栏【高级功能】> 【数据API】中添加

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230030503_17032300310309.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **样本数据**
扫码二维码，添加一条数据，轻联侧会自动监听到样本数据。
*注意：如果表单有更新，需再添加一条表单记录，可以在样式数据中选择最新那条记录后，点击【重新预览】。

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230053355_17032300538076.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. 添加AI防疫健康码识别

添加AI防疫健康码识别-V2，配置参数中图件地址为 健康码字段中的 urls中的[0]，表单取健康码组件中第一张图片的地址。（图片组件是支持多图上传的）

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230509599_17032305100334.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. 添加 AI通信行程卡识别

添加AI通信行程卡识别-V2，配置参数中图件地址为 行程码字段中的 urls中的[0]，表单取行程码组件中第一张图片的地址。（图片组件是支持多图上传的）

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230527314_17032305277374.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 5. 添加 腾讯文档

添加腾讯文档应用，这里只支持个人版的腾讯文档，配置好账号。

- **选择推送的表格**：事先需要在腾讯文档中创建一个表格，编辑好标题列，选择好表格和工作表。
- **字段匹配**：按标题添加对应表单组件数据，测试并预览，在腾讯文档中查看一下是否有数据过来。

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230543384_17032305438811.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 6. 上线流程

最后点击右上角的 上线流程 就完成了此流程的创建。

## 参考资料

1. [腾讯轻联场景连接器网站](https://qinglian.tencent.com/)
2. [腾讯轻联场景连接器新手教程](https://qinglian.tencent.com/help/docs/sHInHG/)
3. [草料webhook说明](./data-api/webhook.md)

## 更多应用场景

- [同步到在线文档](https://cli.im/help/78994)
- [群消息推送](https://cli.im/help/78992)

## 草料社区

如果你对**数据API功能**有使用方面的疑问或希望分享的经验，我们非常欢迎你在社区发表讨论，产品和技术人员都会参与互动。[前往社区](https://cli.im/community/minihome/question/104)