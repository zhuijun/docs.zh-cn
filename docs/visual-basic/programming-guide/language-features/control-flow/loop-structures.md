---
title: 循环结构
ms.date: 07/20/2015
helpviewer_keywords:
- control flow [Visual Basic], loops
- For keyword [Visual Basic], loop structures
- loops
- loop structures [Visual Basic]
- statements [Visual Basic], loop
- Do statement [Visual Basic], Do loops
- conditional statements [Visual Basic], loop structures
ms.assetid: ecacb09b-a4c9-42be-98b2-a15d368b5db8
ms.openlocfilehash: 3f60e9dc83dc7174e765903be13f2870ea40ce4c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403508"
---
# <a name="loop-structures-visual-basic"></a><span data-ttu-id="f6a97-102">循环结构 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6a97-102">Loop Structures (Visual Basic)</span></span>
<span data-ttu-id="f6a97-103">Visual Basic 循环结构使您可以重复运行一个或多个代码行。</span><span class="sxs-lookup"><span data-stu-id="f6a97-103">Visual Basic loop structures allow you to run one or more lines of code repetitively.</span></span> <span data-ttu-id="f6a97-104">您可以重复循环结构中的语句，直到条件为、 `True` `False` 指定次数或为集合中的每个元素指定一次。</span><span class="sxs-lookup"><span data-stu-id="f6a97-104">You can repeat the statements in a loop structure until a condition is `True`, until a condition is `False`, a specified number of times, or once for each element in a collection.</span></span>  
  
 <span data-ttu-id="f6a97-105">下图显示了一个循环结构，它运行一组语句，直到条件变为 true：</span><span class="sxs-lookup"><span data-stu-id="f6a97-105">The following illustration shows a loop structure that runs a set of statements until a condition becomes true:</span></span>  
  
 ![显示 ... 的流程图Until 循环。](./media/loop-structures/do-until-loop-true-condition.gif)  
  
## <a name="while-loops"></a><span data-ttu-id="f6a97-107">While 循环</span><span class="sxs-lookup"><span data-stu-id="f6a97-107">While Loops</span></span>  
 <span data-ttu-id="f6a97-108">`While` `End While` 只要语句中指定的条件为，... 构造将运行一组语句 `While` `True` 。</span><span class="sxs-lookup"><span data-stu-id="f6a97-108">The `While`...`End While` construction runs a set of statements as long as the condition specified in the `While` statement is `True`.</span></span> <span data-ttu-id="f6a97-109">有关详细信息，请参阅[While .。。End While 语句](../../../language-reference/statements/while-end-while-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a97-109">For more information, see [While...End While Statement](../../../language-reference/statements/while-end-while-statement.md).</span></span>  
  
## <a name="do-loops"></a><span data-ttu-id="f6a97-110">Do 循环</span><span class="sxs-lookup"><span data-stu-id="f6a97-110">Do Loops</span></span>  
 <span data-ttu-id="f6a97-111">使用 `Do` ... 构造， `Loop` 可以在循环结构的开始或结束时测试条件。</span><span class="sxs-lookup"><span data-stu-id="f6a97-111">The `Do`...`Loop` construction allows you to test a condition at either the beginning or the end of a loop structure.</span></span> <span data-ttu-id="f6a97-112">您还可以指定是否在条件保持 `True` 或变为之前重复执行循环 `True` 。</span><span class="sxs-lookup"><span data-stu-id="f6a97-112">You can also specify whether to repeat the loop while the condition remains `True` or until it becomes `True`.</span></span> <span data-ttu-id="f6a97-113">有关详细信息，请参阅[Do .。。循环语句](../../../language-reference/statements/do-loop-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a97-113">For more information, see [Do...Loop Statement](../../../language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="for-loops"></a><span data-ttu-id="f6a97-114">For 循环</span><span class="sxs-lookup"><span data-stu-id="f6a97-114">For Loops</span></span>  
 <span data-ttu-id="f6a97-115">`For`... `Next` 构造按设置的次数执行循环。</span><span class="sxs-lookup"><span data-stu-id="f6a97-115">The `For`...`Next` construction performs the loop a set number of times.</span></span> <span data-ttu-id="f6a97-116">它使用循环控制变量（也称为*计数器*）跟踪重复。</span><span class="sxs-lookup"><span data-stu-id="f6a97-116">It uses a loop control variable, also called a *counter*, to keep track of the repetitions.</span></span> <span data-ttu-id="f6a97-117">您可以指定此计数器的起始值和结束值，还可以选择指定从一个重复到下一个重复的量。</span><span class="sxs-lookup"><span data-stu-id="f6a97-117">You specify the starting and ending values for this counter, and you can optionally specify the amount by which it increases from one repetition to the next.</span></span> <span data-ttu-id="f6a97-118">有关详细信息，请参阅[For .。。下一语句](../../../language-reference/statements/for-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a97-118">For more information, see [For...Next Statement](../../../language-reference/statements/for-next-statement.md).</span></span>  
  
## <a name="for-each-loops"></a><span data-ttu-id="f6a97-119">对于每个循环</span><span class="sxs-lookup"><span data-stu-id="f6a97-119">For Each Loops</span></span>  
 <span data-ttu-id="f6a97-120">`For Each`... `Next` 构造为集合中的每个元素运行一组语句。</span><span class="sxs-lookup"><span data-stu-id="f6a97-120">The `For Each`...`Next` construction runs a set of statements once for each element in a collection.</span></span> <span data-ttu-id="f6a97-121">指定循环控制变量，但不需要确定其起始值或终止值。</span><span class="sxs-lookup"><span data-stu-id="f6a97-121">You specify the loop control variable, but you do not have to determine starting or ending values for it.</span></span> <span data-ttu-id="f6a97-122">有关详细信息，请参阅[For Each .。。下一语句](../../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f6a97-122">For more information, see [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6a97-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f6a97-123">See also</span></span>

- [<span data-ttu-id="f6a97-124">控制流</span><span class="sxs-lookup"><span data-stu-id="f6a97-124">Control Flow</span></span>](index.md)
- [<span data-ttu-id="f6a97-125">决策结构</span><span class="sxs-lookup"><span data-stu-id="f6a97-125">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="f6a97-126">其他控件结构</span><span class="sxs-lookup"><span data-stu-id="f6a97-126">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="f6a97-127">嵌套的控件结构</span><span class="sxs-lookup"><span data-stu-id="f6a97-127">Nested Control Structures</span></span>](nested-control-structures.md)
