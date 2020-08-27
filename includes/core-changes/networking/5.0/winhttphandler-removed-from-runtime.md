---
ms.openlocfilehash: 115cd6be935ae12a1293f948a0f899c6c3ff0d78
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608483"
---
### <a name="winhttphandler-removed-from-net-runtime"></a>已从 .NET 运行时中删除 WinHttpHandler

`WinHttpHandler` 类已从 System.Net.Http.dll 程序集删除。 它现在仅作为带外 (OOB) [NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)提供。

#### <a name="version-introduced"></a>引入的版本

5.0

#### <a name="change-description"></a>更改描述

在以前的 .NET 版本中，<xref:System.Net.Http.WinHttpHandler> 类作为核心 .NET 库的一部分提供。 从 .NET 5.0 开始，<xref:System.Net.Http.WinHttpHandler> 类仅作为单独安装的 [NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)提供。

#### <a name="recommended-action"></a>建议操作

安装 [System.Net.Http.WinHttpHandler NuGet 包](https://www.nuget.org/packages/System.Net.Http.WinHttpHandler/)。 或者，如果不需要特定于 WinHTTP 的功能，请改用 <xref:System.Net.Http.SocketsHttpHandler>。

#### <a name="category"></a>类别

网络

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Net.Http.WinHttpHandler?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Net.Http.WinHttpHandler`

-->
