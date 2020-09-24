---
title: 查询表达式语法示例：联接运算符
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 343e8dda-70b2-409d-9334-ce9a880c3cea
ms.openlocfilehash: 3a99038f9432ffc485742587350e2752ba55706f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158391"
---
# <a name="query-expression-syntax-examples-join-operators"></a><span data-ttu-id="47a89-102">查询表达式语法示例：联接运算符</span><span class="sxs-lookup"><span data-stu-id="47a89-102">Query Expression Syntax Examples: Join Operators</span></span>

<span data-ttu-id="47a89-103">联接是面向相互之间没有可导航关系的数据源（如关系数据库表）的查询中的一项重要操作。</span><span class="sxs-lookup"><span data-stu-id="47a89-103">Joining is an important operation in queries that target data sources that have no navigable relationships to each other, such as relational database tables.</span></span> <span data-ttu-id="47a89-104">联接两个数据源就是将一个数据源中的对象与另一个数据源中具有相同公共属性的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="47a89-104">A join of two data sources is the association of objects in one data source with objects that share a common attribute in the other data source.</span></span> <span data-ttu-id="47a89-105">有关详细信息，请参阅 [标准查询运算符概述](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="47a89-105">For more information, see [Standard Query Operators Overview](/previous-versions/visualstudio/visual-studio-2013/bb397896(v=vs.120)).</span></span>  
  
 <span data-ttu-id="47a89-106">本主题中的示例演示如何使用 <xref:System.Linq.Enumerable.GroupJoin%2A> 和 <xref:System.Linq.Enumerable.Join%2A> 方法通过使用查询表达式语法来查询 [AdventureWorks 销售模型](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 。</span><span class="sxs-lookup"><span data-stu-id="47a89-106">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.GroupJoin%2A> and <xref:System.Linq.Enumerable.Join%2A> methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="47a89-107">这些示例中使用的 AdventureWorks 销售模型从 AdventureWorks 示例数据库中的 Contact、Address、Product、SalesOrderHeader 和 SalesOrderDetail 等表生成。</span><span class="sxs-lookup"><span data-stu-id="47a89-107">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="47a89-108">本主题中的示例使用以下 `using` / `Imports` 语句：</span><span class="sxs-lookup"><span data-stu-id="47a89-108">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="groupjoin"></a><span data-ttu-id="47a89-109">GroupJoin</span><span class="sxs-lookup"><span data-stu-id="47a89-109">GroupJoin</span></span>  
  
### <a name="example"></a><span data-ttu-id="47a89-110">示例</span><span class="sxs-lookup"><span data-stu-id="47a89-110">Example</span></span>  

 <span data-ttu-id="47a89-111">以下示例针对 SalesOrderHeader 表和 SalesOrderDetail 表执行 <xref:System.Linq.Enumerable.GroupJoin%2A> 以查找每个客户的订单数。</span><span class="sxs-lookup"><span data-stu-id="47a89-111">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the SalesOrderHeader and SalesOrderDetail tables to find the number of orders per customer.</span></span> <span data-ttu-id="47a89-112">组联接等效于左外部联接，它返回第一个（左侧）数据源的每个元素（即使其他数据源中没有关联元素）。</span><span class="sxs-lookup"><span data-stu-id="47a89-112">A group join is the equivalent of a left outer join, which returns each element of the first (left) data source, even if no correlated elements are in the other data source.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin2)]
 [!code-vb[DP L2E Examples#GroupJoin2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin2)]  
  
### <a name="example"></a><span data-ttu-id="47a89-113">示例</span><span class="sxs-lookup"><span data-stu-id="47a89-113">Example</span></span>  

 <span data-ttu-id="47a89-114">下面的示例对 Contact 和 SalesOrderHeader 表执行 <xref:System.Linq.Enumerable.GroupJoin%2A> 以查找每个联系人的订单数。</span><span class="sxs-lookup"><span data-stu-id="47a89-114">The following example performs a <xref:System.Linq.Enumerable.GroupJoin%2A> over the Contact and SalesOrderHeader tables to find the number of orders per contact.</span></span> <span data-ttu-id="47a89-115">将显示每个联系人的订单数和 ID。</span><span class="sxs-lookup"><span data-stu-id="47a89-115">The order count and IDs for each contact are displayed.</span></span>  
  
 [!code-csharp[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#groupjoin)]
 [!code-vb[DP L2E Examples#GroupJoin](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#groupjoin)]  
  
## <a name="join"></a><span data-ttu-id="47a89-116">联接</span><span class="sxs-lookup"><span data-stu-id="47a89-116">Join</span></span>  
  
### <a name="example"></a><span data-ttu-id="47a89-117">示例</span><span class="sxs-lookup"><span data-stu-id="47a89-117">Example</span></span>  

 <span data-ttu-id="47a89-118">以下示例针对 SalesOrderHeader 表和 SalesOrderDetail 表执行联接，以获得八月份的联机订单。</span><span class="sxs-lookup"><span data-stu-id="47a89-118">The following example performs a join over the SalesOrderHeader and SalesOrderDetail tables to get online orders from the month of August.</span></span>  
  
 [!code-csharp[DP L2E Examples#Join](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#join)]
 [!code-vb[DP L2E Examples#Join](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="47a89-119">请参阅</span><span class="sxs-lookup"><span data-stu-id="47a89-119">See also</span></span>

- [<span data-ttu-id="47a89-120">LINQ to Entities 中的查询</span><span class="sxs-lookup"><span data-stu-id="47a89-120">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
