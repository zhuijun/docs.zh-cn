---
title: 查询数据服务（WCF 数据服务）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: 13334f6425c47e45d729d606d99602a99f35d8e6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286153"
---
# <a name="querying-the-data-service-wcf-data-services"></a><span data-ttu-id="04934-102">查询数据服务（WCF 数据服务）</span><span class="sxs-lookup"><span data-stu-id="04934-102">Querying the Data Service (WCF Data Services)</span></span>

<span data-ttu-id="04934-103">WCF 数据服务客户端库允许使用熟悉的 .NET Framework 编程模式（包括使用语言集成查询（LINQ））对数据服务执行查询。</span><span class="sxs-lookup"><span data-stu-id="04934-103">The WCF Data Services client library enables you to execute queries against a data service by using familiar .NET Framework programming patterns, including using language integrated query (LINQ).</span></span> <span data-ttu-id="04934-104">客户端库将在客户端上定义为 <xref:System.Data.Services.Client.DataServiceQuery%601> 类实例的查询转换为 HTTP GET 请求消息。</span><span class="sxs-lookup"><span data-stu-id="04934-104">The client library translates a query, which is defined on the client as an instance of the <xref:System.Data.Services.Client.DataServiceQuery%601> class, into an HTTP GET request message.</span></span> <span data-ttu-id="04934-105">该库接收响应消息并将该消息转换为客户端数据服务类的实例。</span><span class="sxs-lookup"><span data-stu-id="04934-105">The library receives the response message and translates it into instances of client data service classes.</span></span> <span data-ttu-id="04934-106"><xref:System.Data.Services.Client.DataServiceContext> 所属的 <xref:System.Data.Services.Client.DataServiceQuery%601> 跟踪这些类。</span><span class="sxs-lookup"><span data-stu-id="04934-106">These classes are tracked by the <xref:System.Data.Services.Client.DataServiceContext> to which the <xref:System.Data.Services.Client.DataServiceQuery%601> belongs.</span></span>

## <a name="data-service-queries"></a><span data-ttu-id="04934-107">数据服务查询</span><span class="sxs-lookup"><span data-stu-id="04934-107">Data Service Queries</span></span>

<span data-ttu-id="04934-108"><xref:System.Data.Services.Client.DataServiceQuery%601> 泛型类表示一个查询，该查询返回一个包含零个或零个以上实体类型实例的集合。</span><span class="sxs-lookup"><span data-stu-id="04934-108">The <xref:System.Data.Services.Client.DataServiceQuery%601> generic class represents a query that returns a collection of zero or more entity type instances.</span></span> <span data-ttu-id="04934-109">数据服务查询始终属于现有数据服务上下文。</span><span class="sxs-lookup"><span data-stu-id="04934-109">A data service query always belongs to an existing data service context.</span></span> <span data-ttu-id="04934-110">此上下文含有撰写和执行查询所必需的服务 URI 和元数据信息。</span><span class="sxs-lookup"><span data-stu-id="04934-110">This context maintains the service URI and metadata information that is required to compose and execute the query.</span></span>

<span data-ttu-id="04934-111">使用**添加服务引用**对话框将数据服务添加到基于 .NET Framework 的客户端应用程序时，将创建一个从类继承的实体容器类 <xref:System.Data.Services.Client.DataServiceContext> 。</span><span class="sxs-lookup"><span data-stu-id="04934-111">When you use the **Add Service Reference** dialog to add a data service to a .NET Framework-based client application, an entity container class is created that inherits from the <xref:System.Data.Services.Client.DataServiceContext> class.</span></span> <span data-ttu-id="04934-112">此类包括返回类型化 <xref:System.Data.Services.Client.DataServiceQuery%601> 实例的属性。</span><span class="sxs-lookup"><span data-stu-id="04934-112">This class includes properties that return typed <xref:System.Data.Services.Client.DataServiceQuery%601> instances.</span></span> <span data-ttu-id="04934-113">数据服务公开的每个实体集对应一个属性。</span><span class="sxs-lookup"><span data-stu-id="04934-113">There is one property for each entity set that the data service exposes.</span></span> <span data-ttu-id="04934-114">使用这些属性可以更容易地创建类型化 <xref:System.Data.Services.Client.DataServiceQuery%601> 的实例。</span><span class="sxs-lookup"><span data-stu-id="04934-114">These properties make it easier to create an instance of a typed <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span>

