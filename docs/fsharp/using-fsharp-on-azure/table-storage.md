---
title: 通过 F# 实现 Azure 表格存储入门
description: 使用 Azure 表存储或 Azure Cosmos DB 将结构化数据存储在云中。
author: sylvanc
ms.date: 03/26/2018
ms.custom: devx-track-fsharp
ms.openlocfilehash: bf4f2e63c847e18d253fe5b6cf5dd7773c320fb7
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756203"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a><span data-ttu-id="de280-103">开始使用 Azure 表存储和 Azure Cosmos DB 表 API 使用 F\#</span><span class="sxs-lookup"><span data-stu-id="de280-103">Get started with Azure Table storage and the Azure Cosmos DB Table API using F\#</span></span>

<span data-ttu-id="de280-104">Azure 表存储是一种将结构化的 NoSQL 数据存储在云中的服务。</span><span class="sxs-lookup"><span data-stu-id="de280-104">Azure Table storage is a service that stores structured NoSQL data in the cloud.</span></span> <span data-ttu-id="de280-105">表存储是采用无架构设计的键/属性存储。</span><span class="sxs-lookup"><span data-stu-id="de280-105">Table storage is a key/attribute store with a schemaless design.</span></span> <span data-ttu-id="de280-106">因为表存储无架构，因此可以很容易地随着应用程序需求的发展使数据适应存储。</span><span class="sxs-lookup"><span data-stu-id="de280-106">Because Table storage is schemaless, it's easy to adapt your data as the needs of your application evolve.</span></span> <span data-ttu-id="de280-107">对于所有类型的应用程序，都可以快速并经济高效地访问数据。</span><span class="sxs-lookup"><span data-stu-id="de280-107">Access to data is fast and cost-effective for all kinds of applications.</span></span> <span data-ttu-id="de280-108">对于相似的数据量，表存储的成本通常显著低于传统的 SQL。</span><span class="sxs-lookup"><span data-stu-id="de280-108">Table storage is typically significantly lower in cost than traditional SQL for similar volumes of data.</span></span>

<span data-ttu-id="de280-109">可以使用表存储来存储灵活的数据集，例如 Web 应用程序的用户数据、通讯簿、设备信息，以及服务需要的任何其他类型的元数据。</span><span class="sxs-lookup"><span data-stu-id="de280-109">You can use Table storage to store flexible datasets, such as user data for web applications, address books, device information, and any other type of metadata that your service requires.</span></span> <span data-ttu-id="de280-110">可以在表中存储任意数量的实体，并且一个存储帐户可以包含任意数量的表，直至达到存储帐户的容量极限。</span><span class="sxs-lookup"><span data-stu-id="de280-110">You can store any number of entities in a table, and a storage account may contain any number of tables, up to the capacity limit of the storage account.</span></span>

<span data-ttu-id="de280-111">Azure Cosmos DB 提供了为 Azure 表存储编写的应用程序的表 API，以及需要高级功能的应用程序，例如：</span><span class="sxs-lookup"><span data-stu-id="de280-111">Azure Cosmos DB provides the Table API for applications that are written for Azure Table storage and that require premium capabilities such as:</span></span>

- <span data-ttu-id="de280-112">统包式全局分发。</span><span class="sxs-lookup"><span data-stu-id="de280-112">Turnkey global distribution.</span></span>
- <span data-ttu-id="de280-113">全球范围内专用的吞吐量。</span><span class="sxs-lookup"><span data-stu-id="de280-113">Dedicated throughput worldwide.</span></span>
- <span data-ttu-id="de280-114">99% 的情况下低至个位数的毫秒级延迟。</span><span class="sxs-lookup"><span data-stu-id="de280-114">Single-digit millisecond latencies at the 99th percentile.</span></span>
- <span data-ttu-id="de280-115">保证高可用性。</span><span class="sxs-lookup"><span data-stu-id="de280-115">Guaranteed high availability.</span></span>
- <span data-ttu-id="de280-116">自动编制辅助索引。</span><span class="sxs-lookup"><span data-stu-id="de280-116">Automatic secondary indexing.</span></span>

