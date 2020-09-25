---
title: 用于实体框架的 EntityClient 提供程序
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 9b3194e4a85eda6f405a3ab85723ac2cb9d00090
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181071"
---
# <a name="entityclient-provider-for-the-entity-framework"></a><span data-ttu-id="a496a-102">用于实体框架的 EntityClient 提供程序</span><span class="sxs-lookup"><span data-stu-id="a496a-102">EntityClient Provider for the Entity Framework</span></span>

<span data-ttu-id="a496a-103">EntityClient 提供程序是一种数据提供程序，实体框架应用程序使用该提供程序访问在概念模型中描述的数据。</span><span class="sxs-lookup"><span data-stu-id="a496a-103">The EntityClient provider is a data provider used by Entity Framework applications to access data described in a conceptual model.</span></span> <span data-ttu-id="a496a-104">有关概念模型的信息，请参阅 [建模和映射](modeling-and-mapping.md)。</span><span class="sxs-lookup"><span data-stu-id="a496a-104">For information about conceptual models, see [Modeling and Mapping](modeling-and-mapping.md).</span></span> <span data-ttu-id="a496a-105">EntityClient 使用其他 .NET Framework 数据提供程序访问数据源。</span><span class="sxs-lookup"><span data-stu-id="a496a-105">EntityClient uses other .NET Framework data providers to access the data source.</span></span> <span data-ttu-id="a496a-106">例如，EntityClient 在访问 SQL Server 数据库时使用 SQL Server .NET Framework 数据提供程序 (SqlClient)。</span><span class="sxs-lookup"><span data-stu-id="a496a-106">For example, EntityClient uses the .NET Framework Data Provider for SQL Server (SqlClient) when accessing a SQL Server database.</span></span> <span data-ttu-id="a496a-107">有关 SqlClient 提供程序的信息，请参阅 [SqlClient for the 实体框架](sqlclient-for-the-entity-framework.md)。</span><span class="sxs-lookup"><span data-stu-id="a496a-107">For information about the SqlClient provider, see [SqlClient for the Entity Framework](sqlclient-for-the-entity-framework.md).</span></span> <span data-ttu-id="a496a-108">EntityClient 提供程序是在 <xref:System.Data.EntityClient> 命名空间中实现的。</span><span class="sxs-lookup"><span data-stu-id="a496a-108">The EntityClient provider is implemented in the <xref:System.Data.EntityClient> namespace.</span></span>  
  
## <a name="managing-connections"></a><span data-ttu-id="a496a-109">管理连接</span><span class="sxs-lookup"><span data-stu-id="a496a-109">Managing Connections</span></span>  

 <span data-ttu-id="a496a-110">实体框架通过 <xref:System.Data.EntityClient.EntityConnection> 向基础数据提供程序和关系数据库提供，在存储特定的 ADO.NET 数据提供程序的基础上建立。</span><span class="sxs-lookup"><span data-stu-id="a496a-110">The Entity Framework builds on top of storage-specific ADO.NET data providers by providing an <xref:System.Data.EntityClient.EntityConnection> to an underlying data provider and relational database.</span></span> <span data-ttu-id="a496a-111">若要构造 <xref:System.Data.EntityClient.EntityConnection> 对象，你必须引用一组包含所需模型和映射的元数据，以及特定于存储的数据提供程序名称和连接字符串。</span><span class="sxs-lookup"><span data-stu-id="a496a-111">To construct an <xref:System.Data.EntityClient.EntityConnection> object, you have to reference a set of metadata that contains the necessary models and mapping, and also a storage-specific data provider name and connection string.</span></span> <span data-ttu-id="a496a-112"><xref:System.Data.EntityClient.EntityConnection>准备就绪后，可以通过从概念模型生成的类访问实体。</span><span class="sxs-lookup"><span data-stu-id="a496a-112">After the <xref:System.Data.EntityClient.EntityConnection> is in place, entities can be accessed through the classes generated from the conceptual model.</span></span>  
  
 <span data-ttu-id="a496a-113">可以在 app.config 文件中指定连接字符串。</span><span class="sxs-lookup"><span data-stu-id="a496a-113">You can specify a connection string in app.config file.</span></span>  
  
 <span data-ttu-id="a496a-114"><xref:System.Data.EntityClient> 还包含 <xref:System.Data.EntityClient.EntityConnectionStringBuilder> 类。</span><span class="sxs-lookup"><span data-stu-id="a496a-114">The <xref:System.Data.EntityClient> also includes the <xref:System.Data.EntityClient.EntityConnectionStringBuilder> class.</span></span> <span data-ttu-id="a496a-115">通过使用此类的属性和方法，开发人员可以使用此类以编程方式创建语法正确的连接字符串，并可以分析和重新生成现有的连接字符串。</span><span class="sxs-lookup"><span data-stu-id="a496a-115">This class enables developers to programmatically create syntactically correct connection strings, and parse and rebuild existing connection strings, by using properties and methods of the class.</span></span> <span data-ttu-id="a496a-116">有关详细信息，请参阅 [如何：生成 EntityConnection 连接字符串](how-to-build-an-entityconnection-connection-string.md)。</span><span class="sxs-lookup"><span data-stu-id="a496a-116">For more information, see [How to: Build an EntityConnection Connection String](how-to-build-an-entityconnection-connection-string.md).</span></span>  
  
