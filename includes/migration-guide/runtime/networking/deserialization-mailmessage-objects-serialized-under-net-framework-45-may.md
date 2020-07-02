---
ms.openlocfilehash: ad953a1562db407c04d7860c60eb5964fe6fe2ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619857"
---
### <a name="deserialization-of-mailmessage-objects-serialized-under-the-net-framework-45-may-fail"></a>在 .NET Framework 4.5 下序列化的 MailMessage 对象进行反序列化可能会失败

#### <a name="details"></a>详细信息

从 .NET Framework 4.5 开始，<xref:System.Web.Mail.MailMessage> 对象可以包含非 ASCII 字符。 在 .NET Framework 4 中，仅支持 ASCII 字符。 包含非 ASCII 字符并在 .NET Framework 4.5 或更高版本下序列化的 <xref:System.Web.Mail.MailMessage> 对象不能在 .NET Framework 4 下进行反序列化。

#### <a name="suggestion"></a>建议

请确保在反序列化 <xref:System.Web.Mail.MailMessage> 对象时，代码会提供异常处理。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Web.Mail.MailMessage?displayProperty=nameWithType></li></ul>|
