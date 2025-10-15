# Sync to Online Spreadsheets for Data Analysis

## Scenario Overview

Through Tencent QuickLink, collected form data can be synchronized to applications like Tencent Docs and Vika for statistical analysis, data sharing, and collaborative editing. It also supports synchronization to MySQL databases.

![file](//blogcdnimg.clewm.net/2023/03/image-1680055897726_16800558982709.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## Demo

Using fire hydrant inspections as an example, we demonstrate how inspection records can be synchronized to Tencent Docs' smart tables via Tencent QuickLink. This enables workload statistics for inspectors, checking missed inspections by date, and calculating maintenance costs.

### Video Demo

Duration: 4 minutes

<video src="//blogcdnimg.clewm.net/2022/10/tongbuwendang_16659810199560.mp4" controls></video>

## References

1. [Fire Hydrant Inspection Form (Tencent Docs)](https://docs.qq.com/sheet/DU1JMRWdHb1FNbm5h?tab=0r6h9i)
2. [Tencent QuickLink Scenario Connector Website](https://qinglian.tencent.com/)
3. [Tencent QuickLink Scenario Connector Beginner's Guide](https://qinglian.tencent.com/help/docs/sHInHG/)
4. [CaoLiao Webhook Documentation](./en/data-api/webhook.md)

## Additional Use Cases

- [Group Information Push](https://cli.im/help/78992)
- [AI Function Extension](https://cli.im/help/78997)

## FAQs

#### 1. Currently only supports personal version of Tencent Docs, not the WeCom edition.

#### 2. How to link Tencent spreadsheets to codes

You can link them via Mini Program.

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740448783_16987404495615.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**Add a [Redirect Link] and select [Other Mini Program]**

``` plaintext
appID: wxd45c635d754dbf59
Account Original ID: gh_252c5f06840b
Mini Program Path: pages/detail/detail.html?url=spreadsheet_link
```

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740057186_16987400576742.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**Spreadsheet Link: The URL in the address bar when editing the spreadsheet**

![file](https://blogcdnimg.clewm.net/2023/10/image-1698740255899_16987402565423.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 3. Can the column headers in Tencent spreadsheets match the form component names?

They can be different. Content is manually matched and not automatically identified by names.

## CaoLiao Community

A dedicated community version has been created for this feature, where you can share usage experiences, post questions, and get answers from professional consultants. [Visit the Community](https://cli.im/community/minihome/question/104)