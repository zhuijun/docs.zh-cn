---
title: 应用配置
description: 了解如何在 Blazor 不使用 ConfigurationManager 的情况下配置应用。
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/01/2020
ms.openlocfilehash: a13f663c2c6908ba906e42cb939c3b8707b8cccd
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173297"
---
# <a name="app-configuration"></a><span data-ttu-id="a67fa-103">应用配置</span><span class="sxs-lookup"><span data-stu-id="a67fa-103">App configuration</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a67fa-104">在 Web 窗体中加载应用程序配置的主要方法是在服务器上使用*web.config*文件中的条目， &mdash; 或者*web.config*引用相关的配置文件。您可以使用静态 `ConfigurationManager` 对象与应用程序设置、数据存储库连接字符串以及添加到应用中的其他扩展配置提供程序进行交互。</span><span class="sxs-lookup"><span data-stu-id="a67fa-104">The primary way to load app configuration in Web Forms is with entries in the *web.config* file&mdash;either on the server or a related configuration file referenced by *web.config*. You can use the static `ConfigurationManager` object to interact with app settings, data repository connection strings, and other extended configuration providers that are added into the app.</span></span> <span data-ttu-id="a67fa-105">通常，查看与应用配置的交互，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="a67fa-105">It's typical to see interactions with app configuration as seen in the following code:</span></span>

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

<span data-ttu-id="a67fa-106">Blazor如果你的应用程序托管在 WINDOWS IIS 服务器上，则使用 ASP.NET Core 和服务器端时，可能会出现*web.config*文件。</span><span class="sxs-lookup"><span data-stu-id="a67fa-106">With ASP.NET Core and server-side Blazor, the *web.config* file MAY be present if your app is hosted on a Windows IIS server.</span></span> <span data-ttu-id="a67fa-107">但是， `ConfigurationManager` 与此配置并无交互，你可以从其他来源接收更多结构化应用配置。</span><span class="sxs-lookup"><span data-stu-id="a67fa-107">However, there's no `ConfigurationManager` interaction with this configuration, and you can receive more structured app configuration from other sources.</span></span> <span data-ttu-id="a67fa-108">让我们看看如何收集配置，以及你仍可以如何从*web.config*文件访问配置信息。</span><span class="sxs-lookup"><span data-stu-id="a67fa-108">Let's take a look at how configuration is gathered and how you can still access configuration information from a *web.config* file.</span></span>

## <a name="configuration-sources"></a><span data-ttu-id="a67fa-109">配置源</span><span class="sxs-lookup"><span data-stu-id="a67fa-109">Configuration sources</span></span>

<span data-ttu-id="a67fa-110">ASP.NET Core 认识到你的应用可能需要使用很多配置源。</span><span class="sxs-lookup"><span data-stu-id="a67fa-110">ASP.NET Core recognizes there are many configuration sources you may want to use for your app.</span></span> <span data-ttu-id="a67fa-111">默认情况下，框架将尝试为您提供这些功能的最佳功能。</span><span class="sxs-lookup"><span data-stu-id="a67fa-111">The framework attempts to offer you the best of these features by default.</span></span> <span data-ttu-id="a67fa-112">ASP.NET Core 从这些不同的源读取和聚合配置。</span><span class="sxs-lookup"><span data-stu-id="a67fa-112">Configuration is read and aggregated from these various sources by ASP.NET Core.</span></span> <span data-ttu-id="a67fa-113">对于同一配置密钥，稍后加载的值优先于先前值。</span><span class="sxs-lookup"><span data-stu-id="a67fa-113">Later loaded values for the same configuration key take precedence over earlier values.</span></span>

<span data-ttu-id="a67fa-114">ASP.NET Core 被设计为能够识别云，并使运营商和开发人员更容易地配置应用程序。</span><span class="sxs-lookup"><span data-stu-id="a67fa-114">ASP.NET Core was designed to be cloud-aware and to make configuration of apps easier for both operators and developers.</span></span> <span data-ttu-id="a67fa-115">ASP.NET Core 是环境感知的，知道它是在您的 `Production` 还是环境中运行 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-115">ASP.NET Core is environment-aware and knows if it's running in your `Production` or `Development` environment.</span></span> <span data-ttu-id="a67fa-116">环境指示器是在 `ASPNETCORE_ENVIRONMENT` 系统环境变量中设置的。</span><span class="sxs-lookup"><span data-stu-id="a67fa-116">The environment indicator is set in the `ASPNETCORE_ENVIRONMENT` system environment variable.</span></span> <span data-ttu-id="a67fa-117">如果未配置任何值，应用程序默认为在环境中运行 `Production` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-117">If no value is configured, the app defaults to running in the `Production` environment.</span></span>

