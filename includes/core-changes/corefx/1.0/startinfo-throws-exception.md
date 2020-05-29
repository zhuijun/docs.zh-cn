---
ms.openlocfilehash: 92c03328414410d56a2ff5f445639757367b42c7
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420418"
---
### <a name="processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start"></a>Process.StartInfo 对未启动的进程引发 InvalidOperationException

对于你的代码未启动的进程，读取其 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 属性会引发 <xref:System.InvalidOperationException>。

#### <a name="change-description"></a>更改描述

在 .NET Framework 中，访问你的代码未启动的进程的 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 属性将返回虚拟 <xref:System.Diagnostics.ProcessStartInfo> 对象。 虚拟对象包含其所有属性（<xref:System.Diagnostics.ProcessStartInfo.EnvironmentVariables> 除外）的默认值。

从 .NET Core 1.0 开始，如果读取你未启动的进程的 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 属性（即通过调用 <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType>），则会引发 <xref:System.InvalidOperationException>。

#### <a name="version-introduced"></a>引入的版本

1.0

#### <a name="recommended-action"></a>建议操作

不要访问你的代码未启动的进程的 <xref:System.Diagnostics.Process.StartInfo?displayProperty=nameWithType> 属性。 例如，不要读取 <xref:System.Diagnostics.Process.GetProcesses%2A?displayProperty=nameWithType> 返回的进程的此属性。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Diagnostics.Process.StartInfo?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Diagnostics.Process.StartInfo`

-->
