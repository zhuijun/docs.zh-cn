---
ms.openlocfilehash: 87dc93ece10eaedbfbabddb5f857d0bcd12e05c4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615610"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a><span data-ttu-id="807ac-101">System.Net.ServicePointManager 和 System.Net.Security.SslStream 中仅支持 Tls 1.0、1.1 和 1.2 协议</span><span class="sxs-lookup"><span data-stu-id="807ac-101">Only Tls 1.0, 1.1 and 1.2 protocols supported in System.Net.ServicePointManager and System.Net.Security.SslStream</span></span>

#### <a name="details"></a><span data-ttu-id="807ac-102">详细信息</span><span class="sxs-lookup"><span data-stu-id="807ac-102">Details</span></span>

<span data-ttu-id="807ac-103">从 .NET Framework 4.6 开始，<xref:System.Net.ServicePointManager> 和 <xref:System.Net.Security.SslStream> 类仅可使用以下三种协议之一：Tls1.0、Tls1.1 或 Tls1.2。</span><span class="sxs-lookup"><span data-stu-id="807ac-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager> and <xref:System.Net.Security.SslStream> classes are only allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="807ac-104">不支持 SSL3.0 协议和 RC4 密码。</span><span class="sxs-lookup"><span data-stu-id="807ac-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="807ac-105">建议</span><span class="sxs-lookup"><span data-stu-id="807ac-105">Suggestion</span></span>

<span data-ttu-id="807ac-106">建议的缓解操作是将服务器端应用升级到 Tls1.0、Tls1.1 或 Tls1.2。</span><span class="sxs-lookup"><span data-stu-id="807ac-106">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls1.2.</span></span> <span data-ttu-id="807ac-107">如果这不可行或者如果客户端应用被中断，则可以使用 <xref:System.AppContext?displayProperty=fullName> 类并采用如两种方式中的一种来选择退出此功能：</span><span class="sxs-lookup"><span data-stu-id="807ac-107">If this is not feasible, or if client apps are broken, the <xref:System.AppContext?displayProperty=fullName> class can be used to opt out of this feature in either of two ways:</span></span>

- <span data-ttu-id="807ac-108">以编程方式在 <xref:System.AppContext?displayProperty=fullName> 上设置兼容性开关，如[此处](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)所述。</span><span class="sxs-lookup"><span data-stu-id="807ac-108">By programmatically setting compat switches on the <xref:System.AppContext?displayProperty=fullName>, as explained [here](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</span></span>
- <span data-ttu-id="807ac-109">在 app.config 文件的 `<runtime>` 部分中添加下面的代码行：</span><span class="sxs-lookup"><span data-stu-id="807ac-109">By adding the following line to the `<runtime>` section of the app.config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>
```

| <span data-ttu-id="807ac-110">“属性”</span><span class="sxs-lookup"><span data-stu-id="807ac-110">Name</span></span>    | <span data-ttu-id="807ac-111">值</span><span class="sxs-lookup"><span data-stu-id="807ac-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="807ac-112">范围</span><span class="sxs-lookup"><span data-stu-id="807ac-112">Scope</span></span>   | <span data-ttu-id="807ac-113">次要</span><span class="sxs-lookup"><span data-stu-id="807ac-113">Minor</span></span>       |
| <span data-ttu-id="807ac-114">Version</span><span class="sxs-lookup"><span data-stu-id="807ac-114">Version</span></span> | <span data-ttu-id="807ac-115">4.6</span><span class="sxs-lookup"><span data-stu-id="807ac-115">4.6</span></span>         |
| <span data-ttu-id="807ac-116">类型</span><span class="sxs-lookup"><span data-stu-id="807ac-116">Type</span></span>    | <span data-ttu-id="807ac-117">重定目标</span><span class="sxs-lookup"><span data-stu-id="807ac-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="807ac-118">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="807ac-118">Affected APIs</span></span>

- <xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType>
- <xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType>