<span data-ttu-id="de280-117">为 Azure 表存储编写的应用程序无需更改代码便可使用表 API 迁移到 Azure Cosmos DB，并可充分利用高级功能。</span><span class="sxs-lookup"><span data-stu-id="de280-117">Applications written for Azure Table storage can migrate to Azure Cosmos DB by using the Table API with no code changes and take advantage of premium capabilities.</span></span> <span data-ttu-id="de280-118">表 API 包含可用于 .NET、Java、Python 和 Node.js 的客户端 SDK。</span><span class="sxs-lookup"><span data-stu-id="de280-118">The Table API has client SDKs available for .NET, Java, Python, and Node.js.</span></span>

<span data-ttu-id="de280-119">有关详细信息，请参阅 [Azure Cosmos DB 表 API 简介](/azure/cosmos-db/table-introduction)。</span><span class="sxs-lookup"><span data-stu-id="de280-119">For more information, see [Introduction to Azure Cosmos DB Table API](/azure/cosmos-db/table-introduction).</span></span>

## <a name="about-this-tutorial"></a><span data-ttu-id="de280-120">关于本教程</span><span class="sxs-lookup"><span data-stu-id="de280-120">About this tutorial</span></span>

<span data-ttu-id="de280-121">本教程演示如何使用 Azure 表存储或 Azure Cosmos DB 表 API 编写 F # 代码来执行一些常见任务，包括创建和删除表以及插入、更新、删除和查询表数据。</span><span class="sxs-lookup"><span data-stu-id="de280-121">This tutorial shows how to write F# code to do some common tasks using Azure Table storage or the Azure Cosmos DB Table API, including creating and deleting a table and inserting, updating, deleting, and querying table data.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="de280-122">必备知识</span><span class="sxs-lookup"><span data-stu-id="de280-122">Prerequisites</span></span>

