---
title: 使用 Entity Framework Core 实现基础结构持久性层
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 探索使用 Entity Framework Core 实现基础结构持久性层的细节。
ms.date: 01/30/2020
ms.openlocfilehash: f9d97319d378b6fd3eb681fd2873e5fbeead787f
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100972"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="d85d4-103">使用 Entity Framework Core 实现基础结构持久性层</span><span class="sxs-lookup"><span data-stu-id="d85d4-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="d85d4-104">当使用 SQL Server、Oracle 或 PostgreSQL 等关系数据库时，推荐的方法是基于 Entity Framework (EF) 实现持久性层。</span><span class="sxs-lookup"><span data-stu-id="d85d4-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="d85d4-105">EF 支持 LINQ，并为模型提供强类型化的对象，且为数据库提供简化的持久性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="d85d4-106">Entity Framework 很长一段时期作为 .NET Framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="d85d4-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="d85d4-107">使用 .NET Core 时，还应使用 Entity Framework Core，它在 Windows 或 Linux 上的运行方式与在 .NET Core 上的相同。</span><span class="sxs-lookup"><span data-stu-id="d85d4-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="d85d4-108">EF Core 完全重写了 Entity Framework，采用更小的占用空间来实现，且性能上具有重大改进。</span><span class="sxs-lookup"><span data-stu-id="d85d4-108">EF Core is a complete rewrite of Entity Framework that's implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="d85d4-109">Entity Framework Core 简介</span><span class="sxs-lookup"><span data-stu-id="d85d4-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="d85d4-110">Entity Framework (EF) Core 是轻量化、可扩展和跨平台版的常用 Entity Framework 数据访问技术。</span><span class="sxs-lookup"><span data-stu-id="d85d4-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="d85d4-111">它随 .NET Core 于 2016 年年中引入。</span><span class="sxs-lookup"><span data-stu-id="d85d4-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="d85d4-112">EF 简介已提供于 Microsoft 文档中，因此这里我们只提供指向该信息的链接。</span><span class="sxs-lookup"><span data-stu-id="d85d4-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d85d4-113">其他资源</span><span class="sxs-lookup"><span data-stu-id="d85d4-113">Additional resources</span></span>

- <span data-ttu-id="d85d4-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="d85d4-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="d85d4-115">**借助 Visual Studio 使用 ASP.NET Core 和 Entity Framework Core 入门** </span><span class="sxs-lookup"><span data-stu-id="d85d4-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="d85d4-116">**DbContext 类** </span><span class="sxs-lookup"><span data-stu-id="d85d4-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="d85d4-117">**比较 EF Core 和 EF6.x** </span><span class="sxs-lookup"><span data-stu-id="d85d4-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="d85d4-118">Entity Framework Core 中的基础结构（DDD 角度）</span><span class="sxs-lookup"><span data-stu-id="d85d4-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="d85d4-119">从 DDD 的角度来看，EF 的一个重要功能是能够使用 POCO 域实体，在 EF 术语中也称为 POCO 代码优先实体。</span><span class="sxs-lookup"><span data-stu-id="d85d4-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="d85d4-120">如果使用 POCO 域实体，根据[持久性无感知](https://deviq.com/persistence-ignorance/)和[基础结构无感知](https://ayende.com/blog/3137/infrastructure-ignorance)原则，域模型类对于持久性是无感知的。</span><span class="sxs-lookup"><span data-stu-id="d85d4-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="d85d4-121">根据 DDD 模式，应在实体类自身内封装域行为和规则，以便在访问任何集合时，它可以控制不变量、验证和规则。</span><span class="sxs-lookup"><span data-stu-id="d85d4-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="d85d4-122">因此，从 DDD 角度来看，允许公开访问子实体或值对象的集合不是一个好做法。</span><span class="sxs-lookup"><span data-stu-id="d85d4-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="d85d4-123">相反，建议公开用于控制如何及何时更新字段和属性集合的方法，以及这种情况下应发生什么行为和操作的方法。</span><span class="sxs-lookup"><span data-stu-id="d85d4-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="d85d4-124">自 EF Core 1.1 开始，若要满足这些 DDD 要求，可以在实体中包含纯字段，而非公共属性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="d85d4-125">如果不希望可从外部访问实体字段，创建特性或字段（而非属性）即可。</span><span class="sxs-lookup"><span data-stu-id="d85d4-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="d85d4-126">还可使用专用属性资源库。</span><span class="sxs-lookup"><span data-stu-id="d85d4-126">You can also use private property setters.</span></span>

