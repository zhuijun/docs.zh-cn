---
title: 运行状况监视
description: 了解实现运行状况监视的一种方法。
ms.date: 03/02/2020
ms.openlocfilehash: 3e3e8ec41de1469f0c397d8d80d224dd2f7a2bd2
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267888"
---
# <a name="health-monitoring"></a><span data-ttu-id="49994-103">运行状况监视</span><span class="sxs-lookup"><span data-stu-id="49994-103">Health monitoring</span></span>

<span data-ttu-id="49994-104">运行状况监视可以获取有关容器和微服务状态的近实时信息。</span><span class="sxs-lookup"><span data-stu-id="49994-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="49994-105">运行状况对于微服务操作的多个方面至关重要，并且在业务流程协调程序分阶段执行部分应用程序升级时尤为重要，稍后将对此进行说明。</span><span class="sxs-lookup"><span data-stu-id="49994-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="49994-106">通常，基于微服务的应用程序借助检测信号或运行状况检查，使性能监视器、日程安排和业务流程协调程序得以对大量服务进行跟踪监测。</span><span class="sxs-lookup"><span data-stu-id="49994-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="49994-107">如果服务无法按需或按计划发送某种表示“我处于活动状态”的信号，那么部署更新时，应用程序可能面临风险，或者它可能太晚才发现故障，并且无法阻止可能会导致重大故障的级联故障。</span><span class="sxs-lookup"><span data-stu-id="49994-107">If services cannot send some sort of "I'm alive" signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="49994-108">在典型模型中，服务发送有关其状态的报告，聚合这些信息便能整体了解应用程序运行状况。</span><span class="sxs-lookup"><span data-stu-id="49994-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="49994-109">如果使用的是业务流程协调程序，则可以向业务流程协调程序的群集提供运行状况信息，以便群集可以执行相应操作。</span><span class="sxs-lookup"><span data-stu-id="49994-109">If you're using an orchestrator, you can provide health information to your orchestrator's cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="49994-110">如果使用为应用程序定制的高质量运行状况报告，则可以更轻松地检测到正在运行的应用程序存在的问题并进行修复。</span><span class="sxs-lookup"><span data-stu-id="49994-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="49994-111">在 ASP.NET Core 服务中实现运行状况检查</span><span class="sxs-lookup"><span data-stu-id="49994-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="49994-112">开发 ASP.NET Core 微服务或 Web 应用程序时，可以使用 ASP .NET Core 2.2 中发布的内置运行状况检查功能 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks))。</span><span class="sxs-lookup"><span data-stu-id="49994-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="49994-113">与许多 ASP.NET 核心功能一样，运行状况检查附带一组服务和中间件。</span><span class="sxs-lookup"><span data-stu-id="49994-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="49994-114">运行状况检查服务和中间件使用方便，并提供了一些功能，可以用于验证应用程序（如 SQL Server 数据库或远程 API）所需的任何外部资源是否正常工作。</span><span class="sxs-lookup"><span data-stu-id="49994-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="49994-115">使用该功能时，还可以确定资源正常运行的定义，稍后将会介绍。</span><span class="sxs-lookup"><span data-stu-id="49994-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="49994-116">若要有效使用此功能，需要先在微服务中配置服务。</span><span class="sxs-lookup"><span data-stu-id="49994-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="49994-117">其次，需要查询运行状况报告的前端应用程序。</span><span class="sxs-lookup"><span data-stu-id="49994-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="49994-118">该前端应用程序可能是自定义报告应用程序，也可能是可以根据运行状况状态做出相应反应的业务流程协调程序。</span><span class="sxs-lookup"><span data-stu-id="49994-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="49994-119">在后端 ASP.NET 微服务中使用 HealthChecks 功能</span><span class="sxs-lookup"><span data-stu-id="49994-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="49994-120">本节介绍在使用 [Microsoft.Extensions.Diagnostics.HealthChecks ](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)包时，如何在示例 ASP.NET Core 3.1 Web API 应用程序中实现 HealthChecks 功能。</span><span class="sxs-lookup"><span data-stu-id="49994-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="49994-121">下一节介绍如何在大规模微服务（例如 eShopOnContainers）中实现此功能。</span><span class="sxs-lookup"><span data-stu-id="49994-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="49994-122">首先，需要定义每个微服务的正常运行状况的必备条件。</span><span class="sxs-lookup"><span data-stu-id="49994-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="49994-123">在该示例应用程序中，如果可通过 HTTP 访问微服务 API 并且可以使用与其相关的 SQL Server 数据库，可定义该微服务处于正常运行状态。</span><span class="sxs-lookup"><span data-stu-id="49994-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="49994-124">在 .NET Core 3.1 中，使用内置 API，可以通过以下方式配置服务、为微服务及其依赖的 SQL Server 数据库添加运行状况检查：</span><span class="sxs-lookup"><span data-stu-id="49994-124">In .NET Core 3.1, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check",
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]),
            HealthStatus.Unhealthy,
            new string[] { "orderingdb" });
}
```

<span data-ttu-id="49994-125">在上面的代码中，`services.AddHealthChecks()` 方法配置一个基本 HTTP 检查，会返回状态代码 200 以及“正常”  。</span><span class="sxs-lookup"><span data-stu-id="49994-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with "Healthy".</span></span>  <span data-ttu-id="49994-126">此外，`AddCheck()` 扩展方法可配置自定义 `SqlConnectionHealthCheck`，用于检查相关 SQL 数据库的运行状况。</span><span class="sxs-lookup"><span data-stu-id="49994-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database's health.</span></span>

<span data-ttu-id="49994-127">`AddCheck()` 方法添加具有指定名称的新运行状况检查和类型 `IHealthCheck` 的实现。</span><span class="sxs-lookup"><span data-stu-id="49994-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="49994-128">可以使用 AddCheck 方法添加多个运行状况检查，使微服务在其所有检查均获得“正常”结果后才会提供“正常”状态。</span><span class="sxs-lookup"><span data-stu-id="49994-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a "healthy" status until all its checks are healthy.</span></span>

<span data-ttu-id="49994-129">`SqlConnectionHealthCheck` 是自定义类，可实现 `IHealthCheck`，它使用连接字符串作为构造函数参数，并执行简单查询，检查与 SQL 数据库的连接是否成功。</span><span class="sxs-lookup"><span data-stu-id="49994-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="49994-130">如果查询执行成功，将返回 `HealthCheckResult.Healthy()`，如果失败，将返回包含实际异常的 `FailureStatus`。</span><span class="sxs-lookup"><span data-stu-id="49994-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

<span data-ttu-id="49994-131">请注意，在上面的代码中，`Select 1` 是用于检查数据库运行状况的查询。</span><span class="sxs-lookup"><span data-stu-id="49994-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="49994-132">若要监视微服务的可用性，Kubernetes 等业务流程协调程序可通过发送微服务测试请求来定期执行运行状况检查。</span><span class="sxs-lookup"><span data-stu-id="49994-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="49994-133">请务必让数据库查询保持高效，以便快速执行这些操作而不会导致更高的资源使用率。</span><span class="sxs-lookup"><span data-stu-id="49994-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="49994-134">最后，添加对 URL 路径 `/hc` 进行响应的中间件：</span><span class="sxs-lookup"><span data-stu-id="49994-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

<span data-ttu-id="49994-135">调用 `<yourmicroservice>/hc` 终结点时，它将运行 Startup 类的 `AddHealthChecks()` 方法中配置的所有运行状况检查，并显示结果。</span><span class="sxs-lookup"><span data-stu-id="49994-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="49994-136">eShopOnContainers 中的 HealthChecks 实现</span><span class="sxs-lookup"><span data-stu-id="49994-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="49994-137">eShopOnContainers 中的微服务依赖多个服务来执行其任务。</span><span class="sxs-lookup"><span data-stu-id="49994-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="49994-138">例如，eShopOnContainers 中的 `Catalog.API` 微服务依赖许多服务，例如，Azure Blob 存储、SQL Server 和 RabbitMQ。</span><span class="sxs-lookup"><span data-stu-id="49994-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="49994-139">因此，它使用 `AddCheck()` 方法添加了多个运行状况检查。</span><span class="sxs-lookup"><span data-stu-id="49994-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="49994-140">对于每个依赖服务，需要添加自定义 `IHealthCheck` 实现，用于定义其各自的运行状况状态。</span><span class="sxs-lookup"><span data-stu-id="49994-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="49994-141">开放源代码项目 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 可通过为基于 .NET Core 3.1 构建的每个企业服务提供自定义运行状况检查实现，解决此问题。</span><span class="sxs-lookup"><span data-stu-id="49994-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET Core 3.1.</span></span> <span data-ttu-id="49994-142">每个运行状况检查都可作为单独的 NuGet 包，可轻松添加到项目。</span><span class="sxs-lookup"><span data-stu-id="49994-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="49994-143">eShopOnContainers 将其广泛用于其所有微服务。</span><span class="sxs-lookup"><span data-stu-id="49994-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="49994-144">例如，在 `Catalog.API` 微服务中，添加了以下 NuGet 包：</span><span class="sxs-lookup"><span data-stu-id="49994-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![AspNetCore.Diagnostics.HealthChecks NuGet 包的屏幕截图。](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="49994-146">**图 8-7**。</span><span class="sxs-lookup"><span data-stu-id="49994-146">**Figure 8-7**.</span></span> <span data-ttu-id="49994-147">使用 AspNetCore.Diagnostics.HealthChecks 在 Catalog.API 中实现的运行状况检查</span><span class="sxs-lookup"><span data-stu-id="49994-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="49994-148">在以下代码中，将为每项依赖服务添加运行状况检查实现，然后配置中间件：</span><span class="sxs-lookup"><span data-stu-id="49994-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

<span data-ttu-id="49994-149">最后，添加 HealthCheck 中间件，用于侦听“/hc”终结点：</span><span class="sxs-lookup"><span data-stu-id="49994-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="49994-150">查询微服务，以报告其运行状况状态</span><span class="sxs-lookup"><span data-stu-id="49994-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="49994-151">按照本文所述配置好运行状况检查后，每当在 Docker 上运行该微服务，便可直接通过浏览器检查其运行状况是否正常。</span><span class="sxs-lookup"><span data-stu-id="49994-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="49994-152">必须在 Docker 主机中发布容器端口，以便通过外部 Docker 主机 IP 或 `localhost` 访问该容器，如图 8-8 所示。</span><span class="sxs-lookup"><span data-stu-id="49994-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![运行状况检查返回的 JSON 响应的屏幕截图。](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="49994-154">**图 8-8**。</span><span class="sxs-lookup"><span data-stu-id="49994-154">**Figure 8-8**.</span></span> <span data-ttu-id="49994-155">通过浏览器检查单个服务的运行状况状态</span><span class="sxs-lookup"><span data-stu-id="49994-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="49994-156">在该测试中，可以看到 `Catalog.API` 微服务（在端口 5101 上运行）处于正常运行状态，并以 JSON 形式返回 HTTP 状态 200 和状态信息。</span><span class="sxs-lookup"><span data-stu-id="49994-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="49994-157">该服务还检查了其 SQL Server 数据库依赖项和 RabbitMQ 的运行状况，以便运行状况检查报告显示其运行正常。</span><span class="sxs-lookup"><span data-stu-id="49994-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="49994-158">使用监视程序</span><span class="sxs-lookup"><span data-stu-id="49994-158">Use watchdogs</span></span>

<span data-ttu-id="49994-159">监视程序是一项单独服务，可以监视多个服务的运行和负载状况，并借助前面介绍的 `HealthChecks` 库进行查询，从而报告微服务的运行状况。</span><span class="sxs-lookup"><span data-stu-id="49994-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="49994-160">这有助于防止某些根据单个服务视图检测不到的错误。</span><span class="sxs-lookup"><span data-stu-id="49994-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="49994-161">监视程序也是托管代码的好选择，可以在没有用户交互的情况下根据已知情况执行修正操作。</span><span class="sxs-lookup"><span data-stu-id="49994-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="49994-162">eShopOnContainers 示例包含一个网页，该网页显示了示例运行状况检查报告，如图 8-9 所示。</span><span class="sxs-lookup"><span data-stu-id="49994-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="49994-163">这是最简单的监视程序，因为它只显示 eShopOnContainers 中的微服务和 Web 应用程序的状态。</span><span class="sxs-lookup"><span data-stu-id="49994-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="49994-164">通常，监视程序在检测到不正常运行状态时还会执行相应操作。</span><span class="sxs-lookup"><span data-stu-id="49994-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="49994-165">幸运的是，[AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 还提供 [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet 包，可用于通过已配置的 URI 显示运行状况检查结果。</span><span class="sxs-lookup"><span data-stu-id="49994-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![运行状况检查 UI eShopOnContainers 运行状况状态的屏幕截图。](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="49994-167">**图 8-9**。</span><span class="sxs-lookup"><span data-stu-id="49994-167">**Figure 8-9**.</span></span> <span data-ttu-id="49994-168">eShopOnContainers 中的示例运行状况检查报告</span><span class="sxs-lookup"><span data-stu-id="49994-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="49994-169">总之，此监视器服务可查询每个微服务的“/hc”终结点。</span><span class="sxs-lookup"><span data-stu-id="49994-169">In summary, this watchdog service queries each microservice's "/hc" endpoint.</span></span> <span data-ttu-id="49994-170">这将执行其中定义的所有运行状况检查，并根据这些检查返回总体运行状况状态。</span><span class="sxs-lookup"><span data-stu-id="49994-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="49994-171">可通过几个配置项和两行代码（需要添加到监视器服务的 Startup.cs 中）轻松使用 HealthChecksUI。</span><span class="sxs-lookup"><span data-stu-id="49994-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the *Startup.cs* of the watchdog service.</span></span>

<span data-ttu-id="49994-172">运行状况检查 UI 的示例配置文件：</span><span class="sxs-lookup"><span data-stu-id="49994-172">Sample configuration file for health check UI:</span></span>

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

<span data-ttu-id="49994-173">用于添加 HealthChecksUI 的 Startup.cs 文件：</span><span class="sxs-lookup"><span data-stu-id="49994-173">*Startup.cs* file that adds HealthChecksUI:</span></span>

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config => config.UIPath = "/hc-ui");
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="49994-174">在使用业务流程协调程序的情况下执行运行状况检查</span><span class="sxs-lookup"><span data-stu-id="49994-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="49994-175">若要监视微服务的可用性，Kubernetes 和 Service Fabric 等业务流程协调程序可通过发送微服务测试请求来定期执行运行状况检查。</span><span class="sxs-lookup"><span data-stu-id="49994-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="49994-176">若业务流程协调程序确定某服务/容器运行不正常，它会停止向该实例路由请求。</span><span class="sxs-lookup"><span data-stu-id="49994-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="49994-177">通常，它还会为该容器创建新实例。</span><span class="sxs-lookup"><span data-stu-id="49994-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="49994-178">例如，大多数业务流程协调程序可以使用运行状况检查来管理不会停机的部署。</span><span class="sxs-lookup"><span data-stu-id="49994-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="49994-179">仅当服务/容器的状态变为正常时，业务流程协调程序才会开始将流量路由到服务/容器实例。</span><span class="sxs-lookup"><span data-stu-id="49994-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="49994-180">当业务流程协调程序执行应用程序升级时，运行状况监视尤为重要。</span><span class="sxs-lookup"><span data-stu-id="49994-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="49994-181">某些业务流程协调程序（如 Azure Service Fabric）会分阶段更新服务，例如，它们可能为每个应用程序升级更新五分之一的群集面。</span><span class="sxs-lookup"><span data-stu-id="49994-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="49994-182">同时升级的一组节点称为“升级域”  。</span><span class="sxs-lookup"><span data-stu-id="49994-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="49994-183">完成每个升级域的升级操作并面向用户提供后，在部署进程移至下一升级域之前，该升级域必须通过运行状况检查。</span><span class="sxs-lookup"><span data-stu-id="49994-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="49994-184">服务运行状况的另一方面是报告服务的指标。</span><span class="sxs-lookup"><span data-stu-id="49994-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="49994-185">这是某些业务流程协调程序（如 Service Fabric）运行状况模型的高级功能。</span><span class="sxs-lookup"><span data-stu-id="49994-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="49994-186">因为要借助指标来平衡资源使用情况，所以在使用业务流程协调程序时，指标非常重要。</span><span class="sxs-lookup"><span data-stu-id="49994-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="49994-187">指标也可以是系统运行状况的指示器。</span><span class="sxs-lookup"><span data-stu-id="49994-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="49994-188">例如，某个应用程序包含多个微服务，并且每个实例都会报告每秒的请求数 (RPS) 指标。</span><span class="sxs-lookup"><span data-stu-id="49994-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="49994-189">如果某一服务使用的资源（内存、处理器等）比另一个服务多，则业务流程协调程序会在群集中移动服务实例，尝试使资源使用保持均衡状态。</span><span class="sxs-lookup"><span data-stu-id="49994-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="49994-190">请注意，Azure Service Fabric 提供自己的[运行状况监视模型](/azure/service-fabric/service-fabric-health-introduction)，该模型比简单的运行状况检查更高级。</span><span class="sxs-lookup"><span data-stu-id="49994-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="49994-191">高级监视：可视化、分析和警报</span><span class="sxs-lookup"><span data-stu-id="49994-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="49994-192">监视的最后一部分是对事件流进行可视化、报告服务性能、以及在检测到问题时发出警报。</span><span class="sxs-lookup"><span data-stu-id="49994-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="49994-193">可以使用不同的解决方案来进行这方面的监视。</span><span class="sxs-lookup"><span data-stu-id="49994-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="49994-194">可以使用显示服务状态的简单自定义应用程序，例如介绍 [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) 时显示的自定义页。</span><span class="sxs-lookup"><span data-stu-id="49994-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="49994-195">或者，可以使用更高级的工具（如 [Azure Monitor](https://azure.microsoft.com/services/monitor/)）基于事件流发出警报。</span><span class="sxs-lookup"><span data-stu-id="49994-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="49994-196">最后，如果要存储所有事件流，可以使用 Microsoft Power BI 或其他解决方案（如 Kibana 或 Splunk）来可视化数据。</span><span class="sxs-lookup"><span data-stu-id="49994-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="49994-197">其他资源</span><span class="sxs-lookup"><span data-stu-id="49994-197">Additional resources</span></span>

- <span data-ttu-id="49994-198">**适用于 ASP.NET Core 的 HealthChecks 和 HealthChecks UI** </span><span class="sxs-lookup"><span data-stu-id="49994-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="49994-199">**Service Fabric 运行状况监视简介** </span><span class="sxs-lookup"><span data-stu-id="49994-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="49994-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="49994-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="49994-201">[上一页](implement-circuit-breaker-pattern.md)
>[下一页](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="49994-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
