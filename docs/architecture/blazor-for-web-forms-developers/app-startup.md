---
title: 应用启动
description: 了解如何定义应用的启动逻辑。
author: csharpfritz
ms.author: jefritz
ms.date: 02/25/2020
ms.openlocfilehash: 883f9a3fbe2d52cb7d0fbc5dfc94ce829a5d2bf3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158183"
---
# <a name="app-startup"></a><span data-ttu-id="e2251-103">应用启动</span><span class="sxs-lookup"><span data-stu-id="e2251-103">App startup</span></span>

<span data-ttu-id="e2251-104">为 ASP.NET 编写的应用程序通常具有一个 `global.asax.cs` 定义事件的文件，该 `Application_Start` 事件控制配置哪些服务并使其可用于 HTML 呈现和 .net 处理。</span><span class="sxs-lookup"><span data-stu-id="e2251-104">Applications that are written for ASP.NET typically have a `global.asax.cs` file that defines the `Application_Start` event that controls which services are configured and made available for both HTML rendering and .NET processing.</span></span> <span data-ttu-id="e2251-105">本章介绍 ASP.NET Core 和 Blazor 服务器的不同之处。</span><span class="sxs-lookup"><span data-stu-id="e2251-105">This chapter looks at how things are slightly different with ASP.NET Core and Blazor Server.</span></span>

## <a name="application_start-and-web-forms"></a><span data-ttu-id="e2251-106">Application_Start 和 Web 窗体</span><span class="sxs-lookup"><span data-stu-id="e2251-106">Application_Start and Web Forms</span></span>

<span data-ttu-id="e2251-107">默认 web 窗体 `Application_Start` 方法已在数年内发展，以处理许多配置任务。</span><span class="sxs-lookup"><span data-stu-id="e2251-107">The default web forms `Application_Start` method has grown in purpose over years to handle many configuration tasks.</span></span>  <span data-ttu-id="e2251-108">使用 Visual Studio 2019 中默认模板的全新 web 窗体项目现在包含以下配置逻辑：</span><span class="sxs-lookup"><span data-stu-id="e2251-108">A fresh web forms project with the default template in Visual Studio 2019 now contains the following configuration logic:</span></span>

- <span data-ttu-id="e2251-109">`RouteConfig` -应用程序 URL 路由</span><span class="sxs-lookup"><span data-stu-id="e2251-109">`RouteConfig` - Application URL routing</span></span>
- <span data-ttu-id="e2251-110">`BundleConfig` -CSS 和 JavaScript 捆绑与缩减</span><span class="sxs-lookup"><span data-stu-id="e2251-110">`BundleConfig` - CSS and JavaScript bundling and minification</span></span>

<span data-ttu-id="e2251-111">每个文件都驻留在该 `App_Start` 文件夹中，并在应用程序启动时只运行一次。</span><span class="sxs-lookup"><span data-stu-id="e2251-111">Each of these individual files reside in the `App_Start` folder and run only once at the start of our application.</span></span>  <span data-ttu-id="e2251-112">`RouteConfig` 在默认项目模板中，添加 `FriendlyUrlSettings` 用于 web 窗体的，以允许应用程序 url 忽略 `.ASPX` 文件扩展名。</span><span class="sxs-lookup"><span data-stu-id="e2251-112">`RouteConfig` in the default project template adds the `FriendlyUrlSettings` for web forms to allow application URLs to omit the `.ASPX` file extension.</span></span>  <span data-ttu-id="e2251-113">默认模板还包含一个指令，该指令为 `.ASPX` 带有省略扩展名的文件名的友好 URL (HTTP 301) 提供永久性 http 重定向状态代码。</span><span class="sxs-lookup"><span data-stu-id="e2251-113">The default template also contains a directive that provides permanent HTTP redirect status codes (HTTP 301) for the `.ASPX` pages to the friendly URL with the file name that omits the extension.</span></span>

