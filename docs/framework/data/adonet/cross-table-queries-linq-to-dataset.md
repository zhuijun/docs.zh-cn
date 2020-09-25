---
title: 跨表查询 (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6819a16f-8656-41af-a54d-dfec0cb66366
ms.openlocfilehash: a209cfe4142ad8ebdbce1d715a76ac27300f4e19
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202391"
---
# <a name="cross-table-queries-linq-to-dataset"></a><span data-ttu-id="18c4d-102">跨表查询 (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="18c4d-102">Cross-Table Queries (LINQ to DataSet)</span></span>

<span data-ttu-id="18c4d-103">除了查询单个表外，还可以在 LINQ to DataSet 中执行交叉表查询。</span><span class="sxs-lookup"><span data-stu-id="18c4d-103">In addition to querying a single table, you can also perform cross-table queries in LINQ to DataSet.</span></span> <span data-ttu-id="18c4d-104">这是通过使用 *联接*来完成的。</span><span class="sxs-lookup"><span data-stu-id="18c4d-104">This is done by using a *join*.</span></span> <span data-ttu-id="18c4d-105">联接就是将一个数据源中的对象与另一个数据源中具有相同公共属性的对象（例如产品或联系人 ID）相关联。</span><span class="sxs-lookup"><span data-stu-id="18c4d-105">A join is the association of objects in one data source with objects that share a common attribute in another data source, such as a product or contact ID.</span></span> <span data-ttu-id="18c4d-106">在面向对象的编程中，由于每个对象都有引用另一个对象的成员，所以对象间的关系相对较容易导航。</span><span class="sxs-lookup"><span data-stu-id="18c4d-106">In object-oriented programming, relationships between objects are relatively easy to navigate because each object has a member that references another object.</span></span> <span data-ttu-id="18c4d-107">但在外部数据库表中，导航关系不像这样简单。</span><span class="sxs-lookup"><span data-stu-id="18c4d-107">In external database tables, however, navigating relationships is not as straightforward.</span></span> <span data-ttu-id="18c4d-108">数据库表不包含内置关系。</span><span class="sxs-lookup"><span data-stu-id="18c4d-108">Database tables do not contain built-in relationships.</span></span> <span data-ttu-id="18c4d-109">在这些情况下，可以通过联接操作来匹配每个源中的元素。</span><span class="sxs-lookup"><span data-stu-id="18c4d-109">In these cases, the join operation can be used to match elements from each source.</span></span> <span data-ttu-id="18c4d-110">例如，假设有两个分别包含产品信息和销售信息的表，您可以使用联接操作来匹配同一销售订单的销售信息和产品。</span><span class="sxs-lookup"><span data-stu-id="18c4d-110">For example, given two tables that contain product information and sales information, you could use a join operation to match sales information and products for the same sales order.</span></span>  
  
 <span data-ttu-id="18c4d-111"> (LINQ) 框架的语言集成查询提供两个联接运算符： <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A> 。</span><span class="sxs-lookup"><span data-stu-id="18c4d-111">The Language-Integrated Query (LINQ) framework provides two join operators, <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="18c4d-112">这些运算符执行 *同等联接*：也就是说，仅当键相等时才匹配两个数据源的联接。</span><span class="sxs-lookup"><span data-stu-id="18c4d-112">These operators perform *equi-joins*: that is, joins that match two data sources only when their keys are equal.</span></span> <span data-ttu-id="18c4d-113"> (相反，Transact-sql 支持除之外的联接运算符 `equals` ，例如 `less than` 运算符。 ) </span><span class="sxs-lookup"><span data-stu-id="18c4d-113">(By contrast, Transact-SQL supports join operators other than `equals`, such as the `less than` operator.)</span></span>  
  
 <span data-ttu-id="18c4d-114">对于关系数据库，<xref:System.Linq.Enumerable.Join%2A> 实现内部联接。</span><span class="sxs-lookup"><span data-stu-id="18c4d-114">In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join.</span></span> <span data-ttu-id="18c4d-115">内部联接是仅返回在相对数据集中具有匹配对象的那些对象的一种联接类型。</span><span class="sxs-lookup"><span data-stu-id="18c4d-115">An inner join is a type of join in which only those objects that have a match in the opposite data set are returned.</span></span>  
  
 <span data-ttu-id="18c4d-116"><xref:System.Linq.Enumerable.GroupJoin%2A>运算符在关系数据库术语中没有直接等效项; 它们实现了内部联接和左外部联接的超集。</span><span class="sxs-lookup"><span data-stu-id="18c4d-116">The <xref:System.Linq.Enumerable.GroupJoin%2A> operators have no direct equivalent in relational database terms; they implement a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="18c4d-117">左外部联接是一种联接，它返回第一个 (左) 集合的每个元素，即使它在第二个集合中没有关联元素。</span><span class="sxs-lookup"><span data-stu-id="18c4d-117">A left outer join is a join that returns each element of the first (left) collection, even if it has no correlated elements in the second collection.</span></span>  
  
 <span data-ttu-id="18c4d-118">有关联接的详细信息，请参阅 [联接操作](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))。</span><span class="sxs-lookup"><span data-stu-id="18c4d-118">For more information about joins, see [Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18c4d-119">示例</span><span class="sxs-lookup"><span data-stu-id="18c4d-119">Example</span></span>  

 <span data-ttu-id="18c4d-120">下面的示例对 AdventureWorks 示例数据库中的 `SalesOrderHeader` 和 `SalesOrderDetail` 表执行传统联接以获取 8 月份以来的在线订单。</span><span class="sxs-lookup"><span data-stu-id="18c4d-120">The following example performs a traditional join of the `SalesOrderHeader` and `SalesOrderDetail` tables from the AdventureWorks sample database to obtain online orders from the month of August.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#join)]
 [!code-vb[DP LINQ to DataSet Examples#Join](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#join)]  
  
## <a name="see-also"></a><span data-ttu-id="18c4d-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="18c4d-121">See also</span></span>

- [<span data-ttu-id="18c4d-122">查询数据集</span><span class="sxs-lookup"><span data-stu-id="18c4d-122">Querying DataSets</span></span>](querying-datasets-linq-to-dataset.md)
- [<span data-ttu-id="18c4d-123">单表查询</span><span class="sxs-lookup"><span data-stu-id="18c4d-123">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)
- [<span data-ttu-id="18c4d-124">查询类型化数据集</span><span class="sxs-lookup"><span data-stu-id="18c4d-124">Querying Typed DataSets</span></span>](querying-typed-datasets.md)
- <span data-ttu-id="18c4d-125">[联接运算](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="18c4d-125">[Join Operations](/previous-versions/visualstudio/visual-studio-2013/bb397908(v=vs.120))</span></span>
- [<span data-ttu-id="18c4d-126">LINQ to DataSet 示例</span><span class="sxs-lookup"><span data-stu-id="18c4d-126">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
