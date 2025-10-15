# 获取表单数据

通过此API，用户可以根据二维码URL、表单ID和时间来获取表单数据列表。

## 请求示例

::: code-group

```python [Python + requests]
import requests
import json

url = 'https://open.cli.im/api/v1/form/get_data'

data = {
    'qrCodeUrl': 'https://qr61.cn/xxx/yyy',
    'formSerialNumber': 'D101'
}

headers = {
    'Authorization': 'Bearer <你的APIKey>' // 请替换为你的API Key, 例如'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)

```

```yaml [OpenAPI V3 Schema]
openapi: 3.1.0
info:
  title: 扫描二维码
  version: 1.0.0
  description: 解析二维码中的内容
servers:
  - url: https://open.cli.im/api/v1
paths:
  /form/get_data:
    post:
      summary: 获取表单数据
      description: 根据二维码URL、表单ID和时间范围获取表单数据列表
      security:
        - BearerAuth: []
      requestBody:
        required: true
        content:
          application/json:
            schema:
              type: object
              properties:
                qrCodeUrl:
                  type: string
                  description: 二维码URL
                  example: 'https://qr61.cn/xxx/yyy'
                formSerialNumber:
                  type: string
                  description: 表单编号
                  example: 'D101'
                startTime:
                  type: string
                  description: 开始时间
                  format: date-time
                  example: '2025-01-01 00:00:00'
                endTime:
                  type: string
                  description: 结束时间
                  format: date-time
                  example: '2025-01-31 00:00:00'
                pageToken:
                  type: string
                  description: 分页标记
                  example: 'd29ybGQ='
              required:
                - qrCodeUrl
                - formSerialNumber
      responses:
        '200':
          description: 成功获取表单数据
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: 状态码，0表示成功，其他表示失败
                  message:
                    type: string
                    description: 状态消息，成功时为空，失败时为错误消息
                  data:
                    type: object
                    properties:
                      total:
                        type: integer
                        description: 数据总数
                      list:
                        type: array
                        description: 数据列表
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: 数据编号
                            qrCodeCoding:
                              type: string
                              description: 二维码Coding
                            formSerialNumber:
                              type: string
                              description: 表单编号
                            addTime:
                              type: string
                              description: 添加时间
                              format: date-time
                            recorder:
                              type: string
                              description: 表单填写人
                            fields:
                              type: array
                              description: 表单字段列表
                              items:
                                $ref: '#/components/schemas/FormField'
                      nextPageToken:
                        type: string
                        description: 下一页的分页标记

components:
  securitySchemes:
    BearerAuth:
      type: http
      scheme: bearer
      bearerFormat: JWT
  
  schemas:
    FormField:
      type: object
      properties:
        id:
          type: integer
          description: 字段ID
        groupId:
          type: integer
          description: 字段组ID
        type:
          type: string
          description: 字段类型
          enum: [
            'name', 'tel', 'recorder', 'identity', 'job_number', 
            'carnumber', 'sex', 'text', 'textarea', 'number', 
            'checklist', 'matrix', 'dynamic_matrix', 'date', 'time',
            'radio', 'checkbox', 'address', 'owner_address', 
            'customer_name', 'customer_mobile', 'chained_selects',
            'signature', 'image', 'video', 'audio', 'file', 'description'
          ]
        title:
          type: string
          description: 字段标题
        nameValue:
          $ref: '#/components/schemas/NameValue'
        telValue:
          $ref: '#/components/schemas/TelValue'
        recorderValue:
          $ref: '#/components/schemas/RecorderValue'
        identityValue:
          $ref: '#/components/schemas/IdentityValue'
        jobNumberValue:
          $ref: '#/components/schemas/JobNumberValue'
        carNumberValue:
          $ref: '#/components/schemas/CarNumberValue'
        sexValue:
          $ref: '#/components/schemas/SexValue'
        textValue:
          $ref: '#/components/schemas/TextValue'
        textareaValue:
          $ref: '#/components/schemas/TextareaValue'
        numberValue:
          $ref: '#/components/schemas/NumberValue'
        checkListValue:
          $ref: '#/components/schemas/CheckListValue'
        matrixValue:
          $ref: '#/components/schemas/MatrixValue'
        dynamicMatrixValue:
          $ref: '#/components/schemas/DynamicMatrixValue'
        dateValue:
          $ref: '#/components/schemas/DateValue'
        timeValue:
          $ref: '#/components/schemas/TimeValue'
        radioValue:
          $ref: '#/components/schemas/RadioValue'
        checkboxValue:
          $ref: '#/components/schemas/CheckboxValue'
        addressValue:
          $ref: '#/components/schemas/AddressValue'
        ownerAddressValue:
          $ref: '#/components/schemas/OwnerAddressValue'
        customerNameValue:
          $ref: '#/components/schemas/CustomerNameValue'
        customerMobileValue:
          $ref: '#/components/schemas/CustomerMobileValue'
        signatureValue:
          $ref: '#/components/schemas/SignatureValue'
        imageValue:
          $ref: '#/components/schemas/ImageValue'
        videoValue:
          $ref: '#/components/schemas/VideoValue'
        audioValue:
          $ref: '#/components/schemas/AudioValue'
        fileValue:
          $ref: '#/components/schemas/FileValue'

    # 填写人姓名
    NameValue:
      type: object
      properties:
        value:
          type: string
          description: 姓名字符串值

    # 填写人手机号
    TelValue:
      type: object
      properties:
        value:
          type: string
          description: 手机号字符串值

    # 填写人微信名
    RecorderValue:
      type: object
      properties:
        value:
          type: string
          description: 填表人微信名字符串值

    # 身份证号
    IdentityValue:
      type: object
      properties:
        value:
          type: string
          description: 身份证号字符串值

    # 工号
    JobNumberValue:
      type: object
      properties:
        value:
          type: string
          description: 工号字符串值

    # 车牌号
    CarNumberValue:
      type: object
      properties:
        value:
          type: string
          description: 车牌号字符串值

    # 性别
    SexValue:
      type: object
      properties:
        value:
          type: string
          description: 性别字符串值
          enum: ['男', '女']

    # 文本
    TextValue:
      type: object
      properties:
        value:
          type: string
          description: 文本字符串值

    # 多行文本
    TextareaValue:
      type: object
      properties:
        value:
          type: string
          description: 多行文本字符串值

    # 数字
    NumberValue:
      type: object
      properties:
        value:
          type: string
          description: 数字的字符串值（带单位）

    # 检查项
    CheckListValue:
      type: object
      properties:
        checkValues:
          type: array
          items:
            type: object
            properties:
              optionId:
                type: integer
                description: 检查项的选项ID
              title:
                type: string
                description: 检查项的选项名称
              value:
                type: string
                description: 检查项是否被选中
                enum: ['0', '1']

    # 表格组件
    MatrixValue:
      type: object
      properties:
        matrixValues:
          type: array
          items:
            type: object
            properties:
              title:
                type: string
                description: 标题
              value:
                type: string
                description: 值

    # 动态表格组件
    DynamicMatrixValue:
      type: object
      properties:
        dynamicMatrixValues:
          type: array
          items:
            type: object
            properties:
              title:
                type: string
                description: 标题
              value:
                type: string
                description: 值

    # 日期
    DateValue:
      type: object
      properties:
        value:
          type: string
          description: 日期字符串值

    # 时间
    TimeValue:
      type: object
      properties:
        value:
          type: string
          description: 时间字符串值

    # 单选
    RadioValue:
      type: object
      properties:
        value:
          type: string
          description: 选项的值

    # 多选
    CheckboxValue:
      type: object
      properties:
        values:
          type: array
          items:
            type: string
          description: 多选的值数组

    # 定位组件
    AddressValue:
      type: object
      properties:
        value:
          type: string
          description: 定位字符串值

    # 地址组件
    OwnerAddressValue:
      type: object
      properties:
        value:
          type: string
          description: 地址字符串值

    # 客户姓名
    CustomerNameValue:
      type: object
      properties:
        value:
          type: string
          description: 姓名字符串值

    # 客户手机号
    CustomerMobileValue:
      type: object
      properties:
        value:
          type: string
          description: 手机号字符串值

    # 签名
    SignatureValue:
      type: object
      description: 签名字段值

    # 图像
    ImageValue:
      type: object
      properties:
        images:
          type: array
          items:
            type: object
            properties:
              url:
                type: string
                description: 图像的URL

    # 视频
    VideoValue:
      type: object
      properties:
        videos:
          type: array
          items:
            type: object
            properties:
              url:
                type: string
                description: 视频的URL
              title:
                type: string
                description: 视频的名称

    # 音频
    AudioValue:
      type: object
      properties:
        audios:
          type: array
          items:
            type: object
            properties:
              url:
                type: string
                description: 音频的URL
              title:
                type: string
                description: 音频的名称

    # 文件
    FileValue:
      type: object
      properties:
        files:
          type: array
          items:
            type: object
            properties:
              url:
                type: string
                description: 文件的URL
              title:
                type: string
                description: 文件的名称 
```