## <a name="creating-queries"></a><span data-ttu-id="a496a-117">创建查询</span><span class="sxs-lookup"><span data-stu-id="a496a-117">Creating Queries</span></span>  

 <span data-ttu-id="a496a-118">[!INCLUDE[esql](../../../../../includes/esql-md.md)]语言是一种独立于存储的 SQL 方言，可直接处理概念实体架构，并支持实体数据模型的概念（例如继承和关系）。</span><span class="sxs-lookup"><span data-stu-id="a496a-118">The [!INCLUDE[esql](../../../../../includes/esql-md.md)] language is a storage-independent dialect of SQL that works directly with conceptual entity schemas and supports Entity Data Model concepts such as inheritance and relationships.</span></span> <span data-ttu-id="a496a-119"><xref:System.Data.EntityClient.EntityCommand> 类用于对实体模型执行 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 命令。</span><span class="sxs-lookup"><span data-stu-id="a496a-119">The <xref:System.Data.EntityClient.EntityCommand> class is used to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] command against an entity model.</span></span> <span data-ttu-id="a496a-120">构造 <xref:System.Data.EntityClient.EntityCommand> 对象时，可以指定一个存储过程名称或查询文本。</span><span class="sxs-lookup"><span data-stu-id="a496a-120">When you construct <xref:System.Data.EntityClient.EntityCommand> objects, you can specify a stored procedure name or a query text.</span></span> <span data-ttu-id="a496a-121">实体框架与存储特定的数据提供程序一起使用，以将泛型转换为 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 特定于存储的查询。</span><span class="sxs-lookup"><span data-stu-id="a496a-121">The Entity Framework works with storage-specific data providers to translate generic [!INCLUDE[esql](../../../../../includes/esql-md.md)] into storage-specific queries.</span></span> <span data-ttu-id="a496a-122">有关编写查询的详细信息 [!INCLUDE[esql](../../../../../includes/esql-md.md)] ，请参阅 [实体 SQL 语言](./language-reference/entity-sql-language.md)。</span><span class="sxs-lookup"><span data-stu-id="a496a-122">For more information about writing [!INCLUDE[esql](../../../../../includes/esql-md.md)] queries, see [Entity SQL Language](./language-reference/entity-sql-language.md).</span></span>  
  
 <span data-ttu-id="a496a-123">下面的示例创建一个 <xref:System.Data.EntityClient.EntityCommand> 对象，并 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 将查询文本分配给其 <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="a496a-123">The following example creates an <xref:System.Data.EntityClient.EntityCommand> object and assigns an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query text to its <xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a496a-124">此 [!INCLUDE[esql](../../../../../includes/esql-md.md)] 查询请求从概念模型中按标价排序的产品。</span><span class="sxs-lookup"><span data-stu-id="a496a-124">This [!INCLUDE[esql](../../../../../includes/esql-md.md)] query requests products ordered by the list price from the conceptual model.</span></span> <span data-ttu-id="a496a-125">下面的代码完全不识别存储模型。</span><span class="sxs-lookup"><span data-stu-id="a496a-125">The following code has no knowledge of the storage model at all.</span></span>  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a><span data-ttu-id="a496a-126">执行查询</span><span class="sxs-lookup"><span data-stu-id="a496a-126">Executing Queries</span></span>  

 <span data-ttu-id="a496a-127">执行查询时，查询将经过解析并转换为规范命令目录树。</span><span class="sxs-lookup"><span data-stu-id="a496a-127">When a query is executed, it is parsed and converted into a canonical command tree.</span></span> <span data-ttu-id="a496a-128">所有后续处理都在该命令目录树上执行。</span><span class="sxs-lookup"><span data-stu-id="a496a-128">All subsequent processing is performed on the command tree.</span></span> <span data-ttu-id="a496a-129">命令目录树是 <xref:System.Data.EntityClient> 与基础 .NET Framework 数据访问接口（如）之间的通信方式 <xref:System.Data.SqlClient> 。</span><span class="sxs-lookup"><span data-stu-id="a496a-129">The command tree is the means of communication between the <xref:System.Data.EntityClient> and the underlying .NET Framework data provider, such as <xref:System.Data.SqlClient>.</span></span>  
  
 <span data-ttu-id="a496a-130"><xref:System.Data.EntityClient.EntityDataReader> 公开对概念模型执行 <xref:System.Data.EntityClient.EntityCommand> 的结果。</span><span class="sxs-lookup"><span data-stu-id="a496a-130">The <xref:System.Data.EntityClient.EntityDataReader> exposes the results of executing a <xref:System.Data.EntityClient.EntityCommand> against a conceptual model.</span></span> <span data-ttu-id="a496a-131">若要执行返回 <xref:System.Data.EntityClient.EntityDataReader> 的命令，请调用 <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>。</span><span class="sxs-lookup"><span data-stu-id="a496a-131">To execute the command that returns the <xref:System.Data.EntityClient.EntityDataReader>, call <xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A>.</span></span> <span data-ttu-id="a496a-132"><xref:System.Data.EntityClient.EntityDataReader> 实现 <xref:System.Data.IExtendedDataRecord> 以描述丰富结构化的结果。</span><span class="sxs-lookup"><span data-stu-id="a496a-132">The <xref:System.Data.EntityClient.EntityDataReader> implements <xref:System.Data.IExtendedDataRecord> to describe rich structured results.</span></span>  
  