<span data-ttu-id="d85d4-127">相同地，现可使用类型化为 `IReadOnlyCollection<T>`（受依赖 EF 实现持久性的实体中集合（如 `List<T>`）的专用字段成员的支持）的公共属性对集合进行只读访问。</span><span class="sxs-lookup"><span data-stu-id="d85d4-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="d85d4-128">以前版本的 Entity Framework 需要集合属性来支持 `ICollection<T>`，这意味着任何使用父实体类的开发人员都无法通过其属性集合来添加或删除项。</span><span class="sxs-lookup"><span data-stu-id="d85d4-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="d85d4-129">这种可能性会违反 DDD 中的建议模式。</span><span class="sxs-lookup"><span data-stu-id="d85d4-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="d85d4-130">公开只读 `IReadOnlyCollection<T>` 对象时可使用专用集合，如以下代码示例所示：</span><span class="sxs-lookup"><span data-stu-id="d85d4-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="d85d4-131">`OrderItems` 属性仅可通过 `IReadOnlyCollection<OrderItem>` 以只读形式进行访问。</span><span class="sxs-lookup"><span data-stu-id="d85d4-131">The `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="d85d4-132">此类型是只读的，因此它免受定期外部更新。</span><span class="sxs-lookup"><span data-stu-id="d85d4-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="d85d4-133">EF Core 提供一种方法，可将域模型映射到物理数据库，而不会“污染”域模型。</span><span class="sxs-lookup"><span data-stu-id="d85d4-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="d85d4-134">这是纯 .NET POCO 代码，因为映射操作在持久性层中实现。</span><span class="sxs-lookup"><span data-stu-id="d85d4-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="d85d4-135">在该映射操作中，需要配置“字段到数据库”映射。</span><span class="sxs-lookup"><span data-stu-id="d85d4-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="d85d4-136">在来自 `OrderingContext` 和 `OrderEntityTypeConfiguration` 类的 `OnModelCreating` 方法的以下示例中，调用 `SetPropertyAccessMode` 来告诉 EF Core 通过其字段访问 `OrderItems` 属性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="d85d4-137">使用字段而不使用属性时，`OrderItem` 实体得以持久保存，这就好像它有一个 `List<OrderItem>` 属性一样。</span><span class="sxs-lookup"><span data-stu-id="d85d4-137">When you use fields instead of properties, the `OrderItem` entity is persisted as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="d85d4-138">但是，它公开单个访问器（`AddOrderItem` 方法），用于将新项添加到订单。</span><span class="sxs-lookup"><span data-stu-id="d85d4-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="d85d4-139">因此，行为和数据绑定在一起，将在使用域模型的任何应用程序代码间保持一致。</span><span class="sxs-lookup"><span data-stu-id="d85d4-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="d85d4-140">使用 Entity Framework Core 实现自定义存储库</span><span class="sxs-lookup"><span data-stu-id="d85d4-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="d85d4-141">在实现级别上，当执行更新时，存储库就是一个具有数据持久性代码的类，由工作单元（EF Core 中的 DBContext）进行协调，如下面的类所示：</span><span class="sxs-lookup"><span data-stu-id="d85d4-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using directives...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="d85d4-142">`IBuyerRepository` 接口来自于域模型层（采用协定的形式）。</span><span class="sxs-lookup"><span data-stu-id="d85d4-142">The `IBuyerRepository` interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="d85d4-143">但是，存储库在持久性和基础结构层上实现。</span><span class="sxs-lookup"><span data-stu-id="d85d4-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="d85d4-144">EF DbContext 经由依赖关系注入而通过构造函数。</span><span class="sxs-lookup"><span data-stu-id="d85d4-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="d85d4-145">它在同一 HTTP 请求范围内的多个存储库之间进行共享，这得益于其在 IoC 容器（也可使用 `services.AddDbContext<>` 进行显式设置）中的默认生存期 (`ServiceLifetime.Scoped`)。</span><span class="sxs-lookup"><span data-stu-id="d85d4-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="d85d4-146">存储库中的实现方法（更新或事务与查询）</span><span class="sxs-lookup"><span data-stu-id="d85d4-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="d85d4-147">每个存储库类中，都应放置持久性方法来更新受其相关聚合约束的实体状态。</span><span class="sxs-lookup"><span data-stu-id="d85d4-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="d85d4-148">请记住，聚合与其相关存储库之间存在一对一关系。</span><span class="sxs-lookup"><span data-stu-id="d85d4-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="d85d4-149">同时请考虑到，聚合根实体对象可能已将子实体嵌入其 EF 图内。</span><span class="sxs-lookup"><span data-stu-id="d85d4-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="d85d4-150">例如，购买者可能有作为相关子实体的多个支付方法。</span><span class="sxs-lookup"><span data-stu-id="d85d4-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="d85d4-151">由于 eShopOnContainers 中订购微服务的方式也基于 CQS/CQRS，大多数查询不在自定义存储库中实现。</span><span class="sxs-lookup"><span data-stu-id="d85d4-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="d85d4-152">一般而言，开发人员可以自由地为表示层创建所需查询和联接，而不受聚合、每个聚合的自定义存储库和 DDD 的限制。</span><span class="sxs-lookup"><span data-stu-id="d85d4-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="d85d4-153">本指南建议的大多数自定义存储库具有多个更新或事务性方法，但只有查询方法需要更新数据。</span><span class="sxs-lookup"><span data-stu-id="d85d4-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="d85d4-154">例如，BuyerRepository 存储库实现 FindAsync 方法，因为应用程序需要知道创建订单相关的新买家之前是否存在特定买家。</span><span class="sxs-lookup"><span data-stu-id="d85d4-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="d85d4-155">但是，正如所提及的，使数据发送至表示层或客户端应用的真正查询方法在使用 Dapper 基于灵活查询的 CQRS 查询中得以实现。</span><span class="sxs-lookup"><span data-stu-id="d85d4-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="d85d4-156">使用自定义存储库与直接使用 EF DbContext</span><span class="sxs-lookup"><span data-stu-id="d85d4-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="d85d4-157">实体框架 DbContext 类基于工作单元和存储库模式，且可直接通过代码（如 ASP.NET Core MVC 控制器）进行使用。</span><span class="sxs-lookup"><span data-stu-id="d85d4-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="d85d4-158">工作单元模式和存储库模式产生最简单的代码，如 eShopOnContainers 的 CRUD 目录微服务中所示。</span><span class="sxs-lookup"><span data-stu-id="d85d4-158">The Unit of Work and Repository patterns result in the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="d85d4-159">如果需要尽可能简单的代码，建议直接使用 DbContext 类，就像许多开发人员操作的那样。</span><span class="sxs-lookup"><span data-stu-id="d85d4-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="d85d4-160">但是，实现更复杂的微服务或应用程序时，实现自定义存储库将提供以下几个优势。</span><span class="sxs-lookup"><span data-stu-id="d85d4-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="d85d4-161">工作单元和存储库模式旨在封装基础结构持久性层，以便从应用程序和域模型层脱耦。</span><span class="sxs-lookup"><span data-stu-id="d85d4-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain-model layers.</span></span> <span data-ttu-id="d85d4-162">实现这些模式将促进用于模拟数据库访问的模拟数据库的使用。</span><span class="sxs-lookup"><span data-stu-id="d85d4-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="d85d4-163">图 7-18 中可以看到不使用存储库（直接使用 EF DbContext）与使用存储库（更易于模拟这些存储库）之间的差异。</span><span class="sxs-lookup"><span data-stu-id="d85d4-163">In Figure 7-18, you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories, which makes it easier to mock those repositories.</span></span>

![显示两个存储库中的组件和数据流的关系图。](./media/infrastructure-persistence-layer-implementation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="d85d4-165">**图 7-18**。</span><span class="sxs-lookup"><span data-stu-id="d85d4-165">**Figure 7-18**.</span></span> <span data-ttu-id="d85d4-166">使用自定义存储库与纯 DbContext</span><span class="sxs-lookup"><span data-stu-id="d85d4-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="d85d4-167">图 7-18 显示了使用自定义存储库添加了抽象层，可用于通过模拟存储库来简化测试。</span><span class="sxs-lookup"><span data-stu-id="d85d4-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="d85d4-168">模拟时有多个备选项。</span><span class="sxs-lookup"><span data-stu-id="d85d4-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="d85d4-169">只模拟存储库或模拟整个工作单元。</span><span class="sxs-lookup"><span data-stu-id="d85d4-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="d85d4-170">通常情况下，只模拟存储库就足够了，不需要提取并模拟整个工作单元那般的复杂。</span><span class="sxs-lookup"><span data-stu-id="d85d4-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="d85d4-171">稍后，当我们关注应用程序层时，将看到依赖关系注入在 ASP.NET Core 中的工作方式，以及使用存储库时的实现方式。</span><span class="sxs-lookup"><span data-stu-id="d85d4-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="d85d4-172">简而言之，自定义存储库允许使用不受数据层状态影响的单元测试来更轻松地测试代码。</span><span class="sxs-lookup"><span data-stu-id="d85d4-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="d85d4-173">如果运行的测试还通过 Entity Framework 访问实际的数据库，它们不是单元测试而是更为缓慢的集成测试。</span><span class="sxs-lookup"><span data-stu-id="d85d4-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="d85d4-174">如果直接使用 DbContext，则必须模拟它，或通过使用包含单元测试的可预测数据的内存中 SQL Server 来运行单元测试。</span><span class="sxs-lookup"><span data-stu-id="d85d4-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="d85d4-175">但模拟 DbContext 或控制假数据所需完成的工作比在存储库级别进行模拟所需完成的工作多。</span><span class="sxs-lookup"><span data-stu-id="d85d4-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="d85d4-176">当然，可以始终测试 MVC 控制器。</span><span class="sxs-lookup"><span data-stu-id="d85d4-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="d85d4-177">IoC 容器中的 EF DbContext 和 IUnitOfWork 实例生存期</span><span class="sxs-lookup"><span data-stu-id="d85d4-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="d85d4-178">`DbContext` 对象（作为 `IUnitOfWork` 对象公开）应在相同 HTTP 请求范围内的多个存储库之间进行共享。</span><span class="sxs-lookup"><span data-stu-id="d85d4-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="d85d4-179">例如，当正在执行的操作必须处理多个聚合时，或只是因为正在使用多个存储库实例时，就是这种情况。</span><span class="sxs-lookup"><span data-stu-id="d85d4-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="d85d4-180">还需要提到的是，`IUnitOfWork` 接口属于域层，而不是 EF Core 类型。</span><span class="sxs-lookup"><span data-stu-id="d85d4-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="d85d4-181">为此，`DbContext` 对象的实例必须将其服务生存期设置为 ServiceLifetime.Scoped。</span><span class="sxs-lookup"><span data-stu-id="d85d4-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="d85d4-182">这是在 IoC 容器中通过 ASP.NET Core Web API 项目中 `Startup.cs` 文件的 ConfigureServices 方法向 `services.AddDbContext` 注册 `DbContext` 时的默认生存期。</span><span class="sxs-lookup"><span data-stu-id="d85d4-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="d85d4-183">下面的代码阐释这一点。</span><span class="sxs-lookup"><span data-stu-id="d85d4-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="d85d4-184">不应将 DbContext 实例化模式配置为 ServiceLifetime.Transient 或 ServiceLifetime.Singleton。</span><span class="sxs-lookup"><span data-stu-id="d85d4-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="d85d4-185">IoC 容器中的存储库实例生存期</span><span class="sxs-lookup"><span data-stu-id="d85d4-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="d85d4-186">同样地，通常应将存储库生存期设置为范围内（Autofac 中的 InstancePerLifetimeScope）。</span><span class="sxs-lookup"><span data-stu-id="d85d4-186">In a similar way, repository's lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="d85d4-187">也可设置为短暂（Autofac 中的 InstancePerDependency），但使用范围内生存期时服务在内存方面会更有效率。</span><span class="sxs-lookup"><span data-stu-id="d85d4-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="d85d4-188">DbContext 设置为范围内 (InstancePerLifetimeScope) 生存期（DBContext 的默认生存期）时，为存储库使用的单一生存期可能导致严重的并发问题。</span><span class="sxs-lookup"><span data-stu-id="d85d4-188">Using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d85d4-189">其他资源</span><span class="sxs-lookup"><span data-stu-id="d85d4-189">Additional resources</span></span>

- <span data-ttu-id="d85d4-190">**在 ASP.NET MVC 应用程序中实现存储库模式和工作单元模式** </span><span class="sxs-lookup"><span data-stu-id="d85d4-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="d85d4-191">**Jonathan Allen。Entity Framework、Dapper 和 Chain 中存储库模式的实现策略** </span><span class="sxs-lookup"><span data-stu-id="d85d4-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="d85d4-192">**Cesar de la Torre。比较 ASP.NET Core IoC 容器服务生存期和 Autofac IoC 容器实例范围** </span><span class="sxs-lookup"><span data-stu-id="d85d4-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="d85d4-193">表映射</span><span class="sxs-lookup"><span data-stu-id="d85d4-193">Table mapping</span></span>

<span data-ttu-id="d85d4-194">表映射标识要从数据库查询并保存到数据库的表数据。</span><span class="sxs-lookup"><span data-stu-id="d85d4-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="d85d4-195">前面你已了解如何使用域实体（例如，产品或订单域）来生成相关的数据库架构。</span><span class="sxs-lookup"><span data-stu-id="d85d4-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="d85d4-196">EF 特别围绕着约定的概念进行设计。</span><span class="sxs-lookup"><span data-stu-id="d85d4-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="d85d4-197">约定处理“表的名称是什么？”</span><span class="sxs-lookup"><span data-stu-id="d85d4-197">Conventions address questions like "What will the name of a table be?"</span></span> <span data-ttu-id="d85d4-198">或者“什么属性是主键？”这类问题</span><span class="sxs-lookup"><span data-stu-id="d85d4-198">or "What property is the primary key?"</span></span> <span data-ttu-id="d85d4-199">约定通常基于常规名称。</span><span class="sxs-lookup"><span data-stu-id="d85d4-199">Conventions are typically based on conventional names.</span></span> <span data-ttu-id="d85d4-200">例如，主键通常是以 `Id` 结尾的属性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-200">For example, it is typical for the primary key to be a property that ends with `Id`.</span></span>

<span data-ttu-id="d85d4-201">按照约定，每个实体将设置为映射到名称与 `DbSet<TEntity>` 属性（公开派生上下文中的实体）相同的表中。</span><span class="sxs-lookup"><span data-stu-id="d85d4-201">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="d85d4-202">如果给定实体未提供任何 `DbSet<TEntity>` 值，则使用类名。</span><span class="sxs-lookup"><span data-stu-id="d85d4-202">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="d85d4-203">数据注释与 Fluent API</span><span class="sxs-lookup"><span data-stu-id="d85d4-203">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="d85d4-204">存在许多其他 EF Core 约定，其中大多数可通过使用数据注释或 Fluent API 进行更改，并且在 OnModelCreating 方法内实现。</span><span class="sxs-lookup"><span data-stu-id="d85d4-204">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="d85d4-205">数据注释必须在实体模型类自身上使用，从 DDD 观点来看实体模型类更具侵入性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-205">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="d85d4-206">这是因为你会因与基础结构数据库相关的数据注释而污染模型。</span><span class="sxs-lookup"><span data-stu-id="d85d4-206">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="d85d4-207">另一方面，Fluent API 可方便地更改数据持久性基础结构层中大部分的约定和映射，因此实体模型将保持整洁且从持久性基础结构分离。</span><span class="sxs-lookup"><span data-stu-id="d85d4-207">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="d85d4-208">Fluent API 和 OnModelCreating 方法</span><span class="sxs-lookup"><span data-stu-id="d85d4-208">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="d85d4-209">如前文所述，为了更改约定和映射，可以使用 DbContext 类中的 OnModelCreating 方法。</span><span class="sxs-lookup"><span data-stu-id="d85d4-209">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="d85d4-210">eShopOnContainers 中的订购微服务根据需要实现显式映射和配置，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="d85d4-210">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

        orderConfiguration.HasKey(o => o.Id);

        orderConfiguration.Ignore(b => b.DomainEvents);

        orderConfiguration.Property(o => o.Id)
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="d85d4-211">可以设置同一 `OnModelCreating` 方法内的所有 Fluent API 映射，但最好是将该代码进行分区并得到多个配置类，每个实体一个，如示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d85d4-211">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="d85d4-212">尤其是对于大型模型，最好有单独的配置类用于配置不同的实体类型。</span><span class="sxs-lookup"><span data-stu-id="d85d4-212">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="d85d4-213">示例中的代码演示了几个显式声明和映射。</span><span class="sxs-lookup"><span data-stu-id="d85d4-213">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="d85d4-214">但是，EF Core 约定自动执行这里的许多映射，因此示例中需要的实际代码可能较小。</span><span class="sxs-lookup"><span data-stu-id="d85d4-214">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="d85d4-215">EF Core 中的 Hi/Lo 算法</span><span class="sxs-lookup"><span data-stu-id="d85d4-215">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="d85d4-216">前面示例中代码的一个有趣方面是，它使用 [Hi/Lo 算法](https://vladmihalcea.com/the-hilo-algorithm/)作为键生成策略。</span><span class="sxs-lookup"><span data-stu-id="d85d4-216">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="d85d4-217">在提交更改前需要唯一键时，Hi/Lo 算法很有用。</span><span class="sxs-lookup"><span data-stu-id="d85d4-217">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="d85d4-218">总之，Hi-Lo 算法将唯一标识符分配给表行，同时不依赖于立即将行存储于数据库中。</span><span class="sxs-lookup"><span data-stu-id="d85d4-218">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="d85d4-219">这使你立即开始使用标识符，就像常规顺序数据库 ID 中的那般。</span><span class="sxs-lookup"><span data-stu-id="d85d4-219">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="d85d4-220">Hi/Lo 算法描述用于从相关数据库序列获取一批唯一 ID 的机制。</span><span class="sxs-lookup"><span data-stu-id="d85d4-220">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="d85d4-221">因为该数据库可保证唯一性，所以这些 ID 可以安全地使用，用户之间因此不会有冲突。</span><span class="sxs-lookup"><span data-stu-id="d85d4-221">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="d85d4-222">出于这些原因，此算法很有趣：</span><span class="sxs-lookup"><span data-stu-id="d85d4-222">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="d85d4-223">它不中断工作单元模式。</span><span class="sxs-lookup"><span data-stu-id="d85d4-223">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="d85d4-224">它批量获取序列 ID，以最大限度地减少往返数据库的行程。</span><span class="sxs-lookup"><span data-stu-id="d85d4-224">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="d85d4-225">它生成一个人工可读标识符，不同于使用 GUID 的技术。</span><span class="sxs-lookup"><span data-stu-id="d85d4-225">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="d85d4-226">EF Core 支持使用 `UseHiLo` 方法的 [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm)，如前面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="d85d4-226">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="d85d4-227">映射字段（而非属性）</span><span class="sxs-lookup"><span data-stu-id="d85d4-227">Map fields instead of properties</span></span>

<span data-ttu-id="d85d4-228">使用此功能（自 EF Core 1.1 之后可用），可以直接将列映射到字段。</span><span class="sxs-lookup"><span data-stu-id="d85d4-228">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="d85d4-229">可以不在实体类中使用属性，而只是将列从表格映射到字段。</span><span class="sxs-lookup"><span data-stu-id="d85d4-229">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="d85d4-230">它的常见用法是那些无需从实体外进行访问的任意内部状态的专用字段。</span><span class="sxs-lookup"><span data-stu-id="d85d4-230">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="d85d4-231">可以使用单个字段或集合来执行此操作，如 `List<>` 字段。</span><span class="sxs-lookup"><span data-stu-id="d85d4-231">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="d85d4-232">我们前面讨论对域模型类进行建模时已提过这点，但此处你可以了解如何通过前述代码中强调的 `PropertyAccessMode.Field` 配置来执行该映射。</span><span class="sxs-lookup"><span data-stu-id="d85d4-232">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="d85d4-233">在 EF Core 中使用隐藏在基础结构级别的阴影属性</span><span class="sxs-lookup"><span data-stu-id="d85d4-233">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="d85d4-234">EF Core 中的阴影属性是不存于实体类模型中的属性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-234">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="d85d4-235">这些属性的值和状态完全在基础结构级别于 [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) 类中进行维护。</span><span class="sxs-lookup"><span data-stu-id="d85d4-235">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="d85d4-236">实现查询规范模式</span><span class="sxs-lookup"><span data-stu-id="d85d4-236">Implement the Query Specification pattern</span></span>

<span data-ttu-id="d85d4-237">如之前设计部分所述，查询规范模式是域驱动设计模式，设计用作可放置含可选排序及分页逻辑的查询定义的位置。</span><span class="sxs-lookup"><span data-stu-id="d85d4-237">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="d85d4-238">查询规范模式定义对象中的查询。</span><span class="sxs-lookup"><span data-stu-id="d85d4-238">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="d85d4-239">例如，为了封装搜索某些产品的分页查询，可以创建采用必要输入参数（pageNumber、pageSize、filter 等）的 PagedProduct 规范。</span><span class="sxs-lookup"><span data-stu-id="d85d4-239">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="d85d4-240">然后，在任何存储库方法（通常为 List() 重载）内，它会接受 IQuerySpecification 并基于该规范运行预期的查询。</span><span class="sxs-lookup"><span data-stu-id="d85d4-240">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="d85d4-241">常规规范接口示例如下面的 [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb) 的代码。</span><span class="sxs-lookup"><span data-stu-id="d85d4-241">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="d85d4-242">然后，常规规范基类的实现如下所示。</span><span class="sxs-lookup"><span data-stu-id="d85d4-242">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="d85d4-243">以下规范在给定购物篮 ID 或购物篮所属买家的 ID 情况下来加载单个购物篮实体。</span><span class="sxs-lookup"><span data-stu-id="d85d4-243">The following specification loads a single basket entity given either the basket's ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="d85d4-244">它将[立即加载](/ef/core/querying/related-data)购物篮的 `Items` 集合。</span><span class="sxs-lookup"><span data-stu-id="d85d4-244">It will [eagerly load](/ef/core/querying/related-data) the basket's `Items` collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }

    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="d85d4-245">最后，可以在下方看到常规 EF 存储库可以如何使用此类规范来筛选并立即加载与给定实体类型 T 相关的数据。</span><span class="sxs-lookup"><span data-stu-id="d85d4-245">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

<span data-ttu-id="d85d4-246">除了封装筛选逻辑，该规范还可指定要返回的数据的形状，包括要填充的属性。</span><span class="sxs-lookup"><span data-stu-id="d85d4-246">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="d85d4-247">尽管我们不建议从存储库返回 `IQueryable`，但可以在存储库中使用它们来生成一系列结果。</span><span class="sxs-lookup"><span data-stu-id="d85d4-247">Although we don't recommend returning `IQueryable` from a repository, it's perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="d85d4-248">可以看到此方法在以上 List 方法中使用，List 方法使用中间 `IQueryable` 表达式来生成查询的包含内容列表，然后再使用最后一行上的规范条件来执行查询。</span><span class="sxs-lookup"><span data-stu-id="d85d4-248">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query's list of includes before executing the query with the specification's criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d85d4-249">其他资源</span><span class="sxs-lookup"><span data-stu-id="d85d4-249">Additional resources</span></span>

- <span data-ttu-id="d85d4-250">**表映射** </span><span class="sxs-lookup"><span data-stu-id="d85d4-250">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="d85d4-251">**使用 HiLo 通过 Entity Framework Core 生成键** </span><span class="sxs-lookup"><span data-stu-id="d85d4-251">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="d85d4-252">**支持字段** </span><span class="sxs-lookup"><span data-stu-id="d85d4-252">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="d85d4-253">**Steve Smith.Entity Framework Core 中的封装集合** </span><span class="sxs-lookup"><span data-stu-id="d85d4-253">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="d85d4-254">阴影属性 </span><span class="sxs-lookup"><span data-stu-id="d85d4-254">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="d85d4-255">**规范模式** </span><span class="sxs-lookup"><span data-stu-id="d85d4-255">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="d85d4-256">[上一页](infrastructure-persistence-layer-design.md)
> [下一页](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="d85d4-256">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
