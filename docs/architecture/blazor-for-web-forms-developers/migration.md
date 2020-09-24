---
title: 从 ASP.NET Web 窗体迁移到 Blazor
description: 了解如何将现有的 ASP.NET Web 窗体应用程序迁移到 Blazor 。
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: 853358fbf534ee7501412259c61efe054b4757a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161199"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a><span data-ttu-id="b7e5a-103">从 ASP.NET Web 窗体迁移到 Blazor</span><span class="sxs-lookup"><span data-stu-id="b7e5a-103">Migrate from ASP.NET Web Forms to Blazor</span></span>

<span data-ttu-id="b7e5a-104">将基本代码从 ASP.NET Web 窗体迁移到 Blazor 是一项需要规划的耗时的任务。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-104">Migrating a code base from ASP.NET Web Forms to Blazor is a time-consuming task that requires planning.</span></span> <span data-ttu-id="b7e5a-105">本章概述了该过程。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-105">This chapter outlines the process.</span></span> <span data-ttu-id="b7e5a-106">可以减轻转换的问题是确保应用程序符合 *N 层* 体系结构，在这种情况下，应用模型 (在这种情况下，Web 窗体) 独立于业务逻辑。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-106">Something that can ease the transition is to ensure the app adheres to an *N-tier* architecture, wherein the app model (in this case, Web Forms) is separate from the business logic.</span></span> <span data-ttu-id="b7e5a-107">这种逻辑分离可以清楚地确定需要移动到 .NET Core 和的内容 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-107">This logical separation of layers makes it clear what needs to move to .NET Core and Blazor.</span></span>

<span data-ttu-id="b7e5a-108">在此示例中，将使用 [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) 上提供的 eShop 应用。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-108">For this example, the eShop app available on [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) is used.</span></span> <span data-ttu-id="b7e5a-109">eShop 是一种目录服务，它通过表单条目和验证提供 CRUD 功能。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-109">eShop is a catalog service that provides CRUD capabilities via form entry and validation.</span></span>

<span data-ttu-id="b7e5a-110">为什么应将正在运行的应用程序迁移到 Blazor ？</span><span class="sxs-lookup"><span data-stu-id="b7e5a-110">Why should a working app be migrated to Blazor?</span></span> <span data-ttu-id="b7e5a-111">很多时候都不需要。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-111">Many times, there's no need.</span></span> <span data-ttu-id="b7e5a-112">多年来，ASP.NET Web 窗体将继续受到支持。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-112">ASP.NET Web Forms will continue to be supported for many years.</span></span> <span data-ttu-id="b7e5a-113">但是， Blazor 只支持对已迁移的应用程序提供的许多功能。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-113">However, many of the features that Blazor provides are only supported on a migrated app.</span></span> <span data-ttu-id="b7e5a-114">此类功能包括：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-114">Such features include:</span></span>

- <span data-ttu-id="b7e5a-115">框架中的性能改进，例如 `Span<T>`</span><span class="sxs-lookup"><span data-stu-id="b7e5a-115">Performance improvements in the framework such as `Span<T>`</span></span>
- <span data-ttu-id="b7e5a-116">能够运行方式 WebAssembly</span><span class="sxs-lookup"><span data-stu-id="b7e5a-116">Ability to run as WebAssembly</span></span>
- <span data-ttu-id="b7e5a-117">Linux 和 macOS 的跨平台支持</span><span class="sxs-lookup"><span data-stu-id="b7e5a-117">Cross-platform support for Linux and macOS</span></span>
- <span data-ttu-id="b7e5a-118">应用本地部署或共享框架部署，不影响其他应用</span><span class="sxs-lookup"><span data-stu-id="b7e5a-118">App-local deployment or shared framework deployment without impacting other apps</span></span>

<span data-ttu-id="b7e5a-119">如果这些或其他新功能非常引人注目，则在迁移应用程序时可能有价值。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-119">If these or other new features are compelling enough, there may be value in migrating the app.</span></span> <span data-ttu-id="b7e5a-120">迁移可以采用不同的形状;它可以是整个应用，或者只是需要更改的某些终结点。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-120">The migration can take different shapes; it can be the entire app, or only certain endpoints that require the changes.</span></span> <span data-ttu-id="b7e5a-121">迁移决策最终基于开发人员解决的业务问题。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-121">The decision to migrate is ultimately based on the business problems to be solved by the developer.</span></span>

## <a name="server-side-versus-client-side-hosting"></a><span data-ttu-id="b7e5a-122">服务器端与客户端宿主</span><span class="sxs-lookup"><span data-stu-id="b7e5a-122">Server-side versus client-side hosting</span></span>

<span data-ttu-id="b7e5a-123">如 " [托管模型](hosting-models.md) " 一章中所述， Blazor 可通过两种不同的方式承载应用：服务器端和客户端。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-123">As described in the [hosting models](hosting-models.md) chapter, a Blazor app can be hosted in two different ways: server-side and client-side.</span></span> <span data-ttu-id="b7e5a-124">服务器端模型使用 ASP.NET Core SignalR 连接来管理 DOM 更新，同时在服务器上运行任何实际代码。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-124">The server-side model uses ASP.NET Core SignalR connections to manage the DOM updates while running any actual code on the server.</span></span> <span data-ttu-id="b7e5a-125">客户端模型 WebAssembly 在浏览器中运行，并且不需要服务器连接。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-125">The client-side model runs as WebAssembly within a browser and requires no server connections.</span></span> <span data-ttu-id="b7e5a-126">有很多差异可能会影响最适合特定应用的应用：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-126">There are a number of differences that may affect which is best for a specific app:</span></span>

