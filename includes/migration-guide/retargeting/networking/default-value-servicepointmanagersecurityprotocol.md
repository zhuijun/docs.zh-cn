---
ms.openlocfilehash: 5c86be598ab6196ecf4da05451c7f22d2be52c12
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614343"
---
### <a name="default-value-of-servicepointmanagersecurityprotocol-is-securityprotocoltypesystemdefault"></a><span data-ttu-id="cba42-101">ServicePointManager.SecurityProtocol 的默认值为 SecurityProtocolType.System.Default</span><span class="sxs-lookup"><span data-stu-id="cba42-101">Default value of ServicePointManager.SecurityProtocol is SecurityProtocolType.System.Default</span></span>

#### <a name="details"></a><span data-ttu-id="cba42-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="cba42-102">Details</span></span>

<span data-ttu-id="cba42-103">从面向 .NET Framework 4.7 的应用开始，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 属性的默认值为 <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="cba42-103">Starting with apps that target the .NET Framework 4.7, the default value of the <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> property is <xref:System.Net.SecurityProtocolType.SystemDefault?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cba42-104">此更改允许基于 SslStream 的 .NET Framework 网络 API（例如 FTP、HTTPS 和 SMTP）从操作系统继承默认安全协议，而不是使用 .NET Framework 定义的硬编码值。</span><span class="sxs-lookup"><span data-stu-id="cba42-104">This change allows .NET Framework networking APIs based on SslStream (such as FTP, HTTPS, and SMTP) to inherit the default security protocols from the operating system instead of using hard-coded values defined by the .NET Framework.</span></span> <span data-ttu-id="cba42-105">默认值因操作系统和系统管理员执行的任何自定义配置而异。</span><span class="sxs-lookup"><span data-stu-id="cba42-105">The default varies by operating system and any custom configuration performed by the system administrator.</span></span> <span data-ttu-id="cba42-106">有关 Windows 操作系统各版本中默认 SChannel 协议的信息，请参阅 [Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-)（TLS/SSL (Schannel SSP) 中的协议）。</span><span class="sxs-lookup"><span data-stu-id="cba42-106">For information on the default SChannel protocol in each version of the Windows operating system, see [Protocols in TLS/SSL (Schannel SSP)](https://docs.microsoft.com/windows/desktop/SecAuthN/protocols-in-tls-ssl--schannel-ssp-).</span></span></p><span data-ttu-id="cba42-107">对于面向 .NET Framework 早期版本的应用程序，<xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 属性的默认值取决于所面向的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="cba42-107">For applications that target an earlier version of the .NET Framework, the default value of the <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> property depends on the version of the .NET Framework targeted.</span></span> <span data-ttu-id="cba42-108">请参阅[“针对 .NET Framework 4.5.2 到 4.6 迁移的重定目标更改”中的“网络”部分](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking)，了解详细信息。</span><span class="sxs-lookup"><span data-stu-id="cba42-108">See the [Networking section of Retargeting Changes for Migration from .NET Framework 4.5.2 to 4.6](~/docs/framework/migration-guide/retargeting/4.5.2-4.6.md#networking) for more information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cba42-109">建议</span><span class="sxs-lookup"><span data-stu-id="cba42-109">Suggestion</span></span>

<span data-ttu-id="cba42-110">此更改会影响面向 .NET Framework 4.7 或更高版本的应用程序。</span><span class="sxs-lookup"><span data-stu-id="cba42-110">This change affects applications that target the .NET Framework 4.7 or later versions.</span></span> <span data-ttu-id="cba42-111">如果希望使用定义协议，而不是依赖于系统默认协议，可显式设置 <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> 属性的值。</span><span class="sxs-lookup"><span data-stu-id="cba42-111">If you prefer to use a defined protocol rather than relying on the system default, you can explicitly set the value of the <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cba42-112">如果不需要此更改，可在应用程序配置文件的 [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) 部分中添加配置设置，从而选择弃用此更改。</span><span class="sxs-lookup"><span data-stu-id="cba42-112">If this change is undesirable, you can opt out of it by adding a configuration setting to the [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file.</span></span> <span data-ttu-id="cba42-113">以下示例显示 `<runtime>` 部分和 `Switch.System.Net.DontEnableSystemDefaultTlsVersions` 选择弃用开关：</span><span class="sxs-lookup"><span data-stu-id="cba42-113">The following example shows both the `<runtime>` section and the `Switch.System.Net.DontEnableSystemDefaultTlsVersions` opt-out switch:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSystemDefaultTlsVersions=true" />
</runtime>
```

| <span data-ttu-id="cba42-114">“属性”</span><span class="sxs-lookup"><span data-stu-id="cba42-114">Name</span></span>    | <span data-ttu-id="cba42-115">“值”</span><span class="sxs-lookup"><span data-stu-id="cba42-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cba42-116">范围</span><span class="sxs-lookup"><span data-stu-id="cba42-116">Scope</span></span>   | <span data-ttu-id="cba42-117">次要</span><span class="sxs-lookup"><span data-stu-id="cba42-117">Minor</span></span>       |
| <span data-ttu-id="cba42-118">Version</span><span class="sxs-lookup"><span data-stu-id="cba42-118">Version</span></span> | <span data-ttu-id="cba42-119">4.7</span><span class="sxs-lookup"><span data-stu-id="cba42-119">4.7</span></span>         |
| <span data-ttu-id="cba42-120">类型</span><span class="sxs-lookup"><span data-stu-id="cba42-120">Type</span></span>    | <span data-ttu-id="cba42-121">重定目标</span><span class="sxs-lookup"><span data-stu-id="cba42-121">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="cba42-122">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="cba42-122">Affected APIs</span></span>

- <xref:System.Net.ServicePointManager.SecurityProtocol?displayProperty=nameWithType>
