# 表单字段(FormField)

该篇内容描述表单字段的定义。

表单字段使用type来区分不同的字段类型。不同的type使用不同的对象来存储字段值。

## type和使用的属性对照表

| type | 使用的属性 |
|----------|------------|
| name | nameValue |
| tel | telValue |
| recorder | recorderValue |
| identity | identityValue |
| job_number | jobNumberValue |
| carnumber | carNumberValue |
| sex | sexValue |
| text | textValue |
| textarea | textareaValue |
| number | numberValue |
| checklist | checkListValue |
| matrix | matrixValue |
| dynamic_matrix | dynamicMatrixValue |
| date | dateValue |
| time | timeValue |
| radio | radioValue |
| checkbox | checkboxValue |
| address | addressValue |
| owner_address | ownerAddressValue |
| customer_name | customerNameValue |
| customer_mobile | customerMobileValue |
| chained_selects | selectsValue |
| signature | signatureValue |
| image | imageValue |
| video | videoValue |
| audio | audioValue |
| file | fileValue |
| description | descriptionValue |


## 示例字段数据

:::code-group

```json [文本]
{
    "id": 1000,
    "groupId": 1000,
    "type": "text",
    "title": "姓名",
    "textValue": {
        "value": "张三"
    }
}
```

```json [性别]
{
    "id": 1001,
    "groupId": 1000,
    "type": "sex",
    "title": "性别",
    "sexValue": {
        "value": "男"
    }
}
```

```json [单选]
{
    "id": 1002,
    "groupId": 1000,
    "type": "radio",
    "title": "是否同意",
    "radioValue": {
        "value": "是"
    }
}
```


```json [车牌号]
{
    "id": 1007,
    "groupId": 1000,
    "type": "carnumber",
    "title": "车牌号",
    "carNumberValue": {
        "value": "京A12345"
    }
}
```

```json [检查项]
{
    "id": 1010,
    "groupId": 1000,
    "type": "checklist",
    "title": "检查清单",
    "checkListValue": {
        "checkValues": [
            {
                "optionId": 1,
                "title": "项目一",
                "value": "1"
            },
            {
                "optionId": 2,
                "title": "项目二",
                "value": "0"
            }
        ]
    }
}
```

```json [文件]
{
    "id": 1016,
    "groupId": 1000,
    "type": "file",
    "title": "文件上传",
    "fileValue": {
        "files": [
            {
                "url": "https://example.com/doc1.pdf",
                "title": "文档1.pdf"
            }
        ]
    }
}
```

```json [图像]
{
    "id": 1015,
    "groupId": 1000,
    "type": "image",
    "title": "图片上传",
    "imageValue": {
        "images": [
            {
                "url": "https://example.com/image1.jpg"
            },
            {
                "url": "https://example.com/image2.jpg"
            }
        ]
    }
}
```

```json [表格组件]
{
    "id": 1011,
    "groupId": 1000,
    "type": "matrix",
    "title": "表格",
    "matrixValue": {
        "matrixValues": [
            {
                "title": "第一行",
                "value": "值1"
            },
            {
                "title": "第二行",
                "value": "值2"
            }
        ]
    }
}
```



:::

## 字段详解

`id` integer

字段ID

---

`groupId` integer

字段组ID

---

`type` string

字段类型

