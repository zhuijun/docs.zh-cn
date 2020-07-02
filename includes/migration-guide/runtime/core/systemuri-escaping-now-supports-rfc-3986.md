---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619841"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri 转义现在支持 RFC 3986

#### <a name="details"></a>详细信息

.NET Framework 4.5 中对 URI 转义做了更改，可支持 [RFC 3986](https://tools.ietf.org/html/rfc3986)。 具体更改包括：<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> 根据 RFC 3986 转义保留字符。</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> 未转义保留字符。</li><li>如果 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> 遇到无效的转义序列，则它不会引发异常。</li><li>未保留的转义字符已取消转义。</li></ul>

#### <a name="suggestion"></a>建议

<ul><li>更新应用程序，以便在出现无效转义序列时不依赖于要引发 <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName>。 此类序列现在必须直接进行检测。</li><li>同样，预计转义和非转义 URI 和数据字符串在 .NET Framework 4.0 和 .NET Framework 4.5 中可能会有所不同，并且这些字符串不应直接在各种 .NET 版本中进行比较。 而在对这些字符串进行任何比较前，应在单个 .NET 版本中对其进行分析和规范化。</li></ul>

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
