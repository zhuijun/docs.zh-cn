---
title: 将 NoSQL 数据库用作持久性基础结构
description: 大致了解 NoSQL 数据库（特别是 Azure Cosmos DB）作为持久性实现选项的使用情况。
ms.date: 01/30/2020
ms.openlocfilehash: a478809895b0c20824f08f20558f2d47e10223d0
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100803"
---
# <a name="use-nosql-databases-as-a-persistence-infrastructure"></a><span data-ttu-id="ff973-103">将 NoSQL 数据库用作持久性基础结构</span><span class="sxs-lookup"><span data-stu-id="ff973-103">Use NoSQL databases as a persistence infrastructure</span></span>

<span data-ttu-id="ff973-104">将 NoSQL 数据库用于基础结构数据层时，通常不使用 Entity Framework Core 等 ORM。</span><span class="sxs-lookup"><span data-stu-id="ff973-104">When you use NoSQL databases for your infrastructure data tier, you typically do not use an ORM like Entity Framework Core.</span></span> <span data-ttu-id="ff973-105">而是使用 NoSQL 引擎提供的 API，如 Azure Cosmos DB、MongoDB、Cassandra、RavenDB、CouchDB 或 Azure 存储表等。</span><span class="sxs-lookup"><span data-stu-id="ff973-105">Instead you use the API provided by the NoSQL engine, such as Azure Cosmos DB, MongoDB, Cassandra, RavenDB, CouchDB, or Azure Storage Tables.</span></span>

<span data-ttu-id="ff973-106">但是，当使用 NoSQL 数据库时，尤其是诸如 Azure Cosmos DB、CouchDB 或 RavenDB 等面向文档的数据库时，在关于聚合根、子实体类和值对象类的标识方面，使用 DDD 聚合设计模型的方式部分类似于在 EF Core 中执行的方式。</span><span class="sxs-lookup"><span data-stu-id="ff973-106">However, when you use a NoSQL database, especially a document-oriented database like Azure Cosmos DB, CouchDB, or RavenDB, the way you design your model with DDD aggregates is partially similar to how you can do it in EF Core, in regards to the identification of aggregate roots, child entity classes, and value object classes.</span></span> <span data-ttu-id="ff973-107">但从根本上讲，数据库的选择会影响设计。</span><span class="sxs-lookup"><span data-stu-id="ff973-107">But, ultimately, the database selection will impact in your design.</span></span>

<span data-ttu-id="ff973-108">当使用面向文档的数据库时，可将聚合作为单个文档实现，以 JSON 或其他格式进行序列化。</span><span class="sxs-lookup"><span data-stu-id="ff973-108">When you use a document-oriented database, you implement an aggregate as a single document, serialized in JSON or another format.</span></span> <span data-ttu-id="ff973-109">但是，从域模型代码的角度来看，数据库的使用是透明的。</span><span class="sxs-lookup"><span data-stu-id="ff973-109">However, the use of the database is transparent from a domain model code point of view.</span></span> <span data-ttu-id="ff973-110">在使用 NoSQL 数据库时，仍然使用实体类和聚合根类，但比使用 EF Core 时具有更大的灵活性，因为持久性不相关。</span><span class="sxs-lookup"><span data-stu-id="ff973-110">When using a NoSQL database, you still are using entity classes and aggregate root classes, but with more flexibility than when using EF Core because the persistence is not relational.</span></span>

<span data-ttu-id="ff973-111">区别在于如何保留该模型。</span><span class="sxs-lookup"><span data-stu-id="ff973-111">The difference is in how you persist that model.</span></span> <span data-ttu-id="ff973-112">如果基于 POCO 实体类实现域模型，与基础结构持久性无关，则似乎你可能会移至不同的持久性基础结构，即使从关系数据库到 NoSQL 也是如此。</span><span class="sxs-lookup"><span data-stu-id="ff973-112">If you implemented your domain model based on POCO entity classes, agnostic to the infrastructure persistence, it might look like you could move to a different persistence infrastructure, even from relational to NoSQL.</span></span> <span data-ttu-id="ff973-113">但是，这不应该是你的目标。</span><span class="sxs-lookup"><span data-stu-id="ff973-113">However, that should not be your goal.</span></span> <span data-ttu-id="ff973-114">不同的数据库技术中总是存在各种约束和权衡，因此无法对关系数据库或 NoSQL 数据库使用相同的模型。</span><span class="sxs-lookup"><span data-stu-id="ff973-114">There are always constraints and trade-offs in the different database technologies, so you will not be able to have the same model for relational or NoSQL databases.</span></span> <span data-ttu-id="ff973-115">更改持久性模型并不是简单的任务，因为事务和永久性操作大不相同。</span><span class="sxs-lookup"><span data-stu-id="ff973-115">Changing persistence models is not a trivial task, because transactions and persistence operations will be very different.</span></span>

<span data-ttu-id="ff973-116">例如，在面向文档的数据库中，聚合根可以拥有多个子集合属性。</span><span class="sxs-lookup"><span data-stu-id="ff973-116">For example, in a document-oriented database, it is okay for an aggregate root to have multiple child collection properties.</span></span> <span data-ttu-id="ff973-117">在关系数据库中，无法轻松对查询多个子集合属性进行优化，因为会从 EF 返回 UNION ALL SQL 语句。</span><span class="sxs-lookup"><span data-stu-id="ff973-117">In a relational database, querying multiple child collection properties is not easily optimized, because you get a UNION ALL SQL statement back from EF.</span></span> <span data-ttu-id="ff973-118">对关系数据库或 NoSQL 数据库使用相同的域模型并不简单，且不应尝试这样做。</span><span class="sxs-lookup"><span data-stu-id="ff973-118">Having the same domain model for relational databases or NoSQL databases is not simple, and you should not try to do it.</span></span> <span data-ttu-id="ff973-119">设计模型必须真正了解数据在每个特定数据库中的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ff973-119">You really have to design your model with an understanding of how the data is going to be used in each particular database.</span></span>

