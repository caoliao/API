# Webhook

## 功能介绍

草料将【动态数据】以JSON格式推送到指定接口URL，将数据传输到另一个系统，实现消息提醒和业务对接。
这个地址需要 **`允许公网访问`**。你的服务器需在5s内返回200状态值作为应答；应答异常最多重试5次（15s/1m/4m/16m/1h）

> 当前只支持表单数据推送，包含新提交表单数据、修改表单数据、表单审核结果、标记处理进度推送

## 应用场景

### 1. 连接第三方应用，实现群消息推送，表格数据汇总

通过腾讯轻联（腾讯云推出的"应用连接器"），将草料二维码和其他应用/服务进行连接。
实现如：数据群消息推送、数据二次分析、对接CRM系统、智能AI等功能。以此打破数据孤岛，让数据发挥价值。[了解详情](https://cli.im/help/78884)

[![了解详情](//blogcdnimg.clewm.net/2024/05/image-1714890027335_17148900210360.png)](https://cli.im/help/78994)

### 2. 对接自有系统

将扫码收集数据等功能在草料平台实现，再通过API与企业系统的流程进行对接，企业即可在保留原有系统的前提下，以极低的成本应用草料功能。

![file](//blogcdnimg.clewm.net/2022/02/image-1644546273607_16445462739484.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 操作流程

可以在**表单设置页面**选择数据API，添加推送地址，

也可以在**数据API功能页面**添加推送地址后选择表单推送。

### 1. 表单设置页

表单设置页中，选择【数据API】,填写名称和推送的地址，点保存完成设置。
*`*注意：该设置为表单全局设置，关联此表单的所有码上生效。`*

![file](//blogcdnimg.clewm.net/2022/11/image-1668743694361_16687436948264.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![file](//blogcdnimg.clewm.net/2022/11/image-1668743709153_16687437095751.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 数据API功能页

进入后台 【数据管理】-【数据API】 - 【开通webhook】 填写推送数据和选择需要推送的表单。已开通过的情况下，点击配置，添加更多推送。
*`*注意：在使用腾讯轻联时，因为在腾讯轻联中无法选择表单，所以这里只能选择一个表单或者直接在表单中设置`*

![file](https://blogcdnimg.clewm.net/2024/04/image-1714370711612_17143707125963.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![file](//blogcdnimg.clewm.net/2022/11/image-1668743728364_16687437287845.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 推送数据类型

当前仅支持表单记录的数据推送。但当二维码是批量子码时，除表单记录字段外，还会将模板名称和可变内容一起推送过去。还不支持仅推送子码可变内容

- 普通活码：推送表单记录
- 批量子码：推送表单记录+批量模板名称+子码可变内容

## 推送事件类型

现在支持以下几种事件。

- 新提交表单数据
- 修改表单数据
- 表单审核结果推送
- 标记进度状态更新

## 推送格式说明

### 推送方式

```text
POST
Content-Type: application/json
```

### 格式

草料的所有事件请求均遵循以下格式：

```json
{
    "time": "2022-06-30 17:06:39",
    "event": "事件标识",
    "data": {}
}
```

### 各字段解释如下：

| 字段名 | 含义 | 类型 |
|--------|------|------|
| time | 事件的发生时间，采用+8区YYYY-mm-dd HH:ii:ss表示 | string |
| event | 事件，事件枚举见事件类型章节 | string |
| data | 数据，不同的事件拥有不同的格式，以具体事件的文档为准。 | object |

## 事件类型标识

| 事件 | 标识 |
|------|------|
| 有新的表单数据提交 | FORM_DATA_SUBMIT |
| 表单数据被编辑 | FORM_DATA_EDITED |
| 表单数据被审核 | FORM_DATA_REVIEW |

### 有新的表单数据提交

表单事件暂时不会推送音频、视频、文件类型的数据

示例数据:

```json
{
  "time": "2022-06-30 17:06:39",
  "event": "FORM_DATA_SUBMIT",
  "data": {
    "ref_data": {
      "created_at": "2022-06-30 17:06:39",
      "serial_number": "L1000001",
      "form": {
        "number": "D20",
        "name": "会议签到"
      },
      "submitter": {
        "name": "填写人A",
        "phone_number": "18888881111"
      },
      "review": {
        "state": "待审核",
        "time": "2022-06-30 17:06:39"
      },
      "process": {
        "state": "未处理",
        "time": "2022-06-30 17:06:39"
      },
      "fields": {
        "姓名": "草料",
        "手机": "18888648888",
        "微信名": "CHEN",
        "身份证号": "330200000000000000",
        "工号": "FBI100",
        "单选项": "是",
        "多选项": [
          "选项1",
          "选项3"
        ],
        "检查项": {
          "项目1": "是",
          "项目2": "否",
          "项目3": "无需填写",
          "项目4": ""
        }
      },
      "ref_qrcode": {
        "name": "测试二维码",
        "type": "CHILD",
        "code": "qAbCxZ",
        "template": {
          "name": "测试模板"
        },
        "fields": {
          "文本1填充位": "A",
          "文本2填充位": "B"
        },
        "state": {
          "状态组1": "异常",
          "状态组2": "正常"
        }
      }
    }
  }
}
```
### 字段说明

| 字段 | 描述 | 类型 |
|------|------|------|
| time | 事件发生时间 | string |
| event | 事件标识 | string |
| data | 事件详情数据 | object |
| data.ref_data | 事件中表单详情数据 | object |
| data.ref_data.created_at | 填表时间 | string |
| data.ref_data.serial_number | 记录编号 | string |
| data.ref_data.web_url | 记录地址 | string |
| data.ref_data.form | 表单信息 | object |
| data.ref_data.form.number | 表单编号 | string |
| data.ref_data.form.name | 表单名称 | string |
| data.ref_data.submitter | 表单填写人信息 | object |
| data.ref_data.submitter.name | 表单填写人名称 | string |
| data.ref_data.submitter.phone_number | 表单填写人手机号 | string |
| data.ref_data.review | 审核信息（仅开启审核功能存在） | object |
| data.ref_data.review.state | 审核状态<br>审核中/审核通过/审核不通过 | string |
| data.ref_data.review.time | 审核时间 | string |
| data.ref_data.process | 闭环信息（仅开启闭环功能时存在） | object |
| data.ref_data.process.state | 闭环处理状态 | string |
| data.ref_data.process.time | 闭环处理时间 | string |
| data.ref_data.fields | 表单字段（组件）信息 | map<string, any> |
| data.ref_qrcode | 二维码信息 | object |
| data.ref_qrcode.name | 二维码名称 | string |
| data.ref_qrcode.type | 二维码类型<br>CHILD(子码)/NORMAL(普通活码) | string |
| data.ref_qrcode.code | 码唯一标识 | string |
| data.ref_qrcode.web_url | 码链接 | string |
| data.ref_qrcode.template | 码模板信息（仅子码存在） | string |
| data.ref_qrcode.template.name | 码模板名称 | string |
| data.ref_qrcode.fields | 子码填充位信息（仅子码存在） | object |
| data.ref_qrcode.state | 码状态信息 | map<string, string> |

其中表单字段信息（data.ref_data.fields）和子码字段信息（data.ref_qrcode.fields）内均是key value形式的数据。key代表组件/填充位名称，value代表值。value的类型视该组件的类型决定。

### 表单数据被编辑

事件标识为：FORM_DATA_EDITED
请求数据与 "有新的表单数据提交" 事件相同

### 表单数据被审核

事件标识为：FORM_DATA_REVIEW
请求数据与 "有新的表单数据提交" 事件相同，可以通过data.ref_data.review.state字段获取审核结果

### 表单组件数据示例

姓名、手机、微信名、身份证号、工号、车牌、性别、单行文本、多行文本、日期、时间、但选项、多级选择、编号

均以字符串格式推送。例如：

```json
{
    "fields": {
        "姓名": "草料",
        "性别": "男",
        "多级选择": "浙江省/宁波市/海曙区"
    }
}
```

#### 检查项

检查项是一个map<string, enum string>组成，例如：

```json
{
    "fields": {
         "检查项A": "是",
         "检查项B": "否",
         "检查项C": "无需填写",
         "检查项D": "",
    }
}
```

#### 值的枚举如下

| 值 | 含义 |
|---|---|
| 是 | √ |
| 否 | × |
| 无需填写 | / |
| 空字符串 | |

#### 图片

图片类型组件的值是一个对象，内容如下：

```json
{
    "fields": {
         "图片": {
             "preview_url": "https://草料预览URL/",
              "urls": [
                "图片1下载链接",
                "图片2下载链接"
              ]
         }
    }
}
```

## 常见问题

### 1. webhook功能收费吗？

草料的不同收费版本对应不同的每月推送动态数据条数：

- 免费版、基础版和高级版：1,000条/月；
- 旗舰版：20,000条/月；
- 行业专属版：推送条数不限。

具体查看[草料版本推送说明](https://cli.im/help/84383)

如果你对接了腾讯轻联，腾讯轻联有自己的收费规则，腾讯轻联的免费版：500个任务/月。具体查看[腾讯轻联版本定价说明](https://qinglian.tencent.com/price/)

### 2. 推送条数的计算方式

每一次数据推送就算一条，有新表单记录、完成审核操作、变更闭环状态、还有修改表单记录。

### 3. 图片组件有两个地址，应该如何选择。

每个图片组件我们提供了两个地址，xxx.urls和xxx.preview_urls两种。

- xxx.urls是图片地址，可以引用后直接显示图片（有多图时，不能直接显示），可用于群消息推送时，消息中直接显示图片，也可以用于AI识别；
- xxx.previews_urls是图片预览页地址，可以打开这个地址，浏览多个图片。应用时以超链接的方式进行展示，点击去浏览图片内容。