---
title: Distinct 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875276"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="b2205-102">Distinct 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2205-102">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="b2205-103">限制当前范围变量的值，以消除后面的查询子句中的重复值。</span><span class="sxs-lookup"><span data-stu-id="b2205-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2205-104">语法</span><span class="sxs-lookup"><span data-stu-id="b2205-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2205-105">备注</span><span class="sxs-lookup"><span data-stu-id="b2205-105">Remarks</span></span>  

 <span data-ttu-id="b2205-106">您可以使用 `Distinct` 子句返回唯一项的列表。</span><span class="sxs-lookup"><span data-stu-id="b2205-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="b2205-107">`Distinct`子句使查询忽略重复的查询结果。</span><span class="sxs-lookup"><span data-stu-id="b2205-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="b2205-108">`Distinct`子句适用于子句指定的所有返回字段的重复值 `Select` 。</span><span class="sxs-lookup"><span data-stu-id="b2205-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="b2205-109">如果未 `Select` 指定子句，则将 `Distinct` 子句应用于子句中标识的查询的范围变量 `From` 。</span><span class="sxs-lookup"><span data-stu-id="b2205-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="b2205-110">如果范围变量不是不可变类型，则当该类型的所有成员均与现有查询结果匹配时，该查询将忽略查询结果。</span><span class="sxs-lookup"><span data-stu-id="b2205-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2205-111">示例</span><span class="sxs-lookup"><span data-stu-id="b2205-111">Example</span></span>  

 <span data-ttu-id="b2205-112">下面的查询表达式将联接列表和客户订单列表。</span><span class="sxs-lookup"><span data-stu-id="b2205-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="b2205-113">`Distinct`包含子句是为了返回唯一客户名称和订单日期的列表。</span><span class="sxs-lookup"><span data-stu-id="b2205-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="b2205-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b2205-114">See also</span></span>

- [<span data-ttu-id="b2205-115">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="b2205-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b2205-116">查询</span><span class="sxs-lookup"><span data-stu-id="b2205-116">Queries</span></span>](index.md)
- [<span data-ttu-id="b2205-117">From 子句</span><span class="sxs-lookup"><span data-stu-id="b2205-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="b2205-118">Select 子句</span><span class="sxs-lookup"><span data-stu-id="b2205-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="b2205-119">Where 子句</span><span class="sxs-lookup"><span data-stu-id="b2205-119">Where Clause</span></span>](where-clause.md)
