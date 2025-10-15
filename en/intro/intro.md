# CaoLiao Open Platform

CaoLiao QR Code provides open capabilities including bulk QR codes generation, label production, encoding & decoding, and data connectivity. You can integrate it with enterprise internal systems as a component of the corporate information architecture, or utilize CaoLiao services within third-party applications like WeCom and Tencent Docs.

## I. Open APIs

### 1. Data API Service

CaoLiao offers three data delivery methods: Webhook, official database, and custom database. Connect with third-party data analysis tools to create data dashboards, or actively call data via programming to integrate with other systems.

Use Cases:

- Create visual data dashboards

Enable the 【Official Database】 feature and use tools like Baidu SugarBI to connect with CaoLiao's database for visual dashboard creation.

::: info
More case studies: [Visual Dashboard Case Collection](https://cli.im/help/94931)
:::

![](https://blogcdnimg.clewm.net/2023/09/16296800933186_效果1_16950197715445.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- Connect with Tencent QuickLink to integrate other applications

Enable 【Webhook】 and use Tencent QuickLink to connect CaoLiao QR Code with other apps/services, enabling group notifications, online spreadsheet management, CRM integration, AI features, etc.

![](https://blogcdnimg.clewm.net/2023/09/image-1695019591123_16950195917104.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

- Enterprise process integration

Implement QR code data collection on CaoLiao platform, then use APIs to connect with enterprise systems. This allows enterprises to adopt CaoLiao functionalities at minimal cost while retaining existing systems.

[Learn more about Data API](https://cli.im/help/56845)

### 2. Label Production API

Integrate CaoLiao QR Code with enterprise internal systems as an information architecture component. By connecting with our one-item-one-code label production API, you can batch-generate QR code labels directly within your system—eliminating data export/import steps for greater efficiency. Ideal for product labels, access credentials, personnel cards, etc.

![](https://blogcdnimg.clewm.net/2023/10/image-1698288046374_16982880469162.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

Feishu Multi-dimensional Tables has developed a "CaoLiao QR Code" plugin based on our API. Users can select label templates directly within Feishu to automatically invoke CaoLiao API for batch label generation. [Details](https://cli.im/help/88738)

[Learn about Label Production API](https://cli.im/help/86460)

### 3. Dynamic QR Code Embedding

Beyond scanning, CaoLiao-generated dynamic QR codes can be embedded in WeChat articles, menus, or third-party platforms for direct access.

[Learn about Embedding](https://cli.im/help/55526)

**Bulk dynamic QR code generation and record addition APIs are under development and coming soon.**

## II. Third-party Application Integration

### 1. WeCom × CaoLiao QR Code

For teams using WeCom, install the 【CaoLiao QR Code】 app in WeCom workbench to access exclusive collaboration features that enhance organizational efficiency.

[Learn about WeCom Edition](https://cli.im/wxwork/index)

### 2. Baidu SugarBI × CaoLiao QR Code

CaoLiao has integrated with Baidu SugarBI. Dashboards created via SugarBI can be embedded in CaoLiao Mini Programs for direct access. CaoLiao users also enjoy discounts on SugarBI paid versions.

Push data collected via CaoLiao to SugarBI using Data API for flexible data applications. SugarBI—a Baidu-developed visualization tool based on Echarts—offers rich chart components and intelligent operations for self-service BI dashboards and large screens.

[View Tutorial](./en/data-api/BI/api-with-sugar.md)

### 3. Tencent QuickLink × CaoLiao QR Code

Tencent QuickLink is a "connector" by Tencent Cloud enabling multi-app integration without coding. As a launch partner, CaoLiao has collaborated deeply with Tencent:

**Fast integration with mainstream apps**

Connect with 200+ apps including WeCom, DingTalk, Tencent Docs, Kingdee, Vika, QQ Mail, and NetEase Mail.

**AI capability integration**

Leverage AI applications like health code recognition, image-to-Excel conversion, ID card recognition, and business card recognition to reduce repetitive tasks.

[Learn about QuickLink](https://cli.im/help/78884)

### 4. Ant Blockchain × CaoLiao QR Code

CaoLiao users can freely use Ant Blockchain to notarize form records and sub-code content.

**Timestamp notarization ensures data authenticity**

Submitted records (e.g., inspections, safety commitments, contracts) are automatically blockchain-notarized with unique hash IDs, proving existence at specific times.

**Commodity traceability**

Transparently record supply chain information from production to consumption via blockchain, enabling traceability verification.

**Tamper-proof verification**

After notarization, preserved "hash" and "source files" can be verified for integrity, serving as electronic evidence.

[Visit Ant Group](https://tech.antfin.com/products/TWC)

### 5. Tencent Docs × CaoLiao QR Code

The 【CaoLiao QR Code】 plugin is available on Tencent Docs, offering 150+ QR code templates for quick styling.

[Learn about the Plugin](https://cli.im/help/80061)

### 6. Canva × CaoLiao QR Code

CaoLiao integrates Canva's online design tools for label background editing during QR code production.

Canva provides HD images, illustrations, and visual elements. Users can design label backgrounds directly by searching relevant keywords.

> For integration/partnership inquiries, contact: mkt@nears.cn