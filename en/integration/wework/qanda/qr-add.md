# Adding a QR Code to the WeCom Workbench

You can add QR codes as self-built applications to the WeCom workbench, enabling employees to quickly access them from their workbench.

## 1. Access QR Codes Anytime in WeCom

You can add QR codes that require **frequent viewing or filling** to the workbench, making them ideal for scenarios like item requisition or hazard reporting. These QR codes will remain accessible in the WeCom workbench, allowing employees to open them directly without repeated scanning or time-consuming searches, ensuring flexible and convenient registration.

![](//blogcdnimg.clewm.net/2022/02/image-1645083988125_16450839887901.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 2. Personalized Workbenches for Different Employees

You can assign specific QR codes to the workbenches of corresponding responsible personnel, ensuring dedicated individuals handle specialized tasks.

## Prerequisites

1. The CaoLiao QR Code application must be installed in WeCom. If not installed, refer to the [Installation Guide](https://cli.im/help/69682).
2. The operator must be a WeCom super administrator.

## Steps

### 1. Log in to the CaoLiao Workbench and Configure the QR Code

Locate the QR code you wish to add to the WeCom workbench. Set the access method to **[CaoLiao QR Code Mini Program]**, then download and save the QR code image.

![](//blogcdnimg.clewm.net/2022/02/image-1645686575634_16456865781966.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Decode the QR Code and Copy the Link

Open the [CaoLiao QR Code Tools Page](https://cli.im/tools), navigate to the **[Decoder]**, upload the saved QR code image, and copy the decoded link.

![](//blogcdnimg.clewm.net/2022/02/image-1645087067872_16450870687236.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. Log in to the WeCom Admin Console and Create an Application

Log in to the [WeCom Admin Console](https://work.weixin.qq.com/wework_admin/loginpage_wx), switch to **[Application Management]**, and under the self-built section, click **[Create Application]**.

![](//blogcdnimg.clewm.net/2022/02/image-1645085767997_16450857695429.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. Complete the Self-Built Application Information

Upload the application logo, fill in the name and description, and select the colleagues who need access to this application under **[Visible Range]**.

> Note: The visible members of the self-built application must be within the visible range of the CaoLiao QR Code application.  
> For example, if the CaoLiao QR Code application's visible range includes Zhang San, Li Si, and Wang Wu, the self-built application's visible members must be selected from these three individuals.

![](//blogcdnimg.clewm.net/2022/02/image-1645086491325_16450864918053.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 5. Set the Self-Built Application Homepage

Paste the QR code link obtained in Step 1 into the **[Application Homepage]** field of the self-built application. The QR code will then be directly accessible from the WeCom workbench.

![](//blogcdnimg.clewm.net/2022/02/image-1645088085827_16450880865555.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

You can also add multiple QR codes as self-built applications to different employees' workbenches, streamlining their workflow.