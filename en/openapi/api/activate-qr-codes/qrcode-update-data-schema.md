# QR Code Dynamic Data

## Example Dynamic Data

> Under construction

## Dynamic Data Type Reference Table

| Type | Type Constant | Attributes Used | 
|------ | ----- | ------ |
| Form Submission | 1 | recordSubmit |
| Status Change | 2 | stageChange |
| Document Review | 3 | fileRead |
| Member Join | 4 | memberJoin |
| Bottom Collaboration | 5 | comment |
| QR Code Content Modification | 6 | qrcodeChange |

## Data Details

`type` integer

Dynamic data type, please refer to [Dynamic Data Type Reference Table](#dynamic-data-type-reference-table)

---

### Form Submission

`recordSubmit` object

Used when type=1, contains this field

`recordSubmit.serialNumber` string

Record ID

---

`recordSubmit.qrcodeCoding` string

QR Code Coding

---

`recordSubmit.formSerialNumber` string

Form ID, if type is form submission, this field represents the form ID

---

`recordSubmit.recorder` string

Submitter

---

`recordSubmit.addTime` string

Submission time (yyyy-MM-dd HH:mm:ss)

---

`recordSubmit.fields` []FormField

Field list, please refer to [Form Field](./en/openapi/api/forms/form-field-schema.md)