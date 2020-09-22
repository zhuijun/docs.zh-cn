---
title: 使用作为容器运行的数据库服务器
description: 了解使用仅作为开发容器运行的数据库服务器的重要性。 从不用于生产。
ms.date: 01/30/2020
ms.openlocfilehash: 38f77e195b184d57dcad5904674a0025ef6c2bd8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539394"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="007a4-104">使用作为容器运行的数据库服务器</span><span class="sxs-lookup"><span data-stu-id="007a4-104">Use a database server running as a container</span></span>

<span data-ttu-id="007a4-105">你可以将自己的数据库（SQL Server、PostgreSQL、MySQL 等）放在常规独立服务器、本地群集或云中的 PaaS 服务（如 Azure SQL DB）中。</span><span class="sxs-lookup"><span data-stu-id="007a4-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="007a4-106">但对于开发和测试环境来说，将数据库作为容器运行很方便，因为没有任何外部依赖项，只需运行 `docker-compose up` 命令，即可启动整个应用程序。</span><span class="sxs-lookup"><span data-stu-id="007a4-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="007a4-107">将这些数据库作为容器也有利于集成测试，因为数据库在容器中启动，并且始终填充相同的样本数据，因此预测测试也就更容易了。</span><span class="sxs-lookup"><span data-stu-id="007a4-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="007a4-108">SQL Server 作为包含微服务相关数据库的容器运行</span><span class="sxs-lookup"><span data-stu-id="007a4-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="007a4-109">在 eShopOnContainers 中，有一个名为 `sqldata` 的容器（如 [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) 文件中所定义），该容器运行 SQL Server for Linux 实例，包含需要该实例的所有微服务的 SQL Server 数据库。</span><span class="sxs-lookup"><span data-stu-id="007a4-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="007a4-110">微服务中的一个关键点是每个微服务都拥有其相关数据，因此它应该具有自己的数据库。</span><span class="sxs-lookup"><span data-stu-id="007a4-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="007a4-111">但是，数据库可以位于任何位置。</span><span class="sxs-lookup"><span data-stu-id="007a4-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="007a4-112">在这种情况下，它们都位于同一容器中，以尽可能降低 Docker 内存需求。</span><span class="sxs-lookup"><span data-stu-id="007a4-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="007a4-113">请记住，这对于开发和测试是一个很好的解决方案，但对于生产而言却不是。</span><span class="sxs-lookup"><span data-stu-id="007a4-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="007a4-114">示例应用程序中的 SQL Server 容器在 docker-compose.yml 文件中配置有下列 YAML 代码，这些代码在运行 `docker-compose up` 时执行。</span><span class="sxs-lookup"><span data-stu-id="007a4-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="007a4-115">请注意，YAML 代码整合了来自通用 docker-compose.yml 文件和 docker-compose.override.yml 文件的配置信息。</span><span class="sxs-lookup"><span data-stu-id="007a4-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="007a4-116">（你通常会分离环境设置与 SQL Server 映像的相关基本信息或静态信息。）</span><span class="sxs-lookup"><span data-stu-id="007a4-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="007a4-117">按照类似的方法，不使用 `docker-compose`，而使用下列 `docker run` 命令便可运行该容器：</span><span class="sxs-lookup"><span data-stu-id="007a4-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="007a4-118">但是，如果要部署多容器应用程序（如 eShopOnContainers），使用 `docker-compose up` 命令为应用程序部署所有必需的容器会更方便。</span><span class="sxs-lookup"><span data-stu-id="007a4-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="007a4-119">首次启动此 SQL Server 容器时，容器使用提供的密码初始化 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="007a4-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="007a4-120">SQL Server 作为容器运行后，可以通过连接任何常规 SQL 连接（例如 SQL Server Management Studio、Visual Studio 或 C\# 代码）来更新数据库。</span><span class="sxs-lookup"><span data-stu-id="007a4-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="007a4-121">eShopOnContainers 应用程序提供在启动时在数据库中设定数据，使用样本数据来初始化每个微服务数据库，如下文所述。</span><span class="sxs-lookup"><span data-stu-id="007a4-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="007a4-122">将 SQL Server 作为容器运行不仅可用于无法访问 SQL Server 实例的演示。</span><span class="sxs-lookup"><span data-stu-id="007a4-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="007a4-123">如前所述，对开发和测试环境也非常有用，因为可以通过设定新的样本数据轻松地从清晰的 SQL Server 映像以及已知数据开始运行集成测试。</span><span class="sxs-lookup"><span data-stu-id="007a4-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="007a4-124">其他资源</span><span class="sxs-lookup"><span data-stu-id="007a4-124">Additional resources</span></span>