:::

### 响应示例

**body**

```json
{
  "code": 0,
  "message": "",
  "data": {
    "total": 100,
    "list": [
      {
        "serialNumber": "D1000",
        "qrCodeCoding": "yyy",
        "formSerialNumber": "L101",
        "addTime": "2025-01-01 00:00:00",
        "recorder": "张三",
        "fields": [
          {
            "id": 1000,
            "groupId": 1000,
            "type": "text",
            "title": "姓名",
            "text": {
              "value": "张三"
            }
          },
          {
            "id": 1001,
            "groupId": 1000,
            "type": "sex",
            "title": "性别",
            "sex": {
              "value": "男"
            }
          }
        ]
      }
    ],
    "nextPageToken": "z38cd8gQ="
  }
}
```

### 请求详情

`qrCodeUrl` string *必填*

二维码URL

---

`formSerialNumber` string *必填*

表单编号

---

`startTime` string **可选**

开始时间， 格式如 `2025-01-01 00:00:00`

---

`endTime` string **可选**

结束时间， 格式如 `2025-01-01 00:00:00`

---

`pageToken` string **可选**

分页Token,可以使用上一次请求响应的pageToken来获取下一页的数据。

---

### 响应详情

`code` integer

状态码, 0表示成功, 其他表示失败。

---

`message` string

状态消息, 成功时为"ok", 失败时为错误消息。

---

`data` object

响应的数据

---

`data.total` integer

数据总数

--- 

`data.list` []object

数据列表

---

`data.list[].serialNumber` string

数据编号

---

`data.list[].qrCodeCoding` string

二维码Coding

---

`data.list[].formSerialNumber` string

表单编号

---

`data.list[].addTime` string

添加时间

---

`data.list[].recorder` string

表单填写人

---

`data.list[].fields` []FormField

表单字段

表单的字段列表是一个FormField数组, 你可以通过 [表单字段FormField](./openapi/api/forms/form-field-schema.md) 了解表单字段的定义。

---