## <a name="managing-transactions"></a><span data-ttu-id="a496a-133">管理事务</span><span class="sxs-lookup"><span data-stu-id="a496a-133">Managing Transactions</span></span>  

 <span data-ttu-id="a496a-134">在实体框架中，有两种使用事务的方法：自动和显式。</span><span class="sxs-lookup"><span data-stu-id="a496a-134">In the Entity Framework, there are two ways to use transactions: automatic and explicit.</span></span> <span data-ttu-id="a496a-135">自动事务使用 <xref:System.Transactions> 命名空间，而显式事务使用 <xref:System.Data.EntityClient.EntityTransaction> 类。</span><span class="sxs-lookup"><span data-stu-id="a496a-135">Automatic transactions use the <xref:System.Transactions> namespace, and explicit transactions use the <xref:System.Data.EntityClient.EntityTransaction> class.</span></span>  
  
 <span data-ttu-id="a496a-136">若要更新通过概念模型公开的数据，请参阅 [如何：在实体框架中管理事务](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a496a-136">To update data that is exposed through a conceptual model, see [How to: Manage Transactions in the Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a496a-137">本节内容</span><span class="sxs-lookup"><span data-stu-id="a496a-137">In This Section</span></span>  

 [<span data-ttu-id="a496a-138">如何：生成 EntityConnection 连接字符串</span><span class="sxs-lookup"><span data-stu-id="a496a-138">How to: Build an EntityConnection Connection String</span></span>](how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="a496a-139">如何：执行返回 PrimitiveType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="a496a-139">How to: Execute a Query that Returns PrimitiveType Results</span></span>](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="a496a-140">如何：执行返回 StructuralType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="a496a-140">How to: Execute a Query that Returns StructuralType Results</span></span>](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="a496a-141">如何：执行返回 RefType 结果的查询</span><span class="sxs-lookup"><span data-stu-id="a496a-141">How to: Execute a Query that Returns RefType Results</span></span>](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="a496a-142">如何：执行返回复杂类型的查询</span><span class="sxs-lookup"><span data-stu-id="a496a-142">How to: Execute a Query that Returns Complex Types</span></span>](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="a496a-143">如何：执行返回嵌套集合的查询</span><span class="sxs-lookup"><span data-stu-id="a496a-143">How to: Execute a Query that Returns Nested Collections</span></span>](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="a496a-144">如何：使用 EntityCommand 执行参数化实体 SQL 查询</span><span class="sxs-lookup"><span data-stu-id="a496a-144">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="a496a-145">如何：使用 EntityCommand 执行参数化存储过程</span><span class="sxs-lookup"><span data-stu-id="a496a-145">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="a496a-146">如何：执行多态查询</span><span class="sxs-lookup"><span data-stu-id="a496a-146">How to: Execute a Polymorphic Query</span></span>](how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="a496a-147">如何：使用导航运算符导航关系</span><span class="sxs-lookup"><span data-stu-id="a496a-147">How to: Navigate Relationships with the Navigate Operator</span></span>](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a><span data-ttu-id="a496a-148">请参阅</span><span class="sxs-lookup"><span data-stu-id="a496a-148">See also</span></span>

- <span data-ttu-id="a496a-149">[管理连接和事务](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a496a-149">[Managing Connections and Transactions](/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))</span></span>
- [<span data-ttu-id="a496a-150">ADO.NET 实体框架</span><span class="sxs-lookup"><span data-stu-id="a496a-150">ADO.NET Entity Framework</span></span>](index.md)
- [<span data-ttu-id="a496a-151">语言参考</span><span class="sxs-lookup"><span data-stu-id="a496a-151">Language Reference</span></span>](./language-reference/index.md)
