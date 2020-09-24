---
title: 基于方法的查询语法示例：投影 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 2790ed3e7f8fc2fe6a5c920be8a79402692d6282
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147900"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="4331b-102">基于方法的查询语法示例：投影 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="4331b-102">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>

<span data-ttu-id="4331b-103">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.Select%2A> 和 <xref:System.Linq.Enumerable.SelectMany%2A> 方法以便使用基于方法的查询语法来查询 <xref:System.Data.DataSet>。</span><span class="sxs-lookup"><span data-stu-id="4331b-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="4331b-104">在 `FillDataSet` 这些示例中使用的方法是在将 [数据加载到数据集](loading-data-into-a-dataset.md)时指定的。</span><span class="sxs-lookup"><span data-stu-id="4331b-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="4331b-105">本主题中的示例使用 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表。</span><span class="sxs-lookup"><span data-stu-id="4331b-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="4331b-106">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="4331b-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="4331b-107">有关详细信息，请参阅 [如何：在 Visual Studio 中创建 LINQ to DataSet 项目](how-to-create-a-linq-to-dataset-project-in-vs.md)。</span><span class="sxs-lookup"><span data-stu-id="4331b-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="4331b-108">选择</span><span class="sxs-lookup"><span data-stu-id="4331b-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="4331b-109">示例</span><span class="sxs-lookup"><span data-stu-id="4331b-109">Example</span></span>  

 <span data-ttu-id="4331b-110">此示例使用 <xref:System.Linq.Enumerable.Select%2A> 方法将 `Name`、`ProductNumber` 和 `ListPrice` 属性投影到一系列匿名类型。</span><span class="sxs-lookup"><span data-stu-id="4331b-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="4331b-111">在生成的类型中，还将 `ListPrice` 属性重命名为 `Price`。</span><span class="sxs-lookup"><span data-stu-id="4331b-111">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="4331b-112">SelectMany</span><span class="sxs-lookup"><span data-stu-id="4331b-112">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="4331b-113">示例</span><span class="sxs-lookup"><span data-stu-id="4331b-113">Example</span></span>  

 <span data-ttu-id="4331b-114">此示例使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法来选择 `TotalDue` 小于 500.00 的所有订单。</span><span class="sxs-lookup"><span data-stu-id="4331b-114">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="4331b-115">示例</span><span class="sxs-lookup"><span data-stu-id="4331b-115">Example</span></span>  

 <span data-ttu-id="4331b-116">此示例使用 <xref:System.Linq.Enumerable.SelectMany%2A> 方法来选择于 2002 年 10 月 1 日或之后达成的所有订单。</span><span class="sxs-lookup"><span data-stu-id="4331b-116">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="4331b-117">请参阅</span><span class="sxs-lookup"><span data-stu-id="4331b-117">See also</span></span>

- [<span data-ttu-id="4331b-118">将数据加载到数据集中</span><span class="sxs-lookup"><span data-stu-id="4331b-118">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="4331b-119">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="4331b-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="4331b-120">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="4331b-120">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4331b-121">标准查询运算符概述 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4331b-121">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
