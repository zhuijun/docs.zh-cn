---
ms.openlocfilehash: 7766a59131fffe2b436c15a5ff58e67001be7941
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065093"
---
### <a name="cryptostreamdispose-transforms-final-block-only-when-writing"></a>CryptoStream.Dispose 仅在写入时转换最终块

用于完成 `CryptoStream` 操作的 <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=nameWithType> 方法不再尝试在读取时转换最终块。

#### <a name="change-description"></a>更改说明

在以前的 .NET 版本中，如果用户在 <xref:System.Security.Cryptography.CryptoStreamMode.Read> 模式下使用 <xref:System.Security.Cryptography.CryptoStream> 时执行了不完整的读取操作，<xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 方法可能会引发异常（例如，使用带有填充的 AES 时）。 引发异常是因为尝试转换最终块，但数据不完整。

在 .NET Core 3.0 及更高版本中，<xref:System.Security.Cryptography.CryptoStream.Dispose%2A> 不再尝试在读取时转换最终块，这会允许执行不完整的读取操作。

#### <a name="reason-for-change"></a>更改原因

取消网络操作后，此更改将允许从加密流中进行不完整的读取操作，而无需捕获异常。

#### <a name="version-introduced"></a>引入的版本

3.0

#### <a name="recommended-action"></a>建议操作

大多数应用都不会受到此更改的影响。

如果应用程序先前在读取不完整的情况下捕获到异常，你可以删除相应 `catch` 块。
如果应用在哈希方案中使用了最终块的转换，则可能需要确保在释放所有流之前先对其进行读取。

#### <a name="category"></a>类别

密码

#### <a name="affected-apis"></a>受影响的 API

- <xref:System.Security.Cryptography.CryptoStream.Dispose%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.CryptoStream.Dispose`

-->
