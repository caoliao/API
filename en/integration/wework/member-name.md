# Completing Supplementary Name Information for Members

After integrating with WeCom, contact member information within the visible range will be synchronized. However, due to WeCom restrictions, the CaoLiao platform cannot retrieve and store name information for later use. This results in form data submitted by WeCom members displaying the submitter and name information as a string of characters like "wodkFjCwAAkjJTzgDHDcbf" when exported.

Administrators need to complete the 【Supplementary Name】 field for members on the CaoLiao platform, or members can complete it themselves via mobile, to ensure the submitter and name information in form records display correctly. (This setting does not apply to non-WeCom members.)

## Administrators Completing Information via Desktop

### 1. Navigate to Settings > Member Management

In the 【Organization Structure】 section, locate members without supplementary names and edit their information.

![Administrator Completing Member Names](//blogcdnimg.clewm.net/2022/03/image-1646981802011_16469818048706.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Edit Individually (Click Edit)

![Editing Member Names Individually](//blogcdnimg.clewm.net/2022/03/image-1646981817195_16469818197986.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

:::info Note
The supplementary name should ideally be the member's real name, matching the name displayed in the contacts. Otherwise, the name seen in the backend will differ from the name in exported data.
:::

### 3. Bulk Completion

Click 【Bulk Completion】, download the update document, fill in the supplementary names, then upload the document to complete the bulk update.

![Bulk Completion Step 1](//blogcdnimg.clewm.net/2022/03/image-1646981839979_16469818431078.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![Bulk Completion Step 2](//blogcdnimg.clewm.net/2022/03/image-1646981852736_16469818555681.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![Bulk Completion Step 3](//blogcdnimg.clewm.net/2022/03/image-1646982091475_16469820940667.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Members Completing Information via Mobile

If there are too many members requiring updates, members can complete their own information via the WeCom mobile app to reduce the administrator's workload.

![Members Completing Information Themselves](//blogcdnimg.clewm.net/2022/01/image-1643521180994_16435211810568.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Impact of Incomplete Information

### 1. Exporting Form Records

The submitter and name information in the exported spreadsheet appear as a string of code.

![Exporting Form Records](//blogcdnimg.clewm.net/2021/12/image-1640589995044_16405899953509.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. Exporting Records as PDF

The submitter and name information in the PDF also appear as a string of code.

![Exporting PDF](//blogcdnimg.clewm.net/2021/12/image-1640587235226_16405872359546.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. Image Watermark

The submitter and name information in the image watermark also appear as a string of code.

![Image Watermark](//blogcdnimg.clewm.net/2021/12/image-1640588506190_16405885097638.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. API Interface

Form data retrieved via the API interface displays the submitter and name information as a string of code.

![API Interface](//blogcdnimg.clewm.net/2021/12/image-1640589887877_16405898881435.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 5. QR Code Mini Program Display

For paid users scanning QR codes via WeChat, the default access method is to view the QR code. (WeCom scans are unaffected, and free version users accessing via the CaoLiao Mini Program are also unaffected.)

![Mini Program Display](//blogcdnimg.clewm.net/2021/12/image-1640672319769_16406723201335.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)