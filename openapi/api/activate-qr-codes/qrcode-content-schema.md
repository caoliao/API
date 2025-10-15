# 二维码富文本模块(ContentModule)

以下内容描述活码富文本内容模块的定义。

## 示例模块数据

:::code-group

```json [文本]
{
    "type": "text",
    "text": {
        "value": "Hello World"
    }
}
```

```json [图片]
{
    "type": "image",
    "image": {
        "items": [
            {
                "url": "https://ncstatic.clewm.net/undefined.png"
            }
        ]
    }
}
```

```json [音频]
{
    "type": "audio",
    "audio": {
        "url": "https://ncstatic.clewm.net/undefined.mp3"
    }
}
```

```json [视频]
{
    "type": "video",
    "video": {
        "url": "https://ncstatic.clewm.net/undefined.mp4",
        "title": "视频标题",
        "coverUrl": "https://ncstatic.clewm.net/undefined.png"
    }
}
```

```json [联系方式]
{
    "type": "contact",
    "contact": {
        "wechatName": "微信名称",
        "phone": "电话",
        "email": "邮箱",
        "address": "地址",
        "workTime": "工作时间"
    }
}
```

```json [文件]
{
    "type": "file",
    "file": {
        "title": "文件标题",
        "url": "https://ncstatic.clewm.net/undefined.pdf"
    }
}

:::

## 模块详情

`type` string

模块类型

| 值       | 说明   |
|----------|--------|
| text     | 文本   |
| image    | 图片   |
| audio    | 音频   |
| video    | 视频   |
| contact  | 联系方式 |
| file     | 文件   |

当type使用"text"时, 模块内容为文本, 文本内容使用`text`字段。当type使用"image"时, 模块内容为图片, 图片内容使用`image`字段。以此类推。

--- 

### 文本模块

`text` object

当内容是文本模块时使用

`text.value` string

文本内容

---

### 图片模块

`image` object

当内容是图片模块时使用

`image.items` []object

图片内容

`image.items[].url` string

图片URL

---

### 音频模块

`audio` object

音频内容

`audio.url` string

音频URL

`audio.title` string

音频名称

---

### 视频模块

`video` object

视频内容

`video.url` string

视频URL

`video.title` string

视频标题

`video.coverUrl` string

视频封面

---

### 联系方式模块

`contact` object

联系方式

`contact.wechatName` string

微信名称

`contact.phone` string

电话

`contact.email` string

邮箱

`contact.address` string

地址

`contact.workTime` string

工作时间

---

### 文件模块

`file` object

文件内容

`file.title` string

文件名

`file.url` string

文件URL

