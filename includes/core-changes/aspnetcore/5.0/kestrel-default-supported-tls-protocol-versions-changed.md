---
ms.openlocfilehash: 3244a36808fb687663241e704d08775ea5c96720
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803257"
---
### <a name="kestrel-default-supported-tls-protocol-versions-changed"></a><span data-ttu-id="2ad2f-101">Kestrel：默认支持的 TLS 协议版本已更改</span><span class="sxs-lookup"><span data-stu-id="2ad2f-101">Kestrel: Default supported TLS protocol versions changed</span></span>

<span data-ttu-id="2ad2f-102">Kestrel 现在使用系统默认的 TLS 协议版本，而不是像以前一样将连接限制于 TLS 1.1 和 TLS 1.2 协议。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-102">Kestrel now uses the system default TLS protocol versions rather than restricting connections to the TLS 1.1 and TLS 1.2 protocols like it did previously.</span></span>

<span data-ttu-id="2ad2f-103">此更改允许：</span><span class="sxs-lookup"><span data-stu-id="2ad2f-103">This change allows:</span></span>

* <span data-ttu-id="2ad2f-104">在支持 TLS 1.3 的环境中默认使用它。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-104">TLS 1.3 to be used by default in environments that support it.</span></span>
* <span data-ttu-id="2ad2f-105">在某些环境（例如默认的 Windows Server 2016）中使用 TLS 1.0，但这通常[不理想](/security/engineering/solving-tls1-problem)。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-105">TLS 1.0 to be used in some environments (such as Windows Server 2016 by default), which is usually [not desirable](/security/engineering/solving-tls1-problem).</span></span>

<span data-ttu-id="2ad2f-106">有关讨论，请参阅 [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563)。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-106">For discussion, see issue [dotnet/aspnetcore#22563](https://github.com/dotnet/aspnetcore/issues/22563).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ad2f-107">引入的版本</span><span class="sxs-lookup"><span data-stu-id="2ad2f-107">Version introduced</span></span>

<span data-ttu-id="2ad2f-108">5.0 预览版 6</span><span class="sxs-lookup"><span data-stu-id="2ad2f-108">5.0 Preview 6</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2ad2f-109">旧行为</span><span class="sxs-lookup"><span data-stu-id="2ad2f-109">Old behavior</span></span>

<span data-ttu-id="2ad2f-110">Kestrel 过去默认要求连接使用 TLS 1.1 或 TLS 1.2。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-110">Kestrel required that connections use TLS 1.1 or TLS 1.2 by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2ad2f-111">新行为</span><span class="sxs-lookup"><span data-stu-id="2ad2f-111">New behavior</span></span>

<span data-ttu-id="2ad2f-112">Kestrel 允许操作系统选择要使用的最佳协议，并阻止不安全的协议。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-112">Kestrel allows the operating system to choose the best protocol to use and to block insecure protocols.</span></span> <span data-ttu-id="2ad2f-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> 现在默认为 `SslProtocols.None`，而不是 `SslProtocols.Tls12 | SslProtocols.Tls11`。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-113"><xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType> now defaults to `SslProtocols.None` instead of `SslProtocols.Tls12 | SslProtocols.Tls11`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2ad2f-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="2ad2f-114">Reason for change</span></span>

<span data-ttu-id="2ad2f-115">进行此项更改是为了在 TLS 1.3 和未来的 TLS 版本可用时默认支持它们。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-115">The change was made to support TLS 1.3 and future TLS versions by default as they become available.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ad2f-116">建议操作</span><span class="sxs-lookup"><span data-stu-id="2ad2f-116">Recommended action</span></span>

<span data-ttu-id="2ad2f-117">应使用新的默认协议，除非应用有特定原因而不能使用它们。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-117">Unless your app has a specific reason not to, you should use the new defaults.</span></span> <span data-ttu-id="2ad2f-118">验证你的系统是否配置为仅允许安全协议。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-118">Verify your system is configured to allow only secure protocols.</span></span>

<span data-ttu-id="2ad2f-119">若要禁用旧协议，请执行以下操作之一：</span><span class="sxs-lookup"><span data-stu-id="2ad2f-119">To disable older protocols, take one of the following actions:</span></span>

* <span data-ttu-id="2ad2f-120">参照 [Windows 说明](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry)，在系统范围禁用旧的协议（如 TLS 1.0）。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-120">Disable older protocols, such as TLS 1.0, system-wide with the [Windows instructions](/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).</span></span> <span data-ttu-id="2ad2f-121">目前所有 Windows 版本上都默认启用该协议。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-121">It's currently enabled by default on all Windows versions.</span></span>
* <span data-ttu-id="2ad2f-122">在代码中手动选择要支持的协议，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2ad2f-122">Manually select which protocols you want to support in code as follows:</span></span>

    ```csharp
    using System.Security.Authentication;
    using Microsoft.AspNetCore.Hosting;
    using Microsoft.Extensions.Hosting;

    public class Program
    {
        public static void Main(string[] args) =>
            CreateHostBuilder(args).Build().Run();

        public static IHostBuilder CreateHostBuilder(string[] args) =>
            Host.CreateDefaultBuilder(args)
                .ConfigureWebHostDefaults(webBuilder =>
                {
                    webBuilder.UseKestrel(kestrelOptions =>
                    {
                        kestrelOptions.ConfigureHttpsDefaults(httpsOptions =>
                        {
                            httpsOptions.SslProtocols = SslProtocols.Tls12 | SslProtocols.Tls13;
                        });
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="2ad2f-123">遗憾的是，没有用于排除特定协议的 API。</span><span class="sxs-lookup"><span data-stu-id="2ad2f-123">Unfortunately, there's no API to exclude specific protocols.</span></span>

#### <a name="category"></a><span data-ttu-id="2ad2f-124">类别</span><span class="sxs-lookup"><span data-stu-id="2ad2f-124">Category</span></span>

<span data-ttu-id="2ad2f-125">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2ad2f-125">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ad2f-126">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="2ad2f-126">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`P:Microsoft.AspNetCore.Server.Kestrel.Https.HttpsConnectionAdapterOptions.SslProtocols`

-->
