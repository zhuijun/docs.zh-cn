---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619906"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a>XmlSchemaException 现在正确设置行位置

#### <a name="details"></a>详细信息

如果将 <xref:System.Xml.Linq.LoadOptions.SetLineInfo> 值传递给 Load 方法并发生验证错误，则 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 属性现在包含行信息。

#### <a name="suggestion"></a>建议

应该更新假设不设置 <xref:System.Xml.Schema.XmlSchemaException.LineNumber> 和 <xref:System.Xml.Schema.XmlSchemaException.LinePosition> 的异常处理代码，因为这些属性将会在加载 XML 且使用 SetLineInfo 的时候正确设置。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
