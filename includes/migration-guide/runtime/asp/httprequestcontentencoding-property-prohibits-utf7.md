---
ms.openlocfilehash: 7d3568fef933758c40e47cefa86c24d31d4119fc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619816"
---
### <a name="httprequestcontentencoding-property-prohibits-utf7"></a>HttpRequest.ContentEncoding 属性禁止使用 UTF7

#### <a name="details"></a>详细信息

从 .NET Framework 4.5 开始，<xref:System.Web.HttpRequest?displayProperty=fullName> 正文禁止使用 UTF-7 编码。 在某些情况下，取决于传入的 UTF-7 数据的应用程序数据将不会正确解码。

#### <a name="suggestion"></a>建议

理想情况下，应更新应用程序，使其在 <xref:System.Web.HttpRequest?displayProperty=fullName> 中不使用 UTF-7 编码。 或者，可以使用 [appSettings](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) 元素的 <code>aspnet:AllowUtf7RequestContentEncoding</code> 属性还原旧行为。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Web.HttpRequest.ContentEncoding?displayProperty=nameWithType></li></ul>|
