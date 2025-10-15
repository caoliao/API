# Connect CaoLiao with Other Apps Using Tencent HiFlow

## I. Feature Introduction

[Tencent HiFlow](https://qinglian.tencent.com) is an "application connector" launched by Tencent Cloud that enables multi-app integration without programming. As one of the first partners to join Tencent HiFlow, we have deeply collaborated with the Tencent team to provide users with the following capabilities:

### Quick Integration with Mainstream Apps

Achieve interoperability with over 200 applications including WeCom, DingTalk, Tencent Docs, Feishu, Kingdee, Vika, QQ Mail, and NetEase Mail.

### Double Efficiency with AI

Leverage more than ten AI applications such as health code recognition, image-to-Excel conversion, ID card recognition, and business card recognition to reduce repetitive manual tasks.

### No-Code Visual Operations

Visual design, drag-and-drop operations, and no-code implementation make it easy for non-technical users to get started without programming expertise.

## II. Application Scenarios

### 1. Sync to Online Spreadsheets for Data Aggregation and Analysis

Collected form data can be synchronized to applications like Tencent Docs and Vika for aggregation, sharing, and collaborative editing.

[![Learn More](////blogcdnimg.clewm.net/2023/03/image-1679993841189_16799938417757.png)](https://cli.im/help/78994)

[View Demo and Tutorial](https://cli.im/help/78994)

### 2. Group Message Push

`Instantly push newly submitted form data to internal work groups` via WeCom, Feishu, or DingTalk. Email and SMS notifications are also supported.

**Use Cases:**  
Hazard alerts, repair requests, appointment notifications, inspection anomalies, etc.

[![Learn More](//blogcdnimg.clewm.net/2023/03/image-1679993964136_16799939647961.png)](https://cli.im/help/78992)

[View Guide](https://cli.im/help/78992)

### 3. Integrate with Internal Business Systems

Seamlessly transfer data collected on CaoLiao to internal CRM, financial systems, and more for follow-up and efficient processing.

**Supported Apps:**  
Salesforce, Kingdee, Chanjet, etc.

**Use Cases:**  
Sales lead distribution, automated payroll calculation based on timesheets.

![file](//blogcdnimg.clewm.net/2023/03/image-1679994047876_16799940486522.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. AI-Powered Extensions

Tencent HiFlow's app center includes intelligent AI tools for automatic image, voice, and data recognition to further boost productivity. Supports ID card OCR, health code recognition, itinerary card parsing, and table image analysis.

**Use Cases:**  
Automated health code verification, employee bank card registration, new staff onboarding.

[![Learn More](//blogcdnimg.clewm.net/2022/09/image-1662541525450_16625415262412.png)](https://cli.im/help/78997)

[View Guide](https://cli.im/help/78997)

## III. Customer Cases

### 1. B&B Cleaning and Inventory Management

Builder: Lei Yang, Owner of Olai B&B  

Housekeepers scan QR codes to document pre- and post-cleaning photos, which are manually reviewed by supervisors. Room conditions are logged, and maintenance requests are reported in real time. Data synced to Tencent Docs enables analysis of cleaning hours, supply usage, key replacement progress, and repair tracking. [Details](https://cli.im/article/detail/2002)

### 2. No-Code Cross-Organization Service System with Closed-Loop Management

Builder: Manager Zhu, Anhui Supply and Marketing Group  

Used for internal service requests and system issue reporting, forming a "collection-review-tracking-resolution-knowledge base" workflow. Previously, scattered reporting methods led to duplicate issues and lack of integration with the knowledge base. [Details](https://cli.im/article/detail/2008)

## IV. Tutorials to Create Your Own Workflow

Step-by-step guides for the above scenarios with supporting materials:

- [Push Messages to Groups](https://cli.im/help/78992)
- [Sync to Tencent Docs for Data Management](https://cli.im/help/78994)
- [Automated Health Code Verification After Registration](https://cli.im/help/78997)

## V. API Pricing

### 1. CaoLiao Data API Pricing

Different versions offer varying monthly dynamic data push limits:

- Free/Basic/Advanced: 1,000 entries/month
- Enterprise: 20,000 entries/month
- Industry-Specific: Unlimited

See [CaoLiao Version Details](https://cli.im/help/84383)

### 2. Tencent HiFlow Pricing

Free tier: 500 tasks/month. Details: [HiFlow Pricing](https://qinglian.tencent.com/price/)

### 3. Notes:

One data push in CaoLiao may trigger multiple HiFlow tasks. Refer to [HiFlow Task Counting Rules](https://hiflow.tencent.com/docs/faq/howTaskCount/).

## Resources

- [Tencent HiFlow Pricing](https://qinglian.tencent.com/price/)
- [Tencent HiFlow Website](https://hiflow.tencent.com/)
- [HiFlow Beginner's Guide](https://hiflow.tencent.com/docs/set-console/)
- [HiFlow Task Counting Explained](https://hiflow.tencent.com/docs/faq/howTaskCount/)
- [CaoLiao Webhook Features](./en/data-api/webhook.md)
- [CaoLiao Data API Features](https://cli.im/help/56845)
- [Enable Official Database for Visual Reports](./en/data-api/BI/api-with-sugar.md)

## FAQs

### 1. Can I push to different groups based on conditions?

Yes, HiFlow supports conditional workflows to route data to different apps.

### 2. Does it support WeCom version of Tencent Docs?

Not yet. Follow HiFlow updates for future support.

### 3. Can images, audio, videos, and signatures be pushed?

Currently supports images and signatures (URLs/preview links). Audio/video/files are not supported yet.

### 4. What data gets pushed?

Currently supports form submissions, edits, and approvals. Status changes and sub-code dynamic data will be added later.

## CaoLiao Community

Join our dedicated community to share experiences and get expert advice: [Visit Community](https://cli.im/community/minihome/question/104)