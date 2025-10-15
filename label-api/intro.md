# 一物一码标签制作

## 功能介绍

草料提供批量生码、标签制作的能力，你可以将草料二维码与企业的内部系统集成，作为整个企业信息化体系的组件。对接草料标签API后，**可在自有系统或网页中，批量生成二维码标签**，替代了将数据导出再导入草料平台批量生码的模式，更加高效便捷。

例如可对接产品、资产、溯源等自有管理系统，当有新增数据时，可根据规则自动拼接标签url，在系统里批量生成对应产品或资产标签，用于下载打印。

![file](https://blogcdnimg.clewm.net/2023/11/image-1698821337352_16988213383853.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## API调用方式

### 调用私有样式

适用于调用账号下已保存的标签样式，例如基于草料提供的公共样式，设置过企业logo、标签背景色、字段数等。

在后台-「标签样式」目录下选择之前保存的我的标签样式，进入标签样式详情页，点击「API对接」，开启调用。调用时再根据需求传入不同的参数内容， 即可批量生成不同的标签图片。

![file](https://blogcdnimg.clewm.net/2023/08/image-1692783856092_16927838567829.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

[私有样式API接口文档](https://cli.im/help/87763)

### 调用公共样式

适用于直接调用草料标签样式库中的公共样式。可在[标签样式库](https://cli.im/label)中，选择一个标签，直接获取标签编号，或者进入样式详情页，点击开通标签制作API。调用时再根据需求传入不同的参数内容， 即可批量生成不同的标签图片

![file](https://blogcdnimg.clewm.net/2023/11/image-1700631336604_17006313376686.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

[公共样式API接口文档](https://cli.im/help/87765)

## 调用流程及说明

### 调用流程

![file](https://blogcdnimg.clewm.net/2023/10/image-1698368753434_16983687539373.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 调用说明

1. Beta期间 开通API 的用户可长期免费调用；

2. API调用根据IP秒级并发30次，如需更高并发次数，可[前往社区反馈](https://cli.im/community/minihome/mixflow/90)

3. 如果标签API调用流程、速度等方面问题，可以[前往社区反馈](https://cli.im/community/minihome/mixflow/90)，草料官方顾问和技术会定期查看并回复

## 客户案例

### 1. 第三方开发者，开发插件集成飞书多维表格

可利用草料标签API接口，开发相应插件，集成在自己的软件或者系统中，提供批量生成二维码标签的能力。

例如第三方开发者Ryan Cui基于标签API开发的「草料二维码」插件，已经在飞书多维表格提供。通过插件，用户在飞书多维表格中可直接选择标签样式，匹配字段，将会自动调用草料的标签API，批量生成二维码标签。[了解详情](https://cli.im/help/88738)

效果演示：

![](https://blogcdnimg.clewm.net/2023/09/111_16952671050634.gif?x-oss-process=)

### 2. 某车友社区，将API内嵌网页，实时生成标签

可在现有系统或网页中接入草料标签API，标签图将会自动生成插入。新增数据时，可自动调用草料标签API，将指定的内容生成二维码标签展示。

例如某车友社区平台，调用草料标签API，将微信群地址生成二维码标签，插入社区网页中，无需另外生成标签后再上传，更加高效便捷。

![file](https://blogcdnimg.clewm.net/2023/10/image-1698218056751_16982180578545.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)