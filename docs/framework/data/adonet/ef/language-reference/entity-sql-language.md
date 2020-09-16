---
title: Entity SQL 语言
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: 2600b7626ebc5196c702f2d1e3159fd9549227f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553377"
---
# <a name="entity-sql-language"></a><span data-ttu-id="07062-102">Entity SQL 语言</span><span class="sxs-lookup"><span data-stu-id="07062-102">Entity SQL Language</span></span>
<span data-ttu-id="07062-103">Entity SQL 是类似于 SQL 的与存储无关的查询语言。</span><span class="sxs-lookup"><span data-stu-id="07062-103">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="07062-104">通过 Entity SQL，可以将实体数据作为对象或以表格形式进行查询。</span><span class="sxs-lookup"><span data-stu-id="07062-104">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="07062-105">在以下情况下，应考虑使用 Entity SQL：</span><span class="sxs-lookup"><span data-stu-id="07062-105">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="07062-106">当查询必须在运行时动态构造时。</span><span class="sxs-lookup"><span data-stu-id="07062-106">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="07062-107">在这种情况下，还应考虑使用 <xref:System.Data.Objects.ObjectQuery%601> 的查询生成器方法，而不是在运行时构造 Entity SQL 查询字符串。</span><span class="sxs-lookup"><span data-stu-id="07062-107">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="07062-108">当您要将查询定义为模型定义的一部分时。</span><span class="sxs-lookup"><span data-stu-id="07062-108">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="07062-109">在数据模型中只支持 Entity SQL。</span><span class="sxs-lookup"><span data-stu-id="07062-109">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="07062-110">有关详细信息，请参阅 [QueryView 元素 (MSL) ](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span><span class="sxs-lookup"><span data-stu-id="07062-110">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="07062-111">当使用 EntityClient，通过 <xref:System.Data.EntityClient.EntityDataReader> 将只读实体数据返回为行集时。</span><span class="sxs-lookup"><span data-stu-id="07062-111">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="07062-112">有关详细信息，请参阅 [用于 Entity Framework 的 EntityClient 提供程序](../entityclient-provider-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="07062-112">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="07062-113">如果您已经是基于 SQL 的查询语言的专家，Entity SQL 可能对您而言是最简单不过了。</span><span class="sxs-lookup"><span data-stu-id="07062-113">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="07062-114">将 Entity SQL 与 EntityClient 提供程序结合使用</span><span class="sxs-lookup"><span data-stu-id="07062-114">Using Entity SQL with the EntityClient provider</span></span>  
 <span data-ttu-id="07062-115">如果您要将 Entity SQL 与 EntityClient 提供程序结合使用，有关更多信息请参见下列主题：</span><span class="sxs-lookup"><span data-stu-id="07062-115">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="07062-116">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="07062-116">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="07062-117">如何：生成 EntityConnection 连接字符串</span><span class="sxs-lookup"><span data-stu-id="07062-117">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="07062-118">如何：执行返回 PrimitiveType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="07062-118">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="07062-119">如何：执行返回 StructuralType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="07062-119">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="07062-120">如何：执行返回 RefType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="07062-120">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="07062-121">如何：执行返回复杂类型的查询</span><span class="sxs-lookup"><span data-stu-id="07062-121">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="07062-122">如何：执行返回嵌套集合的查询</span><span class="sxs-lookup"><span data-stu-id="07062-122">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="07062-123">如何：使用 EntityCommand 执行参数化实体 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="07062-123">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="07062-124">如何：使用 EntityCommand 执行参数化存储过程</span><span class="sxs-lookup"><span data-stu-id="07062-124">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="07062-125">如何：执行多态查询</span><span class="sxs-lookup"><span data-stu-id="07062-125">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="07062-126">如何：使用导航运算符导航关系</span><span class="sxs-lookup"><span data-stu-id="07062-126">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="07062-127">将 Entity SQL 与对象查询结合使用</span><span class="sxs-lookup"><span data-stu-id="07062-127">Using Entity SQL with object queries</span></span>  
 <span data-ttu-id="07062-128">如果您要将 Entity SQL 与对象查询结合使用，有关更多信息请参见下列主题：</span><span class="sxs-lookup"><span data-stu-id="07062-128">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="07062-129">[如何：执行返回实体类型对象的查询](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-129">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-130">[如何：执行参数化查询](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-130">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-131">[如何：使用导航属性导航关系](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-131">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-132">[如何：调用用户定义的函数](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-132">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-133">[如何：筛选数据](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-133">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-134">[如何：对数据排序](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-134">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-135">[如何：对数据分组](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-135">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-136">[如何：聚合数据](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-136">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-137">[如何：执行返回匿名类型对象的查询](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-137">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-138">[如何：执行返回基元类型集合的查询](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-138">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-139">[如何：在 EntityCollection 中查询相关对象](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-139">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-140">[如何：对两个查询的联合排序](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-140">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="07062-141">[如何：按页查看查询结果](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="07062-141">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="07062-142">本节内容</span><span class="sxs-lookup"><span data-stu-id="07062-142">In This Section</span></span>  
 [<span data-ttu-id="07062-143">Entity SQL 概述</span><span class="sxs-lookup"><span data-stu-id="07062-143">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="07062-144">实体 SQL 引用</span><span class="sxs-lookup"><span data-stu-id="07062-144">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="07062-145">请参阅</span><span class="sxs-lookup"><span data-stu-id="07062-145">See also</span></span>

- [<span data-ttu-id="07062-146">ADO.NET 实体框架</span><span class="sxs-lookup"><span data-stu-id="07062-146">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="07062-147">语言参考</span><span class="sxs-lookup"><span data-stu-id="07062-147">Language Reference</span></span>](index.md)