- <span data-ttu-id="b7e5a-127">运行方式 WebAssembly 仍处于开发阶段，可能不支持所有功能 (如当前时间线程) </span><span class="sxs-lookup"><span data-stu-id="b7e5a-127">Running as WebAssembly is still in development and may not support all features (such as threading) at the current time</span></span>
- <span data-ttu-id="b7e5a-128">客户端和服务器之间的对话通信可能会导致服务器端模式发生延迟问题</span><span class="sxs-lookup"><span data-stu-id="b7e5a-128">Chatty communication between the client and server may cause latency issues in server-side mode</span></span>
- <span data-ttu-id="b7e5a-129">对数据库和内部或受保护的服务的访问需要单独的服务和客户端托管</span><span class="sxs-lookup"><span data-stu-id="b7e5a-129">Access to databases and internal or protected services require a separate service with client-side hosting</span></span>

<span data-ttu-id="b7e5a-130">在撰写本文时，服务器端模型更加类似于 Web 窗体。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-130">At the time of writing, the server-side model more closely resembles Web Forms.</span></span> <span data-ttu-id="b7e5a-131">本章节中的大部分重点介绍服务器端托管模型，因为它是生产就绪的模型。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-131">Most of this chapter focuses on the server-side hosting model, as it's production-ready.</span></span>

## <a name="create-a-new-project"></a><span data-ttu-id="b7e5a-132">创建新项目</span><span class="sxs-lookup"><span data-stu-id="b7e5a-132">Create a new project</span></span>

<span data-ttu-id="b7e5a-133">此初始迁移步骤是创建一个新项目。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-133">This initial migration step is to create a new project.</span></span> <span data-ttu-id="b7e5a-134">此项目类型基于 .NET Core 的 SDK 样式项目，并简化了以前的项目格式中使用的很多样板。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-134">This project type is based on the SDK style projects of .NET Core and simplifies much of the boilerplate that was used in previous project formats.</span></span> <span data-ttu-id="b7e5a-135">有关更多详细信息，请参阅 " [项目结构](project-structure.md)" 一章。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-135">For more detail, please see the chapter on [Project Structure](project-structure.md).</span></span>

<span data-ttu-id="b7e5a-136">创建该项目后，安装上一个项目中使用的库。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-136">Once the project has been created, install the libraries that were used in the previous project.</span></span> <span data-ttu-id="b7e5a-137">在较旧的 Web 窗体项目中，可能已使用 *packages.config* 文件列出了所需的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-137">In older Web Forms projects, you may have used the *packages.config* file to list the required NuGet packages.</span></span> <span data-ttu-id="b7e5a-138">在新的 SDK 样式项目中， *packages.config* 已替换为 `<PackageReference>` 项目文件中的元素。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-138">In the new SDK-style project, *packages.config* has been replaced with `<PackageReference>` elements in the project file.</span></span> <span data-ttu-id="b7e5a-139">此方法的优点是所有依赖项都以可传递的方式安装。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-139">A benefit to this approach is that all dependencies are installed transitively.</span></span> <span data-ttu-id="b7e5a-140">你只列出你关注的顶级依赖关系。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-140">You only list the top-level dependencies you care about.</span></span>

<span data-ttu-id="b7e5a-141">你使用的许多依赖项都适用于 .NET Core，包括实体框架6和 log4net。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-141">Many of the dependencies you're using are available for .NET Core, including Entity Framework 6 and log4net.</span></span> <span data-ttu-id="b7e5a-142">如果没有可用的 .NET Core 或 .NET Standard 版本，则通常可以使用 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-142">If there's no .NET Core or .NET Standard version available, the .NET Framework version can often be used.</span></span> <span data-ttu-id="b7e5a-143">你的里程可能会有所不同。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-143">Your mileage may vary.</span></span> <span data-ttu-id="b7e5a-144">任何在 .NET Core 中不可用的 API 都会导致运行时错误。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-144">Any API used that isn't available in .NET Core causes a runtime error.</span></span> <span data-ttu-id="b7e5a-145">Visual Studio 会通知你此类包。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-145">Visual Studio notifies you of such packages.</span></span> <span data-ttu-id="b7e5a-146">**解决方案资源管理器**中项目的 "**引用**" 节点上将显示一个黄色图标。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-146">A yellow icon appears on the project's **References** node in **Solution Explorer**.</span></span>

<span data-ttu-id="b7e5a-147">在 Blazor 基于的 eShop 项目中，可以看到已安装的包。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-147">In the Blazor-based eShop project, you can see the packages that are installed.</span></span> <span data-ttu-id="b7e5a-148">以前， *packages.config* 文件列出了项目中使用的每个包，导致文件的长度几乎为50行。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-148">Previously, the *packages.config* file listed every package used in the project, resulting in a file almost 50 lines long.</span></span> <span data-ttu-id="b7e5a-149">*packages.config*的代码段如下：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-149">A snippet of *packages.config* is:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

