---
title: 使用 IHttpClientFactory 实现复原 HTTP 请求
description: 了解如何使用自 .NET Core 2.1 起可用的 IHttpClientFactory 来创建 `HttpClient` 实例，使其更轻松地在应用程序中使用。
ms.date: 08/31/2020
ms.openlocfilehash: ae093ef960b2540bf4916bf72ad3bec51fa33ebe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152567"
---
# <a name="use-ihttpclientfactory-to-implement-resilient-http-requests"></a><span data-ttu-id="71bc0-103">使用 IHttpClientFactory 实现复原 HTTP 请求</span><span class="sxs-lookup"><span data-stu-id="71bc0-103">Use IHttpClientFactory to implement resilient HTTP requests</span></span>

<span data-ttu-id="71bc0-104"><xref:System.Net.Http.IHttpClientFactory> 是由自 .NET Core 2.1 起可用的固定工厂 `DefaultHttpClientFactory` 实现的协定，用于创建在应用程序中使用的 <xref:System.Net.Http.HttpClient> 实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-104"><xref:System.Net.Http.IHttpClientFactory> is a contract implemented by `DefaultHttpClientFactory`, an opinionated factory, available since .NET Core 2.1, for creating <xref:System.Net.Http.HttpClient> instances to be used in your applications.</span></span>

## <a name="issues-with-the-original-httpclient-class-available-in-net-core"></a><span data-ttu-id="71bc0-105">.NET Core 中提供的原始 HttpClient 类的相关问题</span><span class="sxs-lookup"><span data-stu-id="71bc0-105">Issues with the original HttpClient class available in .NET Core</span></span>

<span data-ttu-id="71bc0-106">常见的原始 <xref:System.Net.Http.HttpClient> 类非常易于使用，但在某些情况下，许多开发人员却并未正确使用该类。</span><span class="sxs-lookup"><span data-stu-id="71bc0-106">The original and well-known <xref:System.Net.Http.HttpClient> class can be easily used, but in some cases, it isn't being properly used by many developers.</span></span>

