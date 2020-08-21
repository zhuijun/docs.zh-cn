---
title: 使用 IHostedService 和 BackgroundService 类在微服务中实现后台任务
description: 用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 了解使用 IHostedService 和 BackgroundService 在微服务 .NET Core 中实现后台任务的新选项。
ms.date: 08/14/2020
ms.openlocfilehash: 4ab215f2196cd2e66b116465c3a582a9846c8066
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267992"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="f62f1-103">使用 IHostedService 和 BackgroundService 类在微服务中实现后台任务</span><span class="sxs-lookup"><span data-stu-id="f62f1-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="f62f1-104">任何应用程序中都可能需要使用后台任务和计划作业，无论应用程序是否遵循微服务体系结构模式均是如此。</span><span class="sxs-lookup"><span data-stu-id="f62f1-104">Background tasks and scheduled jobs are something you might need to use in any application, whether or not it follows the microservices architecture pattern.</span></span> <span data-ttu-id="f62f1-105">使用微服务体系结构的区别在于，你可以在一个单独的用于托管的进程/容器中实现后台任务，以便根据需要对其纵向缩减/扩展。</span><span class="sxs-lookup"><span data-stu-id="f62f1-105">The difference when using a microservices architecture is that you can implement the background task in a separate process/container for hosting so you can scale it down/up based on your need.</span></span>

<span data-ttu-id="f62f1-106">一般在 .NET Core 中，我们将这些类型的任务称为托管服务  ，因为它们是托管在主机/应用程序/微服务中的服务/逻辑。</span><span class="sxs-lookup"><span data-stu-id="f62f1-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="f62f1-107">请注意，在这种情况下，托管服务仅表示具有后台任务逻辑的类。</span><span class="sxs-lookup"><span data-stu-id="f62f1-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="f62f1-108">自 .NET Core 2.0 开始，该框架提供名为 <xref:Microsoft.Extensions.Hosting.IHostedService> 的新接口，有助于轻松实现托管服务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="f62f1-109">基本理念是，可以注册多个后台任务（托管服务），在 Web 主机或主机运行时在后台运行，如图 6-26 所示。</span><span class="sxs-lookup"><span data-stu-id="f62f1-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![比较 ASP.NET Core IWebHost 和 .NET Core IHost 的关系图。](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="f62f1-111">**图 6-26**.</span><span class="sxs-lookup"><span data-stu-id="f62f1-111">**Figure 6-26**.</span></span> <span data-ttu-id="f62f1-112">在 WebHost 与主机中使用 IHostedService</span><span class="sxs-lookup"><span data-stu-id="f62f1-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="f62f1-113">ASP.NET Core 1.x 和 2.x 支持 `IWebHost`，适用于 Web 应用中的后台进程。</span><span class="sxs-lookup"><span data-stu-id="f62f1-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="f62f1-114">.NET Core 2.1 及更高版本支持 `IHost`，适用于带有纯控制台应用的后台进程。</span><span class="sxs-lookup"><span data-stu-id="f62f1-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="f62f1-115">请注意 `WebHost` 和 `Host` 之间产生的差异。</span><span class="sxs-lookup"><span data-stu-id="f62f1-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="f62f1-116">ASP.NET Core 2.0 中的 `WebHost`（实现 `IWebHost` 的基类）是用于为进程提供 HTTP 服务器功能的基础结构项目，例如，在实现 MVC Web 应用或 Web API 服务时。</span><span class="sxs-lookup"><span data-stu-id="f62f1-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="f62f1-117">它提供 ASP.NET Core 中所有新的基础结构优点，使用户能够使用依赖关系注入，在请求管道中插入中间件等。</span><span class="sxs-lookup"><span data-stu-id="f62f1-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="f62f1-118">`WebHost` 将这些相同的 `IHostedServices` 用于后台任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="f62f1-119">.NET Core 2.1 中引入了 `Host`（实现 `IHost` 的基类）。</span><span class="sxs-lookup"><span data-stu-id="f62f1-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="f62f1-120">基本上，`Host` 能让用户拥有与 `WebHost`（依赖项注入、托管服务等）相似的基础结构，但在这种情况下，只需拥有一个简单轻便的进程作为主机，与 MVC、Web API 或 HTTP 服务器功能无关。</span><span class="sxs-lookup"><span data-stu-id="f62f1-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="f62f1-121">因此，可以选择一个专用主机进程或使用 `IHost` 创建一个来专门处理托管服务，例如仅用于托管 `IHostedServices` 的微服务，或者也可以选择性地扩展现有的 ASP.NET Core `WebHost`，例如现有的 ASP.NET Core Web API 或 MVC 应用。</span><span class="sxs-lookup"><span data-stu-id="f62f1-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="f62f1-122">每种方法都有优缺点，具体取决于业务和可伸缩性需求。</span><span class="sxs-lookup"><span data-stu-id="f62f1-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="f62f1-123">重要的是，如果后台任务与 HTTP (`IWebHost`) 无关，则应使用 `IHost`。</span><span class="sxs-lookup"><span data-stu-id="f62f1-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="f62f1-124">在 WebHost 或主机中注册托管服务</span><span class="sxs-lookup"><span data-stu-id="f62f1-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="f62f1-125">让我们进一步深化对 `IHostedService` 接口的了解，因为它在 `WebHost` 或 `Host` 中的使用非常相似。</span><span class="sxs-lookup"><span data-stu-id="f62f1-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="f62f1-126">SignalR 是使用托管服务的项目的一个示例，但也可以将其用于更简单的操作，如：</span><span class="sxs-lookup"><span data-stu-id="f62f1-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="f62f1-127">轮询数据库以查找更改的后台任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="f62f1-128">定期更新某些缓存的计划任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="f62f1-129">允许任务在后台线程上执行的 QueueBackgroundWorkItem 实现。</span><span class="sxs-lookup"><span data-stu-id="f62f1-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="f62f1-130">在 Web 应用后台处理消息队列中的消息，同时共享 `ILogger` 等公共服务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="f62f1-131">从 `Task.Run()` 开始的后台任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="f62f1-132">基本上，可以将所有这些操作卸载至实现 `IHostedService` 的后台任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="f62f1-133">向 `WebHost` 或 `Host` 添加一个或多个 `IHostedServices` 的方式是，通过 ASP.NET Core `WebHost`（或 .NET Core 2.1 及更高版本中的 `Host`）中的 <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  扩展方法对它们进行注册。</span><span class="sxs-lookup"><span data-stu-id="f62f1-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="f62f1-134">基本上，必须在常见的 `Startup` 类的 `ConfigureServices()` 方法中注册托管服务，如以下典型的 ASP.NET WebHost 中的代码所示。</span><span class="sxs-lookup"><span data-stu-id="f62f1-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="f62f1-135">在该代码中，`GracePeriodManagerService` 托管服务是来自 eShopOnContainers 中的订购业务微服务的真实代码，而另外两个只是两个额外示例。</span><span class="sxs-lookup"><span data-stu-id="f62f1-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="f62f1-136">`IHostedService` 后台任务的执行与应用程序（就此而言，为主机或微服务）的生存期相协调。</span><span class="sxs-lookup"><span data-stu-id="f62f1-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="f62f1-137">当应用程序启动时注册任务，当应用程序关闭时，有机会执行某些正常操作或清理。</span><span class="sxs-lookup"><span data-stu-id="f62f1-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="f62f1-138">始终可以启动后台线程来运行任何任务，而无需使用 `IHostedService`。</span><span class="sxs-lookup"><span data-stu-id="f62f1-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="f62f1-139">不同之处就在于应用的关闭时间，此时会直接终止线程，而没有机会执行正常的清理操作。</span><span class="sxs-lookup"><span data-stu-id="f62f1-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="f62f1-140">IHostedService 接口</span><span class="sxs-lookup"><span data-stu-id="f62f1-140">The IHostedService interface</span></span>

