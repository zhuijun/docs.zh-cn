---
title: ASP.NET Core 中断性变更
titleSuffix: ''
description: 列出 ASP.NET Core 中的中断性变更。
ms.date: 07/08/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: ca9e615e88964e1c37e9c0b721bca8c34bf671ac
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174388"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="ee45c-103">ASP.NET Core 中断性变更</span><span class="sxs-lookup"><span data-stu-id="ee45c-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="ee45c-104">ASP.NET Core 提供 .NET Core 使用的 Web 应用开发功能。</span><span class="sxs-lookup"><span data-stu-id="ee45c-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="ee45c-105">本页记录了以下中断性变更：</span><span class="sxs-lookup"><span data-stu-id="ee45c-105">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="ee45c-106">已删除过时防伪、CORS、诊断、MVC 和路由 API</span><span class="sxs-lookup"><span data-stu-id="ee45c-106">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="ee45c-107">身份验证：Google+ 弃用</span><span class="sxs-lookup"><span data-stu-id="ee45c-107">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="ee45c-108">身份验证：已删除 HttpContext.Authentication 属性</span><span class="sxs-lookup"><span data-stu-id="ee45c-108">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="ee45c-109">身份验证：已替换 Newtonsoft.json 类型</span><span class="sxs-lookup"><span data-stu-id="ee45c-109">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="ee45c-110">身份验证：已更改 OAuthHandler ExchangeCodeAsync 签名</span><span class="sxs-lookup"><span data-stu-id="ee45c-110">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="ee45c-111">授权：AddAuthorization 重载已移到不同的程序集</span><span class="sxs-lookup"><span data-stu-id="ee45c-111">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="ee45c-112">授权：已从 AuthorizationFilterContext.Filters 中删除 IAllowAnonymous</span><span class="sxs-lookup"><span data-stu-id="ee45c-112">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="ee45c-113">授权：IAuthorizationPolicyProvider 实现需要新方法</span><span class="sxs-lookup"><span data-stu-id="ee45c-113">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="ee45c-114">Azure:Microsoft 预先指定的 Azure 集成包已删除</span><span class="sxs-lookup"><span data-stu-id="ee45c-114">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="ee45c-115">Blazor：在编译时从组件中剪裁掉无意义的空白</span><span class="sxs-lookup"><span data-stu-id="ee45c-115">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="ee45c-116">缓存：已删除 CompactOnMemoryPressure 属性</span><span class="sxs-lookup"><span data-stu-id="ee45c-116">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="ee45c-117">缓存：Microsoft.Extensions.Caching.SqlServer 使用新的 SqlClient 包</span><span class="sxs-lookup"><span data-stu-id="ee45c-117">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="ee45c-118">缓存：ResponseCaching“Pubternal”类型已更改为内部类型</span><span class="sxs-lookup"><span data-stu-id="ee45c-118">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="ee45c-119">数据保护：DataProtection.AzureStorage 使用新的 Azure 存储 API</span><span class="sxs-lookup"><span data-stu-id="ee45c-119">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis)
- [<span data-ttu-id="ee45c-120">扩展：影响某些 NuGet 包的包引用更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-120">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="ee45c-121">托管：已从 Windows 托管捆绑包中删除 AspNetCoreModule V1</span><span class="sxs-lookup"><span data-stu-id="ee45c-121">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="ee45c-122">托管：通用主机限制 Startup 构造函数注入</span><span class="sxs-lookup"><span data-stu-id="ee45c-122">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="ee45c-123">托管：已为 IIS 进程外应用启用 HTTPS 重定向</span><span class="sxs-lookup"><span data-stu-id="ee45c-123">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="ee45c-124">托管：已替换 IHostingEnvironment 和 IApplicationLifetime 类型</span><span class="sxs-lookup"><span data-stu-id="ee45c-124">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="ee45c-125">托管：已从 WebHostBuilder 依赖项中删除 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="ee45c-125">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="ee45c-126">HTTP：标记为已过时并被替换的 Kestrel 和 IIS BadHttpRequestException 类型</span><span class="sxs-lookup"><span data-stu-id="ee45c-126">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="ee45c-127">HTTP：浏览器的 SameSite 更改会影响身份验证</span><span class="sxs-lookup"><span data-stu-id="ee45c-127">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="ee45c-128">HTTP：已删除 DefaultHttpContext 扩展性</span><span class="sxs-lookup"><span data-stu-id="ee45c-128">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="ee45c-129">HTTP：HeaderNames 字段已更改为静态只读</span><span class="sxs-lookup"><span data-stu-id="ee45c-129">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="ee45c-130">HTTP：IHttpClientFactory 创建的 HttpClient 实例记录整数状态代码</span><span class="sxs-lookup"><span data-stu-id="ee45c-130">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="ee45c-131">HTTP：响应正文基础结构更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-131">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="ee45c-132">HTTP：已更改某些 Cookie SameSite 默认值</span><span class="sxs-lookup"><span data-stu-id="ee45c-132">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="ee45c-133">HTTP：已默认禁用同步 IO</span><span class="sxs-lookup"><span data-stu-id="ee45c-133">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="ee45c-134">HttpSys：默认情况下禁用客户端证书重新协商</span><span class="sxs-lookup"><span data-stu-id="ee45c-134">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="ee45c-135">标识：已删除 AddDefaultUI 方法重载</span><span class="sxs-lookup"><span data-stu-id="ee45c-135">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="ee45c-136">标识：UI 启动版本更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-136">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="ee45c-137">标识：对于未经身份验证的标识，SignInAsync 会引发异常</span><span class="sxs-lookup"><span data-stu-id="ee45c-137">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="ee45c-138">标识：SignInManager 构造函数接受新参数</span><span class="sxs-lookup"><span data-stu-id="ee45c-138">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="ee45c-139">标识：UI 使用静态 Web 资产功能</span><span class="sxs-lookup"><span data-stu-id="ee45c-139">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="ee45c-140">IIS：保留 UrlRewrite 中间件查询字符串</span><span class="sxs-lookup"><span data-stu-id="ee45c-140">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="ee45c-141">Kestrel：默认检测运行时的配置更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-141">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="ee45c-142">Kestrel：已删除连接适配器</span><span class="sxs-lookup"><span data-stu-id="ee45c-142">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="ee45c-143">Kestrel：默认支持的 TLS 协议版本已更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-143">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="ee45c-144">Kestrel：已删除空 HTTPS 程序集</span><span class="sxs-lookup"><span data-stu-id="ee45c-144">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="ee45c-145">Kestrel：在不兼容的 Windows 版本上通过 TLS 禁用 HTTP/2</span><span class="sxs-lookup"><span data-stu-id="ee45c-145">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="ee45c-146">Kestrel：请求尾部标头已移到新集合</span><span class="sxs-lookup"><span data-stu-id="ee45c-146">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="ee45c-147">Kestrel：传输抽象层更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-147">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="ee45c-148">本地化：API 已标记为已过时</span><span class="sxs-lookup"><span data-stu-id="ee45c-148">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="ee45c-149">本地化：已删除“Pubternal”API</span><span class="sxs-lookup"><span data-stu-id="ee45c-149">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="ee45c-150">本地化：ResourceManagerWithCultureStringLocalizer 类和 WithCulture 接口成员已删除</span><span class="sxs-lookup"><span data-stu-id="ee45c-150">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="ee45c-151">日志记录：已将 DebugLogger 类设为内部类</span><span class="sxs-lookup"><span data-stu-id="ee45c-151">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="ee45c-152">MVC：已删除控制器操作 Async 后缀</span><span class="sxs-lookup"><span data-stu-id="ee45c-152">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="ee45c-153">MVC：JsonResult 已移至 Microsoft.AspNetCore.Mvc.Core</span><span class="sxs-lookup"><span data-stu-id="ee45c-153">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="ee45c-154">MVC：已弃用预编译工具</span><span class="sxs-lookup"><span data-stu-id="ee45c-154">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="ee45c-155">MVC：类型已更改为内部</span><span class="sxs-lookup"><span data-stu-id="ee45c-155">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="ee45c-156">MVC：已删除 Web API 兼容性填充码</span><span class="sxs-lookup"><span data-stu-id="ee45c-156">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="ee45c-157">Razor：运行时编译已移到包</span><span class="sxs-lookup"><span data-stu-id="ee45c-157">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="ee45c-158">会话状态：已删除过时的 API</span><span class="sxs-lookup"><span data-stu-id="ee45c-158">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="ee45c-159">共享框架：已从 Microsoft.AspNetCore.App 中删除程序集</span><span class="sxs-lookup"><span data-stu-id="ee45c-159">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="ee45c-160">共享框架：已删除 Microsoft.AspNetCore.All</span><span class="sxs-lookup"><span data-stu-id="ee45c-160">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="ee45c-161">SignalR：已替换 HandshakeProtocol.SuccessHandshakeData</span><span class="sxs-lookup"><span data-stu-id="ee45c-161">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="ee45c-162">SignalR：已删除 HubConnection 方法</span><span class="sxs-lookup"><span data-stu-id="ee45c-162">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="ee45c-163">SignalR：已更改 HubConnectionContext 构造函数</span><span class="sxs-lookup"><span data-stu-id="ee45c-163">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="ee45c-164">SignalR：JavaScript 客户端包名称更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-164">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="ee45c-165">SignalR：MessagePack 中心协议已移至 MessagePack 2.x 包</span><span class="sxs-lookup"><span data-stu-id="ee45c-165">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="ee45c-166">SignalR：MessagePack 中心协议选项类型已更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-166">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="ee45c-167">SignalR：过时的 API</span><span class="sxs-lookup"><span data-stu-id="ee45c-167">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="ee45c-168">SignalR：UseSignalR 和 UseConnections 方法已删除</span><span class="sxs-lookup"><span data-stu-id="ee45c-168">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="ee45c-169">SPA：SpaServices 和 NodeServices 控制台记录器回退默认更改</span><span class="sxs-lookup"><span data-stu-id="ee45c-169">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="ee45c-170">SPA：SpaServices 和 NodeServices 已标记为过时</span><span class="sxs-lookup"><span data-stu-id="ee45c-170">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="ee45c-171">静态文件：CSV 内容类型已更改为符合标准</span><span class="sxs-lookup"><span data-stu-id="ee45c-171">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="ee45c-172">目标框架：不支持 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee45c-172">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="ee45c-173">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="ee45c-173">ASP.NET Core 5.0</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

***

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

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

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

***

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

***

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

***

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

***

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

***

## <a name="aspnet-core-31"></a><span data-ttu-id="ee45c-174">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="ee45c-174">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="ee45c-175">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ee45c-175">ASP.NET Core 3.0</span></span>

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
