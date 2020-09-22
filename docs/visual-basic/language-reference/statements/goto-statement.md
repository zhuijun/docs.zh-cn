---
title: GoTo 语句
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 000f6754575bcce6b2d79d85541e755219aca956
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866620"
---
# <a name="goto-statement"></a><span data-ttu-id="6f67e-102">GoTo 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-102">GoTo Statement</span></span>

<span data-ttu-id="6f67e-103">无条件地分支到过程中的指定行。</span><span class="sxs-lookup"><span data-stu-id="6f67e-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f67e-104">语法</span><span class="sxs-lookup"><span data-stu-id="6f67e-104">Syntax</span></span>  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="6f67e-105">部件</span><span class="sxs-lookup"><span data-stu-id="6f67e-105">Part</span></span>  

 `line`  
 <span data-ttu-id="6f67e-106">必需。</span><span class="sxs-lookup"><span data-stu-id="6f67e-106">Required.</span></span> <span data-ttu-id="6f67e-107">任何行标签。</span><span class="sxs-lookup"><span data-stu-id="6f67e-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f67e-108">备注</span><span class="sxs-lookup"><span data-stu-id="6f67e-108">Remarks</span></span>  

 <span data-ttu-id="6f67e-109">`GoTo`语句只能分支到其出现的过程中的行。</span><span class="sxs-lookup"><span data-stu-id="6f67e-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="6f67e-110">该行必须具有可引用的行标签 `GoTo` 。</span><span class="sxs-lookup"><span data-stu-id="6f67e-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="6f67e-111">有关详细信息，请参阅 [如何：标签语句](../../programming-guide/program-structure/how-to-label-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="6f67e-111">For more information, see [How to: Label Statements](../../programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f67e-112">`GoTo` 语句可以使代码难以阅读和维护。</span><span class="sxs-lookup"><span data-stu-id="6f67e-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="6f67e-113">请尽可能使用控制结构。</span><span class="sxs-lookup"><span data-stu-id="6f67e-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="6f67e-114">有关详细信息，请参阅 [Control Flow](../../programming-guide/language-features/control-flow/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6f67e-114">For more information, see [Control Flow](../../programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="6f67e-115">不能使用 `GoTo` 语句从 `For` ...、 `Next` `For Each` ... `Next` `SyncLock` `End SyncLock` `Try` `Catch` 、... ... ... ... ... ... .。。... `Finally` 、 `With` ... `End With` 或 `Using` ... `End Using` 构造中的标签。</span><span class="sxs-lookup"><span data-stu-id="6f67e-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="6f67e-116">分支和尝试构造</span><span class="sxs-lookup"><span data-stu-id="6f67e-116">Branching and Try Constructions</span></span>  

 <span data-ttu-id="6f67e-117">在 `Try` ... `Catch`...`Finally` 构造，以下规则适用于使用语句的分支 `GoTo` 。</span><span class="sxs-lookup"><span data-stu-id="6f67e-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="6f67e-118">块或区域</span><span class="sxs-lookup"><span data-stu-id="6f67e-118">Block or region</span></span>|<span data-ttu-id="6f67e-119">从外部分支</span><span class="sxs-lookup"><span data-stu-id="6f67e-119">Branching in from outside</span></span>|<span data-ttu-id="6f67e-120">从内部分支出</span><span class="sxs-lookup"><span data-stu-id="6f67e-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="6f67e-121">`Try` 模块</span><span class="sxs-lookup"><span data-stu-id="6f67e-121">`Try` block</span></span>|<span data-ttu-id="6f67e-122">仅从 `Catch` 同一构造的块 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="6f67e-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="6f67e-123">仅限于整个构造之外</span><span class="sxs-lookup"><span data-stu-id="6f67e-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="6f67e-124">`Catch` 模块</span><span class="sxs-lookup"><span data-stu-id="6f67e-124">`Catch` block</span></span>|<span data-ttu-id="6f67e-125">不允许</span><span class="sxs-lookup"><span data-stu-id="6f67e-125">Never allowed</span></span>|<span data-ttu-id="6f67e-126">仅对整个构造以外的或 `Try` 相同构造<sup>1</sup>的块</span><span class="sxs-lookup"><span data-stu-id="6f67e-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="6f67e-127">`Finally` 模块</span><span class="sxs-lookup"><span data-stu-id="6f67e-127">`Finally` block</span></span>|<span data-ttu-id="6f67e-128">不允许</span><span class="sxs-lookup"><span data-stu-id="6f67e-128">Never allowed</span></span>|<span data-ttu-id="6f67e-129">不允许</span><span class="sxs-lookup"><span data-stu-id="6f67e-129">Never allowed</span></span>|  
  
 <span data-ttu-id="6f67e-130"><sup>1</sup> （如果 `Try` 有 `Catch` ） .。。...`Finally` 构造嵌套在另一个块中， `Catch` 块可以 `Try` 在其自身的嵌套级别（而不是其他块）分支到块 `Try` 。</span><span class="sxs-lookup"><span data-stu-id="6f67e-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="6f67e-131">嵌套 `Try` ... `Catch`...`Finally` 构造必须完全包含在 `Try` `Catch` 它所嵌套到的构造内或块中。</span><span class="sxs-lookup"><span data-stu-id="6f67e-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="6f67e-132">下图显示了一个 `Try` 嵌套在另一个构造内的构造。</span><span class="sxs-lookup"><span data-stu-id="6f67e-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="6f67e-133">这两个构造的块中的各种分支都指示为有效或无效。</span><span class="sxs-lookup"><span data-stu-id="6f67e-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Try 结构分支示意图](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="6f67e-135">示例</span><span class="sxs-lookup"><span data-stu-id="6f67e-135">Example</span></span>  

 <span data-ttu-id="6f67e-136">下面的示例使用 `GoTo` 语句分支到过程中的行标签。</span><span class="sxs-lookup"><span data-stu-id="6f67e-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="6f67e-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6f67e-137">See also</span></span>

- [<span data-ttu-id="6f67e-138">Do...Loop 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-138">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="6f67e-139">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-139">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="6f67e-140">For Each...Next 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-140">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="6f67e-141">If...Then...Else 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-141">If...Then...Else Statement</span></span>](if-then-else-statement.md)
- [<span data-ttu-id="6f67e-142">Select...Case 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-142">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="6f67e-143">Try...Catch...Finally 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-143">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="6f67e-144">While...End While 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-144">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="6f67e-145">With...End With 语句</span><span class="sxs-lookup"><span data-stu-id="6f67e-145">With...End With Statement</span></span>](with-end-with-statement.md)