<span data-ttu-id="ff973-120">使用 NoSQL 数据库的一项优势是实体更加非规范化，所以不用设置表映射。</span><span class="sxs-lookup"><span data-stu-id="ff973-120">A benefit when using NoSQL databases is that the entities are more denormalized, so you do not set a table mapping.</span></span> <span data-ttu-id="ff973-121">域模型较使用关系数据库时更加灵活。</span><span class="sxs-lookup"><span data-stu-id="ff973-121">Your domain model can be more flexible than when using a relational database.</span></span>

<span data-ttu-id="ff973-122">当基于聚合设计域模型时，移至 NoSQL 和面向文档的数据库可能比使用关系数据库更容易，因为设计的聚合类似于面向文档的数据库中的序列化文档。</span><span class="sxs-lookup"><span data-stu-id="ff973-122">When you design your domain model based on aggregates, moving to NoSQL and document-oriented databases might be even easier than using a relational database, because the aggregates you design are similar to serialized documents in a document-oriented database.</span></span> <span data-ttu-id="ff973-123">然后，可以在这些“包”中包含该聚合可能需要的所有信息。</span><span class="sxs-lookup"><span data-stu-id="ff973-123">Then you can include in those "bags" all the information you might need for that aggregate.</span></span>

<span data-ttu-id="ff973-124">例如，以下 JSON 代码是使用面向文档的数据库时，一个实现订单聚合的示例。</span><span class="sxs-lookup"><span data-stu-id="ff973-124">For instance, the following JSON code is a sample implementation of an order aggregate when using a document-oriented database.</span></span> <span data-ttu-id="ff973-125">它与在 eShopOnContainers 示例中实现的订单聚合类似，但未在下方使用 EF Core。</span><span class="sxs-lookup"><span data-stu-id="ff973-125">It is similar to the order aggregate we implemented in the eShopOnContainers sample, but without using EF Core underneath.</span></span>

```json
{
    "id": "2017001",
    "orderDate": "2/25/2017",
    "buyerId": "1234567",
    "address": [
        {
        "street": "100 One Microsoft Way",
        "city": "Redmond",
        "state": "WA",
        "zip": "98052",
        "country": "U.S."
        }
    ],
    "orderItems": [
        {"id": 20170011, "productId": "123456", "productName": ".NET T-Shirt",
        "unitPrice": 25, "units": 2, "discount": 0},
        {"id": 20170012, "productId": "123457", "productName": ".NET Mug",
        "unitPrice": 15, "units": 1, "discount": 0}
    ]
}
```

## <a name="introduction-to-azure-cosmos-db-and-the-native-cosmos-db-api"></a><span data-ttu-id="ff973-126">Azure Cosmos DB 和本机 Cosmos DB API 简介</span><span class="sxs-lookup"><span data-stu-id="ff973-126">Introduction to Azure Cosmos DB and the native Cosmos DB API</span></span>

<span data-ttu-id="ff973-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) 是 Microsoft 针对任务关键型应用程序的全球分布式数据库服务。</span><span class="sxs-lookup"><span data-stu-id="ff973-127">[Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/introduction) is Microsoft's globally distributed database service for mission-critical applications.</span></span> <span data-ttu-id="ff973-128">Azure Cosmos DB 提供[统包全局分发](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally)、全球范围内[吞吐量和存储的弹性扩展](https://docs.microsoft.com/azure/cosmos-db/partition-data)、99% 的情况下低至个位数的毫秒延迟、[五种定义完善的一致性级别](https://docs.microsoft.com/azure/cosmos-db/consistency-levels)以及有保证的高可用性，所有这些均由[业界领先的 SLA](https://azure.microsoft.com/support/legal/sla/cosmos-db/) 提供支持。</span><span class="sxs-lookup"><span data-stu-id="ff973-128">Azure Cosmos DB provides [turn-key global distribution](https://docs.microsoft.com/azure/cosmos-db/distribute-data-globally), [elastic scaling of throughput and storage](https://docs.microsoft.com/azure/cosmos-db/partition-data) worldwide, single-digit millisecond latencies at the 99th percentile, [five well-defined consistency levels](https://docs.microsoft.com/azure/cosmos-db/consistency-levels), and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/).</span></span> <span data-ttu-id="ff973-129">Azure Cosmos DB [自动为数据编制索引](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf)，无需用户处理架构和管理索引。</span><span class="sxs-lookup"><span data-stu-id="ff973-129">Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management.</span></span> <span data-ttu-id="ff973-130">它采用多模型，并支持文档、键值、图和分栏式数据模型。</span><span class="sxs-lookup"><span data-stu-id="ff973-130">It is multi-model and supports document, key-value, graph, and columnar data models.</span></span>

![显示 Azure Cosmos DB 全局分发的关系图。](./media/nosql-database-persistence-infrastructure/azure-cosmos-db-global-distribution.png)

<span data-ttu-id="ff973-132">**图 7-19**。</span><span class="sxs-lookup"><span data-stu-id="ff973-132">**Figure 7-19**.</span></span> <span data-ttu-id="ff973-133">Azure Cosmos DB 全局分发</span><span class="sxs-lookup"><span data-stu-id="ff973-133">Azure Cosmos DB global distribution</span></span>