<span data-ttu-id="f62f1-141">当注册 `IHostedService` 时，.NET Core 会在应用程序启动和停止期间分别调用 `IHostedService` 类型的 `StartAsync()` 和 `StopAsync()` 方法。</span><span class="sxs-lookup"><span data-stu-id="f62f1-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="f62f1-142">有关详细信息，请参阅 [IHostedService 接口](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span><span class="sxs-lookup"><span data-stu-id="f62f1-142">For more details, refer [IHostedService interface](https://docs.microsoft.com/aspnet/core/fundamentals/host/hosted-services?view=aspnetcore-3.1&tabs=visual-studio#ihostedservice-interface)</span></span>

<span data-ttu-id="f62f1-143">如你所想，可以创建 IHostedService 的多个实现，并在 `ConfigureService()` 方法中将它们注册到 DI 容器中，如前所示。</span><span class="sxs-lookup"><span data-stu-id="f62f1-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="f62f1-144">所有这些托管服务将随应用程序/微服务一起启动和停止。</span><span class="sxs-lookup"><span data-stu-id="f62f1-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="f62f1-145">作为开发人员，当主机触发 `StopAsync()` 方法时，需负责处理服务的停止操作。</span><span class="sxs-lookup"><span data-stu-id="f62f1-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="f62f1-146">使用从 BackgroundService 基类派生的自定义托管服务类来实现 IHostedService</span><span class="sxs-lookup"><span data-stu-id="f62f1-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="f62f1-147">可以从头开始创建自定义托管服务类并实现 `IHostedService`，因为在使用 .NET Core 2.0 时需执行这些操作。</span><span class="sxs-lookup"><span data-stu-id="f62f1-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="f62f1-148">但是，由于大多数后台任务在取消令牌管理和其他典型操作方面都有类似的需求，因此有一个非常方便且可以从中进行派生的抽象基类，名为 `BackgroundService`（自 .NET Core 2.1 起提供）。</span><span class="sxs-lookup"><span data-stu-id="f62f1-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="f62f1-149">该类提供设置后台任务所需的主要工作。</span><span class="sxs-lookup"><span data-stu-id="f62f1-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="f62f1-150">下一个代码是在 .NET Core 中实现的抽象 BackgroundService 基类。</span><span class="sxs-lookup"><span data-stu-id="f62f1-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="f62f1-151">从上一抽象基类派生时，得益于该继承的实现，用户只需在自定义的托管服务类中实现 `ExecuteAsync()` 方法，如以下来自 eShopOnContainers 的简化代码所示，该代码轮询数据库并在需要时将集成事件发布到事件总线中。</span><span class="sxs-lookup"><span data-stu-id="f62f1-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        // Constructor's parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="f62f1-152">在 eShopOnContainers 的此特定情况下，它正在执行一个应用程序方法，该方法查询数据库表以查找具有特定状态的订单，并且在应用更改时，它会通过事件总线（其下可以使用 RabbitMQ 或 Azure 服务总线）发布集成事件。</span><span class="sxs-lookup"><span data-stu-id="f62f1-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="f62f1-153">当然，也可以改为运行任何其他业务的后台任务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="f62f1-154">默认情况下，取消令牌会设置为 5 秒超时，但可以在使用 `IWebHostBuilder` 的 `UseShutdownTimeout` 扩展构建 `WebHost` 时更改该值。</span><span class="sxs-lookup"><span data-stu-id="f62f1-154">By default, the cancellation token is set with a 5 seconds timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="f62f1-155">这意味着我们的服务预计将在 5 秒内取消，否则会更突然地终止。</span><span class="sxs-lookup"><span data-stu-id="f62f1-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="f62f1-156">以下代码会将该时间更改为 10 秒。</span><span class="sxs-lookup"><span data-stu-id="f62f1-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="f62f1-157">摘要类图</span><span class="sxs-lookup"><span data-stu-id="f62f1-157">Summary class diagram</span></span>

