---
ms.openlocfilehash: d00b8ecaa61b358e062d85a2b68ca8a95cada442
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803237"
---
### <a name="kestrel-configuration-changes-at-run-time-detected-by-default"></a><span data-ttu-id="75d30-101">Kestrel：默认检测运行时的配置更改</span><span class="sxs-lookup"><span data-stu-id="75d30-101">Kestrel: Configuration changes at run time detected by default</span></span>

<span data-ttu-id="75d30-102">Kestrel 现在会在运行时响应对项目的 `IConfiguration` 实例 `Kestrel` 部分（例如 appsettings.json\*\*）的更改。</span><span class="sxs-lookup"><span data-stu-id="75d30-102">Kestrel now reacts to changes made to the `Kestrel` section of the project's `IConfiguration` instance (for example, *appsettings.json*) at run time.</span></span> <span data-ttu-id="75d30-103">若要详细了解如何使用 appsettings.json 配置 Kestrel**，请参阅[终结点配置](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration)中的 appsettings.json 示例**。</span><span class="sxs-lookup"><span data-stu-id="75d30-103">To learn more about how to configure Kestrel using *appsettings.json*, see the *appsettings.json* example in [Endpoint configuration](/aspnet/core/fundamentals/servers/kestrel#endpoint-configuration).</span></span>

<span data-ttu-id="75d30-104">Kestrel 将根据需要绑定、取消绑定和重新绑定终结点，以响应这些配置更改。</span><span class="sxs-lookup"><span data-stu-id="75d30-104">Kestrel will bind, unbind, and rebind endpoints as necessary to react to these configuration changes.</span></span>

