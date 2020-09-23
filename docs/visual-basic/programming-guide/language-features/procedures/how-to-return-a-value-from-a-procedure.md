---
title: 如何：从过程返回值
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: cbc785a07aa8a7b299508a093e08d5d0510b838a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071373"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a><span data-ttu-id="cc5ba-102">如何：从过程返回值 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc5ba-102">How to: Return a Value from a Procedure (Visual Basic)</span></span>

<span data-ttu-id="cc5ba-103">`Function`过程通过执行 `Return` 语句或遇到或语句，将值返回到调用代码 `Exit Function` `End Function` 。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-103">A `Function` procedure returns a value to the calling code either by executing a `Return` statement or by encountering an `Exit Function` or `End Function` statement.</span></span>  
  
### <a name="to-return-a-value-using-the-return-statement"></a><span data-ttu-id="cc5ba-104">使用 Return 语句返回值</span><span class="sxs-lookup"><span data-stu-id="cc5ba-104">To return a value using the Return statement</span></span>  
  
1. <span data-ttu-id="cc5ba-105">将 `Return` 语句放在过程任务完成的点。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-105">Put a `Return` statement at the point where the procedure's task is completed.</span></span>  
  
2. <span data-ttu-id="cc5ba-106">在关键字后面跟 `Return` 一个表达式，该表达式生成要返回到调用代码的值。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-106">Follow the `Return` keyword with an expression that yields the value you want to return to the calling code.</span></span>  
  
3. <span data-ttu-id="cc5ba-107">在同一过程中可拥有多个 `Return` 语句。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-107">You can have more than one `Return` statement in the same procedure.</span></span>  
  
     <span data-ttu-id="cc5ba-108">下面的 `Function` 过程计算直角三角形的最长边，或斜边，并将其返回给调用代码。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-108">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, and returns it to the calling code.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="cc5ba-109">下面的示例演示对的典型调用 `hypotenuse` ，它存储返回的值。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-109">The following example shows a typical call to `hypotenuse`, which stores the returned value.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a><span data-ttu-id="cc5ba-110">使用 Exit 函数或 End 函数返回值</span><span class="sxs-lookup"><span data-stu-id="cc5ba-110">To return a value using Exit Function or End Function</span></span>  
  
1. <span data-ttu-id="cc5ba-111">在过程中的至少一个位置 `Function` ，为过程名称赋值。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-111">In at least one place in the `Function` procedure, assign a value to the procedure's name.</span></span>  
  
2. <span data-ttu-id="cc5ba-112">执行 `Exit Function` 或 `End Function` 语句时，Visual Basic 返回最近分配给该过程名称的值。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-112">When you execute an `Exit Function` or `End Function` statement, Visual Basic returns the value most recently assigned to the procedure's name.</span></span>  
  
3. <span data-ttu-id="cc5ba-113">在同一过程中可拥有多个 `Exit Function` 语句，也可混合 `Return` 和 `Exit Function` 语句。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-113">You can have more than one `Exit Function` statement in the same procedure, and you can mix `Return` and `Exit Function` statements in the same procedure.</span></span>  
  
4. <span data-ttu-id="cc5ba-114">一个过程中只能有一个 `End Function` 语句 `Function` 。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-114">You can have only one `End Function` statement in a `Function` procedure.</span></span>  
  
     <span data-ttu-id="cc5ba-115">有关详细信息和示例，请参阅 [Function 语句](../../../language-reference/statements/function-statement.md)中的 "返回值"。</span><span class="sxs-lookup"><span data-stu-id="cc5ba-115">For more information and an example, see "Return Value" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc5ba-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="cc5ba-116">See also</span></span>

- [<span data-ttu-id="cc5ba-117">过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-117">Procedures</span></span>](./index.md)
- [<span data-ttu-id="cc5ba-118">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-118">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="cc5ba-119">Property 过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-119">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="cc5ba-120">运算符过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-120">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cc5ba-121">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="cc5ba-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="cc5ba-122">Function 语句</span><span class="sxs-lookup"><span data-stu-id="cc5ba-122">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="cc5ba-123">Return 语句</span><span class="sxs-lookup"><span data-stu-id="cc5ba-123">Return Statement</span></span>](../../../language-reference/statements/return-statement.md)
- [<span data-ttu-id="cc5ba-124">如何：创建返回值的过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-124">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="cc5ba-125">如何：调用返回值的过程</span><span class="sxs-lookup"><span data-stu-id="cc5ba-125">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
