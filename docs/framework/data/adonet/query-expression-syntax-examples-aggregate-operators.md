---
title: 查询表达式语法示例：聚合运算符 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 85dafa07-e102-46e7-ab78-37bf06f257a6
ms.openlocfilehash: 2277058c4dad4632f4f47a39e32463eaf77dcd5e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164566"
---
# <a name="query-expression-syntax-examples-aggregate-operators-linq-to-dataset"></a><span data-ttu-id="91165-102">查询表达式语法示例：聚合运算符 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="91165-102">Query Expression Syntax Examples: Aggregate Operators (LINQ to DataSet)</span></span>

<span data-ttu-id="91165-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Sum%2A> 方法来查询 <xref:System.Data.DataSet> 并使用查询表达式语法聚合数据。</span><span class="sxs-lookup"><span data-stu-id="91165-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Average%2A>, <xref:System.Linq.Enumerable.Count%2A>, <xref:System.Linq.Enumerable.Max%2A>, <xref:System.Linq.Enumerable.Min%2A>, and <xref:System.Linq.Enumerable.Sum%2A> methods to query a <xref:System.Data.DataSet> and aggregate data using query expression syntax.</span></span>  
  
 <span data-ttu-id="91165-104">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="91165-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="91165-105">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="91165-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="91165-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="91165-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="91165-107">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="91165-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="average"></a><span data-ttu-id="91165-108">平均值</span><span class="sxs-lookup"><span data-stu-id="91165-108">Average</span></span>  
  
### <a name="example"></a><span data-ttu-id="91165-109">示例</span><span class="sxs-lookup"><span data-stu-id="91165-109">Example</span></span>  

 <span data-ttu-id="91165-110">此示例使用 <xref:System.Linq.Enumerable.Average%2A> 方法来计算每种款式的产品的平均定价。</span><span class="sxs-lookup"><span data-stu-id="91165-110">This example uses the <xref:System.Linq.Enumerable.Average%2A> method to find the average list price of the products of each style.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#average2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#Average2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#average2_mq)]  
  
### <a name="example"></a><span data-ttu-id="91165-111">示例</span><span class="sxs-lookup"><span data-stu-id="91165-111">Example</span></span>  

 <span data-ttu-id="91165-112">此示例使用 <xref:System.Linq.Enumerable.Average%2A> 获取每个联系人 ID 的总平均应付金额。</span><span class="sxs-lookup"><span data-stu-id="91165-112">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the average total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averagegrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averagegrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="91165-113">示例</span><span class="sxs-lookup"><span data-stu-id="91165-113">Example</span></span>  

 <span data-ttu-id="91165-114">此示例使用 <xref:System.Linq.Enumerable.Average%2A> 获取每个联系人的具有平均 `TotalDue` 的订单。</span><span class="sxs-lookup"><span data-stu-id="91165-114">This example uses <xref:System.Linq.Enumerable.Average%2A> to get the orders with the average `TotalDue` for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#averageelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#AverageElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#averageelements_mq)]  
  
## <a name="count"></a><span data-ttu-id="91165-115">Count</span><span class="sxs-lookup"><span data-stu-id="91165-115">Count</span></span>  
  