<span data-ttu-id="f62f1-158">下图显示了实现 IHostedServices 时涉及的类和接口的直观摘要。</span><span class="sxs-lookup"><span data-stu-id="f62f1-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![显示 IWebHost 和 IHost 可以托管多个服务的关系图。](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="f62f1-160">**图 6-27**。</span><span class="sxs-lookup"><span data-stu-id="f62f1-160">**Figure 6-27**.</span></span> <span data-ttu-id="f62f1-161">显示多个与 IHostedService 相关的类和接口的类图</span><span class="sxs-lookup"><span data-stu-id="f62f1-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="f62f1-162">类图：IWebHost 和 IHost 可以托管许多服务，这些服务从实现 IHostedService 的 BackgroundService 继承。</span><span class="sxs-lookup"><span data-stu-id="f62f1-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="f62f1-163">部署注意事项和要点</span><span class="sxs-lookup"><span data-stu-id="f62f1-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="f62f1-164">请务必注意，部署 ASP.NET Core `WebHost` 或 .NET Core `Host` 的方式可能会影响最终解决方案。</span><span class="sxs-lookup"><span data-stu-id="f62f1-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="f62f1-165">例如，如果在 IIS 或常规 Azure 应用服务上部署 `WebHost`，由于应用池回收，主机可能会被关闭。</span><span class="sxs-lookup"><span data-stu-id="f62f1-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="f62f1-166">但是，如果将主机作为容器部署到 Kubernetes 等业务流程协调程序中，则可以控制主机的实时实例数量。</span><span class="sxs-lookup"><span data-stu-id="f62f1-166">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="f62f1-167">此外，还可以考虑云中专门针对这些方案的其他方法，例如 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="f62f1-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="f62f1-168">最后，如果需要服务一直处于运行状态并在 Windows Server 上部署，可以使用 Windows 服务。</span><span class="sxs-lookup"><span data-stu-id="f62f1-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="f62f1-169">但即使对于部署到应用池中的 `WebHost`，也存在如重新填充或刷新应用程序的内存中缓存这样的情况，这仍然适用。</span><span class="sxs-lookup"><span data-stu-id="f62f1-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="f62f1-170">`IHostedService` 接口为在 ASP.NET Core Web 应用程序（在 .NET Core 2.0 及更高版本中）或任何进程/主机（从使用 `IHost` 的 .NET Core 2.1 开始）中启动后台任务提供了一种便捷方式。</span><span class="sxs-lookup"><span data-stu-id="f62f1-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="f62f1-171">其主要优势在于，当主机本身将要关闭时，可以有机会进行正常取消以清理后台任务的代码。</span><span class="sxs-lookup"><span data-stu-id="f62f1-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up the code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f62f1-172">其他资源</span><span class="sxs-lookup"><span data-stu-id="f62f1-172">Additional resources</span></span>

- <span data-ttu-id="f62f1-173">**在 ASP.NET Core/Standard 2.0 中生成计划任务** </span><span class="sxs-lookup"><span data-stu-id="f62f1-173">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="f62f1-174">**在 ASP.NET Core 2.0 中实现 IHostedService** </span><span class="sxs-lookup"><span data-stu-id="f62f1-174">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="f62f1-175">**使用 ASP.NET Core 2.1 的 GenericHost 示例** </span><span class="sxs-lookup"><span data-stu-id="f62f1-175">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="f62f1-176">[上一页](test-aspnet-core-services-web-apps.md)
> [下一页](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="f62f1-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
