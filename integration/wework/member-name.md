# 完善成员的补充姓名

集成企业微信后，会同步可见范围内的通讯录成员信息。但受企业微信限制，草料平台无法获取姓名信息后储存下来使用，就会造成企业微信成员填写的表单数据，在导出时，填表人、姓名信息不能正确显示，会显示成一串如"wodkFjCwAAkjJTzgDHDcbf"的字符。

需要管理员在草料平台完善成员的【补充姓名】，或由成员自己在手机端进行完善，才会正确显示表单记录中的填表人和姓名信息。（该设置不涉及非企业微信成员）

## 管理员在电脑端完善

### 1. 打开- 设置- 成员管理

在【组织架构】，找到没有补充姓名的成员，进行编辑完善。

![管理员完善成员姓名](//blogcdnimg.clewm.net/2022/03/image-1646981802011_16469818048706.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 单个修改（点击编辑）

![单个修改成员姓名](//blogcdnimg.clewm.net/2022/03/image-1646981817195_16469818197986.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

:::info 注意
补充姓名最好是成员的真实姓名，与通讯录显示的姓名一致，不然在后台看到的姓名跟导出数据中的姓名会不一样。
:::

### 3. 批量完善

点击【批量完善】，下载更新文档，在文档中填写补充姓名，再将文档上传，就能完成批量完善姓名。

![批量完善步骤1](//blogcdnimg.clewm.net/2022/03/image-1646981839979_16469818431078.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![批量完善步骤2](//blogcdnimg.clewm.net/2022/03/image-1646981852736_16469818555681.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

![批量完善步骤3](//blogcdnimg.clewm.net/2022/03/image-1646982091475_16469820940667.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 成员在手机端自行完善

如果需要完善的成员数量过多，可让成员自己在手机端企业微信进行完善，减轻管理员的工作量。

![成员自行完善](//blogcdnimg.clewm.net/2022/01/image-1643521180994_16435211810568.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

## 未完善的影响

### 1. 导出表单记录

表格中的填写人和姓名信息是一串代码。

![导出表单记录](//blogcdnimg.clewm.net/2021/12/image-1640589995044_16405899953509.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 2. 导出记录PDF

PDF中的填写人和姓名信息也是一串代码

![导出PDF](//blogcdnimg.clewm.net/2021/12/image-1640587235226_16405872359546.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 3. 图片水印

图片水印上填写人和姓名信息也是一串代码

![图片水印](//blogcdnimg.clewm.net/2021/12/image-1640588506190_16405885097638.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 4. API接口

通过API接口获取的表单数据，填写人和姓名信息也是一串代码

![API接口](//blogcdnimg.clewm.net/2021/12/image-1640589887877_16405898881435.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)

### 5. 查看二维码小程序时，填表人都显示为企业微信用户

付费用户使用微信扫码默认的打开方式是 查看二维码。（企业微信扫码不受影响，免费版用户打打开的是草料小程序也不受影响。）

![小程序显示](//blogcdnimg.clewm.net/2021/12/image-1640672319769_16406723201335.png?x-oss-process=image/auto-orient,1/quality,q_50/format,jpg)