# 群消息推送

## 场景简介

通过腾讯轻联，将表单填写的记录，即时推送到内部工作群，支持企业微信、飞书、钉钉，此外还可以以邮件和短信推送消息。

**适用场景：**
隐患排查提醒、故障报修提醒、预约报名通知、巡检异常提醒等。

![](//blogcdnimg.clewm.net/2023/03/image-1680056669818_16800566709529.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 图文教程

以我们常用的故障上报应用为例，实现将上传的故障记录推送到企业微信群。
钉钉群和飞书群的推送也是类同的。

### 概述

需要进入腾讯轻联，搭建新流程，触发应用为【草料二维码】，执行应用为【企业微信群机器人】。

## 准备工作

1. 创建好故障上报二维码或自己场景二维码，[示例模板](https://cli.im/share/yUNDZTv)
2. 在企业微信群添加群机器人，[如何开启企微群机器人](https://open.work.weixin.qq.com/help2/pc/14931)

### 1. 创建流程

登录[腾讯轻联后台](https://ipaas.cloud.tencent.com/login)，【新建流程】

![](https://blogcdnimg.clewm.net/2023/12/image-1703221820136_17032218207439.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 配置草料应用

- **添加草料二维码应用，选择触发方式为**：新表单提交；

![](https://blogcdnimg.clewm.net/2023/12/image-1702621882685_17026218831515.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **授权配置**

![](https://blogcdnimg.clewm.net/2023/12/image-1702621898895_17026218993538.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **参数配置**
点击执行预览，下面会出现监听地址，复制该地址，配置到表单的数据API中。

![](https://blogcdnimg.clewm.net/2023/12/image-1702622036385_17026220368551.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **配置webhook地址**
复制腾讯轻联推送地址到草料后台的webhook推送地址。在【表单设置】>【设置】>【数据API】里添加，或在导航栏【高级功能】> 【数据API】中添加

![](https://blogcdnimg.clewm.net/2023/12/image-1702622063920_17026220645867.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **样本数据**
扫码二维码，添加一条数据，轻联侧会自动监听到样本数据。
*注意：如果表单有更新，需再添加一条表单记录，可以在样式数据中选择最新那条记录后，点击【重新预览】。

![](https://blogcdnimg.clewm.net/2023/12/image-1702622078956_17026220798412.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. 添加执行应用：企业微信群机器人

同类方式可以添加钉钉群机器人和飞书群机器人。

- **添加企微机器人，选择执行操作**：发送富文本消息；

![](https://blogcdnimg.clewm.net/2023/12/image-1702620476047_17026204767409.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **授权配置**；添加企微群机器人地址
需要在企微群中添加群机器人，获取机器人地址。[如何开启企微群机器人](https://open.work.weixin.qq.com/help2/pc/14931)

![](https://blogcdnimg.clewm.net/2023/12/image-1702620643237_17026206438181.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **参数配置**
富文本消息为：引用变量+文本的方式，推送动态信息，可参考下图 。配置好后，点击执行预览，就可以在企微群中收到该条消息。

![](https://blogcdnimg.clewm.net/2023/12/image-1702620768462_17026207694901.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![](https://blogcdnimg.clewm.net/2023/12/image-1702620802545_17026208034045.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. 发布流程

保存后，两个应用都被打上勾兑，说明流程配置成交，点击【发布】。如有错误发布不了，可以点击【检查】查看问题。

![](https://blogcdnimg.clewm.net/2023/12/image-1702621014716_17026210155847.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 参考资料

1. [腾讯轻联场景连接器网站](https://qinglian.tencent.com/)
2. [腾讯轻联场景连接器新手教程](https://qinglian.tencent.com/help/docs/sHInHG/)
3. [草料webhook说明](./data-api/webhook.md)

## 更多应用场景

- [同步到腾讯文档](https://cli.im/help/78994)
- [AI功能扩展](https://cli.im/help/78997)

## 常见问题

### 1. 为什么我的变量跟表单内容不一致。

这是因为你重新选择了新的表单，需要重新提交记录，再点击测试样式，选择新样本。

### 2. 如何实现按条件提醒，比如巡检异常。

可以草料应用后面添加一个内置的条件判断应用，设置条件，满足执行群消息提醒，不满足则不处理。这里支持组合条件。

![](https://blogcdnimg.clewm.net/2023/12/image-1702625193428_17026251939159.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. 是否可以同时执行提醒到多个群。

可以的，添加新流程，流程中添加新的群机器人地址（新账号）。

### 4. 是否能按条件，提醒到不同的群。

可以的，结合条件判断应用，满足不同的条件，执行不同的群消息应用，各应用添加的是不同的群机器人地址。

## 草料社区

为此功能特开了个社区版本，可以分享使用经验，发布问答、会有专业顾问为你解答，[前往社区](https://cli.im/community/minihome/question/104)