<span data-ttu-id="04934-115">在以下情况下会执行查询：</span><span class="sxs-lookup"><span data-stu-id="04934-115">A query is executed in the following scenarios:</span></span>

- <span data-ttu-id="04934-116">隐式枚举结果时，如：</span><span class="sxs-lookup"><span data-stu-id="04934-116">When results are enumerated implicitly, such as:</span></span>

  - <span data-ttu-id="04934-117"><xref:System.Data.Services.Client.DataServiceContext> 上的某个属性表示并枚举实体集时，如在 `foreach` (C#) 或 `For Each` (Visual Basic) 循环期间。</span><span class="sxs-lookup"><span data-stu-id="04934-117">When a property on the <xref:System.Data.Services.Client.DataServiceContext> that represents and entity set is enumerated, such as during a `foreach` (C#) or `For Each` (Visual Basic) loop.</span></span>

  - <span data-ttu-id="04934-118">将查询赋给 `List` 集合时。</span><span class="sxs-lookup"><span data-stu-id="04934-118">When the query is assigned to a `List` collection.</span></span>

- <span data-ttu-id="04934-119">显式调用 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 或 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法时。</span><span class="sxs-lookup"><span data-stu-id="04934-119">When the <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> or <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> method is explicitly called.</span></span>

- <span data-ttu-id="04934-120">调用 LINQ 查询执行运算符（例如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Single%2A>）时。</span><span class="sxs-lookup"><span data-stu-id="04934-120">When a LINQ query execution operator, such as <xref:System.Linq.Enumerable.First%2A> or <xref:System.Linq.Enumerable.Single%2A> is called.</span></span>

<span data-ttu-id="04934-121">下面的查询在执行时返回罗斯文数据服务中的所有 `Customers` 实体：</span><span class="sxs-lookup"><span data-stu-id="04934-121">The following query, when it is executed, returns all `Customers` entities in the Northwind data service:</span></span>

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

<span data-ttu-id="04934-122">有关详细信息，请参阅[如何：执行数据服务查询](how-to-execute-data-service-queries-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-122">For more information, see [How to: Execute Data Service Queries](how-to-execute-data-service-queries-wcf-data-services.md).</span></span>

<span data-ttu-id="04934-123">WCF 数据服务客户端支持对后期绑定对象的查询，例如在 c # 中使用*动态*类型时。</span><span class="sxs-lookup"><span data-stu-id="04934-123">The WCF Data Services client supports queries for late-bound objects, such as when you use the *dynamic* type in C#.</span></span> <span data-ttu-id="04934-124">但是，出于性能方面的考虑，应始终针对数据服务编写强类型查询。</span><span class="sxs-lookup"><span data-stu-id="04934-124">However, for performance reasons you should always compose strongly typed queries against the data service.</span></span> <span data-ttu-id="04934-125">客户端不支持 <xref:System.Tuple> 类型和动态对象。</span><span class="sxs-lookup"><span data-stu-id="04934-125">The <xref:System.Tuple> type and dynamic objects are not supported by the client.</span></span>

## <a name="linq-queries"></a><span data-ttu-id="04934-126">LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="04934-126">LINQ Queries</span></span>

<span data-ttu-id="04934-127">由于 <xref:System.Data.Services.Client.DataServiceQuery%601> 类实现 <xref:System.Linq.IQueryable%601> linq 定义的接口，因此 WCF 数据服务的客户端库可以将针对实体集数据的 LINQ 查询转换为一个 URI，该 URI 表示针对数据服务资源计算的查询表达式。</span><span class="sxs-lookup"><span data-stu-id="04934-127">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, the WCF Data Services client library is able to transform LINQ queries against entity set data into a URI that represents a query expression evaluated against a data service resource.</span></span> <span data-ttu-id="04934-128">下面的示例是一个等效于之前 <xref:System.Data.Services.Client.DataServiceQuery%601> 的 LINQ 查询，它返回运费成本超过 30 美元的 `Orders` 并按运费成本对结果进行排序：</span><span class="sxs-lookup"><span data-stu-id="04934-128">The following example is a LINQ query that is equivalent to the previous <xref:System.Data.Services.Client.DataServiceQuery%601> that returns `Orders` that have a freight cost of more than $30 and orders the results by the freight cost:</span></span>

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

<span data-ttu-id="04934-129">此 LINQ 查询转换为对基于 Northwind 的[快速入门](quickstart-wcf-data-services.md)数据服务执行的以下查询 URI：</span><span class="sxs-lookup"><span data-stu-id="04934-129">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](quickstart-wcf-data-services.md) data service:</span></span>

```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> <span data-ttu-id="04934-130">可以采用 LINQ 语法表示的查询集大于数据服务使用的基于具象状态传输 (REST) 的 URI 语法所支持的查询集。</span><span class="sxs-lookup"><span data-stu-id="04934-130">The set of queries expressible in the LINQ syntax is broader than those enabled in the representational state transfer (REST)-based URI syntax that is used by data services.</span></span> <span data-ttu-id="04934-131">如果无法将查询映射到目标数据服务中的 URI，则会引发 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="04934-131">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span>

<span data-ttu-id="04934-132">有关详细信息，请参阅[LINQ 注意事项](linq-considerations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-132">For more information, see [LINQ Considerations](linq-considerations-wcf-data-services.md).</span></span>

## <a name="adding-query-options"></a><span data-ttu-id="04934-133">添加查询选项</span><span class="sxs-lookup"><span data-stu-id="04934-133">Adding Query Options</span></span>

<span data-ttu-id="04934-134">数据服务查询支持 WCF 数据服务提供的所有查询选项。</span><span class="sxs-lookup"><span data-stu-id="04934-134">Data service queries support all the query options that WCF Data Services provides.</span></span> <span data-ttu-id="04934-135">调用 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法可向 <xref:System.Data.Services.Client.DataServiceQuery%601> 实例追加查询选项。</span><span class="sxs-lookup"><span data-stu-id="04934-135">You call the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to append query options to a <xref:System.Data.Services.Client.DataServiceQuery%601> instance.</span></span> <span data-ttu-id="04934-136"><xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 返回一个新的 <xref:System.Data.Services.Client.DataServiceQuery%601> 实例，该实例等效于原始查询，但带有新的查询选项集。</span><span class="sxs-lookup"><span data-stu-id="04934-136"><xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> returns a new <xref:System.Data.Services.Client.DataServiceQuery%601> instance that is equivalent to the original query but with the new query option set.</span></span> <span data-ttu-id="04934-137">下面的查询在执行时会返回按 `Orders` 值进行筛选并按 `Freight` 降序排序的 `OrderID`：</span><span class="sxs-lookup"><span data-stu-id="04934-137">The following query, when executed, returns `Orders` that are filtered by the `Freight` value and ordered by the `OrderID`, descending:</span></span>

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

<span data-ttu-id="04934-138">可以使用 `$orderby` 查询选项基于单个属性对查询进行排序和筛选，如下面的示例所示，该示例基于 `Orders` 属性的值对返回的 `Freight` 对象进行筛选和排序：</span><span class="sxs-lookup"><span data-stu-id="04934-138">You can use the `$orderby` query option to both order and filter a query based on a single property, as in the following example that filters and orders the returned `Orders` objects based on the value of the `Freight` property:</span></span>

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

<span data-ttu-id="04934-139">可以连续调用 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法来构造复杂的查询表达式。</span><span class="sxs-lookup"><span data-stu-id="04934-139">You can call the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method consecutively to construct complex query expressions.</span></span> <span data-ttu-id="04934-140">有关详细信息，请参阅[如何：将查询选项添加到数据服务查询](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-140">For more information, see [How to: Add Query Options to a Data Service Query](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).</span></span>

<span data-ttu-id="04934-141">查询选项为表示 LINQ 查询的语法成分提供了另一种方法。</span><span class="sxs-lookup"><span data-stu-id="04934-141">Query options give you another way to express the syntactic components of a LINQ query.</span></span> <span data-ttu-id="04934-142">有关详细信息，请参阅[LINQ 注意事项](linq-considerations-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-142">For more information, see [LINQ Considerations](linq-considerations-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="04934-143">不能使用 `$select` 方法将 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 查询选项添加到查询 URI 中。</span><span class="sxs-lookup"><span data-stu-id="04934-143">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="04934-144">我们建议使用 LINQ <xref:System.Linq.Enumerable.Select%2A> 方法，让客户端在请求 URI 中生成 `$select` 查询选项。</span><span class="sxs-lookup"><span data-stu-id="04934-144">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a><span data-ttu-id="04934-145">客户端执行与服务器执行</span><span class="sxs-lookup"><span data-stu-id="04934-145">Client versus Server Execution</span></span>

<span data-ttu-id="04934-146">客户端分两个部分来执行查询。</span><span class="sxs-lookup"><span data-stu-id="04934-146">The client executes a query in two parts.</span></span> <span data-ttu-id="04934-147">只要有可能，将首先在客户端上计算查询中的表达式，然后生成基于 URI 的查询并将其发送至数据服务，以针对服务中的数据进行计算。</span><span class="sxs-lookup"><span data-stu-id="04934-147">Whenever possible, expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="04934-148">请考虑以下 LINQ 查询：</span><span class="sxs-lookup"><span data-stu-id="04934-148">Consider the following LINQ query:</span></span>

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

<span data-ttu-id="04934-149">在本例中，表达式 `(basePrice – (basePrice * discount))` 在客户端上进行计算。</span><span class="sxs-lookup"><span data-stu-id="04934-149">In this example, the expression `(basePrice – (basePrice * discount))` is evaluated on the client.</span></span> <span data-ttu-id="04934-150">因此，发送至数据服务的实际查询 URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` 将在筛选子句中包含已计算的十进制值 `90`。</span><span class="sxs-lookup"><span data-stu-id="04934-150">Because of this, the actual query URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` that is sent to the data service contains the already calculated decimal value of `90` in the filter clause.</span></span> <span data-ttu-id="04934-151">数据服务将计算筛选表达式的其他部分，包括子字符串表达式。</span><span class="sxs-lookup"><span data-stu-id="04934-151">The other parts of the filtering expression, including the substring expression, are evaluated by the data service.</span></span> <span data-ttu-id="04934-152">在客户端上计算的表达式遵循公共语言运行时（CLR）语义，而发送到数据服务的表达式依赖于 OData 协议的数据服务实现。</span><span class="sxs-lookup"><span data-stu-id="04934-152">Expressions that are evaluated on the client follow common language runtime (CLR) semantics, while expressions sent to the data service rely on the data service implementation of the OData Protocol.</span></span> <span data-ttu-id="04934-153">还应当注意这种分别计算会导致意外结果的情况，例如当客户端和服务同时在不同时区中执行基于时间的计算时。</span><span class="sxs-lookup"><span data-stu-id="04934-153">You should also be aware of scenarios where this separate evaluation may cause unexpected results, such as when both the client and service perform time-based evaluations in different time zones.</span></span>

## <a name="query-responses"></a><span data-ttu-id="04934-154">查询响应</span><span class="sxs-lookup"><span data-stu-id="04934-154">Query Responses</span></span>

<span data-ttu-id="04934-155">执行 <xref:System.Data.Services.Client.DataServiceQuery%601> 时将返回所请求的实体类型的 <xref:System.Collections.Generic.IEnumerable%601>。</span><span class="sxs-lookup"><span data-stu-id="04934-155">When executed, the <xref:System.Data.Services.Client.DataServiceQuery%601> returns an <xref:System.Collections.Generic.IEnumerable%601> of the requested entity type.</span></span> <span data-ttu-id="04934-156">可以将此查询结果强制转换为 <xref:System.Data.Services.Client.QueryOperationResponse%601> 对象，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="04934-156">This query result can be cast to a <xref:System.Data.Services.Client.QueryOperationResponse%601> object, as in the following example:</span></span>

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

<span data-ttu-id="04934-157">表示数据服务中的实体的实体类型实例是在客户端上由称为对象具体化的过程创建的。</span><span class="sxs-lookup"><span data-stu-id="04934-157">The entity type instances that represent entities in the data service are created on the client by a process called object materialization.</span></span> <span data-ttu-id="04934-158">有关详细信息，请参阅[对象具体化](object-materialization-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-158">For more information, see [Object Materialization](object-materialization-wcf-data-services.md).</span></span> <span data-ttu-id="04934-159"><xref:System.Data.Services.Client.QueryOperationResponse%601> 对象实现 <xref:System.Collections.Generic.IEnumerable%601> 以提供对查询结果的访问。</span><span class="sxs-lookup"><span data-stu-id="04934-159">The <xref:System.Data.Services.Client.QueryOperationResponse%601> object implements <xref:System.Collections.Generic.IEnumerable%601> to provide access to the results of the query.</span></span>

<span data-ttu-id="04934-160"><xref:System.Data.Services.Client.QueryOperationResponse%601> 还包括下列成员，它们可用来访问有关查询结果的其他信息：</span><span class="sxs-lookup"><span data-stu-id="04934-160">The <xref:System.Data.Services.Client.QueryOperationResponse%601> also has the following members that enable you to access additional information about a query result:</span></span>

- <span data-ttu-id="04934-161"><xref:System.Data.Services.Client.OperationResponse.Error%2A> - 获取由操作引发的错误（如果发生了这样的错误）。</span><span class="sxs-lookup"><span data-stu-id="04934-161"><xref:System.Data.Services.Client.OperationResponse.Error%2A> - gets an error thrown by the operation, if any has occurred.</span></span>

- <span data-ttu-id="04934-162"><xref:System.Data.Services.Client.OperationResponse.Headers%2A> - 包含与查询响应关联的 HTTP 响应标头的集合。</span><span class="sxs-lookup"><span data-stu-id="04934-162"><xref:System.Data.Services.Client.OperationResponse.Headers%2A> - contains the collection of HTTP response headers associated with the query response.</span></span>

- <span data-ttu-id="04934-163"><xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> - 获取生成了 <xref:System.Data.Services.Client.DataServiceQuery%601> 的原始 <xref:System.Data.Services.Client.QueryOperationResponse%601>。</span><span class="sxs-lookup"><span data-stu-id="04934-163"><xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> - gets the original <xref:System.Data.Services.Client.DataServiceQuery%601> that generated the <xref:System.Data.Services.Client.QueryOperationResponse%601>.</span></span>

- <span data-ttu-id="04934-164"><xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> - 获取查询响应的 HTTP 响应代码。</span><span class="sxs-lookup"><span data-stu-id="04934-164"><xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> - gets the HTTP response code for the query response.</span></span>

- <span data-ttu-id="04934-165"><xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> - 获取在对 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 调用 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法时，实体集中的实体总数。</span><span class="sxs-lookup"><span data-stu-id="04934-165"><xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> - gets the total number of entities in the entity set when the <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> method was called on the <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span>

- <span data-ttu-id="04934-166"><xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> - 返回一个 <xref:System.Data.Services.Client.DataServiceQueryContinuation> 对象，该对象包含下一页结果的 URI。</span><span class="sxs-lookup"><span data-stu-id="04934-166"><xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> - returns a <xref:System.Data.Services.Client.DataServiceQueryContinuation> object that contains the URI of the next page of results.</span></span>

<span data-ttu-id="04934-167">默认情况下，WCF 数据服务仅返回查询 URI 显式选择的数据。</span><span class="sxs-lookup"><span data-stu-id="04934-167">By default, WCF Data Services only returns data that is explicitly selected by the query URI.</span></span> <span data-ttu-id="04934-168">这样即提供了在需要时从数据服务显式加载其他数据的选项。</span><span class="sxs-lookup"><span data-stu-id="04934-168">This gives you the option to explicitly load additional data from the data service when it is needed.</span></span> <span data-ttu-id="04934-169">每次从数据服务显式加载数据时都会向数据服务发送一个请求。</span><span class="sxs-lookup"><span data-stu-id="04934-169">A request is sent to the data service each time you explicitly load data from the data service.</span></span> <span data-ttu-id="04934-170">可以显式加载的数据包括相关实体、分页响应数据以及二进制数据流。</span><span class="sxs-lookup"><span data-stu-id="04934-170">Data that can be explicitly loaded includes related entities, paged response data, and binary data streams.</span></span>

> [!NOTE]
> <span data-ttu-id="04934-171">由于数据服务可能返回分页响应，因此建议您的应用程序使用编程模式来处理分页的数据服务响应。</span><span class="sxs-lookup"><span data-stu-id="04934-171">Because a data service may return a paged response, we recommend that your application use the programming pattern to handle a paged data service response.</span></span> <span data-ttu-id="04934-172">有关详细信息，请参阅[加载延迟的内容](loading-deferred-content-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-172">For more information, see [Loading Deferred Content](loading-deferred-content-wcf-data-services.md).</span></span>

<span data-ttu-id="04934-173">还可以通过指定在响应中仅返回某个实体的某些属性来减少查询返回的数据量。</span><span class="sxs-lookup"><span data-stu-id="04934-173">The amount of data returned by a query can also be reduced by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="04934-174">有关详细信息，请参阅[查询投影](query-projections-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-174">For more information, see [Query Projections](query-projections-wcf-data-services.md).</span></span>

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a><span data-ttu-id="04934-175">获取集合中实体的总数</span><span class="sxs-lookup"><span data-stu-id="04934-175">Getting a Count of the Total Number of Entities in the Set</span></span>

<span data-ttu-id="04934-176">在某些方案中，不仅知道查询返回的实体数，还要知道实体集中实体的总数，这一点非常有帮助。</span><span class="sxs-lookup"><span data-stu-id="04934-176">In some scenarios, it is helpful to know the total number of entities in an entity set and not merely the number returned by the query.</span></span> <span data-ttu-id="04934-177">调用 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 上的 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法可请求在查询结果中包含集中实体的总数。</span><span class="sxs-lookup"><span data-stu-id="04934-177">Call the <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> method on the <xref:System.Data.Services.Client.DataServiceQuery%601> to request that this total count of entities in the set be included with the query result.</span></span> <span data-ttu-id="04934-178">在这种情况下，返回的 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> 的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 属性返回集中实体的总数。</span><span class="sxs-lookup"><span data-stu-id="04934-178">In this case, the <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> property of the returned <xref:System.Data.Services.Client.QueryOperationResponse%601> returns the total number of entities in the set.</span></span>

<span data-ttu-id="04934-179">还可以仅获取集合中实体的总数，该总数可作为 <xref:System.Int32> 或 <xref:System.Int64> 值，方法是分别调用 <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.LongCount%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="04934-179">You can also get only the total count of entities in the set either as an <xref:System.Int32> or as a <xref:System.Int64> value by calling the <xref:System.Linq.Enumerable.Count%2A> or <xref:System.Linq.Enumerable.LongCount%2A> methods respectively.</span></span> <span data-ttu-id="04934-180">调用这些方法时，不会返回 <xref:System.Data.Services.Client.QueryOperationResponse%601>；仅返回计数值。</span><span class="sxs-lookup"><span data-stu-id="04934-180">When these methods are called, a <xref:System.Data.Services.Client.QueryOperationResponse%601> is not returned; only the count value is returned.</span></span> <span data-ttu-id="04934-181">有关详细信息，请参阅[如何：确定查询返回的实体数](number-of-entities-returned-by-a-query-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="04934-181">For more information, see [How to: Determine the Number of Entities Returned by a Query](number-of-entities-returned-by-a-query-wcf.md).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="04934-182">本节内容</span><span class="sxs-lookup"><span data-stu-id="04934-182">In This Section</span></span>

- [<span data-ttu-id="04934-183">查询投影</span><span class="sxs-lookup"><span data-stu-id="04934-183">Query Projections</span></span>](query-projections-wcf-data-services.md)

- [<span data-ttu-id="04934-184">对象具体化</span><span class="sxs-lookup"><span data-stu-id="04934-184">Object Materialization</span></span>](object-materialization-wcf-data-services.md)

- [<span data-ttu-id="04934-185">LINQ 注意事项</span><span class="sxs-lookup"><span data-stu-id="04934-185">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="04934-186">如何：执行数据服务查询</span><span class="sxs-lookup"><span data-stu-id="04934-186">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="04934-187">如何：将查询选项添加到数据服务查询</span><span class="sxs-lookup"><span data-stu-id="04934-187">How to: Add Query Options to a Data Service Query</span></span>](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [<span data-ttu-id="04934-188">如何：确定由查询返回的实体数</span><span class="sxs-lookup"><span data-stu-id="04934-188">How to: Determine the Number of Entities Returned by a Query</span></span>](number-of-entities-returned-by-a-query-wcf.md)

- [<span data-ttu-id="04934-189">如何：为数据服务请求指定客户端凭据</span><span class="sxs-lookup"><span data-stu-id="04934-189">How to: Specify Client Credentials for a Data Service Request</span></span>](specify-client-creds-for-a-data-service-request-wcf.md)

- [<span data-ttu-id="04934-190">如何：设置客户端请求中的标头</span><span class="sxs-lookup"><span data-stu-id="04934-190">How to: Set Headers in the Client Request</span></span>](how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [<span data-ttu-id="04934-191">如何：投影查询结果</span><span class="sxs-lookup"><span data-stu-id="04934-191">How to: Project Query Results</span></span>](how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a><span data-ttu-id="04934-192">另请参阅</span><span class="sxs-lookup"><span data-stu-id="04934-192">See also</span></span>

- [<span data-ttu-id="04934-193">WCF 数据服务客户端库</span><span class="sxs-lookup"><span data-stu-id="04934-193">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