<span data-ttu-id="75d30-105">有关讨论，请参阅 [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807)。</span><span class="sxs-lookup"><span data-stu-id="75d30-105">For discussion, see issue [dotnet/aspnetcore#22807](https://github.com/dotnet/aspnetcore/issues/22807).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="75d30-106">引入的版本</span><span class="sxs-lookup"><span data-stu-id="75d30-106">Version introduced</span></span>

<span data-ttu-id="75d30-107">5.0 预览版 7</span><span class="sxs-lookup"><span data-stu-id="75d30-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="75d30-108">旧行为</span><span class="sxs-lookup"><span data-stu-id="75d30-108">Old behavior</span></span>

<span data-ttu-id="75d30-109">在 ASP.NET Core 5.0 预览版 6 之前，Kestrel 不支持在运行时更改配置。</span><span class="sxs-lookup"><span data-stu-id="75d30-109">Before ASP.NET Core 5.0 Preview 6, Kestrel didn't support changing configuration at run time.</span></span>

<span data-ttu-id="75d30-110">在 ASP.NET Core 5.0 预览版 6 中，可以选择在运行时响应配置更改（这是现在的默认行为）。</span><span class="sxs-lookup"><span data-stu-id="75d30-110">In ASP.NET Core 5.0 Preview 6, you could opt into the now-default behavior of reacting to configuration changes at run time.</span></span> <span data-ttu-id="75d30-111">要选择加入，需要手动绑定 Kestrel 的配置：</span><span class="sxs-lookup"><span data-stu-id="75d30-111">Opting in required binding Kestrel's configuration manually:</span></span>

```csharp
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
                webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                {
                    kestrelOptions.Configure(
                        builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: true);
                });

                webBuilder.UseStartup<Startup>();
            });
}
```

#### <a name="new-behavior"></a><span data-ttu-id="75d30-112">新行为</span><span class="sxs-lookup"><span data-stu-id="75d30-112">New behavior</span></span>

<span data-ttu-id="75d30-113">默认情况下，Kestrel 会在运行时响应配置更改。</span><span class="sxs-lookup"><span data-stu-id="75d30-113">Kestrel reacts to configuration changes at run time by default.</span></span> <span data-ttu-id="75d30-114">为支持该更改，<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> 默认使用 `reloadOnChange: true` 调用 `KestrelServerOptions.Configure(IConfiguration, bool)`。</span><span class="sxs-lookup"><span data-stu-id="75d30-114">To support that change, <xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A> calls `KestrelServerOptions.Configure(IConfiguration, bool)` with `reloadOnChange: true` by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="75d30-115">更改原因</span><span class="sxs-lookup"><span data-stu-id="75d30-115">Reason for change</span></span>

<span data-ttu-id="75d30-116">此项更改是为了在运行时支持终结点重新配置，而无需完全重启服务器。</span><span class="sxs-lookup"><span data-stu-id="75d30-116">The change was made to support endpoint reconfiguration at run time without completely restarting the server.</span></span> <span data-ttu-id="75d30-117">与完全重启服务器不同，未更改的终结点甚至不会暂时解除绑定。</span><span class="sxs-lookup"><span data-stu-id="75d30-117">Unlike with a full server restart, unchanged endpoints aren't unbound even temporarily.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="75d30-118">建议操作</span><span class="sxs-lookup"><span data-stu-id="75d30-118">Recommended action</span></span>

* <span data-ttu-id="75d30-119">在大多数情况下，Kestrel 的默认配置部分在运行时不会更改，这种更改不会有任何影响，也不需要执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="75d30-119">For most scenarios in which Kestrel's default configuration section doesn't change at run time, this change has no impact and no action is needed.</span></span>
* <span data-ttu-id="75d30-120">对于 Kestrel 的默认配置部分在运行时发生更改并且 Kestrel 应响应这种更改的情况，这是现在的默认行为。</span><span class="sxs-lookup"><span data-stu-id="75d30-120">For scenarios in which Kestrel's default configuration section does change at run time and Kestrel should react to it, this is now the default behavior.</span></span>
* <span data-ttu-id="75d30-121">对于 Kestrel 的默认配置部分在运行时更改并且 Kestrel 不应对其做出反应的情况，你可以选择退出，如下所示：</span><span class="sxs-lookup"><span data-stu-id="75d30-121">For scenarios in which Kestrel's default configuration section changes at run time and Kestrel shouldn't react to it, you can opt out as follows:</span></span>

    ```csharp
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
                    webBuilder.UseKestrel((builderContext, kestrelOptions) =>
                    {
                        kestrelOptions.Configure(
                            builderContext.Configuration.GetSection("Kestrel"), reloadOnChange: false);
                    });

                    webBuilder.UseStartup<Startup>();
                });
    }
    ```

<span data-ttu-id="75d30-122">**注意：**</span><span class="sxs-lookup"><span data-stu-id="75d30-122">**Notes:**</span></span>

<span data-ttu-id="75d30-123">此更改不会修改 `KestrelServerOptions.Configure(IConfiguration)` 重载的行为，它仍默认为 `reloadOnChange: false` 行为。</span><span class="sxs-lookup"><span data-stu-id="75d30-123">This change doesn't modify the behavior of the `KestrelServerOptions.Configure(IConfiguration)` overload, which still defaults to the `reloadOnChange: false` behavior.</span></span>

<span data-ttu-id="75d30-124">另外，请务必确保配置源支持重载。</span><span class="sxs-lookup"><span data-stu-id="75d30-124">It's also important to make sure the configuration source supports reloading.</span></span> <span data-ttu-id="75d30-125">对于 JSON 源，将通过调用 `AddJsonFile(path, reloadOnChange: true)` 配置重载。</span><span class="sxs-lookup"><span data-stu-id="75d30-125">For JSON sources, reloading is configured by calling `AddJsonFile(path, reloadOnChange: true)`.</span></span> <span data-ttu-id="75d30-126">默认情况下，已为 appsettings.json 和 appsettings.{Environment}.json 配置重载\*\* \*\*。</span><span class="sxs-lookup"><span data-stu-id="75d30-126">Reloading is already configured by default for *appsettings.json* and *appsettings.{Environment}.json*.</span></span>

#### <a name="category"></a><span data-ttu-id="75d30-127">类别</span><span class="sxs-lookup"><span data-stu-id="75d30-127">Category</span></span>

<span data-ttu-id="75d30-128">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="75d30-128">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="75d30-129">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="75d30-129">Affected APIs</span></span>

<xref:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults%2A?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`Overload:Microsoft.Extensions.Hosting.GenericHostBuilderExtensions.ConfigureWebHostDefaults`

-->
