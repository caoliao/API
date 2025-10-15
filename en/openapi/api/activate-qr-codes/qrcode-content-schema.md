# QR Code Rich Text Modules (ContentModule)

The following describes the definition of dynamic QR code rich text content modules.

## Sample Module Data

:::code-group

```json [Text]
{
    "type": "text",
    "text": {
        "value": "Hello World"
    }
}
```

```json [Image]
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

```json [Audio]
{
    "type": "audio",
    "audio": {
        "url": "https://ncstatic.clewm.net/undefined.mp3"
    }
}
```

```json [Video]
{
    "type": "video",
    "video": {
        "url": "https://ncstatic.clewm.net/undefined.mp4",
        "title": "Video Title",
        "coverUrl": "https://ncstatic.clewm.net/undefined.png"
    }
}
```

```json [Contact]
{
    "type": "contact",
    "contact": {
        "wechatName": "WeChat Name",
        "phone": "Phone",
        "email": "Email",
        "address": "Address",
        "workTime": "Working Hours"
    }
}
```

```json [File]
{
    "type": "file",
    "file": {
        "title": "File Title",
        "url": "https://ncstatic.clewm.net/undefined.pdf"
    }
}

:::

## Module Details

`type` string

Module type

| Value    | Description   |
|----------|--------------|
| text     | Text         |
| image    | Image        |
| audio    | Audio        |
| video    | Video        |
| contact  | Contact      |
| file     | File         |

When the type is "text", the module content is text, and the text content uses the `text` field. When the type is "image", the module content is an image, and the image content uses the `image` field. And so on.

--- 

### Text Module

`text` object

Used when the content is a text module.

`text.value` string

Text content

---

### Image Module

`image` object

Used when the content is an image module.

`image.items` []object

Image content

`image.items[].url` string

Image URL

---

### Audio Module

`audio` object

Audio content

`audio.url` string

Audio URL

`audio.title` string

Audio name

---

### Video Module

`video` object

Video content

`video.url` string

Video URL

`video.title` string

Video title

`video.coverUrl` string

Video cover

---

### Contact Module

`contact` object

Contact information

`contact.wechatName` string

WeChat name

`contact.phone` string

Phone

`contact.email` string

Email

`contact.address` string

Address

`contact.workTime` string

Working hours

---

### File Module

`file` object

File content

`file.title` string

File name

`file.url` string

File URL