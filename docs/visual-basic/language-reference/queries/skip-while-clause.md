---
title: Skip While 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359640"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="47991-102">Skip While 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47991-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="47991-103">跳过集合中指定条件为 `true` 的任何元素，然后返回剩余元素。</span><span class="sxs-lookup"><span data-stu-id="47991-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47991-104">语法</span><span class="sxs-lookup"><span data-stu-id="47991-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="47991-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="47991-105">Parts</span></span>  
  
|<span data-ttu-id="47991-106">术语</span><span class="sxs-lookup"><span data-stu-id="47991-106">Term</span></span>|<span data-ttu-id="47991-107">定义</span><span class="sxs-lookup"><span data-stu-id="47991-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="47991-108">必需。</span><span class="sxs-lookup"><span data-stu-id="47991-108">Required.</span></span> <span data-ttu-id="47991-109">表示要为其测试元素的条件的表达式。</span><span class="sxs-lookup"><span data-stu-id="47991-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="47991-110">表达式必须返回一个 `Boolean` 值或函数等效项，如 `Integer` 要计算为的 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="47991-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47991-111">备注</span><span class="sxs-lookup"><span data-stu-id="47991-111">Remarks</span></span>  
 <span data-ttu-id="47991-112">`Skip While`子句会绕过查询结果开头的元素，直到提供的 `expression` 返回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="47991-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="47991-113">`expression`返回后 `false` ，该查询将返回所有剩余元素。</span><span class="sxs-lookup"><span data-stu-id="47991-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="47991-114">`expression`对于剩余的结果，将忽略。</span><span class="sxs-lookup"><span data-stu-id="47991-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="47991-115">`Skip While`子句与子句的不同之处 `Where` 在于， `Where` 子句可用于从查询中排除不满足特定条件的所有元素。</span><span class="sxs-lookup"><span data-stu-id="47991-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="47991-116">`Skip While`子句仅排除元素，直到第一次未满足条件。</span><span class="sxs-lookup"><span data-stu-id="47991-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="47991-117">`Skip While`当使用排序的查询结果时，子句最有用。</span><span class="sxs-lookup"><span data-stu-id="47991-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="47991-118">您可以使用子句从查询结果的开头跳过特定数目的结果 `Skip` 。</span><span class="sxs-lookup"><span data-stu-id="47991-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47991-119">示例</span><span class="sxs-lookup"><span data-stu-id="47991-119">Example</span></span>  
 <span data-ttu-id="47991-120">下面的代码示例使用 `Skip While` 子句跳过结果，直到找到美国中的第一个客户。</span><span class="sxs-lookup"><span data-stu-id="47991-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="47991-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="47991-121">See also</span></span>

- [<span data-ttu-id="47991-122">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="47991-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="47991-123">查询</span><span class="sxs-lookup"><span data-stu-id="47991-123">Queries</span></span>](index.md)
- [<span data-ttu-id="47991-124">Select 子句</span><span class="sxs-lookup"><span data-stu-id="47991-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="47991-125">From 子句</span><span class="sxs-lookup"><span data-stu-id="47991-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="47991-126">Skip 子句</span><span class="sxs-lookup"><span data-stu-id="47991-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="47991-127">Take While 子句</span><span class="sxs-lookup"><span data-stu-id="47991-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="47991-128">Where 子句</span><span class="sxs-lookup"><span data-stu-id="47991-128">Where Clause</span></span>](where-clause.md)
