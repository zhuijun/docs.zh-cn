---
ms.openlocfilehash: ccd056f23d26e6cce4cc691542784792bffe9fc6
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558164"
---
### <a name="environmentosversion-returns-the-correct-operating-system-version"></a>Environment.OSVersion 返回正确的操作系统版本

<xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回操作系统 (OS) 的实际版本，而不是为应用程序兼容性而选择的 OS。

#### <a name="change-description"></a>更改描述

在以前的 .NET 版本中，当应用程序在 Windows 兼容模式下运行时，<xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回的 OS 版本可能不正确。 有关详细信息，请参阅 [GetVersionExA 函数备注](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。

从 .NET 5.0 开始，<xref:System.Environment.OSVersion?displayProperty=nameWithType> 返回操作系统的实际版本。

#### <a name="reason-for-change"></a>更改原因

此属性的用户希望它返回操作系统的实际版本。 大多数 .NET 应用并未在其应用程序清单中指定其支持的版本，因此会从 dotnet 主机获取默认的支持版本。 因此，兼容性填充码对于正在运行的应用没有什么意义。 当 Windows 发布新版本时，如果较旧的 dotnet 主机仍在使用，这些应用可能会收到错误的 OS 版本。 返回实际版本更符合开发人员对此 API 的期望。

#### <a name="version-introduced"></a>引入的版本

5.0

#### <a name="recommended-action"></a>建议操作

查看和测试使用 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 的任何代码，以确保其行为符合预期。

#### <a name="category"></a>类别

Core .NET 库

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Environment.OSVersion`

-->
