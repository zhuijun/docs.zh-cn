---
title: AndAlso 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371929"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="58923-102">AndAlso 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58923-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="58923-103">对两个表达式执行短路逻辑与运算。</span><span class="sxs-lookup"><span data-stu-id="58923-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58923-104">语法</span><span class="sxs-lookup"><span data-stu-id="58923-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="58923-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="58923-105">Parts</span></span>  
  
|<span data-ttu-id="58923-106">术语</span><span class="sxs-lookup"><span data-stu-id="58923-106">Term</span></span>|<span data-ttu-id="58923-107">定义</span><span class="sxs-lookup"><span data-stu-id="58923-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="58923-108">必需。</span><span class="sxs-lookup"><span data-stu-id="58923-108">Required.</span></span> <span data-ttu-id="58923-109">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="58923-109">Any `Boolean` expression.</span></span> <span data-ttu-id="58923-110">结果是 `Boolean` 这两个表达式的比较结果。</span><span class="sxs-lookup"><span data-stu-id="58923-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="58923-111">必需。</span><span class="sxs-lookup"><span data-stu-id="58923-111">Required.</span></span> <span data-ttu-id="58923-112">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="58923-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="58923-113">必需。</span><span class="sxs-lookup"><span data-stu-id="58923-113">Required.</span></span> <span data-ttu-id="58923-114">任何 `Boolean` 表达式。</span><span class="sxs-lookup"><span data-stu-id="58923-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58923-115">备注</span><span class="sxs-lookup"><span data-stu-id="58923-115">Remarks</span></span>  
 <span data-ttu-id="58923-116">如果编译后的代码可以根据另一个表达式的结果跳过对一个表达式的计算，则将逻辑运算称为*短路*。</span><span class="sxs-lookup"><span data-stu-id="58923-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="58923-117">如果第一个表达式的计算结果确定了运算的最终结果，则不需要计算第二个表达式，因为它不能更改最终结果。</span><span class="sxs-lookup"><span data-stu-id="58923-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="58923-118">如果绕过的表达式较复杂，或者它涉及过程调用，则短路可以提高性能。</span><span class="sxs-lookup"><span data-stu-id="58923-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="58923-119">如果两个表达式的计算结果均为 `True` ， `result` 则为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="58923-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="58923-120">下表说明了如何 `result` 确定。</span><span class="sxs-lookup"><span data-stu-id="58923-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="58923-121">如果 `expression1` 为 </span><span class="sxs-lookup"><span data-stu-id="58923-121">If `expression1` is</span></span>|<span data-ttu-id="58923-122">并且 `expression2` 为</span><span class="sxs-lookup"><span data-stu-id="58923-122">And `expression2` is</span></span>|<span data-ttu-id="58923-123">的值 `result` 为</span><span class="sxs-lookup"><span data-stu-id="58923-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="58923-124">（未计算）</span><span class="sxs-lookup"><span data-stu-id="58923-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="58923-125">数据类型</span><span class="sxs-lookup"><span data-stu-id="58923-125">Data Types</span></span>  
 <span data-ttu-id="58923-126">`AndAlso`仅为[布尔数据类型](../data-types/boolean-data-type.md)定义运算符。</span><span class="sxs-lookup"><span data-stu-id="58923-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="58923-127">Visual Basic 在计算表达式之前，根据需要将每个操作数转换为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="58923-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="58923-128">如果将结果赋给数值类型，Visual Basic 会将其从转换 `Boolean` 为该类型，使其 `False` 成为 `0` 并 `True` 变成 `-1` 。</span><span class="sxs-lookup"><span data-stu-id="58923-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="58923-129">有关详细信息，请参阅[布尔类型转换](../data-types/boolean-data-type.md#type-conversions)。</span><span class="sxs-lookup"><span data-stu-id="58923-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="58923-130">重载</span><span class="sxs-lookup"><span data-stu-id="58923-130">Overloading</span></span>  
 <span data-ttu-id="58923-131">[And 运算符](and-operator.md)和[IsFalse 运算符](isfalse-operator.md)可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义它们的行为。</span><span class="sxs-lookup"><span data-stu-id="58923-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="58923-132">重载 `And` 和 `IsFalse` 运算符会影响运算符的行为 `AndAlso` 。</span><span class="sxs-lookup"><span data-stu-id="58923-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="58923-133">如果你的代码 `AndAlso` 在重载和的类或结构上使用 `And` `IsFalse` ，请确保你了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="58923-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="58923-134">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="58923-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58923-135">示例</span><span class="sxs-lookup"><span data-stu-id="58923-135">Example</span></span>  
 <span data-ttu-id="58923-136">下面的示例使用 `AndAlso` 运算符对两个表达式执行逻辑与运算。</span><span class="sxs-lookup"><span data-stu-id="58923-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="58923-137">结果是一个 `Boolean` 值，该值表示整个联合表达式是否为 true。</span><span class="sxs-lookup"><span data-stu-id="58923-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="58923-138">如果第一个表达式为 `False` ，则不计算第二个表达式。</span><span class="sxs-lookup"><span data-stu-id="58923-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="58923-139">前面的示例 `True` 分别生成、 `False` 和的结果 `False` 。</span><span class="sxs-lookup"><span data-stu-id="58923-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="58923-140">在的计算中 `secondCheck` ，不计算第二个表达式，因为第一个表达式已经存在 `False` 。</span><span class="sxs-lookup"><span data-stu-id="58923-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="58923-141">但是，在的计算中计算第二个表达式 `thirdCheck` 。</span><span class="sxs-lookup"><span data-stu-id="58923-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58923-142">示例</span><span class="sxs-lookup"><span data-stu-id="58923-142">Example</span></span>  
 <span data-ttu-id="58923-143">下面的示例演示了在 `Function` 数组的元素中搜索给定值的过程。</span><span class="sxs-lookup"><span data-stu-id="58923-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="58923-144">如果数组为空，或超出了数组长度，则该 `While` 语句不会对照搜索值测试数组元素。</span><span class="sxs-lookup"><span data-stu-id="58923-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="58923-145">另请参阅</span><span class="sxs-lookup"><span data-stu-id="58923-145">See also</span></span>

- [<span data-ttu-id="58923-146">逻辑/按位运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58923-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="58923-147">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="58923-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="58923-148">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="58923-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="58923-149">And 运算符</span><span class="sxs-lookup"><span data-stu-id="58923-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="58923-150">IsFalse 运算符</span><span class="sxs-lookup"><span data-stu-id="58923-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="58923-151">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="58923-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
