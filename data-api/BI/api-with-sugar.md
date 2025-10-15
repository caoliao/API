# 数据API+百度SugarBI，搭建可视化看板

通过数据API功能将草料收集到的数据推送到百度SugarBI中，可自由应用数据，搭建自己想要的看板内容。SugarBI为百度研发的可视化工具，需额外付费购买。

草料目前已经和百度SugarBI完成了对接，通过SugarBI制作的看板支持内嵌到草料的小程序中直接跳转访问。同时草料用户购买百度SugarBI的付费版本可享受折扣优惠，原价480元/年仅需400元/年。

## 一、案例效果

### 1. 设备状态与巡检计划完成情况分析

可以快速查看重点计划完成率、未完成数量，点击可详细查看设备清单。还可以筛选指定日期内的完成情况。[查看示例](https://sugar.aipage.com/report/r_1013e-17hzobcu-kbgmgv/86b0d1a98d22b5afe789e16c0502f69d)

![](//blogcdnimg.clewm.net/2021/08/16296800933186_效果1.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 出入库库存统计与明细查询

支持输入品类名称，查询当前库存与出入库数量。[查看示例](https://sugar.aipage.com/report/r_1013e-boo7mgij-kejxgz/8b0d83bc802236bbcc12a545fa4f1cbd)

![](//blogcdnimg.clewm.net/2021/08/16296800924176_效果2.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

更多案例效果：[可视化看板案例合集](https://cli.im/help/94931)

### 使用前须知

上述看板是由草料提供的 **数据api功能+百度SugarBI** 制作

#### 1.数据api功能介绍

草料提供了**官方数据库功能**，草料平台中的码数据、表单数据、状态与计划数据等，会实时同步您账号对应的阿里云数据库。使用外部的BI（数据分析）工具，连接此数据库，就可以制作出各类想要的看板效果。[查看官方数据库说明](https://cli.im/help/62995)

::: info 提示
api数据会根据在草料设置的功能来推送，如：
在草料后台设置了状态功能，就会推送 code_state，即码的状态数据；在草料后台添加了计划并执行后，就会推送 code_task_log，即码的计划完成情况数据；**未设置相关功能或者无数据产生时并不会推送。**
:::

**建议您在使用二维码并有相关数据产生后，再去制作可视化看板。**

#### 2.百度SugarBI

SugarBI 是百度研发的数据可视化工具。推荐百度SugarBI，原因是价格便宜（推荐基础版：价格480元/年），并且数据实时更新，还提供1个月的免费试用。目前草料已与百度Sugar BI团队达成协议，用户购买百度的SugarBI可享受折扣优惠，基础版400元/年即可购买。具体购买流程可看下方介绍

## 二、应用教程

### 1. 开启草料的官方数据库

可以在登录草料后，后台左侧`数据管理`–`数据API`，选择`官方数据库`（[前往使用](https://user.cli.im/opendata)）。

![](https://blogcdnimg.clewm.net/2024/07/image-1719908536590_17199085325376.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

官方数据库申请成功后得到的数据库示例如下：

``` plaintext
类型：MySQL 5.7
主机：rm-bp1m4fy8d66u3c6xmbo.mysql.rds.aliyuncs.com
端口：3306
数据库名：cli_13268724（示例）
用户名：cli_13268724（示例）
密码：ekiji17jd02jk9md（示例）
```

### 2. 注册并使用百度SugarBI

百度云注册链接，[点击进行注册](https://login.bce.baidu.com/)，注册一个新账户（云账号/百度账号均可，建议云账号），注册之后不要做任何实名认证，然后将账户ID发送给百度智能云客户经理，此账户之后即可享受百度SugarBI的专属折扣优惠。

注：此步骤需在您试用百度SugarBl前完成，完成对接后可获得百度智能云专属一对一支持

![](https://blogcdnimg.clewm.net/2024/06/image-1719462996692_17194629967138.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

扫码添加百度云智能客户经理

![](https://blogcdnimg.clewm.net/2024/06/image-1719463174020_17194631739396.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

百度sugar 官网：[https://cloud.baidu.com/product/sugar.html](https://cloud.baidu.com/product/sugar.html)

百度sugar 操作文档：[https://cloud.baidu.com/doc/SUGAR/s/ek6z5wq34](https://cloud.baidu.com/doc/SUGAR/s/ek6z5wq34)

### 3. 百度SugarBI视频教程

视频教程分上下篇：

- **上篇**是介绍 数据分析的流程和准备工作（约5分钟）；
- **下篇**是介绍 使用百度Sugar制作报表（约15分钟）。

------

### 4. 连接百度SugarBI图文教程

基本流程：连接数据源-创建数据模型-制作报表-预览和分享

#### 1.连接数据源

在SugarBI中选择资源中心-数据管理-数据源-添加数据源，选择类型：MySQL 5.X，填上草料提供的官方数据库信息，添加即可。

![](https://blogcdnimg.clewm.net/2024/07/image-1719909602110_17199095980447.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 2.创建数据模型

数据模型可用于后续图表中的数据展示， 选择**数据模型-新建数据模型**，在创建数据模型时会用到草料数据api中的数据表，[查看数据表说明](https://cli.im/help/62995)

![](https://blogcdnimg.clewm.net/2024/06/image-1719463581342_17194635812710.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

上一步新建了数据模型后即会进入到模型的编辑页面，页面的左侧会列出数据源中的所有数据表，拖动要分析的数据表至页面中间区域

![](https://blogcdnimg.clewm.net/2024/07/image-1719909747967_17199097438860.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

在这里给大家推荐比较常用的数据模型：

**模型一：设备状态分析**

base_codeinfo（码的基本信息表）内关联code_state（码的状态表），得到各设备的状态值与更新时间，分析状态分布。

![](https://blogcdnimg.clewm.net/2024/07/image-1719910223945_17199102198638.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**模型二：计划完成情况**

code_task_log（计划执行情况表） 左关联 base_codeinfo（码的基本信息表），得到计划完成情况并与之对应的码信息。

![](https://blogcdnimg.clewm.net/2024/07/image-1719910248526_17199102444209.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**模型三：批量码分析**

template_XXXXXX （批量码信息表）左关联 table_dXX（表单数据表）、code_state（码的状态表）。template_XXXXXX可以获取到码的可变内容信息。

![](https://blogcdnimg.clewm.net/2024/07/image-1719910319539_17199103154583.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**模型四：串联后续表单记录**

比如在故障上报的记录里，添加维修记录表单，将这两条记录串联起来得到完整的信息。[添加后续动态功能介绍](https://cli.im/help/82975)
使用table_dxx（故障上报表）左关联table_dxx(维修记录表单)，关联条件是 记录编号和来源编号。如果还有更多后续表单，可以再左关联此表单。

![](https://blogcdnimg.clewm.net/2024/07/image-1719910574006_17199105699635.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 3.创建报表

SugarBI 可制作报表与大屏，这里介绍报表的创建方法，大屏也同理。两者区别在于，大屏是一屏显示，各图表可以精细编辑；报表是上下浏览，内容更多，便于内部分享分析。

![](https://blogcdnimg.clewm.net/2024/07/image-1719910638933_17199106348642.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 4.增加图表并绑定数据

在报表编辑器中，您可以通过页面顶部的工具栏新增一个图表（如环形饼图）

![](https://blogcdnimg.clewm.net/2024/07/image-1719910874431_17199108703848.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

按照以下步骤将数据模型中的字段绑定到环形饼图上进行可视化展现

![](https://blogcdnimg.clewm.net/2024/07/image-1719910897581_17199108935221.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

1. 点击选中要操作的环形饼图，页面右侧的「控制面板」会展现该图表的配置项
2. 选择要使用的数据模型
3. 将code_task_log表中的状态维度字段拖拽至扇区名称
4. 将记录数度量字段拖拽至扇区大小，即可看到该环形饼图会自动展示按照计划完成情况进行汇总的已检/未检图表
5. 可拖动图表的位置，以及调整图表的大小。还可以向页面中增加其它的图表，都和上面的环形饼图类似的操作即可。
6. 点击页面右上角的「保存」并「退出」即可。

#### 5.分享使用

自由搭建完看板内容后可分享使用，设置分享（发布）为公开，复制链接即可

![](https://blogcdnimg.clewm.net/2024/07/image-1719910975375_17199109713264.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 三、学习交流

在实际操作过程中可能会遇到各类问题，可以 [前往草料社区](https://cli.im/community/minihome/question/104) 查看相关问题或提问，与数据报表大牛互助交流，草料官方顾问和技术也会定期查看并回复