<span data-ttu-id="a67fa-118">应用可根据环境名称从多个源触发并添加配置。</span><span class="sxs-lookup"><span data-stu-id="a67fa-118">Your app can trigger and add configuration from several sources based on the environment's name.</span></span> <span data-ttu-id="a67fa-119">默认情况下，按列出的顺序从以下资源加载配置：</span><span class="sxs-lookup"><span data-stu-id="a67fa-119">By default, configuration is loaded from the following resources in the order listed:</span></span>

1. <span data-ttu-id="a67fa-120">*appsettings.js*文件（如果存在）</span><span class="sxs-lookup"><span data-stu-id="a67fa-120">*appsettings.json* file, if present</span></span>
1. <span data-ttu-id="a67fa-121">*appsettings。{ENVIRONMENT_NAME} json*文件（如果存在）</span><span class="sxs-lookup"><span data-stu-id="a67fa-121">*appsettings.{ENVIRONMENT_NAME}.json* file, if present</span></span>
1. <span data-ttu-id="a67fa-122">磁盘上的用户机密文件（如果存在）</span><span class="sxs-lookup"><span data-stu-id="a67fa-122">User secrets file on disk, if present</span></span>
1. <span data-ttu-id="a67fa-123">环境变量</span><span class="sxs-lookup"><span data-stu-id="a67fa-123">Environment variables</span></span>
1. <span data-ttu-id="a67fa-124">命令行参数</span><span class="sxs-lookup"><span data-stu-id="a67fa-124">Command-line arguments</span></span>

## <a name="appsettingsjson-format-and-access"></a><span data-ttu-id="a67fa-125">格式和访问 appsettings.js</span><span class="sxs-lookup"><span data-stu-id="a67fa-125">appsettings.json format and access</span></span>

<span data-ttu-id="a67fa-126">文件*上的appsettings.js*可以通过结构化的值进行分层，如以下 JSON：</span><span class="sxs-lookup"><span data-stu-id="a67fa-126">The *appsettings.json* file can be hierarchical with values structured like the following JSON:</span></span>

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

<span data-ttu-id="a67fa-127">当出现前面的 JSON 时，配置系统平展子值并引用其完全限定的分层路径。</span><span class="sxs-lookup"><span data-stu-id="a67fa-127">When presented with the preceding JSON, the configuration system flattens child values and references their fully qualified hierarchical paths.</span></span> <span data-ttu-id="a67fa-128">冒号 (`:`) 字符分隔层次结构中的每个属性。</span><span class="sxs-lookup"><span data-stu-id="a67fa-128">A colon (`:`) character separates each property in the hierarchy.</span></span> <span data-ttu-id="a67fa-129">例如，配置项将 `section1:key0` 访问 `section1` 对象文字的 `key0` 值。</span><span class="sxs-lookup"><span data-stu-id="a67fa-129">For example, the configuration key `section1:key0` accesses the `section1` object literal's `key0` value.</span></span>

## <a name="user-secrets"></a><span data-ttu-id="a67fa-130">用户机密</span><span class="sxs-lookup"><span data-stu-id="a67fa-130">User secrets</span></span>

<span data-ttu-id="a67fa-131">用户机密包括：</span><span class="sxs-lookup"><span data-stu-id="a67fa-131">User secrets are:</span></span>

* <span data-ttu-id="a67fa-132">存储在开发人员工作站上的 JSON 文件中的配置值位于应用开发文件夹之外。</span><span class="sxs-lookup"><span data-stu-id="a67fa-132">Configuration values that are stored in a JSON file on the developer's workstation, outside of the app development folder.</span></span>
* <span data-ttu-id="a67fa-133">仅在环境中运行时加载 `Development` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-133">Only loaded when running in the `Development` environment.</span></span>
* <span data-ttu-id="a67fa-134">与特定应用相关联。</span><span class="sxs-lookup"><span data-stu-id="a67fa-134">Associated with a specific app.</span></span>
* <span data-ttu-id="a67fa-135">通过 .NET Core CLI 的命令进行管理 `user-secrets` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-135">Managed with the .NET Core CLI's `user-secrets` command.</span></span>