<span data-ttu-id="71bc0-107">虽然此类实现 `IDisposable`，但在 `using` 语句中声明和实例化它并非首选操作，因为释放 `HttpClient` 对象时，基础套接字不会立即释放，这可能会导致套接字耗尽问题。</span><span class="sxs-lookup"><span data-stu-id="71bc0-107">Though this class implements `IDisposable`, declaring and instantiating it within a `using` statement is not preferred because when the `HttpClient` object gets disposed of, the underlying socket is not immediately released, which can lead to a _socket exhaustion_ problem.</span></span> <span data-ttu-id="71bc0-108">有关此问题的详细信息，请参阅[你正在以错误方式使用 HttpClient，这将导致软件受损](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/)的博客文章。</span><span class="sxs-lookup"><span data-stu-id="71bc0-108">For more information about this issue, see the blog post [You're using HttpClient wrong and it's destabilizing your software](https://aspnetmonsters.com/2016/08/2016-08-27-httpclientwrong/).</span></span>

<span data-ttu-id="71bc0-109">因此，`HttpClient` 应进行一次实例化并在应用程序的生命周期中重复使用。</span><span class="sxs-lookup"><span data-stu-id="71bc0-109">Therefore, `HttpClient` is intended to be instantiated once and reused throughout the life of an application.</span></span> <span data-ttu-id="71bc0-110">在负载较重的情况下，实例化每个请求的 `HttpClient` 类将耗尽可用的套接字数。</span><span class="sxs-lookup"><span data-stu-id="71bc0-110">Instantiating an `HttpClient` class for every request will exhaust the number of sockets available under heavy loads.</span></span> <span data-ttu-id="71bc0-111">该问题会导致 `SocketException` 错误。</span><span class="sxs-lookup"><span data-stu-id="71bc0-111">That issue will result in `SocketException` errors.</span></span> <span data-ttu-id="71bc0-112">要解决此问题，可能的方法是将 `HttpClient` 对象创建为单一对象或静态对象，请参阅[关于 HttpClient 用法的 Microsoft 文章](../../../csharp/tutorials/console-webapiclient.md)中的说明。</span><span class="sxs-lookup"><span data-stu-id="71bc0-112">Possible approaches to solve that problem are based on the creation of the `HttpClient` object as singleton or static, as explained in this [Microsoft article on HttpClient usage](../../../csharp/tutorials/console-webapiclient.md).</span></span> <span data-ttu-id="71bc0-113">对于生存期较短的控制台应用或一天运行几次的类似应用，这可能是一个不错的解决方案。</span><span class="sxs-lookup"><span data-stu-id="71bc0-113">This can be a good solution for short-lived console apps or similar, that run a few times a day.</span></span>

<span data-ttu-id="71bc0-114">在长期运行的进程中使用 `HttpClient` 的共享实例时，开发人员会遇到另一个问题。</span><span class="sxs-lookup"><span data-stu-id="71bc0-114">Another issue that developers run into is when using a shared instance of `HttpClient` in long-running processes.</span></span> <span data-ttu-id="71bc0-115">在将 HttpClient 实例化为单一实例或静态对象的情况下，它无法处理 DNS 更改，如 dotnet/runtime GitHub 存储库的此[问题](https://github.com/dotnet/runtime/issues/18348)中所述。</span><span class="sxs-lookup"><span data-stu-id="71bc0-115">In a situation where the HttpClient is instantiated as a singleton or a static object, it fails to handle the DNS changes as described in this [issue](https://github.com/dotnet/runtime/issues/18348) of the dotnet/runtime GitHub repository.</span></span>

<span data-ttu-id="71bc0-116">但是，问题实际上不是 `HttpClient` 本身，而是 [HttpClient 的默认构造函数](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor)，因为它创建了一个新的实际 <xref:System.Net.Http.HttpMessageHandler> 实例，该实例具有上面提到的“套接字耗尽”和 DNS 更改问题  。</span><span class="sxs-lookup"><span data-stu-id="71bc0-116">However, the issue isn't really with `HttpClient` per se, but with the [default constructor for HttpClient](/dotnet/api/system.net.http.httpclient.-ctor?view=netcore-3.1#System_Net_Http_HttpClient__ctor), because it creates a new concrete instance of <xref:System.Net.Http.HttpMessageHandler>, which is the one that has *sockets exhaustion* and DNS changes issues mentioned above.</span></span>

<span data-ttu-id="71bc0-117">若要解决上述问题并使 `HttpClient` 实例可管理，.NET Core 2.1 引入了 <xref:System.Net.Http.IHttpClientFactory> 接口，该接口可用于在应用中通过依赖关系注入 (DI) 来配置和创建 `HttpClient` 实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-117">To address the issues mentioned above and to make `HttpClient` instances manageable, .NET Core 2.1 introduced the <xref:System.Net.Http.IHttpClientFactory> interface which can be used to configure and create `HttpClient` instances in an app through Dependency Injection (DI).</span></span> <span data-ttu-id="71bc0-118">它还提供基于 Polly 的中间件的扩展，以利用 HttpClient 中的委托处理程序。</span><span class="sxs-lookup"><span data-stu-id="71bc0-118">It also provides extensions for Polly-based middleware to take advantage of delegating handlers in HttpClient.</span></span>

<span data-ttu-id="71bc0-119">[Polly](http://www.thepollyproject.org/) 是瞬态故障处理库，它可以通过流畅且线程安全的方式使用一些预定义的策略，帮助开发人员为其应用程序增加弹性。</span><span class="sxs-lookup"><span data-stu-id="71bc0-119">[Polly](http://www.thepollyproject.org/) is a transient-fault-handling library that helps developers add resiliency to their applications, by using some pre-defined policies in a fluent and thread-safe manner.</span></span>

## <a name="benefits-of-using-ihttpclientfactory"></a><span data-ttu-id="71bc0-120">使用 IHttpClientFactory 的好处</span><span class="sxs-lookup"><span data-stu-id="71bc0-120">Benefits of using IHttpClientFactory</span></span>

<span data-ttu-id="71bc0-121">同时实现 <xref:System.Net.Http.IHttpMessageHandlerFactory> 的 <xref:System.Net.Http.IHttpClientFactory> 当前实现具有以下优势：</span><span class="sxs-lookup"><span data-stu-id="71bc0-121">The current implementation of <xref:System.Net.Http.IHttpClientFactory>, that also implements <xref:System.Net.Http.IHttpMessageHandlerFactory>, offers the following benefits:</span></span>

- <span data-ttu-id="71bc0-122">提供一个中心位置，用于命名和配置逻辑 `HttpClient` 对象。</span><span class="sxs-lookup"><span data-stu-id="71bc0-122">Provides a central location for naming and configuring logical `HttpClient` objects.</span></span> <span data-ttu-id="71bc0-123">例如，可以配置预配置的客户端（服务代理）以访问特定微服务。</span><span class="sxs-lookup"><span data-stu-id="71bc0-123">For example, you may configure a client (Service Agent) that's pre-configured to access a specific microservice.</span></span>
- <span data-ttu-id="71bc0-124">通过后列方式整理出站中间件的概念：在 `HttpClient` 中委托处理程序并实现基于 Polly 的中间件以利用 Polly 的复原策略。</span><span class="sxs-lookup"><span data-stu-id="71bc0-124">Codify the concept of outgoing middleware via delegating handlers in `HttpClient` and implementing Polly-based middleware to take advantage of Polly's policies for resiliency.</span></span>
- <span data-ttu-id="71bc0-125">`HttpClient` 已经具有委托处理程序的概念，这些委托处理程序可以链接在一起，处理出站 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="71bc0-125">`HttpClient` already has the concept of delegating handlers that could be linked together for outgoing HTTP requests.</span></span> <span data-ttu-id="71bc0-126">将 HTTP 客户端注册到工厂后，可使用一个 Polly 处理程序将 Polly 策略用于重试、断路器等。</span><span class="sxs-lookup"><span data-stu-id="71bc0-126">You can register HTTP clients into the factory and you can use a Polly handler to use Polly policies for Retry, CircuitBreakers, and so on.</span></span>
- <span data-ttu-id="71bc0-127">管理 <xref:System.Net.Http.HttpMessageHandler> 的生存期，避免在自行管理 `HttpClient` 生存期时出现上述问题。</span><span class="sxs-lookup"><span data-stu-id="71bc0-127">Manage the lifetime of <xref:System.Net.Http.HttpMessageHandler> to avoid the mentioned problems/issues that can occur when managing `HttpClient` lifetimes yourself.</span></span>

> [!TIP]
> <span data-ttu-id="71bc0-128">由于关联的 `HttpMessageHandler` 由工厂管理，因此可安全释放由 DI 注入的 `HttpClient` 实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-128">The `HttpClient` instances injected by DI, can be disposed of safely, because the associated `HttpMessageHandler` is managed by the factory.</span></span> <span data-ttu-id="71bc0-129">事实上，注入的 `HttpClient` 实例是从 DI 角度区分范围的  。</span><span class="sxs-lookup"><span data-stu-id="71bc0-129">As a matter of fact, injected `HttpClient` instances are *Scoped* from a DI perspective.</span></span>

> [!NOTE]
> <span data-ttu-id="71bc0-130">`IHttpClientFactory` (`DefaultHttpClientFactory`) 实现与 `Microsoft.Extensions.DependencyInjection` NuGet 包中的 DI 实现紧密关联。</span><span class="sxs-lookup"><span data-stu-id="71bc0-130">The implementation of `IHttpClientFactory` (`DefaultHttpClientFactory`) is tightly tied to the DI implementation in the `Microsoft.Extensions.DependencyInjection` NuGet package.</span></span> <span data-ttu-id="71bc0-131">有关使用其他 DI 容器的详细信息，请参阅此 [GitHub 讨论](https://github.com/dotnet/extensions/issues/1345)。</span><span class="sxs-lookup"><span data-stu-id="71bc0-131">For more information about using other DI containers, see this [GitHub discussion](https://github.com/dotnet/extensions/issues/1345).</span></span>

## <a name="multiple-ways-to-use-ihttpclientfactory"></a><span data-ttu-id="71bc0-132">IHttpClientFactory 的多种用法</span><span class="sxs-lookup"><span data-stu-id="71bc0-132">Multiple ways to use IHttpClientFactory</span></span>

<span data-ttu-id="71bc0-133">可以通过多种方法在应用程序中使用 `IHttpClientFactory`：</span><span class="sxs-lookup"><span data-stu-id="71bc0-133">There are several ways that you can use `IHttpClientFactory` in your application:</span></span>

- <span data-ttu-id="71bc0-134">基本用法</span><span class="sxs-lookup"><span data-stu-id="71bc0-134">Basic usage</span></span>
- <span data-ttu-id="71bc0-135">使用命名客户端</span><span class="sxs-lookup"><span data-stu-id="71bc0-135">Use Named Clients</span></span>
- <span data-ttu-id="71bc0-136">使用类型化客户端</span><span class="sxs-lookup"><span data-stu-id="71bc0-136">Use Typed Clients</span></span>
- <span data-ttu-id="71bc0-137">使用生成的客户端</span><span class="sxs-lookup"><span data-stu-id="71bc0-137">Use Generated Clients</span></span>

<span data-ttu-id="71bc0-138">为简洁起见，本指南介绍了使用 `IHttpClientFactory` 的最结构化的方法，即使用类型化客户端（服务代理模式）。</span><span class="sxs-lookup"><span data-stu-id="71bc0-138">For the sake of brevity, this guidance shows the most structured way to use `IHttpClientFactory`, which is to use Typed Clients (Service Agent pattern).</span></span> <span data-ttu-id="71bc0-139">不过，所有选项均已记录，并且当前在此[涵盖 `IHttpClientFactory` 用法的文章](/aspnet/core/fundamentals/http-requests#consumption-patterns)中列出。</span><span class="sxs-lookup"><span data-stu-id="71bc0-139">However, all options are documented and are currently listed in this [article covering the `IHttpClientFactory` usage](/aspnet/core/fundamentals/http-requests#consumption-patterns).</span></span>

## <a name="how-to-use-typed-clients-with-ihttpclientfactory"></a><span data-ttu-id="71bc0-140">如何结合使用类型化客户端和 IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="71bc0-140">How to use Typed Clients with IHttpClientFactory</span></span>

<span data-ttu-id="71bc0-141">那么，什么是“类型化客户端”？</span><span class="sxs-lookup"><span data-stu-id="71bc0-141">So, what's a "Typed Client"?</span></span> <span data-ttu-id="71bc0-142">它只是为某些特定用途预配置的 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="71bc0-142">It's just an `HttpClient` that's pre-configured for some specific use.</span></span> <span data-ttu-id="71bc0-143">此配置可以包括特定值，如基本服务器、HTTP 标头或超时。</span><span class="sxs-lookup"><span data-stu-id="71bc0-143">This configuration can include specific values such as the base server, HTTP headers or time outs.</span></span>

<span data-ttu-id="71bc0-144">下图显示了如何将类型化客户端与 `IHttpClientFactory` 结合使用：</span><span class="sxs-lookup"><span data-stu-id="71bc0-144">The following diagram shows how Typed Clients are used with `IHttpClientFactory`:</span></span>

![展示如何将类型化客户端与 IHttpClientFactory 结合使用的图表。](./media/use-httpclientfactory-to-implement-resilient-http-requests/client-application-code.png)

<span data-ttu-id="71bc0-146">**图 8-4**。</span><span class="sxs-lookup"><span data-stu-id="71bc0-146">**Figure 8-4**.</span></span> <span data-ttu-id="71bc0-147">结合使用 `IHttpClientFactory` 和类型化客户端类。</span><span class="sxs-lookup"><span data-stu-id="71bc0-147">Using `IHttpClientFactory` with Typed Client classes.</span></span>

<span data-ttu-id="71bc0-148">在上图中，`ClientService`（由控制器或客户端代码使用）使用由注册的 `IHttpClientFactory` 创建的 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="71bc0-148">In the above image, a `ClientService` (used by a controller or client code) uses an `HttpClient` created by the registered `IHttpClientFactory`.</span></span> <span data-ttu-id="71bc0-149">此工厂将池的 `HttpMessageHandler` 分配给 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="71bc0-149">This factory assigns an `HttpMessageHandler` from a pool to the `HttpClient`.</span></span> <span data-ttu-id="71bc0-150">当使用扩展方法 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> 在 DI 容器中注册 `IHttpClientFactory` 时，可以使用 Polly 策略配置 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="71bc0-150">The `HttpClient` can be configured with Polly's policies when registering the `IHttpClientFactory` in the DI container with the extension method <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A>.</span></span>

<span data-ttu-id="71bc0-151">要配置上述结构，请通过安装包含 <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> 的 <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> 扩展方法的 `Microsoft.Extensions.Http` NuGet 包，在应用程序中添加 <xref:System.Net.Http.IHttpClientFactory>。</span><span class="sxs-lookup"><span data-stu-id="71bc0-151">To configure the above structure, add <xref:System.Net.Http.IHttpClientFactory> in your application by installing the `Microsoft.Extensions.Http` NuGet package that includes the <xref:Microsoft.Extensions.DependencyInjection.HttpClientFactoryServiceCollectionExtensions.AddHttpClient%2A> extension method for <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="71bc0-152">此扩展方法用于注册内部 `DefaultHttpClientFactory` 类，后者用作接口 `IHttpClientFactory` 的单一实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-152">This extension method registers the internal `DefaultHttpClientFactory` class to be used as a singleton for the interface `IHttpClientFactory`.</span></span> <span data-ttu-id="71bc0-153">它定义 <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder> 的临时配置。</span><span class="sxs-lookup"><span data-stu-id="71bc0-153">It defines a transient configuration for the <xref:Microsoft.Extensions.Http.HttpMessageHandlerBuilder>.</span></span> <span data-ttu-id="71bc0-154">此消息处理程序（<xref:System.Net.Http.HttpMessageHandler> 对象）获取自池，可供从工厂返回的 `HttpClient` 使用。</span><span class="sxs-lookup"><span data-stu-id="71bc0-154">This message handler (<xref:System.Net.Http.HttpMessageHandler> object), taken from a pool, is used by the `HttpClient` returned from the factory.</span></span>

<span data-ttu-id="71bc0-155">在下一个代码中，可以看到如何使用 `AddHttpClient()` 注册需要使用 `HttpClient` 的类型化客户端（服务代理）。</span><span class="sxs-lookup"><span data-stu-id="71bc0-155">In the next code, you can see how `AddHttpClient()` can be used to register Typed Clients (Service Agents) that need to use `HttpClient`.</span></span>

```csharp
// Startup.cs
//Add http client services at ConfigureServices(IServiceCollection services)
services.AddHttpClient<ICatalogService, CatalogService>();
services.AddHttpClient<IBasketService, BasketService>();
services.AddHttpClient<IOrderingService, OrderingService>();
```

<span data-ttu-id="71bc0-156">按先前代码中所示注册客户端服务，使 `DefaultClientFactory` 为每个服务创建一个标准 `HttpClient`。</span><span class="sxs-lookup"><span data-stu-id="71bc0-156">Registering the client services as shown in the previous code, makes the `DefaultClientFactory` create a standard `HttpClient` for each service.</span></span>

<span data-ttu-id="71bc0-157">还可以在注册中添加特定于实例的配置（例如，配置基址），并添加一些弹性策略，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="71bc0-157">You could also add instance-specific configuration in the registration to, for example, configure the base address, and add some resiliency policies, as shown in the following code:</span></span>

```csharp
services.AddHttpClient<ICatalogService, CatalogService>(client =>
{
    client.BaseAddress = new Uri(Configuration["BaseUrl"]);
})
    .AddPolicyHandler(GetRetryPolicy())
    .AddPolicyHandler(GetCircuitBreakerPolicy());
```

<span data-ttu-id="71bc0-158">就本示例而言，可以在下一个代码中看到以上策略之一：</span><span class="sxs-lookup"><span data-stu-id="71bc0-158">Just for the example sake, you can see one of the above policies in the next code:</span></span>

```csharp
static IAsyncPolicy<HttpResponseMessage> GetRetryPolicy()
{
    return HttpPolicyExtensions
        .HandleTransientHttpError()
        .OrResult(msg => msg.StatusCode == System.Net.HttpStatusCode.NotFound)
        .WaitAndRetryAsync(6, retryAttempt => TimeSpan.FromSeconds(Math.Pow(2, retryAttempt)));
}
```

<span data-ttu-id="71bc0-159">可以在[下一篇文章](implement-http-call-retries-exponential-backoff-polly.md)中找到有关使用 Polly 的更多详细信息。</span><span class="sxs-lookup"><span data-stu-id="71bc0-159">You can find more details about using Polly in the [Next article](implement-http-call-retries-exponential-backoff-polly.md).</span></span>

### <a name="httpclient-lifetimes"></a><span data-ttu-id="71bc0-160">HttpClient 生存期</span><span class="sxs-lookup"><span data-stu-id="71bc0-160">HttpClient lifetimes</span></span>

<span data-ttu-id="71bc0-161">每次从 `IHttpClientFactory` 获取 `HttpClient` 对象时，都会返回一个新实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-161">Each time you get an `HttpClient` object from the `IHttpClientFactory`, a new instance is returned.</span></span> <span data-ttu-id="71bc0-162">但每个 `HttpClient` 使用 `IHttpClientFactory` 汇集和重用的 `HttpMessageHandler`，以减少资源消耗，只要 `HttpMessageHandler` 的生存期尚未过期。</span><span class="sxs-lookup"><span data-stu-id="71bc0-162">But each `HttpClient` uses an `HttpMessageHandler` that's pooled and reused by the `IHttpClientFactory` to reduce resource consumption, as long as the `HttpMessageHandler`'s lifetime hasn't expired.</span></span>

<span data-ttu-id="71bc0-163">由于每个处理程序通常都管理自己的基础 HTTP 连接，所以有必要汇集处理程序；创建的处理程序数量如果多于必需的数量，则可能导致连接延迟。</span><span class="sxs-lookup"><span data-stu-id="71bc0-163">Pooling of handlers is desirable as each handler typically manages its own underlying HTTP connections; creating more handlers than necessary can result in connection delays.</span></span> <span data-ttu-id="71bc0-164">部分处理程序还保持连接无期限地打开，这样可以防止处理程序对 DNS 更改作出反应。</span><span class="sxs-lookup"><span data-stu-id="71bc0-164">Some handlers also keep connections open indefinitely, which can prevent the handler from reacting to DNS changes.</span></span>

<span data-ttu-id="71bc0-165">池中的 `HttpMessageHandler` 对象的生存期就是池中的 `HttpMessageHandler` 实例可重用的时间长度。</span><span class="sxs-lookup"><span data-stu-id="71bc0-165">The `HttpMessageHandler` objects in the pool have a lifetime that's the length of time that an `HttpMessageHandler` instance in the pool can be reused.</span></span> <span data-ttu-id="71bc0-166">默认值为两分钟，但可基于每个类型化客户端重写此值。</span><span class="sxs-lookup"><span data-stu-id="71bc0-166">The default value is two minutes, but it can be overridden per Typed Client.</span></span> <span data-ttu-id="71bc0-167">要重写该值，请在创建客户端时在返回的 <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> 上调用 `SetHandlerLifetime()`，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="71bc0-167">To override it, call `SetHandlerLifetime()` on the <xref:Microsoft.Extensions.DependencyInjection.IHttpClientBuilder> that's returned when creating the client, as shown in the following code:</span></span>

```csharp
//Set 5 min as the lifetime for the HttpMessageHandler objects in the pool used for the Catalog Typed Client
services.AddHttpClient<ICatalogService, CatalogService>()
    .SetHandlerLifetime(TimeSpan.FromMinutes(5));
```

<span data-ttu-id="71bc0-168">每个类型化客户端都可自行配置处理程序生存期值。</span><span class="sxs-lookup"><span data-stu-id="71bc0-168">Each Typed Client can have its own configured handler lifetime value.</span></span> <span data-ttu-id="71bc0-169">将生存期设置为 `InfiniteTimeSpan` 可禁用处理程序到期。</span><span class="sxs-lookup"><span data-stu-id="71bc0-169">Set the lifetime to `InfiniteTimeSpan` to disable handler expiry.</span></span>

### <a name="implement-your-typed-client-classes-that-use-the-injected-and-configured-httpclient"></a><span data-ttu-id="71bc0-170">实现使用注入的和配置的 HttpClient 的类型化客户端类</span><span class="sxs-lookup"><span data-stu-id="71bc0-170">Implement your Typed Client classes that use the injected and configured HttpClient</span></span>

<span data-ttu-id="71bc0-171">在上一步中，需要定义类型化客户端类，如示例代码中的类，“BasketService”、“CatalogService”、“OrderingService”等。类型化客户端是一个类，它接受 `HttpClient` 对象（通过其构造函数注入），并用它来调用某些远程 HTTP 服务。</span><span class="sxs-lookup"><span data-stu-id="71bc0-171">As a previous step, you need to have your Typed Client classes defined, such as the classes in the sample code, like 'BasketService', 'CatalogService', 'OrderingService', etc. – A Typed Client is a class that accepts an `HttpClient` object (injected through its constructor) and uses it to call some remote HTTP service.</span></span> <span data-ttu-id="71bc0-172">例如：</span><span class="sxs-lookup"><span data-stu-id="71bc0-172">For example:</span></span>

```csharp
public class CatalogService : ICatalogService
{
    private readonly HttpClient _httpClient;
    private readonly string _remoteServiceBaseUrl;

    public CatalogService(HttpClient httpClient)
    {
        _httpClient = httpClient;
    }

    public async Task<Catalog> GetCatalogItems(int page, int take,
                                               int? brand, int? type)
    {
        var uri = API.Catalog.GetAllCatalogItems(_remoteServiceBaseUrl,
                                                 page, take, brand, type);

        var responseString = await _httpClient.GetStringAsync(uri);

        var catalog = JsonConvert.DeserializeObject<Catalog>(responseString);
        return catalog;
    }
}
```

<span data-ttu-id="71bc0-173">Typed Client（在本例中为 `CatalogService`）由 DI（依赖项注入）激活，这意味着除 `HttpClient` 外，它还可接受其构造函数中的任何注册服务。</span><span class="sxs-lookup"><span data-stu-id="71bc0-173">The Typed Client (`CatalogService` in the example) is activated by DI (Dependency Injection), that means it can accept any registered service in its constructor, in addition to `HttpClient`.</span></span>

<span data-ttu-id="71bc0-174">Typed Client 实际上是一个临时对象，这意味着每当需要实例时，就会创建一个新的实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-174">A Typed Client is effectively a transient object, that means a new instance is created each time one is needed.</span></span> <span data-ttu-id="71bc0-175">它会在每次构造时接收一个新的 `HttpClient` 实例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-175">It receives a new `HttpClient` instance each time it's constructed.</span></span> <span data-ttu-id="71bc0-176">但是，池中的 `HttpMessageHandler` 对象是由多个 `HttpClient` 实例重复使用的对象。</span><span class="sxs-lookup"><span data-stu-id="71bc0-176">However, the `HttpMessageHandler` objects in the pool are the objects that are reused by multiple `HttpClient` instances.</span></span>

### <a name="use-your-typed-client-classes"></a><span data-ttu-id="71bc0-177">使用类型化客户端类</span><span class="sxs-lookup"><span data-stu-id="71bc0-177">Use your Typed Client classes</span></span>

<span data-ttu-id="71bc0-178">最后，在实现了类型化类后，可使用 `AddHttpClient()` 来注册和配置它们。</span><span class="sxs-lookup"><span data-stu-id="71bc0-178">Finally, once you have your typed classes implemented, you can have them registered and configured with `AddHttpClient()`.</span></span> <span data-ttu-id="71bc0-179">之后，可在 DI 注入服务的任何位置使用它们。</span><span class="sxs-lookup"><span data-stu-id="71bc0-179">After that you can use them wherever have services injected by DI.</span></span> <span data-ttu-id="71bc0-180">例如，在 Razor 页面代码或 MVC Web 应用的控制器中，如 eShopOnContainers 的以下代码中：</span><span class="sxs-lookup"><span data-stu-id="71bc0-180">For example, in a Razor page code or controller of an MVC web app, like in the following code from eShopOnContainers:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC.Controllers
{
    public class CatalogController : Controller
    {
        private ICatalogService _catalogSvc;

        public CatalogController(ICatalogService catalogSvc) =>
                                                           _catalogSvc = catalogSvc;

        public async Task<IActionResult> Index(int? BrandFilterApplied,
                                               int? TypesFilterApplied,
                                               int? page,
                                               [FromQuery]string errorMsg)
        {
            var itemsPage = 10;
            var catalog = await _catalogSvc.GetCatalogItems(page ?? 0,
                                                            itemsPage,
                                                            BrandFilterApplied,
                                                            TypesFilterApplied);
            //… Additional code
        }

        }
}
```

<span data-ttu-id="71bc0-181">到目前为止，以上代码段只显示了执行常规 HTTP 请求的示例。</span><span class="sxs-lookup"><span data-stu-id="71bc0-181">Up to this point, the above code snippet has only shown the example of performing regular HTTP requests.</span></span> <span data-ttu-id="71bc0-182">但以下部分会展示“神奇之处”，它将介绍由 `HttpClient` 发出的所有 HTTP 请求如何具有可复原策略，例如带指数退避的重试、断路器、使用身份验证令牌的安全功能，甚至其他任何自定义功能。</span><span class="sxs-lookup"><span data-stu-id="71bc0-182">But the 'magic' comes in the following sections where it shows how all the HTTP requests made by `HttpClient`, can have resilient policies such as retries with exponential backoff, circuit breakers, security features using auth tokens, or even any other custom feature.</span></span> <span data-ttu-id="71bc0-183">所有这些都可通过向已注册的 Typed Client 添加策略和委派处理程序来完成。</span><span class="sxs-lookup"><span data-stu-id="71bc0-183">And all of these can be done just by adding policies and delegating handlers to your registered Typed Clients.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="71bc0-184">其他资源</span><span class="sxs-lookup"><span data-stu-id="71bc0-184">Additional resources</span></span>

- <span data-ttu-id="71bc0-185">在 .NET Core 中使用 HttpClientFactory </span><span class="sxs-lookup"><span data-stu-id="71bc0-185">**Using HttpClientFactory in .NET Core**</span></span>  
  [https://docs.microsoft.com/aspnet/core/fundamentals/http-requests](/aspnet/core/fundamentals/http-requests)

- <span data-ttu-id="71bc0-186">`dotnet/extensions` GitHub 存储库中的 HttpClientFactory 源代码 </span><span class="sxs-lookup"><span data-stu-id="71bc0-186">**HttpClientFactory source code in the `dotnet/extensions` GitHub repository**</span></span>  
  <https://github.com/dotnet/extensions/tree/master/src/HttpClientFactory>

- <span data-ttu-id="71bc0-187">**Polly（.NET 的恢复和暂时性故障处理库）**</span><span class="sxs-lookup"><span data-stu-id="71bc0-187">**Polly (.NET resilience and transient-fault-handling library)**</span></span>  
  <http://www.thepollyproject.org/>
  
- <span data-ttu-id="71bc0-188">使用无依赖项注入的 IHttpClientFactory（GitHub 问题） </span><span class="sxs-lookup"><span data-stu-id="71bc0-188">**Using IHttpClientFactory without dependency injection (GitHub issue)**</span></span>  
  <https://github.com/dotnet/extensions/issues/1345>

>[!div class="step-by-step"]
><span data-ttu-id="71bc0-189">[上一页](implement-resilient-entity-framework-core-sql-connections.md)
>[下一页](implement-http-call-retries-exponential-backoff-polly.md)</span><span class="sxs-lookup"><span data-stu-id="71bc0-189">[Previous](implement-resilient-entity-framework-core-sql-connections.md)
[Next](implement-http-call-retries-exponential-backoff-polly.md)</span></span>
