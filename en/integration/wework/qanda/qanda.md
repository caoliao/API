# WeCom Edition FAQs

## Existing Account Integration with WeCom

### 1. Integration Process Issues

#### 1) How to integrate an existing CaoLiao account into WeCom for use

Go to 【Workbench】> 【Integrate Account into WeCom Edition】 to automatically sync enterprise contacts. Members can then use WeCom to scan QR codes, fill out forms, view data, share content with colleagues, and receive notifications. [View integration tutorial](https://cli.im/help/69682)

#### 2) Will integration affect existing features, data, or member collaboration?

Integration is simply **the process of binding your account to WeCom**. It will not impact existing features, data, or members. All operations in WeChat will continue to function normally, while additional WeCom-exclusive features will be enabled. Synced WeCom members can collaborate more efficiently within WeCom.

#### 3) During integration, scanning the QR code shows "App already added, proceed to workbench"

This message indicates you've already added the CaoLiao QR Code app in WeCom. Log out, switch to 【Log in via WeCom QR Code】, and then go to 【Import Old Account Data】 on the right side of the workbench to complete the binding. [View import tutorial](https://cli.im/help/69625)

#### 4) During integration, scanning the QR code shows "Recommend to admin" and fails to add the app

Due to WeCom rules, enterprises with 500+ employees cannot directly add third-party apps. You must recommend the app to an admin for addition and configuration. [View tutorial](https://cli.im/help/69676)

#### 5) How to proceed if WeCom is not yet registered

If your company hasn't registered for WeCom, you can quickly register for free and then integrate with CaoLiao. Newly registered enterprises inviting members may receive red packet rewards from WeCom. [Learn more](https://cli.im/help/70233)

### 2. Post-Integration Special Issues

#### 1) After integration, WeCom backend shows "Free Edition" despite having a paid plan

Due to WeCom restrictions, payment must be processed through WeCom to upgrade to a paid plan and lift the 50-user visible range limit. Contact your WeCom admin to purchase the "Legacy User Integration Plan" for 1 RMB to sync paid benefits. [View tutorial](https://cli.im/help/69993)

#### 2) How to unbind WeCom and revert to pre-integration state

**WeCom admins** can go to 【WeCom】> 【Admin Console】> 【App Management】, find the 【CaoLiao QR Code】 app, and delete it to revert to the standard version. The original account login (via password or WeChat QR code) will remain functional.

> Desktop reversion must be performed by a WeCom admin.

**Windows Steps:**

Step 1: Click your WeCom profile > 【Manage Enterprise】 to enter the admin console.

![](//blogcdnimg.clewm.net/2023/02/企业微信截图_16753103607837_16753252497253-scaled.jpg?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

Step 2: Locate the CaoLiao QR Code app in 【App Management】.

![](//blogcdnimg.clewm.net/2023/02/企业微信截图_16753255621875_16753259483343.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![](//blogcdnimg.clewm.net/2023/02/企业微信截图_1675325895192_16753259468665.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

Step 3: Click 【Delete Mini Program】 to remove the CaoLiao app and revert.

![](//blogcdnimg.clewm.net/2023/02/windows企业微信回退-03_16753280904983-scaled.jpg?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

**macOS Steps:**

Step 1: Click 【Admin Console】 to enter WeCom backend.

![](//blogcdnimg.clewm.net/2023/01/a02b23e6-0c25-4147-9adb-0f155479dab8-1_16740337527028.jpg?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

Step 2: Locate the CaoLiao QR Code app in 【App Management】.

![](//blogcdnimg.clewm.net/2023/01/82c899cf-dd03-4db9-9d4b-0d0194eea8d2_16740309647020.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

Step 3: Click 【Delete Mini Program】 to remove the CaoLiao app and revert.

![](//blogcdnimg.clewm.net/2023/02/windows企业微信回退-03_16753280904983-scaled.jpg?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 3) How to rebind if the wrong WeCom enterprise was linked

**Rebinding:** Log out, delete the CaoLiao QR Code app via 【WeCom】> 【Admin Console】> 【App Management】, then log back in with your original account. Switch to the correct WeCom enterprise on mobile and rescan to integrate.

## Already Using WeCom Edition

### 1. Usage Issues

#### 1) How to import data from an existing CaoLiao account

Go to 【Workbench】> 【Import Old Account Data】. Only one account's data can be imported once, and it will completely overwrite existing data in the current WeCom project. Ensure the project has no critical data before proceeding. [View import tutorial](https://cli.im/help/69625)

#### 2) How to add/remove members synced from WeCom contacts

Adjust the app's visible range in WeCom admin console to modify synced members. [View tutorial](https://cli.im/help/69665)

#### 3) How to receive notifications in WeCom

When configuring form notifications, select "Any synced contact member" as recipients to deliver alerts directly to WeCom. [View tutorial](https://cli.im/help/51912#1)

**Notification delivery methods:**
- **Synced members**: WeCom notifications
- **Non-synced members with bound Official Account**: WeChat Official Account notifications
- **Non-synced members without bound Official Account**: SMS (only first notification; subsequent notifications require Official Account binding or contact sync)

#### 4) How to restrict QR code access/form filling/dynamic data viewing to WeCom members only

For internal QR codes, use free permission settings to limit access to WeCom colleagues for viewing, form filling, dynamic data, and status updates. [View tutorial](https://cli.im/help/70250#1)

#### 5) What features are included in the 30-day free trial of Flagship Edition? What happens after trial ends?

The trial includes all advanced features: advanced member permissions, advanced form functions, bulk exports, etc. Post-trial, generated codes remain usable, and WeCom-exclusive collaboration features stay free. [View trial benefits](https://cli.im/help/70106)

#### 6) Form data exported from WeCom members shows garbled names. How to fix?

Due to WeCom restrictions, CaoLiao cannot store name information. Have admins/members manually 【Supplement Names】 for proper display. [View tutorial](https://cli.im/help/70178)

#### 7) Why do synced members lack department info? How to resolve?

If you selected individual members (not entire departments) when setting the app's visible range, department info won't sync. Modify contact sync range to include whole departments. [View tutorial](https://cli.im/help/69665)

#### 8) How to change WeCom Edition project admin

Self-service admin transfer is unavailable. Contact [customer support](https://cli.im/api/soboten/commonLink?channel_id=12) for manual processing.

#### 9) How to modify enterprise logo/name shown in backend

Go to desktop admin console: 【Admin Console】- 【Settings】- 【Account Info】

#### 10) How to hide CaoLiao QR Code app in WeCom 【Workbench】 and use our own app instead

Currently unsupported. Future 【Industry-Specific Edition】 users will gain self-built app capabilities to access CaoLiao features via their own enterprise apps in WeCom.

### 2. Purchasing Questions

#### 1) How to upgrade to paid plan

WeCom admins can upgrade via 【WeCom Admin Console】> 【App Management】> 【CaoLiao QR Code】 details page. [View tutorial](https://cli.im/help/69904)

#### 2) Are discounts available?

No discounts for 1-year plans. Multi-year purchases qualify:  
- 2 years: 15% off  
- 3 years: 30% off  
- 5 years: 40% off  
- 10 years: 45% off  

#### 3) Do you accept corporate bank transfers?

WeCom purchases support WeChat Pay/online banking. For corporate transfers, contact [customer support](https://cli.im/api/soboten/commonLink?channel_id=12).

#### 4) How to request a contract

Find the contract request portal at the bottom of 【CaoLiao Pricing Page】. Submit company details to receive the contract within 3 workdays. [Apply now](https://cli.im/user/contract)

#### 5) How to request an invoice

After payment, locate the CaoLiao order in WeCom admin console > 【Order Services】> 【Request Invoice】. [View tutorial](https://cli.im/help/70467)

#### 6) How to renew/upgrade plans

WeCom admins can go to 【Admin Console】> 【App Management】> 【CaoLiao QR Code】> 【Change Payment Plan】. [View tutorial](https://cli.im/help/69904#1)

#### 7) What happens when paid plan expires?

Expired unpaid plans will block access to 【CaoLiao QR Code】 app in WeCom and QR code viewing via WeCom. WeChat operations remain unaffected. [Details](https://cli.im/help/70206)

### 3. WeCom Edition Pricing Adjustments

#### 1) Do all enterprises need to pay WeCom API fees?

Per WeCom's latest policies, all enterprises using CaoLiao's WeCom edition must pay API fees based on visible range size. See announcement: [WeCom Edition Pricing Adjustment Notice](https://cli.im/help/76366)

- **Free Edition users**: 90-day free API access. Payment required post-trial.
- **Advanced feature users**: Must pay standard CaoLiao plan fees (same as website) + WeCom API fees.

#### 2) Which member actions require paid WeCom API licenses?

All WeCom operations require payment:  
- WeCom QR code login to desktop backend  
- Opening mini programs in workbench  
- Viewing QR codes/forms in WeCom  
- Status updates/dynamic data viewing  
- Sharing form data with colleagues  
- Receiving notifications  
- Adding follow-up actions to records  
- etc.  

#### 3) How to check app installation date?

Go to desktop backend: 【Settings】> 【Project Info】> "Creation Date"

#### 4) Can WeCom API licenses be reassigned to other users?

Yes. When member changes occur, active API licenses can be reassigned via:  
- **Active transfer**: 30-day cooldown  
- **Inactive transfer**: No cooldown  
Contact CaoLiao support for reassignment.

#### 5) Are there expiration alerts for WeCom API licenses?

Yes. Free trials/paid licenses show alerts 7 days pre-expiration and block access post-expiration.

![](//blogcdnimg.clewm.net/2022/05/image-1653630851899_16536308526747.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

#### 6) What is "visible range"?

The group of employees who can see the app in WeCom 【Workbench】. "Employee count" = visible range size.