<span data-ttu-id="a67fa-136">通过执行以下命令为机密存储配置应用 `user-secrets` ：</span><span class="sxs-lookup"><span data-stu-id="a67fa-136">Configure your app for secrets storage by executing the `user-secrets` command:</span></span>

```dotnetcli
dotnet user-secrets init
```

<span data-ttu-id="a67fa-137">前面的命令将一个 `UserSecretsId` 元素添加到项目文件。</span><span class="sxs-lookup"><span data-stu-id="a67fa-137">The preceding command adds a `UserSecretsId` element to the project file.</span></span> <span data-ttu-id="a67fa-138">元素包含用于将机密与应用关联的 GUID。</span><span class="sxs-lookup"><span data-stu-id="a67fa-138">The element contains a GUID, which is used to associate secrets with the app.</span></span> <span data-ttu-id="a67fa-139">然后，可以使用命令定义机密 `set` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-139">You can then define a secret with the `set` command.</span></span> <span data-ttu-id="a67fa-140">例如：</span><span class="sxs-lookup"><span data-stu-id="a67fa-140">For example:</span></span>

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

<span data-ttu-id="a67fa-141">上述命令使 `Parent:ApiKey` 使用值的开发人员工作站上的配置密钥可用 `12345` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-141">The preceding command makes the `Parent:ApiKey` configuration key available on a developer's workstation with the value `12345`.</span></span>

<span data-ttu-id="a67fa-142">有关创建、存储和管理用户机密的详细信息，请参阅 ASP.NET Core 文档中的开发中的[应用机密的安全存储](/aspnet/core/security/app-secrets)。</span><span class="sxs-lookup"><span data-stu-id="a67fa-142">For more information about creating, storing, and managing user secrets, see the [Safe storage of app secrets in development in ASP.NET Core](/aspnet/core/security/app-secrets) document.</span></span>

## <a name="environment-variables"></a><span data-ttu-id="a67fa-143">环境变量</span><span class="sxs-lookup"><span data-stu-id="a67fa-143">Environment variables</span></span>

<span data-ttu-id="a67fa-144">将下一组值加载到应用配置中是系统的环境变量。</span><span class="sxs-lookup"><span data-stu-id="a67fa-144">The next set of values loaded into your app configuration is the system's environment variables.</span></span> <span data-ttu-id="a67fa-145">现在，你的所有系统环境变量设置都可以通过配置 API 来访问。</span><span class="sxs-lookup"><span data-stu-id="a67fa-145">All of your system's environment variable settings are now accessible to you through the configuration API.</span></span> <span data-ttu-id="a67fa-146">在应用中进行读取时，将按冒号字符分隔层次结构值。</span><span class="sxs-lookup"><span data-stu-id="a67fa-146">Hierarchical values are flattened and separated by colon characters when read inside your app.</span></span> <span data-ttu-id="a67fa-147">但是，某些操作系统不允许冒号字符环境变量名称。</span><span class="sxs-lookup"><span data-stu-id="a67fa-147">However, some operating systems don't allow the colon character environment variable names.</span></span> <span data-ttu-id="a67fa-148">ASP.NET Core 通过在访问时将具有双下划线 () 的值转换为冒号来解决此限制 `__` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-148">ASP.NET Core addresses this limitation by converting values that have double-underscores (`__`) into a colon when they're accessed.</span></span> <span data-ttu-id="a67fa-149">`Parent:ApiKey`可以通过环境变量重写上面的用户机密部分的值 `Parent__ApiKey` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-149">The `Parent:ApiKey` value from the user secrets section above can be overridden with the environment variable `Parent__ApiKey`.</span></span>

## <a name="command-line-arguments"></a><span data-ttu-id="a67fa-150">命令行参数</span><span class="sxs-lookup"><span data-stu-id="a67fa-150">Command-line arguments</span></span>

<span data-ttu-id="a67fa-151">当你的应用程序启动时，还可以将配置作为命令行参数提供。</span><span class="sxs-lookup"><span data-stu-id="a67fa-151">Configuration can also be provided as command-line arguments when your app is started.</span></span> <span data-ttu-id="a67fa-152">使用双划线 (`--`) 或正斜杠 (`/`) 表示法来指示要设置的配置值的名称以及要配置的值。</span><span class="sxs-lookup"><span data-stu-id="a67fa-152">Use the double-dash (`--`) or forward-slash (`/`) notation to indicate the name of the configuration value to set and the value to be configured.</span></span> <span data-ttu-id="a67fa-153">语法类似于以下命令：</span><span class="sxs-lookup"><span data-stu-id="a67fa-153">The syntax resembles the following commands:</span></span>

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a><span data-ttu-id="a67fa-154">返回 web.config</span><span class="sxs-lookup"><span data-stu-id="a67fa-154">The return of web.config</span></span>

