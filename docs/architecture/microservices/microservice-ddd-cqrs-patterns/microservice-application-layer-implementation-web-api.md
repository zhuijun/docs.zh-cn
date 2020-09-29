---
title: 使用 Web API 实现微服务应用层
description: 了解依赖关系注入和转存进程模式及其在 Web API 应用层中的实现详细信息。
ms.date: 08/17/2020
ms.openlocfilehash: 56d4eecb2831a57460b01ff4da8150d6dcce5bc5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173414"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="cbf1c-103">使用 Web API 实现微服务应用层</span><span class="sxs-lookup"><span data-stu-id="cbf1c-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="cbf1c-104">使用依赖关系注入将基础结构对象注入到应用层中</span><span class="sxs-lookup"><span data-stu-id="cbf1c-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="cbf1c-105">如前所述，可以在要生成的项目（程序集）中实现应用层，例如在 Web API 项目或 MVC web 应用项目中。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="cbf1c-106">如果使用 ASP.NET Core 构建微服务，应用程序层通常是 Web API 库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="cbf1c-107">如果要从自定义应用程序层代码中分离来自 ASP.NET Core 的内容（其基础结构以及你的控制器），还可将应用程序层置于单独的类库，但这是可选操作。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="cbf1c-108">例如，订购微服务的应用层代码直接在 Ordering.API 项目（ASP.NET Core Web API 项目）中实现，如图 7-23 所示。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="解决方案资源管理器中 Ordering.API 微服务的屏幕截图。":::
<span data-ttu-id="cbf1c-110">Ordering.API 微服务的解决方案资源管理器视图，显示“应用程序”文件夹下的子文件夹：行为、命令、DomainEventHandler、IntegrationEvent、模型、查询和验证。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-110">The Solution Explorer view of the Ordering.API microservice, showing the subfolders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries, and Validations.</span></span>
:::image-end:::

<span data-ttu-id="cbf1c-111">**图 7-23**。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-111">**Figure 7-23**.</span></span> <span data-ttu-id="cbf1c-112">Ordering.API ASP.NET Core Web API 项目中的应用程序层</span><span class="sxs-lookup"><span data-stu-id="cbf1c-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="cbf1c-113">ASP.NET Core 包含一个简单的[内置 IoC 容器](/aspnet/core/fundamentals/dependency-injection)（表示为 接口），默认情况下，该容器支持构造函数注入，ASP.NET 可通过 DI 提供某些服务。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-113">ASP.NET Core includes a simple [built-in IoC container](/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="cbf1c-114">ASP.NET Core 使用“服务”这一术语来表示将通过 DI 注入的你注册的类型。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="cbf1c-115">可以在应用程序的 Startup 类中的 ConfigureServices 方法中配置内置容器的服务。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="cbf1c-116">依赖项会在类型需要以及在 IoC 容器中注册的服务中实现。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="cbf1c-117">通常需要注入实现基础结构对象的依赖项。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="cbf1c-118">一个要注入的典型的依赖项是存储库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-118">A typical dependency to inject is a repository.</span></span> <span data-ttu-id="cbf1c-119">但可注入任何其他你拥有的基础结构依赖项。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="cbf1c-120">对于较简单的实现，可直接注入 Unit of Work 模式对象（EF DbContext 对象），因为 DBContext 也是基础结构持久性对象的实现。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="cbf1c-121">在下面的示例中，可以看到 .NET 如何通过构造函数注入所需的存储库对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="cbf1c-122">此类是一个命令处理程序，我们将在下一部分中对其进行介绍。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-122">The class is a command handler, which will get covered in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}