<span data-ttu-id="ff973-134">使用 C\# 模型实现 Azure Cosmos DB API 使用的聚合时，该聚合可类似于结合 EF Core 使用的 C\# POCO 类。</span><span class="sxs-lookup"><span data-stu-id="ff973-134">When you use a C\# model to implement the aggregate to be used by the Azure Cosmos DB API, the aggregate can be similar to the C\# POCO classes used with EF Core.</span></span> <span data-ttu-id="ff973-135">区别在于从应用程序和基础结构层使用它们的方式，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="ff973-135">The difference is in the way to use them from the application and infrastructure layers, as in the following code:</span></span>

```csharp
// C# EXAMPLE OF AN ORDER AGGREGATE BEING PERSISTED WITH AZURE COSMOS DB API
// *** Domain Model Code ***
// Aggregate: Create an Order object with its child entities and/or value objects.
// Then, use AggregateRoot's methods to add the nested objects so invariants and
// logic is consistent across the nested properties (value objects and entities).

Order orderAggregate = new Order
{
    Id = "2017001",
    OrderDate = new DateTime(2005, 7, 1),
    BuyerId = "1234567",
    PurchaseOrderNumber = "PO18009186470"
}

Address address = new Address
{
    Street = "100 One Microsoft Way",
    City = "Redmond",
    State = "WA",
    Zip = "98052",
    Country = "U.S."
}

orderAggregate.UpdateAddress(address);

OrderItem orderItem1 = new OrderItem
{
    Id = 20170011,
    ProductId = "123456",
    ProductName = ".NET T-Shirt",
    UnitPrice = 25,
    Units = 2,
    Discount = 0;
};

//Using methods with domain logic within the entity. No anemic-domain model
orderAggregate.AddOrderItem(orderItem1);
// *** End of Domain Model Code ***

// *** Infrastructure Code using Cosmos DB Client API ***
Uri collectionUri = UriFactory.CreateDocumentCollectionUri(databaseName,
    collectionName);

await client.CreateDocumentAsync(collectionUri, orderAggregate);

// As your app evolves, let's say your object has a new schema. You can insert
// OrderV2 objects without any changes to the database tier.
Order2 newOrder = GetOrderV2Sample("IdForSalesOrder2");
await client.CreateDocumentAsync(collectionUri, newOrder);
```

<span data-ttu-id="ff973-136">可以看到，使用域模型的方式可与当基础架构为 EF 时在域模型层中使用它的方式类似。</span><span class="sxs-lookup"><span data-stu-id="ff973-136">You can see that the way you work with your domain model can be similar to the way you use it in your domain model layer when the infrastructure is EF.</span></span> <span data-ttu-id="ff973-137">仍使用相同的聚合根方法，确保聚合内的一致性、不变量和验证。</span><span class="sxs-lookup"><span data-stu-id="ff973-137">You still use the same aggregate root methods to ensure consistency, invariants, and validations within the aggregate.</span></span>

<span data-ttu-id="ff973-138">但是，当将模型保存到 NoSQL 数据库时，与 EF Core 代码或与关系数据库相关的任何其他代码相比，该代码和 API 会发生显著变化。</span><span class="sxs-lookup"><span data-stu-id="ff973-138">However, when you persist your model into the NoSQL database, the code and API change dramatically compared to EF Core code or any other code related to relational databases.</span></span>

## <a name="implement-net-code-targeting-mongodb-and-azure-cosmos-db"></a><span data-ttu-id="ff973-139">实现针对 MongoDB 和 Azure Cosmos DB 的 .NET 代码</span><span class="sxs-lookup"><span data-stu-id="ff973-139">Implement .NET code targeting MongoDB and Azure Cosmos DB</span></span>

### <a name="use-azure-cosmos-db-from-net-containers"></a><span data-ttu-id="ff973-140">从 .NET 容器使用 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="ff973-140">Use Azure Cosmos DB from .NET containers</span></span>

<span data-ttu-id="ff973-141">可以像从其他任何 .NET 应用程序一样，从运行在容器中的 .NET 代码访问 Azure Cosmos DB 数据库。</span><span class="sxs-lookup"><span data-stu-id="ff973-141">You can access Azure Cosmos DB databases from .NET code running in containers, like from any other .NET application.</span></span> <span data-ttu-id="ff973-142">例如，实现 eShopOnContainers 中的 Locations.API 和 Marketing.API 微服务，这样它们就可以使用 Azure Cosmos DB 数据库。</span><span class="sxs-lookup"><span data-stu-id="ff973-142">For instance, the Locations.API and Marketing.API microservices in eShopOnContainers are implemented so they can consume Azure Cosmos DB databases.</span></span>