<span data-ttu-id="a67fa-155">如果已将应用程序部署到 IIS 上的 Windows，则*web.config*文件仍会将 IIS 配置为管理你的应用程序。</span><span class="sxs-lookup"><span data-stu-id="a67fa-155">If you've deployed your app to Windows on IIS, the *web.config* file still configures IIS to manage your app.</span></span> <span data-ttu-id="a67fa-156">默认情况下，IIS 会将对 ASP.NET Core 模块的引用添加 (ANCM) 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-156">By default, IIS adds a reference to the ASP.NET Core Module (ANCM).</span></span> <span data-ttu-id="a67fa-157">ANCM 是一个本机 IIS 模块，它托管你的应用程序来代替 Kestrel web 服务器。</span><span class="sxs-lookup"><span data-stu-id="a67fa-157">ANCM is a native IIS module that hosts your app in place of the Kestrel web server.</span></span> <span data-ttu-id="a67fa-158">此*web.config*部分类似于下面的 XML 标记：</span><span class="sxs-lookup"><span data-stu-id="a67fa-158">This *web.config* section resembles the following XML markup:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

<span data-ttu-id="a67fa-159">应用特定的配置可以通过 `environmentVariables` 在元素中嵌套元素来定义 `aspNetCore` 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-159">App-specific configuration can be defined by nesting an `environmentVariables` element in the `aspNetCore` element.</span></span> <span data-ttu-id="a67fa-160">此部分中定义的值将作为环境变量提供给 ASP.NET Core 应用。</span><span class="sxs-lookup"><span data-stu-id="a67fa-160">The values defined in this section are presented to the ASP.NET Core app as environment variables.</span></span> <span data-ttu-id="a67fa-161">环境变量会在应用程序启动的这段时间内正确加载。</span><span class="sxs-lookup"><span data-stu-id="a67fa-161">The environment variables load appropriately during that segment of app startup.</span></span>

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a><span data-ttu-id="a67fa-162">在应用中读取配置</span><span class="sxs-lookup"><span data-stu-id="a67fa-162">Read configuration in the app</span></span>

<span data-ttu-id="a67fa-163">ASP.NET Core 提供通过接口的应用配置 <xref:Microsoft.Extensions.Configuration.IConfiguration> 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-163">ASP.NET Core provides app configuration through the <xref:Microsoft.Extensions.Configuration.IConfiguration> interface.</span></span> <span data-ttu-id="a67fa-164">此配置接口应由 Blazor 组件、 Blazor 页面以及需要访问配置的任何其他 ASP.NET Core 托管类请求。</span><span class="sxs-lookup"><span data-stu-id="a67fa-164">This configuration interface should be requested by your Blazor components, Blazor pages, and any other ASP.NET Core-managed class that needs access to configuration.</span></span> <span data-ttu-id="a67fa-165">ASP.NET Core 框架将用先前配置的解析配置自动填充此接口。</span><span class="sxs-lookup"><span data-stu-id="a67fa-165">The ASP.NET Core framework will automatically populate this interface with the resolved configuration configured earlier.</span></span> <span data-ttu-id="a67fa-166">在 Blazor 页或组件的 Razor 标记上，可以将对象注入到 `IConfiguration` `@inject` *Razor*文件顶部的指令，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a67fa-166">On a Blazor page or a component's Razor markup, you can inject the `IConfiguration` object with an `@inject` directive at the top of the *.razor* file like this:</span></span>

```razor
@inject IConfiguration Configuration
```

<span data-ttu-id="a67fa-167">前面的语句使 `IConfiguration` 对象在 `Configuration` Razor 模板的其余部分中可用作变量。</span><span class="sxs-lookup"><span data-stu-id="a67fa-167">This preceding statement makes the `IConfiguration` object available as the `Configuration` variable throughout the rest of the Razor template.</span></span>

<span data-ttu-id="a67fa-168">可以通过指定作为索引器参数查找的配置设置层次结构来读取各个配置设置：</span><span class="sxs-lookup"><span data-stu-id="a67fa-168">Individual configuration settings can be read by specifying the configuration setting hierarchy sought as an indexer parameter:</span></span>

```csharp
var mySetting = Configuration["section1:key0"];
```

