# 同步到在线表格，进行数据分析

## 场景简介

通过腾讯轻联，收集的表单数据同步到腾讯文档、维格表等应用，进行汇总统计、数据分享和协同编辑等操作。还支持同步到Mysql数据库。

![file](//blogcdnimg.clewm.net/2023/03/image-1680055897726_16800558982709.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 效果演示

我们以常见的消火栓巡检为例，使用腾讯轻联将巡检记录同步到腾讯文档的智能表，进行各巡检人员的工作量统计、按日期检查漏检情况、维修费用计算等。

### 视频演示

视频时长为：4分钟

<video src="//blogcdnimg.clewm.net/2022/10/tongbuwendang_16659810199560.mp4" controls></video>

## 参考资料

1. [消火栓巡检表（腾讯文档）](https://docs.qq.com/sheet/DU1JMRWdHb1FNbm5h?tab=0r6h9i)
2. [腾讯轻联场景连接器网站](https://qinglian.tencent.com/)
3. [腾讯轻联场景连接器新手教程](https://qinglian.tencent.com/help/docs/sHInHG/)
4. [草料webhook说明](./data-api/webhook.md)

## 更多应用场景

- [群信息推送](https://cli.im/help/78992)
- [AI功能扩展](https://cli.im/help/78997)

## 常见问题

#### 1. 现只支持个人版腾讯文档，不支持企业微信版的。

#### 2.如何将腾讯表格链接到码上

以小程序方式链接到码上就可以。

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740448783_16987404495615.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**添加【跳转链接】选择【其它小程序**

``` plaintext
appID：wxd45c635d754dbf59
账号原始ID:gh_252c5f06840b
小程序路径：pages/detail/detail.html?url=表格链接
```

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740057186_16987400576742.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**表格链接：为编辑表格时的地址栏地址**

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740255899_16987402565423.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 3. 腾讯表格的表头名称可以跟表单组件名称要一样吗？

可以是不一样的，内容是手工匹配的，并不是按名称自动识别匹配。

## 草料社区

为此功能特开了个社区版本，可以分享使用经验，发布问答、会有专业顾问为你解答，[前往社区](https://cli.im/community/minihome/question/104)
