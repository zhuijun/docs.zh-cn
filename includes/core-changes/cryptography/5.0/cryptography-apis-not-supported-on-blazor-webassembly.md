---
ms.openlocfilehash: 6c2aff4abf558307d599ff7533c82286e037bc71
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406138"
---
### <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a>Blazor WebAssembly 不支持的 System.Security.Cryptography API

在浏览器上运行时，<xref:System.Security.Cryptography> API 在运行时引发 <xref:System.PlatformNotSupportedException>。

#### <a name="change-description"></a>更改描述

在以前的 .NET 版本中，大多数 <xref:System.Security.Cryptography> API 不可用于 Blazor WebAssembly 应用。 从 .NET 5.0 开始，Blazor WebAssembly 应用面向整个 .NET 5 API 外围应用，但由于浏览器沙盒约束，并非所有 .NET 5 API 都受支持。 在 .NET 5.0 及更高版本中，不支持的 <xref:System.Security.Cryptography> API 在 WebAssembly 上运行时引发 <xref:System.PlatformNotSupportedException>。

> [!TIP]
> 生成支持浏览器平台的项目时，[平台兼容性分析器](../../../../docs/core/compatibility/code-analysis.md#ca1416-platform-compatibility)将标记对受影响的 API 的任何调用。 默认情况下，此分析器在 .NET 5.0 及更高版本的应用中运行。

#### <a name="reason-for-change"></a>更改原因

Microsoft 无法将 OpenSSL 作为依赖项提供在 Blazor WebAssembly 配置中。 通过尝试与浏览器的 `SubtleCrypto` API 集成来尝试解决此问题。 遗憾的是，这需要大量的 API 更改，因此难以集成。

#### <a name="version-introduced"></a>引入的版本

5.0 RC1

#### <a name="recommended-action"></a>建议操作

目前没有建议任何好的解决方法。

#### <a name="category"></a>类别

- ASP.NET Core
- 密码

#### <a name="affected-apis"></a>受影响的 API

除以下 API 之外的所有 <xref:System.Security.Cryptography?displayProperty=fullName> API：

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

#### Affected APIs

- `T:System.Security.Cryptography`

-->
