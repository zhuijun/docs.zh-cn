---
title: 如何：创建返回值的过程
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 3d28162d2a2103477a20b08fc03c937de8b5a475
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071867"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="eb8aa-102">如何：创建返回值的过程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb8aa-102">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="eb8aa-103">使用过程将 `Function` 值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-103">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="eb8aa-104">创建返回值的过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-104">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="eb8aa-105">在任何其他过程之外，使用 `Function` 语句，然后使用 `End Function` 语句。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-105">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="eb8aa-106">在 `Function` 语句中，在关键字后面跟 `Function` 上过程的名称，然后是括号中的参数列表。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-106">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="eb8aa-107">在括号后跟一个 `As` 子句以指定返回值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-107">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="eb8aa-108">将过程的代码语句放置在 `Function` 和 `End Function` 语句之间。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-108">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="eb8aa-109">使用 `Return` 语句将值返回到调用代码。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-109">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="eb8aa-110">下面的 `Function` 过程计算直角三角形的最长边（或斜边），并给出另一方的值。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-110">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="eb8aa-111">下面的示例演示对的典型调用 `hypotenuse` 。</span><span class="sxs-lookup"><span data-stu-id="eb8aa-111">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="eb8aa-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="eb8aa-112">See also</span></span>

- [<span data-ttu-id="eb8aa-113">过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-113">Procedures</span></span>](./index.md)
- [<span data-ttu-id="eb8aa-114">Sub 过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-114">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="eb8aa-115">Property 过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-115">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="eb8aa-116">运算符过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-116">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="eb8aa-117">过程形参和实参</span><span class="sxs-lookup"><span data-stu-id="eb8aa-117">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="eb8aa-118">Function 语句</span><span class="sxs-lookup"><span data-stu-id="eb8aa-118">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="eb8aa-119">如何：从过程返回值</span><span class="sxs-lookup"><span data-stu-id="eb8aa-119">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="eb8aa-120">如何：调用返回值的过程</span><span class="sxs-lookup"><span data-stu-id="eb8aa-120">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