<span data-ttu-id="e2251-114">通过 ASP.NET Core 和 Blazor，这些方法可以简化并合并到 `Startup` 类中，也可以消除这些方法以支持常见的 web 技术。</span><span class="sxs-lookup"><span data-stu-id="e2251-114">With ASP.NET Core and Blazor, these methods are either simplified and consolidated into the `Startup` class or they are eliminated in favor of common web technologies.</span></span>

## <a name="blazor-server-startup-structure"></a><span data-ttu-id="e2251-115">Blazor 服务器启动结构</span><span class="sxs-lookup"><span data-stu-id="e2251-115">Blazor Server Startup Structure</span></span>

<span data-ttu-id="e2251-116">Blazor 服务器应用程序位于 ASP.NET Core 3.0 或更高版本的应用程序的顶层。</span><span class="sxs-lookup"><span data-stu-id="e2251-116">Blazor Server applications reside on top of an ASP.NET Core 3.0 or later application.</span></span>  <span data-ttu-id="e2251-117">ASP.NET Core web 应用程序通过 `Startup.cs` 应用程序根文件夹的类中的一对方法进行配置。</span><span class="sxs-lookup"><span data-stu-id="e2251-117">ASP.NET Core web applications are configured through a pair of methods in the `Startup.cs` class on the root folder of the application.</span></span>  <span data-ttu-id="e2251-118">Startup 类的默认内容如下所示</span><span class="sxs-lookup"><span data-stu-id="e2251-118">The Startup class's default content is listed below</span></span>

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

<span data-ttu-id="e2251-119">与 ASP.NET Core 的其余部分一样，启动类是通过依赖关系注入原则创建的。</span><span class="sxs-lookup"><span data-stu-id="e2251-119">Like the rest of ASP.NET Core, the Startup class is created with dependency injection principles.</span></span>  <span data-ttu-id="e2251-120">`IConfiguration`提供给构造函数并在公共属性中储藏更改，以便以后在配置期间进行访问。</span><span class="sxs-lookup"><span data-stu-id="e2251-120">The `IConfiguration` is provided to the constructor and stashed in a public property for later access during configuration.</span></span>

<span data-ttu-id="e2251-121">`ConfigureServices`ASP.NET Core 中引入的方法允许为框架的内置依赖关系注入容器配置各种 ASP.NET Core 框架服务。</span><span class="sxs-lookup"><span data-stu-id="e2251-121">The `ConfigureServices` method introduced in ASP.NET Core allows for the various ASP.NET Core framework services to be configured for the framework's built-in dependency injection container.</span></span>  <span data-ttu-id="e2251-122">各种 `services.Add*` 方法添加了一些服务，这些服务可实现身份验证、razor 页面、MVC 控制器路由、SignalR 和 Blazor 服务器交互等功能。</span><span class="sxs-lookup"><span data-stu-id="e2251-122">The various `services.Add*` methods add services that enable features such as authentication, razor pages, MVC controller routing, SignalR, and Blazor Server interactions among many others.</span></span>  <span data-ttu-id="e2251-123">Web 窗体中不需要此方法，因为在 web.config 配置文件中引用 ASP.NET 定义了对 ASPX、.ASCX、FOO.ASHX 和 .ASMX 文件的分析和处理。</span><span class="sxs-lookup"><span data-stu-id="e2251-123">This method was not needed in web forms, as the parsing and handling of the ASPX, ASCX, ASHX, and ASMX files was defined by referencing ASP.NET in the web.config configuration file.</span></span>  <span data-ttu-id="e2251-124">有关 ASP.NET Core 中的依赖项注入的详细信息，请 [参阅联机文档](/aspnet/core/fundamentals/dependency-injection)。</span><span class="sxs-lookup"><span data-stu-id="e2251-124">More information about dependency injection in ASP.NET Core is available in the [online documentation](/aspnet/core/fundamentals/dependency-injection).</span></span>

