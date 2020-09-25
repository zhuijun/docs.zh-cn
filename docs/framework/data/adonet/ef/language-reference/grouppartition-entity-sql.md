---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204471"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="310f1-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="310f1-102">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="310f1-103">返回从聚合与之相关的当前组分区提取的参数值集合。</span><span class="sxs-lookup"><span data-stu-id="310f1-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="310f1-104">`GroupPartition` 聚合是基于组的聚合，没有基于集合的形式。</span><span class="sxs-lookup"><span data-stu-id="310f1-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310f1-105">语法</span><span class="sxs-lookup"><span data-stu-id="310f1-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="310f1-106">参数</span><span class="sxs-lookup"><span data-stu-id="310f1-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="310f1-107">任何 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 表达式。</span><span class="sxs-lookup"><span data-stu-id="310f1-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="310f1-108">备注</span><span class="sxs-lookup"><span data-stu-id="310f1-108">Remarks</span></span>  

 <span data-ttu-id="310f1-109">以下查询生成产品列表以及每个产品的订单行数量的集合。</span><span class="sxs-lookup"><span data-stu-id="310f1-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="310f1-110">以下两个查询在语义上是相同的：</span><span class="sxs-lookup"><span data-stu-id="310f1-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="310f1-111">`GROUPPARTITION` 运算符可以与用户定义的聚合函数结合使用。</span><span class="sxs-lookup"><span data-stu-id="310f1-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="310f1-112">`GROUPPARTITION` 是一个特殊的聚合运算符，它保留对于分组的输入集的引用。</span><span class="sxs-lookup"><span data-stu-id="310f1-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="310f1-113">此引用可以用在 GROUP BY 处于作用域内的查询中的任何位置。</span><span class="sxs-lookup"><span data-stu-id="310f1-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="310f1-114">例如：</span><span class="sxs-lookup"><span data-stu-id="310f1-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="310f1-115">对于常规 `GROUP BY` ，将隐藏分组的结果。</span><span class="sxs-lookup"><span data-stu-id="310f1-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="310f1-116">您只能在聚合函数中使用结果。</span><span class="sxs-lookup"><span data-stu-id="310f1-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="310f1-117">为了能够看到分组的结果，必须使用子查询使分组的结果与输入集相关。</span><span class="sxs-lookup"><span data-stu-id="310f1-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="310f1-118">下面两个查询是等效的：</span><span class="sxs-lookup"><span data-stu-id="310f1-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="310f1-119">如示例中所示，通过 GROUPPARTITION 聚合运算符，可以在分组后更轻松地获得对输入集的引用。</span><span class="sxs-lookup"><span data-stu-id="310f1-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="310f1-120">当您使用 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 参数时，GROUPPARTITION 运算符可以在运算符输入中指定任何 `expression` 表达式。</span><span class="sxs-lookup"><span data-stu-id="310f1-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="310f1-121">例如，下面针对组分区的所有输入表达式都是有效的：</span><span class="sxs-lookup"><span data-stu-id="310f1-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="310f1-122">示例</span><span class="sxs-lookup"><span data-stu-id="310f1-122">Example</span></span>  

 <span data-ttu-id="310f1-123">下面的示例演示如何将 GROUPPARTITION 子句与 GROUP BY 子句一起使用。</span><span class="sxs-lookup"><span data-stu-id="310f1-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="310f1-124">GROUP BY 子句按照 `SalesOrderHeader` 实体的 `Contact`对这些实体进行分组。</span><span class="sxs-lookup"><span data-stu-id="310f1-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="310f1-125">然后，GROUPPARTITION 子句投影每个组的 `TotalDue` 属性，而生成一个十进制值集合。</span><span class="sxs-lookup"><span data-stu-id="310f1-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
