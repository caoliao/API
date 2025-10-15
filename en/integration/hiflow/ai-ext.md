# AI Feature Extension

## Scenario Overview

Tencent Qinglian Application Center comes with rich intelligent AI applications that can automatically recognize images, voice data, and more to further improve work efficiency.

**Supported Applications:**
ID card OCR, epidemic health code recognition, bank cards, invoices, table image parsing, voice-to-text, etc.

**Applicable Scenarios:**
Automatic epidemic record recognition, labor personnel bank card reporting, etc.

![file](//blogcdnimg.clewm.net/2022/09/image-1662541984660_16625419862039.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Hands-on Experience

Scan the QR code below, fill in the epidemic prevention information, and [view the epidemic registration form](https://docs.qq.com/sheet/DU25QUENVem5IV0tl?tab=BB08J2).
*Note: Remember to delete the row of data you submitted, but do not modify other data.

![file](//blogcdnimg.clewm.net/2023/03/image-1680057762745_16800577631522.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Tutorial:

Taking epidemic prevention registration as an example, automatically recognize health codes, synchronize the results to Tencent Docs, and notify abnormal cases in the WeCom group.

> Note: The AI components in Qinglian are currently being upgraded. There are two versions of the same AI application—choose the one labeled **V2**, as the other is unavailable.

### Preparations:

1. Create an epidemic QR code or a scenario-specific QR code. [Example template](https://cli.im/share/7NpigkN)
2. Create a registration table in your personal Tencent Docs and edit the headers. [Example table](https://docs.qq.com/sheet/DU25QUENVem5IV0tl?tab=BB08J2)

### 1. Create a Workflow

Log in to the [Tencent Qinglian backend](https://ipaas.cloud.tencent.com/login) and select **New Workflow**.

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229830275_17032298308771.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Configure CaoLiao Application

- **Add the CaoLiao QR Code application and select the trigger method**: New form submission;

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229894502_17032298949209.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Authorization Configuration**

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229907792_17032299082049.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Parameter Configuration**
Click **Execute Preview**, and a listening address will appear below. Copy this address and configure it in the form's data API.

![file](https://blogcdnimg.clewm.net/2023/12/image-1703229995917_17032299966761.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Configure Webhook Address**
Copy the Tencent Qinglian push address to the webhook push address in the CaoLiao backend. Add it in **Form Settings** > **Settings** > **Data API**, or navigate to **Advanced Features** > **Data API**.

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230030503_17032300310309.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Sample Data**
Scan the QR code and add a piece of data. Qinglian will automatically detect the sample data.
*Note: If the form is updated, add another form record. You can select the latest record in the sample data and click **Preview Again**.

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230053355_17032300538076.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. Add AI Epidemic Health Code Recognition

Add **AI Epidemic Health Code Recognition-V2**. In the parameter configuration, set the image address to the first URL (`urls[0]`) in the health code field. The form retrieves the address of the first image in the health code component. (The image component supports multi-image uploads.)

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230509599_17032305100334.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. Add AI Travel Itinerary Card Recognition

Add **AI Travel Itinerary Card Recognition-V2**. In the parameter configuration, set the image address to the first URL (`urls[0]`) in the travel code field. The form retrieves the address of the first image in the travel code component. (The image component supports multi-image uploads.)

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230527314_17032305277374.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 5. Add Tencent Docs

Add the Tencent Docs application. Only the personal version of Tencent Docs is supported here. Configure your account.

- **Select the target spreadsheet**: Create a table in Tencent Docs beforehand, edit the column headers, and select the table and worksheet.
- **Field matching**: Map the corresponding form component data by header. Test and preview to check if the data appears in Tencent Docs.

![file](https://blogcdnimg.clewm.net/2023/12/image-1703230543384_17032305438811.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 6. Publish the Workflow

Finally, click **Publish Workflow** in the upper-right corner to complete the workflow creation.

## References

1. [Tencent Qinglian Scenario Connector Website](https://qinglian.tencent.com/)
2. [Tencent Qinglian Scenario Connector Beginner's Guide](https://qinglian.tencent.com/help/docs/sHInHG/)
3. [CaoLiao Webhook Documentation](./en/data-api/webhook.md)

## More Application Scenarios

- [Sync to Online Docs](https://cli.im/help/78994)
- [Group Message Push](https://cli.im/help/78992)

## CaoLiao Community

If you have questions about **data API functionality** or want to share your experience, we welcome you to join the discussion in our community. Product and technical teams will actively participate. [Join the Community](https://cli.im/community/minihome/question/104)