type和使用的属性见 [type和使用的属性对照表](#type和使用的属性对照表)

---

`title` string

字段标题

---

### 填写人姓名

`nameValue` object

姓名字段, 当`type`为`name`时, 使用`nameValue`对象来存储字段值。

`nameValue.value` string

姓名字符串值

---

### 填写人手机号

`telValue` object

填表人手机号字段, 当`type`为`tel`时, 使用`telValue`对象来存储字段值。

`telValue.value` string

手机号字符串值

---

### 填写人微信名

`recorderValue` object

填表人微信名字段, 当`type`为`recorder`时, 使用`recorderValue`对象来存储字段值。

`recorderValue.value` string

填表人微信名字符串值

---

### 身份证号

`identityValue` object

填表人身份证号字段, 当`type`为`identity`时, 使用`identityValue`对象来存储字段值。

`identityValue.value` string

身份证号字符串值

---

### 工号

`jobNumberValue` object

工号字段, 当`type`为`job_number`时, 使用`jobNumberValue`对象来存储字段值。

`jobNumberValue.value` string

工号字符串值

---

### 车牌号

`carNumberValue` object

车牌号字段, 当`type`为`carnumber`时, 使用`carNumberValue`对象来存储字段值。

`carNumberValue.value` string

车牌号字符串值

---

### 性别

`sexValue` object

性别字段, 当`type`为`sex`时, 使用`sexValue`对象来存储字段值。

`sexValue.value` string

性别字符串值, 可能为`男`或`女`

---

### 文本

`textValue` object

文本字段, 当`type`为`text`时, 使用`textValue`对象来存储字段值。

`textValue.value` string

文本字符串值

---

### 多行文本

`textareaValue` object

多行文本字段, 当`type`为`textarea`时, 使用`textareaValue`对象来存储字段值。

`textareaValue.value` string

多行文本字符串值

---

### 数字

`numberValue` object

数字字段, 当`type`为`number`时, 使用`numberValue`对象来存储字段值。

`numberValue.value` number

数字的字符串值（带单位）

---

### 检查项

`checkListValue` object

检查项字段, 当`type`为`checklist`时, 使用`checkListValue`对象来存储字段值。

`checkListValue.checkValues` []object

检查项的值, 是一个对象数组, 每个对象的格式如下:

`checkListValue.checkValues[].optionId` integer

检查项的选项ID

`checkListValue.checkValues[].title` string

检查项的选项名称

`checkListValue.checkValues[].value` string

检查项是否被选中，可能的值为`"0"`未选中，`"1"`选中

---

### 表格组件

`matrixValue` object

表格组件字段, 当`type`为`matrix`时, 使用`matrixValue`对象来存储字段值。

`matrixValue.matrixValues` []object

表格组件的值, 是一个对象数组, 每个对象的格式如下:

`matrixValue.matrixValues[].title` string

标题

`matrixValue.matrixValues[].value` string

值

---

### 动态表格组件

`dynamicMatrixValue` object

动态表格组件字段, 当`type`为`dynamic_matrix`时, 使用`dynamicMatrixValue`对象来存储字段值。

`dynamicMatrixValue.dynamicMatrixValues` []object

动态表格组件的值, 是一个对象数组, 每个对象的格式如下:

`dynamicMatrixValue.dynamicMatrixValues[].title` string

标题

`dynamicMatrixValue.dynamicMatrixValues[].value` string

值

---

### 日期

`dateValue` object

日期字段, 当`type`为`date`时, 使用`dateValue`对象来存储字段值。

`dateValue.value` string

日期字符串值, 格式与表单字段设置一致

---

### 时间

`timeValue` object

时间字段, 当`type`为`time`时, 使用`timeValue`对象来存储字段值。

`timeValue.value` string

时间字符串值, 格式与表单字段设置一致

---

### 单选

`radioValue` object

单选字段, 当`type`为`radio`时, 使用`radioValue`对象来存储字段值。

`radioValue.value` string

选项的值

---

### 多选

`checkboxValue` object

多选字段, 当`type`为`checkbox`时, 使用`checkboxValue`对象来存储字段值。

`checkboxValue.values` []string

多选的值, 是一个字符串数组

---

### 定位组件

`addressValue` object

定位组件字段, 当`type`为`address`时, 使用`addressValue`对象来存储字段值。

`addressValue.value` string

定位字符串值

---

### 地址组件

`ownerAddressValue` object

地址组件字段, 当`type`为`owner_address`时, 使用`ownerAddressValue`对象来存储字段值。

`ownerAddressValue.value` string

地址字符串值

---

### 姓名

`customerNameValue` object

姓名字段, 当`type`为`customer_name`时, 使用`customerNameValue`对象来存储字段值。

`customerNameValue.value` string

姓名字符串值

### 手机号

`customerMobileValue` object

手机号字段, 当`type`为`customer_mobile`时, 使用`customerMobileValue`对象来存储字段值。

`customerMobileValue.value` string

手机号字符串值

---

### 签名

`signatureValue` object

签名字段, 当`type`为`signature`时, 使用`signatureValue`对象来存储字段值。

---

### 图像

`imageValue` object

图像字段, 当`type`为`image`时, 使用`imageValue`对象来存储字段值。

`imageValue.images` []object

图像列表

`imageValue.images[].url` string

图像的URL

---

### 文件

`fileValue` object

文件字段, 当`type`为`file`时, 使用`fileValue`对象来存储字段值。

`fileValue.files` []object

文件列表

`fileValue.files[].url` string

文件的URL

`fileValue.files[].title` string

文件的名称

---

### 音频

`audioValue` object

音频字段, 当`type`为`audio`时, 使用`audioValue`对象来存储字段值。

`audioValue.audios` []object

音频对象

`audioValue.audios[].url` string

音频的URL

`audioValue.audios[].title` string

音频的名称

---

### 视频

`videoValue` object

视频字段, 当`type`为`video`时, 使用`videoValue`对象来存储字段值。

`videoValue.videos` []object

视频列表

`videoValue.videos[].url` string

视频的URL

`videoValue.videos[].title` string

视频的名称

```json [文件]
{
    "id": 1016,
    "groupId": 1000,
    "type": "file",
    "title": "文件上传",
    "fileValue": {
        "files": [
            {
                "url": "https://example.com/doc1.pdf",
                "title": "文档1.pdf"
            }
        ]
    }
}
```
