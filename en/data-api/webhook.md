# Webhook

## Feature Introduction

CaoLiao pushes [dynamic data] in JSON format to a specified interface URL, transmitting data to another system for notifications and business integration.  
This address must **`allow public network access`**. Your server must return a 200 status code within 5 seconds as a response; if the response fails, it will retry up to 5 times (15s/1m/4m/16m/1h).

> Currently, only form data push is supported, including new form submissions, edited form data, form review results, and marked progress updates.

## Application Scenarios

### 1. Connect third-party apps for group message push and spreadsheet data aggregation

Through Tencent QuickLink (an "app connector" launched by Tencent Cloud), integrate CaoLiao QR codes with other apps/services.  
Enable features like: data group messaging, secondary data analysis, CRM system integration, and AI functions. This breaks data silos and maximizes data value. [Learn more](https://cli.im/help/78884)

[![Learn more](//blogcdnimg.clewm.net/2024/05/image-1714890027335_17148900210360.png)](https://cli.im/help/78994)

### 2. Integrate with proprietary systems

Implement QR code-based data collection on CaoLiao's platform, then use APIs to connect with enterprise system workflows. This allows businesses to leverage CaoLiao's features at minimal cost while retaining existing systems.

![file](//blogcdnimg.clewm.net/2022/02/image-1644546273607_16445462739484.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Workflow

You can add push addresses in the **Forms Settings page** by selecting Data API,  
or add push addresses in the **Data API feature page** and then select forms to push.

### 1. Forms Settings Page

In Forms Settings, select [Data API], enter a name and push address, then save.  
*`*Note: This is a global setting for the form and applies to all associated QR codes.`*

![file](//blogcdnimg.clewm.net/2022/11/image-1668743694361_16687436948264.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![file](//blogcdnimg.clewm.net/2022/11/image-1668743709153_16687437095751.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Data API Feature Page

Go to the workbench: 【Data Management】-【Data API】-【Enable Webhook】, enter push data and select forms to push. If already enabled, click Configure to add more pushes.  
*`*Note: When using Tencent QuickLink, since forms cannot be selected there, you can only choose one form here or set it directly in the form.`*

![file](https://blogcdnimg.clewm.net/2024/04/image-1714370711612_17143707125963.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![file](//blogcdnimg.clewm.net/2022/11/image-1668743728364_16687437287845.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Push Data Types

Currently, only form record data push is supported. However, when the QR code is a batch sub-code, the template name and variable content will also be pushed along with the form record fields. Pushing only sub-code variable content is not yet supported.

- Regular dynamic QR codes: Push form records
- Batch sub-codes: Push form records + batch template name + sub-code variable content

## Push Event Types

Currently supports the following events:

- New form submission
- Edited form data
- Form review result push
- Marked progress status update

## Push Format Specification

### Push Method

```text
POST
Content-Type: application/json
```

### Format

All CaoLiao event requests follow this format:

```json
{
    "time": "2022-06-30 17:06:39",
    "event": "event identifier",
    "data": {}
}
```

### Field Explanations:

| Field | Description | Type |
|--------|------|------|
| time | Event timestamp, using +8 timezone in YYYY-mm-dd HH:ii:ss format | string |
| event | Event type (see Event Types section) | string |
| data | Data payload, format varies by event (refer to specific event documentation) | object |

## Event Type Identifiers

| Event | Identifier |
|------|------|
| New form submission | FORM_DATA_SUBMIT |
| Edited form data | FORM_DATA_EDITED |
| Form review result | FORM_DATA_REVIEW |

### New Form Submission

Form events currently do not push audio, video, or file-type data.

Sample data:

```json
{
  "time": "2022-06-30 17:06:39",
  "event": "FORM_DATA_SUBMIT",
  "data": {
    "ref_data": {
      "created_at": "2022-06-30 17:06:39",
      "serial_number": "L1000001",
      "form": {
        "number": "D20",
        "name": "Meeting Check-in"
      },
      "submitter": {
        "name": "Submitter A",
        "phone_number": "18888881111"
      },
      "review": {
        "state": "Pending Review",
        "time": "2022-06-30 17:06:39"
      },
      "process": {
        "state": "Unprocessed",
        "time": "2022-06-30 17:06:39"
      },
      "fields": {
        "Name": "CaoLiao",
        "Phone": "18888648888",
        "WeChat ID": "CHEN",
        "ID Number": "330200000000000000",
        "Employee ID": "FBI100",
        "Single Choice": "Yes",
        "Multiple Choice": [
          "Option 1",
          "Option 3"
        ],
        "Check Items": {
          "Item 1": "Yes",
          "Item 2": "No",
          "Item 3": "N/A",
          "Item 4": ""
        }
      },
      "ref_qrcode": {
        "name": "Test QR Code",
        "type": "CHILD",
        "code": "qAbCxZ",
        "template": {
          "name": "Test Template"
        },
        "fields": {
          "Text 1 Placeholder": "A",
          "Text 2 Placeholder": "B"
        },
        "state": {
          "Status Group 1": "Abnormal",
          "Status Group 2": "Normal"
        }
      }
    }
  }
}
```

### Field Descriptions

| Field | Description | Type |
|------|------|------|
| time | Event timestamp | string |
| event | Event identifier | string |
| data | Event details | object |
| data.ref_data | Form record details | object |
| data.ref_data.created_at | Submission time | string |
| data.ref_data.serial_number | Record ID | string |
| data.ref_data.web_url | Record URL | string |
| data.ref_data.form | Form info | object |
| data.ref_data.form.number | Form ID | string |
| data.ref_data.form.name | Form name | string |
| data.ref_data.submitter | Submitter info | object |
| data.ref_data.submitter.name | Submitter name | string |
| data.ref_data.submitter.phone_number | Submitter phone | string |
| data.ref_data.review | Review info (if enabled) | object |
| data.ref_data.review.state | Review status<br>Pending/Approved/Rejected | string |
| data.ref_data.review.time | Review time | string |
| data.ref_data.process | Progress info (if enabled) | object |
| data.ref_data.process.state | Progress status | string |
| data.ref_data.process.time | Progress update time | string |
| data.ref_data.fields | Form field data | map<string, any> |
| data.ref_qrcode | QR code info | object |
| data.ref_qrcode.name | QR code name | string |
| data.ref_qrcode.type | QR code type<br>CHILD(sub-code)/NORMAL(regular dynamic code) | string |
| data.ref_qrcode.code | Unique code ID | string |
| data.ref_qrcode.web_url | Code URL | string |
| data.ref_qrcode.template | Template info (sub-codes only) | string |
| data.ref_qrcode.template.name | Template name | string |
| data.ref_qrcode.fields | Sub-code placeholder data (sub-codes only) | object |
| data.ref_qrcode.state | Code status data | map<string, string> |

Form field data (data.ref_data.fields) and sub-code field data (data.ref_qrcode.fields) are both key-value pairs. The key represents the component/placeholder name, and the value type depends on the component type.

### Edited Form Data

Event identifier: FORM_DATA_EDITED  
Payload structure identical to "New Form Submission" event.

### Form Review Result

Event identifier: FORM_DATA_REVIEW  
Payload structure identical to "New Form Submission" event. Review result can be obtained via data.ref_data.review.state field.

### Form Component Data Examples

Name, Phone, WeChat ID, ID Number, Employee ID, License Plate, Gender, Single-line Text, Multi-line Text, Date, Time, Single Choice, Multi-level Selection, Serial Number

All pushed as strings. Example:

```json
{
    "fields": {
        "Name": "CaoLiao",
        "Gender": "Male",
        "Multi-level Selection": "Zhejiang Province/Ningbo City/Haishu District"
    }
}
```

#### Check Items

Check items are structured as map<string, enum string>. Example:

```json
{
    "fields": {
         "Check Item A": "Yes",
         "Check Item B": "No",
         "Check Item C": "N/A",
         "Check Item D": "",
    }
}
```

#### Value Enums

| Value | Meaning |
|---|---|
| Yes | √ |
| No | × |
| N/A | / |
| Empty string | |

#### Images

Image-type component values are objects:

```json
{
    "fields": {
         "Image": {
             "preview_url": "https://preview-url/",
              "urls": [
                "image1-download-url",
                "image2-download-url"
              ]
         }
    }
}
```

## FAQs

### 1. Is webhook a paid feature?

Different CaoLiao editions have varying monthly push limits:

- Free, Basic, and Advanced: 1,000 pushes/month
- Enterprise: 20,000 pushes/month
- Industry-Specific: Unlimited pushes

See [CaoLiao Edition Push Limits](https://cli.im/help/84383)

For Tencent QuickLink integration:  
Free edition allows 500 tasks/month. See [Tencent QuickLink Pricing](https://qinglian.tencent.com/price/)

### 2. How are push counts calculated?

Each data push counts as one, including: new submissions, review completions, status changes, and form edits.

### 3. Image components have two URLs - which to use?

Each image component provides two URL types: xxx.urls and xxx.preview_urls.

- xxx.urls: Direct image URLs (for single images) - suitable for displaying images directly in group messages or AI recognition
- xxx.previews_urls: Image preview page URLs (for multiple images) - display as hyperlinks for browsing