<span data-ttu-id="de280-123">若要使用本指南，必须先 [创建 Azure 存储帐户](/azure/storage/storage-create-storage-account) 或 [Azure Cosmos DB 帐户](https://azure.microsoft.com/try/cosmosdb/)。</span><span class="sxs-lookup"><span data-stu-id="de280-123">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account) or [Azure Cosmos DB account](https://azure.microsoft.com/try/cosmosdb/).</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="de280-124">创建 F # 脚本并开始 F# 交互窗口</span><span class="sxs-lookup"><span data-stu-id="de280-124">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="de280-125">本文中的示例可用于 F # 应用程序或 F # 脚本。</span><span class="sxs-lookup"><span data-stu-id="de280-125">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="de280-126">若要创建 F # 脚本，请创建 `.fsx` 扩展名为的文件，例如 `tables.fsx` f # 开发环境中的文件。</span><span class="sxs-lookup"><span data-stu-id="de280-126">To create an F# script, create a file with the `.fsx` extension, for example `tables.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="de280-127">接下来，使用 [包管理器](package-management.md) （如 [Paket](https://fsprojects.github.io/Paket/) 或 [NuGet](https://www.nuget.org/) ） `WindowsAzure.Storage` `WindowsAzure.Storage.dll` 通过指令在脚本中安装包和引用 `#r` 。</span><span class="sxs-lookup"><span data-stu-id="de280-127">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span> <span data-ttu-id="de280-128">为 `Microsoft.WindowsAzure.ConfigurationManager` 获取 Microsoft Azure 命名空间，请再次执行此操作。</span><span class="sxs-lookup"><span data-stu-id="de280-128">Do it again for `Microsoft.WindowsAzure.ConfigurationManager` in order to get the Microsoft.Azure namespace.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="de280-129">添加命名空间声明</span><span class="sxs-lookup"><span data-stu-id="de280-129">Add namespace declarations</span></span>

<span data-ttu-id="de280-130">将下列 `open` 语句添加到 `tables.fsx` 文件顶部：</span><span class="sxs-lookup"><span data-stu-id="de280-130">Add the following `open` statements to the top of the `tables.fsx` file:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a><span data-ttu-id="de280-131">获取 Azure 存储连接字符串</span><span class="sxs-lookup"><span data-stu-id="de280-131">Get your Azure Storage connection string</span></span>

<span data-ttu-id="de280-132">如果要连接到 Azure 存储表服务，则需要为本教程提供连接字符串。</span><span class="sxs-lookup"><span data-stu-id="de280-132">If you're connecting to Azure Storage Table service, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="de280-133">可以从 Azure 门户复制连接字符串。</span><span class="sxs-lookup"><span data-stu-id="de280-133">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="de280-134">有关连接字符串的详细信息，请参阅 [配置存储连接字符串](/azure/storage/storage-configure-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="de280-134">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

### <a name="get-your-azure-cosmos-db-connection-string"></a><span data-ttu-id="de280-135">获取 Azure Cosmos DB 连接字符串</span><span class="sxs-lookup"><span data-stu-id="de280-135">Get your Azure Cosmos DB connection string</span></span>

<span data-ttu-id="de280-136">如果要连接到 Azure Cosmos DB，则需要此教程的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="de280-136">If you're connecting to Azure Cosmos DB, you'll need your connection string for this tutorial.</span></span> <span data-ttu-id="de280-137">可以从 Azure 门户复制连接字符串。</span><span class="sxs-lookup"><span data-stu-id="de280-137">You can copy your connection string from the Azure portal.</span></span> <span data-ttu-id="de280-138">在 Azure 门户的 Cosmos DB 帐户中， **Settings**  >  选择 "设置" "**连接字符串**"，并选择 "**复制**" 按钮复制主连接字符串。</span><span class="sxs-lookup"><span data-stu-id="de280-138">In the Azure portal, in your Cosmos DB account, go to **Settings** > **Connection String**, and select the **Copy** button to copy your Primary Connection String.</span></span>

<span data-ttu-id="de280-139">对于本教程，请在脚本中输入连接字符串，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="de280-139">For the tutorial, enter your connection string in your script, like the following example:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

<span data-ttu-id="de280-140">但对于实际项目， **不建议这样做** 。</span><span class="sxs-lookup"><span data-stu-id="de280-140">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="de280-141">存储帐户密钥类似于存储帐户的根密码。</span><span class="sxs-lookup"><span data-stu-id="de280-141">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="de280-142">始终要小心保护存储帐户密钥。</span><span class="sxs-lookup"><span data-stu-id="de280-142">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="de280-143">避免将其分发给其他用户、对其进行硬编码或将其保存在其他人可以访问的纯文本文件中。</span><span class="sxs-lookup"><span data-stu-id="de280-143">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="de280-144">如果你认为密钥可能已泄漏，你可以使用 Azure 门户重新生成密钥。</span><span class="sxs-lookup"><span data-stu-id="de280-144">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="de280-145">对于实际应用程序，维护存储连接字符串的最佳方式是在配置文件中。</span><span class="sxs-lookup"><span data-stu-id="de280-145">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="de280-146">若要从配置文件中提取连接字符串，可以执行以下操作：</span><span class="sxs-lookup"><span data-stu-id="de280-146">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

<span data-ttu-id="de280-147">不一定要使用 Azure Configuration Manager。</span><span class="sxs-lookup"><span data-stu-id="de280-147">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="de280-148">你还可以使用 API，例如 .NET Framework 的 `ConfigurationManager` 类型。</span><span class="sxs-lookup"><span data-stu-id="de280-148">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="de280-149">解析连接字符串</span><span class="sxs-lookup"><span data-stu-id="de280-149">Parse the connection string</span></span>

<span data-ttu-id="de280-150">若要分析连接字符串，请使用：</span><span class="sxs-lookup"><span data-stu-id="de280-150">To parse the connection string, use:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

<span data-ttu-id="de280-151">这会返回一个 `CloudStorageAccount` 。</span><span class="sxs-lookup"><span data-stu-id="de280-151">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-the-table-service-client"></a><span data-ttu-id="de280-152">创建表服务客户端</span><span class="sxs-lookup"><span data-stu-id="de280-152">Create the Table service client</span></span>

<span data-ttu-id="de280-153">`CloudTableClient`利用类，您可以检索表存储中的表和实体。</span><span class="sxs-lookup"><span data-stu-id="de280-153">The `CloudTableClient` class enables you to retrieve tables and entities in Table storage.</span></span> <span data-ttu-id="de280-154">下面是创建服务客户端的一种方法：</span><span class="sxs-lookup"><span data-stu-id="de280-154">Here's one way to create the service client:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

<span data-ttu-id="de280-155">现在，已准备好编写从表存储读取数据并将数据写入表存储的代码。</span><span class="sxs-lookup"><span data-stu-id="de280-155">Now you are ready to write code that reads data from and writes data to Table storage.</span></span>

### <a name="create-a-table"></a><span data-ttu-id="de280-156">创建表</span><span class="sxs-lookup"><span data-stu-id="de280-156">Create a table</span></span>

<span data-ttu-id="de280-157">此示例演示如何创建表（如果表已经不存在）：</span><span class="sxs-lookup"><span data-stu-id="de280-157">This example shows how to create a table if it does not already exist:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a><span data-ttu-id="de280-158">将实体添加到表</span><span class="sxs-lookup"><span data-stu-id="de280-158">Add an entity to a table</span></span>

<span data-ttu-id="de280-159">实体必须具有从继承的类型 `TableEntity` 。</span><span class="sxs-lookup"><span data-stu-id="de280-159">An entity has to have a type that inherits from `TableEntity`.</span></span> <span data-ttu-id="de280-160">您可以 `TableEntity` 采用任何喜欢的方式进行扩展，但您的类型 *必须* 具有无参数的构造函数。</span><span class="sxs-lookup"><span data-stu-id="de280-160">You can extend `TableEntity` in any way you like, but your type *must* have a parameter-less constructor.</span></span> <span data-ttu-id="de280-161">只有具有和的属性 `get` `set` 存储在 Azure 表中。</span><span class="sxs-lookup"><span data-stu-id="de280-161">Only properties that have both `get` and `set` are stored in your Azure Table.</span></span>

<span data-ttu-id="de280-162">实体的分区和行键唯一标识表中的实体。</span><span class="sxs-lookup"><span data-stu-id="de280-162">An entity's partition and row key uniquely identify the entity in the table.</span></span> <span data-ttu-id="de280-163">查询分区键相同的实体的速度快于查询分区键不同的实体的速度，但使用不同的分区键可实现更高的并行操作可伸缩性。</span><span class="sxs-lookup"><span data-stu-id="de280-163">Entities with the same partition key can be queried faster than those with different partition keys, but using diverse partition keys allows for greater scalability of parallel operations.</span></span>

<span data-ttu-id="de280-164">下面的示例 `Customer` 使用 `lastName` 作为分区键，并使用 `firstName` 作为行键。</span><span class="sxs-lookup"><span data-stu-id="de280-164">Here's an example of a `Customer` that uses the `lastName` as the partition key and the `firstName` as the row key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

<span data-ttu-id="de280-165">现在将添加 `Customer` 到表中。</span><span class="sxs-lookup"><span data-stu-id="de280-165">Now add `Customer` to the table.</span></span> <span data-ttu-id="de280-166">为此，请创建一个 `TableOperation` 对表执行的。</span><span class="sxs-lookup"><span data-stu-id="de280-166">To do so, create a `TableOperation` that executes on the table.</span></span> <span data-ttu-id="de280-167">在这种情况下，你将创建一个 `Insert` 操作。</span><span class="sxs-lookup"><span data-stu-id="de280-167">In this case, you create an `Insert` operation.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a><span data-ttu-id="de280-168">插入一批实体</span><span class="sxs-lookup"><span data-stu-id="de280-168">Insert a batch of entities</span></span>

<span data-ttu-id="de280-169">您可以使用单个写入操作将一批实体插入到表中。</span><span class="sxs-lookup"><span data-stu-id="de280-169">You can insert a batch of entities into a table using a single write operation.</span></span> <span data-ttu-id="de280-170">批处理操作允许将操作组合成单个执行，但有一些限制：</span><span class="sxs-lookup"><span data-stu-id="de280-170">Batch operations allow you to combine operations into a single execution, but they have some restrictions:</span></span>

- <span data-ttu-id="de280-171">可以在同一批处理操作中执行更新、删除和插入操作。</span><span class="sxs-lookup"><span data-stu-id="de280-171">You can perform updates, deletes, and inserts in the same batch operation.</span></span>
- <span data-ttu-id="de280-172">一个批处理操作最多可包含100个实体。</span><span class="sxs-lookup"><span data-stu-id="de280-172">A batch operation can include up to 100 entities.</span></span>
- <span data-ttu-id="de280-173">批处理操作中的所有实体都必须具有相同的分区键。</span><span class="sxs-lookup"><span data-stu-id="de280-173">All entities in a batch operation must have the same partition key.</span></span>
- <span data-ttu-id="de280-174">尽管可以在批处理操作中执行查询，但它必须是批处理中的唯一操作。</span><span class="sxs-lookup"><span data-stu-id="de280-174">While it is possible to perform a query in a batch operation, it must be the only operation in the batch.</span></span>

<span data-ttu-id="de280-175">下面是将两个插入合并为一个批处理操作的一些代码：</span><span class="sxs-lookup"><span data-stu-id="de280-175">Here's some code that combines two inserts into a batch operation:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a><span data-ttu-id="de280-176">检索分区中的所有实体</span><span class="sxs-lookup"><span data-stu-id="de280-176">Retrieve all entities in a partition</span></span>

<span data-ttu-id="de280-177">若要查询表以获取某个分区中的所有实体，请使用 `TableQuery` 对象。</span><span class="sxs-lookup"><span data-stu-id="de280-177">To query a table for all entities in a partition, use a `TableQuery` object.</span></span> <span data-ttu-id="de280-178">在这里，您将筛选 "Smith" 为分区键的实体。</span><span class="sxs-lookup"><span data-stu-id="de280-178">Here, you filter for entities where "Smith" is the partition key.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

<span data-ttu-id="de280-179">现在可以打印结果：</span><span class="sxs-lookup"><span data-stu-id="de280-179">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a><span data-ttu-id="de280-180">检索分区中的一部分实体</span><span class="sxs-lookup"><span data-stu-id="de280-180">Retrieve a range of entities in a partition</span></span>

<span data-ttu-id="de280-181">如果不想查询分区中的所有实体，则可以通过结合使用分区键筛选器与行键筛选器来指定一个范围。</span><span class="sxs-lookup"><span data-stu-id="de280-181">If you don't want to query all the entities in a partition, you can specify a range by combining the partition key filter with a row key filter.</span></span> <span data-ttu-id="de280-182">在这里，您将使用两个筛选器来获取 "Smith" 分区中的行键 (名) 以字母 "M" 前面的字母开头的所有实体。</span><span class="sxs-lookup"><span data-stu-id="de280-182">Here, you use two filters to get all entities in the "Smith" partition where the row key (first name) starts with a letter earlier than "M" in the alphabet.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

<span data-ttu-id="de280-183">现在可以打印结果：</span><span class="sxs-lookup"><span data-stu-id="de280-183">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a><span data-ttu-id="de280-184">检索单个实体</span><span class="sxs-lookup"><span data-stu-id="de280-184">Retrieve a single entity</span></span>

<span data-ttu-id="de280-185">可以编写查询以检索单个特定实体。</span><span class="sxs-lookup"><span data-stu-id="de280-185">You can write a query to retrieve a single, specific entity.</span></span> <span data-ttu-id="de280-186">在这里，您将使用 `TableOperation` 来指定客户 "Ben Smith"。</span><span class="sxs-lookup"><span data-stu-id="de280-186">Here, you use a `TableOperation` to specify the customer "Ben Smith".</span></span> <span data-ttu-id="de280-187">返回，而不是集合 `Customer` 。</span><span class="sxs-lookup"><span data-stu-id="de280-187">Instead of a collection, you get back a `Customer`.</span></span> <span data-ttu-id="de280-188">在查询中同时指定分区键和行键是从表服务中检索单个实体的最快方法。</span><span class="sxs-lookup"><span data-stu-id="de280-188">Specifying both the partition key and the row key in a query is the fastest way to retrieve a single entity from the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

<span data-ttu-id="de280-189">现在可以打印结果：</span><span class="sxs-lookup"><span data-stu-id="de280-189">You now print the results:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a><span data-ttu-id="de280-190">替换实体</span><span class="sxs-lookup"><span data-stu-id="de280-190">Replace an entity</span></span>

<span data-ttu-id="de280-191">若要更新实体，请从表服务中检索它，修改实体对象，然后使用操作将更改保存回表服务 `Replace` 。</span><span class="sxs-lookup"><span data-stu-id="de280-191">To update an entity, retrieve it from the Table service, modify the entity object, and then save the changes back to the Table service using a `Replace` operation.</span></span> <span data-ttu-id="de280-192">这会导致在服务器上完全替换该实体，除非服务器上的该实体自检索后已更改，在这种情况下，该操作将失败。</span><span class="sxs-lookup"><span data-stu-id="de280-192">This causes the entity to be fully replaced on the server, unless the entity on the server has changed since it was retrieved, in which case the operation fails.</span></span> <span data-ttu-id="de280-193">此失败是为了防止应用程序无意中覆盖其他源的更改。</span><span class="sxs-lookup"><span data-stu-id="de280-193">This failure is to prevent your application from inadvertently overwriting changes from other sources.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a><span data-ttu-id="de280-194">插入或替换实体</span><span class="sxs-lookup"><span data-stu-id="de280-194">Insert-or-replace an entity</span></span>

<span data-ttu-id="de280-195">有时，您不知道实体是否存在于表中。</span><span class="sxs-lookup"><span data-stu-id="de280-195">Sometimes, you don't know whether an entity exists in the table.</span></span> <span data-ttu-id="de280-196">如果是这样，则不再需要存储在其中的当前值。</span><span class="sxs-lookup"><span data-stu-id="de280-196">And if it does, the current values stored in it are no longer needed.</span></span> <span data-ttu-id="de280-197">`InsertOrReplace`如果实体存在，则可以使用创建实体，而不考虑其状态。</span><span class="sxs-lookup"><span data-stu-id="de280-197">You can use `InsertOrReplace` to create the entity, or replace it if it exists, regardless of its state.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a><span data-ttu-id="de280-198">查询一部分实体属性</span><span class="sxs-lookup"><span data-stu-id="de280-198">Query a subset of entity properties</span></span>

<span data-ttu-id="de280-199">表查询可以只检索实体中的几个属性，而不是所有这些属性。</span><span class="sxs-lookup"><span data-stu-id="de280-199">A table query can retrieve just a few properties from an entity instead of all of them.</span></span> <span data-ttu-id="de280-200">此方法称为 "投影"，可提高查询性能，尤其适用于大型实体。</span><span class="sxs-lookup"><span data-stu-id="de280-200">This technique, called projection, can improve query performance, especially for large entities.</span></span> <span data-ttu-id="de280-201">此处，使用和仅返回电子邮件 `DynamicTableEntity` 地址 `EntityResolver` 。</span><span class="sxs-lookup"><span data-stu-id="de280-201">Here, you return only email addresses using `DynamicTableEntity` and `EntityResolver`.</span></span> <span data-ttu-id="de280-202">本地存储模拟器不支持投影，因此此代码仅在使用表服务中的帐户时运行。</span><span class="sxs-lookup"><span data-stu-id="de280-202">Projection is not supported on the local storage emulator, so this code runs only when you're using an account on the Table service.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a><span data-ttu-id="de280-203">以异步方式检索页中的实体</span><span class="sxs-lookup"><span data-stu-id="de280-203">Retrieve entities in pages asynchronously</span></span>

<span data-ttu-id="de280-204">如果正在读取大量实体，并且想要在检索它们时处理它们，而不是等待返回全部实体，则可以使用分段查询。</span><span class="sxs-lookup"><span data-stu-id="de280-204">If you are reading a large number of entities, and you want to process them as they are retrieved rather than waiting for them all to return, you can use a segmented query.</span></span> <span data-ttu-id="de280-205">在这里，你将使用异步工作流返回页面结果，以便在你等待返回大量结果时不会阻止执行。</span><span class="sxs-lookup"><span data-stu-id="de280-205">Here, you return results in pages by using an async workflow so that execution is not blocked while you're waiting for a large set of results to return.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

<span data-ttu-id="de280-206">现在，你可以同步执行此计算：</span><span class="sxs-lookup"><span data-stu-id="de280-206">You now execute this computation synchronously:</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a><span data-ttu-id="de280-207">删除实体</span><span class="sxs-lookup"><span data-stu-id="de280-207">Delete an entity</span></span>

<span data-ttu-id="de280-208">检索实体后，可以将其删除。</span><span class="sxs-lookup"><span data-stu-id="de280-208">You can delete an entity after you have retrieved it.</span></span> <span data-ttu-id="de280-209">与更新实体一样，如果实体在检索后发生更改，则此操作将失败。</span><span class="sxs-lookup"><span data-stu-id="de280-209">As with updating an entity, this fails if the entity has changed since you retrieved it.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a><span data-ttu-id="de280-210">删除表</span><span class="sxs-lookup"><span data-stu-id="de280-210">Delete a table</span></span>

<span data-ttu-id="de280-211">可以从存储帐户中删除表。</span><span class="sxs-lookup"><span data-stu-id="de280-211">You can delete a table from a storage account.</span></span> <span data-ttu-id="de280-212">在删除表之后的一段时间内无法重新创建它。</span><span class="sxs-lookup"><span data-stu-id="de280-212">A table that has been deleted will be unavailable to be re-created for a period of time following the deletion.</span></span>

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a><span data-ttu-id="de280-213">后续步骤</span><span class="sxs-lookup"><span data-stu-id="de280-213">Next steps</span></span>

<span data-ttu-id="de280-214">现在，你已了解有关表存储的基础知识，请单击下面的链接了解更复杂的存储任务和 Azure Cosmos DB 表 API。</span><span class="sxs-lookup"><span data-stu-id="de280-214">Now that you've learned the basics of Table storage, follow these links to learn about more complex storage tasks and the Azure Cosmos DB Table API.</span></span>

- [<span data-ttu-id="de280-215">Azure Cosmos DB 简介表 API</span><span class="sxs-lookup"><span data-stu-id="de280-215">Introduction to Azure Cosmos DB Table API</span></span>](/azure/cosmos-db/table-introduction)
- [<span data-ttu-id="de280-216">.NET 存储客户端库参考</span><span class="sxs-lookup"><span data-stu-id="de280-216">Storage Client Library for .NET reference</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="de280-217">Azure 存储类型提供程序</span><span class="sxs-lookup"><span data-stu-id="de280-217">Azure Storage Type Provider</span></span>](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [<span data-ttu-id="de280-218">Azure 存储团队博客</span><span class="sxs-lookup"><span data-stu-id="de280-218">Azure Storage Team Blog</span></span>](/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="de280-219">配置连接字符串</span><span class="sxs-lookup"><span data-stu-id="de280-219">Configuring Connection Strings</span></span>](/azure/storage/common/storage-configure-connection-string)