<span data-ttu-id="b7e5a-150">`<packages>`元素包含所有必要的依赖项。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-150">The `<packages>` element includes all necessary dependencies.</span></span> <span data-ttu-id="b7e5a-151">很难确定包含了哪些包，因为你需要它们。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-151">It's difficult to identify which of these packages are included because you require them.</span></span> <span data-ttu-id="b7e5a-152">某些 `<package>` 元素只是为了满足所需的依赖项需求而列出。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-152">Some `<package>` elements are listed simply to satisfy the needs of dependencies you require.</span></span>

<span data-ttu-id="b7e5a-153">Blazor项目在项目文件的元素中列出所需的依赖项 `<ItemGroup>` ：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-153">The Blazor project lists the dependencies you require within an `<ItemGroup>` element in the project file:</span></span>

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

<span data-ttu-id="b7e5a-154">一个 NuGet 包可简化 Web 窗体开发人员的生活，这是 [Windows 兼容性包](../../core/porting/windows-compat-pack.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-154">One NuGet package that simplifies the life of Web Forms developers is the [Windows Compatibility Pack](../../core/porting/windows-compat-pack.md).</span></span> <span data-ttu-id="b7e5a-155">尽管 .NET Core 是跨平台的，但某些功能只能在 Windows 上使用。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-155">Although .NET Core is cross-platform, some features are only available on Windows.</span></span> <span data-ttu-id="b7e5a-156">Windows 特定功能通过安装兼容包提供。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-156">Windows-specific features are made available by installing the compatibility pack.</span></span> <span data-ttu-id="b7e5a-157">此类功能的示例包括注册表、WMI 和目录服务。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-157">Examples of such features include the Registry, WMI, and Directory Services.</span></span> <span data-ttu-id="b7e5a-158">该包增加了 20000 Api，并激活了许多你可能已经熟悉的服务。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-158">The package adds around 20,000 APIs and activates many services with which you may already be familiar.</span></span> <span data-ttu-id="b7e5a-159">EShop 项目不需要兼容包;但是，如果你的项目使用特定于 Windows 的功能，则包会使迁移工作更加轻松。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-159">The eShop project doesn't require the compatibility pack; but if your projects use Windows-specific features, the package eases the migration efforts.</span></span>

## <a name="enable-startup-process"></a><span data-ttu-id="b7e5a-160">启用启动过程</span><span class="sxs-lookup"><span data-stu-id="b7e5a-160">Enable startup process</span></span>

<span data-ttu-id="b7e5a-161">对于 Blazor 其他 ASP.NET Core 服务，的启动过程已从 Web 窗体更改并遵循类似的设置。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-161">The startup process for Blazor has changed from Web Forms and follows a similar setup for other ASP.NET Core services.</span></span> <span data-ttu-id="b7e5a-162">托管服务器端时， Blazor 组件作为正常 ASP.NET Core 应用的一部分运行。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-162">When hosted server-side, Blazor components are run as part of a normal ASP.NET Core app.</span></span> <span data-ttu-id="b7e5a-163">当使用在浏览器中承载时 WebAssembly ， Blazor 组件将使用类似的承载模型。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-163">When hosted in the browser with WebAssembly, Blazor components use a similar hosting model.</span></span> <span data-ttu-id="b7e5a-164">不同之处在于，组件是作为独立的服务从任何后端进程运行的。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-164">The difference is the components are run as a separate service from any of the backend processes.</span></span> <span data-ttu-id="b7e5a-165">无论采用哪种方式，启动都是类似的。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-165">Either way, the startup is similar.</span></span>

<span data-ttu-id="b7e5a-166">*Global.asax.cs*文件是 Web 窗体项目的默认启动页。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-166">The *Global.asax.cs* file is the default startup page for Web Forms projects.</span></span> <span data-ttu-id="b7e5a-167">在 eShop 项目中，此文件 (IoC) 容器配置控制反转，并处理应用或请求的各种生命周期事件。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-167">In the eShop project, this file configures the Inversion of Control (IoC) container and handles the various lifecycle events of the app or request.</span></span> <span data-ttu-id="b7e5a-168">其中一些事件通过中间件 (（如) ）进行处理 `Application_BeginRequest` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-168">Some of these events are handled with middleware (such as `Application_BeginRequest`).</span></span> <span data-ttu-id="b7e5a-169">其他事件需要通过依赖关系注入 (DI) 来覆盖特定服务。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-169">Other events require the overriding of specific services via dependency injection (DI).</span></span>

<span data-ttu-id="b7e5a-170">例如，eShop 的 *Global.asax.cs* 文件包含以下代码：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-170">By way of example, the *Global.asax.cs* file for eShop, contains the following code:</span></span>

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

<span data-ttu-id="b7e5a-171">前面的文件成为 `Startup` 服务器端的类 Blazor ：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-171">The preceding file becomes the `Startup` class in server-side Blazor:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

<span data-ttu-id="b7e5a-172">你可能会注意到，Web 窗体中的一项重大更改是 DI 的突出。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-172">One significant change you may notice from Web Forms is the prominence of DI.</span></span> <span data-ttu-id="b7e5a-173">DI 是 ASP.NET Core 设计中的一个指导原则。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-173">DI has been a guiding principle in the ASP.NET Core design.</span></span> <span data-ttu-id="b7e5a-174">它支持 ASP.NET Core 框架的几乎所有方面的自定义。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-174">It supports customization of almost all aspects of the ASP.NET Core framework.</span></span> <span data-ttu-id="b7e5a-175">甚至可以在许多方案中使用内置服务提供程序。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-175">There's even a built-in service provider that can be used for many scenarios.</span></span> <span data-ttu-id="b7e5a-176">如果需要进行更多的自定义，则很多社区项目都可能支持此功能。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-176">If more customization is required, it can be supported by the many community projects.</span></span> <span data-ttu-id="b7e5a-177">例如，你可以继续执行第三方 DI 库投资。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-177">For example, you can carry forward your third-party DI library investment.</span></span>

<span data-ttu-id="b7e5a-178">在原始 eShop 应用程序中，有一些配置用于会话管理。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-178">In the original eShop app, there's some configuration for session management.</span></span> <span data-ttu-id="b7e5a-179">由于服务器端 Blazor 使用 ASP.NET Core SignalR 进行通信，因此不支持会话状态，因为连接可能独立于 HTTP 上下文。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-179">Since server-side Blazor uses ASP.NET Core SignalR for communication, session state isn't supported as the connections may occur independent of an HTTP context.</span></span> <span data-ttu-id="b7e5a-180">使用会话状态的应用需要先重新架构，然后才能作为 Blazor 应用运行。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-180">An app that uses session state requires rearchitecting before running as a Blazor app.</span></span>

<span data-ttu-id="b7e5a-181">有关应用程序启动的详细信息，请参阅 [应用程序启动](app-startup.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-181">For more information about app startup, see [App startup](app-startup.md).</span></span>

## <a name="migrate-http-modules-and-handlers-to-middleware"></a><span data-ttu-id="b7e5a-182">将 HTTP 模块和处理程序迁移到中间件</span><span class="sxs-lookup"><span data-stu-id="b7e5a-182">Migrate HTTP modules and handlers to middleware</span></span>

<span data-ttu-id="b7e5a-183">HTTP 模块和处理程序是 Web 窗体中的常见模式，用来控制 HTTP 请求管道。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-183">HTTP modules and handlers are common patterns in Web Forms to control the HTTP request pipeline.</span></span> <span data-ttu-id="b7e5a-184">实现 `IHttpModule` 或 `IHttpHandler` 可以注册并处理传入请求的类。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-184">Classes that implement `IHttpModule` or `IHttpHandler` could be registered and process incoming requests.</span></span> <span data-ttu-id="b7e5a-185">Web 窗体在 *web.config* 文件中配置模块和处理程序。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-185">Web Forms configures modules and handlers in the *web.config* file.</span></span> <span data-ttu-id="b7e5a-186">Web 窗体在很大程度上取决于应用生命周期事件处理。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-186">Web Forms is also heavily based on app lifecycle event handling.</span></span> <span data-ttu-id="b7e5a-187">ASP.NET Core 改为使用中间件。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-187">ASP.NET Core uses middleware instead.</span></span> <span data-ttu-id="b7e5a-188">中间件是在类的方法中注册的 `Configure` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-188">Middleware is registered in the `Configure` method of the `Startup` class.</span></span> <span data-ttu-id="b7e5a-189">中间件执行顺序由注册顺序决定。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-189">Middleware execution order is determined by the registration order.</span></span>

<span data-ttu-id="b7e5a-190">在 " [启用启动过程](#enable-startup-process) " 部分，Web 窗体将引发生命周期事件作为 `Application_BeginRequest` 方法。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-190">In the [Enable startup process](#enable-startup-process) section, a lifecycle event was raised by Web Forms as the `Application_BeginRequest` method.</span></span> <span data-ttu-id="b7e5a-191">此事件在 ASP.NET Core 中不可用。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-191">This event isn't available in ASP.NET Core.</span></span> <span data-ttu-id="b7e5a-192">实现此行为的一种方法是实现中间件，如 *Startup.cs* 文件示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-192">One way to achieve this behavior is to implement middleware as seen in the *Startup.cs* file example.</span></span> <span data-ttu-id="b7e5a-193">此中间件执行相同的逻辑，然后将控制转移到中间件管道中的下一个处理程序。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-193">This middleware does the same logic and then transfers control to the next handler in the middleware pipeline.</span></span>

<span data-ttu-id="b7e5a-194">有关迁移模块和处理程序的详细信息，请参阅 [将 HTTP 处理程序和模块迁移到 ASP.NET Core 中间件](/aspnet/core/migration/http-modules)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-194">For more information on migrating modules and handlers, see [Migrate HTTP handlers and modules to ASP.NET Core middleware](/aspnet/core/migration/http-modules).</span></span>

## <a name="migrate-static-files"></a><span data-ttu-id="b7e5a-195">迁移静态文件</span><span class="sxs-lookup"><span data-stu-id="b7e5a-195">Migrate static files</span></span>

<span data-ttu-id="b7e5a-196">为了提供静态文件 (例如 HTML、CSS、图像和 JavaScript) ，文件必须由中间件公开。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-196">To serve static files (for example, HTML, CSS, images, and JavaScript), the files must be exposed by middleware.</span></span> <span data-ttu-id="b7e5a-197">通过调用 `UseStaticFiles` 方法，可以从 web 根路径提供静态文件。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-197">Calling the `UseStaticFiles` method enables the serving of static files from the web root path.</span></span> <span data-ttu-id="b7e5a-198">默认 web 根目录为 *wwwroot*，但可以对其进行自定义。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-198">The default web root directory is *wwwroot*, but it can be customized.</span></span> <span data-ttu-id="b7e5a-199">在 `Configure` eShop 的类的方法中包括 `Startup` ：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-199">As included in the `Configure` method of eShop's `Startup` class:</span></span>

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

<span data-ttu-id="b7e5a-200">EShop 项目可实现基本的静态文件访问。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-200">The eShop project enables basic static file access.</span></span> <span data-ttu-id="b7e5a-201">有很多自定义可用于静态文件访问。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-201">There are many customizations available for static file access.</span></span> <span data-ttu-id="b7e5a-202">有关启用默认文件或文件浏览器的信息，请参阅 [ASP.NET Core 中的静态文件](/aspnet/core/fundamentals/static-files)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-202">For information on enabling default files or a file browser, see [Static files in ASP.NET Core](/aspnet/core/fundamentals/static-files).</span></span>

## <a name="migrate-runtime-bundling-and-minification-setup"></a><span data-ttu-id="b7e5a-203">迁移运行时绑定和缩减安装程序</span><span class="sxs-lookup"><span data-stu-id="b7e5a-203">Migrate runtime bundling and minification setup</span></span>

<span data-ttu-id="b7e5a-204">绑定和缩减是一种性能优化技术，用于减少服务器请求检索特定文件类型的数量和大小。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-204">Bundling and minification are performance optimization techniques for reducing the number and size of server requests to retrieve certain file types.</span></span> <span data-ttu-id="b7e5a-205">在将 JavaScript 和 CSS 发送到客户端之前，通常会采用某种形式的绑定或缩减。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-205">JavaScript and CSS often undergo some form of bundling or minification before being sent to the client.</span></span> <span data-ttu-id="b7e5a-206">在 ASP.NET Web 窗体中，这些优化在运行时进行处理。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-206">In ASP.NET Web Forms, these optimizations are handled at runtime.</span></span> <span data-ttu-id="b7e5a-207">优化约定定义为 *App_Start/bundleconfig.cs* 文件。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-207">The optimization conventions are defined an *App_Start/BundleConfig.cs* file.</span></span> <span data-ttu-id="b7e5a-208">在 ASP.NET Core 中采用了一种更具声明性的方法。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-208">In ASP.NET Core, a more declarative approach is adopted.</span></span> <span data-ttu-id="b7e5a-209">文件将列出要缩小的文件以及特定的缩减设置。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-209">A file lists the files to be minified, along with specific minification settings.</span></span>

<span data-ttu-id="b7e5a-210">有关捆绑和缩减的详细信息，请参阅 [ASP.NET Core 中的捆绑和缩小静态资产](/aspnet/core/client-side/bundling-and-minification)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-210">For more information on bundling and minification, see [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).</span></span>

## <a name="migrate-aspx-pages"></a><span data-ttu-id="b7e5a-211">迁移 ASPX 页</span><span class="sxs-lookup"><span data-stu-id="b7e5a-211">Migrate ASPX pages</span></span>

<span data-ttu-id="b7e5a-212">Web 窗体应用中的页面是扩展名为 *.aspx* 的文件。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-212">A page in a Web Forms app is a file with the *.aspx* extension.</span></span> <span data-ttu-id="b7e5a-213">Web 窗体页通常可以映射到中的组件 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-213">A Web Forms page can often be mapped to a component in Blazor.</span></span> <span data-ttu-id="b7e5a-214">Blazor组件是在扩展名为*razor*的文件中创作的。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-214">A Blazor component is authored in a file with the *.razor* extension.</span></span> <span data-ttu-id="b7e5a-215">对于 eShop 项目，五个页面会转换为 Razor 页面。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-215">For the eShop project, five pages are converted to a Razor page.</span></span>

<span data-ttu-id="b7e5a-216">例如，详细信息视图包含 Web 窗体项目中的三个文件： " *详细信息*"、" *Details.aspx.cs*" 和 " *Details.aspx.designer.cs*"。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-216">For example, the details view comprises three files in the Web Forms project: *Details.aspx*, *Details.aspx.cs*, and *Details.aspx.designer.cs*.</span></span> <span data-ttu-id="b7e5a-217">转换为时 Blazor ，代码隐藏和标记将合并为*详细信息。*</span><span class="sxs-lookup"><span data-stu-id="b7e5a-217">When converting to Blazor, the code-behind and markup are combined into *Details.razor*.</span></span> <span data-ttu-id="b7e5a-218">Razor 编译 (等效于 *designer.cs* 文件中) 存储在 *obj* 目录中，默认情况下，在 **解决方案资源管理器**中可查看。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-218">Razor compilation (equivalent to what's in *.designer.cs* files) is stored in the *obj* directory and isn't, by default, viewable in **Solution Explorer**.</span></span> <span data-ttu-id="b7e5a-219">Web 窗体页由以下标记组成：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-219">The Web Forms page consists of the following markup:</span></span>

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

<span data-ttu-id="b7e5a-220">前面标记的代码隐藏包含以下代码：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-220">The preceding markup's code-behind includes the following code:</span></span>

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

<span data-ttu-id="b7e5a-221">转换为时 Blazor ，Web 窗体页会转换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-221">When converted to Blazor, the Web Forms page translates to the following code:</span></span>

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

<span data-ttu-id="b7e5a-222">请注意，代码和标记位于同一个文件中。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-222">Notice that the code and markup are in the same file.</span></span> <span data-ttu-id="b7e5a-223">所有必需的服务都可通过属性进行访问 `@inject` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-223">Any required services are made accessible with the `@inject` attribute.</span></span> <span data-ttu-id="b7e5a-224">在 `@page` 此页上，可以在路由中访问此页 `Catalog/Details/{id}` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-224">Per the `@page` directive, this page can be accessed at the `Catalog/Details/{id}` route.</span></span> <span data-ttu-id="b7e5a-225">路由占位符的值已 `{id}` 被约束为一个整数。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-225">The value of the route's `{id}` placeholder has been constrained to an integer.</span></span> <span data-ttu-id="b7e5a-226">如 " [路由](pages-routing-layouts.md) " 一节中所述，与 Web 窗体不同，Razor 组件显式声明其路由以及所包含的所有参数。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-226">As described in the [routing](pages-routing-layouts.md) section, unlike Web Forms, a Razor component explicitly states its route and any parameters that are included.</span></span> <span data-ttu-id="b7e5a-227">许多 Web 窗体控件在中的对应项可能不完全相同 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-227">Many Web Forms controls may not have exact counterparts in Blazor.</span></span> <span data-ttu-id="b7e5a-228">通常，具有相同用途的等效 HTML 代码段。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-228">There's often an equivalent HTML snippet that will serve the same purpose.</span></span> <span data-ttu-id="b7e5a-229">例如， `<asp:Label />` 可以将控件替换为 HTML `<label>` 元素。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-229">For example, the `<asp:Label />` control can be replaced with an HTML `<label>` element.</span></span>

### <a name="model-validation-in-no-locblazor"></a><span data-ttu-id="b7e5a-230">模型验证 Blazor</span><span class="sxs-lookup"><span data-stu-id="b7e5a-230">Model validation in Blazor</span></span>

<span data-ttu-id="b7e5a-231">如果 Web 窗体代码包括验证，则可以使用很少的更改传输您的大部分内容。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-231">If your Web Forms code includes validation, you can transfer much of what you have with little-to-no changes.</span></span> <span data-ttu-id="b7e5a-232">中运行的好处 Blazor 是，可以运行相同的验证逻辑，而无需自定义 JavaScript。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-232">A benefit to running in Blazor is that the same validation logic can be run without needing custom JavaScript.</span></span> <span data-ttu-id="b7e5a-233">数据批注实现了简单的模型验证。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-233">Data annotations enable easy model validation.</span></span>

<span data-ttu-id="b7e5a-234">例如， *Create .aspx* 页面包含带有验证的数据输入窗体。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-234">For example, the *Create.aspx* page has a data entry form with validation.</span></span> <span data-ttu-id="b7e5a-235">示例代码段如下所示：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-235">An example snippet would look like this:</span></span>

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

<span data-ttu-id="b7e5a-236">在中 Blazor ， *创建 razor* 文件中提供了等效标记：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-236">In Blazor, the equivalent markup is provided in a *Create.razor* file:</span></span>

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

<span data-ttu-id="b7e5a-237">`EditForm`上下文包括验证支持，可在输入前后环绕。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-237">The `EditForm` context includes validation support and can be wrapped around input.</span></span> <span data-ttu-id="b7e5a-238">数据批注是添加验证的常用方法。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-238">Data annotations are a common way to add validation.</span></span> <span data-ttu-id="b7e5a-239">可以通过组件添加此类验证支持 `DataAnnotationsValidator` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-239">Such validation support can be added via the `DataAnnotationsValidator` component.</span></span> <span data-ttu-id="b7e5a-240">有关此机制的详细信息，请参阅 [ASP.NET Core Blazor 窗体和验证](/aspnet/core/blazor/forms-validation)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-240">For more information on this mechanism, see [ASP.NET Core Blazor forms and validation](/aspnet/core/blazor/forms-validation).</span></span>

## <a name="migrate-configuration"></a><span data-ttu-id="b7e5a-241">迁移配置</span><span class="sxs-lookup"><span data-stu-id="b7e5a-241">Migrate configuration</span></span>

<span data-ttu-id="b7e5a-242">在 Web 窗体项目中，配置数据通常存储在 *web.config* 文件中。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-242">In a Web Forms project, configuration data is most commonly stored in the *web.config* file.</span></span> <span data-ttu-id="b7e5a-243">配置数据通过访问 `ConfigurationManager` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-243">The configuration data is accessed with `ConfigurationManager`.</span></span> <span data-ttu-id="b7e5a-244">通常需要服务来分析对象。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-244">Services were often required to parse objects.</span></span> <span data-ttu-id="b7e5a-245">通过 .NET Framework 4.7.2，可组合性通过添加到配置 `ConfigurationBuilders` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-245">With .NET Framework 4.7.2, composability was added to configuration via `ConfigurationBuilders`.</span></span> <span data-ttu-id="b7e5a-246">这些生成器允许开发人员为配置添加各种源，然后在运行时编写这些源以检索必要的值。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-246">These builders allowed developers to add various sources for configuration that was then composed at runtime to retrieve the necessary values.</span></span>

<span data-ttu-id="b7e5a-247">ASP.NET Core 引入了一个灵活的配置系统，该系统允许你定义应用和部署所使用的配置源。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-247">ASP.NET Core introduced a flexible configuration system that allows you to define the configuration source or sources used by your app and deployment.</span></span> <span data-ttu-id="b7e5a-248">`ConfigurationBuilder`您在 Web 窗体应用程序中使用的基础结构在 ASP.NET Core 配置系统中使用的概念后建模。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-248">The `ConfigurationBuilder` infrastructure that you may be using in your Web Forms app was modeled after the concepts used in the ASP.NET Core configuration system.</span></span>

<span data-ttu-id="b7e5a-249">以下代码片段演示了 Web 窗体 eShop 项目如何使用 *web.config* 来存储配置值：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-249">The following snippet demonstrates how the Web Forms eShop project uses *web.config* to store configuration values:</span></span>

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

<span data-ttu-id="b7e5a-250">机密（如数据库连接字符串）通常存储在 *web.config*中。机密不可避免地保存在不安全的位置，如源代码管理。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-250">It's common for secrets, such as database connection strings, to be stored within the *web.config*. The secrets are inevitably persisted in unsecure locations, such as source control.</span></span> <span data-ttu-id="b7e5a-251">对于 Blazor ASP.NET Core 上的，上面的基于 XML 的配置将替换为以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-251">With Blazor on ASP.NET Core, the preceding XML-based configuration is replaced with the following JSON:</span></span>

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

<span data-ttu-id="b7e5a-252">JSON 为默认配置格式;但 ASP.NET Core 支持许多其他格式，包括 XML。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-252">JSON is the default configuration format; however, ASP.NET Core supports many other formats, including XML.</span></span> <span data-ttu-id="b7e5a-253">还有多个社区支持的格式。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-253">There are also several community-supported formats.</span></span>

<span data-ttu-id="b7e5a-254">项目类中的构造函数 Blazor `Startup` `IConfiguration` 通过一种称为 "构造函数注入" 的 DI 技术接受实例：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-254">The constructor in the Blazor project's `Startup` class accepts an `IConfiguration` instance through a DI technique known as constructor injection:</span></span>

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

<span data-ttu-id="b7e5a-255">默认情况下，环境变量、JSON 文件 (*appsettings.js* 和 *appsettings。 {环境} json*) 和命令行选项在配置对象中注册为有效的配置源。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-255">By default, environment variables, JSON files (*appsettings.json* and *appsettings.{Environment}.json*), and command-line options are registered as valid configuration sources in the configuration object.</span></span> <span data-ttu-id="b7e5a-256">可以通过访问配置源 `Configuration[key]` 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-256">The configuration sources can be accessed via `Configuration[key]`.</span></span> <span data-ttu-id="b7e5a-257">更高级的技术是使用选项模式将配置数据绑定到对象。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-257">A more advanced technique is to bind the configuration data to objects using the options pattern.</span></span> <span data-ttu-id="b7e5a-258">有关配置和选项模式的详细信息，请分别参阅 ASP.NET Core 中 ASP.NET Core 和[options 模式](/aspnet/core/fundamentals/configuration/options)下的[配置](/aspnet/core/fundamentals/configuration/)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-258">For more information on configuration and the options pattern, see [Configuration in ASP.NET Core](/aspnet/core/fundamentals/configuration/) and [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectively.</span></span>

## <a name="migrate-data-access"></a><span data-ttu-id="b7e5a-259">迁移数据访问</span><span class="sxs-lookup"><span data-stu-id="b7e5a-259">Migrate data access</span></span>

<span data-ttu-id="b7e5a-260">数据访问是任何应用程序的一个重要方面。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-260">Data access is an important aspect of any app.</span></span> <span data-ttu-id="b7e5a-261">EShop 项目在数据库中存储目录信息，并使用实体框架 (EF) 6 检索数据。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-261">The eShop project stores catalog information in a database and retrieves the data with Entity Framework (EF) 6.</span></span> <span data-ttu-id="b7e5a-262">由于 .NET Core 3.0 支持 EF 6，因此项目可以继续使用它。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-262">Since EF 6 is supported in .NET Core 3.0, the project can continue to use it.</span></span>

<span data-ttu-id="b7e5a-263">EShop 需要以下与 EF 相关的更改：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-263">The following EF-related changes were necessary to eShop:</span></span>

- <span data-ttu-id="b7e5a-264">在 .NET Framework 中， `DbContext` 对象接受 *名称 = ConnectionString* 格式的字符串，并使用中的连接字符串 `ConfigurationManager.AppSettings[ConnectionString]` 进行连接。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-264">In .NET Framework, the `DbContext` object accepts a string of the form *name=ConnectionString* and uses the connection string from `ConfigurationManager.AppSettings[ConnectionString]` to connect.</span></span> <span data-ttu-id="b7e5a-265">在 .NET Core 中，不支持这种情况。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-265">In .NET Core, this isn't supported.</span></span> <span data-ttu-id="b7e5a-266">必须提供连接字符串。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-266">The connection string must be supplied.</span></span>
- <span data-ttu-id="b7e5a-267">以同步方式访问数据库。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-267">The database was accessed in a synchronous way.</span></span> <span data-ttu-id="b7e5a-268">尽管这可行，可伸缩性可能会受到影响。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-268">Though this works, scalability may suffer.</span></span> <span data-ttu-id="b7e5a-269">此逻辑应移动到异步模式。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-269">This logic should be moved to an asynchronous pattern.</span></span>

<span data-ttu-id="b7e5a-270">尽管对数据集绑定的本机支持不相同，但 Blazor 在 Razor 页中提供了其 c # 支持的灵活性和强大功能。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-270">Although there isn't the same native support for dataset binding, Blazor provides flexibility and power with its C# support in a Razor page.</span></span> <span data-ttu-id="b7e5a-271">例如，您可以执行计算并显示结果。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-271">For example, you can perform calculations and display the result.</span></span> <span data-ttu-id="b7e5a-272">有关中的数据模式的详细信息 Blazor ，请参阅 [数据访问](data.md) 章节。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-272">For more information on data patterns in Blazor, see the [Data access](data.md) chapter.</span></span>

## <a name="architectural-changes"></a><span data-ttu-id="b7e5a-273">体系结构更改</span><span class="sxs-lookup"><span data-stu-id="b7e5a-273">Architectural changes</span></span>

<span data-ttu-id="b7e5a-274">最后，在迁移到时，需要考虑一些重要的体系结构差异 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-274">Finally, there are some important architectural differences to consider when migrating to Blazor.</span></span> <span data-ttu-id="b7e5a-275">其中的许多更改都适用于基于 .NET Core 或 ASP.NET Core 的任何内容。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-275">Many of these changes are applicable to anything based on .NET Core or ASP.NET Core.</span></span>

<span data-ttu-id="b7e5a-276">由于 Blazor 是基于 .Net core 构建的，因此请注意确保 .Net core 支持。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-276">Because Blazor is built on .NET Core, there are considerations in ensuring support on .NET Core.</span></span> <span data-ttu-id="b7e5a-277">一些主要更改包括删除以下功能：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-277">Some of the major changes include the removal of the following features:</span></span>

- <span data-ttu-id="b7e5a-278">多个 Appdomain</span><span class="sxs-lookup"><span data-stu-id="b7e5a-278">Multiple AppDomains</span></span>
- <span data-ttu-id="b7e5a-279">远程处理</span><span class="sxs-lookup"><span data-stu-id="b7e5a-279">Remoting</span></span>
- <span data-ttu-id="b7e5a-280">代码访问安全性 (CAS)</span><span class="sxs-lookup"><span data-stu-id="b7e5a-280">Code Access Security (CAS)</span></span>
- <span data-ttu-id="b7e5a-281">安全透明度</span><span class="sxs-lookup"><span data-stu-id="b7e5a-281">Security Transparency</span></span>

<span data-ttu-id="b7e5a-282">若要详细了解如何识别在 .NET Core 上运行所需的更改，请参阅将 [代码从 .NET Framework 移植到 .Net core](../../core/porting/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-282">For more information on techniques to identify necessary changes to support running on .NET Core, see [Port your code from .NET Framework to .NET Core](../../core/porting/index.md).</span></span>

<span data-ttu-id="b7e5a-283">ASP.NET Core 是 ASP.NET 的重新塑造版本，并且有一些更改最初可能不明显。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-283">ASP.NET Core is a reimagined version of ASP.NET and has some changes that may not initially seem obvious.</span></span> <span data-ttu-id="b7e5a-284">主要变化如下：</span><span class="sxs-lookup"><span data-stu-id="b7e5a-284">The main changes are:</span></span>

- <span data-ttu-id="b7e5a-285">无同步上下文，这意味着没有 `HttpContext.Current` 、 `Thread.CurrentPrincipal` 或其他静态访问器</span><span class="sxs-lookup"><span data-stu-id="b7e5a-285">No synchronization context, which means there's no `HttpContext.Current`, `Thread.CurrentPrincipal`, or other static accessors</span></span>
- <span data-ttu-id="b7e5a-286">无卷影复制</span><span class="sxs-lookup"><span data-stu-id="b7e5a-286">No shadow copying</span></span>
- <span data-ttu-id="b7e5a-287">无请求队列</span><span class="sxs-lookup"><span data-stu-id="b7e5a-287">No request queue</span></span>

<span data-ttu-id="b7e5a-288">ASP.NET Core 中的许多操作都是异步的，因此可以更轻松地不加载 i/o 限制任务。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-288">Many operations in ASP.NET Core are asynchronous, which allows easier off-loading of I/O-bound tasks.</span></span> <span data-ttu-id="b7e5a-289">切勿使用或来阻止，这一点很重要 `Task.Wait()` `Task.GetResult()` ，因为这样可以快速耗尽线程池资源。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-289">It's important to never block by using `Task.Wait()` or `Task.GetResult()`, which can quickly exhaust thread pool resources.</span></span>

## <a name="migration-conclusion"></a><span data-ttu-id="b7e5a-290">迁移结论</span><span class="sxs-lookup"><span data-stu-id="b7e5a-290">Migration conclusion</span></span>

<span data-ttu-id="b7e5a-291">此时，你已了解将 Web 窗体项目移动到所需的多个示例 Blazor 。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-291">At this point, you've seen many examples of what it takes to move a Web Forms project to Blazor.</span></span> <span data-ttu-id="b7e5a-292">有关完整示例，请参阅[eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor)项目。</span><span class="sxs-lookup"><span data-stu-id="b7e5a-292">For a full example, see the [eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor) project.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b7e5a-293">上一页</span><span class="sxs-lookup"><span data-stu-id="b7e5a-293">Previous</span></span>](security-authentication-authorization.md)