```

<span data-ttu-id="cbf1c-123">类使用注入的存储库执行事务和保持状态更改。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="cbf1c-124">类是命令处理程序、ASP.NET Core Web API 控制器方法，还是 [DDD 应用程序服务](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)，这并不重要。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="cbf1c-125">它最终是一个简单类，该类使用存储库、域实体和其他应用程序协调，这与命令处理程序相似。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="cbf1c-126">依赖项注入的工作原理对于所有所述的类都是相同的，如基于构造函数使用 DI 的示例。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="cbf1c-127">注册依赖项实现类型和接口或抽象</span><span class="sxs-lookup"><span data-stu-id="cbf1c-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="cbf1c-128">使用通过构造函数注入的对象前，需要知道在何处注册接口和类，这些接口和类生成通过 DI 注入应用程序类的对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="cbf1c-129">（如基于构造函数的 DI，如前面所示。）</span><span class="sxs-lookup"><span data-stu-id="cbf1c-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="cbf1c-130">使用由 ASP.NET Core 提供的内置 IoC 容器</span><span class="sxs-lookup"><span data-stu-id="cbf1c-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="cbf1c-131">使用 ASP.NET Core 提供的内置 IoC 容器时，在 Startup.cs 文件中注册要注入ConfigureServices 方法的类型，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="cbf1c-132">在 IoC 容器中注册类型时最常用的模式是注册一对类型 - 一个接口及其相关实现类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="cbf1c-133">当通过任何构造函数请求 IoC 容器中的对象时，请求特定接口类型的对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="cbf1c-134">例如，在前面的示例中，最后一行说明当构造函数具有 IMyCustomRepository（接口或抽象）依赖项时，IoC 容器将注入 MyCustomSQLServerRepository 实现类的实例。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="cbf1c-135">将 Scrutor 库用于自动类型注册</span><span class="sxs-lookup"><span data-stu-id="cbf1c-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="cbf1c-136">在 .NET Core 中使用 DI 时，可能需要扫描程序集，并自动按约定注册其类型。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="cbf1c-137">当前 ASP.NET Core 中未提供此功能。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="cbf1c-138">但是，可以使用 [Scrutor](https://github.com/khellang/Scrutor) 库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="cbf1c-139">如果需要在 IoC 容器中注册许多类型，使用该方法很方便。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cbf1c-140">其他资源</span><span class="sxs-lookup"><span data-stu-id="cbf1c-140">Additional resources</span></span>

- <span data-ttu-id="cbf1c-141">**Matthew King。向 Scrutor 注册服务** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="cbf1c-142">**Kristian Hellang。Scrutor。**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="cbf1c-143">GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="cbf1c-144">使用 Autofac 作为 IoC 容器</span><span class="sxs-lookup"><span data-stu-id="cbf1c-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="cbf1c-145">还可使用其他 IoC 容器，并将其插入 ASP.NET Core 管道，就像 eShopOnContainers（使用 [Autofac](https://autofac.org/)）中的订购微服务一样。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="cbf1c-146">使用 Autofac 时通常通过模块注册类型，这可根据类型位置，在多个文件之间拆分注册类型，就像可在多个类库中分布应用程序类型一样。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="cbf1c-147">例如，下面是 [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) 项目的 [Autofac 应用程序模块](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs)，包含要注入的类型。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="cbf1c-148">Autofac 还具有用于[按名称约定扫描程序集和注册类型](https://autofac.readthedocs.io/en/latest/register/scanning.html)的功能。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="cbf1c-149">注册过程和概念类似于向内置 ASP.NET Core IoC 容器注册类型，但使用 Autofac 时，语法略有不同。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="cbf1c-150">在示例代码中，抽象 IOrderRepository 与实现类 OrderRepository 一同注册。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="cbf1c-151">这意味着每当构造函数通过 IOrderRepository 抽象或接口声明依赖项时，IoC 容器会注入 OrderRepository 类的实例。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="cbf1c-152">实例作用域类型确定实例在相同服务或依赖项的请求之间的共享方式。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="cbf1c-153">发出依赖项请求时，IoC 容器会返回以下项：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="cbf1c-154">每个生存期范围的一个实例（在 ASP.NET Core IoC 容器中称为“已设置范围”）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="cbf1c-155">每个依赖项的一个实例（在 ASP.NET Core IoC 容器中称为“暂时”）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="cbf1c-156">使用 IoC 容器的跨所有对象共享的一个实例（在 ASP.NET Core IoC 容器中称为“单一实例”）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cbf1c-157">其他资源</span><span class="sxs-lookup"><span data-stu-id="cbf1c-157">Additional resources</span></span>

- <span data-ttu-id="cbf1c-158">**ASP.NET Core 中的依赖关系注入简介** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="cbf1c-159">**Autofac。**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-159">**Autofac.**</span></span> <span data-ttu-id="cbf1c-160">官方文档。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="cbf1c-161">**比较 ASP.NET Core IoC 容器服务生存期和 Autofac IoC 容器实例作用域 - Cesar de la Torre。**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="cbf1c-162">实现命令和命令处理程序模式</span><span class="sxs-lookup"><span data-stu-id="cbf1c-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="cbf1c-163">在上一部分中的“DI 通过构造函数”示例中，IoC 容器通过类中的构造函数注入存储库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="cbf1c-164">但是，它们究竟是在哪里注入的？</span><span class="sxs-lookup"><span data-stu-id="cbf1c-164">But exactly where were they injected?</span></span> <span data-ttu-id="cbf1c-165">在简单的 Web API（例如 eShopOnContainers 中的目录微服务）中，它们在控制器构造函数的 MVC 控制器级别注入（作为 ASP.NET Core 请求管道的一部分）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers' level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="cbf1c-166">但是，在本部分的初始代码（eShopOnContainers 中来自 Ordering.API 服务的 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 类）中，依赖项注入通过特定命令处理程序的构造函数完成。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="cbf1c-167">让我们来了解一下什么是命令处理程序，以及使用它的好处。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="cbf1c-168">命令模式在本质上与本指南之前介绍的 CQRS 模式相关。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="cbf1c-169">CQRS 具有两个功能。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-169">CQRS has two sides.</span></span> <span data-ttu-id="cbf1c-170">第一个功能是查询，通过 [Dapper](https://github.com/StackExchange/dapper-dot-net) 微 ORM 使用简化的查询，我们已经在前文中介绍过了。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="cbf1c-171">第二个功能是命令（这是事务的起点），以及服务外的输入通道。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="cbf1c-172">如图 7-24 所示，该模式基于接受客户端的命令、根据域模式规则进行处理，最后保持事务状态。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client-side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![显示从客户端到数据库的高级别数据流的关系图。](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="cbf1c-174">**图 7-24**。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-174">**Figure 7-24**.</span></span> <span data-ttu-id="cbf1c-175">CQRS 模式中的命令高级别视图或“事务端”</span><span class="sxs-lookup"><span data-stu-id="cbf1c-175">High-level view of the commands or "transactional side" in a CQRS pattern</span></span>

<span data-ttu-id="cbf1c-176">图 7-24 显示 UI 应用通过 API 向 `CommandHandler` 发送命令以更新数据库，此命令取决于域模型和基础结构。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="cbf1c-177">命令类</span><span class="sxs-lookup"><span data-stu-id="cbf1c-177">The command class</span></span>

<span data-ttu-id="cbf1c-178">命令是让系统执行更改系统状态的操作的请求。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="cbf1c-179">命令具有命令性，且应仅处理一次。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="cbf1c-180">由于命令具有命令性，所以通常采用命令语气使用谓词（如“create”或“update”）命名，命令可能包括聚合类型，例如 CreateOrderCommand。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="cbf1c-181">与事件不同，命令不是过去发生的事实，它只是一个请求，因此可以拒绝它。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="cbf1c-182">命令可能源自 UI，由用户发出请求而产生，也可能来自进程管理器，由进程管理器指导聚合执行操作而产生。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="cbf1c-183">命令的一个重要特征是它应该由单一接收方处理，且仅处理一次。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="cbf1c-184">这是因为命令是要在应用程序中执行的单个操作或事务。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="cbf1c-185">例如，同一个订单创建命令的处理次数不应超过一次。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="cbf1c-186">这是命令和事件之间的一个重要区别。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="cbf1c-187">事件可能会经过多次处理，因为许多系统或微服务可能会对该事件感兴趣。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="cbf1c-188">此外，请注意，如果命令不是幂等，命令仅会处理一次。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="cbf1c-189">如果命令可执行多次且结果不变（由于命令的本质或系统处理命令的方式），则命令是幂等。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="cbf1c-190">建议将命令和更新设置为幂等，如果在域的业务规则和固定协定下有意义。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain's business rules and invariants.</span></span> <span data-ttu-id="cbf1c-191">例如，我们使用同一个示例，如果出于任何原因（重试逻辑、黑客攻击等），相同的 CreateOrder 命令多次到达系统，应能识别并确保不会创建多个订单。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="cbf1c-192">为此，需要在操作中附加一些类型的标识，确定是否已处理命令或更新。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="cbf1c-193">可将命令发送给单个接收方，但不会发布命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="cbf1c-194">发布适用于声明事实的事件 - 事件已发生，事件接收方可能对其感兴趣。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="cbf1c-195">对于事件，发布服务器无需在意哪些接收方获取事件或对其进行什么操作。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="cbf1c-196">但域或集成事件是一个例外，前面章节已有介绍。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="cbf1c-197">命令通过包含数据字段或集合（其中包含执行命令所需的所有信息）的类实现。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="cbf1c-198">命令是一种特殊的数据传输对象 (DTO)，专门用于请求更改或事务。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="cbf1c-199">命令本身完全基于处理命令所需的信息，别无其他。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="cbf1c-200">下面的示例显示了简化的 `CreateOrderCommand` 类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="cbf1c-201">这是 eShopOnContainers 的订购微服务中使用的不可变命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment: Note that it is recommended to implement immutable Commands
// In this case, its immutability is achieved by having all the setters as private
// plus only being able to update the data just once, when creating the object through its constructor.
// References on Immutable Commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties

[DataContract]
public class CreateOrderCommand
    : IRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string UserId { get; private set; }

    [DataMember]
    public string UserName { get; private set; }

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string userId, string userName, string city, string street, string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = basketItems.ToOrderItemsDTO().ToList();
        UserId = userId;
        UserName = userName;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }


    public class OrderItemDTO
    {
        public int ProductId { get; set; }

        public string ProductName { get; set; }

        public decimal UnitPrice { get; set; }

        public decimal Discount { get; set; }

        public int Units { get; set; }

        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="cbf1c-202">基本上，命令类包含通过使用域模型对象执行业务事务所需的所有数据。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="cbf1c-203">因此，命令是包含只读数据、不包含行为的数据结构。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="cbf1c-204">命令的名称指示其用途。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-204">The command's name indicates its purpose.</span></span> <span data-ttu-id="cbf1c-205">在 C# 等许多语言中，命令表示为类，但它们不是真正的面向对象意义上的真的类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="cbf1c-206">命令的另一个特征是不变性，因为它们的预期用途是由域模型直接处理。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="cbf1c-207">它们不需要在预计的生存期内更改。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="cbf1c-208">在 C# 类中，可通过不使用任何可更改内部状态的资源库或其他方法，实现不变性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-208">In a C# class, immutability can be achieved by not having any setters or other methods that change the internal state.</span></span>

<span data-ttu-id="cbf1c-209">请记住，如果打算或希望命令经过序列化/反序列化过程，则这些属性必须具有一个专用资源库和 `[DataMember]`（或 `[JsonProperty]`）属性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-209">Keep in mind that if you intend or expect commands to go through a serializing/deserializing process, the properties must have a private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute.</span></span> <span data-ttu-id="cbf1c-210">否则，反序列化程序将无法使用所需的值在目标上重建对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-210">Otherwise, the deserializer won't be able to reconstruct the object at the destination with the required values.</span></span> <span data-ttu-id="cbf1c-211">如果该类的构造函数带有所有属性的参数，并且使用通常的 camelCase 命名约定，并且可以将该构造函数注释为 `[JsonConstructor]`，则也可以使用真正的只读属性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-211">You can also use truly read-only properties if the class has a constructor with parameters for all properties, with the usual camelCase naming convention, and annotate the constructor as `[JsonConstructor]`.</span></span> <span data-ttu-id="cbf1c-212">但是，此选项需要更多代码。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-212">However, this option requires more code.</span></span>

<span data-ttu-id="cbf1c-213">例如，用于创建订单的命令类可能与你要创建的订单在数据上类似，但你可能不需要相同的属性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-213">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="cbf1c-214">例如，`CreateOrderCommand` 命令没有订单 ID，因为订单尚未创建。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-214">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="cbf1c-215">许多命令类可能很简单，只需要一些有关需要更改的状态的字段。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-215">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="cbf1c-216">如果只需要使用类似以下的命令将订单状态从“处理中”更改为“已付款”或“已发货”，则是这种情况：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-216">That would be the case if you are just changing the status of an order from "in process" to "paid" or "shipped" by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="cbf1c-217">一些开发人员将其 UI 请求对象从命令 DTO 中分离，但这只是一种个人偏好。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-217">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="cbf1c-218">这种分离既枯燥又没有太大价值，对象几乎都是相同的形状。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-218">It is a tedious separation with not much additional value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="cbf1c-219">例如，在 eShopOnContainers 中，一些命令直接来自客户端。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-219">For instance, in eShopOnContainers, some commands come directly from the client-side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="cbf1c-220">命令处理程序类</span><span class="sxs-lookup"><span data-stu-id="cbf1c-220">The Command handler class</span></span>

<span data-ttu-id="cbf1c-221">应为每个命令实现特定命令处理程序类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-221">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="cbf1c-222">这是该模式的工作原理，是应用命令对象、域对象和基础结构存储库对象的情景。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-222">That is how the pattern works, and it's where you'll use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="cbf1c-223">对于 CQRS 和 DDD ，命令处理程序实际上是应用程序层的核心。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-223">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="cbf1c-224">但是，域类中应包含所有域逻辑 - 在聚合根（根实体）、子实体或[域服务](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/)中，但不在命令处理程序中（命令处理程序是应用程序层中的类）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-224">However, all the domain logic should be contained in the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="cbf1c-225">命令处理程序类为上一节提到的单一责任原则 (SRP) 的实现方式提供了强大的基石。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-225">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="cbf1c-226">命令处理程序收到命令，并从使用的聚合获取结果。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-226">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="cbf1c-227">结果应为成功执行命令，或者异常。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-227">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="cbf1c-228">出现异常时，系统状态应保持不变。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-228">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="cbf1c-229">命令处理程序通常执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-229">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="cbf1c-230">它接收 DTO 等命令对象（从[转存进程](https://en.wikipedia.org/wiki/Mediator_pattern)或其他基础结构对象）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-230">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="cbf1c-231">它会验证命令是否有效（如果转存进程未验证）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-231">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="cbf1c-232">它会实例化作为当前命令目标的聚合根实例。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-232">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="cbf1c-233">它会在聚合根实例上执行方法，从命令获得所需数据。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-233">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="cbf1c-234">它将聚合的新状态保持到相关数据库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-234">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="cbf1c-235">这最后一个操作是实际的事务。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-235">This last operation is the actual transaction.</span></span>

<span data-ttu-id="cbf1c-236">通常情况下，命令处理程序处理由聚合根（根实体）驱动的单个聚合。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-236">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="cbf1c-237">如果多个聚合应受到单个命令接收的影响，可使用域事件跨多个聚合传播状态或操作。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-237">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="cbf1c-238">请注意，处理命令时，所有域逻辑应在域模型（聚合）内，完全封装并准备好进行单元测试。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-238">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="cbf1c-239">命令处理程序的作用是从数据库获取域模型，最后指示基础结构层（存储库）在模型更改完成后保存更改。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-239">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="cbf1c-240">此方法的优点是，你可在独立的、完全封装的、丰富行为域模型中重构域逻辑，无需在应用程序或基础结构层中更改代码，命令处理程序、Web API、存储库等是管道级别。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-240">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="cbf1c-241">如果命令处理程序很复杂，包含过多逻辑，则可能存在代码异味。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-241">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="cbf1c-242">请查看它们，如果发现域逻辑，则重构代码，将域行为移动到域对象（聚合根和子实体）的方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-242">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="cbf1c-243">作为命令处理程序类的示例，下面的代码演示本章开头介绍的同一个 `CreateOrderCommandHandler` 类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-243">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="cbf1c-244">这个示例还强调了 Handle 方法以及域模型对象/聚合的操作。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-244">In this case, it also highlights the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}
```

