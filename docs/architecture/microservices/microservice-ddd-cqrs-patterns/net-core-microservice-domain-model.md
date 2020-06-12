---
title: 使用 .NET Core 实现微服务域模型
description: 适用于容器化 .NET 应用程序的 .NET 微服务体系结构 | 获取面向 DDD 的域模型的实现详细信息。
ms.date: 10/08/2018
ms.openlocfilehash: 0b42ecc2440faf5870b2d99e31d03cda00b21ce0
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306899"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="6f1a2-103">使用 .NET Core 实现微服务域模型</span><span class="sxs-lookup"><span data-stu-id="6f1a2-103">Implement a microservice domain model with .NET Core</span></span>

<span data-ttu-id="6f1a2-104">上一节解释了域模型设计的基本设计原则和模式。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="6f1a2-105">现在开始探索使用 .NET Core（纯 C\# 代码）和 EF Core 实现域模型的可能方式。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="6f1a2-106">域模型将仅由代码组成。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-106">Your domain model will be composed simply of your code.</span></span> <span data-ttu-id="6f1a2-107">它只有 EF Core 模型要求，并不真正依赖于 EF。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="6f1a2-108">你不应该硬依赖或引用 EF Core 或域模型中的任何其他 ORM。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="6f1a2-109">自定义 .NET Standard 库中的域模型结构</span><span class="sxs-lookup"><span data-stu-id="6f1a2-109">Domain model structure in a custom .NET Standard Library</span></span>

<span data-ttu-id="6f1a2-110">用于 eShopOnContainers 参考应用程序的文件夹组织演示了该应用程序的 DDD 模型。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="6f1a2-111">你可能会发现，不同的文件夹组织能更清楚地传达为应用程序所做的设计选择。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="6f1a2-112">如图 7-10 所示，订购域模型包含两个聚合，即订单聚合和买方聚合。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-112">As you can see in Figure 7-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="6f1a2-113">每个聚合都是一组域实体和值对象，但聚合也可以由单个域实体（聚合根或根实体）组成。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="解决方案资源管理器中的 Ordering.Domain 项目的屏幕截图。":::
<span data-ttu-id="6f1a2-115">Ordering.Domain 项目的解决方案资源管理器视图，其中显示包含 BuyerAggregate 和 OrderAggregate 文件夹的 AggregatesModel 文件夹，这两个文件夹各自包含其实体类、值对象文件等。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-115">The Solution Explorer view for the Ordering.Domain project, showing the AggregatesModel folder containing the BuyerAggregate and OrderAggregate folders, each one containing its entity classes, value object files and so on.</span></span>
:::image-end:::

