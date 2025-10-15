# Retrieve Forms Data

This API allows users to obtain forms data lists based on QR code URL, form ID, and time parameters.

## Request Example

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
    'Authorization': 'Bearer <YourAPIKey>' // Replace with your API Key, e.g. 'Bearer abc123456'
}

response = requests.post(url, json=data)
print(response.text)

```

```yaml [OpenAPI V3 Schema]
openapi: 3.1.0
info:
  title: QR Code Scanning
  version: 1.0.0
  description: Parse content from QR codes
servers:
  - url: https://open.cli.im/api/v1
paths:
  /form/get_data:
    post:
      summary: Retrieve Forms Data
      description: Get forms data list based on QR code URL, form ID, and time range
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
                  description: QR code URL
                  example: 'https://qr61.cn/xxx/yyy'
                formSerialNumber:
                  type: string
                  description: Form serial number
                  example: 'D101'
                startTime:
                  type: string
                  description: Start time
                  format: date-time
                  example: '2025-01-01 00:00:00'
                endTime:
                  type: string
                  description: End time
                  format: date-time
                  example: '2025-01-31 00:00:00'
                pageToken:
                  type: string
                  description: Pagination token
                  example: 'd29ybGQ='
              required:
                - qrCodeUrl
                - formSerialNumber
      responses:
        '200':
          description: Successfully retrieved forms data
          content:
            application/json:
              schema:
                type: object
                properties:
                  code:
                    type: integer
                    description: Status code (0 for success, others for failure)
                  message:
                    type: string
                    description: Status message (empty for success, error message for failure)
                  data:
                    type: object
                    properties:
                      total:
                        type: integer
                        description: Total data count
                      list:
                        type: array
                        description: Data list
                        items:
                          type: object
                          properties:
                            serialNumber:
                              type: string
                              description: Data serial number
                            qrCodeCoding:
                              type: string
                              description: QR code coding
                            formSerialNumber:
                              type: string
                              description: Form serial number
                            addTime:
                              type: string
                              description: Creation time
                              format: date-time
                            recorder:
                              type: string
                              description: Form submitter
                            fields:
                              type: array
                              description: Form fields list
                              items:
                                $ref: '#/components/schemas/FormField'
                      nextPageToken:
                        type: string
                        description: Pagination token for next page

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
          description: Field ID
        groupId:
          type: integer
          description: Field group ID
        type:
          type: string
          description: Field type
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
          description: Field title
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

    # Submitter name
    NameValue:
      type: object
      properties:
        value:
          type: string
          description: Name string value

    # Submitter phone number
    TelValue:
      type: object
      properties:
        value:
          type: string
          description: Phone number string value

    # Submitter WeChat name
    RecorderValue:
      type: object
      properties:
        value:
          type: string
          description: Submitter WeChat name string value

    # ID number
    IdentityValue:
      type: object
      properties:
        value:
          type: string
          description: ID number string value

    # Employee ID
    JobNumberValue:
      type: object
      properties:
        value:
          type: string
          description: Employee ID string value

    # License plate number
    CarNumberValue:
      type: object
      properties:
        value:
          type: string
          description: License plate number string value

    # Gender
    SexValue:
      type: object
      properties:
        value:
          type: string
          description: Gender string value
          enum: ['Male', 'Female']

    # Text
    TextValue:
      type: object
      properties:
        value:
          type: string
          description: Text string value

    # Multiline text
    TextareaValue:
      type: object
      properties:
        value:
          type: string
          description: Multiline text string value

    # Number
    NumberValue:
      type: object
      properties:
        value:
          type: string
          description: Number string value (with unit)

    # Checklist
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
                description: Checklist option ID
              title:
                type: string
                description: Checklist option name
              value:
                type: string
                description: Whether the option is selected
                enum: ['0', '1']

    # Table component
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
                description: Title
              value:
                type: string
                description: Value

    # Dynamic table component
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
                description: Title
              value:
                type: string
                description: Value

    # Date
    DateValue:
      type: object
      properties:
        value:
          type: string
          description: Date string value

    # Time
    TimeValue:
      type: object
      properties:
        value:
          type: string
          description: Time string value

    # Radio button
    RadioValue:
      type: object
      properties:
        value:
          type: string
          description: Selected option value

    # Checkbox
    CheckboxValue:
      type: object
      properties:
        values:
          type: array
          items:
            type: string
          description: Array of selected values

    # Location component
    AddressValue:
      type: object
      properties:
        value:
          type: string
          description: Location string value

    # Address component
    OwnerAddressValue:
      type: object
      properties:
        value:
          type: string
          description: Address string value

    # Customer name
    CustomerNameValue:
      type: object
      properties:
        value:
          type: string
          description: Name string value

    # Customer phone number
    CustomerMobileValue:
      type: object
      properties:
        value:
          type: string
          description: Phone number string value

    # Signature
    SignatureValue:
      type: object
      description: Signature field value

    # Image
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
                description: Image URL

    # Video
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
                description: Video URL
              title:
                type: string
                description: Video name

    # Audio
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
                description: Audio URL
              title:
                type: string
                description: Audio name

    # File
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
                description: File URL
              title:
                type: string
                description: File name 
```

:::

### Response Example

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
        "recorder": "Zhang San",
        "fields": [
          {
            "id": 1000,
            "groupId": 1000,
            "type": "text",
            "title": "Name",
            "text": {
              "value": "Zhang San"
            }
          },
          {
            "id": 1001,
            "groupId": 1000,
            "type": "sex",
            "title": "Gender",
            "sex": {
              "value": "Male"
            }
          }
        ]
      }
    ],
    "nextPageToken": "z38cd8gQ="
  }
}
```

### Request Details

`qrCodeUrl` string *Required*

QR code URL

---

`formSerialNumber` string *Required*

Form serial number

---

`startTime` string *Optional*

Start time, formatted as `2025-01-01 00:00:00`

---

`endTime` string *Optional*

End time, formatted as `2025-01-01 00:00:00`

---

`pageToken` string *Optional*

Pagination token. Use the pageToken from the previous response to retrieve the next page of data.

---

### Response Details

`code` integer

Status code (0 for success, others for failure)

---

`message` string

Status message ("ok" for success, error message for failure)

---

`data` object

Response data

---

`data.total` integer

Total data count

--- 

`data.list` []object

Data list

---

`data.list[].serialNumber` string

Data serial number

---

`data.list[].qrCodeCoding` string

QR code coding

---

`data.list[].formSerialNumber` string

Form serial number

---

`data.list[].addTime` string

Creation time

---

`data.list[].recorder` string

Form submitter

---

`data.list[].fields` []FormField

Form fields

The form fields list is an array of FormField objects. Refer to [FormField Schema](./en/openapi/api/forms/form-field-schema.md) for field definitions.

---