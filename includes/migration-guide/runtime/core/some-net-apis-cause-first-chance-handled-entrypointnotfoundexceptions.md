---
ms.openlocfilehash: ed526095459a48aa37b585dfed79cc12b9fb9e56
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621941"
---
### <a name="some-net-apis-cause-first-chance-handled-entrypointnotfoundexceptions"></a>一些 .NET API 会导致最可能的（已处理）EntryPointNotFoundExceptions

#### <a name="details"></a>详细信息

在 .NET Framework 4.5 中，少量 .NET 方法开始引发最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName>。 这些异常在 .NET Framework 内进行处理，但可能会中断不希望出现最可能的异常的测试自动化。 启用 HighVersionLie 后，这些相同的 API 会中断一些 ApiVerifier 方案。

#### <a name="suggestion"></a>建议

升级到 .NET Framework 4.5.1 可避免此 bug 出现。 还可以更新测试自动化以便不中断对最可能的 <xref:System.EntryPointNotFoundException?displayProperty=fullName> 的操作。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.5|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String)?displayProperty=nameWithType></li><li><xref:System.Diagnostics.Debug.Assert(System.Boolean,System.String,System.String,System.Object[])?displayProperty=nameWithType></li><li><xref:System.Xml.Serialization.XmlSerializer.%23ctor(System.Type)></li></ul>|
