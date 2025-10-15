# 二维码动态数据

## 示例动态数据

> 施工中

## 动态数据类型对照表

| 类型 ｜ type常量 | 使用的属性 | 
|------ | ----- | ------ |
| 表单填写 | 1 | recordSubmit |
| 状态变更 | 2 | stageChange |
| 文件签阅 | 3 | fileRead |
| 成员加入 | 4 | memberJoin |
| 底部协作 | 5 | comment |
| 码内容修改 | 6 | qrcodeChange |

## 数据详情

`type` integer

动态数据类型, 请参考[动态数据类型对照表](#动态数据类型对照表)

---

### 表单填写

`recordSubmit` object

当type=1时使用, 使用该字段

`recordSubmit.serialNumber` string

记录编号

---

`recordSubmit.qrcodeCoding` string

二维码Coding

---

`recordSubmit.formSerialNumber` string

表单编号, 假设类型为表单填写, 则该字段为表单编号

---

`recordSubmit.recorder` string

填写人

---

`recordSubmit.addTime` string

填写时间(yyyy-MM-dd HH:mm:ss)

---

`recordSubmit.fields` []FormField

字段列表，请参考[表单字段](./openapi/api/forms/form-field-schema.md)