<span data-ttu-id="ff973-143">但是，从 Docker 开发环境的角度来看，Azure Cosmos DB 存在限制。</span><span class="sxs-lookup"><span data-stu-id="ff973-143">However, there’s a limitation in Azure Cosmos DB from a Docker development environment point of view.</span></span> <span data-ttu-id="ff973-144">即使有可以在本地开发计算机上运行的本地 [Azure Cosmos DB 仿真器](https://docs.microsoft.com/azure/cosmos-db/local-emulator)，它也仅支持 Windows。</span><span class="sxs-lookup"><span data-stu-id="ff973-144">Even though there’s an on-premises [Azure Cosmos DB Emulator](https://docs.microsoft.com/azure/cosmos-db/local-emulator) that can run in a local development machine, it only supports Windows.</span></span> <span data-ttu-id="ff973-145">不支持 Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="ff973-145">Linux and macOS aren't supported.</span></span>

<span data-ttu-id="ff973-146">此外，也可能在 Docker 上运行此仿真器，但仅在 Windows 容器上运行，而不在 Linux 容器上运行。</span><span class="sxs-lookup"><span data-stu-id="ff973-146">There's also the possibility to run this emulator on Docker, but just on Windows Containers, not with Linux Containers.</span></span> <span data-ttu-id="ff973-147">如果将应用程序部署为 Linux 容器，这对开发环境来说从一开始就是一个障碍，因为目前无法同时在用于 Windows 的 Docker 上部署 Linux 和 Windows 容器。</span><span class="sxs-lookup"><span data-stu-id="ff973-147">That's an initial handicap for the development environment if your application is deployed as Linux containers, since, currently, you can't deploy Linux and Windows Containers on Docker for Windows at the same time.</span></span> <span data-ttu-id="ff973-148">所有正在部署的容器都必须适用于 Linux 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="ff973-148">Either all containers being deployed have to be for Linux or for Windows.</span></span>

<span data-ttu-id="ff973-149">对于开发/测试解决方案，更为直接且理想的部署是能够将数据库系统作为容器与自定义容器一起部署，这样开发/测试环境就始终一致。</span><span class="sxs-lookup"><span data-stu-id="ff973-149">The ideal and more straightforward deployment for a dev/test solution is to be able to deploy your database systems as containers along with your custom containers so your dev/test environments are always consistent.</span></span>

### <a name="use-mongodb-api-for-local-devtest-linuxwindows-containers-plus-azure-cosmos-db"></a><span data-ttu-id="ff973-150">将 MongoDB API 用于本地开发/测试 Linux/Windows 容器以及 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="ff973-150">Use MongoDB API for local dev/test Linux/Windows containers plus Azure Cosmos DB</span></span>

<span data-ttu-id="ff973-151">Cosmos DB 数据库支持 .NET 的 MongoDB API 以及本地 MongoDB 网络协议。</span><span class="sxs-lookup"><span data-stu-id="ff973-151">Cosmos DB databases support MongoDB API for .NET as well as the native MongoDB wire protocol.</span></span> <span data-ttu-id="ff973-152">这意味着通过使用现有的驱动程序，为 MongoDB 编写的应用程序现在可以与 Cosmos DB 通信，并且可使用 Cosmos DB 数据库而非 MongoDB 数据库，如图 7-20 所示。</span><span class="sxs-lookup"><span data-stu-id="ff973-152">This means that by using existing drivers, your application written for MongoDB can now communicate with Cosmos DB and use Cosmos DB databases instead of MongoDB databases, as shown in Figure 7-20.</span></span>

![显示 Cosmos DB 支持 .NET 和 MongoDB Wire Protocol 的关系图。](./media/nosql-database-persistence-infrastructure/mongodb-api-wire-protocol.png)

<span data-ttu-id="ff973-154">**图 7-20**。</span><span class="sxs-lookup"><span data-stu-id="ff973-154">**Figure 7-20**.</span></span> <span data-ttu-id="ff973-155">使用 MongoDB API 和协议访问 Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="ff973-155">Using MongoDB API and protocol to access Azure Cosmos DB</span></span>

<span data-ttu-id="ff973-156">这对于含有 Linux 容器的 Docker 环境中的概念证明来说是一种非常便捷的方法，因为 [MongoDB Docker 映像](https://hub.docker.com/r/_/mongo/)是一种支持 Docker Linux 容器和 Docker Windows 容器的多体系映像。</span><span class="sxs-lookup"><span data-stu-id="ff973-156">This is a very convenient approach for proof of concepts in Docker environments with Linux containers because the [MongoDB Docker image](https://hub.docker.com/r/_/mongo/) is a multi-arch image that supports Docker Linux containers and Docker Windows containers.</span></span>

<span data-ttu-id="ff973-157">如下图所示，通过使用 MongoDB API，eShopOnContainers 支持适用于本地开发环境的 MongoDB Linux 和 Windows 容器，随后只需[将 MongoDB 连接字符串更改为指向 Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account)，即可作为 Azure Cosmos DB 移至可伸缩的 PaaS 云解决方案。</span><span class="sxs-lookup"><span data-stu-id="ff973-157">As shown in the following image, by using the MongoDB API, eShopOnContainers supports MongoDB Linux and Windows containers for the local development environment but then, you can move to a scalable, PaaS cloud solution as Azure Cosmos DB by simply [changing the MongoDB connection string to point to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

![显示 eShopOnContainers 中的位置微服务可以使用 Cosmos DB 或 Mongo DB 的关系图。](./media/nosql-database-persistence-infrastructure/eshoponcontainers-mongodb-containers.png)

<span data-ttu-id="ff973-159">**图 7-21**。</span><span class="sxs-lookup"><span data-stu-id="ff973-159">**Figure 7-21**.</span></span> <span data-ttu-id="ff973-160">使用用于 dev-env 或 Azure Cosmos DB 的 MongoDB 容器进行生产的 eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ff973-160">eShopOnContainers using MongoDB containers for dev-env or Azure Cosmos DB for production</span></span>

<span data-ttu-id="ff973-161">生产 Azure Cosmos DB 将作为 PaaS 和可扩展服务在 Azure 云中运行。</span><span class="sxs-lookup"><span data-stu-id="ff973-161">The production Azure Cosmos DB would be running in Azure's cloud as a PaaS and scalable service.</span></span>

<span data-ttu-id="ff973-162">自定义 .NET Core 容器可以在本地开发 Docker 主机（在 Windows 10 计算机上使用用于 Windows 的 Docker）上运行，也可以被部署到生产环境中，如 Azure AKS 中的 Kubernetes 或 Azure Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="ff973-162">Your custom .NET Core containers can run on a local development Docker host (that is using Docker for Windows in a Windows 10 machine) or be deployed into a production environment, like Kubernetes in Azure AKS or Azure Service Fabric.</span></span> <span data-ttu-id="ff973-163">在第二个环境中，只需部署 .NET Core 自定义容器，而不是 MongoDB 容器，因为将在云中使用 Azure Cosmos DB 来处理生产中的数据。</span><span class="sxs-lookup"><span data-stu-id="ff973-163">In this second environment, you would deploy only the .NET Core custom containers but not the MongoDB container since you'd be using Azure Cosmos DB in the cloud for handling the data in production.</span></span>

<span data-ttu-id="ff973-164">使用 MongoDB API 的明显好处是解决方案可以在数据库引擎、MongoDB 或 Azure Cosmos DB 中运行，因此要迁移到不同环境应该很容易。</span><span class="sxs-lookup"><span data-stu-id="ff973-164">A clear benefit of using the MongoDB API is that your solution could run in both database engines, MongoDB or Azure Cosmos DB, so migrations to different environments should be easy.</span></span> <span data-ttu-id="ff973-165">但是，有时为充分利用特定数据库引擎的功能，使用本机 API（即本机 Cosmos DB API）是值得的。</span><span class="sxs-lookup"><span data-stu-id="ff973-165">However, sometimes it is worthwhile to use a native API (that is the native Cosmos DB API) in order to take full advantage of the capabilities of a specific database engine.</span></span>

<span data-ttu-id="ff973-166">若要进一步比较在云中仅使用 MongoDB 和 Cosmos DB 的差异，请参阅此页中[使用 Azure Cosmos DB 的好处](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction)。</span><span class="sxs-lookup"><span data-stu-id="ff973-166">For further comparison between simply using MongoDB versus Cosmos DB in the cloud, see the [Benefits of using Azure Cosmos DB in this page](https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction).</span></span>

### <a name="analyze-your-approach-for-production-applications-mongodb-api-vs-cosmos-db-api"></a><span data-ttu-id="ff973-167">分析适用于生产应用程序的方法：MongoDB API vs.Cosmos DB API</span><span class="sxs-lookup"><span data-stu-id="ff973-167">Analyze your approach for production applications: MongoDB API vs. Cosmos DB API</span></span>

<span data-ttu-id="ff973-168">我们在 eShopOnContainers 中使用 MongoDB API，因为我们的首要任务是从根本上拥有使用 NoSQL 数据库的一致开发/测试环境，该数据库也可以与 Azure Cosmos DB 一起使用。</span><span class="sxs-lookup"><span data-stu-id="ff973-168">In eShopOnContainers, we're using MongoDB API because our priority was fundamentally to have a consistent dev/test environment using a NoSQL database that could also work with Azure Cosmos DB.</span></span>

<span data-ttu-id="ff973-169">但是，如果打算使用 MongoDB API 访问 Azure 中的 Azure Cosmos 数据库以获取生产应用程序，则应该分析与使用本机 Azure Cosmos DB API 相比，使用 MongoDB API 访问 Azure Cosmos DB 数据库时的功能和性能差异。</span><span class="sxs-lookup"><span data-stu-id="ff973-169">However, if you planning to use MongoDB API to access Azure Cosmos DB in Azure for production applications, you should analyze the differences in capabilities and performance when using MongoDB API to access Azure Cosmos DB databases compared to using the native Azure Cosmos DB API.</span></span> <span data-ttu-id="ff973-170">如果相似，则可以使用 MongoDB API，并且可以获取同时支持两个 NoSQL 数据库引擎的好处。</span><span class="sxs-lookup"><span data-stu-id="ff973-170">If it is similar you can use MongoDB API and you get the benefit of supporting two NoSQL database engines at the same time.</span></span>

<span data-ttu-id="ff973-171">此外，也可以将 MongoDB 群集作为 Azure 云中的生产数据库与 [MongoDB Azure 服务](https://www.mongodb.com/scale/mongodb-azure-service)一起使用。</span><span class="sxs-lookup"><span data-stu-id="ff973-171">You could also use MongoDB clusters as the production database in Azure's cloud, too, with [MongoDB Azure Service](https://www.mongodb.com/scale/mongodb-azure-service).</span></span> <span data-ttu-id="ff973-172">但这不是由 Microsoft 提供的 PaaS 服务。</span><span class="sxs-lookup"><span data-stu-id="ff973-172">But that is not a PaaS service provided by Microsoft.</span></span> <span data-ttu-id="ff973-173">在这种情况下，Azure 只托管来自 MongoDB 的解决方案。</span><span class="sxs-lookup"><span data-stu-id="ff973-173">In this case, Azure is just hosting that solution coming from MongoDB.</span></span>

<span data-ttu-id="ff973-174">基本上，这只是指出不应总是针对 Azure Cosmos DB 使用 MongoDB API 的免责声明，就像在 eShopOnContainers 中所做的那样，因为这对于 Linux 容器来说是一个方便的选择。</span><span class="sxs-lookup"><span data-stu-id="ff973-174">Basically, this is just a disclaimer stating that you shouldn't always use MongoDB API against Azure Cosmos DB, as we did in eShopOnContainers because it was a convenient choice for Linux containers.</span></span> <span data-ttu-id="ff973-175">应根据特定需求以及需要对生产应用程序执行的测试来做出决定。</span><span class="sxs-lookup"><span data-stu-id="ff973-175">The decision should be based on the specific needs and tests you need to do for your production application.</span></span>

### <a name="the-code-use-mongodb-api-in-net-core-applications"></a><span data-ttu-id="ff973-176">代码：在 .NET Core 应用程序中使用 MongoDB API</span><span class="sxs-lookup"><span data-stu-id="ff973-176">The code: Use MongoDB API in .NET Core applications</span></span>

<span data-ttu-id="ff973-177">适用于 .NET 的 MongoDB API 是基于 NuGet 包的，你需要添加到类似于下图所示的 Locations.API 项目中。</span><span class="sxs-lookup"><span data-stu-id="ff973-177">MongoDB API for .NET is based on NuGet packages that you need to add to your projects, like in the Locations.API project shown in the following figure.</span></span>

![MongoDB NuGet 包中的依赖项的屏幕截图。](./media/nosql-database-persistence-infrastructure/mongodb-api-nuget-packages.png)

<span data-ttu-id="ff973-179">**图 7-22**。</span><span class="sxs-lookup"><span data-stu-id="ff973-179">**Figure 7-22**.</span></span> <span data-ttu-id="ff973-180">.NET Core 项目中的 MongoDB API NuGet 包引用</span><span class="sxs-lookup"><span data-stu-id="ff973-180">MongoDB API NuGet packages references in a .NET Core project</span></span>

<span data-ttu-id="ff973-181">让我们来研究下面几节中的代码。</span><span class="sxs-lookup"><span data-stu-id="ff973-181">Let's investigate the code in the following sections.</span></span>

#### <a name="a-model-used-by-mongodb-api"></a><span data-ttu-id="ff973-182">MongoDB API 使用的模型</span><span class="sxs-lookup"><span data-stu-id="ff973-182">A Model used by MongoDB API</span></span>

<span data-ttu-id="ff973-183">首先，需要定义一个在应用程序内存空间中保存来自数据库的数据的模型。</span><span class="sxs-lookup"><span data-stu-id="ff973-183">First, you need to define a model that will hold the data coming from the database in your application's memory space.</span></span> <span data-ttu-id="ff973-184">以下是 eShopOnContainers 中用于定位的模型示例。</span><span class="sxs-lookup"><span data-stu-id="ff973-184">Here's an example of the model used for Locations at eShopOnContainers.</span></span>

```csharp
using MongoDB.Bson;
using MongoDB.Bson.Serialization.Attributes;
using MongoDB.Driver.GeoJsonObjectModel;
using System.Collections.Generic;

public class Locations
{
    [BsonId]
    [BsonRepresentation(BsonType.ObjectId)]
    public string Id { get; set; }
    public int LocationId { get; set; }
    public string Code { get; set; }
    [BsonRepresentation(BsonType.ObjectId)]
    public string Parent_Id { get; set; }
    public string Description { get; set; }
    public double Latitude { get; set; }
    public double Longitude { get; set; }
    public GeoJsonPoint<GeoJson2DGeographicCoordinates> Location
                                                             { get; private set; }
    public GeoJsonPolygon<GeoJson2DGeographicCoordinates> Polygon
                                                             { get; private set; }
    public void SetLocation(double lon, double lat) => SetPosition(lon, lat);
    public void SetArea(List<GeoJson2DGeographicCoordinates> coordinatesList)
                                                    => SetPolygon(coordinatesList);

    private void SetPosition(double lon, double lat)
    {
        Latitude = lat;
        Longitude = lon;
        Location = new GeoJsonPoint<GeoJson2DGeographicCoordinates>(
            new GeoJson2DGeographicCoordinates(lon, lat));
    }

    private void SetPolygon(List<GeoJson2DGeographicCoordinates> coordinatesList)
    {
        Polygon = new GeoJsonPolygon<GeoJson2DGeographicCoordinates>(
                  new GeoJsonPolygonCoordinates<GeoJson2DGeographicCoordinates>(
                  new GeoJsonLinearRingCoordinates<GeoJson2DGeographicCoordinates>(
                                                                 coordinatesList)));
    }
}
```

<span data-ttu-id="ff973-185">可以看到来自 MongoDB NuGet 包的一些属性和类型。</span><span class="sxs-lookup"><span data-stu-id="ff973-185">You can see there are a few attributes and types coming from the MongoDB NuGet packages.</span></span>

<span data-ttu-id="ff973-186">NoSQL 数据库通常非常适合处理非关系分层数据。</span><span class="sxs-lookup"><span data-stu-id="ff973-186">NoSQL databases are usually very well suited for working with non-relational hierarchical data.</span></span> <span data-ttu-id="ff973-187">在此示例中，我们使用专用于地理位置的 MongoDB 类型，例如 `GeoJson2DGeographicCoordinates`。</span><span class="sxs-lookup"><span data-stu-id="ff973-187">In this example, we are using MongoDB types especially made for geo-locations, like `GeoJson2DGeographicCoordinates`.</span></span>

#### <a name="retrieve-the-database-and-the-collection"></a><span data-ttu-id="ff973-188">检索数据库和集合</span><span class="sxs-lookup"><span data-stu-id="ff973-188">Retrieve the database and the collection</span></span>

<span data-ttu-id="ff973-189">在 eShopOnContainers 中，我们已经创建了自定义数据库上下文，并在其中实现代码来检索数据库和 MongoCollections，如以下代码所示。</span><span class="sxs-lookup"><span data-stu-id="ff973-189">In eShopOnContainers, we have created a custom database context where we implement the code to retrieve the database and the MongoCollections, as in the following code.</span></span>

```csharp
public class LocationsContext
{
    private readonly IMongoDatabase _database = null;

    public LocationsContext(IOptions<LocationSettings> settings)
    {
        var client = new MongoClient(settings.Value.ConnectionString);
        if (client != null)
            _database = client.GetDatabase(settings.Value.Database);
    }

    public IMongoCollection<Locations> Locations
    {
        get
        {
            return _database.GetCollection<Locations>("Locations");
        }
    }
}
```

#### <a name="retrieve-the-data"></a><span data-ttu-id="ff973-190">检索数据</span><span class="sxs-lookup"><span data-stu-id="ff973-190">Retrieve the data</span></span>

<span data-ttu-id="ff973-191">在 C＃ 代码中，如 Web API 控制器或自定义存储库实现，可在查询 MongoDB API 时，编写如下代码。</span><span class="sxs-lookup"><span data-stu-id="ff973-191">In C# code, like Web API controllers or custom Repositories implementation, you can write similar code to the following when querying through the MongoDB API.</span></span> <span data-ttu-id="ff973-192">请注意，`_context` 对象是之前的 `LocationsContext` 类的实例。</span><span class="sxs-lookup"><span data-stu-id="ff973-192">Note that the `_context` object is an instance of the previous `LocationsContext` class.</span></span>

```csharp
public async Task<Locations> GetAsync(int locationId)
{
    var filter = Builders<Locations>.Filter.Eq("LocationId", locationId);
    return await _context.Locations
                            .Find(filter)
                            .FirstOrDefaultAsync();
}
```

#### <a name="use-an-env-var-in-the-docker-composeoverrideyml-file-for-the-mongodb-connection-string"></a><span data-ttu-id="ff973-193">在 docker-compose.override.yml 文件中对 MongoDB 连接字符串使用 env-var</span><span class="sxs-lookup"><span data-stu-id="ff973-193">Use an env-var in the docker-compose.override.yml file for the MongoDB connection string</span></span>

<span data-ttu-id="ff973-194">创建 MongoClient 对象时，需要一个基本参数，该参数恰好是指向正确数据库的 `ConnectionString` 参数。</span><span class="sxs-lookup"><span data-stu-id="ff973-194">When creating a MongoClient object, it needs a fundamental parameter which is precisely the `ConnectionString` parameter pointing to the right database.</span></span> <span data-ttu-id="ff973-195">对于 eShopOnContainers，连接字符串可以指向本地 MongoDB Docker 容器或“生产”Azure Cosmos DB 数据库。</span><span class="sxs-lookup"><span data-stu-id="ff973-195">In the case of eShopOnContainers, the connection string can point to a local MongoDB Docker container or to a "production" Azure Cosmos DB database.</span></span>  <span data-ttu-id="ff973-196">该连接字符串来自在 `docker-compose.override.yml` 文件中定义的环境变量，该文件在使用 docker-compose 或 Visual Studio 进行部署时使用，如以下 yml 代码所示。</span><span class="sxs-lookup"><span data-stu-id="ff973-196">That connection string comes from the environment variables defined in the `docker-compose.override.yml` files used when deploying with docker-compose or Visual Studio, as in the following yml code.</span></span>

```yml
# docker-compose.override.yml
version: '3.4'
services:
  # Other services
  locations-api:
    environment:
      # Other settings
      - ConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}

```

<span data-ttu-id="ff973-197">`ConnectionString` 环境变量通过以下方式解析：如果使用 Azure Cosmos DB 连接字符串在 `.env` 文件中定义该 `ESHOP_AZURE_COSMOSDB` 全局变量，则将使用它访问云中的 Azure Cosmos DB 数据库。</span><span class="sxs-lookup"><span data-stu-id="ff973-197">The `ConnectionString` environment variable is resolved this way: If the `ESHOP_AZURE_COSMOSDB` global variable is defined in the `.env` file with the Azure Cosmos DB connection string, it will use it to access the Azure Cosmos DB database in the cloud.</span></span> <span data-ttu-id="ff973-198">如果未定义，它将采用 `mongodb://nosqldata` 值并使用 MongoDB 开发容器。</span><span class="sxs-lookup"><span data-stu-id="ff973-198">If it’s not defined, it will take the `mongodb://nosqldata` value and use the development MongoDB container.</span></span>

<span data-ttu-id="ff973-199">以下代码演示带有 Azure Cosmos DB 连接字符串全局环境变量的 `.env` 文件，如在 eShopOnContainers 中实现一样：</span><span class="sxs-lookup"><span data-stu-id="ff973-199">The following code shows the `.env` file with the Azure Cosmos DB connection string global environment variable, as implemented in eShopOnContainers:</span></span>

```yml
# .env file, in eShopOnContainers root folder
# Other Docker environment variables

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost
ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=<YourDockerHostIP>

#ESHOP_AZURE_COSMOSDB=<YourAzureCosmosDBConnData>

#Other environment variables for additional Azure infrastructure assets
#ESHOP_AZURE_REDIS_BASKET_DB=<YourAzureRedisBasketInfo>
#ESHOP_AZURE_STORAGE_CATALOG_URL=<YourAzureStorage_Catalog_BLOB_URL>
#ESHOP_AZURE_SERVICE_BUS=<YourAzureServiceBusInfo>
```

<span data-ttu-id="ff973-200">取消注释 ESHOP_AZURE_COSMOSDB 行，并使用从 Azure 门户获得的 Azure Cosmos DB 连接字符串进行更新，如[将 MongoDB 应用程序连接到 Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account) 中所述。</span><span class="sxs-lookup"><span data-stu-id="ff973-200">Uncomment the ESHOP_AZURE_COSMOSDB line and update it with your Azure Cosmos DB connection string obtained from the Azure portal as explained in [Connect a MongoDB application to Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account).</span></span>

<span data-ttu-id="ff973-201">如果 `ESHOP_AZURE_COSMOSDB` 全局变量为空，则意味着它在 `.env` 文件中已被注释掉，那么容器将使用默认的 MongoDB 连接字符串。</span><span class="sxs-lookup"><span data-stu-id="ff973-201">If the `ESHOP_AZURE_COSMOSDB` global variable is empty, meaning it's commented out in the `.env` file, then the container uses a default MongoDB connection string.</span></span> <span data-ttu-id="ff973-202">此连接字符串指向部署在 eShopOnContainers 中的本地 MongoDB 容器，该容器名为 `nosqldata`，并在 docker-compose 文件中定义，如以下 .yml 代码所示：</span><span class="sxs-lookup"><span data-stu-id="ff973-202">This connection string points to the local MongoDB container deployed in eShopOnContainers that is named `nosqldata` and was defined at the docker-compose file, as shown in the following .yml code:</span></span>

``` yml
# docker-compose.yml
version: '3.4'
services:
  # ...Other services...
  nosqldata:
    image: mongo
```

#### <a name="additional-resources"></a><span data-ttu-id="ff973-203">其他资源</span><span class="sxs-lookup"><span data-stu-id="ff973-203">Additional resources</span></span>

- <span data-ttu-id="ff973-204">**Modeling document data for NoSQL databases**（针对 NoSQL 数据库的文档数据建模） </span><span class="sxs-lookup"><span data-stu-id="ff973-204">**Modeling document data for NoSQL databases** </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/modeling-data>

- <span data-ttu-id="ff973-205">**Vaughn Vernon。The Ideal Domain-Driven Design Aggregate Store?** （理想的域驱动设计聚合存储？）</span><span class="sxs-lookup"><span data-stu-id="ff973-205">**Vaughn Vernon. The Ideal Domain-Driven Design Aggregate Store?**</span></span> \
  <https://kalele.io/blog-posts/the-ideal-domain-driven-design-aggregate-store/>

- <span data-ttu-id="ff973-206">**Introduction to Azure Cosmos DB:API for MongoDB**（Azure Cosmos DB 简介：适用于 MongoDB 的 API）  </span><span class="sxs-lookup"><span data-stu-id="ff973-206">**Introduction to Azure Cosmos DB: API for MongoDB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-introduction>

- <span data-ttu-id="ff973-207">**Azure Cosmos DB：Build a MongoDB API web app with .NET and the Azure portal**（使用 .NET 和 Azure 门户生成 MongoDB API Web 应用）  </span><span class="sxs-lookup"><span data-stu-id="ff973-207">**Azure Cosmos DB: Build a MongoDB API web app with .NET and the Azure portal**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/create-mongodb-dotnet>

- <span data-ttu-id="ff973-208">**Use the Azure Cosmos DB Emulator for local development and testing**（将 Azure Cosmos DB 仿真器用于本地开发和测试）  </span><span class="sxs-lookup"><span data-stu-id="ff973-208">**Use the Azure Cosmos DB Emulator for local development and testing**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/local-emulator>

- <span data-ttu-id="ff973-209">**Connect a MongoDB application to Azure Cosmos DB**（将 MongoDB 应用程序连接到 Azure Cosmos DB）  </span><span class="sxs-lookup"><span data-stu-id="ff973-209">**Connect a MongoDB application to Azure Cosmos DB**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/connect-mongodb-account>

- <span data-ttu-id="ff973-210">**The Cosmos DB Emulator Docker image (Windows Container)** （Cosmos DB 仿真器 Docker 映像 [Windows 容器]）  </span><span class="sxs-lookup"><span data-stu-id="ff973-210">**The Cosmos DB Emulator Docker image (Windows Container)**  </span></span>\
  <https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator/>

- <span data-ttu-id="ff973-211">**The MongoDB Docker image (Linux and Windows Container)** （MongoDB Docker 映像 [Linux 和 Windows 容器]）  </span><span class="sxs-lookup"><span data-stu-id="ff973-211">**The MongoDB Docker image (Linux and Windows Container)**  </span></span>\
  <https://hub.docker.com/_/mongo/>

- <span data-ttu-id="ff973-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB:API for MongoDB account**（将 MongoChef [Studio 3T] 用于 Azure Cosmos DB：适用于 MongoDB 的 API 帐户）  </span><span class="sxs-lookup"><span data-stu-id="ff973-212">**Use MongoChef (Studio 3T) with an Azure Cosmos DB: API for MongoDB account**  </span></span>\
  <https://docs.microsoft.com/azure/cosmos-db/mongodb-mongochef>

>[!div class="step-by-step"]
><span data-ttu-id="ff973-213">[上一页](infrastructure-persistence-layer-implementation-entity-framework-core.md)
>[下一页](microservice-application-layer-web-api-design.md)</span><span class="sxs-lookup"><span data-stu-id="ff973-213">[Previous](infrastructure-persistence-layer-implementation-entity-framework-core.md)
[Next](microservice-application-layer-web-api-design.md)</span></span>
