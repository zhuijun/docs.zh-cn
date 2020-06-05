---
title: 宽松委托转换
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410665"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="9d223-102">宽松委托转换 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d223-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="9d223-103">通过宽松委托转换，您可以将 sub 和函数分配给委托或处理程序，即使它们的签名不相同。</span><span class="sxs-lookup"><span data-stu-id="9d223-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="9d223-104">因此，绑定到委托将与已允许方法调用的绑定一致。</span><span class="sxs-lookup"><span data-stu-id="9d223-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="9d223-105">参数和返回类型</span><span class="sxs-lookup"><span data-stu-id="9d223-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="9d223-106">宽松转换要求在设置为以下条件时满足以下条件 `Option Strict` `On` ：</span><span class="sxs-lookup"><span data-stu-id="9d223-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="9d223-107">必须将每个委托参数的数据类型的扩大转换为分配的函数或的对应参数的数据类型 `Sub` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="9d223-108">在下面的示例中，委托 `Del1` 具有一个参数，即 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="9d223-109">`m`指定 lambda 表达式中的参数必须有一个数据类型，该数据类型的扩大转换来自 `Integer` ，如 `Long` 或 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="9d223-110">仅当设置为时，才允许收缩转换 `Option Strict` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="9d223-111">扩大转换必须与指定函数的返回类型或 `Sub` 委托的返回类型在相反方向上存在。</span><span class="sxs-lookup"><span data-stu-id="9d223-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="9d223-112">在下面的示例中，每个分配的 lambda 表达式的主体的计算结果都必须是扩大到的数据类型， `Integer` 因为的返回类型 `del1` 是 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="9d223-113">如果 `Option Strict` 设置为，则将 `Off` 在这两个方向上删除扩大限制。</span><span class="sxs-lookup"><span data-stu-id="9d223-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="9d223-114">省略参数规范</span><span class="sxs-lookup"><span data-stu-id="9d223-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="9d223-115">宽松委托还允许您完全省略分配的方法中的参数规范：</span><span class="sxs-lookup"><span data-stu-id="9d223-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="9d223-116">请注意，不能指定某些参数并忽略其他参数。</span><span class="sxs-lookup"><span data-stu-id="9d223-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="9d223-117">在某些情况下，忽略参数的功能非常有用，例如定义一个事件处理程序，其中涉及多个复杂参数。</span><span class="sxs-lookup"><span data-stu-id="9d223-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="9d223-118">不使用某些事件处理程序的参数。</span><span class="sxs-lookup"><span data-stu-id="9d223-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="9d223-119">相反，处理程序将直接访问在其上注册事件的控件的状态，并忽略参数。</span><span class="sxs-lookup"><span data-stu-id="9d223-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="9d223-120">宽松的委托允许在没有歧义结果时省略此类声明中的参数。</span><span class="sxs-lookup"><span data-stu-id="9d223-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="9d223-121">在下面的示例中，可以将完全指定的方法 `OnClick` 重写为 `RelaxedOnClick` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="9d223-122">AddressOf 示例</span><span class="sxs-lookup"><span data-stu-id="9d223-122">AddressOf Examples</span></span>  
 <span data-ttu-id="9d223-123">前面的示例中使用了 Lambda 表达式，使类型关系易于查看。</span><span class="sxs-lookup"><span data-stu-id="9d223-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="9d223-124">但是，允许使用、或的委托分配使用相同的 `AddressOf` 松弛法 `Handles` `AddHandler` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="9d223-125">在下面的示例中，函数 `f1` 、、 `f2` 和都 `f3` `f4` 可以分配给 `Del1` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="9d223-126">仅当设置为时，下面的示例才有效 `Option Strict` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="9d223-127">删除函数返回</span><span class="sxs-lookup"><span data-stu-id="9d223-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="9d223-128">通过宽松委托转换，您可以将函数分配给 `Sub` 委托，从而有效地忽略函数的返回值。</span><span class="sxs-lookup"><span data-stu-id="9d223-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="9d223-129">但是，不能将分配 `Sub` 给函数委托。</span><span class="sxs-lookup"><span data-stu-id="9d223-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="9d223-130">在下面的示例中，函数的地址 `doubler` 分配给 `Sub` 委托 `Del3` 。</span><span class="sxs-lookup"><span data-stu-id="9d223-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="9d223-131">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9d223-131">See also</span></span>

- [<span data-ttu-id="9d223-132">Lambda 表达式</span><span class="sxs-lookup"><span data-stu-id="9d223-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="9d223-133">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="9d223-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="9d223-134">委托</span><span class="sxs-lookup"><span data-stu-id="9d223-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="9d223-135">如何：在 Visual Basic 中将过程传递给另一过程</span><span class="sxs-lookup"><span data-stu-id="9d223-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="9d223-136">局部类型推理</span><span class="sxs-lookup"><span data-stu-id="9d223-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="9d223-137">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="9d223-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
