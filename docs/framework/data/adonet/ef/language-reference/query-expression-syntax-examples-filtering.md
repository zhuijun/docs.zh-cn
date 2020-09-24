---
title: 查询表达式语法示例：筛选
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: feb05c0813587f8801aadd8bf64c4700badb2330
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152970"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="99dbd-102">查询表达式语法示例：筛选</span><span class="sxs-lookup"><span data-stu-id="99dbd-102">Query Expression Syntax Examples: Filtering</span></span>

<span data-ttu-id="99dbd-103">本主题中的示例演示如何使用 `Where` 和 `Where…Contains` 方法通过使用查询表达式语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="99dbd-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="99dbd-104">请注意，Where .。。`Contains`</span><span class="sxs-lookup"><span data-stu-id="99dbd-104">Note, Where…`Contains`</span></span> <span data-ttu-id="99dbd-105">不能用作 [已编译查询](compiled-queries-linq-to-entities.md)的一部分。</span><span class="sxs-lookup"><span data-stu-id="99dbd-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="99dbd-106">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="99dbd-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="99dbd-107">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="99dbd-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="99dbd-108">其中</span><span class="sxs-lookup"><span data-stu-id="99dbd-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="99dbd-109">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-109">Example</span></span>  

 <span data-ttu-id="99dbd-110">以下示例返回所有联机订单。</span><span class="sxs-lookup"><span data-stu-id="99dbd-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="99dbd-111">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-111">Example</span></span>  

 <span data-ttu-id="99dbd-112">以下示例返回订单数量大于 2 且小于 6 的订单。</span><span class="sxs-lookup"><span data-stu-id="99dbd-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="99dbd-113">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-113">Example</span></span>  

 <span data-ttu-id="99dbd-114">以下示例返回所有红色产品。</span><span class="sxs-lookup"><span data-stu-id="99dbd-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="99dbd-115">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-115">Example</span></span>  

 <span data-ttu-id="99dbd-116">以下示例使用 `Where` 方法以查找在 2003 年 12 月 1 日之后生成的订单，然后使用 `order.SalesOrderDetail` 导航属性以获取每个订单的详细信息。</span><span class="sxs-lookup"><span data-stu-id="99dbd-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="99dbd-117">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="99dbd-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="99dbd-118">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-118">Example</span></span>  

 <span data-ttu-id="99dbd-119">以下示例将一个数组用作 `Where…Contains` 子句的一部分，以查找 `ProductModelID` 与数组中的值匹配的所有产品。</span><span class="sxs-lookup"><span data-stu-id="99dbd-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="99dbd-120">作为 `Where…Contains` 子句中谓词的一部分，您可以使用 <xref:System.Array>、<xref:System.Collections.Generic.List%601> 或实现 <xref:System.Collections.Generic.IEnumerable%601> 接口的任何类型的集合。</span><span class="sxs-lookup"><span data-stu-id="99dbd-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="99dbd-121">还可以在 LINQ to Entities 查询中声明和初始化集合。</span><span class="sxs-lookup"><span data-stu-id="99dbd-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="99dbd-122">有关更多信息，请参见下一个示例。</span><span class="sxs-lookup"><span data-stu-id="99dbd-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="99dbd-123">示例</span><span class="sxs-lookup"><span data-stu-id="99dbd-123">Example</span></span>  

 <span data-ttu-id="99dbd-124">以下示例声明并初始化 `Where…Contains` 子句中的数组，以查找 `ProductModelID` 或 `Size` 与数组中的值匹配的所有产品。</span><span class="sxs-lookup"><span data-stu-id="99dbd-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="99dbd-125">请参阅</span><span class="sxs-lookup"><span data-stu-id="99dbd-125">See also</span></span>

- [<span data-ttu-id="99dbd-126">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="99dbd-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
