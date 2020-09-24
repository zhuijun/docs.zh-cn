---
title: LINQ to Entities 查询中的表达式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
ms.openlocfilehash: f65759d37661271588d56965eadcccbe997623f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166646"
---
# <a name="expressions-in-linq-to-entities-queries"></a><span data-ttu-id="be4b3-102">LINQ to Entities 查询中的表达式</span><span class="sxs-lookup"><span data-stu-id="be4b3-102">Expressions in LINQ to Entities Queries</span></span>

<span data-ttu-id="be4b3-103">表达式是求值结果可以为单个值、对象、方法或命名空间的一段代码。</span><span class="sxs-lookup"><span data-stu-id="be4b3-103">An expression is a fragment of code that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="be4b3-104">表达式可以包含文本值、方法调用、运算符及其操作数，或者简单名称。</span><span class="sxs-lookup"><span data-stu-id="be4b3-104">Expressions can contain a literal value, a method call, an operator and its operands, or a simple name.</span></span> <span data-ttu-id="be4b3-105">简单名称可以是变量名、类型成员名、方法参数名、命名空间名或类型名。</span><span class="sxs-lookup"><span data-stu-id="be4b3-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span> <span data-ttu-id="be4b3-106">表达式可以使用运算符（运算符又可使用其他表达式作为参数）或方法调用（方法调用的参数又可以是其他方法调用）。</span><span class="sxs-lookup"><span data-stu-id="be4b3-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls.</span></span> <span data-ttu-id="be4b3-107">因此，表达式可以非常简单，也可以极其复杂。</span><span class="sxs-lookup"><span data-stu-id="be4b3-107">Therefore, expressions can range from simple to very complex.</span></span>  
  
 <span data-ttu-id="be4b3-108">在 LINQ to Entities 查询中，表达式可以包含命名空间中的类型所允许的任何内容 <xref:System.Linq.Expressions> ，包括 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="be4b3-108">In LINQ to Entities queries, expressions can contain anything allowed by the types within the <xref:System.Linq.Expressions> namespace, including lambda expressions.</span></span> <span data-ttu-id="be4b3-109">可在 LINQ to Entities 查询中使用的表达式是可用于查询实体框架的表达式的超集。作为对实体框架的查询的一部分的表达式仅限于 `ObjectQuery<T>` 和基础数据源所支持的操作。</span><span class="sxs-lookup"><span data-stu-id="be4b3-109">The expressions that can be used in LINQ to Entities queries are a superset of the expressions that can be used to query the Entity Framework.Expressions that are part of queries against the Entity Framework are limited to operations supported by `ObjectQuery<T>` and the underlying data source.</span></span>  
  
 <span data-ttu-id="be4b3-110">在下面的示例中，`Where` 子句中的比较运算就是一个表达式：</span><span class="sxs-lookup"><span data-stu-id="be4b3-110">In the following example, the comparison in the `Where` clause is an expression:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
> <span data-ttu-id="be4b3-111">特定语言构造（如 c # `unchecked` ）在 LINQ to Entities 中没有意义。</span><span class="sxs-lookup"><span data-stu-id="be4b3-111">Specific language constructs, such as C# `unchecked`, have no meaning in LINQ to Entities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="be4b3-112">本节内容</span><span class="sxs-lookup"><span data-stu-id="be4b3-112">In This Section</span></span>  

 [<span data-ttu-id="be4b3-113">常量表达式</span><span class="sxs-lookup"><span data-stu-id="be4b3-113">Constant Expressions</span></span>](constant-expressions.md)  
  
 [<span data-ttu-id="be4b3-114">比较表达式</span><span class="sxs-lookup"><span data-stu-id="be4b3-114">Comparison Expressions</span></span>](comparison-expressions.md)  
  
 [<span data-ttu-id="be4b3-115">Null 比较</span><span class="sxs-lookup"><span data-stu-id="be4b3-115">Null Comparisons</span></span>](null-comparisons.md)  
  
 [<span data-ttu-id="be4b3-116">初始化表达式</span><span class="sxs-lookup"><span data-stu-id="be4b3-116">Initialization Expressions</span></span>](initialization-expressions.md)  
  
 [<span data-ttu-id="be4b3-117">关系、导航属性和外键</span><span class="sxs-lookup"><span data-stu-id="be4b3-117">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)  
  
## <a name="see-also"></a><span data-ttu-id="be4b3-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="be4b3-118">See also</span></span>

- [<span data-ttu-id="be4b3-119">ADO.NET 实体框架</span><span class="sxs-lookup"><span data-stu-id="be4b3-119">ADO.NET Entity Framework</span></span>](../index.md)
