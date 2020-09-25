---
title: 查询表达式语法示例：联接运算符 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f4d86667-3392-470d-a076-5ca6cbb660f6
ms.openlocfilehash: 637b815553d7c7f9a5fb4ffe644d2975468e1090
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189092"
---
# <a name="query-expression-syntax-examples-join-operators-linq-to-dataset"></a><span data-ttu-id="7c031-102">查询表达式语法示例：联接运算符 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7c031-102">Query Expression Syntax Examples: Join Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="7c031-103">联接是面向相互之间没有可导航关系的数据源（如关系数据库表）的查询中的一项重要操作。</span><span class="sxs-lookup"><span data-stu-id="7c031-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="7c031-104">联接两个数据源就是将一个数据源中的对象与另一个数据源中具有相同公共属性的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="7c031-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="7c031-105">有关详细信息，请参阅 [标准查询运算符概述 (c # ) ](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 或 [标准查询运算符概述 (Visual Basic) ](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="7c031-105">For more information, see [Standard Query Operators Overview (C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) or [Standard Query Operators Overview (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).</span></span>  
  
 <span data-ttu-id="7c031-106">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法以便使用查询表达式语法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="7c031-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7c031-107">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="7c031-107">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7c031-108">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="7c031-108">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7c031-109">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="7c031-109">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7c031-110">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="7c031-110">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="groupjoin"></a><span data-ttu-id="7c031-111">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="7c031-111">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c031-112">示例</span><span class="sxs-lookup"><span data-stu-id="7c031-112">Example</span></span>  

 <span data-ttu-id="7c031-113">此示例对 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 `SalesOrderHeader` 表执行 `SalesOrderDetail` 以得出每个客户的订单数。</span><span class="sxs-lookup"><span data-stu-id="7c031-113">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `SalesOrderHeader` and `SalesOrderDetail` tables to find the number of orders per customer.</span></span> <span data-ttu-id="7c031-114">组联接等效于左外部联接，它返回第一个（左侧）数据源的每个元素（即使其他数据源中没有关联元素）。</span><span class="sxs-lookup"><span data-stu-id="7c031-114">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="7c031-115">示例</span><span class="sxs-lookup"><span data-stu-id="7c031-115">Example</span></span>  

 <span data-ttu-id="7c031-116">此示例对 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 `Contact` 表执行 `SalesOrderHeader`。</span><span class="sxs-lookup"><span data-stu-id="7c031-116">This example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the `Contact` and `SalesOrderHeader` tables.</span></span> <span data-ttu-id="7c031-117">组联接等效于左外部联接，它返回第一个（左侧）数据源的每个元素（即使其他数据源中没有关联元素）。</span><span class="sxs-lookup"><span data-stu-id="7c031-117">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP LINQ to DataSet Examples#GroupJoin](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="7c031-118">联接</span><span class="sxs-lookup"><span data-stu-id="7c031-118">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c031-119">示例</span><span class="sxs-lookup"><span data-stu-id="7c031-119">Example</span></span>  

 <span data-ttu-id="7c031-120">此示例对 `SalesOrderHeader` 和 `SalesOrderDetail` 表执行联接，以获取八月份的联机订单。</span><span class="sxs-lookup"><span data-stu-id="7c031-120">This example performs a join over the `SalesOrderHeader` and `SalesOrderDetail` tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="7c031-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="7c031-121">See also</span></span>

- [<span data-ttu-id="7c031-122">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="7c031-122">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7c031-123">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="7c031-123">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7c031-124">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="7c031-124">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7c031-125">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c031-125">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
