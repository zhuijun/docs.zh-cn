---
title: 基于方法的查询语法示例：分组
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cb23c25c-1075-4cc3-a8ff-4db72e536c0d
ms.openlocfilehash: 2d84e755217878bfa248add37a752224a20d3f84
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191978"
---
# <a name="method-based-query-syntax-examples-grouping"></a><span data-ttu-id="c78cd-102">基于方法的查询语法示例：分组</span><span class="sxs-lookup"><span data-stu-id="c78cd-102">Method-Based Query Syntax Examples: Grouping</span></span>

<span data-ttu-id="c78cd-103">本主题中的示例说明如何使用 `GroupBy` 方法通过使用基于方法的查询语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="c78cd-103">The examples in this topic show you how to use the `GroupBy` method to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using method-based query syntax.</span></span> <span data-ttu-id="c78cd-104">这些示例中使用的 AdventureWorks 销售模型基于 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 表生成。</span><span class="sxs-lookup"><span data-stu-id="c78cd-104">The AdventureWorks Sales Model that is used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="c78cd-105">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="c78cd-105">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="c78cd-106">示例</span><span class="sxs-lookup"><span data-stu-id="c78cd-106">Example</span></span>  

 <span data-ttu-id="c78cd-107">下面的示例使用 `GroupBy` 方法来返回按邮政编码分组的 `Address` 对象。</span><span class="sxs-lookup"><span data-stu-id="c78cd-107">The following example uses the `GroupBy` method to return `Address` objects that are grouped by postal code.</span></span> <span data-ttu-id="c78cd-108">这些结果将投影到一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="c78cd-108">The results are projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple3_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple3_mq)]  
  
## <a name="example"></a><span data-ttu-id="c78cd-109">示例</span><span class="sxs-lookup"><span data-stu-id="c78cd-109">Example</span></span>  

 <span data-ttu-id="c78cd-110">下面的示例使用 `GroupBy` 方法来返回按联系人姓氏的首字母分组的 `Contact` 对象。</span><span class="sxs-lookup"><span data-stu-id="c78cd-110">The following example uses the `GroupBy` method to return `Contact` objects that are grouped by the first letter of the contact's last name.</span></span> <span data-ttu-id="c78cd-111">这些结果还按姓氏的首字母进行排序，并投影到一个匿名类型。</span><span class="sxs-lookup"><span data-stu-id="c78cd-111">The results are also sorted by the first letter of the last name and projected into an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbysimple2_mq)]
 [!code-vb[DP L2E Examples#GroupBySimple2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbysimple2_mq)]  
  
## <a name="example"></a><span data-ttu-id="c78cd-112">示例</span><span class="sxs-lookup"><span data-stu-id="c78cd-112">Example</span></span>  

 <span data-ttu-id="c78cd-113">下面的示例使用 `GroupBy` 方法来返回按客户 ID 分组的 `SalesOrderHeader` 对象。</span><span class="sxs-lookup"><span data-stu-id="c78cd-113">The following example uses the `GroupBy` method to return `SalesOrderHeader` objects that are grouped by customer ID.</span></span> <span data-ttu-id="c78cd-114">同时还返回每个客户的销售数量。</span><span class="sxs-lookup"><span data-stu-id="c78cd-114">The number of sales for each customer is also returned.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupbycount_mq)]
 [!code-vb[DP L2E Examples#GroupByCount_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupbycount_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="c78cd-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="c78cd-115">See also</span></span>

- [<span data-ttu-id="c78cd-116">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="c78cd-116">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
