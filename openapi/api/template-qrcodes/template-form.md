# 模版组件

以下内容描述获取模版组件接口时模版组件的定义。

## 示例组件数据

:::code-group

```json [文本、多行文本、定位、图片、文件、音频、视频]
{
    "fieldId": 1,
    "type": "text",
    "title": "文本1"
}
```

```json [数字]
{
    "fieldId": 2,
    "type": "number",
    "title": "数字1",
    "numberField": {
        "unit": "元"
    }
}
```

```json [日期]
{
    "fieldId": 3,
    "type": "date",
    "title": "日期1",
    "dateField": {
        "dateFormat": "yyyy/MM/dd"
    }
}
```

```json [单选项]
{
    "fieldId": 4,
    "type": "radio",
    "title": "单选项1",
    "radioField": {
        "optionFields": [
            {
                "optionId": 1317735,
                "optionValue": "选项1",
                "isOtherOption": 0
            },
            {
                "optionId": 5074778,
                "optionValue": "其他",
                "isOtherOption": 1
            }
        ]
    }
}
```

```json [多选项]
{
    "fieldId": 5,
    "type": "checkbox",
    "title": "多选项1",
    "checkboxField": {
        "optionFields": [
            {
                "optionId": 1317744,
                "optionValue": "选项1",
                "isOtherOption": 0
            },
            {
                "optionId": 5074779,
                "optionValue": "其他",
                "isOtherOption": 1
            }
        ]
    }
}
```

:::

## 组件详情

`fieldId` number

组件ID，返回组件ID主要是为了创建子码时进行上送。

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

当type为"text"，"textarea"，"address"，"image"，"audio"，"video"，"file"时，无需返回任何组件内容，只返回组件ID和组件名称。当type为"number"，"date"，"radio"，"checkbox"时，额外返回对应的组件内容。

--- 

### 四种特殊组件（数字、日期、单选项、多选项）

#### 数字组件

`numberField` object

当类型是数字组件时返回

`numberField.unit` string

单位

---

#### 日期组件

`dateField` object

当类型是日期组件时返回

`dateField.dateFormat` string

日期格式

---

#### 单选项组件

`radioField` object

当类型是单选项组件时返回

`radioField.optionFields` []object

选项内容

`radioField.optionFields[].optionId` number

选项ID

`radioField.optionFields[].optionValue` string

选项值

`radioField.optionFields[].isOtherOption` number

是否是其他选项，0-不是其他选项，1-是其他选项

---

#### 多选项组件

`checkboxField` object

当类型是多选项组件时返回

`checkboxField.optionFields` []object

选项内容

`checkboxField.optionFields[].optionId` number

选项ID

`checkboxField.optionFields[].optionValue` string

选项值

`checkboxField.optionFields[].isOtherOption` number

是否是其他选项，0-不是其他选项，1-是其他选项