<span data-ttu-id="a67fa-169">您可以通过使用方法检索整个配置节，方法是使用与 <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> 类似的语法检索特定位置的键集合， `GetSection("section1")` 以便从前面的示例中检索 section1 的配置。</span><span class="sxs-lookup"><span data-stu-id="a67fa-169">You can fetch entire configuration sections by using the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> method to retrieve a collection of keys at a specific location with a syntax similar to `GetSection("section1")` to retrieve the configuration for section1 from the earlier example.</span></span>

## <a name="strongly-typed-configuration"></a><span data-ttu-id="a67fa-170">强类型配置</span><span class="sxs-lookup"><span data-stu-id="a67fa-170">Strongly typed configuration</span></span>

<span data-ttu-id="a67fa-171">使用 Web 窗体，可以创建从类型和关联的类型继承的强类型配置类型 <xref:System.Configuration.ConfigurationSection> 。</span><span class="sxs-lookup"><span data-stu-id="a67fa-171">With Web Forms, it was possible to create a strongly typed configuration type that inherited from the <xref:System.Configuration.ConfigurationSection> type and associated types.</span></span> <span data-ttu-id="a67fa-172">`ConfigurationSection`允许您为这些配置值配置一些业务规则和处理。</span><span class="sxs-lookup"><span data-stu-id="a67fa-172">A `ConfigurationSection` allowed you to configure some business rules and processing for those configuration values.</span></span>

<span data-ttu-id="a67fa-173">在 ASP.NET Core 中，可以指定将接收配置值的类层次结构。</span><span class="sxs-lookup"><span data-stu-id="a67fa-173">In ASP.NET Core, you can specify a class hierarchy that will receive the configuration values.</span></span> <span data-ttu-id="a67fa-174">这些类：</span><span class="sxs-lookup"><span data-stu-id="a67fa-174">These classes:</span></span>

* <span data-ttu-id="a67fa-175">不需要从父类继承。</span><span class="sxs-lookup"><span data-stu-id="a67fa-175">Don't need to inherit from a parent class.</span></span>
* <span data-ttu-id="a67fa-176">应包括 `public` 与你要捕获的配置结构的属性和类型引用相匹配的属性。</span><span class="sxs-lookup"><span data-stu-id="a67fa-176">Should include `public` properties that match the properties and type references for the configuration structure you wish to capture.</span></span>

<span data-ttu-id="a67fa-177">对于前面*appsettings.js*的示例，可以定义以下类来捕获值：</span><span class="sxs-lookup"><span data-stu-id="a67fa-177">For the earlier *appsettings.json* sample, you could define the following classes to capture the values:</span></span>

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

<span data-ttu-id="a67fa-178">可以通过将以下行添加到方法来填充此类层次结构 `Startup.ConfigureServices` ：</span><span class="sxs-lookup"><span data-stu-id="a67fa-178">This class hierarchy can be populated by adding the following line to the `Startup.ConfigureServices` method:</span></span>

```csharp
services.Configure<MyConfig>(Configuration);
```

<span data-ttu-id="a67fa-179">在应用程序的其余部分中，你可以将输入参数添加到 `@inject` 类型的 Razor 模板中的类或指令， `IOptions<MyConfig>` 以接收强类型配置设置。</span><span class="sxs-lookup"><span data-stu-id="a67fa-179">In the rest of the app, you can add an input parameter to classes or an `@inject` directive in Razor templates of type `IOptions<MyConfig>` to receive the strongly typed configuration settings.</span></span> <span data-ttu-id="a67fa-180">`IOptions<MyConfig>.Value`属性将生成 `MyConfig` 从配置设置填充的值。</span><span class="sxs-lookup"><span data-stu-id="a67fa-180">The `IOptions<MyConfig>.Value` property will yield the `MyConfig` value populated from the configuration settings.</span></span>

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

<span data-ttu-id="a67fa-181">有关选项功能的详细信息，请参阅 ASP.NET Core 文档的[选项模式](/aspnet/core/fundamentals/configuration/options#options-interfaces)。</span><span class="sxs-lookup"><span data-stu-id="a67fa-181">More information about the Options feature can be found in the [Options pattern in ASP.NET Core](/aspnet/core/fundamentals/configuration/options#options-interfaces) document.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a67fa-182">[上一页](middleware.md)
>[下一页](security-authentication-authorization.md)</span><span class="sxs-lookup"><span data-stu-id="a67fa-182">[Previous](middleware.md)
[Next](security-authentication-authorization.md)</span></span>