<span data-ttu-id="e2251-125">`Configure`方法介绍 ASP.NET Core 的 HTTP 管道的概念。</span><span class="sxs-lookup"><span data-stu-id="e2251-125">The `Configure` method introduces the concept of the HTTP pipeline to ASP.NET Core.</span></span>  <span data-ttu-id="e2251-126">在此方法中，我们将从上到下声明 [中间件](middleware.md) ，它们将处理发送到应用程序的每个请求。</span><span class="sxs-lookup"><span data-stu-id="e2251-126">In this method, we declare from top to bottom the [Middleware](middleware.md) that will handle every request sent to our application.</span></span> <span data-ttu-id="e2251-127">默认配置中的大多数功能分散在 web 窗体配置文件中，并且现在位于一个位置以便于参考。</span><span class="sxs-lookup"><span data-stu-id="e2251-127">Most of these features in the default configuration were scattered across the web forms configuration files and are now in one place for ease of reference.</span></span>

<span data-ttu-id="e2251-128">不会再配置放置在文件中的自定义错误页 `web.config` ，但现在将配置为在应用程序环境未标记的情况下始终显示 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="e2251-128">No longer is the configuration of the custom error page placed in a `web.config` file, but now is configured to always be shown if the application environment is not labeled `Development`.</span></span>  <span data-ttu-id="e2251-129">此外，ASP.NET Core 的应用程序现已配置为在默认情况下通过方法调用为安全页面提供 TLS `UseHttpsRedirection` 。</span><span class="sxs-lookup"><span data-stu-id="e2251-129">Additionally, ASP.NET Core applications are now configured to serve secure pages with TLS by default with the `UseHttpsRedirection` method call.</span></span>

<span data-ttu-id="e2251-130">接下来，将向中列出一个意外的配置方法 `UseStaticFiles` 。</span><span class="sxs-lookup"><span data-stu-id="e2251-130">Next, an unexpected configuration method is listed to `UseStaticFiles`.</span></span>  <span data-ttu-id="e2251-131">在 ASP.NET Core 中，必须显式启用对静态文件的请求 (（如 JavaScript、CSS 和图像) 文件）的支持，并且默认情况下，只有应用的 *wwwroot* 文件夹中的文件可公开寻址。</span><span class="sxs-lookup"><span data-stu-id="e2251-131">In ASP.NET Core, support for requests for static files (like JavaScript, CSS, and image files) must be explicitly enabled, and only files in the app's *wwwroot* folder are publicly addressable by default.</span></span>

<span data-ttu-id="e2251-132">下一行是从 web 窗体复制其中一个配置选项的第一个 `UseRouting` 。</span><span class="sxs-lookup"><span data-stu-id="e2251-132">The next line is the first that replicates one of the configuration options from web forms: `UseRouting`.</span></span>  <span data-ttu-id="e2251-133">此方法将 ASP.NET Core 路由器添加到管道，可将其配置为此处或在可考虑路由到的单个文件中。</span><span class="sxs-lookup"><span data-stu-id="e2251-133">This method adds the ASP.NET Core router to the pipeline and it can be either configured here or in the individual files that it can consider routing to.</span></span>  <span data-ttu-id="e2251-134">有关路由配置的详细信息，请参阅 [路由部分](pages-routing-layouts.md)。</span><span class="sxs-lookup"><span data-stu-id="e2251-134">More information about routing configuration can be found in the [Routing section](pages-routing-layouts.md).</span></span>

