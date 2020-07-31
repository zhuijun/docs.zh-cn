---
title: Join 操作（C#）
description: 联接两个数据源时可将对象与跨数据源共享属性的对象相关联。 了解 C# 中的 LINQ 框架的联接方法。
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- Join
- GroupJoin
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165697"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="ab18c-104">Join 操作（C#）</span><span class="sxs-lookup"><span data-stu-id="ab18c-104">Join Operations (C#)</span></span>

<span data-ttu-id="ab18c-105">联接两个数据源就是将一个数据源中的对象与另一个数据源中具有相同公共属性的对象相关联。</span><span class="sxs-lookup"><span data-stu-id="ab18c-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="ab18c-106">当查询所面向的数据源相互之间具有无法直接领会的关系时，Join 就成为一项重要的运算。</span><span class="sxs-lookup"><span data-stu-id="ab18c-106">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="ab18c-107">在面向对象的编程中，这可能意味着在未建模对象之间进行关联，例如对单向关系进行反向推理。</span><span class="sxs-lookup"><span data-stu-id="ab18c-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="ab18c-108">下面是单向关系的一个示例：Customer 类有一个类型为 City 的属性，但 City 类没有作为 Customer 对象集合的属性。</span><span class="sxs-lookup"><span data-stu-id="ab18c-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="ab18c-109">如果你具有一个 City 对象列表，并且要查找每个城市中的所有客户，则可以使用联接运算完成此项查找。</span><span class="sxs-lookup"><span data-stu-id="ab18c-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="ab18c-110">LINQ 框架中提供的 join 方法包括 <xref:System.Linq.Enumerable.Join%2A> 和 <xref:System.Linq.Enumerable.GroupJoin%2A>。</span><span class="sxs-lookup"><span data-stu-id="ab18c-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="ab18c-111">这些方法执行同等联接，即根据 2 个数据源的键是否相等来匹配这 2 个数据源的联接。</span><span class="sxs-lookup"><span data-stu-id="ab18c-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="ab18c-112">（与此相较，Transact-SQL 支持除“等于”之外的联接运算符，例如“小于”运算符。）用关系数据库术语表达，就是说 <xref:System.Linq.Enumerable.Join%2A> 实现了内部联接，这种联接只返回那些在另一个数据集中具有匹配项的对象。</span><span class="sxs-lookup"><span data-stu-id="ab18c-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="ab18c-113"><xref:System.Linq.Enumerable.GroupJoin%2A> 方法在关系数据库术语中没有直接等效项，但实现了内部联接和左外部联接的超集。</span><span class="sxs-lookup"><span data-stu-id="ab18c-113">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="ab18c-114">左外部联接是指返回第一个（左侧）数据源的每个元素的联接，即使其他数据源中没有关联元素。</span><span class="sxs-lookup"><span data-stu-id="ab18c-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="ab18c-115">下图显示了一个概念性视图，其中包含两个集合以及这两个集合中的包含在内部联接或左外部联接中的元素。</span><span class="sxs-lookup"><span data-stu-id="ab18c-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![显示内部/外部的两个重叠圆圈。](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="ab18c-117">方法</span><span class="sxs-lookup"><span data-stu-id="ab18c-117">Methods</span></span>  
  
|<span data-ttu-id="ab18c-118">方法名</span><span class="sxs-lookup"><span data-stu-id="ab18c-118">Method Name</span></span>|<span data-ttu-id="ab18c-119">描述</span><span class="sxs-lookup"><span data-stu-id="ab18c-119">Description</span></span>|<span data-ttu-id="ab18c-120">C# 查询表达式语法</span><span class="sxs-lookup"><span data-stu-id="ab18c-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="ab18c-121">详细信息</span><span class="sxs-lookup"><span data-stu-id="ab18c-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="ab18c-122">根据键选择器函数 Join 两个序列并提取值对。</span><span class="sxs-lookup"><span data-stu-id="ab18c-122">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="ab18c-123">根据键选择器函数 Join 两个序列，并对每个元素的结果匹配项进行分组。</span><span class="sxs-lookup"><span data-stu-id="ab18c-123">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ab18c-124">查询表达式语法示例</span><span class="sxs-lookup"><span data-stu-id="ab18c-124">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="ab18c-125">下面的示例使用 `join … in … on … equals …` 子句基于特定值联接两个序列：</span><span class="sxs-lookup"><span data-stu-id="ab18c-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="ab18c-126">下面的示例使用 `join … in … on … equals … into …` 子句基于特定值联接两个序列，并对每个元素的结果匹配项进行分组：</span><span class="sxs-lookup"><span data-stu-id="ab18c-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="ab18c-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="ab18c-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="ab18c-128">标准查询运算符概述 (C#)</span><span class="sxs-lookup"><span data-stu-id="ab18c-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="ab18c-129">匿名类型</span><span class="sxs-lookup"><span data-stu-id="ab18c-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="ab18c-130">构建 Join 和跨产品查询</span><span class="sxs-lookup"><span data-stu-id="ab18c-130">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="ab18c-131">join 子句</span><span class="sxs-lookup"><span data-stu-id="ab18c-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="ab18c-132">使用组合键 Join</span><span class="sxs-lookup"><span data-stu-id="ab18c-132">Join by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="ab18c-133">如何联接不同文件的内容 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab18c-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="ab18c-134">对 Join 子句的结果进行排序</span><span class="sxs-lookup"><span data-stu-id="ab18c-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="ab18c-135">执行自定义联接操作</span><span class="sxs-lookup"><span data-stu-id="ab18c-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="ab18c-136">执行分组联接</span><span class="sxs-lookup"><span data-stu-id="ab18c-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="ab18c-137">执行内部联接</span><span class="sxs-lookup"><span data-stu-id="ab18c-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="ab18c-138">执行左外部联接</span><span class="sxs-lookup"><span data-stu-id="ab18c-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="ab18c-139">如何从多个源填充对象集合 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ab18c-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
