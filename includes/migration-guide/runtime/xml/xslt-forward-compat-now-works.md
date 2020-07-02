---
ms.openlocfilehash: e3b9711ac66901d69838de4c9f309d086b06fd4d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619910"
---
### <a name="xslt-forward-compat-now-works"></a>XSLT 向前兼容现在有效

#### <a name="details"></a>详细信息

在 .NET Framework 4 中，XSLT 1.0 向前兼容性具有以下问题：<ul><li>如果其版本设置为 2.0，并且分析器遇到无法识别的 XSLT 1.0 构造，则无法加载样式表。</li><li>如果将样式表版本设置为 1.1，则 <code>xsl:sort</code> 构造无法对数据进行排序。</li></ul>在 .NET Framework 4.5 中，这些问题已修复，并且 XSLT 1.0 向前兼容性模式可正常工作。

#### <a name="suggestion"></a>建议

大多数应用应该不受影响，但由于遵循 xsl:sort，某些情况下数据排序将会不同。 如果在 1.1 样式表中使用 <code>xsl:sort</code>，请确定应用不依赖于未排序数据。 如果应用依赖于 4.0 排序行为，请从样式表删除 <code>xsl:sort</code>。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Xml.Xsl.XslCompiledTransform?displayProperty=nameWithType></li></ul>|