<span data-ttu-id="cbf1c-245">以下是命令处理程序应执行的附加步骤：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-245">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="cbf1c-246">使用命令数据对聚合根的方法和行为进行操作。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-246">Use the command's data to operate with the aggregate root's methods and behavior.</span></span>

- <span data-ttu-id="cbf1c-247">在域对象中，执行事务时引发域事件，但这从命令处理程序角度看是透明的。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-247">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="cbf1c-248">如果聚合操作结果成功且在完成事务后，引发集成事件。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-248">If the aggregate's operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="cbf1c-249">（可能还会由存储库等基础结构类引发。）</span><span class="sxs-lookup"><span data-stu-id="cbf1c-249">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cbf1c-250">其他资源</span><span class="sxs-lookup"><span data-stu-id="cbf1c-250">Additional resources</span></span>

- <span data-ttu-id="cbf1c-251">**Mark Seemann。在边界上，应用程序不是面向对象的** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-251">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="cbf1c-252">**命令和事件** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-252">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="cbf1c-253">**命令处理程序有什么用途？**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-253">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="cbf1c-254">**Jimmy Bogard。域命令模式 - 处理程序** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-254">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="cbf1c-255">**Jimmy Bogard。域命令模式 - 验证** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-255">**Jimmy Bogard. Domain Command Patterns – Validation** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="cbf1c-256">命令处理管道：如何触发命令处理程序</span><span class="sxs-lookup"><span data-stu-id="cbf1c-256">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="cbf1c-257">下一个问题是如何调用命令处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-257">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="cbf1c-258">可从每个相关的 ASP.NET Core 控制器手动调用。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-258">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="cbf1c-259">但是，此方法过于耦合，并不理想。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-259">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="cbf1c-260">建议的其他两个主要选项是：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-260">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="cbf1c-261">通过内存中转存进程模式项目。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-261">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="cbf1c-262">在控制器和处理程序之间使用异步消息队列。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-262">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="cbf1c-263">在命令管道中使用转存进程模式（内存中）</span><span class="sxs-lookup"><span data-stu-id="cbf1c-263">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="cbf1c-264">如图 7-25 所示，在 CQRS 方法中使用类似于内存中总线的智能转存进程，该进程非常智能，可基于要接收的命令或 DTO 的类型重定向到正确的命令处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-264">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="cbf1c-265">组件之间的黑色箭头表示对象（许多情况下，通过 DI 注入）之间的依赖关系及其相关交互。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-265">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![显示从客户端到数据库的详细数据流的关系图。](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="cbf1c-267">**图 7-25**。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-267">**Figure 7-25**.</span></span> <span data-ttu-id="cbf1c-268">在单个 CQRS 微服务进程中使用转存进程模式</span><span class="sxs-lookup"><span data-stu-id="cbf1c-268">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="cbf1c-269">上图显示了图 7-24 的放大图：ASP.NET Core 控制器将命令发送到 MediatR 的命令管道，使它们到达相应的处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-269">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="cbf1c-270">使用转存进程模式的原因是对于企业应用程序，处理请求可能很复杂。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-270">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="cbf1c-271">你需要添加具有开放数量的整合问题，例如登录、验证、审核和安全性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-271">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="cbf1c-272">在这些情况下，可以依赖转存进程管道（请参阅[转存进程模式](https://en.wikipedia.org/wiki/Mediator_pattern)），以提供应对这些额外行为或整合问题的方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-272">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="cbf1c-273">转存进程是封装此进程方式的对象。它基于状态、命令处理程序调用方式或提供给处理程序的负载，协调执行。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-273">A mediator is an object that encapsulates the "how" of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="cbf1c-274">借助转存进程组件，可通过应用修饰器（或[管道行为](https://github.com/jbogard/MediatR/wiki/Behaviors)从 [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) 开始），采用集中且透明的方式，应用整合问题。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-274">With a mediator component, you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="cbf1c-275">有关更多信息，请参见[修饰器模式](https://en.wikipedia.org/wiki/Decorator_pattern)。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-275">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="cbf1c-276">修饰器和行为类似于[面向方面编程 (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)，仅应用于由转存进程组件管理的特定进程管道。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-276">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="cbf1c-277">AOP 中实现整合问题的方面基于编译时注入的 aspect weaver 或基于对象调用截获应用。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-277">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="cbf1c-278">这两种典型 AOP 方法的工作方式有时“就像是魔术”，因为不容易了解 AOP 的工作方式。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-278">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="cbf1c-279">处理严重问题或 bug 时，AOP 可能难以调试。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-279">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="cbf1c-280">另一方面，这些修饰器/行为是显式的，且仅在转存进程的上下文中应用，因此调试更可预测、更轻松。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-280">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="cbf1c-281">例如，在 eShopOnContainers 订购微服务中，实现了两个示例行为：一个 [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 类和一个 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-281">For example, in the eShopOnContainers ordering microservice, has an implementation of two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="cbf1c-282">下一节通过演示 eShopOnContainers 如何使用 [MediatR](https://www.nuget.org/packages/MediatR) [行为](https://github.com/jbogard/MediatR/wiki/Behaviors)介绍了行为的实现。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-282">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR](https://www.nuget.org/packages/MediatR) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="cbf1c-283">在命令的管道中使用消息队列（进程外）</span><span class="sxs-lookup"><span data-stu-id="cbf1c-283">Use message queues (out-of-proc) in the command's pipeline</span></span>

<span data-ttu-id="cbf1c-284">另一种选择是使用基于中转站或消息队列的异步消息，如图 7-26 所示。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-284">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="cbf1c-285">可在命令处理程序前，将此选项与转存进程组件合并。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-285">That option could also be combined with the mediator component right before the command handler.</span></span>

![使用 HA 消息队列显示数据流的关系图。](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="cbf1c-287">**图 7-26**。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-287">**Figure 7-26**.</span></span> <span data-ttu-id="cbf1c-288">通过 CQRS 命令使用消息队列（进程外和进程间通信）</span><span class="sxs-lookup"><span data-stu-id="cbf1c-288">Using message queues (out of the process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="cbf1c-289">还可以通过高可用性消息队列处理命令的管道，以将命令传递到相应的处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-289">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="cbf1c-290">使用消息队列接受命令可能会进一步复杂化命令管道，因为很可能需要将管道拆分为通过外部消息队列连接的两个进程。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-290">Using message queues to accept the commands can further complicate your command's pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="cbf1c-291">如果需要基于异步消息传送，提高可伸缩性和性能，则仍应使用此方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-291">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="cbf1c-292">请思考图 7-26 的情况，控制器将命令消息发布到队列，然后返回。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-292">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="cbf1c-293">然后命令处理程序按自己的步调处理消息。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-293">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="cbf1c-294">这是队列的一大优点：消息队列可在需要超高可伸缩性时（例如股票或具有大量传入数据的任何其他方案）充当缓冲区。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-294">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="cbf1c-295">但是，由于消息队列具有异步性质，你需要了解如何与客户端应用程序就命令进程的成功或失败进行通信。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-295">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command's process.</span></span> <span data-ttu-id="cbf1c-296">一般来说，应永远不要使用“发后不理”命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-296">As a rule, you should never use "fire and forget" commands.</span></span> <span data-ttu-id="cbf1c-297">每个业务应用程序需要了解命令是否处理成功，或至少了解是否已验证和接受。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-297">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="cbf1c-298">因此，相较于运行事务后返回操作结果的进程内命令进程，如果要在验证提交到异步队列的命令消息后响应客户端，这会增加系统复杂性。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-298">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation's result after running the transaction.</span></span> <span data-ttu-id="cbf1c-299">使用队列时，可能需要通过其他操作结果消息返回命令进程结果，这将需要在系统中使用其他组件和自定义通信。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-299">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="cbf1c-300">此外，异步命令是单向命令，这在许多情况下可能不是必要的，如下文中 Burtsev Alexey 和 Greg Young 之间有趣的[在线对话](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ)中所介绍的：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-300">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="cbf1c-301">\[Burtsev Alexey\] 我发现有人在许多代码中使用异步命令处理或单向命令消息传送，但这样做是不合理的（他们并没有执行长操作或外部异步代码，他们甚至没有跨应用程序边界使用消息总线）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-301">\[Burtsev Alexey\] I find lots of code where people use async command handling or one-way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross-application boundary to be using message bus).</span></span> <span data-ttu-id="cbf1c-302">他们为什么要引入不必要的复杂性？</span><span class="sxs-lookup"><span data-stu-id="cbf1c-302">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="cbf1c-303">实际上我至今没有看到过使用阻止命令处理程序的 CQRS 代码示例，但是它在大多数情况下是有效的。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-303">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="cbf1c-304">\[Greg Young\] \[...\] 异步命令并不存在；它实际上是另一种事件。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-304">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="cbf1c-305">如果我必须接受你发送给我的信息并在我不同意时引发事件，则这不再是你告诉我执行某个操作（\[即，这不是命令\]）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-305">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it's not a command\].</span></span> <span data-ttu-id="cbf1c-306">这是你告诉我一些操作已完成。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-306">It's you telling me something has been done.</span></span> <span data-ttu-id="cbf1c-307">虽然最初似乎只有细微差异，但会产生多方面影响。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-307">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="cbf1c-308">异步命令会极大地增加系统的复杂性，因为没有指示失败的简单方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-308">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="cbf1c-309">因此，除非需要缩放要求或在特殊情况下需要通过消息传达内部微服务，否则不建议使用异步命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-309">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="cbf1c-310">在这些情况下，必须设计针对失败的单独报告和恢复系统。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-310">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="cbf1c-311">在 eShopOnContainers 的初始版本中，我们决定使用同步命令处理，从 HTTP 请求启动，由转存进程模式驱动。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-311">In the initial version of eShopOnContainers, it was decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="cbf1c-312">这样一来，可轻松地返回进程的成功或失败，如 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/netcore1.1/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) 实现中一样。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-312">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/netcore1.1/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="cbf1c-313">在任何情况下，这应该是基于你的应用程序或微服务的业务要求的决定。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-313">In any case, this should be a decision based on your application's or microservice's business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="cbf1c-314">通过转存进程模式 (MediatR) 实现命令进程管道</span><span class="sxs-lookup"><span data-stu-id="cbf1c-314">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="cbf1c-315">作为示例实现，本指南建议基于转存进程模式使用进程内管道，驱动命令引入和路由命令（内存中）到正确的命令处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-315">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="cbf1c-316">本指南还建议应用[行为](https://github.com/jbogard/MediatR/wiki/Behaviors)以分隔整合问题。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-316">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="cbf1c-317">有关 .NET Core 中的实现，可使用多个开发源代码库来实现转存进程模式。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-317">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="cbf1c-318">本指南中使用的库是 [MediatR](https://github.com/jbogard/MediatR) 开放源代码库（由 Jimmy Bogard 创建），但也可使用其他方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-318">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="cbf1c-319">MediatR 是一个小型的简单库，可处理命令等内存中消息，同时应用修饰器或行为。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-319">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="cbf1c-320">使用转存进程模式有助于减小耦合度，并隔离请求工作的问题，同时自动连接到执行该工作的处理程序（在此情况下为命令处理程序）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-320">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="cbf1c-321">本指南中 Jimmy Bogard 介绍了使用转存进程模式的另一个好处：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-321">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="cbf1c-322">我认为在这里值得提一下测试，它提供了针对系统行为的良好一致窗口。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-322">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="cbf1c-323">请求传入，响应传出。我们发现这对生成行为一致的测试很有用。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-323">Request-in, response-out. We've found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="cbf1c-324">首先，让我们看一下示例 WebAPI 控制器，你会在其中使用转存进程对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-324">First, let's look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="cbf1c-325">如果你没有使用转存进程对象，则需要为此控制器注入所有依赖项，例如记录器对象等。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-325">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="cbf1c-326">因此，构造函数可能很复杂。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-326">Therefore, the constructor would be complicated.</span></span> <span data-ttu-id="cbf1c-327">但是，如果你使用转存进程对象，控制器的构造函数可以简单很多，只需几个依赖项而不是许多依赖项（如果你针对每个整合操作使用一个依赖项），如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-327">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

<span data-ttu-id="cbf1c-328">你会发现转存进程可提供简洁、精益的 Web API 控制器构造函数。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-328">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="cbf1c-329">此外，在控制器方法中，将命令发送到转存进程对象的代码几乎只有一行：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-329">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="cbf1c-330">实现幂等命令</span><span class="sxs-lookup"><span data-stu-id="cbf1c-330">Implement idempotent Commands</span></span>

<span data-ttu-id="cbf1c-331">在 eShopOnContainers 中，比上述更高级的示例是从订购微服务提交 CreateOrderCommand 对象。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-331">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="cbf1c-332">但由于订购业务进程有点复杂，所以在我们的示例中，其实是从购物篮微服务开始，提交 CreateOrderCommand 对象的操作从名为 [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) 的集成事件处理程序（而不是从客户端应用调用的简单 WebAPI 控制器，如之前较简单示例所示）执行。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-332">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="cbf1c-333">不过，将命令提交到 MediatR 的操作非常类似，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-333">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="cbf1c-334">但是，这种情况还是有点高级，因为我们也要实现幂等命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-334">However, this case is also slightly more advanced because we're also implementing idempotent commands.</span></span> <span data-ttu-id="cbf1c-335">CreateOrderCommand 进程应该是幂等的，所以如果出于任何原因（如重试），通过网络复制相同消息，将仅处理同一个业务订单一次。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-335">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="cbf1c-336">这是通过以下方式实现的：包装业务命令（在此情况下为 CreateOrderCommand），将其嵌入通用 IdentifiedCommand（通过来自网络的每个消息的 ID 跟踪，必须是幂等的）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-336">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand, which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="cbf1c-337">在以下代码中，你会发现 IdentifiedCommand 仅仅是包含 ID 和已包装业务命令对象的 DTO。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-337">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="cbf1c-338">名为 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) 的 IdentifiedCommand 的 CommandHandler 将基本上检查消息中的 ID 是否已存在于表格中。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-338">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="cbf1c-339">如果已存在，将不会再次处理该命令，因此它充当幂等命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-339">If it already exists, that command won't be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="cbf1c-340">基础结构代码由以下 `_requestManager.ExistAsync` 方法调用执行。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-340">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> : IRequestHandler<IdentifiedCommand<T, R>, R>
        where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;
    private readonly ILogger<IdentifiedCommandHandler<T, R>> _logger;

    public IdentifiedCommandHandler(
        IMediator mediator,
        IRequestManager requestManager,
        ILogger<IdentifiedCommandHandler<T, R>> logger)
    {
        _mediator = mediator;
        _requestManager = requestManager;
        _logger = logger ?? throw new System.ArgumentNullException(nameof(logger));
    }

    /// <summary>
    /// Creates the result value to return if a previous request was found
    /// </summary>
    /// <returns></returns>
    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    /// <summary>
    /// This method handles the command. It just ensures that no other request exists with the same ID, and if this is the case
    /// just enqueues the original inner command.
    /// </summary>
    /// <param name="message">IdentifiedCommand which contains both original command & request ID</param>
    /// <returns>Return value of inner command or default value if request same ID was found</returns>
    public async Task<R> Handle(IdentifiedCommand<T, R> message, CancellationToken cancellationToken)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);
            try
            {
                var command = message.Command;
                var commandName = command.GetGenericTypeName();
                var idProperty = string.Empty;
                var commandId = string.Empty;

                switch (command)
                {
                    case CreateOrderCommand createOrderCommand:
                        idProperty = nameof(createOrderCommand.UserId);
                        commandId = createOrderCommand.UserId;
                        break;

                    case CancelOrderCommand cancelOrderCommand:
                        idProperty = nameof(cancelOrderCommand.OrderNumber);
                        commandId = $"{cancelOrderCommand.OrderNumber}";
                        break;

                    case ShipOrderCommand shipOrderCommand:
                        idProperty = nameof(shipOrderCommand.OrderNumber);
                        commandId = $"{shipOrderCommand.OrderNumber}";
                        break;

                    default:
                        idProperty = "Id?";
                        commandId = "n/a";
                        break;
                }

                _logger.LogInformation(
                    "----- Sending command: {CommandName} - {IdProperty}: {CommandId} ({@Command})",
                    commandName,
                    idProperty,
                    commandId,
                    command);

                // Send the embeded business command to mediator so it runs its related CommandHandler
                var result = await _mediator.Send(command, cancellationToken);

                _logger.LogInformation(
                    "----- Command result: {@Result} - {CommandName} - {IdProperty}: {CommandId} ({@Command})",
                    result,
                    commandName,
                    idProperty,
                    commandId,
                    command);

                return result;
            }
            catch
            {
                return default(R);
            }
        }
    }
}
```

<span data-ttu-id="cbf1c-341">由于 IdentifiedCommand 充当业务命令的信封，当业务命令由于不是重复 ID 而需要处理时，它会获取此内部业务命令，然后将其重新提交到转存进程，正如从 [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) 运行 `_mediator.Send(message.Command)` 时显示的代码的最后一部分所示。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-341">Since the IdentifiedCommand acts like a business command's envelope, when the business command needs to be processed because it is not a repeated ID, then it takes that inner business command and resubmits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="cbf1c-342">执行该操作时，它会链接和运行业务命令处理程序（在此情况下是针对订购数据库运行事务的 [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)），如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-342">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="cbf1c-343">注册由 MediatR 使用的类型</span><span class="sxs-lookup"><span data-stu-id="cbf1c-343">Register the types used by MediatR</span></span>

<span data-ttu-id="cbf1c-344">为了让 MediatR 识别命令处理程序类，需要在 IoC 容器中注册转存进程类和命令处理程序。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-344">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="cbf1c-345">默认情况下，MediatR 使用 Autofac 作为 IoC 容器，但还可以使用内置的 ASP.NET Core IoC 容器或受 MediatR 支持的其他容器。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-345">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="cbf1c-346">下面的代码演示如何在使用 Autofac 模块时注册转存进程的类型和命令。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-346">The following code shows how to register Mediator's types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand).GetTypeInfo().Assembly)
                .AsClosedTypesOf(typeof(IRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="cbf1c-347">MediatR 的魅力就在于此。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-347">This is where "the magic happens" with MediatR.</span></span>

<span data-ttu-id="cbf1c-348">由于每个命令处理程序都实现了泛型 `IRequestHandler<T>` 接口，因此使用 `RegisteredAssemblyTypes` 方法注册程序集时，所有标记为 `IRequestHandler` 的类型也将注册到它们的 `Commands` 中。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-348">As each command handler implements the generic `IRequestHandler<T>` interface, when you register the assemblies using `RegisteredAssemblyTypes` method all the types marked as `IRequestHandler` also gets registered with their `Commands`.</span></span> <span data-ttu-id="cbf1c-349">例如：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-349">For   example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="cbf1c-350">这是将命令与命令处理程序关联的代码。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-350">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="cbf1c-351">此处理程序仅仅是简单类，但它继承自 `RequestHandler<T>`，MediatR 确保其使用正确负载（命令）调用。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-351">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="cbf1c-352">使用 MediatR 中的行为处理命令时，应用整合问题</span><span class="sxs-lookup"><span data-stu-id="cbf1c-352">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="cbf1c-353">还需要执行一个操作：将整合问题应用到转存进程管道。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-353">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="cbf1c-354">还可在 Autofac 注册模块代码的末尾查看其如何注册行为类型，特别是 LoggingBehavior 类和 ValidatorBehavior 类。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-354">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="cbf1c-355">但是还可以添加其他自定义行为。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-355">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="cbf1c-356">[LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) 类可像以下代码那样实现 - 记录执行的命令处理程序的信息，以及是否成功。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-356">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="cbf1c-357">只需通过实现此行为类并在管道（在上面的 MediatorModule 中）中注册，所有通过 MediatR 处理的命令都会记录有关执行的信息。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-357">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="cbf1c-358">eShopOnContainers 订购微服务还会应用基本验证的第二个行为，即依赖 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 库的 [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) 类，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-358">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="cbf1c-359">如果验证失败，则此处的行为会引发异常，但是也可以返回结果对象，在成功时包含命令结果，或在未成功时包含验证消息。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-359">Here the behavior is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn't.</span></span> <span data-ttu-id="cbf1c-360">这样便可以更轻松地向用户显示验证结果。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-360">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="cbf1c-361">然后将根据 [FluentValidation](https://github.com/JeremySkinner/FluentValidation) 库为通过 CreateOrderCommand 传递的数据创建验证，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="cbf1c-361">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, you would create validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="cbf1c-362">可以创建其他验证。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-362">You could create additional validations.</span></span> <span data-ttu-id="cbf1c-363">这是实现命令验证的一种简洁、巧妙的方法。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-363">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="cbf1c-364">类似地，可实现其他方面的其他行为或要应用到命令的整合问题（需要处理它们时）。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-364">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="cbf1c-365">其他资源</span><span class="sxs-lookup"><span data-stu-id="cbf1c-365">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="cbf1c-366">转存进程模式</span><span class="sxs-lookup"><span data-stu-id="cbf1c-366">The mediator pattern</span></span>

- <span data-ttu-id="cbf1c-367">**转存进程模式** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-367">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="cbf1c-368">修饰器模式</span><span class="sxs-lookup"><span data-stu-id="cbf1c-368">The decorator pattern</span></span>

- <span data-ttu-id="cbf1c-369">**修饰器模式** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-369">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="cbf1c-370">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="cbf1c-370">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="cbf1c-371">**MediatR。**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-371">**MediatR.**</span></span> <span data-ttu-id="cbf1c-372">GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-372">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="cbf1c-373">**结合使用 CQRS 与 MediatR 和 AutoMapper** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-373">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="cbf1c-374">**简化控制器：POST 和命令。**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-374">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="cbf1c-375">**解决转存进程管道的整合问题** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-375">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="cbf1c-376">**CQRS 和 REST：完美组合** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-376">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="cbf1c-377">**MediatR 管道示例** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-377">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="cbf1c-378">**MediatR 和 ASP.NET Core 的垂直切片测试固定例程** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-378">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="cbf1c-379">**适用于 Microsoft 依赖注入的 MediatR 扩展已发布** </span><span class="sxs-lookup"><span data-stu-id="cbf1c-379">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="cbf1c-380">Fluent 验证</span><span class="sxs-lookup"><span data-stu-id="cbf1c-380">Fluent validation</span></span>

- <span data-ttu-id="cbf1c-381">**Jeremy Skinner。FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="cbf1c-381">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="cbf1c-382">GitHub 存储库。</span><span class="sxs-lookup"><span data-stu-id="cbf1c-382">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="cbf1c-383">[上一页](microservice-application-layer-web-api-design.md)
> [下一页](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="cbf1c-383">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
