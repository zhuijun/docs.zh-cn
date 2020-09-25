---
title: 查询表达式语法示例：投影 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: e003c4356c2ab32814ac7a76ce008e21fb34192e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183164"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="1fcbf-102">查询表达式语法示例：投影 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1fcbf-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>

<span data-ttu-id="1fcbf-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法以便使用查询表达式语法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="1fcbf-104">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="1fcbf-105">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="1fcbf-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="1fcbf-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="1fcbf-107">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="1fcbf-108">选择</span><span class="sxs-lookup"><span data-stu-id="1fcbf-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="1fcbf-109">示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-109">Example</span></span>  

 <span data-ttu-id="1fcbf-110">此示例使用 <xref:System.Linq.Enumerable.Select%2A> 方法返回 `Product` 表中的所有行并显示产品名称。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="1fcbf-111">示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-111">Example</span></span>  

 <span data-ttu-id="1fcbf-112">此示例使用 <xref:System.Linq.Enumerable.Select%2A> 仅返回一系列产品名称。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="1fcbf-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="1fcbf-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="1fcbf-114">示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-114">Example</span></span>  

 <span data-ttu-id="1fcbf-115">此示例使用 `From …, …` (等效于 <xref:System.Linq.Enumerable.SelectMany%2A> 方法）来选择 `TotalDue` 小于 500.00 的所有订单。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="1fcbf-116">示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-116">Example</span></span>  

 <span data-ttu-id="1fcbf-117">此示例使用 `From …, …`（等效于 <xref:System.Linq.Enumerable.SelectMany%2A> 方法）来选择于 2002 年 10 月 1 日或之后达成的所有订单。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="1fcbf-118">示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-118">Example</span></span>  

 <span data-ttu-id="1fcbf-119">此示例使用 `From …, …` （等效于 <xref:System.Linq.Enumerable.SelectMany%2A> 方法）来选择订单总额大于 10000.00 的所有订单，并使用 `From` 赋值以避免请求二次总额。</span><span class="sxs-lookup"><span data-stu-id="1fcbf-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="1fcbf-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="1fcbf-120">See also</span></span>

- [<span data-ttu-id="1fcbf-121">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="1fcbf-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="1fcbf-122">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="1fcbf-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="1fcbf-123">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fcbf-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1fcbf-124">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1fcbf-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
