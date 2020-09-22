---
title: Let 子句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: a6ff3fc80a2b6752c61a8b8f7d4ce62b5a46baad
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90869887"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="dbc5f-102">Let 子句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dbc5f-102">Let Clause (Visual Basic)</span></span>

<span data-ttu-id="dbc5f-103">计算值并将其分配给查询中的新变量。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc5f-104">语法</span><span class="sxs-lookup"><span data-stu-id="dbc5f-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="dbc5f-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="dbc5f-105">Parts</span></span>  
  
|<span data-ttu-id="dbc5f-106">术语</span><span class="sxs-lookup"><span data-stu-id="dbc5f-106">Term</span></span>|<span data-ttu-id="dbc5f-107">定义</span><span class="sxs-lookup"><span data-stu-id="dbc5f-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="dbc5f-108">必需。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-108">Required.</span></span> <span data-ttu-id="dbc5f-109">可用于引用所提供表达式的结果的别名。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="dbc5f-110">必需。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-110">Required.</span></span> <span data-ttu-id="dbc5f-111">将进行计算并分配给指定变量的表达式。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc5f-112">备注</span><span class="sxs-lookup"><span data-stu-id="dbc5f-112">Remarks</span></span>  

 <span data-ttu-id="dbc5f-113">`Let`使用子句可以计算每个查询结果的值，并使用别名引用这些值。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="dbc5f-114">别名可用于其他子句，如 `Where` 子句。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="dbc5f-115">`Let`使用子句可以创建更易于阅读的查询语句，因为您可以为查询中包括的 expression 子句指定一个别名，并在每次使用 expression 子句时替换该别名。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="dbc5f-116">可以在子句中包含任意数量的 `variable` 和 `expression` 赋值 `Let` 。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="dbc5f-117">用逗号分隔每个分配 (，) 。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbc5f-118">示例</span><span class="sxs-lookup"><span data-stu-id="dbc5f-118">Example</span></span>  

 <span data-ttu-id="dbc5f-119">下面的代码示例使用 `Let` 子句来计算产品10% 的折扣。</span><span class="sxs-lookup"><span data-stu-id="dbc5f-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="dbc5f-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="dbc5f-120">See also</span></span>

- [<span data-ttu-id="dbc5f-121">Visual Basic 中的 LINQ 简介</span><span class="sxs-lookup"><span data-stu-id="dbc5f-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="dbc5f-122">查询</span><span class="sxs-lookup"><span data-stu-id="dbc5f-122">Queries</span></span>](index.md)
- [<span data-ttu-id="dbc5f-123">Select 子句</span><span class="sxs-lookup"><span data-stu-id="dbc5f-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="dbc5f-124">From 子句</span><span class="sxs-lookup"><span data-stu-id="dbc5f-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="dbc5f-125">Where 子句</span><span class="sxs-lookup"><span data-stu-id="dbc5f-125">Where Clause</span></span>](where-clause.md)
