---
title: 如何：将过程传递给另一过程
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 3a7a653bbf238b50e3c7339da76df0f68ab9b59f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085784"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a><span data-ttu-id="c41c2-102">如何：在 Visual Basic 中将过程传递给另一过程</span><span class="sxs-lookup"><span data-stu-id="c41c2-102">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>

<span data-ttu-id="c41c2-103">此示例演示如何使用委托将过程传递给另一个过程。</span><span class="sxs-lookup"><span data-stu-id="c41c2-103">This example shows how to use delegates to pass a procedure to another procedure.</span></span>  
  
 <span data-ttu-id="c41c2-104">委托是一种类型，您可以像在 Visual Basic 中那样使用任何其他类型。</span><span class="sxs-lookup"><span data-stu-id="c41c2-104">A delegate is a type that you can use like any other type in Visual Basic.</span></span> <span data-ttu-id="c41c2-105">`AddressOf`运算符在应用于过程名称时返回一个委托对象。</span><span class="sxs-lookup"><span data-stu-id="c41c2-105">The `AddressOf` operator returns a delegate object when applied to a procedure name.</span></span>  
  
 <span data-ttu-id="c41c2-106">此示例包含一个带有委托参数的过程，该参数可以引用另一个过程，并使用 `AddressOf` 运算符获得。</span><span class="sxs-lookup"><span data-stu-id="c41c2-106">This example has a procedure with a delegate parameter that can take a reference to another procedure, obtained with the `AddressOf` operator.</span></span>  
  
### <a name="create-the-delegate-and-matching-procedures"></a><span data-ttu-id="c41c2-107">创建委托和匹配过程</span><span class="sxs-lookup"><span data-stu-id="c41c2-107">Create the delegate and matching procedures</span></span>  
  
1. <span data-ttu-id="c41c2-108">创建一个名为的委托 `MathOperator` 。</span><span class="sxs-lookup"><span data-stu-id="c41c2-108">Create a delegate named `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="c41c2-109">`AddNumbers`使用与相同的参数和返回值创建一个名为的过程 `MathOperator` ，使签名匹配。</span><span class="sxs-lookup"><span data-stu-id="c41c2-109">Create a procedure named `AddNumbers` with parameters and return value that match those of `MathOperator`, so that the signatures match.</span></span>  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. <span data-ttu-id="c41c2-110">使用匹配的签名创建一个名为的过程 `SubtractNumbers` `MathOperator` 。</span><span class="sxs-lookup"><span data-stu-id="c41c2-110">Create a procedure named `SubtractNumbers` with a signature that matches `MathOperator`.</span></span>  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. <span data-ttu-id="c41c2-111">创建一个名为 `DelegateTest` 的过程，该过程使用委托作为参数。</span><span class="sxs-lookup"><span data-stu-id="c41c2-111">Create a procedure named `DelegateTest` that takes a delegate as a parameter.</span></span>  
  
     <span data-ttu-id="c41c2-112">此过程可以接受对或的 `AddNumbers` 引用 `SubtractNumbers` ，因为其签名与 `MathOperator` 签名匹配。</span><span class="sxs-lookup"><span data-stu-id="c41c2-112">This procedure can accept a reference to `AddNumbers` or `SubtractNumbers`, because their signatures match the `MathOperator` signature.</span></span>  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. <span data-ttu-id="c41c2-113">创建一个名为 `Test` 的过程，该过程 `DelegateTest` 使用委托 `AddNumbers` 作为参数，并再次使用的委托 `SubtractNumbers` 作为参数。</span><span class="sxs-lookup"><span data-stu-id="c41c2-113">Create a procedure named `Test` that calls `DelegateTest` once with the delegate for `AddNumbers` as a parameter, and again with the delegate for `SubtractNumbers` as a parameter.</span></span>  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     <span data-ttu-id="c41c2-114">`Test`调用时，它首先显示 `AddNumbers` 对和的操作结果， `5` 即 `3` 8。</span><span class="sxs-lookup"><span data-stu-id="c41c2-114">When `Test` is called, it first displays the result of `AddNumbers` acting on `5` and `3`, which is 8.</span></span> <span data-ttu-id="c41c2-115">然后 `SubtractNumbers` ，将显示对和的操作结果，即 `9` `3` 6。</span><span class="sxs-lookup"><span data-stu-id="c41c2-115">Then the result of `SubtractNumbers` acting on `9` and `3` is displayed, which is 6.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c41c2-116">请参阅</span><span class="sxs-lookup"><span data-stu-id="c41c2-116">See also</span></span>

- [<span data-ttu-id="c41c2-117">委托</span><span class="sxs-lookup"><span data-stu-id="c41c2-117">Delegates</span></span>](index.md)
- [<span data-ttu-id="c41c2-118">AddressOf 运算符</span><span class="sxs-lookup"><span data-stu-id="c41c2-118">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="c41c2-119">Delegate 语句</span><span class="sxs-lookup"><span data-stu-id="c41c2-119">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="c41c2-120">如何：调用委托方法</span><span class="sxs-lookup"><span data-stu-id="c41c2-120">How to: Invoke a Delegate Method</span></span>](how-to-invoke-a-delegate-method.md)
