# API Overview

This document introduces the interfaces provided by the dynamic QR code record API.

## Operations on Dynamic QR Codes

CaoLiao QR Code operations include creation, modification, deletion, and querying of dynamic QR codes. The creation of a dynamic QR code must rely on a template—meaning a template must exist before a dynamic QR code can be created. In the current version, templates must be created on the CaoLiao QR Code platform. After creating a template and obtaining its UID, you can query all component information of the template and assign values to the relevant components to successfully create a dynamic QR code.

![image-20250102111646743](https://gstatic.clewm.net/caoliao-resource/250102/308ba7_09fb1c99.png)

The following are APIs related to dynamic QR codes:

| API                     | Functionality                                                                 |
|-------------------------|-------------------------------------------------------------------------------|
| Get Template Metadata   | After creating a QR code template on the CaoLiao QR Code platform, you can query the template's metadata information using its UID. |
| Create Dynamic QR Code  | Create a dynamic QR code based on the template UID, template metadata, and customized component content. |
| Get Dynamic QR Code Content | Retrieve the component content and status information of a dynamic QR code using its UID. |
| Edit Dynamic QR Code    | Edit an existing dynamic QR code.                                             |
| Delete Dynamic QR Code  | Delete the dynamic QR code (supports batch deletion).                         |

## Operations on Statuses

The CaoLiao QR Code status component can be added to a QR code to display the real-time status of the dynamic QR code. Similar to the creation of dynamic QR code templates, the creation of status components must also be completed on the CaoLiao QR Code platform. Currently, the CaoLiao API allows you to query status component information and update the status of sub-codes.

![image-20250102125537462](https://gstatic.clewm.net/caoliao-resource/250102/308ba7_673f43fa.png)

The following are APIs related to statuses:

| API                     | Functionality                                                                 |
|-------------------------|-------------------------------------------------------------------------------|
| Get Status Component Information | Retrieve all status information for an entire status group using its UID. |
| Update Dynamic QR Code Status | If the dynamic QR code has status information, you can update the status of the sub-code in real time using the QR code UID and the relevant status ID. |

## Operations on Records

CaoLiao QR Code records are generated when users fill out forms within the QR code. Currently, the CaoLiao API allows you to query forms and records.

The following are APIs related to records:

| API                     | Functionality                                                                 |
|-------------------------|-------------------------------------------------------------------------------|
| Get Form Metadata       | Retrieve all component configuration information for a form using its UID.    |
| Batch Query Records     | Batch query record information under a form using its UID (supports QR code and time-based searches). |
| Get Single Record Details | Query detailed information for a specific record using its UID.              |