# 模版子码组件(获取子码内容)

以下内容描述获取子码接口时模版子码组件的定义。

## 示例组件数据

:::code-group

```json [文本]
{
    "fieldId": 1,
    "type": "text",
    "title": "文本1",
    "text": {
        "value": "Hello World"
    }
}
```

```json [多行文本]
{
    "fieldId": 2,
    "type": "textarea",
    "title": "多行文本1",
    "textarea": {
        "value": "Hello World\nHello World"
    }
}
```

```json [数字]
{
    "fieldId": 3,
    "type": "number",
    "title": "数字1",
    "number": {
        "value": 123
    }
}
```

```json [日期]
{
    "fieldId": 4,
    "type": "date",
    "title": "日期1",
    "date": {
        "value": "2025-03-04"
    }
}
```

```json [单选项]
{
    "fieldId": 5,
    "type": "radio",
    "title": "单选项1",
    "radio": {
        "value": "选项1"
    }
}
```

```json [多选项]
{
    "fieldId": 6,
    "type": "checkbox",
    "title": "多选项1",
    "checkbox": {
        "value": ["选项1", "选项2"]
    }
}
```

```json [定位]
{
    "fieldId": 7,
    "type": "address",
    "title": "定位1",
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
    "title": "图片1",
    "image": {
        "url": "https://ncstatic.clewm.net/undefined.png"
    }
}
```

```json [音频]
{
    "fieldId": 9,
    "type": "audio",
    "title": "音频1",
    "audio": {
        "title": "音频标题",
        "url": "https://ncstatic.clewm.net/undefined.mp3"
    }
}
```

```json [视频]
{
    "fieldId": 10,
    "type": "video",
    "title": "视频1",
    "video": {
        "url": "https://ncstatic.clewm.net/undefined.mp4"
    }
}
```

```json [文件]
{
    "fieldId": 11,
    "type": "file",
    "title": "文件1",
    "file": {
        "title": "文件标题",
        "url": "https://ncstatic.clewm.net/undefined.pdf",
        "size": 123456
    }
}

:::

## 组件详情

`fieldId` number

组件ID

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
| audio    | 音频   |
| video    | 视频   |
| file     | 文件   |

当type使用"text"时, 组件内容为文本, 文本内容使用`text`字段。当type使用"image"时, 组件内容为图片, 图片内容使用`image`字段。以此类推。

--- 

### 文本组件

`text` object

当内容是文本组件时使用

`text.value` string

文本内容

---

### 多行文本组件

`textarea` object

当内容是多行文本组件时使用

`textarea.value` string

多行文本内容

---

### 数字组件

`number` object

当内容是数字组件时使用

`number.value` number

数字内容

---

### 日期组件

`date` object

当内容是日期组件时使用

`date.value` string

日期内容

---

### 单选项组件

`radio` object

当内容是单选项组件时使用

`radio.value` string

单选项内容

---

### 多选项组件

`checkbox` object

当内容是多选项组件时使用

`checkbox.value` []string

多选项内容

---

### 定位组件

`address` object

当内容是定位组件时使用

`address.address` string

地址

`address.lat` number

纬度

`address.log` number

经度

---

### 图片组件

`image` object

当内容是图片组件时使用

`image.images` []object

图片内容

`image.images[].url` string

图片URL

---

### 音频组件

`audio` object

当内容是音频组件时使用

`audio.audios` []object

音频内容

`audio.audios[].url` string

音频URL

`audio.audios[].title` string

音频名称

---

### 视频组件

`video` object

当内容是视频组件时使用

`video.videos` []object

视频内容

`video.videos[].url` string

视频URL

---

### 文件组件

`file` object

当内容是文件组件时使用

`file.files` []object

文件内容

`file.files[].url` string

文件URL

`file.files[].title` string

文件名称

`file.files[].size` number

文件大小