---
ms.openlocfilehash: 26a001ec2009a1a66dd9038b9bd3a42d7bcefb73
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619839"
---
### <a name="missing-target-framework-moniker-results-in-40-behavior"></a>在 4.0 行为中缺少了目标框架名字对象结果

#### <a name="details"></a>详细信息

未在程序集级别应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 的应用程序将通过使用 .NET Framework 4.0 的语义 (quirks) 自动运行。 为了确保高质量，建议所有二进制文件均通过 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName> 显式属性化，以指示用于生成它们的 .NET Framework 版本。 请注意，在项目文件中使用目标框架名字对象将使 MSBuild 自动应用 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>。

#### <a name="suggestion"></a>建议

应通过以下方法提供 <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=fullName>：将该属性直接添加到程序集，或者在[项目文件中或通过 Visual Studio 的项目属性 GUI](https://devblogs.microsoft.com/visualstudio/visual-studio-managed-multi-targeting-part-1-concepts-target-framework-moniker-target-framework/) 指定目标框架。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |主要|
|Version|4.5|
|类型|运行时|
