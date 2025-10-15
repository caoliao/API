# 模版子码组件(创建子码)

以下内容描述创建子码接口时子码组件数据的上送定义。

## 示例组件数据

:::code-group

```json [文本]
{
    "fieldId": 1,
    "type": "text",
    "text": {
        "value": "Hello World"
    }
}
```

```json [多行文本]
{
    "fieldId": 2,
    "type": "textarea",
    "textarea": {
        "value": "Hello World\nHello World"
    }
}
```

```json [数字]
{
    "fieldId": 3,
    "type": "number",
    "number": {
        "value": 123
    }
}
```

```json [日期]
{
    "fieldId": 4,
    "type": "date",
    "date": {
        "value": "2025-03-04"
    }
}
```

```json [单选项]
{
    "fieldId": 5,
    "type": "radio",
    "radio": {
        "value": "选项1"
    }
}
```

```json [多选项]
{
    "fieldId": 6,
    "type": "checkbox",
    "checkbox": {
        "value": ["选项1", "选项2"]
    }
}
```

```json [定位]
{
    "fieldId": 7,
    "type": "address",
    "address": {
        "address": "浙江省宁波市海曙区灵桥路",
        "lat": 29.85957,
        "log": 121.55084
    }
}
```

```json [图片]
{
    "fieldId": 8,
    "type": "image",
    "image": {
        "url": "https://ncstatic.clewm.net/undefined.png"
    }
}
```

```json [音频]
{
    "fieldId": 9,
    "type": "audio",
    "audio": {
        "title": "音频标题",
        "url": "https://ncstatic.clewm.net/undefined.mp3"
    }
}
```

:::

## 组件详情

`fieldId` number

组件ID，取自获取模版详情接口返回的组件ID

--- 

`title` string

组件标题

--- 

`type` string

组件类型

| 值       | 说明   |
|----------|--------|
| text     | 文本   |
| textarea | 多行文本 |
| number   | 数字   |
| date     | 日期   |
| radio    | 单选项 |
| checkbox | 多选项 |
| address  | 定位   |
| image    | 图片   |
| file     | 文件   |

当type使用"text"时, 上送组件内容为文本, 文本内容使用`text`字段。当type使用"image"时, 上送组件内容为图片, 图片内容使用`image`字段。以此类推。目前暂不支持视频与音频组件进行子码创建。

--- 

### 文本组件

`text` object

当内容是文本组件时上送

`text.value` string

文本内容

---

### 多行文本组件

`textarea` object

当内容是多行文本组件时上送

`textarea.value` string

多行文本内容

---

### 数字组件

`number` object

当内容是数字组件时上送

`number.value` number

数字内容

---

### 日期组件

`date` object

当内容是日期组件时上送

`date.value` string

日期内容

---

### 单选项组件

`radio` object

当内容是单选项组件时上送

`radio.optionId` number

单选项id，取自查询模版接口返回的单选项组件id

`radio.otherValue` string

其他选项内容，如果该选项是其他选项，则上送其他选项内容, 否则无需上送

---

### 多选项组件

`checkbox` object

当内容是多选项组件时上送

`checkbox.optionCreateDataList` []object

多选项列表

`checkbox.optionCreateDataList[].optionId` number

多选项id，取自查询模版接口返回的多选项组件id

`checkbox.optionCreateDataList[].otherValue` string

其他选项内容，如果该选项是其他选项，则上送其他选项内容, 否则无需上送

---

### 定位组件

`address` object

当内容是定位组件时上送

`address.address` string

地址

`address.lat` number

纬度

`address.log` number

经度

---

### 图片组件

`image` object

当内容是图片组件时上送

`image.images` []object

图片内容

`image.images[].url` string

图片URL

---

### 文件组件

`file` object

当内容是文件组件时上送

`file.files` []object

文件内容

`file.files[].url` string

文件URL

`file.files[].title` string

文件名称