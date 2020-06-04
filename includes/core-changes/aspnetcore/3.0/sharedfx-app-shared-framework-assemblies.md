---
ms.openlocfilehash: d598d8d3203e804e5e935c3564b0053f9fc2e9a6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84145001"
---
### <a name="shared-framework-assemblies-removed-from-microsoftaspnetcoreapp"></a><span data-ttu-id="e4362-101">共享框架：从 Microsoft.AspNetCore.App 中删除了程序集</span><span class="sxs-lookup"><span data-stu-id="e4362-101">Shared framework: Assemblies removed from Microsoft.AspNetCore.App</span></span>

<span data-ttu-id="e4362-102">从 ASP.NET Core 3.0 开始，ASP.NET Core 共享框架 (`Microsoft.AspNetCore.App`) 只包含 Microsoft 完全开发、支持和可服务的第一方程序集。</span><span class="sxs-lookup"><span data-stu-id="e4362-102">Starting in ASP.NET Core 3.0, the ASP.NET Core shared framework (`Microsoft.AspNetCore.App`) only contains first-party assemblies that are fully developed, supported, and serviceable by Microsoft.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e4362-103">更改描述</span><span class="sxs-lookup"><span data-stu-id="e4362-103">Change description</span></span>

<span data-ttu-id="e4362-104">将这一更改视为重新定义 ASP.NET Core“平台”的边界。</span><span class="sxs-lookup"><span data-stu-id="e4362-104">Think of the change as the redefining of boundaries for the ASP.NET Core "platform."</span></span> <span data-ttu-id="e4362-105">[任何人都可通过 GitHub 生成共享框架的源代码](https://github.com/dotnet/source-build)，共享框架将继续为应用提供 .NET Core 共享框架的现有优势。</span><span class="sxs-lookup"><span data-stu-id="e4362-105">The shared framework will be [source-buildable by anybody via GitHub](https://github.com/dotnet/source-build) and will continue to offer the existing benefits of .NET Core shared frameworks to your apps.</span></span> <span data-ttu-id="e4362-106">一些优势包括部署大小更小、集中修补和启动时间更快。</span><span class="sxs-lookup"><span data-stu-id="e4362-106">Some benefits include smaller deployment size, centralized patching, and faster startup time.</span></span>

<span data-ttu-id="e4362-107">作为此更改的一部分，`Microsoft.AspNetCore.App` 中引入了一些值得注意的重大更改。</span><span class="sxs-lookup"><span data-stu-id="e4362-107">As part of the change, some notable breaking changes are introduced in `Microsoft.AspNetCore.App`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e4362-108">引入的版本</span><span class="sxs-lookup"><span data-stu-id="e4362-108">Version introduced</span></span>

<span data-ttu-id="e4362-109">3.0</span><span class="sxs-lookup"><span data-stu-id="e4362-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e4362-110">旧行为</span><span class="sxs-lookup"><span data-stu-id="e4362-110">Old behavior</span></span>

<span data-ttu-id="e4362-111">项目通过项目文件中的 `<PackageReference>` 元素引用了 `Microsoft.AspNetCore.App`。</span><span class="sxs-lookup"><span data-stu-id="e4362-111">Projects referenced `Microsoft.AspNetCore.App` via a `<PackageReference>` element in the project file.</span></span>

<span data-ttu-id="e4362-112">此外，`Microsoft.AspNetCore.App` 包含以下子组件：</span><span class="sxs-lookup"><span data-stu-id="e4362-112">Additionally, `Microsoft.AspNetCore.App` contained the following subcomponents:</span></span>

- <span data-ttu-id="e4362-113">Json.NET (`Newtonsoft.Json`)</span><span class="sxs-lookup"><span data-stu-id="e4362-113">Json.NET (`Newtonsoft.Json`)</span></span>
- <span data-ttu-id="e4362-114">Entity Framework Core（以 `Microsoft.EntityFrameworkCore.` 为前缀的程序集）</span><span class="sxs-lookup"><span data-stu-id="e4362-114">Entity Framework Core (assemblies prefixed with `Microsoft.EntityFrameworkCore.`)</span></span>
- <span data-ttu-id="e4362-115">Roslyn (`Microsoft.CodeAnalysis`)</span><span class="sxs-lookup"><span data-stu-id="e4362-115">Roslyn (`Microsoft.CodeAnalysis`)</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e4362-116">新行为</span><span class="sxs-lookup"><span data-stu-id="e4362-116">New behavior</span></span>

<span data-ttu-id="e4362-117">对 `Microsoft.AspNetCore.App` 的引用不再需要项目文件中的 `<PackageReference>` 元素。</span><span class="sxs-lookup"><span data-stu-id="e4362-117">A reference to `Microsoft.AspNetCore.App` no longer requires a `<PackageReference>` element in the project file.</span></span> <span data-ttu-id="e4362-118">.NET Core SDK 支持名为 `<FrameworkReference>` 的新元素，该元素将替代对 `<PackageReference>` 的使用。</span><span class="sxs-lookup"><span data-stu-id="e4362-118">The .NET Core SDK supports a new element called `<FrameworkReference>`, which replaces the use of `<PackageReference>`.</span></span>

<span data-ttu-id="e4362-119">有关详细信息，请参阅 [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612)。</span><span class="sxs-lookup"><span data-stu-id="e4362-119">For more information, see [dotnet/aspnetcore#3612](https://github.com/dotnet/aspnetcore/issues/3612).</span></span>

<span data-ttu-id="e4362-120">Entity Framework Core 作为 NuGet 包提供。</span><span class="sxs-lookup"><span data-stu-id="e4362-120">Entity Framework Core ships as NuGet packages.</span></span> <span data-ttu-id="e4362-121">此更改将使随附模型与 .NET 上的所有其他数据访问库保持一致。</span><span class="sxs-lookup"><span data-stu-id="e4362-121">This change aligns the shipping model with all other data access libraries on .NET.</span></span> <span data-ttu-id="e4362-122">它在支持各种 .NET 平台的同时，为 Entity Framework Core 提供最简单的途径来继续创新。</span><span class="sxs-lookup"><span data-stu-id="e4362-122">It provides Entity Framework Core the simplest path to continue innovating while supporting the various .NET platforms.</span></span> <span data-ttu-id="e4362-123">将 Entity Framework Core 移出共享框架不会影响其作为 Microsoft 开发、支持和可服务的库的状态。</span><span class="sxs-lookup"><span data-stu-id="e4362-123">The move of Entity Framework Core out of the shared framework has no impact on its status as a Microsoft-developed, supported, and serviceable library.</span></span> <span data-ttu-id="e4362-124">[.NET Core 支持策略](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)继续支持此功能。</span><span class="sxs-lookup"><span data-stu-id="e4362-124">The [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) continues to cover it.</span></span>

<span data-ttu-id="e4362-125">Json.NET 和 Entity Framework Core 可继续使用 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="e4362-125">Json.NET and Entity Framework Core continue to work with ASP.NET Core.</span></span> <span data-ttu-id="e4362-126">但是，它们不会包含在共享框架中。</span><span class="sxs-lookup"><span data-stu-id="e4362-126">They won't, however, be included in the shared framework.</span></span>

<span data-ttu-id="e4362-127">有关详细信息，请参阅 [.NET Core 3.0 中 JSON 的未来](https://github.com/dotnet/announcements/issues/90)。</span><span class="sxs-lookup"><span data-stu-id="e4362-127">For more information, see [The future of JSON in .NET Core 3.0](https://github.com/dotnet/announcements/issues/90).</span></span> <span data-ttu-id="e4362-128">另请参阅[从共享框架中删除的二进制文件的完整列表](https://github.com/dotnet/aspnetcore/issues/3755)。</span><span class="sxs-lookup"><span data-stu-id="e4362-128">Also see [the complete list of binaries](https://github.com/dotnet/aspnetcore/issues/3755) removed from the shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e4362-129">更改原因</span><span class="sxs-lookup"><span data-stu-id="e4362-129">Reason for change</span></span>

<span data-ttu-id="e4362-130">此更改简化了 `Microsoft.AspNetCore.App` 的使用，并减少了 NuGet 包与共享框架之间的重复。</span><span class="sxs-lookup"><span data-stu-id="e4362-130">This change simplifies the consumption of `Microsoft.AspNetCore.App` and reduces the duplication between NuGet packages and shared frameworks.</span></span>

<span data-ttu-id="e4362-131">有关此更改动机的详细信息，请参阅[博客文章](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/)。</span><span class="sxs-lookup"><span data-stu-id="e4362-131">For more information on the motivation for this change, see [this blog post](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e4362-132">建议操作</span><span class="sxs-lookup"><span data-stu-id="e4362-132">Recommended action</span></span>

<span data-ttu-id="e4362-133">项目不需要使用 `Microsoft.AspNetCore.App` 中的程序集作为 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="e4362-133">It won't be necessary for projects to consume assemblies in `Microsoft.AspNetCore.App` as NuGet packages.</span></span> <span data-ttu-id="e4362-134">为了简化 ASP.NET Core 共享框架的定位和使用，已不再生成自 ASP.NET Core 1.0 以来提供的许多 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="e4362-134">To simplify the targeting and usage of the ASP.NET Core shared framework, many NuGet packages shipped since ASP.NET Core 1.0 are no longer produced.</span></span> <span data-ttu-id="e4362-135">通过将 `<FrameworkReference>` 用于 `Microsoft.AspNetCore.App`，应用仍可使用这些包提供的 API。</span><span class="sxs-lookup"><span data-stu-id="e4362-135">The APIs those packages provide are still available to apps by using a `<FrameworkReference>` to `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="e4362-136">常见的 API 示例包括 Kestrel、MVC 和 Razor。</span><span class="sxs-lookup"><span data-stu-id="e4362-136">Common API examples include Kestrel, MVC, and Razor.</span></span>

<span data-ttu-id="e4362-137">此更改不适用于通过 ASP.NET Core 2.x 中的 `Microsoft.AspNetCore.App` 引用的所有二进制文件。</span><span class="sxs-lookup"><span data-stu-id="e4362-137">This change doesn't apply to all binaries referenced via `Microsoft.AspNetCore.App` in ASP.NET Core 2.x.</span></span> <span data-ttu-id="e4362-138">值得注意的例外包括：</span><span class="sxs-lookup"><span data-stu-id="e4362-138">Notable exceptions include:</span></span>

- <span data-ttu-id="e4362-139">继续以 .NET Standard 为目标的 `Microsoft.Extensions` 库将以 NuGet 包的形式提供（请参阅 <https://github.com/dotnet/extensions>）。</span><span class="sxs-lookup"><span data-stu-id="e4362-139">`Microsoft.Extensions` libraries that continue to target .NET Standard will be available as NuGet packages (see <https://github.com/dotnet/extensions>).</span></span>
- <span data-ttu-id="e4362-140">不属于 `Microsoft.AspNetCore.App` 的 ASP.NET Core 团队生成的 API。</span><span class="sxs-lookup"><span data-stu-id="e4362-140">APIs produced by the ASP.NET Core team that aren't part of `Microsoft.AspNetCore.App`.</span></span> <span data-ttu-id="e4362-141">例如，以下组件以 NuGet 包的形式提供：</span><span class="sxs-lookup"><span data-stu-id="e4362-141">For example, the following components are available as NuGet packages:</span></span>
  - <span data-ttu-id="e4362-142">Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="e4362-142">Entity Framework Core</span></span>
  - <span data-ttu-id="e4362-143">提供第三方集成的 API</span><span class="sxs-lookup"><span data-stu-id="e4362-143">APIs that provide third-party integration</span></span>
  - <span data-ttu-id="e4362-144">实验性功能</span><span class="sxs-lookup"><span data-stu-id="e4362-144">Experimental features</span></span>
  - <span data-ttu-id="e4362-145">包含无法[满足共享框架中的要求](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)的依赖项的 API</span><span class="sxs-lookup"><span data-stu-id="e4362-145">APIs with dependencies that couldn't [fulfill the requirements to be in the shared framework](https://github.com/dotnet/aspnetcore/blob/4e44e5bcbedd961cc0d4f6b846699c7c494f5597/docs/SharedFramework.md)</span></span>
- <span data-ttu-id="e4362-146">用于保留对 Json.NET 的支持的 MVC 扩展。</span><span class="sxs-lookup"><span data-stu-id="e4362-146">Extensions to MVC that maintain support for Json.NET.</span></span> <span data-ttu-id="e4362-147">API 将作为 NuGet 包提供，以支持使用 Json.NET 和 MVC。</span><span class="sxs-lookup"><span data-stu-id="e4362-147">An API will be provided as a NuGet package to support using Json.NET and MVC.</span></span>
- <span data-ttu-id="e4362-148">SignalR .NET 客户端将继续支持 .NET Standard 并作为 NuGet 包提供。</span><span class="sxs-lookup"><span data-stu-id="e4362-148">The SignalR .NET client will continue to support .NET Standard and ship as a NuGet package.</span></span> <span data-ttu-id="e4362-149">它可用于许多 .NET 运行时，例如 Xamarin 和 UWP。</span><span class="sxs-lookup"><span data-stu-id="e4362-149">It's intended for use on many .NET runtimes, such as Xamarin and UWP.</span></span>

<span data-ttu-id="e4362-150">有关详细信息，请参阅[停止为 3.0 中的共享框架程序集生成包](https://github.com/dotnet/aspnetcore/issues/3756)。</span><span class="sxs-lookup"><span data-stu-id="e4362-150">For more information, see [Stop producing packages for shared framework assemblies in 3.0](https://github.com/dotnet/aspnetcore/issues/3756).</span></span> <span data-ttu-id="e4362-151">有关讨论，请参阅 [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757)。</span><span class="sxs-lookup"><span data-stu-id="e4362-151">For discussion, see [dotnet/aspnetcore#3757](https://github.com/dotnet/aspnetcore/issues/3757).</span></span>

#### <a name="category"></a><span data-ttu-id="e4362-152">类别</span><span class="sxs-lookup"><span data-stu-id="e4362-152">Category</span></span>

<span data-ttu-id="e4362-153">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e4362-153">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e4362-154">受影响的 API</span><span class="sxs-lookup"><span data-stu-id="e4362-154">Affected APIs</span></span>

- <xref:Microsoft.CodeAnalysis?displayProperty=nameWithType>
- <xref:Microsoft.EntityFrameworkCore?displayProperty=nameWithType>

<!--

#### Affected APIs

- `N:Microsoft.CodeAnalysis`
- `N:Microsoft.EntityFrameworkCore`

-->
