---
title: 创建简单的数据驱动 CRUD 微服务
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 了解如何在微服务应用程序的上下文中创建简单的 CRUD（数据驱动）微服务。
ms.date: 08/14/2020
ms.openlocfilehash: 46654b9e6283d913910b62621d056e034c18870e
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679144"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="2bdcc-103">创建简单的数据驱动 CRUD 微服务</span><span class="sxs-lookup"><span data-stu-id="2bdcc-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="2bdcc-104">本部分概述如何创建一个简单的微服务，用于对数据源执行创建、读取、更新和删除 (CRUD) 操作。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="2bdcc-105">设计简单的 CRUD 微服务</span><span class="sxs-lookup"><span data-stu-id="2bdcc-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="2bdcc-106">从设计的角度来看，这种类型的容器化微服务是非常简单的。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="2bdcc-107">这有可能是由于要解决的问题很简单，也可能是由于其实现只是一个概念证明。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![显示简单 CRUD 微服务内部设计模式的关系图。](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="2bdcc-109">图 6-4  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-109">**Figure 6-4**.</span></span> <span data-ttu-id="2bdcc-110">简单 CRUD 微服务的内部设计</span><span class="sxs-lookup"><span data-stu-id="2bdcc-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="2bdcc-111">这种由数据驱动的简单服务的一个例子是 eShopOnContainers 示例应用程序的目录微服务。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="2bdcc-112">此类型的服务在单个 ASP.NET Core Web API 项目中实现其全部功能，该项目包含用于其数据模型、业务逻辑和数据访问代码的类。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="2bdcc-113">它还将其相关数据存储在 SQL Server 上运行的数据库（作为另一个用于开发/测试的容器）中，但也可以存储在任何常规 SQL Server 主机上，如图 6-5 中所示。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![显示数据驱动/CRUD 微服务容器的关系图。](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="2bdcc-115">图 6-5  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-115">**Figure 6-5**.</span></span> <span data-ttu-id="2bdcc-116">简单的数据驱动 CRUD 微服务设计</span><span class="sxs-lookup"><span data-stu-id="2bdcc-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="2bdcc-117">上一个关系图显示了逻辑 Catalog 微服务包括其 Catalog 数据库，该数据库无论是否与其位于同一 Docker 主机均可。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="2bdcc-118">若该数据库位于同一 Docker 主机，可能更利于开发，但不利于生产。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="2bdcc-119">开发这种类型的服务时，只需要 [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) 和数据访问 API 或 ORM（如 [Entity Framework Core](https://docs.microsoft.com/ef/core/index)）。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="2bdcc-120">还可以通过 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) 自动生成 [Swagger](https://swagger.io/) 元数据，用于提供有关服务功能的说明，如下一部分中所述。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="2bdcc-121">请注意，在 Docker 容器中运行 SQL Server 这样的数据库服务器十分适用于开发环境，因为可以设置和运行全部所需的依赖关系，而无需在云中或本地预配数据库。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="2bdcc-122">这在运行集成测试时十分方便。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="2bdcc-123">但是对于生产环境，则不建议在容器中运行数据库服务器，因为这种方法通常无法实现高可用性。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="2bdcc-124">对于 Azure 中的生产环境，建议使用 Azure SQL 数据库或任何其他可提供高可用性和高扩展性的数据库技术。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="2bdcc-125">例如，对于 NoSQL 方法，可选择 CosmosDB。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="2bdcc-126">最后，通过编辑 Dockerfile 和 docker-compose.yml 元数据文件，可配置此容器的映像的创建方式—它使用哪种基映像，以及设计内部和外部名称及 TCP 端口等设置。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="2bdcc-127">使用 ASP.NET Core 实现简单 CRUD 微服务</span><span class="sxs-lookup"><span data-stu-id="2bdcc-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="2bdcc-128">要使用 .NET Core 和 Visual Studio 实现简单 CRUD 微服务，需先创建一个简单的 ASP.NET Core Web API 项目（在 .NET Core 上运行以便可在 Linux Docker 主机上运行），如图 6 6 所示。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![显示项目设置的 Visual studio 的屏幕截图。](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="2bdcc-130">图 6-6  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-130">**Figure 6-6**.</span></span> <span data-ttu-id="2bdcc-131">在 Visual Studio 2019 中创建 ASP.NET Core Web API 项目</span><span class="sxs-lookup"><span data-stu-id="2bdcc-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="2bdcc-132">要创建 ASP.NET Core Web API 项目，首先需选择 ASP.NET Core Web 应用程序，然后选择 API 类型。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="2bdcc-133">创建该项目之后，便可使用 Entity Framework API 或其他 API 实现 MVC 控制器，与任何其他 Web API 项目中的操作一样。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="2bdcc-134">在新的 Web API 项目中，可以看到该微服务中的唯一依赖关系在 ASP.NET Core 本身上。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="2bdcc-135">在内部，Microsoft.AspNetCore.All 依赖项内引用的是实体框架和许多其他 .NET Core NuGet 包，如图 6-7 所示  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![VS 显示 Catalog.Api 的 NuGet 依赖项的屏幕截图。](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="2bdcc-137">图 6-7  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-137">**Figure 6-7**.</span></span> <span data-ttu-id="2bdcc-138">简单 CRUD Web API 微服务中的依赖关系</span><span class="sxs-lookup"><span data-stu-id="2bdcc-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="2bdcc-139">API 项目包括对 Microsoft.AspNetCore.App NuGet 包的引用，其中包括对所有基本包的引用。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-139">The API project includes references to Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="2bdcc-140">它也可能包含其他一些包。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="2bdcc-141">使用 Entity Framework Core 实现 CRUD Web API 服务</span><span class="sxs-lookup"><span data-stu-id="2bdcc-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="2bdcc-142">Entity Framework (EF) Core 是轻量化、可扩展和跨平台版的常用 Entity Framework 数据访问技术。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="2bdcc-143">EF Core 是一种支持 .NET 开发人员使用 .NET 对象处理数据库的对象关系映射程序 (ORM)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="2bdcc-144">目录微服务使用 EF 和 SQL Server 提供程序，因为其数据库在具有 SQL Server for Linux Docker 映像的容器中运行。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="2bdcc-145">但也可将数据库部署到任何其他 SQL Server 中，如本地 Windows 或 Azure SQL DB。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="2bdcc-146">唯一需要更改的是 ASP.NET Web API 微服务中的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="2bdcc-147">数据模型</span><span class="sxs-lookup"><span data-stu-id="2bdcc-147">The data model</span></span>

<span data-ttu-id="2bdcc-148">使用 EF Core 时，数据访问是通过使用模型来执行的。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="2bdcc-149">模型由（域模型）实体类和表示与数据库的会话的派生上下文 (DbContext) 组成，用于查询和保存数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="2bdcc-150">可从现有数据库生成模型，手动编码模型使之与数据库相匹配，或采用代码优先方法（通过此方法可在模型随时间推移发生更改后轻松地对于数据库进行相应改进），使用 EF 迁移技术基于模型创建数据库。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations technique to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="2bdcc-151">对于目录微服务，已使用后一种方法。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-151">For the catalog microservice, the last approach has been used.</span></span> <span data-ttu-id="2bdcc-152">可在以下代码示例中看到 CatalogItem 实体类的示例，这是一个简单的普通旧 CLR 对象 ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) 实体类。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

<span data-ttu-id="2bdcc-153">还需要一个 DbContext 来表示与数据库的会话。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="2bdcc-154">对于目录微服务，CatalogContext 类派生自 DbContext 基类，如下例中所示：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

<span data-ttu-id="2bdcc-155">可具有更多 `DbContext` 实现。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="2bdcc-156">例如，在示例 Catalog.API 微服务中，还有一个名为 `CatalogContextSeed` 的 `DbContext`，它会在首次尝试访问数据库时自动填充示例数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="2bdcc-157">此方法对于演示数据以及自动化测试方案很有用。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="2bdcc-158">在 `DbContext` 中，使用 `OnModelCreating` 方法来自定义对象/数据库实体映射和其他[EF 扩展点](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="2bdcc-159">从 Web API 控制器查询数据</span><span class="sxs-lookup"><span data-stu-id="2bdcc-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="2bdcc-160">通常使用语言集成查询 (LINQ) 从数据库检索实体类的实例，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    }
    //...
}
```

##### <a name="saving-data"></a><span data-ttu-id="2bdcc-161">保存数据</span><span class="sxs-lookup"><span data-stu-id="2bdcc-161">Saving data</span></span>

<span data-ttu-id="2bdcc-162">使用实体类的实例在数据库中创建、删除和修改数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="2bdcc-163">可向 Web API 控制器添加代码，如以下硬编码示例（在此例中为模拟数据）所示。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="2bdcc-164">ASP.NET Core 和 Web API 控制器中的依赖注入</span><span class="sxs-lookup"><span data-stu-id="2bdcc-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="2bdcc-165">在 ASP.NET Core 中可非常方便地使用依赖关系注入 (DI)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="2bdcc-166">无需设置第三方控制反转 (IoC) 容器，但如果愿意，可将喜欢的 IoC 容器插入 ASP.NET Core 基础结构。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="2bdcc-167">在本例中，这意味着可通过控制器构造函数直接插入所需的 EF DBContext 或其他存储库。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="2bdcc-168">在前面提到的 `CatalogController` 类中，`CatalogContext`（继承自 `DbContext`）类型与 `CatalogController()` 构造函数中的其他必需对象一起注入。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-168">In the `CatalogController` class mentioned earlier, `CatalogContext` (which inherits from `DbContext`) type is injected along with the other required objects in the `CatalogController()` constructor.</span></span>

<span data-ttu-id="2bdcc-169">需在 Web API 项目中设置一个重要配置，即向服务的 IoC 容器注册 DbContext 类。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="2bdcc-170">通常在 `Startup` 类中执行此操作，方法是在 `ConfigureServices()` 方法中调用 `services.AddDbContext<CatalogContext>()` 方法，如以下简化的示例中所示  ：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<CatalogContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...
    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...
}
```

### <a name="additional-resources"></a><span data-ttu-id="2bdcc-171">其他资源</span><span class="sxs-lookup"><span data-stu-id="2bdcc-171">Additional resources</span></span>

- <span data-ttu-id="2bdcc-172">**查询数据** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="2bdcc-173">**保存数据** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="2bdcc-174">Docker 容器使用的数据库连接字符串和环境变量</span><span class="sxs-lookup"><span data-stu-id="2bdcc-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="2bdcc-175">可使用 ASP.NET Core 设置并向 settings.json 文件添加 ConnectionString 属性，如下例中所示：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

```json
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

<span data-ttu-id="2bdcc-176">Settings.json 文件中可为 ConnectionString 属性或任何其他属性设置默认值。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="2bdcc-177">但使用 Docker 时，这些属性会被 docker-compose.override.yml 文件中指定的环境变量的值替代。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="2bdcc-178">在 docker-compose.yml 或 docker-compose.override.yml 文件中，可初始化这些环境变量，以便 Docker 将其设置为 OS 环境变量，如以下 docker-compose.override.yml 文件中所示（本示例中连接字符串和其他行会换行，但在你自己的文件中不换行）。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

<span data-ttu-id="2bdcc-179">相较于项目或微服务级别的配置文件，解决方法级别的 docker-compose.yml 文件不仅更灵活，而且如果使用从部署工具（如 Azure DevOps Services Docker 部署任务）设置的值替换在 docker-compose 文件中声明的环境变量，使用该文件会更安全。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="2bdcc-180">最后，可使用配置 \["ConnectionString"\] 从代码中获取该值，如前面的代码示例中的 ConfigureServices 方法中所示。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="2bdcc-181">但对于生产环境，可能需要寻找其他方法来存储连接字符串等机密。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="2bdcc-182">使用 [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) 是管理应用程序机密的绝佳方式。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="2bdcc-183">Azure Key Vault 有助于存储和保护云应用程序和服务使用的加密密钥和机密。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="2bdcc-184">机密是指需严格控制的任何内容（如 API 密钥、连接字符串和密码等），而使用记录、设置过期日期和管理访问*等*均涵盖于严控范围内。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="2bdcc-185">Azure Key Vault 允许对应用程序机密的使用情况进行非常详尽地控制，无需让任何人知晓这些内容。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="2bdcc-186">甚至可轮换机密以增强安全性，且不会对开发或操作造成中断。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="2bdcc-187">必须在组织的 Active Directory 中注册应用程序，如此才可使用 Key Vault。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="2bdcc-188">有关更多详细信息，请查看 *Key Vault 概念文档*。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="2bdcc-189">在 ASP.NET Web API 中实现版本控制</span><span class="sxs-lookup"><span data-stu-id="2bdcc-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="2bdcc-190">随着业务需求的改变，可能会添加新的资源集，资源之间的关系可能会改变，资源中数据的结构也可能被修改。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="2bdcc-191">更新 Web API 以适应新要求是一个相对比较简单的过程，但必须考虑这些更改会为使用 Web API 的客户端应用程序带来怎样的影响。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="2bdcc-192">虽然设计和实现 Web API 的开发人员对该 API 具有完全控制，但对由远程运营的第三方组织所构建的客户端应用程序却不具有同等程度的控制。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third-party organizations operating remotely.</span></span>

<span data-ttu-id="2bdcc-193">通过版本控制，Web API 能够指示其公开的功能和资源。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="2bdcc-194">客户端应用程序然后便可向特定版本的功能或资源提交请求。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="2bdcc-195">有几种方法可用于实现版本控制：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="2bdcc-196">URI 版本管理</span><span class="sxs-lookup"><span data-stu-id="2bdcc-196">URI versioning</span></span>

- <span data-ttu-id="2bdcc-197">查询字符串版本控制</span><span class="sxs-lookup"><span data-stu-id="2bdcc-197">Query string versioning</span></span>

- <span data-ttu-id="2bdcc-198">标头版本控制</span><span class="sxs-lookup"><span data-stu-id="2bdcc-198">Header versioning</span></span>

<span data-ttu-id="2bdcc-199">查询字符串和 URI 版本控制实现起来最简单。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="2bdcc-200">标头版本控制是一个好方法。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-200">Header versioning is a good approach.</span></span> <span data-ttu-id="2bdcc-201">但标头版本控制不如 URI 版本控制简单明确。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-201">However, header versioning is not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="2bdcc-202">由于 URL 版本控制最简单明晰，eShopOnContainers 示例应用程序使用 URI 版本控制。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="2bdcc-203">使用 URI 版本控制时，如 eShopOnContainers 示例应用程序所示，每次修改 Web API 或更改资源的架构时，都需向每个资源的 URI 中添加版本号。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="2bdcc-204">现有 URI 应维持原有工作方式，返回符合架构的资源，该架构与请求的版本匹配。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="2bdcc-205">如下面的代码示例中所示，可通过在 Web API 控制器中使用 Route 属性来设置版本，让版本信息在 URI 中一目了然（在本例中为 v1）。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="2bdcc-206">此版本控制机制很简单，取决于将请求路由到相应终结点的服务器。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="2bdcc-207">但如果使用 REST，为实现更精密的版本控制和使用最佳方法，应使用超媒体并实现 [HATEOAS（将超文本用作应用状态的引擎）](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2bdcc-208">其他资源</span><span class="sxs-lookup"><span data-stu-id="2bdcc-208">Additional resources</span></span>

- <span data-ttu-id="2bdcc-209">**Scott Hanselman.ASP.NET Core RESTful Web API versioning made easy**（简化 ASP.NET Core RESTful Web API 版本控制） </span><span class="sxs-lookup"><span data-stu-id="2bdcc-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="2bdcc-210">**RESTful Web API 版本控制** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="2bdcc-211">**Roy Fielding。版本控制、超媒体和 REST** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="2bdcc-212">从 ASP.NET Core Web API 生成 Swagger 描述元数据</span><span class="sxs-lookup"><span data-stu-id="2bdcc-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="2bdcc-213">[Swagger](https://swagger.io/) 是一个常用开源框架，由包含大量工具的大型“生态系统”提供支持，可帮助设计、生成、存档和使用 RESTful API。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="2bdcc-214">它正逐渐变为 API 描述性元数据域的标准。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="2bdcc-215">应在所有类型的微服务中，无论是数据驱动的微服务还是多个高级域驱动微服务，包含 Swagger 描述性元数据（如下一部分中所述）。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in the following section).</span></span>

<span data-ttu-id="2bdcc-216">Swagger 的核心是 Swagger 规范，它是 JSON 或 YAML 文件中的 API 描述性元数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="2bdcc-217">该规范为 API 创建 RESTful 协定，并以人类和机器均可识别的格式详细描述其资源和操作，以简化开发、发现和集成。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="2bdcc-218">该规范是 OpenAPI 规范 (OAS) 的基础，开发于开放、透明和协作化的社区，旨在让 RESTful 接口定义的方式实现标准化。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="2bdcc-219">该规范在如何发现服务以及如何理解其功能方面对其结构进行定义。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="2bdcc-220">有关详细信息，包括 Web 编辑器以及 Spotify、Uber、Slack 和 Microsoft 等公司的 Swagger 规范的示例，请访问 Swagger 站点 (<https://swagger.io>)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="2bdcc-221">为何使用 Swagger？</span><span class="sxs-lookup"><span data-stu-id="2bdcc-221">Why use Swagger?</span></span>

<span data-ttu-id="2bdcc-222">为 API 生成 Swagger 元数据的主要原因如下。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="2bdcc-223">**为让其他产品能够自动使用和集成 API**。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="2bdcc-224">许多产品和[商业工具](https://swagger.io/commercial-tools/)以及许多[库和框架](https://swagger.io/open-source-integrations/)均支持 Swagger。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="2bdcc-225">Microsoft 具有高级产品和工具，可自动使用基于 Swagger 的 API，举例如下：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="2bdcc-226">[AutoRest](https://github.com/Azure/AutoRest)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="2bdcc-227">可自动生成用于调用 Swagger 的 .NET 客户端类。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="2bdcc-228">可通过 CLI 使用此工具，它也与 Visual Studio 集成以便能够通过 GUI 轻松使用。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="2bdcc-229">[Microsoft Flow](https://flow.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="2bdcc-230">可自动[使用 API 并将其集成](https://flow.microsoft.com/blog/integrating-custom-api/)到高级 Microsoft Flow 工作流，且无需具备编程技能。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="2bdcc-231">[Microsoft PowerApps](https://powerapps.microsoft.com/)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="2bdcc-232">可自动从通过 [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/) 生成的 [PowerApps 移动应用](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/)使用 API，且无需具备编程技能。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="2bdcc-233">[Azure 应用服务逻辑应用](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps)。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="2bdcc-234">可自动[使用 API 并将其集成到 Azure 应用服务逻辑应用](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api)，且无需具备编程技能。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="2bdcc-235">**能够自动生成 API 文档**。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="2bdcc-236">创建大规模 RESTful API 时，如基于微服务的复杂应用程序，需要处理大量终结点，同时请求和响应负载中会使用各种不同的数据模型。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="2bdcc-237">具备正确的文档和稳定可靠的 API 资源管理器（通过 Swagger 获取），是 API 成功发挥功能和开发人员成功使用它的关键所在。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="2bdcc-238">Microsoft Flow、PowerApps 和 Azure 逻辑应用通过使用 Swagger 的元数据来了解如何使用和连接 API。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="2bdcc-239">基于 *swagger-ui*，可通过多种方式以功能 API 帮助页面的形式自动生成针对 ASP.NET Core REST API 应用程序的 Swagger 元数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="2bdcc-240">或许，最常用的方式是当前 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 中使用的 [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore)，我们将在本指南中对此进行详细介绍，但除此以外，也可选择使用 [NSwag](https://github.com/RSuter/NSwag)，它可以生成 Typescript 和 C\# API 客户端，也可基于 Swagger 或 OpenAPI 规范生成 C\# 控制器，甚至可使用 [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio) 扫描包含这些控制器的 .dll 来生成控制器。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="2bdcc-241">如何使用 Swashbuckle NuGet 包自动生成 API Swagger 元数据</span><span class="sxs-lookup"><span data-stu-id="2bdcc-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="2bdcc-242">手动（在 JSON 或 YAML 文件中）生成 Swagger 元数据可能会耗时较长且较为枯燥。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="2bdcc-243">但可使用 [Swashbuckle NuGet 包](https://aka.ms/swashbuckledotnetcore)动态生成 Swagger API 元数据，让 ASP.NET Web API 服务自动发现 API。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="2bdcc-244">Swashbuckle 为 ASP.NET Web API 项目自动生成 Swagger 元数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="2bdcc-245">它支持 ASP.NET Core Web API 项目和传统 ASP.NET Web API 以及任何其他风格，如 Azure API 应用、Azure 移动应用和基于 ASP.NET 的 Azure Service Fabric 微服务等。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="2bdcc-246">它还支持容器上部署的普通 Web API，就像为引用应用程序提供支持那样。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="2bdcc-247">Swashbuckle 将 API 资源管理器和 Swagger 或 [swagger ui](https://github.com/swagger-api/swagger-ui) 结合起来，为 API 使用者提供更丰富的发现和文档体验。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="2bdcc-248">除 Swagger 元数据生成器引擎外，Swashbuckle 还包含 swagger-ui 的嵌入版本，可在安装 Swashbuckle 后自动提供。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="2bdcc-249">这意味除 API 外，又有了一个好用的发现 UI，可帮助开发人员使用 API。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="2bdcc-250">它只需要少量代码和维护，因为它自动生成，这让用户能够专注于生成 API。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="2bdcc-251">API 资源管理器的结果如图 6-8 所示。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![显示 eShopOContainers API 的 Swagger API 资源管理器的屏幕截图。](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="2bdcc-253">图 6-8  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-253">**Figure 6-8**.</span></span> <span data-ttu-id="2bdcc-254">基于 Swagger 元数据的 Swashbuckle API 资源管理器—eShopOnContainers 目录微服务</span><span class="sxs-lookup"><span data-stu-id="2bdcc-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="2bdcc-255">Swashbuckle 生成的 Swagger UI API 文档包括所有已发布操作。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="2bdcc-256">此处，API 资源管理器不是最重要的部分。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="2bdcc-257">一旦具有可在 Swagger 元数据中进行自我描述的 Web API 后，便可从基于 Swagger 的工具中无缝使用 API，这些工具包括可面向多个平台的客户端代理类代码生成器。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="2bdcc-258">例如，之前提到过，[AutoRest](https://github.com/Azure/AutoRest) 可自动生成 .NET 客户端类。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="2bdcc-259">同时还有 [swagger-codegen](https://github.com/swagger-api/swagger-codegen) 等其他工具可用，这些工具可用于自动生成 API 客户端库、服务器存根（stub）和文档的代码。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="2bdcc-260">目前，Swashbuckle 在用于 ASP.NET Core 应用程序的高级元包 [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) 下包含五个内部 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level metapackage [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="2bdcc-261">在 Web API 项目中安装这些 NuGet 包后，需在 Startup 类中配置 Swagger，如以下简化的  代码所示：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

<span data-ttu-id="2bdcc-262">完成此操作后，便可启动应用程序，并使用类似以下的 URL 浏览以下 Swagger JSON 和 UI 终结点：</span><span class="sxs-lookup"><span data-stu-id="2bdcc-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="2bdcc-263">之前已展示由 Swashbuckle 为类似于 `http://<your-root-url>/swagger` 的 URL 生成的 UI。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="2bdcc-264">图 6-9 中还展示了如何测试 API 方法。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![显示可用测试工具的 Swagger UI 的屏幕截图。](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="2bdcc-266">图 6-9  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-266">**Figure 6-9**.</span></span> <span data-ttu-id="2bdcc-267">Swashbuckle UI 测试目录/项目 API 方法</span><span class="sxs-lookup"><span data-stu-id="2bdcc-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="2bdcc-268">Swagger UI API 详细信息显示了一个响应示例，可用于执行真正的 API，这对于开发人员发现非常有用。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="2bdcc-269">图 6-10 显示了当使用 [Postman](https://www.getpostman.com/) 请求 `http://<your-root-url>/swagger/v1/swagger.json` 时，从 eShopOnContainers 微服务（工具在下方使用此微服务）中生成的 Swagger JSON 元数据。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![显示 Swagger JSON 元数据的示例 Postman UI 的屏幕截图。](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="2bdcc-271">图 6-10  。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-271">**Figure 6-10**.</span></span> <span data-ttu-id="2bdcc-272">Swagger JSON 元数据</span><span class="sxs-lookup"><span data-stu-id="2bdcc-272">Swagger JSON metadata</span></span>

<span data-ttu-id="2bdcc-273">就是这么简单。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-273">It is that simple.</span></span> <span data-ttu-id="2bdcc-274">由于是自动生成的，向 API 中添加更多功能后，Swagger 元数据会增长。</span><span class="sxs-lookup"><span data-stu-id="2bdcc-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2bdcc-275">其他资源</span><span class="sxs-lookup"><span data-stu-id="2bdcc-275">Additional resources</span></span>

- <span data-ttu-id="2bdcc-276">**使用 Swagger 的 ASP.NET Web API 帮助页** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="2bdcc-277">**Swashbuckle 和 ASP.NET Core 入门** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="2bdcc-278">**NSwag 和 ASP.NET Core 入门** </span><span class="sxs-lookup"><span data-stu-id="2bdcc-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="2bdcc-279">[上一页](microservice-application-design.md)
> [下一页](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="2bdcc-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
