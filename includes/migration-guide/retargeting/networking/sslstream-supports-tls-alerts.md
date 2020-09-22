---
ms.openlocfilehash: 5b566dd89801caff7a253abc2fb62c5fd79591f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606890"
---
### <a name="sslstream-supports-tls-alerts"></a><span data-ttu-id="b6b99-101">SslStream 支持 TLS 警报</span><span class="sxs-lookup"><span data-stu-id="b6b99-101">SslStream supports TLS Alerts</span></span>

#### <a name="details"></a><span data-ttu-id="b6b99-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="b6b99-102">Details</span></span>

<span data-ttu-id="b6b99-103">TLS 握手失败后，第一个 I/O 读取/写入操作将引发带有内部 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 异常的 <xref:System.IO.IOException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="b6b99-103">After a failed TLS handshake, an <xref:System.IO.IOException?displayProperty=fullName> with an inner <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> exception will be thrown by the first I/O Read/Write operation.</span></span> <span data-ttu-id="b6b99-104">可以使用 [TLS 和 SSL 警报的 Schannel 错误代码](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts)将 <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> 的 <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> 代码从远程参与方映射到 TLS 警报。有关详细信息，请参阅 [RFC 2246：第 7.2.2 节错误警报](https://tools.ietf.org/html/rfc2246#section-7.2.2)。</span><span class="sxs-lookup"><span data-stu-id="b6b99-104">The <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=fullName> code for the <xref:System.ComponentModel.Win32Exception?displayProperty=fullName> can be mapped to the TLS Alert from the remote party using the [Schannel error codes for TLS and SSL alerts](/windows/desktop/SecAuthN/schannel-error-codes-for-tls-and-ssl-alerts).For more information, see [RFC 2246: Section 7.2.2 Error alerts](https://tools.ietf.org/html/rfc2246#section-7.2.2).</span></span> <br/><span data-ttu-id="b6b99-105">.NET Framework 4.6.2 及更早版本中的行为是：如果另一方握手失败然后立即拒绝连接，则传输通道（通常为 TCP 连接）将在写入或读取时超时。</span><span class="sxs-lookup"><span data-stu-id="b6b99-105">The behavior in .NET Framework 4.6.2 and earlier is that the transport channel (usually TCP connection) will timeout during either Write or Read if the other party failed the handshake and immediately afterwards rejected the connection.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b6b99-106">建议</span><span class="sxs-lookup"><span data-stu-id="b6b99-106">Suggestion</span></span>

<span data-ttu-id="b6b99-107">调用网络 I/O API（例如 <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)>）的应用程序应处理 <xref:System.IO.IOException> 或 <xref:System.TimeoutException?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="b6b99-107">Applications calling network I/O APIs such as <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)> should handle <xref:System.IO.IOException> or <xref:System.TimeoutException?displayProperty=fullName>.</span></span><br/><span data-ttu-id="b6b99-108">从 .NET Framework 4.7 开始，TLS 警报功能将默认启用。</span><span class="sxs-lookup"><span data-stu-id="b6b99-108">The TLS Alerts feature is enabled by default starting with .NET Framework 4.7.</span></span> <span data-ttu-id="b6b99-109">在 .NET Framework 4.7 或更高系统上运行的面向 .NET Framework 4.0 到 4.6.2 版本的应用程序将禁用该功能以保留兼容性。</span><span class="sxs-lookup"><span data-stu-id="b6b99-109">Applications targeting versions of the .NET Framework from 4.0 through 4.6.2 running on a .NET Framework 4.7 or higher system will have the feature disabled to preserve compatibility.</span></span> <br/><span data-ttu-id="b6b99-110">以下配置 API 用于为在 .NET Framework 4.7 或更高版本上运行的 .NET Framework 4.6 和更高版本应用程序启用或禁用该功能。</span><span class="sxs-lookup"><span data-stu-id="b6b99-110">The following configuration API is available to enable or disable the feature for .NET Framework 4.6 and later applications running on .NET Framework 4.7 or later.</span></span>

- <span data-ttu-id="b6b99-111">以编程方式： 必须是应用程序执行的第一件事，因为 ServicePointManager 将只初始化一次：</span><span class="sxs-lookup"><span data-stu-id="b6b99-111">Programmatically:   Must be the very first thing the application does since ServicePointManager will initialize only once:</span></span>

    ```csharp
    AppContext.SetSwitch("TestSwitch.LocalAppContext.DisableCaching", true);

    // Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2.
    AppContext.SetSwitch("Switch.System.Net.DontEnableTlsAlerts", true);
    ```

- <span data-ttu-id="b6b99-112">AppConfig：</span><span class="sxs-lookup"><span data-stu-id="b6b99-112">AppConfig:</span></span>

    ```xml
    <runtime>
      <AppContextSwitchOverrides value="Switch.System.Net.DontEnableTlsAlerts=true"/>
      <!-- Set to 'false' to enable the feature in .NET Framework 4.6 - 4.6.2. -->
    </runtime>
    ```

- <span data-ttu-id="b6b99-113">注册表项（计算机全局）： 将值设置为 `false` 以在 .NET Framework 4.6 - 4.6.2 中启用该功能。</span><span class="sxs-lookup"><span data-stu-id="b6b99-113">Registry key (machine global):   Set the Value to `false` to enable the feature in .NET Framework 4.6 - 4.6.2.</span></span>

    ```ini
    Key: HKLM\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts
    - Type: String
    - Value: "true"
    ```

| <span data-ttu-id="b6b99-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="b6b99-114">Name</span></span>    | <span data-ttu-id="b6b99-115">“值”</span><span class="sxs-lookup"><span data-stu-id="b6b99-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b6b99-116">范围</span><span class="sxs-lookup"><span data-stu-id="b6b99-116">Scope</span></span>   | <span data-ttu-id="b6b99-117">边缘</span><span class="sxs-lookup"><span data-stu-id="b6b99-117">Edge</span></span>        |
| <span data-ttu-id="b6b99-118">Version</span><span class="sxs-lookup"><span data-stu-id="b6b99-118">Version</span></span> | <span data-ttu-id="b6b99-119">4.7</span><span class="sxs-lookup"><span data-stu-id="b6b99-119">4.7</span></span>         |
| <span data-ttu-id="b6b99-120">类型</span><span class="sxs-lookup"><span data-stu-id="b6b99-120">Type</span></span>    | <span data-ttu-id="b6b99-121">重定目标</span><span class="sxs-lookup"><span data-stu-id="b6b99-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="b6b99-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="b6b99-122">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.WebRequest?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Http?displayProperty=nameWithType>
