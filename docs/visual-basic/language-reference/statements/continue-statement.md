---
title: Continue 语句
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: cf73ea1b3d402609c9966980dcab9ddd9bc096c2
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874968"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="5a095-102">Continue 语句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5a095-102">Continue Statement (Visual Basic)</span></span>

<span data-ttu-id="5a095-103">将控制立即传输到循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="5a095-103">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a095-104">语法</span><span class="sxs-lookup"><span data-stu-id="5a095-104">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="5a095-105">备注</span><span class="sxs-lookup"><span data-stu-id="5a095-105">Remarks</span></span>  

 <span data-ttu-id="5a095-106">可以从 `Do` 、或循环内传输 `For` `While` 到循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="5a095-106">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="5a095-107">控制权会立即传递到循环条件测试，这等效于将转换为 `For` 或 `While` 语句，或 `Do` `Loop` 包含或子句的或语句 `Until` `While` 。</span><span class="sxs-lookup"><span data-stu-id="5a095-107">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="5a095-108">可以在 `Continue` 允许传输的循环中的任意位置使用。</span><span class="sxs-lookup"><span data-stu-id="5a095-108">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="5a095-109">允许传输控件的规则与 [GoTo 语句](goto-statement.md)相同。</span><span class="sxs-lookup"><span data-stu-id="5a095-109">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="5a095-110">例如，如果循环完全包含在 `Try` 块、 `Catch` 块或 `Finally` 块中，则可以使用 `Continue` 来传出循环。</span><span class="sxs-lookup"><span data-stu-id="5a095-110">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="5a095-111">另一方面，如果 `Try` `End Try` 循环中包含 ... 结构，则不能使用 `Continue` 将控件从块中传输出去 `Finally` ，并且 `Try` `Catch` 仅当完全从 `Try` ... `End Try` 结构中传输时，才能使用它来传出或阻止。</span><span class="sxs-lookup"><span data-stu-id="5a095-111">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="5a095-112">如果有相同类型的嵌套循环（例如 `Do` 另一个循环内的循环），则 `Do` 语句将 `Continue Do` 跳到包含它的最内层循环的下一次迭代 `Do` 。</span><span class="sxs-lookup"><span data-stu-id="5a095-112">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="5a095-113">不能使用 `Continue` 跳到相同类型的包含循环的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="5a095-113">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="5a095-114">如果具有不同类型的嵌套循环（例如 `Do` 循环内的循环）， `For` 可以使用或跳到任一循环的下一次迭代 `Continue Do` `Continue For` 。</span><span class="sxs-lookup"><span data-stu-id="5a095-114">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a095-115">示例</span><span class="sxs-lookup"><span data-stu-id="5a095-115">Example</span></span>  

 <span data-ttu-id="5a095-116">下面的代码示例使用 `Continue While` 语句跳转到数组的下一列（如果除数为零）。</span><span class="sxs-lookup"><span data-stu-id="5a095-116">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="5a095-117">在 `Continue While` `For` 循环内。</span><span class="sxs-lookup"><span data-stu-id="5a095-117">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="5a095-118">它转移到 `While col < lastcol` 语句，后者是包含循环的最内层循环的下一次迭代 `While` `For` 。</span><span class="sxs-lookup"><span data-stu-id="5a095-118">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="5a095-119">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5a095-119">See also</span></span>

- [<span data-ttu-id="5a095-120">Do...Loop 语句</span><span class="sxs-lookup"><span data-stu-id="5a095-120">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="5a095-121">For...Next 语句</span><span class="sxs-lookup"><span data-stu-id="5a095-121">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="5a095-122">While...End While 语句</span><span class="sxs-lookup"><span data-stu-id="5a095-122">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="5a095-123">尝试 .。。Catch .。。Finally 语句</span><span class="sxs-lookup"><span data-stu-id="5a095-123">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