<span data-ttu-id="e2251-135">此方法中的最后一个语句定义 ASP.NET Core 所侦听的终结点。</span><span class="sxs-lookup"><span data-stu-id="e2251-135">The final statement in this method defines the endpoints that ASP.NET Core is listening on.</span></span>  <span data-ttu-id="e2251-136">这些是可在 web 服务器上访问的 web 可访问位置，并接收一些由 .NET 处理并返回给你的内容。</span><span class="sxs-lookup"><span data-stu-id="e2251-136">These are the web accessible locations that you can access on the web server and receive some content handled by .NET and returned to you.</span></span>  <span data-ttu-id="e2251-137">第一项 `MapBlazorHub` 配置 SignalR 集线器，以便在为服务器提供实时和持久连接的情况下处理 Blazor 组件的状态和呈现。</span><span class="sxs-lookup"><span data-stu-id="e2251-137">The first entry, `MapBlazorHub` configures a SignalR hub for use in providing the real-time and persistent connection to the server where the state and rendering of Blazor components is handled.</span></span>  <span data-ttu-id="e2251-138">`MapFallbackToPage`方法调用指示启动 Blazor 应用程序的页面的 web 可访问位置，还会将应用程序配置为处理来自客户端的深层链接请求。</span><span class="sxs-lookup"><span data-stu-id="e2251-138">The `MapFallbackToPage` method call indicates the web-accessible location of the page that starts the Blazor application and also configures the application to handle deep-linking requests from the client-side.</span></span>  <span data-ttu-id="e2251-139">如果打开浏览器并直接导航到应用程序中的 Blazor 已处理路由（例如， `/counter` 在默认项目模板中），则会看到此功能在工作。</span><span class="sxs-lookup"><span data-stu-id="e2251-139">You will see this feature at work if you open a browser and navigate directly to Blazor handled route in your application, such as `/counter` in the default project template.</span></span> <span data-ttu-id="e2251-140">该请求由 *_Host* 的 "Blazor" 回退页面进行处理，后者随后运行 "路由器" 并呈现计数器页。</span><span class="sxs-lookup"><span data-stu-id="e2251-140">The request gets handled by the *_Host.cshtml* fallback page, which then runs the Blazor router and renders the counter page.</span></span>

## <a name="upgrading-the-bundleconfig-process"></a><span data-ttu-id="e2251-141">升级 BundleConfig 进程</span><span class="sxs-lookup"><span data-stu-id="e2251-141">Upgrading the BundleConfig Process</span></span>

<span data-ttu-id="e2251-142">用于捆绑 CSS 样式表和 JavaScript 文件之类的资产的技术显著发展，同时还提供了一些快速发展的工具和技术，用于管理这些资源。</span><span class="sxs-lookup"><span data-stu-id="e2251-142">Technologies for bundling assets like CSS stylesheets and JavaScript files have evolved significantly, with other technologies providing quickly evolving tools and techniques for managing these resources.</span></span>  <span data-ttu-id="e2251-143">为此，我们建议使用节点命令行工具（如 Grunt/Gulp/WebPack）打包静态资产。</span><span class="sxs-lookup"><span data-stu-id="e2251-143">To this end, we recommend using a Node command-line tool such as Grunt / Gulp / WebPack to package your static assets.</span></span>

<span data-ttu-id="e2251-144">可以将 Grunt、Gulp 和 WebPack 命令行工具及其关联的配置添加到应用程序中，ASP.NET Core 将在应用程序生成过程中不知不觉地忽略这些文件。</span><span class="sxs-lookup"><span data-stu-id="e2251-144">The Grunt, Gulp, and WebPack command-line tools and their associated configurations can be added to your application and ASP.NET Core will quietly ignore those files during the application build process.</span></span>  <span data-ttu-id="e2251-145">你可以通过在项目文件中添加一个调用来运行其任务，方法是 `Target` 在项目文件中添加，其语法类似于以下语法，它将触发 gulp 脚本和 `min` 该脚本中的目标</span><span class="sxs-lookup"><span data-stu-id="e2251-145">You can add a call to run their tasks by adding a `Target` inside your project file with syntax similar to the following that would trigger a gulp script and the `min` target inside that script</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

<span data-ttu-id="e2251-146">有关用于管理 CSS 和 JavaScript 文件的这两种策略的更多详细信息，请参阅 [捆绑和缩小静态资产中的 ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) 文档。</span><span class="sxs-lookup"><span data-stu-id="e2251-146">More details about both strategies to manage your CSS and JavaScript files are available in the [Bundle and minify static assets in ASP.NET Core](/aspnet/core/client-side/bundling-and-minification) documentation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e2251-147">[上一页](project-structure.md)
>[下一页](components.md)</span><span class="sxs-lookup"><span data-stu-id="e2251-147">[Previous](project-structure.md)
[Next](components.md)</span></span>