### <a name="example"></a><span data-ttu-id="91165-116">示例</span><span class="sxs-lookup"><span data-stu-id="91165-116">Example</span></span>  

 <span data-ttu-id="91165-117">此示例使用 <xref:System.Linq.Enumerable.Count%2A> 返回联系人 ID 的列表及每个联系人 ID 的订单数。</span><span class="sxs-lookup"><span data-stu-id="91165-117">This example uses <xref:System.Linq.Enumerable.Count%2A> to return a list of contact IDs and how many orders each has.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countnested)]
 [!code-vb[DP LINQ to DataSet Examples#CountNested](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countnested)]  
  
### <a name="example"></a><span data-ttu-id="91165-118">示例</span><span class="sxs-lookup"><span data-stu-id="91165-118">Example</span></span>  

 <span data-ttu-id="91165-119">此示例按颜色对产品分组并使用 <xref:System.Linq.Enumerable.Count%2A> 返回每个颜色组中的产品数目。</span><span class="sxs-lookup"><span data-stu-id="91165-119">This example groups products by color and uses <xref:System.Linq.Enumerable.Count%2A> to return the number of products in each color group.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#countgrouped)]
 [!code-vb[DP LINQ to DataSet Examples#CountGrouped](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#countgrouped)]  
  
## <a name="max"></a><span data-ttu-id="91165-120">最大值</span><span class="sxs-lookup"><span data-stu-id="91165-120">Max</span></span>  
  
### <a name="example"></a><span data-ttu-id="91165-121">示例</span><span class="sxs-lookup"><span data-stu-id="91165-121">Example</span></span>  

 <span data-ttu-id="91165-122">此示例使用 <xref:System.Linq.Enumerable.Max%2A> 方法获取每个联系人 ID 的最大总应付金额。</span><span class="sxs-lookup"><span data-stu-id="91165-122">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the largest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxgrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="91165-123">示例</span><span class="sxs-lookup"><span data-stu-id="91165-123">Example</span></span>  

 <span data-ttu-id="91165-124">此示例使用 <xref:System.Linq.Enumerable.Max%2A> 方法获取每个联系人 ID 的具有最大 `TotalDue` 的订单。</span><span class="sxs-lookup"><span data-stu-id="91165-124">This example uses the <xref:System.Linq.Enumerable.Max%2A> method to get the orders with the largest `TotalDue` for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#maxelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MaxElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#maxelements_mq)]  
  
## <a name="min"></a><span data-ttu-id="91165-125">Min</span><span class="sxs-lookup"><span data-stu-id="91165-125">Min</span></span>  
  
### <a name="example"></a><span data-ttu-id="91165-126">示例</span><span class="sxs-lookup"><span data-stu-id="91165-126">Example</span></span>  

 <span data-ttu-id="91165-127">此示例使用 <xref:System.Linq.Enumerable.Min%2A> 方法获取每个联系人 ID 的最小总应付金额。</span><span class="sxs-lookup"><span data-stu-id="91165-127">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the smallest total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#mingrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#mingrouped_mq)]  
  
### <a name="example"></a><span data-ttu-id="91165-128">示例</span><span class="sxs-lookup"><span data-stu-id="91165-128">Example</span></span>  

 <span data-ttu-id="91165-129">此示例使用 <xref:System.Linq.Enumerable.Min%2A> 方法获取每个联系人的具有最小总应付金额的订单。</span><span class="sxs-lookup"><span data-stu-id="91165-129">This example uses the <xref:System.Linq.Enumerable.Min%2A> method to get the orders with the smallest total due for each contact.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#minelements_mq)]
 [!code-vb[DP LINQ to DataSet Examples#MinElements_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#minelements_mq)]  
  
## <a name="sum"></a><span data-ttu-id="91165-130">Sum</span><span class="sxs-lookup"><span data-stu-id="91165-130">Sum</span></span>  
  
### <a name="example"></a><span data-ttu-id="91165-131">示例</span><span class="sxs-lookup"><span data-stu-id="91165-131">Example</span></span>  

 <span data-ttu-id="91165-132">此示例使用 <xref:System.Linq.Enumerable.Sum%2A> 方法获取每个联系人 ID 的总应付金额。</span><span class="sxs-lookup"><span data-stu-id="91165-132">This example uses the <xref:System.Linq.Enumerable.Sum%2A> method to get the total due for each contact ID.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#sumgrouped_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SumGrouped_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#sumgrouped_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="91165-133">请参阅</span><span class="sxs-lookup"><span data-stu-id="91165-133">See also</span></span>

- [<span data-ttu-id="91165-134">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="91165-134">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="91165-135">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="91165-135">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="91165-136">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="91165-136">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="91165-137">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91165-137">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
