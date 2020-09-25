---
title: 查询表达式语法示例：排序 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 653a4a97-1e4a-4b2d-8d24-7dbe1f2a5c84
ms.openlocfilehash: e29ce3a1cf666057ae717f0717af73db7be87e30
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189066"
---
# <a name="query-expression-syntax-examples-ordering-linq-to-dataset"></a><span data-ttu-id="6c2f3-102">查询表达式语法示例：排序 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="6c2f3-102">Query Expression Syntax Examples: Ordering (LINQ to DataSet)</span></span>

<span data-ttu-id="6c2f3-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.OrderByDescending%2A>、<xref:System.Linq.Enumerable.Reverse%2A> 和 <xref:System.Linq.Enumerable.ThenByDescending%2A> 方法来查询 <xref:System.Data.DataSet> 并使用查询表达式语法对结果排序。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.OrderByDescending%2A>, <xref:System.Linq.Enumerable.Reverse%2A>, and <xref:System.Linq.Enumerable.ThenByDescending%2A> methods to query a <xref:System.Data.DataSet> and order the results using the query expression syntax.</span></span>  
  
 <span data-ttu-id="6c2f3-104">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="6c2f3-105">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="6c2f3-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="6c2f3-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="6c2f3-107">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="orderby"></a><span data-ttu-id="6c2f3-108">OrderBy</span><span class="sxs-lookup"><span data-stu-id="6c2f3-108">OrderBy</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c2f3-109">示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-109">Example</span></span>  

 <span data-ttu-id="6c2f3-110">此示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 返回按姓氏排序的联系人列表。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-110">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to return a list of contacts ordered by last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple1)]  
  
### <a name="example"></a><span data-ttu-id="6c2f3-111">示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-111">Example</span></span>  

 <span data-ttu-id="6c2f3-112">此示例使用 <xref:System.Linq.Enumerable.OrderBy%2A> 按姓氏的长度对联系人列表排序。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-112">This example uses <xref:System.Linq.Enumerable.OrderBy%2A> to sort a list of contacts by length of last name.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbysimple2)]
 [!code-vb[DP LINQ to DataSet Examples#OrderBySimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbysimple2)]  
  
## <a name="orderbydescending"></a><span data-ttu-id="6c2f3-113">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="6c2f3-113">OrderByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c2f3-114">示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-114">Example</span></span>  

 <span data-ttu-id="6c2f3-115">此示例使用等效于 `orderby… descending` 方法的 `Order By … Descending` (<xref:System.Linq.Enumerable.OrderByDescending%2A>) 从高到低排序价格列表。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-115">This example uses `orderby… descending` (`Order By … Descending`), which is equivalent to the <xref:System.Linq.Enumerable.OrderByDescending%2A> method, to sort the price list from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#orderbydescendingsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#OrderByDescendingSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#orderbydescendingsimple1)]  
  
## <a name="reverse"></a><span data-ttu-id="6c2f3-116">Reverse</span><span class="sxs-lookup"><span data-stu-id="6c2f3-116">Reverse</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c2f3-117">示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-117">Example</span></span>  

 <span data-ttu-id="6c2f3-118">此示例使用 <xref:System.Linq.Enumerable.Reverse%2A> 创建 `OrderDate` 早于 2002 年 2 月 20 日的订单的列表。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-118">This example uses <xref:System.Linq.Enumerable.Reverse%2A> to create a list of orders where `OrderDate` is earlier than Feb 20, 2002.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#reverse)]
 [!code-vb[DP LINQ to DataSet Examples#Reverse](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#reverse)]  
  
## <a name="thenbydescending"></a><span data-ttu-id="6c2f3-119">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="6c2f3-119">ThenByDescending</span></span>  
  
### <a name="example"></a><span data-ttu-id="6c2f3-120">示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-120">Example</span></span>  

 <span data-ttu-id="6c2f3-121">此示例使用等效于 `OrderBy… Descending` 方法的 <xref:System.Linq.Enumerable.ThenByDescending%2A> 先按名称然后按定价从高到低对产品列表排序。</span><span class="sxs-lookup"><span data-stu-id="6c2f3-121">This example uses `OrderBy… Descending` , which is equivalent to the <xref:System.Linq.Enumerable.ThenByDescending%2A> method, to sort a list of products, first by name and then by list price, from highest to lowest.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#thenbydescendingsimple)]
 [!code-vb[DP LINQ to DataSet Examples#ThenByDescendingSimple](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#thenbydescendingsimple)]  
  
## <a name="see-also"></a><span data-ttu-id="6c2f3-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="6c2f3-122">See also</span></span>

- [<span data-ttu-id="6c2f3-123">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="6c2f3-123">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="6c2f3-124">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="6c2f3-124">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="6c2f3-125">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="6c2f3-125">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="6c2f3-126">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c2f3-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
