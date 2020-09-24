---
title: LINQ to Entities 中的已知问题和注意事项
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: acd71129-5ff0-4b4e-b266-c72cc0c53601
ms.openlocfilehash: 0d36461cea68383e070db80d85f596151bd9c2ae
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161953"
---
# <a name="known-issues-and-considerations-in-linq-to-entities"></a><span data-ttu-id="b4329-102">LINQ to Entities 中的已知问题和注意事项</span><span class="sxs-lookup"><span data-stu-id="b4329-102">Known Issues and Considerations in LINQ to Entities</span></span>

<span data-ttu-id="b4329-103">本部分提供有关 LINQ to Entities 查询的已知问题的信息。</span><span class="sxs-lookup"><span data-stu-id="b4329-103">This section provides information about known issues with LINQ to Entities queries.</span></span>  
  
- [<span data-ttu-id="b4329-104">不能缓存的 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="b4329-104">LINQ Queries That cannot be Cached</span></span>](#LINQQueriesThatAreNotCached)  
  
- [<span data-ttu-id="b4329-105">排序信息丢失</span><span class="sxs-lookup"><span data-stu-id="b4329-105">Ordering Information Lost</span></span>](#OrderingInfoLost)  
  
- [<span data-ttu-id="b4329-106">不支持无符号整数</span><span class="sxs-lookup"><span data-stu-id="b4329-106">Unsigned Integers Not Supported</span></span>](#UnsignedIntsUnsupported)  
  
- [<span data-ttu-id="b4329-107">类型转换错误</span><span class="sxs-lookup"><span data-stu-id="b4329-107">Type Conversion Errors</span></span>](#TypeConversionErrors)  
  
- [<span data-ttu-id="b4329-108">不支持引用非标量变量</span><span class="sxs-lookup"><span data-stu-id="b4329-108">Referencing Non-Scalar Variables Not Supported</span></span>](#RefNonScalarClosures)  
  
- [<span data-ttu-id="b4329-109">使用 SQL Server 2000，嵌套查询可能会失败</span><span class="sxs-lookup"><span data-stu-id="b4329-109">Nested Queries May Fail with SQL Server 2000</span></span>](#NestedQueriesSQL2000)  
  
- [<span data-ttu-id="b4329-110">投影到匿名类型</span><span class="sxs-lookup"><span data-stu-id="b4329-110">Projecting to an Anonymous Type</span></span>](#ProjectToAnonymousType)  
  
<a name="LINQQueriesThatAreNotCached"></a>

## <a name="linq-queries-that-cannot-be-cached"></a><span data-ttu-id="b4329-111">不能缓存的 LINQ 查询</span><span class="sxs-lookup"><span data-stu-id="b4329-111">LINQ Queries That cannot be Cached</span></span>  

 <span data-ttu-id="b4329-112">从 .NET Framework 4.5 开始，LINQ to Entities 查询是自动缓存的。</span><span class="sxs-lookup"><span data-stu-id="b4329-112">Starting with .NET Framework 4.5, LINQ to Entities queries are automatically cached.</span></span> <span data-ttu-id="b4329-113">但是，不自动缓存将 `Enumerable.Contains` 运算符应用到内存中集合的 LINQ to Entities 查询。</span><span class="sxs-lookup"><span data-stu-id="b4329-113">However, LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="b4329-114">此外，不允许在已编译的 LINQ 查询中参数化内存中的集合。</span><span class="sxs-lookup"><span data-stu-id="b4329-114">Also parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
<a name="OrderingInfoLost"></a>

## <a name="ordering-information-lost"></a><span data-ttu-id="b4329-115">排序信息丢失</span><span class="sxs-lookup"><span data-stu-id="b4329-115">Ordering Information Lost</span></span>  

 <span data-ttu-id="b4329-116">如果将列投影到匿名类型，则会在某些查询中丢失排序信息，这些查询将针对设置为兼容级别 "80" 的 SQL Server 2005 数据库执行。</span><span class="sxs-lookup"><span data-stu-id="b4329-116">Projecting columns into an anonymous type will cause ordering information to be lost in some queries that are executed against a SQL Server 2005 database set to a compatibility level of "80".</span></span>  <span data-ttu-id="b4329-117">当 order-by 列表中的列名与选择器中的列名相同时，就会发生这种情况，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="b4329-117">This occurs when a column name in the order-by list matches a column name in the selector, as shown in the following example:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt543840)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT543840](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt543840)]  
  
<a name="UnsignedIntsUnsupported"></a>

## <a name="unsigned-integers-not-supported"></a><span data-ttu-id="b4329-118">不支持无符号整数</span><span class="sxs-lookup"><span data-stu-id="b4329-118">Unsigned Integers Not Supported</span></span>  

 <span data-ttu-id="b4329-119">不支持在 LINQ to Entities 查询中指定无符号整数类型，因为实体框架不支持无符号整数。</span><span class="sxs-lookup"><span data-stu-id="b4329-119">Specifying an unsigned integer type in a LINQ to Entities query is not supported because the Entity Framework does not support unsigned integers.</span></span> <span data-ttu-id="b4329-120">如果指定无符号整数，则在 <xref:System.ArgumentException> 查询表达式转换过程中会引发异常，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="b4329-120">If you specify an unsigned integer, an <xref:System.ArgumentException> exception will be thrown during the query expression translation, as shown in the following example.</span></span> <span data-ttu-id="b4329-121">此示例查询其 ID 为 48000 的订单。</span><span class="sxs-lookup"><span data-stu-id="b4329-121">This example queries for an order with ID 48000.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#uintasqueryparam)]
 [!code-vb[DP L2E Conceptual Examples#UIntAsQueryParam](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#uintasqueryparam)]  
  
<a name="TypeConversionErrors"></a>

## <a name="type-conversion-errors"></a><span data-ttu-id="b4329-122">类型转换错误</span><span class="sxs-lookup"><span data-stu-id="b4329-122">Type Conversion Errors</span></span>  

 <span data-ttu-id="b4329-123">在 Visual Basic 中，如果使用 `CByte` 函数将某一属性映射到值为 1 且为 SQL Server 位类型的列，则会引发 <xref:System.Data.SqlClient.SqlException> 并显示“发生算术溢出错误”消息。</span><span class="sxs-lookup"><span data-stu-id="b4329-123">In Visual Basic, when a property is mapped to a column of SQL Server bit type with a value of 1 using the `CByte` function, a <xref:System.Data.SqlClient.SqlException> is thrown with an "Arithmetic overflow error" message.</span></span> <span data-ttu-id="b4329-124">下面的示例查询 AdventureWorks 示例数据库中的 `Product.MakeFlag` 列，在循环访问查询结果时引发一个异常。</span><span class="sxs-lookup"><span data-stu-id="b4329-124">The following example queries the `Product.MakeFlag` column in the AdventureWorks sample database and an exception is thrown when the query results are iterated over.</span></span>  
  
 [!code-vb[DP L2E Conceptual Examples#SBUDT544355](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt544355)]  
  
<a name="RefNonScalarClosures"></a>

## <a name="referencing-non-scalar-variables-not-supported"></a><span data-ttu-id="b4329-125">不支持引用非标量变量</span><span class="sxs-lookup"><span data-stu-id="b4329-125">Referencing Non-Scalar Variables Not Supported</span></span>  

 <span data-ttu-id="b4329-126">不支持在查询中引用非标量变量（如实体）。</span><span class="sxs-lookup"><span data-stu-id="b4329-126">Referencing a non-scalar variables, such as an entity, in a query is not supported.</span></span> <span data-ttu-id="b4329-127">在此类查询执行时，会引发 <xref:System.NotSupportedException> 异常，并显示以下消息：“无法创建类型为‘`EntityType`’的常量值。</span><span class="sxs-lookup"><span data-stu-id="b4329-127">When such a query executes, a <xref:System.NotSupportedException> exception is thrown with a message that states "Unable to create a constant value of type `EntityType`.</span></span> <span data-ttu-id="b4329-128">此上下文中仅支持基元类型(‘如 Int32、String 和 Guid’)。”[Unable to create a constant value of type 'Closure type'. Only primitive types ('such as Int32, String, and Guid') are supported in this context.]</span><span class="sxs-lookup"><span data-stu-id="b4329-128">Only primitive types ('such as Int32, String, and Guid') are supported in this context."</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4329-129">支持引用标量变量的集合。</span><span class="sxs-lookup"><span data-stu-id="b4329-129">Referencing a collection of scalar variables is supported.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#sbudt555877)]
 [!code-vb[DP L2E Conceptual Examples#SBUDT555877](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#sbudt555877)]  
  
<a name="NestedQueriesSQL2000"></a>

## <a name="nested-queries-may-fail-with-sql-server-2000"></a><span data-ttu-id="b4329-130">使用 SQL Server 2000，嵌套查询可能会失败</span><span class="sxs-lookup"><span data-stu-id="b4329-130">Nested Queries May Fail with SQL Server 2000</span></span>  

 <span data-ttu-id="b4329-131">使用 SQL Server 2000，如果 LINQ to Entities 查询生成具有三级或以上深度的嵌套 Transact-SQL 查询，则它们可能会失败。</span><span class="sxs-lookup"><span data-stu-id="b4329-131">With SQL Server 2000, LINQ to Entities queries may fail if they produce nested Transact-SQL queries that are three or more levels deep.</span></span>  
  
<a name="ProjectToAnonymousType"></a>

## <a name="projecting-to-an-anonymous-type"></a><span data-ttu-id="b4329-132">投影到匿名类型</span><span class="sxs-lookup"><span data-stu-id="b4329-132">Projecting to an Anonymous Type</span></span>  

 <span data-ttu-id="b4329-133">如果通过使用 <xref:System.Data.Objects.ObjectQuery%601.Include%2A> 上的 <xref:System.Data.Objects.ObjectQuery%601> 方法将初始查询路径定义为包括相关对象，然后使用 LINQ 将返回的对象投影到匿名类型，则查询结果中将不包含在 Include 方法中指定的对象。</span><span class="sxs-lookup"><span data-stu-id="b4329-133">If you define your initial query path to include related objects by using the <xref:System.Data.Objects.ObjectQuery%601.Include%2A> method on the <xref:System.Data.Objects.ObjectQuery%601> and then use LINQ to project the returned objects to an anonymous type, the objects specified in the include method are not included in the query results.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype1)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype1)]  
  
 <span data-ttu-id="b4329-134">若要获取相关对象，请勿将返回的类型投影到匿名类型。</span><span class="sxs-lookup"><span data-stu-id="b4329-134">To get related objects, do not project returned types to an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#projtoanontype2)]
 [!code-vb[DP L2E Conceptual Examples#ProjToAnonType2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#projtoanontype2)]  
  
## <a name="see-also"></a><span data-ttu-id="b4329-135">请参阅</span><span class="sxs-lookup"><span data-stu-id="b4329-135">See also</span></span>

- [<span data-ttu-id="b4329-136">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="b4329-136">LINQ to Entities</span></span>](linq-to-entities.md)
