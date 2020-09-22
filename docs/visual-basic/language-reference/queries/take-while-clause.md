---
title: Take While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 632e9e2195f21a3aa1d1ffd28e9838905c471156
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869658"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="dd23c-102">Take While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd23c-102">Take While Clause (Visual Basic)</span></span>

<span data-ttu-id="dd23c-103">包括集合中指定条件为 `true` 的任何元素，并绕过剩余元素。</span><span class="sxs-lookup"><span data-stu-id="dd23c-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd23c-104">语法</span><span class="sxs-lookup"><span data-stu-id="dd23c-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="dd23c-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="dd23c-105">Parts</span></span>  
  
|<span data-ttu-id="dd23c-106">术语</span><span class="sxs-lookup"><span data-stu-id="dd23c-106">Term</span></span>|<span data-ttu-id="dd23c-107">定义</span><span class="sxs-lookup"><span data-stu-id="dd23c-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="dd23c-108">必需。</span><span class="sxs-lookup"><span data-stu-id="dd23c-108">Required.</span></span> <span data-ttu-id="dd23c-109">表示要为其测试元素的条件的表达式。</span><span class="sxs-lookup"><span data-stu-id="dd23c-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="dd23c-110">表达式必须返回一个 `Boolean` 值或函数等效项，如 `Integer` 要计算为的 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="dd23c-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd23c-111">备注</span><span class="sxs-lookup"><span data-stu-id="dd23c-111">Remarks</span></span>  

 <span data-ttu-id="dd23c-112">`Take While`子句包括从查询结果的开头开始直到提供的返回的元素 `expression` `false` 。</span><span class="sxs-lookup"><span data-stu-id="dd23c-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="dd23c-113">返回后 `expression` `false` ，查询将跳过所有剩余的元素。</span><span class="sxs-lookup"><span data-stu-id="dd23c-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="dd23c-114">`expression`对于剩余的结果，将忽略。</span><span class="sxs-lookup"><span data-stu-id="dd23c-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="dd23c-115">`Take While`子句与子句的不同之处 `Where` 在于， `Where` 子句可用于包括查询中满足特定条件的所有元素。</span><span class="sxs-lookup"><span data-stu-id="dd23c-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="dd23c-116">`Take While`子句仅包含元素，直到第一次未满足条件。</span><span class="sxs-lookup"><span data-stu-id="dd23c-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="dd23c-117">`Take While`当使用排序的查询结果时，子句最有用。</span><span class="sxs-lookup"><span data-stu-id="dd23c-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd23c-118">示例</span><span class="sxs-lookup"><span data-stu-id="dd23c-118">Example</span></span>  

 <span data-ttu-id="dd23c-119">下面的代码示例使用 `Take While` 子句检索结果，直到找到第一个不含任何订单的客户。</span><span class="sxs-lookup"><span data-stu-id="dd23c-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dd23c-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dd23c-120">See also</span></span>

- [<span data-ttu-id="dd23c-121">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="dd23c-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="dd23c-122">查询</span><span class="sxs-lookup"><span data-stu-id="dd23c-122">Queries</span></span>](index.md)
- [<span data-ttu-id="dd23c-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="dd23c-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="dd23c-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="dd23c-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="dd23c-125">Take 子句</span><span class="sxs-lookup"><span data-stu-id="dd23c-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="dd23c-126">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="dd23c-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="dd23c-127">Where 子句</span><span class="sxs-lookup"><span data-stu-id="dd23c-127">Where Clause</span></span>](where-clause.md)
