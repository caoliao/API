# Group Message Push

## Scenario Overview

Through Tencent QuickLink, instantly push form submission records to internal work groups, supporting WeCom, Feishu, and DingTalk, with additional options for email and SMS notifications.

**Applicable Scenarios:**
Hazard detection alerts, fault repair reminders, appointment notifications, inspection anomaly alerts, etc.

![](//blogcdnimg.clewm.net/2023/03/image-1680056669818_16800566709529.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### Step-by-Step Tutorial

Using a common fault reporting application as an example, this guide demonstrates how to push submitted fault records to a WeCom group. The process is similar for DingTalk and Feishu groups.

### Summary

Access Tencent QuickLink to create a new workflow, with **CaoLiao QR Code** as the trigger application and **WeCom Group Bot** as the execution application.

## Prerequisites

1. Create a fault reporting QR code or a scenario-specific QR code. [Example template](https://cli.im/share/yUNDZTv)
2. Add a group bot to your WeCom group. [How to enable a WeCom group bot](https://open.work.weixin.qq.com/help2/pc/14931)

### 1. Create a Workflow

Log in to the [Tencent QuickLink backend](https://ipaas.cloud.tencent.com/login) and select **New Workflow**.

![](https://blogcdnimg.clewm.net/2023/12/image-1703221820136_17032218207439.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Configure the CaoLiao Application

- **Add the CaoLiao QR Code application and select the trigger method**: New form submission.

![](https://blogcdnimg.clewm.net/2023/12/image-1702621882685_17026218831515.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Authorization Configuration**

![](https://blogcdnimg.clewm.net/2023/12/image-1702621898895_17026218993538.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Parameter Configuration**
Click **Execute Preview** to generate a listening address. Copy this address and configure it in the form's Data API settings.

![](https://blogcdnimg.clewm.net/2023/12/image-1702622036385_17026220368551.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Configure Webhook Address**
Copy the Tencent QuickLink push address and add it to the webhook push address in CaoLiao's backend. Navigate to **Form Settings > Settings > Data API** or **Advanced Features > Data API**.

![](https://blogcdnimg.clewm.net/2023/12/image-1702622063920_17026220645867.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Sample Data**
Scan the QR code and submit a test record. QuickLink will automatically detect the sample data.
*Note: If the form is updated, submit another record and select the latest entry before clicking **Re-preview**.

![](https://blogcdnimg.clewm.net/2023/12/image-1702622078956_17026220798412.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. Add Execution Application: WeCom Group Bot

The same method applies to DingTalk and Feishu group bots.

- **Add the WeCom Bot and select the execution action**: Send rich text message.

![](https://blogcdnimg.clewm.net/2023/12/image-1702620476047_17026204767409.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Authorization Configuration**: Add the WeCom group bot address.
  Obtain the bot address by adding a group bot in WeCom. [How to enable a WeCom group bot](https://open.work.weixin.qq.com/help2/pc/14931)

![](https://blogcdnimg.clewm.net/2023/12/image-1702620643237_17026206438181.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- **Parameter Configuration**
  Configure the rich text message using variables and static text for dynamic content. After setup, click **Execute Preview** to receive the message in the WeCom group.

![](https://blogcdnimg.clewm.net/2023/12/image-1702620768462_17026207694901.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![](https://blogcdnimg.clewm.net/2023/12/image-1702620802545_17026208034045.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. Publish the Workflow

After saving, both applications should show as verified. Click **Publish**. If errors prevent publishing, use **Check** to identify issues.

![](https://blogcdnimg.clewm.net/2023/12/image-1702621014716_17026210155847.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## References

1. [Tencent QuickLink Website](https://qinglian.tencent.com/)
2. [Tencent QuickLink Beginner's Guide](https://qinglian.tencent.com/help/docs/sHInHG/)
3. [CaoLiao Webhook Documentation](./en/data-api/webhook.md)

## Additional Use Cases

- [Sync to Tencent Docs](https://cli.im/help/78994)
- [AI Function Extensions](https://cli.im/help/78997)

## FAQs

### 1. Why don't my variables match the form content?

This occurs if you've reselected the form. Resubmit a record and re-test with the new sample.

### 2. How to implement conditional alerts (e.g., inspection anomalies)?

Add a built-in conditional judgment application after the CaoLiao step. Set conditions to trigger group alerts only when met.

![](https://blogcdnimg.clewm.net/2023/12/image-1702625193428_17026251939159.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. Can alerts be sent to multiple groups simultaneously?

Yes. Add a new workflow with a different group bot address (new account).

### 4. Can alerts be routed to different groups based on conditions?

Yes. Combine conditional judgment with multiple group bot applications, each targeting a different group.

## CaoLiao Community

A dedicated community version is available for sharing experiences and Q&A with expert support. [Visit Community](https://cli.im/community/minihome/question/104)