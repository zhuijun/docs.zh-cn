---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621135"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a>默认应用域的 TargetFrameworkName 不再默认为 null（如果未设置）

#### <a name="details"></a>详细信息

以前，除非显式设置，否则默认应用域中的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> 为 null。 从 4.6 开始，默认应用域的 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> 属性将具有派生自 TargetFrameworkAttribute 的默认值（如果存在）。 除非显式重写，否则非默认应用域将继续从默认应用域继承 <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName>（在 4.6 中不会默认为 null）。

#### <a name="suggestion"></a>建议

应更新代码，以独立于默认为 null 的 <xref:System.AppDomainSetup.TargetFrameworkName>。 如果需要此属性继续评估为 null，它可显式设为该值。

| “属性”    | 值       |
|:--------|:------------|
| 范围   |边缘|
|Version|4.6|
|类型|运行时

#### <a name="affected-apis"></a>受影响的 API

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
