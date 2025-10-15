```markdown
---
head:
  - - meta
    - name: description
      content: Learn about the definition and usage of form fields in CaoLiao QR codes, including attribute comparison tables for different field types, sample data, and detailed field explanations to help users quickly master form field applications.
  - - meta
    - name: keywords
      content: form fields, field types, attribute comparison table, sample data, field details, form design, data collection, CaoLiao QR code
---
# Form Fields (FormField)

This document describes the definition of form fields.

Form fields are distinguished by their `type`. Different `type` values use different objects to store field values.

## Field Type and Attribute Comparison Table

| type | Attribute Used |
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

## Sample Field Data

:::code-group

```json [Text]
{
    "id": 1000,
    "groupId": 1000,
    "type": "text",
    "title": "Name",
    "textValue": {
        "value": "Zhang San"
    }
}
```

```json [Gender]
{
    "id": 1001,
    "groupId": 1000,
    "type": "sex",
    "title": "Gender",
    "sexValue": {
        "value": "Male"
    }
}
```

```json [Single Choice]
{
    "id": 1002,
    "groupId": 1000,
    "type": "radio",
    "title": "Agreement",
    "radioValue": {
        "value": "Yes"
    }
}
```

```json [License Plate]
{
    "id": 1007,
    "groupId": 1000,
    "type": "carnumber",
    "title": "License Plate",
    "carNumberValue": {
        "value": "京A12345"
    }
}
```

```json [Checklist]
{
    "id": 1010,
    "groupId": 1000,
    "type": "checklist",
    "title": "Checklist",
    "checkListValue": {
        "checkValues": [
            {
                "optionId": 1,
                "title": "Item 1",
                "value": "1"
            },
            {
                "optionId": 2,
                "title": "Item 2",
                "value": "0"
            }
        ]
    }
}
```

```json [File]
{
    "id": 1016,
    "groupId": 1000,
    "type": "file",
    "title": "File Upload",
    "fileValue": {
        "files": [
            {
                "url": "https://example.com/doc1.pdf",
                "title": "Document1.pdf"
            }
        ]
    }
}
```

```json [Image]
{
    "id": 1015,
    "groupId": 1000,
    "type": "image",
    "title": "Image Upload",
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

```json [Table Component]
{
    "id": 1011,
    "groupId": 1000,
    "type": "matrix",
    "title": "Table",
    "matrixValue": {
        "matrixValues": [
            {
                "title": "First Row",
                "value": "Value 1"
            },
            {
                "title": "Second Row",
                "value": "Value 2"
            }
        ]
    }
}
```

:::

## Field Details

`id` integer

Field ID

---

`groupId` integer

Field group ID

---

`type` string

Field type

Refer to the [Field Type and Attribute Comparison Table](#field-type-and-attribute-comparison-table) for `type` and corresponding attributes.

---

`title` string

Field title

---

### Submitter Name

`nameValue` object

Name field. When `type` is `name`, the `nameValue` object is used to store the field value.

`nameValue.value` string

Name string value

---

### Submitter Phone Number

`telValue` object

Submitter phone number field. When `type` is `tel`, the `telValue` object is used to store the field value.

`telValue.value` string

Phone number string value

---

### Submitter WeChat Name

`recorderValue` object

Submitter WeChat name field. When `type` is `recorder`, the `recorderValue` object is used to store the field value.

`recorderValue.value` string

Submitter WeChat name string value

---

### ID Number

`identityValue` object

Submitter ID number field. When `type` is `identity`, the `identityValue` object is used to store the field value.

`identityValue.value` string

ID number string value

---

### Employee ID

`jobNumberValue` object

Employee ID field. When `type` is `job_number`, the `jobNumberValue` object is used to store the field value.

`jobNumberValue.value` string

Employee ID string value

---

### License Plate Number

`carNumberValue` object

License plate number field. When `type` is `carnumber`, the `carNumberValue` object is used to store the field value.

`carNumberValue.value` string

License plate number string value

---

### Gender

`sexValue` object

Gender field. When `type` is `sex`, the `sexValue` object is used to store the field value.

`sexValue.value` string

Gender string value, either `Male` or `Female`

---

### Text

`textValue` object

Text field. When `type` is `text`, the `textValue` object is used to store the field value.

`textValue.value` string

Text string value

---

### Multiline Text

`textareaValue` object

Multiline text field. When `type` is `textarea`, the `textareaValue` object is used to store the field value.

`textareaValue.value` string

Multiline text string value

---

### Number

`numberValue` object

Number field. When `type` is `number`, the `numberValue` object is used to store the field value.

`numberValue.value` number

Number string value (with unit)

---

### Checklist

`checkListValue` object

Checklist field. When `type` is `checklist`, the `checkListValue` object is used to store the field value.

`checkListValue.checkValues` []object

Checklist values, an array of objects with the following format:

`checkListValue.checkValues[].optionId` integer

Checklist option ID

`checkListValue.checkValues[].title` string

Checklist option name

`checkListValue.checkValues[].value` string

Whether the option is selected: `"0"` for unselected, `"1"` for selected

---

### Table Component

`matrixValue` object

Table component field. When `type` is `matrix`, the `matrixValue` object is used to store the field value.

`matrixValue.matrixValues` []object

Table component values, an array of objects with the following format:

`matrixValue.matrixValues[].title` string

Title

`matrixValue.matrixValues[].value` string

Value

---

### Dynamic Table Component

`dynamicMatrixValue` object

Dynamic table component field. When `type` is `dynamic_matrix`, the `dynamicMatrixValue` object is used to store the field value.

`dynamicMatrixValue.dynamicMatrixValues` []object

Dynamic table component values, an array of objects with the following format:

`dynamicMatrixValue.dynamicMatrixValues[].title` string

Title

`dynamicMatrixValue.dynamicMatrixValues[].value` string

Value

---

### Date

`dateValue` object

Date field. When `type` is `date`, the `dateValue` object is used to store the field value.

`dateValue.value` string

Date string value, formatted according to form field settings

---

### Time

`timeValue` object

Time field. When `type` is `time`, the `timeValue` object is used to store the field value.

`timeValue.value` string

Time string value, formatted according to form field settings

---

### Single Choice

`radioValue` object

Single-choice field. When `type` is `radio`, the `radioValue` object is used to store the field value.

`radioValue.value` string

Selected option value

---

### Multiple Choice

`checkboxValue` object

Multiple-choice field. When `type` is `checkbox`, the `checkboxValue` object is used to store the field value.

`checkboxValue.values` []string

Selected option values, an array of strings

---

### Location Component

`addressValue` object

Location component field. When `type` is `address`, the `addressValue` object is used to store the field value.

`addressValue.value` string

Location string value

---

### Address Component

`ownerAddressValue` object

Address component field. When `type` is `owner_address`, the `ownerAddressValue` object is used to store the field value.

`ownerAddressValue.value` string

Address string value

---

### Name

`customerNameValue` object

Name field. When `type` is `customer_name`, the `customerNameValue` object is used to store the field value.

`customerNameValue.value` string

Name string value

---

### Phone Number

`customerMobileValue` object

Phone number field. When `type` is `customer_mobile`, the `customerMobileValue` object is used to store the field value.

`customerMobileValue.value` string

Phone number string value

---

### Signature

`signatureValue` object

Signature field. When `type` is `signature`, the `signatureValue` object is used to store the field value.

---

### Image

`imageValue` object

Image field. When `type` is `image`, the `imageValue` object is used to store the field value.

`imageValue.images` []object

Image list

`imageValue.images[].url` string

Image URL

---

### File

`fileValue` object

File field. When `type` is `file`, the `fileValue` object is used to store the field value.

`fileValue.files` []object

File list

`fileValue.files[].url` string

File URL

`fileValue.files[].title` string

File name

---

### Audio

`audioValue` object

Audio field. When `type` is `audio`, the `audioValue` object is used to store the field value.

`audioValue.audios` []object

Audio object

`audioValue.audios[].url` string

Audio URL

`audioValue.audios[].title` string

Audio name

---

### Video

`videoValue` object

Video field. When `type` is `video`, the `videoValue` object is used to store the field value.

`videoValue.videos` []object

Video list

`videoValue.videos[].url` string

Video URL

`videoValue.videos[].title` string

Video name

```json [File]
{
    "id": 1016,
    "groupId": 1000,
    "type": "file",
    "title": "File Upload",
    "fileValue": {
        "files": [
            {
                "url": "https://example.com/doc1.pdf",
                "title": "Document1.pdf"
            }
        ]
    }
}
```