<span data-ttu-id="6f1a2-116">**图 7-10**。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-116">**Figure 7-10**.</span></span> <span data-ttu-id="6f1a2-117">eShopOnContainers 中订购微服务的域模型结构</span><span class="sxs-lookup"><span data-stu-id="6f1a2-117">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="6f1a2-118">此外，域模型层还包含存储库协定（接口）作为域模型的基础结构要求。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-118">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="6f1a2-119">换而言之，这些接口表示基础结构层必须实现的存储库和方法。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-119">In other words, these interfaces express what repositories and the methods the infrastructure layer must implement.</span></span> <span data-ttu-id="6f1a2-120">务必将存储库实现放在域模型层之外、基础结构层库之中，这样，域模型层就不会受到基础结构技术（例如 Entity Framework）中 API 或类的“污染”。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-120">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not "contaminated" by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="6f1a2-121">你还可以看到 一个 [SeedWork](https://martinfowler.com/bliki/Seedwork.html) 文件夹，其中包含可用作域实体和值对象基础的自定义基类，因此每个域的对象类中都没有冗余代码。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-121">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain's object class.</span></span>

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="6f1a2-122">在自定义 .NET Standard 库中构造聚合</span><span class="sxs-lookup"><span data-stu-id="6f1a2-122">Structure aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="6f1a2-123">聚合是指组合到一起以匹配事务一致性的域对象群集。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-123">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="6f1a2-124">这些对象可能是实体实例（其中一个是聚合根或根实体）加上任何附加值对象。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-124">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="6f1a2-125">事务一致性意味着，保证聚合在业务操作结束时保持一致且处于最新状态。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-125">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="6f1a2-126">例如，eShopOnContainers 订购微服务域模型中订单聚合的组成如图 7-11 所示。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-126">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 7-11.</span></span>

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="OrderAggregate 文件夹及其类的屏幕截图。":::
<span data-ttu-id="6f1a2-128">OrderAggregate 文件夹的详细视图：Address.cs 是值对象，IOrderRepository 是存储库接口，Order.cs 是聚合根，OrderItem.cs 是子实体，而 OrderStatus.cs 是枚举类。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-128">A detailed view of the OrderAggregate folder: Address.cs is a value object, IOrderRepository is a repo interface, Order.cs is an aggregate root, OrderItem.cs is a child entity, and OrderStatus.cs is an enumeration class.</span></span>
:::image-end:::

<span data-ttu-id="6f1a2-129">**图 7-11**。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-129">**Figure 7-11**.</span></span> <span data-ttu-id="6f1a2-130">Visual Studio 解决方案中的订单聚合</span><span class="sxs-lookup"><span data-stu-id="6f1a2-130">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="6f1a2-131">如果打开聚合文件夹中的任意文件，可以看到它是如何被标记为自定义基类或接口的（像实体或值对象一样），正如在 [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) 文件夹中所实现的一样。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-131">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implement-domain-entities-as-poco-classes"></a><span data-ttu-id="6f1a2-132">将域实体作为 POCO 类实现</span><span class="sxs-lookup"><span data-stu-id="6f1a2-132">Implement domain entities as POCO classes</span></span>

<span data-ttu-id="6f1a2-133">通过创建实现域实体的 POCO 类，可在 .NET 中实现域模型。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-133">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="6f1a2-134">在下面的示例中，Order 类同时被定义为实体和聚合根。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-134">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="6f1a2-135">Order 类派生自 Entity 基类，因此它可以重用与实体相关的通用代码。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-135">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="6f1a2-136">请记住，这些基类和接口由你在域模型项目中定义，因此它是你的代码，而不是 ORM（例如 EF）中的基础结构代码。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-136">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="6f1a2-137">值得注意的是，这是一个作为 POCO 类实现的域实体。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-137">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="6f1a2-138">它不直接依赖于 Entity Framework Core 或任何其他基础结构框架。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-138">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="6f1a2-139">DDD 中采用的就是这种实现方式，即完全通过 C# 代码来实现域模型。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-139">This implementation is as it should be in DDD, just C# code implementing a domain model.</span></span>

<span data-ttu-id="6f1a2-140">此外，该类用名为 IAggregateRoot 的接口修饰。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-140">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="6f1a2-141">该接口是一个空接口，有时称为*标记接口*，仅用于指示此实体类也是聚合根。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-141">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="6f1a2-142">标记接口有时被认为是一种反模式；然而，它也是一种对类进行标记的干净方式，尤其是当该接口可能正在不断演变时。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-142">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="6f1a2-143">属性可以是标记的另一种选择，但是，将基类 (Entity) 放在 IAggregate 接口旁边比在该类上方放置一个 Aggregate 属性标记更为显眼。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-143">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="6f1a2-144">在任何情况下，这都只是一个偏好问题。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-144">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="6f1a2-145">具有聚合根意味着与聚合实体的一致性和业务规则相关的大部分代码应该作为 Order 聚合根类中的方法实现（例如，向聚合添加 OrderItem 对象时的 AddOrderItem）。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-145">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate's entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="6f1a2-146">不能单独或直接创建或更新 OrderItems 对象；AggregateRoot 类必须保持对其子实体执行的任何更新操作的控制和一致性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-146">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulate-data-in-the-domain-entities"></a><span data-ttu-id="6f1a2-147">封装域实体中的数据</span><span class="sxs-lookup"><span data-stu-id="6f1a2-147">Encapsulate data in the Domain Entities</span></span>

<span data-ttu-id="6f1a2-148">实体模型中的一个常见问题是，它们将集合导航属性公开为可公开访问的列表类型。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-148">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="6f1a2-149">这使得任何协作方开发人员都能操作这些集合类型的内容，这可能会绕过与集合相关的重要业务规则，从而可能使对象处于无效状态。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-149">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="6f1a2-150">若要解决该问题，可向相关集合公开只读访问权限，并显式提供一些方法来定义客户端操作这些集合的方式。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-150">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="6f1a2-151">请注意，在前面的代码中，许多属性是只读或私有属性，只能由类方法进行更新，因此任何更新都应考虑在类方法中指定的业务领域不变量和逻辑。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-151">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update considers business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="6f1a2-152">例如，使用 DDD 模式时，不能从任何命令处理程序方法或应用层类执行以下命令（实际上，你应该无法这样做）：</span><span class="sxs-lookup"><span data-stu-id="6f1a2-152">For example, following DDD patterns, **you should *not* do the following** from any command handler method or application layer class (actually, it should be impossible for you to do so):</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="6f1a2-153">在此示例中，Add 方法就是一种数据添加操作，可以直接访问 OrderItems 集合。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-153">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="6f1a2-154">因此，与针对子实体执行的该操作相关的大部分域逻辑、规则或验证将分布于应用层（命令处理程序和 Web API 控制器）中。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-154">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="6f1a2-155">如果绕过聚合根，聚合根无法保证其不变量、有效性或一致性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-155">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="6f1a2-156">最终将产生面条式代码或事务脚本代码。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-156">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="6f1a2-157">若要遵循 DDD 模式，实体不能在任何实体属性中拥有公共 setter。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-157">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="6f1a2-158">实体中的更改应由显式方法驱动，这些方法使用显式通用语言来描述它们正在实体中执行的更改。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-158">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="6f1a2-159">此外，实体中的集合（如订单项）应为只读属性（稍后会解释 AsReadOnly 方法）。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-159">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="6f1a2-160">只能从聚合根类方法或子实体方法中更新它。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-160">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="6f1a2-161">从 Order 聚合根的代码中可以看到，所有 setter 都应该是私有的，或者至少是从外部只读的，因此针对实体数据或其子实体的任何操作都必须通过实体类中的方法来执行。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-161">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity's data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="6f1a2-162">这将以一种面向对象的可控方式（而不是通过实现事务脚本代码）保持一致性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-162">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="6f1a2-163">下面的代码片段展示了对将 OrderItem 对象添加到 Order 聚合的任务进行编码的正确方式。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-163">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object's business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="6f1a2-164">在此片段中，与 OrderItem 对象创建相关的大部分验证或逻辑都由 Order 聚合根在 AddOrderItem 方法中控制 — 特别是与聚合中的其他元素相关的验证和逻辑。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-164">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="6f1a2-165">例如，你可能在多次调用 AddOrderItem 后得到相同的产品项。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-165">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="6f1a2-166">在该方法中，你可以检查产品项并将相同的产品项合并到具有多个单元的单个 OrderItem 对象中。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-166">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="6f1a2-167">此外，如果折扣金额不同但产品 ID 相同，则可能会应用较高的折扣。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-167">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="6f1a2-168">此原则适用于 OrderItem 对象的任何其他域逻辑。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-168">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="6f1a2-169">此外，新的 OrderItem(params) 操作也由 Order 聚合根中的 AddOrderItem 方法控制和执行。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-169">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="6f1a2-170">因此，与该操作相关的大部分逻辑或验证（尤其是影响其他子实体间一致性的逻辑或验证）将位于聚合根的单个位置中。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-170">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="6f1a2-171">这是聚合根模式的最终目的。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-171">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="6f1a2-172">使用 Entity Framework Core 1.1 或更高版本时，可以更好地表示 DDD 实体，因为它允许[映射到字段](https://docs.microsoft.com/ef/core/modeling/backing-field)以及属性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-172">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="6f1a2-173">这在保护子实体或值对象集合时很有用。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-173">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="6f1a2-174">借助此增强功能，你可以使用简单的私有字段，而不必使用属性，并且可以在公共方法中实现对字段集合的任何更新，并通过 AsReadOnly 方法提供只读访问。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-174">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="6f1a2-175">在 DDD 中，你想通过实体（或构造函数）中的方法只更新实体，以便控制任何不变量和数据一致性，因此，属性定义为仅具有 get 取值函数。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-175">In DDD, you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="6f1a2-176">这些属性受私有字段支持。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-176">The properties are backed by private fields.</span></span> <span data-ttu-id="6f1a2-177">只能从类中访问私有成员。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-177">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="6f1a2-178">但是，有一个例外：EF Core 也需要设置这些字段（这样它就可以返回具有适当值的对象）。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-178">However, there one exception: EF Core needs to set these fields as well (so it can return the object with the proper values).</span></span>

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="6f1a2-179">将仅具有 get 取值函数的属性映射到数据库表中的字段</span><span class="sxs-lookup"><span data-stu-id="6f1a2-179">Map properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="6f1a2-180">将属性映射到数据库表列不是域的责任，而是基础结构和持久性层的一部分。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-180">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="6f1a2-181">之所以提到这一点，是为了让你留意 EF Core 1.1 或更高版本中有关如何为实体建模的新功能。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-181">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="6f1a2-182">有关此主题的其他详细信息，请参阅基础结构和持久性部分。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-182">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="6f1a2-183">使用 EF Core 1.0 或更高版本时，需要在 DbContext 中将定义为仅具有 getter 的属性映射到数据库表中的实际字段。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-183">When you use EF Core 1.0 or later, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="6f1a2-184">此操作通过 PropertyBuilder 类的 HasField 方法完成。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-184">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="map-fields-without-properties"></a><span data-ttu-id="6f1a2-185">映射不含属性的字段</span><span class="sxs-lookup"><span data-stu-id="6f1a2-185">Map fields without properties</span></span>

<span data-ttu-id="6f1a2-186">通过借助 EF Core 1.1 或更高版本中的功能将列映射到字段，也可以不使用属性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-186">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="6f1a2-187">你可以只将表中的列映射到字段。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-187">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="6f1a2-188">它的常见用例是那些无需从实体外访问的内部状态的私有字段。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-188">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="6f1a2-189">例如，前面的 OrderAggregate 代码示例中有几个私有字段，比如 `_paymentMethodId` 字段，对于 setter 或 getter，它们都没有相关属性。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-189">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="6f1a2-190">该字段也可以在订单的业务逻辑内进行计算并从订单的方法中使用，但它也需要保存在数据库中。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-190">That field could also be calculated within the order's business logic and used from the order's methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="6f1a2-191">因此，EF Core（从 v1.1 开始）提供了一种将没有相关属性的字段映射到数据库列的方法。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-191">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="6f1a2-192">本指南的[基础结构层](ddd-oriented-microservice.md#the-infrastructure-layer)部分也对此进行了说明。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-192">This is also explained in the [Infrastructure layer](ddd-oriented-microservice.md#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6f1a2-193">其他资源</span><span class="sxs-lookup"><span data-stu-id="6f1a2-193">Additional resources</span></span>

- <span data-ttu-id="6f1a2-194">**Vaughn Vernon。使用 DDD 和 Entity Framework 对聚合建模**。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-194">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="6f1a2-195">请注意，*不*是 Entity Framework Core。</span><span class="sxs-lookup"><span data-stu-id="6f1a2-195">Note that this is *not* Entity Framework Core.</span></span> \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- <span data-ttu-id="6f1a2-196">**Julie Lerman.数据点 - 域驱动设计的编码：面向数据聚焦型开发人员的提示** </span><span class="sxs-lookup"><span data-stu-id="6f1a2-196">**Julie Lerman. Data Points - Coding for Domain-Driven Design: Tips for Data-Focused Devs** </span></span>\
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- <span data-ttu-id="6f1a2-197">**Udi Dahan.如何创建完全封装的域模型** </span><span class="sxs-lookup"><span data-stu-id="6f1a2-197">**Udi Dahan. How to create fully encapsulated Domain Models** </span></span>\
  <https://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> <span data-ttu-id="6f1a2-198">[上一页](microservice-domain-model.md)
> [下一页](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="6f1a2-198">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>
