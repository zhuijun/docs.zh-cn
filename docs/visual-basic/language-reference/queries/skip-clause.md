---
title: Skip 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359653"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="5a6bf-102">Skip 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a6bf-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="5a6bf-103">绕过集合中指定数量的元素，然后返回剩余的元素。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a6bf-104">语法</span><span class="sxs-lookup"><span data-stu-id="5a6bf-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="5a6bf-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="5a6bf-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="5a6bf-106">必需。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-106">Required.</span></span> <span data-ttu-id="5a6bf-107">值或计算结果为要跳过的序列的元素数的表达式。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a6bf-108">备注</span><span class="sxs-lookup"><span data-stu-id="5a6bf-108">Remarks</span></span>  
 <span data-ttu-id="5a6bf-109">`Skip`子句使查询绕过结果列表开头的元素，并返回剩余的元素。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="5a6bf-110">要跳过的元素数由 `count` 参数标识。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="5a6bf-111">可以将 `Skip` 子句与子句结合使用， `Take` 以便从查询的任何段返回数据范围。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="5a6bf-112">为此，请将范围中第一个元素的索引传递给 `Skip` 子句，并将范围的大小传递到 `Take` 子句。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="5a6bf-113">在 `Skip` 查询中使用子句时，您可能还需要确保按使 `Skip` 子句跳过预期结果的顺序返回结果。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="5a6bf-114">有关对查询结果进行排序的详细信息，请参阅[Order By 子句](order-by-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-114">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="5a6bf-115">您可以使用 `SkipWhile` 子句来指定仅忽略某些元素，具体取决于所提供的条件。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a6bf-116">示例</span><span class="sxs-lookup"><span data-stu-id="5a6bf-116">Example</span></span>  
 <span data-ttu-id="5a6bf-117">下面的代码示例将 `Skip` 子句与子句一起使用 `Take` ，以从页的查询返回数据。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="5a6bf-118">`GetCustomers`函数使用 `Skip` 子句跳过列表中的客户，直至提供的起始索引值，并使用 `Take` 子句返回从该索引值开始的客户页面。</span><span class="sxs-lookup"><span data-stu-id="5a6bf-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5a6bf-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a6bf-119">See also</span></span>

- [<span data-ttu-id="5a6bf-120">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="5a6bf-120">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="5a6bf-121">查询</span><span class="sxs-lookup"><span data-stu-id="5a6bf-121">Queries</span></span>](index.md)
- [<span data-ttu-id="5a6bf-122">Select 子句</span><span class="sxs-lookup"><span data-stu-id="5a6bf-122">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="5a6bf-123">From 子句</span><span class="sxs-lookup"><span data-stu-id="5a6bf-123">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="5a6bf-124">Order By 子句</span><span class="sxs-lookup"><span data-stu-id="5a6bf-124">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="5a6bf-125">Skip While 子句</span><span class="sxs-lookup"><span data-stu-id="5a6bf-125">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="5a6bf-126">Take 子句</span><span class="sxs-lookup"><span data-stu-id="5a6bf-126">Take Clause</span></span>](take-clause.md)