- <span data-ttu-id="007a4-125">**Run the SQL Server Docker image on Linux, Mac, or Windows**（在 Linux、Mac 或 Windows 上运行 SQL Server Docker 映像） </span><span class="sxs-lookup"><span data-stu-id="007a4-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="007a4-126">**Connect and query SQL Server on Linux with sqlcmd**（使用 sqlcmd 连接和查询 Linux 上的 SQL Server） </span><span class="sxs-lookup"><span data-stu-id="007a4-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="007a4-127">在 Web 应用程序启动时设定测试数据</span><span class="sxs-lookup"><span data-stu-id="007a4-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="007a4-128">要在应用程序启动时向数据库添加数据，可以将以下代码添加到 Web API 项目 `Program` 类中的 `Main` 方法中：</span><span class="sxs-lookup"><span data-stu-id="007a4-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="007a4-129">在容器启动期间应用迁移并为数据库设定种子时，会出现一个重要警告。</span><span class="sxs-lookup"><span data-stu-id="007a4-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="007a4-130">由于数据库服务器可能因某种原因不可用，因此必须等待服务器可用时处理重试。</span><span class="sxs-lookup"><span data-stu-id="007a4-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="007a4-131">此重试逻辑由 `MigrateDbContext()` 扩展方法处理，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="007a4-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```csharp
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="007a4-132">自定义 CatalogContextSeed 类中的以下代码可填充数据。</span><span class="sxs-lookup"><span data-stu-id="007a4-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="007a4-133">运行集成测试时，可以生成与集成测试一致的数据很有用。</span><span class="sxs-lookup"><span data-stu-id="007a4-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="007a4-134">能够从头开始创建所有内容（包括在容器上运行的 SQL Server 实例）对测试环境非常有用。</span><span class="sxs-lookup"><span data-stu-id="007a4-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="007a4-135">EF Core InMemory 数据库与作为容器运行的 SQL Server</span><span class="sxs-lookup"><span data-stu-id="007a4-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="007a4-136">运行测试时，另一个不错的选择是使用 Entity Framework InMemory 数据库提供程序。</span><span class="sxs-lookup"><span data-stu-id="007a4-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="007a4-137">可以在 Web API 项目 Startup 类的 ConfigureServices 方法中指定该配置：</span><span class="sxs-lookup"><span data-stu-id="007a4-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }

    // Other Startup code ...
}
```

<span data-ttu-id="007a4-138">不过，存在一个重要的问题。</span><span class="sxs-lookup"><span data-stu-id="007a4-138">There is an important catch, though.</span></span> <span data-ttu-id="007a4-139">内存数据库不支持指定于特定数据库的许多约束。</span><span class="sxs-lookup"><span data-stu-id="007a4-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="007a4-140">例如，在 EF Core 模型的列中添加唯一索引，以及针对内存数据库编写测试，检查其是否允许添加重复值。</span><span class="sxs-lookup"><span data-stu-id="007a4-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="007a4-141">但是，使用内存数据库时，无法处理列上的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="007a4-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="007a4-142">因此，内存数据库与真正 SQL Server 数据库的工作方式不完全相同 - 前者不会模拟特定于数据库的约束。</span><span class="sxs-lookup"><span data-stu-id="007a4-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="007a4-143">即便如此，内存数据库仍然可用于测试和原型设计。</span><span class="sxs-lookup"><span data-stu-id="007a4-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="007a4-144">但如果想要创建考虑特定数据库实现行为的准确集成测试，则需要使用像 SQL Server 这样真正的数据库。</span><span class="sxs-lookup"><span data-stu-id="007a4-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="007a4-145">为此，在容器中运行 SQL Server 是一个不错的选择，它比 EF Core InMemory 数据库提供程序更准确。</span><span class="sxs-lookup"><span data-stu-id="007a4-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="007a4-146">使用在容器中运行的 Redis 缓存服务</span><span class="sxs-lookup"><span data-stu-id="007a4-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="007a4-147">可以在容器上运行 Redis，特别是用于开发和测试以及概念验证方案。</span><span class="sxs-lookup"><span data-stu-id="007a4-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="007a4-148">这种方案很方便，因为可以在容器上运行所有依赖项 - 不仅适用于本地开发机器，还适用于 CI/CD 管道中的环境测试。</span><span class="sxs-lookup"><span data-stu-id="007a4-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="007a4-149">但是，如果生产环境中运行 Redis，则最好是寻找像 Redis Microsoft Azure 这样的高可用性解决方案，该解决方案作为 PaaS（平台即服务）运行。</span><span class="sxs-lookup"><span data-stu-id="007a4-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="007a4-150">你只需在代码中更改连接字符串。</span><span class="sxs-lookup"><span data-stu-id="007a4-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="007a4-151">Redis 提供使用 Redis 的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="007a4-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="007a4-152">该映像可在 Docker 中心获得，请访问此 URL：</span><span class="sxs-lookup"><span data-stu-id="007a4-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="007a4-153">可在命令提示符中执行以下 Docker CLI 命令来直接运行 Docker Redis 容器：</span><span class="sxs-lookup"><span data-stu-id="007a4-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="007a4-154">Redis 映像包含公开：6379（Redis 使用的端口），因此链接容器可自动使用标准容器链接。</span><span class="sxs-lookup"><span data-stu-id="007a4-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="007a4-155">在 eShopOnContainers 中，`basket-api` 微服务使用作为容器运行的 Redis 缓存。</span><span class="sxs-lookup"><span data-stu-id="007a4-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="007a4-156">该 `basketdata` 容器被定义为 docker-compose.yml  文件的一部分，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="007a4-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="007a4-157">docker-compose.yml 中的此代码基于 redis 映像定义了一个名为 `basketdata` 的容器，并在内部发布端口 6379。</span><span class="sxs-lookup"><span data-stu-id="007a4-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="007a4-158">这意味着，只能从 Docker 主机中运行的其他容器访问它。</span><span class="sxs-lookup"><span data-stu-id="007a4-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="007a4-159">最后，在 docker-compose.override.yml  文件中，eShopOnContainers 示例的 `basket-api` 微服务定义了用于该 Redis 容器的连接字符串：</span><span class="sxs-lookup"><span data-stu-id="007a4-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="007a4-160">如前文所述，微服务的名称 `basketdata` 通过 Docker 的内部网络 DNS 进行解析。</span><span class="sxs-lookup"><span data-stu-id="007a4-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="007a4-161">[上一页](multi-container-applications-docker-compose.md)
>[下一页](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="007a4-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
