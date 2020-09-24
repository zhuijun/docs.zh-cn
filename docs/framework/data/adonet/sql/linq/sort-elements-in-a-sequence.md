---
title: 在序列中对元素进行排序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: b594e756b099aa94e1043fd4256da3eff46d0d95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91155752"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="d44f7-102">在序列中对元素进行排序</span><span class="sxs-lookup"><span data-stu-id="d44f7-102">Sort Elements in a Sequence</span></span>

<span data-ttu-id="d44f7-103">使用 <xref:System.Linq.Enumerable.OrderBy%2A> 运算符可按一个或多个键对序列进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="d44f7-104">设计为支持按简单的基元类型（如 `string`、`int` 等）进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="d44f7-105">它不支持对复杂的多值类（如匿名类型）进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="d44f7-106">它也不支持 `byte` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="d44f7-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d44f7-107">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-107">Example</span></span>  

 <span data-ttu-id="d44f7-108">下面的示例按雇佣日期对 `Employees` 进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="d44f7-109">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-109">Example</span></span>  

 <span data-ttu-id="d44f7-110">下面的示例使用 `where` 按运费对运往 `Orders` 的 `London` 进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="d44f7-111">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-111">Example</span></span>  

 <span data-ttu-id="d44f7-112">下面的示例按单价从高到底对 `Products` 进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="d44f7-113">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-113">Example</span></span>  

 <span data-ttu-id="d44f7-114">下面的示例使用复合的 `OrderBy` 先按城市后按联系人姓名对 `Customers` 进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="d44f7-115">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-115">Example</span></span>  

 <span data-ttu-id="d44f7-116">下面的示例按从 `EmployeeID 1` `ShipCountry` 到最高到最低的运费对订单进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="d44f7-117">示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-117">Example</span></span>  

 <span data-ttu-id="d44f7-118">下面的示例结合使用 <xref:System.Linq.Enumerable.OrderBy%2A>、<xref:System.Linq.Enumerable.Max%2A> 和 <xref:System.Linq.Enumerable.GroupBy%2A> 运算符查找每个类别中单价最高的 `Products`，然后按类别 ID 对组进行排序。</span><span class="sxs-lookup"><span data-stu-id="d44f7-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="d44f7-119">如果您对 Northwind 示例数据库运行上一个查询，所得到的结果将与如下内容类似：</span><span class="sxs-lookup"><span data-stu-id="d44f7-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="d44f7-120">请参阅</span><span class="sxs-lookup"><span data-stu-id="d44f7-120">See also</span></span>

- [<span data-ttu-id="d44f7-121">查询示例</span><span class="sxs-lookup"><span data-stu-id="d44f7-121">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="d44f7-122">下载示例数据库</span><span class="sxs-lookup"><span data-stu-id="d44f7-122">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
