---
ms.openlocfilehash: 17fde81f9734966692c9f41d2213f8682dedea46
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497267"
---
### <a name="contractinvariant-or-contractrequirestexception-do-not-consider-stringisnullorempty-to-be-pure"></a>Contract.Invariant 或 Contract.Requires\<TException> 不认为 String.IsNullOrEmpty 为 pure

#### <a name="details"></a>详细信息

对于面向 .NET Framework 4.6.1 的应用，如果 <xref:System.Diagnostics.Contracts.Contract.Invariant%2A?displayProperty=nameWithType> 的不变协定或 <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType)> 的前提条件协定调用 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，则重写器会发出编译器警告 CC1036：&quot;在方法中没有 [Pure] 的情况下检测到对方法“System.String.IsNullOrWhteSpace(System.String)”的调用。&quot;这是编译器警告，不是编译器错误。

#### <a name="suggestion"></a>建议

此行为在 [GitHub 问题 #339](https://github.com/Microsoft/CodeContracts/issues/339) 中已得到解决。 要去除此警告，可以从 [GitHub](https://github.com/Microsoft/CodeContracts/blob/master/README.md) 下载并编译代码协定工具的已更新版本的源代码。 可在页面底部找到下载信息。

| “属性”    | “值”       |
|:--------|:------------|
| 范围   |次要|
|Version|4.6.1|
|类型|运行时|

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)?displayProperty=nameWithType>
- <xref:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Diagnostics.Contracts.Contract.Invariant(System.Boolean)`
- `M:System.Diagnostics.Contracts.Contract.Requires(System.Boolean)`

-->
