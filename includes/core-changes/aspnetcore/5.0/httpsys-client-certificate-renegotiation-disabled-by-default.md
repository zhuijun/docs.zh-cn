---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325230"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a>HttpSys：默认情况下禁用客户端证书重新协商

默认情况下，重新协商连接和请求客户端证书的选项已禁用。 有关讨论，请参阅问题 [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181)。

#### <a name="version-introduced"></a>引入的版本

ASP.NET Core 5.0

#### <a name="old-behavior"></a>旧行为

可以重新协商连接以请求客户端证书。

#### <a name="new-behavior"></a>新行为

只能在初始连接握手期间请求客户端证书。 有关详细信息，请参阅拉取请求 [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162)。

#### <a name="reason-for-change"></a>更改原因

重新协商导致了许多性能和死锁问题。 它在 HTTP/2 中也不受支持。 有关 ASP.NET Core 3.1 中引入控制此行为的选项时的其他上下文，请参阅问题 [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806)。

#### <a name="recommended-action"></a>建议操作

需要客户端证书的应用应使用 netsh.exe 将 `clientcertnegotiation` 选项设置为 `enabled`。 有关详细信息，请参阅 [netsh http 命令](/windows-server/networking/technologies/netsh/netsh-http)。

如果要仅针对应用的某些部分启用客户端证书，请参阅[可选客户端证书](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)中的指南。

如果需要旧的重新协商行为，请将 `HttpSysOptions.ClientCertificateMethod` 设置为旧值 `ClientCertificateMethod.AllowRenegotiate`。 由于上述原因和链接的指南中的原因，不建议这样做。

#### <a name="category"></a>类别

ASP.NET Core

#### <a name="affected-apis"></a>受影响的 API

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
