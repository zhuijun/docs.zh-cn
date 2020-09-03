---
title: ASP.NET Core 中断性变更
titleSuffix: ''
description: 列出 ASP.NET Core 中的中断性变更。
ms.date: 08/25/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 443494291f4ec58aecd7c8d8ed42cb4086e64095
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957725"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="b810a-103">ASP.NET Core 中断性变更</span><span class="sxs-lookup"><span data-stu-id="b810a-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="b810a-104">ASP.NET Core 提供 .NET Core 使用的 Web 应用开发功能。</span><span class="sxs-lookup"><span data-stu-id="b810a-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="b810a-105">选择以下链接之一，了解特定版本中的中断性变更：</span><span class="sxs-lookup"><span data-stu-id="b810a-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="b810a-106">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="b810a-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="b810a-107">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b810a-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="b810a-108">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b810a-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="b810a-109">本页记录了 ASP.NET Core 3.0、3.1 和 5.0 中的以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="b810a-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="b810a-110">已删除过时防伪、CORS、诊断、MVC 和路由 API</span><span class="sxs-lookup"><span data-stu-id="b810a-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="b810a-111">身份验证：Google+ 弃用</span><span class="sxs-lookup"><span data-stu-id="b810a-111">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="b810a-112">身份验证：已删除 HttpContext.Authentication 属性</span><span class="sxs-lookup"><span data-stu-id="b810a-112">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="b810a-113">身份验证：已替换 Newtonsoft.json 类型</span><span class="sxs-lookup"><span data-stu-id="b810a-113">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="b810a-114">身份验证：已更改 OAuthHandler ExchangeCodeAsync 签名</span><span class="sxs-lookup"><span data-stu-id="b810a-114">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="b810a-115">授权：AddAuthorization 重载已移到不同的程序集</span><span class="sxs-lookup"><span data-stu-id="b810a-115">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="b810a-116">授权：已从 AuthorizationFilterContext.Filters 中删除 IAllowAnonymous</span><span class="sxs-lookup"><span data-stu-id="b810a-116">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="b810a-117">授权：IAuthorizationPolicyProvider 实现需要新方法</span><span class="sxs-lookup"><span data-stu-id="b810a-117">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="b810a-118">授权：终结点路由中的资源为 HttpContext</span><span class="sxs-lookup"><span data-stu-id="b810a-118">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="b810a-119">Azure:Microsoft 预先指定的 Azure 集成包已删除</span><span class="sxs-lookup"><span data-stu-id="b810a-119">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="b810a-120">BinaryFormatter 序列化方法已过时，并且已在 ASP.NET 应用中禁用</span><span class="sxs-lookup"><span data-stu-id="b810a-120">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="b810a-121">Blazor：在编译时从组件中剪裁掉无意义的空白</span><span class="sxs-lookup"><span data-stu-id="b810a-121">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="b810a-122">Blazor：NuGet 包的目标框架已更改</span><span class="sxs-lookup"><span data-stu-id="b810a-122">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="b810a-123">缓存：已删除 CompactOnMemoryPressure 属性</span><span class="sxs-lookup"><span data-stu-id="b810a-123">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="b810a-124">缓存：Microsoft.Extensions.Caching.SqlServer 使用新的 SqlClient 包</span><span class="sxs-lookup"><span data-stu-id="b810a-124">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="b810a-125">缓存：ResponseCaching“Pubternal”类型已更改为内部类型</span><span class="sxs-lookup"><span data-stu-id="b810a-125">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="b810a-126">数据保护：DataProtection.AzureStorage 使用新的 Azure 存储 API</span><span class="sxs-lookup"><span data-stu-id="b810a-126">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="b810a-127">扩展：影响某些 NuGet 包的包引用更改</span><span class="sxs-lookup"><span data-stu-id="b810a-127">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="b810a-128">托管：已从 Windows 托管捆绑包中删除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="b810a-128">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="b810a-129">托管：通用主机限制 Startup 构造函数注入</span><span class="sxs-lookup"><span data-stu-id="b810a-129">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="b810a-130">托管：已为 IIS 进程外应用启用 HTTPS 重定向</span><span class="sxs-lookup"><span data-stu-id="b810a-130">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="b810a-131">托管：已替换 IHostingEnvironment 和 IApplicationLifetime 类型</span><span class="sxs-lookup"><span data-stu-id="b810a-131">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="b810a-132">托管：已从 WebHostBuilder 依赖项中删除 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="b810a-132">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="b810a-133">HTTP：标记为已过时并被替换的 Kestrel 和 IIS BadHttpRequestException 类型</span><span class="sxs-lookup"><span data-stu-id="b810a-133">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="b810a-134">HTTP：浏览器的 SameSite 更改会影响身份验证</span><span class="sxs-lookup"><span data-stu-id="b810a-134">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="b810a-135">HTTP：已删除 DefaultHttpContext 扩展性</span><span class="sxs-lookup"><span data-stu-id="b810a-135">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="b810a-136">HTTP：HeaderNames 字段已更改为静态只读</span><span class="sxs-lookup"><span data-stu-id="b810a-136">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="b810a-137">HTTP：IHttpClientFactory 创建的 HttpClient 实例记录整数状态代码</span><span class="sxs-lookup"><span data-stu-id="b810a-137">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="b810a-138">HTTP：响应正文基础结构更改</span><span class="sxs-lookup"><span data-stu-id="b810a-138">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="b810a-139">HTTP：已更改某些 Cookie SameSite 默认值</span><span class="sxs-lookup"><span data-stu-id="b810a-139">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="b810a-140">HTTP：已默认禁用同步 IO</span><span class="sxs-lookup"><span data-stu-id="b810a-140">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="b810a-141">HttpSys：默认情况下禁用客户端证书重新协商</span><span class="sxs-lookup"><span data-stu-id="b810a-141">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="b810a-142">标识：已删除 AddDefaultUI 方法重载</span><span class="sxs-lookup"><span data-stu-id="b810a-142">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="b810a-143">标识：UI 启动版本更改</span><span class="sxs-lookup"><span data-stu-id="b810a-143">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="b810a-144">标识：对于未经身份验证的标识，SignInAsync 会引发异常</span><span class="sxs-lookup"><span data-stu-id="b810a-144">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="b810a-145">标识：SignInManager 构造函数接受新参数</span><span class="sxs-lookup"><span data-stu-id="b810a-145">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="b810a-146">标识：UI 使用静态 Web 资产功能</span><span class="sxs-lookup"><span data-stu-id="b810a-146">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="b810a-147">IIS：保留 UrlRewrite 中间件查询字符串</span><span class="sxs-lookup"><span data-stu-id="b810a-147">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="b810a-148">Kestrel：默认检测运行时的配置更改</span><span class="sxs-lookup"><span data-stu-id="b810a-148">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="b810a-149">Kestrel：已删除连接适配器</span><span class="sxs-lookup"><span data-stu-id="b810a-149">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="b810a-150">Kestrel：默认支持的 TLS 协议版本已更改</span><span class="sxs-lookup"><span data-stu-id="b810a-150">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="b810a-151">Kestrel：已删除空 HTTPS 程序集</span><span class="sxs-lookup"><span data-stu-id="b810a-151">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="b810a-152">Kestrel：在不兼容的 Windows 版本上通过 TLS 禁用 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="b810a-152">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="b810a-153">Kestrel：Libuv 传输标记为已过时</span><span class="sxs-lookup"><span data-stu-id="b810a-153">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="b810a-154">Kestrel：请求尾部标头已移到新集合</span><span class="sxs-lookup"><span data-stu-id="b810a-154">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="b810a-155">Kestrel：传输抽象层更改</span><span class="sxs-lookup"><span data-stu-id="b810a-155">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="b810a-156">本地化：API 已标记为已过时</span><span class="sxs-lookup"><span data-stu-id="b810a-156">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="b810a-157">本地化：已删除“Pubternal”API</span><span class="sxs-lookup"><span data-stu-id="b810a-157">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="b810a-158">本地化：请求本地化中间件中删除了已过时的构造函数</span><span class="sxs-lookup"><span data-stu-id="b810a-158">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="b810a-159">本地化：ResourceManagerWithCultureStringLocalizer 类和 WithCulture 接口成员已删除</span><span class="sxs-lookup"><span data-stu-id="b810a-159">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="b810a-160">日志记录：已将 DebugLogger 类设为内部类</span><span class="sxs-lookup"><span data-stu-id="b810a-160">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="b810a-161">中间件：数据库错误页标记为已过时</span><span class="sxs-lookup"><span data-stu-id="b810a-161">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="b810a-162">MVC：已删除控制器操作 Async 后缀</span><span class="sxs-lookup"><span data-stu-id="b810a-162">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="b810a-163">MVC：JsonResult 已移至 Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="b810a-163">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="b810a-164">MVC：已弃用预编译工具</span><span class="sxs-lookup"><span data-stu-id="b810a-164">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="b810a-165">MVC：类型已更改为内部</span><span class="sxs-lookup"><span data-stu-id="b810a-165">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="b810a-166">MVC：已删除 Web API 兼容性填充码</span><span class="sxs-lookup"><span data-stu-id="b810a-166">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="b810a-167">Razor：已删除 RazorTemplateEngine API</span><span class="sxs-lookup"><span data-stu-id="b810a-167">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="b810a-168">Razor：运行时编译已移到包</span><span class="sxs-lookup"><span data-stu-id="b810a-168">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="b810a-169">安全性：Cookie 名称编码已删除</span><span class="sxs-lookup"><span data-stu-id="b810a-169">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="b810a-170">安全性：IdentityModel NuGet 包版本已更新</span><span class="sxs-lookup"><span data-stu-id="b810a-170">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="b810a-171">会话状态：已删除过时的 API</span><span class="sxs-lookup"><span data-stu-id="b810a-171">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="b810a-172">共享框架：已从 Microsoft.AspNetCore.App 中删除程序集</span><span class="sxs-lookup"><span data-stu-id="b810a-172">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="b810a-173">共享框架：已删除 Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="b810a-173">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="b810a-174">SignalR：已替换 HandshakeProtocol.SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="b810a-174">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="b810a-175">SignalR：已删除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="b810a-175">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="b810a-176">SignalR：已更改 HubConnectionContext 构造函数</span><span class="sxs-lookup"><span data-stu-id="b810a-176">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="b810a-177">SignalR：JavaScript 客户端包名称更改</span><span class="sxs-lookup"><span data-stu-id="b810a-177">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="b810a-178">SignalR：MessagePack 中心协议已移至 MessagePack 2.x 包</span><span class="sxs-lookup"><span data-stu-id="b810a-178">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="b810a-179">SignalR：MessagePack 中心协议选项类型已更改</span><span class="sxs-lookup"><span data-stu-id="b810a-179">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="b810a-180">SignalR：过时的 API</span><span class="sxs-lookup"><span data-stu-id="b810a-180">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="b810a-181">SignalR：UseSignalR 和 UseConnections 方法已删除</span><span class="sxs-lookup"><span data-stu-id="b810a-181">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="b810a-182">SPA：SpaServices 和 NodeServices 控制台记录器回退默认更改</span><span class="sxs-lookup"><span data-stu-id="b810a-182">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="b810a-183">SPA：SpaServices 和 NodeServices 已标记为过时</span><span class="sxs-lookup"><span data-stu-id="b810a-183">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="b810a-184">静态文件：CSV 内容类型已更改为符合标准</span><span class="sxs-lookup"><span data-stu-id="b810a-184">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="b810a-185">目标框架：不支持 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b810a-185">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="b810a-186">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="b810a-186">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

***

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

***

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

***

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

***

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

***

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

***

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

***

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

***

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

***
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

***

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

***

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

***

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

***

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

***

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="b810a-187">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b810a-187">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="b810a-188">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b810a-188">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

***

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

***

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

***

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

***

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

***

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

***

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

***

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

***

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

***

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

***

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

***

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

***

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

***

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

***

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

***

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

***

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

***

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

***

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

***

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

***

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

***

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

***

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

***

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

***

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

***

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

***

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

***

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

***

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

***

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

***

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

***

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

***

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

***

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

***

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

***

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

***

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

***

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

***

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

***

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

***

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

***

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

***

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

***

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

***

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

***

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

***

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

***

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

***

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

***

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

***
