---
title: 通过 Ocelot 实现 API 网关
description: 了解如何通过 Ocelot 实现 API 网关以及如何在基于容器的环境中使用 Ocelot。
ms.date: 03/02/2020
ms.openlocfilehash: f103c1e394a3f829489b61fd17af749798b02f70
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864093"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="de66a-103">通过 Ocelot 实现 API 网关</span><span class="sxs-lookup"><span data-stu-id="de66a-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de66a-104">引用微服务应用程序 [ eShopOnContainers ](https://github.com/dotnet-architecture/eShopOnContainers) 当前正在使用 [Envoy](https://www.envoyproxy.io/) 提供的功能来实现 API 网关，而不是之前引用的 [Ocelot](https://github.com/ThreeMammals/Ocelot)。</span><span class="sxs-lookup"><span data-stu-id="de66a-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="de66a-105">我们之所以选择这种设计，是因为 Envoy 对 WebSocket 协议的内置支持，这是 eShopOnContainers 中实现的新 gRPC 服务间通信所必需的。</span><span class="sxs-lookup"><span data-stu-id="de66a-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="de66a-106">但是，我们在指南中保留了此部分，因此，你可以将 Ocelot 视为适用于生产级方案的简单且功能强大的轻型 API 网关。</span><span class="sxs-lookup"><span data-stu-id="de66a-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="de66a-107">构建和设计 API 网关</span><span class="sxs-lookup"><span data-stu-id="de66a-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="de66a-108">以下体系结构关系图显示了如何在 eShopOnContainers 中通过 Ocelot 实现 API 网关。</span><span class="sxs-lookup"><span data-stu-id="de66a-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![显示 eShopOnContainers 体系结构的图示。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="de66a-110">图 6-28。</span><span class="sxs-lookup"><span data-stu-id="de66a-110">**Figure 6-28**.</span></span> <span data-ttu-id="de66a-111">使用 API 网关的 eShopOnContainers 体系结构</span><span class="sxs-lookup"><span data-stu-id="de66a-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="de66a-112">该图显示了如何使用“用于 Windows 的 Docker”或“用于 Mac 的 Docker”将整个应用程序部署到单个 Docker 主机或开发电脑。</span><span class="sxs-lookup"><span data-stu-id="de66a-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="de66a-113">然而，虽然部署到业务流程协调程序中的方法与之相似，但图中的容器都可在业务流程协调程序中横向扩展。</span><span class="sxs-lookup"><span data-stu-id="de66a-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="de66a-114">此外，应从业务流程协调程序卸载基础结构资产（如数据库、缓存和消息代理），并将其部署到基础结构的高可用系统，如 Azure SQL 数据库、Azure Cosmos DB、Azure Redis、Azure 服务总线或本地 HA 群集解决方案。</span><span class="sxs-lookup"><span data-stu-id="de66a-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="de66a-115">此外，在关系图中还可以看到，在开发和部署微服务以及自己的相关 API 网关时，拥有多个 API 网关后，多个开发团队可进行自治（在本例中为“营销”功能和“购物”功能）。</span><span class="sxs-lookup"><span data-stu-id="de66a-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="de66a-116">如果有单一 API 网关，这意味着多个开发团队可更新单个点，由此可将所有微服务与应用程序的某一个部分相结合。</span><span class="sxs-lookup"><span data-stu-id="de66a-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="de66a-117">更进一步来说，在设计时，有时也可将精细 API 网关限于单个业务微服务，具体取决于所选体系结构。</span><span class="sxs-lookup"><span data-stu-id="de66a-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="de66a-118">使用由业务或域指示的 API 网关边界将有助于更好地设计。</span><span class="sxs-lookup"><span data-stu-id="de66a-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="de66a-119">例如，由于精细 API 网关的概念类似于 UI 复合服务，因此 API 网关层中的精细粒度特别适用于基于微服务的高级复合 UI 应用程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="de66a-120">上一节[创建基于微服务的复合 UI](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md) 中深入介绍许多详细信息。</span><span class="sxs-lookup"><span data-stu-id="de66a-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="de66a-121">对于许多中型和大型应用程序，关键在于使用自定义生成的 API 网关产品，这通常是一种不错的方法，但不能作为单一聚合器或唯一的中央自定义 API 网关，除非该 API 网关允许多个开发团队在多个独立配置区域创建自主微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="de66a-122">通过 API 网关重新路由的示例微服务/容器</span><span class="sxs-lookup"><span data-stu-id="de66a-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="de66a-123">例如，eShopOnContainers 具有大约六项必须通过 API 网关发布的内部微服务类型，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![显示其子文件夹的“服务”文件夹的屏幕截图。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="de66a-125">图 6-29。</span><span class="sxs-lookup"><span data-stu-id="de66a-125">**Figure 6-29**.</span></span> <span data-ttu-id="de66a-126">Visual Studio 的 eShopOnContainers 解决方案中的微服务文件夹</span><span class="sxs-lookup"><span data-stu-id="de66a-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="de66a-127">对于“标识”服务，尽管借助 Ocelot，也可以将其纳入重新路由列表，但在设计过程中会将其从 API 网关路由中排除，因为它是系统中唯一的横切关注点。</span><span class="sxs-lookup"><span data-stu-id="de66a-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="de66a-128">目前，所有这些服务都是作为 ASP.NET Core Web API 服务实现的，可以从代码中了解到。</span><span class="sxs-lookup"><span data-stu-id="de66a-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="de66a-129">我们主要来看一项微服务，比如“目录”微服务代码。</span><span class="sxs-lookup"><span data-stu-id="de66a-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![显示 Catalog.API 项目内容的解决方案资源管理器的屏幕截图。](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="de66a-131">图 6-30。</span><span class="sxs-lookup"><span data-stu-id="de66a-131">**Figure 6-30**.</span></span> <span data-ttu-id="de66a-132">Web API 微服务示例（“目录”微服务）</span><span class="sxs-lookup"><span data-stu-id="de66a-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="de66a-133">可看到“目录”微服务是典型的 ASP.NET Core Web API 项目，其中包含多个控制器和方法，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="de66a-134">HTTP 请求将最终运行访问微服务数据库的那种 C# 代码以及任何其他必需的操作。</span><span class="sxs-lookup"><span data-stu-id="de66a-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="de66a-135">对于微服务 URL，当容器部署在本地开发电脑（本地 Docker 主机）中时，每个微服务的容器始终有一个内部端口（通常是端口 80），在其 dockerfile 中指定，如以下 dockerfile 中所示：</span><span class="sxs-lookup"><span data-stu-id="de66a-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container always has an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="de66a-136">代码中显示的端口 80 位于 Docker 主机内部，因此客户端应用无法访问。</span><span class="sxs-lookup"><span data-stu-id="de66a-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="de66a-137">客户端应用只能访问使用 `docker-compose` 进行部署时发布的外部端口（如有）。</span><span class="sxs-lookup"><span data-stu-id="de66a-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="de66a-138">部署到生产环境时，不应发布这些外部端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="de66a-139">这正是要使用 API 网关的原因，这样可避免客户端应用与微服务直接通信。</span><span class="sxs-lookup"><span data-stu-id="de66a-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="de66a-140">但是，在开发时，却要直接访问微服务/容器并通过 Swagger 运行它。</span><span class="sxs-lookup"><span data-stu-id="de66a-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="de66a-141">这就是为什么在 eShopOnContainers 中，即使 API 网关或客户端应用不使用外部端口，仍要指定外部端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="de66a-142">以下是“目录”微服务的 `docker-compose.override.yml` 文件示例：</span><span class="sxs-lookup"><span data-stu-id="de66a-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="de66a-143">可以看到如何在 docker-compose.override.yml 配置中将端口 80 作为“目录”容器的内部端口，将端口 5101 作为外部访问的端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="de66a-144">但是，使用 API 网关时，应用程序不应使用此端口，端口仅用于调试、运行和测试“目录”微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="de66a-145">通常不会将 docker-compose 部署到生产环境中，因为适合微服务的生产部署环境是 Kubernetes 或 Service Fabric 等业务流程协调程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="de66a-146">部署到这些环境时，会使用不同的配置文件，部署时不直接发布微服务的任何外部端口，但始终要使用 API 网关中的反向代理。</span><span class="sxs-lookup"><span data-stu-id="de66a-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="de66a-147">在本地 Docker 主机中运行“目录”微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="de66a-148">从 Visual Studio 运行完整的 eShopOnContainers 解决方案（它将运行 docker-compose 文件中的所有服务）；在 CMD 或放置 `docker-compose.yml` 和 `docker-compose.override.yml` 的文件夹中的 PowerShell 中运行以下 docker-compose 命令启动“目录”微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="de66a-149">此命令仅运行 catalog-api 服务容器以及 docker-compose.yml 中指定的依赖项。</span><span class="sxs-lookup"><span data-stu-id="de66a-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="de66a-150">此事例中为 SQL Server 容器和 RabbitMQ 容器。</span><span class="sxs-lookup"><span data-stu-id="de66a-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="de66a-151">然后，可直接访问“目录”微服务，并直接通过该“外部”端口由 Swagger UI 查看其方法，此事例中为 `http://localhost:5101/swagger`：</span><span class="sxs-lookup"><span data-stu-id="de66a-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![显示 Catalog.API REST API 的 Swagger UI 的屏幕截图。](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="de66a-153">图 6-31。</span><span class="sxs-lookup"><span data-stu-id="de66a-153">**Figure 6-31**.</span></span> <span data-ttu-id="de66a-154">通过其 Swagger UI 测试“目录”微服务</span><span class="sxs-lookup"><span data-stu-id="de66a-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="de66a-155">此时，可在 Visual Studio 中的 C# 代码中设置断点，使用 Swagger UI 中公开的方法测试微服务，最后使用 `docker-compose down` 命令清理所有内容。</span><span class="sxs-lookup"><span data-stu-id="de66a-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="de66a-156">但是，在这种情况下，通过外部端口 5101 直接访问与微服务的通信正是你希望在应用程序中避免的。</span><span class="sxs-lookup"><span data-stu-id="de66a-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="de66a-157">可设置 API 网关的间接附加级别来避免该情况（此事例中为 Ocelot）。</span><span class="sxs-lookup"><span data-stu-id="de66a-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="de66a-158">这样一来，客户端应用将不会直接访问微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="de66a-159">通过 Ocelot 实现 API 网关</span><span class="sxs-lookup"><span data-stu-id="de66a-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="de66a-160">Ocelot 基本上是一组可按特定顺序应用的中间件。</span><span class="sxs-lookup"><span data-stu-id="de66a-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="de66a-161">Ocelot 仅适用于 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="de66a-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="de66a-162">包的最新版本以 `.NETCoreApp 3.1` 为目标，因此不适用于 .NET Framework 应用程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-162">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="de66a-163">使用 Visual Studio 中的 [Ocelot NuGet 包](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 项目中安装 Ocelot 及其依赖项。</span><span class="sxs-lookup"><span data-stu-id="de66a-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="de66a-164">在 eShopOnContainers 中，其 API 网关实现是一个非常简单的 ASP.NET Core WebHost 项目，而 Ocelot 的中间件可处理所有 API 网关功能，如下图所示：</span><span class="sxs-lookup"><span data-stu-id="de66a-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![显示 Ocelot API 网关项目的解决方案资源管理器的屏幕截图。](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="de66a-166">图 6-32。</span><span class="sxs-lookup"><span data-stu-id="de66a-166">**Figure 6-32**.</span></span> <span data-ttu-id="de66a-167">eShopOnContainers 中的 OcelotApiGw 基础项目</span><span class="sxs-lookup"><span data-stu-id="de66a-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="de66a-168">此 ASP.NET Core WebHost 项目基本上由两个简单文件生成：`Program.cs` 和 `Startup.cs`。</span><span class="sxs-lookup"><span data-stu-id="de66a-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="de66a-169">Program.cs 只需要创建和配置典型的 ASP.NET Core BuildWebHost。</span><span class="sxs-lookup"><span data-stu-id="de66a-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="de66a-170">对于 Ocelot，必须通过 `AddJsonFile()` 方法向生成器提供 `configuration.json` 文件。</span><span class="sxs-lookup"><span data-stu-id="de66a-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="de66a-171">通常可使用不同端口在 `configuration.json` 中指定所有 API 网关 Re-Route，即具有特定端口的外部终结点和相关内部终结点。</span><span class="sxs-lookup"><span data-stu-id="de66a-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="de66a-172">配置具有两个部分。</span><span class="sxs-lookup"><span data-stu-id="de66a-172">There are two sections to the configuration.</span></span> <span data-ttu-id="de66a-173">一组 ReRoute 和一个 GlobalConfiguration。</span><span class="sxs-lookup"><span data-stu-id="de66a-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="de66a-174">ReRoute 是指示 Ocelot 如何处理上游请求的对象。</span><span class="sxs-lookup"><span data-stu-id="de66a-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="de66a-175">全局配置允许替代 ReRoute 特定设置。</span><span class="sxs-lookup"><span data-stu-id="de66a-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="de66a-176">如果不想管理大量的 ReRoute 特定设置，可采用此方法。</span><span class="sxs-lookup"><span data-stu-id="de66a-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="de66a-177">以下是 eShopOnContainers 中某个 API 网关的 [ReRoute 配置文件](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)的简化示例。</span><span class="sxs-lookup"><span data-stu-id="de66a-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="de66a-178">Ocelot API 网关的主要功能是接收传入的 HTTP 请求并将其转发到下游服务，目前作为另一 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="de66a-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="de66a-179">Ocelot 将一个请求到另一请求的路由描述为 ReRoute。</span><span class="sxs-lookup"><span data-stu-id="de66a-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="de66a-180">例如，我们主要来看上方 configuration.json（即“购物篮”微服务的配置）中的某个 ReRoute。</span><span class="sxs-lookup"><span data-stu-id="de66a-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="de66a-181">DownstreamPathTemplate、Scheme 和 DownstreamHostAndPorts 构成要将此请求转发到的内部微服务 URL。</span><span class="sxs-lookup"><span data-stu-id="de66a-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="de66a-182">端口是服务使用的内部端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="de66a-183">使用容器时，在其 dockerfile 中指定端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="de66a-184">`Host` 是一个服务名称，取决于使用的服务名称解析。</span><span class="sxs-lookup"><span data-stu-id="de66a-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="de66a-185">使用 docker-compose 时，服务名称由 Docker 主机提供，它使用 docker-compose 文件中提供的服务名称。</span><span class="sxs-lookup"><span data-stu-id="de66a-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="de66a-186">如果使用 Kubernetes 或 Service Fabric 等业务流程协调程序，则应通过每个业务流程协调程序提供的 DNS 或名称解析来解析该名称。</span><span class="sxs-lookup"><span data-stu-id="de66a-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="de66a-187">DownstreamHostAndPorts 是一个数组，包含要将请求转发到的任何下游服务的主机和端口。</span><span class="sxs-lookup"><span data-stu-id="de66a-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="de66a-188">通常这只包含一个条目，但有时可能想要将均衡请求加载到下游服务，而通过 Ocelot 即可添加多个条目，然后选择负载均衡器。</span><span class="sxs-lookup"><span data-stu-id="de66a-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="de66a-189">但是如果使用 Azure 和任何业务流程协调程序，那么通过云和业务流程协调程序基础结构进行负载均衡可能会更好。</span><span class="sxs-lookup"><span data-stu-id="de66a-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="de66a-190">UpstreamPathTemplate 是一个 URL，Ocelot 将其用来识别用于客户端中给定请求的 DownstreamPathTemplate。</span><span class="sxs-lookup"><span data-stu-id="de66a-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="de66a-191">最后，使用了 UpstreamHttpMethod，因此 Ocelot 可区分对相同 URL 的不同的请求（GET、POST、PUT）。</span><span class="sxs-lookup"><span data-stu-id="de66a-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="de66a-192">此时，即可拥有使用一个或[多个合并 configuration.json 文件](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)的单个 Ocelot API 网关，也可将[配置存储在 Consul KV 存储中](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)。</span><span class="sxs-lookup"><span data-stu-id="de66a-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="de66a-193">但正如体系结构和设计部分中所介绍的那样，如果真的想拥有自主微服务，那么最好将单一 API 网关拆分成多个 API 网关和/或 BFF（用于前端的后端）。</span><span class="sxs-lookup"><span data-stu-id="de66a-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="de66a-194">为此，我们来看看如何通过 Docker 容器实现该方法。</span><span class="sxs-lookup"><span data-stu-id="de66a-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="de66a-195">使用单个 Docker 容器映像运行多个不同类型的 API 网关/BFF 容器</span><span class="sxs-lookup"><span data-stu-id="de66a-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="de66a-196">在 eShopOnContainers 中，为 Ocelot API 网关使用单个 Docker 容器映像。但是在运行时，通过提供不同的 configuration.json 文件为每种类型的 API 网关/BFF 创建不同的服务/容器，并使用 docker 卷为每个服务访问不同的 PC 文件夹。</span><span class="sxs-lookup"><span data-stu-id="de66a-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![所有 API 网关的单个 Ocelot 网关 Docker 映像的图示。](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="de66a-198">图 6-33。</span><span class="sxs-lookup"><span data-stu-id="de66a-198">**Figure 6-33**.</span></span> <span data-ttu-id="de66a-199">在多个 API 网关类型中重用单个 Ocelot Docker 映像</span><span class="sxs-lookup"><span data-stu-id="de66a-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="de66a-200">在 eShopOnContainers 中，使用名为“OcelotApiGw”的项目和 docker-compose.yml 文件中指定的映像名称“eshop/ocelotapigw”创建“Generic Ocelot API Gateway Docker Image”。</span><span class="sxs-lookup"><span data-stu-id="de66a-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="de66a-201">然后在部署到 Docker 时，会有四个从同一 Docker 映像创建的 API 网关容器，如以下从 docker-compose.yml 文件中提取的内容所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="de66a-202">另外，如 docker-compose.override.yml 文件所示，这些 API 网关容器之间唯一的区别是 Ocelot 配置文件，该文件对每个服务容器的配置文件都不同，并且在运行时通过 Docker 卷指定。</span><span class="sxs-lookup"><span data-stu-id="de66a-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="de66a-203">由于上面的代码，并且如下方 Visual Studio Explorer 所示，定义每个特定业务/BFF API 网关所需的唯一文件只有 configuration.json 文件，因为这四个 API 网关基于相同 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="de66a-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![显示具有 configuration.json 文件的所有 API 网关的屏幕截图。](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="de66a-205">图 6-34。</span><span class="sxs-lookup"><span data-stu-id="de66a-205">**Figure 6-34**.</span></span> <span data-ttu-id="de66a-206">使用 Ocelot 定义每个 API 网关/BFF 所需的唯一文件是配置文件</span><span class="sxs-lookup"><span data-stu-id="de66a-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="de66a-207">将 API 网关拆分成多个 API 网关后，专注于不同微服务子集的不同开发团队可使用独立 Ocelot 配置文件来管理自己的 API 网关。</span><span class="sxs-lookup"><span data-stu-id="de66a-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="de66a-208">同时重用相同的 Ocelot Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="de66a-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="de66a-209">现在，如果通过 API 网关运行 eShopOnContainers（在打开 eShopOnContainers-ServicesAndWebApps.sln 解决方案或运行“docker-compose up”时，默认包含在 VS 中），将执行以下示例路由。</span><span class="sxs-lookup"><span data-stu-id="de66a-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="de66a-210">例如，访问 webshoppingapigw API 网关提供的上游 URL `http://localhost:5202/api/v1/c/catalog/items/2/` 时，将从 Docker 主机中的内部下游 URL `http://catalog-api/api/v1/2` 获取相同结果，如以下浏览器所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![显示通过 API 网关进行响应的浏览器屏幕截图。](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="de66a-212">图 6-35。</span><span class="sxs-lookup"><span data-stu-id="de66a-212">**Figure 6-35**.</span></span> <span data-ttu-id="de66a-213">通过 API 网关提供的 URL 访问微服务</span><span class="sxs-lookup"><span data-stu-id="de66a-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="de66a-214">由于测试或调试原因，如果想不通过 API 网关直接访问目录 Docker 容器（仅在开发环境中），考虑到“catalog-api”是 Docker 主机内部的 DNS 解析（由 docker-compose 服务名称处理服务发现），直接访问容器的唯一方法是通过 docker-compose.override.yml 中发布的外部端口，该端口仅用于开发测试，例如以下浏览器中的 `http://localhost:5101/api/v1/Catalog/items/1`。</span><span class="sxs-lookup"><span data-stu-id="de66a-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![显示对 Catalog.api 的直接响应的浏览器屏幕截图。](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="de66a-216">图 6-36。</span><span class="sxs-lookup"><span data-stu-id="de66a-216">**Figure 6-36**.</span></span> <span data-ttu-id="de66a-217">出于测试目的直接访问微服务</span><span class="sxs-lookup"><span data-stu-id="de66a-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="de66a-218">但由于已配置应用程序，因此它会通过 API 网关访问所有微服务，而非通过直接端口“快捷方式”。</span><span class="sxs-lookup"><span data-stu-id="de66a-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="de66a-219">eShopOnContainers 中的网关聚合模式</span><span class="sxs-lookup"><span data-stu-id="de66a-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="de66a-220">如上所述，可通过代码使用自定义服务灵活实现请求聚合。</span><span class="sxs-lookup"><span data-stu-id="de66a-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="de66a-221">还可使用 [Ocelot 中的请求聚合功能](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)实现请求聚合，但可能无法满足你对灵活性的要求。</span><span class="sxs-lookup"><span data-stu-id="de66a-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="de66a-222">因此，在 eShopOnContainers 中实现聚合的首选方法是为每个聚合器提供显式 ASP.NET Core Web API 服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="de66a-223">根据该方法，在考虑到早前所示的简化全局体系结构关系图中未显示的聚合器服务时，API 网关复合关系图实际上得到了更多扩展。</span><span class="sxs-lookup"><span data-stu-id="de66a-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="de66a-224">在下图中，还可了解聚合器服务如何与其相关 API 网关协同工作。</span><span class="sxs-lookup"><span data-stu-id="de66a-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![显示聚合器服务的 eShopOnContainers 体系结构的图示。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="de66a-226">图 6-37。</span><span class="sxs-lookup"><span data-stu-id="de66a-226">**Figure 6-37**.</span></span> <span data-ttu-id="de66a-227">使用聚合器服务的 eShopOnContainers 体系结构</span><span class="sxs-lookup"><span data-stu-id="de66a-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="de66a-228">进一步放大视图，在下图的“购物”业务区中，可以看到在使用 API 网关中的聚合器服务时，客户端应用和微服务之间的干扰减少了。</span><span class="sxs-lookup"><span data-stu-id="de66a-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![显示放大的 eShopOnContainers 体系结构的图示。](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="de66a-230">图 6-38。</span><span class="sxs-lookup"><span data-stu-id="de66a-230">**Figure 6-38**.</span></span> <span data-ttu-id="de66a-231">聚合器服务的放大影像</span><span class="sxs-lookup"><span data-stu-id="de66a-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="de66a-232">可以看到，当关系图显示可能来自 API 网关的请求时，它可能变得复杂。</span><span class="sxs-lookup"><span data-stu-id="de66a-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="de66a-233">虽然可以看到如何简化蓝色箭头，但从客户端应用角度来看，通过减少通信中的干扰和延迟来使用聚合器模式时，尤其是远程应用（移动和 SPA 应用）的用户体验最终可获得显著改善。</span><span class="sxs-lookup"><span data-stu-id="de66a-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="de66a-234">对于“营销”业务范围和微服务，它是一个简单的用例，因此不需要使用聚合器，但如果需要，也可使用。</span><span class="sxs-lookup"><span data-stu-id="de66a-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="de66a-235">Ocelot API 网关中的身份验证和授权</span><span class="sxs-lookup"><span data-stu-id="de66a-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="de66a-236">在 Ocelot API 网关中，可使用提供身份验证令牌的 [IdentityServer](https://identityserver.io/)，在 API 网关外部或内部设置身份验证服务，例如 ASP.NET Core Web API 服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="de66a-237">由于 eShopOnContainers 使用的多个 API 网关具有基于 BFF 和业务范围的边界，因此“标识/身份验证”服务排除在 API 网关之外，如下图中黄色高亮部分所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![显示 API 网关下的标识微服务的图示。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="de66a-239">图 6-39。</span><span class="sxs-lookup"><span data-stu-id="de66a-239">**Figure 6-39**.</span></span> <span data-ttu-id="de66a-240">eShopOnContainers 中的“标识”服务的位置</span><span class="sxs-lookup"><span data-stu-id="de66a-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="de66a-241">但是，Ocelot 还支持在 API 网关边界内设置“标识/身份验证”微服务，如另一图所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![显示 Ocelot API 网关中的身份验证的图示。](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="de66a-243">图 6-40。</span><span class="sxs-lookup"><span data-stu-id="de66a-243">**Figure 6-40**.</span></span> <span data-ttu-id="de66a-244">Ocelot 中的身份验证</span><span class="sxs-lookup"><span data-stu-id="de66a-244">Authentication in Ocelot</span></span>

<span data-ttu-id="de66a-245">如上图所示，当标识微服务位于 API 网关 (AG) 下时：1) AG 从标识微服务请求身份验证令牌，2) 标识微服务将令牌返回到 AG，3-4) AG 使用身份验证令牌向微服务发出请求。</span><span class="sxs-lookup"><span data-stu-id="de66a-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="de66a-246">由于 eShopOnContainers 应用程序已将 API 网关拆分为多个 BFF（用于前端的后端）和业务范围 API 网关，因此另一种选择是为横切关注点创建其他 API 网关。</span><span class="sxs-lookup"><span data-stu-id="de66a-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="de66a-247">对于基于更复杂的微服务且具有多个横切关注点微服务的架构，这种选择更加合理。</span><span class="sxs-lookup"><span data-stu-id="de66a-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="de66a-248">由于 eShopOnContainers 中只有一个横切关注点，为简单起见，决定仅从 API 网关领域处理安全服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="de66a-249">在任何情况下，如果应用受到 API 网关级别的保护，则尝试使用任何安全的微服务时，首先会访问 Ocelot API 网关的身份验证模块。</span><span class="sxs-lookup"><span data-stu-id="de66a-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="de66a-250">这将重定向 HTTP 请求，访问“标识”或“身份验证”微服务以获取访问令牌，这样便可通过 access_token 访问受保护的服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="de66a-251">使用身份验证在 API 网关级别保护服务的方法是在 configuration.json 的相关设置中设置 AuthenticationProviderKey。</span><span class="sxs-lookup"><span data-stu-id="de66a-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="de66a-252">Ocelot 运行时，会查看 ReRoutes AuthenticationOptions.AuthenticationProviderKey 并检查是否有使用给定密钥注册的验证提供程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="de66a-253">如果没有，那么 Ocelot 将不会启动。</span><span class="sxs-lookup"><span data-stu-id="de66a-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="de66a-254">如果有，那么 ReRoute 将在执行时使用该提供程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="de66a-255">由于通过 `authenticationProviderKey = "IdentityApiKey"` 配置了 Ocelot WebHost，只要该服务的任何请求不具备身份验证令牌，就需要进行身份验证。</span><span class="sxs-lookup"><span data-stu-id="de66a-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="de66a-256">然后，还需要在微服务等任何要访问的资源（如以下“购物篮”微服务控制器）上通过 [Authorize] 属性设置授权。</span><span class="sxs-lookup"><span data-stu-id="de66a-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="de66a-257">ValidAudience（如“basket”）通过 Startup 类的 ConfigureServices() 中的 `AddJwtBearer()` 与每个微服务中定义的受众相关联，如下方代码所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="de66a-258">如果尝试使用基于 API 网关的 ReRoute URL（例如 `http://localhost:5202/api/v1/b/basket/1`）访问任何安全的微服务（如“购物篮”微服务），除非提供有效令牌，否则会出现“401 未授权”。</span><span class="sxs-lookup"><span data-stu-id="de66a-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="de66a-259">另一方面，如果 ReRoute URL 未经身份验证，Ocelot 将调用与其关联的任何下游方案（内部微服务 URL）。</span><span class="sxs-lookup"><span data-stu-id="de66a-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="de66a-260">Ocelot 的 ReRoute 层中的授权。</span><span class="sxs-lookup"><span data-stu-id="de66a-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="de66a-261">Ocelot 支持在进行身份验证后评估的基于声明的授权。</span><span class="sxs-lookup"><span data-stu-id="de66a-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="de66a-262">通过将以下行添加到 ReRoute 配置中，可以在路由级别设置授权。</span><span class="sxs-lookup"><span data-stu-id="de66a-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="de66a-263">在该示例中，调用授权中间件时，Ocelot 将查找用户在令牌中是否具有声明类型“UserType”并且该声明的值是否为“employee”。</span><span class="sxs-lookup"><span data-stu-id="de66a-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="de66a-264">如果不是，则不向用户授权，并且响应为 403 禁止访问。</span><span class="sxs-lookup"><span data-stu-id="de66a-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="de66a-265">使用 Kubernetes 入口和 Ocelot API 网关</span><span class="sxs-lookup"><span data-stu-id="de66a-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="de66a-266">使用 Kubernetes 时（如在 Azure Kubernetes 服务群集中），通常会根据 Nginx 通过 [Kubernetes 入口层](https://kubernetes.io/docs/concepts/services-networking/ingress/)统一所有 HTTP 请求。</span><span class="sxs-lookup"><span data-stu-id="de66a-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="de66a-267">在 Kubernetes 中，如果不使用任何入口方法，那么服务和 Pod 的 IP 只能由群集网络路由。</span><span class="sxs-lookup"><span data-stu-id="de66a-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="de66a-268">但是，如果使用入口方法，则 Internet 和服务（包括 API 网关）间会有一个中间层，充当反向代理。</span><span class="sxs-lookup"><span data-stu-id="de66a-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="de66a-269">入口为规则的集合，允许入站连接到达群集服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="de66a-270">入口通常配置为提供外部可访问的 URL、负载均衡流量、SSL 终止等服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="de66a-271">用户通过将入口资源发布到 API 服务器来请求入口。</span><span class="sxs-lookup"><span data-stu-id="de66a-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="de66a-272">在 eShopOnContainers 中，在本地进行开发并仅使用开发计算机作为 Docker 主机时，不会使用任何入口，只使用多个 API 网关。</span><span class="sxs-lookup"><span data-stu-id="de66a-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="de66a-273">但是，当面向基于 Kubernetes 的“生产”环境时，eShopOnContainers 会在 API 网关前使用入口。</span><span class="sxs-lookup"><span data-stu-id="de66a-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="de66a-274">这样一来，客户端仍可调用相同基 URL，但请求会路由到多个 API 网关或 BFF。</span><span class="sxs-lookup"><span data-stu-id="de66a-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="de66a-275">API 网关只是呈现服务的前端或外观，Web 应用通常不在其呈现范围内。</span><span class="sxs-lookup"><span data-stu-id="de66a-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="de66a-276">此外，API 网关可能会隐藏某些内部微服务。</span><span class="sxs-lookup"><span data-stu-id="de66a-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="de66a-277">然而，入口只重定向 HTTP 请求，而不会试图隐藏任何微服务或 Web 应用。</span><span class="sxs-lookup"><span data-stu-id="de66a-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="de66a-278">在 Web 应用程序前的 Kubernetes 中加入入口 Nginx 层和几个 Ocelot API 网关/BFF 是理想的体系结构，如下图所示。</span><span class="sxs-lookup"><span data-stu-id="de66a-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![显示入口层如何适合 AKS 环境的图示。](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="de66a-280">图 6-41。</span><span class="sxs-lookup"><span data-stu-id="de66a-280">**Figure 6-41**.</span></span> <span data-ttu-id="de66a-281">部署到 Kubernetes 时 eShopOnContainers 中的入口层</span><span class="sxs-lookup"><span data-stu-id="de66a-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="de66a-282">Kubernetes 入口充当流向应用的所有流量的反向代理，包括通常在 Api 网关范围之外的 Web 应用程序。</span><span class="sxs-lookup"><span data-stu-id="de66a-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="de66a-283">将 eShopOnContainers 部署到 Kubernetes 时，它只通过入口公开一些服务或终结点，基本上是以下列出的 URL 上的后缀：</span><span class="sxs-lookup"><span data-stu-id="de66a-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="de66a-284">`/` 用于客户端 SPA Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="de66a-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="de66a-285">`/webmvc` 用于客户端 MVC Web 应用程序</span><span class="sxs-lookup"><span data-stu-id="de66a-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="de66a-286">`/webstatus` 用于显示 status/healthchecks 的客户端 Web 应用</span><span class="sxs-lookup"><span data-stu-id="de66a-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="de66a-287">`/webshoppingapigw` 用于 Web BFF 和购物业务流程</span><span class="sxs-lookup"><span data-stu-id="de66a-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="de66a-288">`/webmarketingapigw` 用于 Web BFF 和营销业务流程</span><span class="sxs-lookup"><span data-stu-id="de66a-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="de66a-289">`/mobileshoppingapigw` 用于移动 BFF 和购物业务流程</span><span class="sxs-lookup"><span data-stu-id="de66a-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="de66a-290">`/mobilemarketingapigw` 用于移动 BFF 和营销业务流程</span><span class="sxs-lookup"><span data-stu-id="de66a-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="de66a-291">部署到 Kubernetes 时，每个 Ocelot API 网关为运行 API 网关的每个 pod 使用不同的“configuration.json”文件。</span><span class="sxs-lookup"><span data-stu-id="de66a-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="de66a-292">这些“configuration.json”文件是通过装载（最初使用 deploy.ps1 脚本）卷提供的，该卷是基于名为“ocelot”的 Kubernetes 配置映射创建的。</span><span class="sxs-lookup"><span data-stu-id="de66a-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="de66a-293">每个容器将其相关配置文件装载到名为 `/app/configuration` 的容器文件夹中。</span><span class="sxs-lookup"><span data-stu-id="de66a-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="de66a-294">在 eShopOnContainers 的源代码文件中，可在 `k8s/ocelot/` 文件夹中找到原始的“configuration.json”文件。</span><span class="sxs-lookup"><span data-stu-id="de66a-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="de66a-295">每个 BFF/APIGateway 都有一个文件。</span><span class="sxs-lookup"><span data-stu-id="de66a-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="de66a-296">Ocelot API 网关中的其他横切功能</span><span class="sxs-lookup"><span data-stu-id="de66a-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="de66a-297">使用 Ocelot API 网关时，还有其他重要的功能等待你来研究和使用，如以下链接所述。</span><span class="sxs-lookup"><span data-stu-id="de66a-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="de66a-298">客户端中集成 Ocelot 与 Consul 或 Eureka 的服务发现 </span><span class="sxs-lookup"><span data-stu-id="de66a-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="de66a-299">API 网关层中的缓存 </span><span class="sxs-lookup"><span data-stu-id="de66a-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="de66a-300">API 网关层中的日志记录 </span><span class="sxs-lookup"><span data-stu-id="de66a-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="de66a-301">API 网关层中的服务质量（重试次数和断路器） </span><span class="sxs-lookup"><span data-stu-id="de66a-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="de66a-302">速率限制 </span><span class="sxs-lookup"><span data-stu-id="de66a-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="de66a-303">[上一页](background-tasks-with-ihostedservice.md)
> [下一页](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="de66a-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
