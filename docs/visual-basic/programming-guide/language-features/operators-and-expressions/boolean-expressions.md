---
title: 布尔表达式
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 8d34eb4c8b14bb4754f2a3cf5b6f9a7601aa4662
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388953"
---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="12b87-102">布尔表达式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12b87-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="12b87-103">*布尔表达式*是计算结果为[布尔数据类型](../../../language-reference/data-types/boolean-data-type.md)的值的表达式： `True` 或 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="12b87-104">`Boolean`表达式可以采用多种形式。</span><span class="sxs-lookup"><span data-stu-id="12b87-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="12b87-105">最简单的方式是将变量值直接 `Boolean` 与文本进行比较 `Boolean` ，如下面的示例中所示。</span><span class="sxs-lookup"><span data-stu-id="12b87-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="12b87-106">= 运算符的两种含义</span><span class="sxs-lookup"><span data-stu-id="12b87-106">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="12b87-107">请注意，赋值语句与 `newCustomer = True` 前面示例中的表达式看起来相同，但它执行不同的功能，并且使用方式不同。</span><span class="sxs-lookup"><span data-stu-id="12b87-107">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="12b87-108">在前面的示例中，表达式 `newCustomer = True` 表示一个布尔值，而 `=` 符号被解释为比较运算符。</span><span class="sxs-lookup"><span data-stu-id="12b87-108">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="12b87-109">在独立语句中， `=` 符号被解释为赋值运算符，并将右侧的值赋给左侧的变量。</span><span class="sxs-lookup"><span data-stu-id="12b87-109">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="12b87-110">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="12b87-110">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 <span data-ttu-id="12b87-111">有关详细信息，请参阅[值比较](value-comparisons.md)和[语句](../../../language-reference/statements/index.md)。</span><span class="sxs-lookup"><span data-stu-id="12b87-111">For further information, see [Value Comparisons](value-comparisons.md) and [Statements](../../../language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="12b87-112">比较运算符</span><span class="sxs-lookup"><span data-stu-id="12b87-112">Comparison Operators</span></span>  
 <span data-ttu-id="12b87-113">比较运算符（例如、、、、 `=` `<` 和） `>` `<>` `<=` `>=` 生成布尔表达式，方法是将运算符左侧的表达式与运算符右侧的表达式进行比较，并将结果计算为 `True` 或 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-113">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="12b87-114">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="12b87-114">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="12b87-115">因为42小于81，所以前面的示例中的布尔表达式的计算结果为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-115">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="12b87-116">有关此类表达式的详细信息，请参阅[值比较](value-comparisons.md)。</span><span class="sxs-lookup"><span data-stu-id="12b87-116">For more information on this kind of expression, see [Value Comparisons](value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="12b87-117">与逻辑运算符组合在一起的比较运算符</span><span class="sxs-lookup"><span data-stu-id="12b87-117">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="12b87-118">可以使用逻辑运算符组合比较表达式以生成更复杂的布尔表达式。</span><span class="sxs-lookup"><span data-stu-id="12b87-118">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="12b87-119">下面的示例演示如何结合使用比较运算符和逻辑运算符。</span><span class="sxs-lookup"><span data-stu-id="12b87-119">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="12b87-120">在前面的示例中，整个表达式的值取决于运算符两侧的表达式的值 `And` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-120">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="12b87-121">如果两个表达式都是 `True` ，则整个表达式的计算结果为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-121">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="12b87-122">如果任一表达式为 `False` ，则整个表达式的计算结果为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-122">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="12b87-123">短路运算符</span><span class="sxs-lookup"><span data-stu-id="12b87-123">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="12b87-124">逻辑运算符 `AndAlso` 和 `OrElse` 表现为*短路*的行为。</span><span class="sxs-lookup"><span data-stu-id="12b87-124">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="12b87-125">短路运算符首先计算左操作数。</span><span class="sxs-lookup"><span data-stu-id="12b87-125">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="12b87-126">如果左操作数确定整个表达式的值，则程序执行将继续，而不计算正确的表达式。</span><span class="sxs-lookup"><span data-stu-id="12b87-126">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="12b87-127">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="12b87-127">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 <span data-ttu-id="12b87-128">在前面的示例中，运算符计算左侧表达式的值 `45 < 12` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-128">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="12b87-129">由于左侧表达式的计算结果为 `False` ，因此整个逻辑表达式的计算结果必须为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-129">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="12b87-130">因此，程序执行会跳过块中代码的执行 `If` ，而不计算正确的表达式 `testFunction(3)` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-130">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="12b87-131">此示例不调用， `testFunction()` 因为左侧表达式 falsifies 整个表达式。</span><span class="sxs-lookup"><span data-stu-id="12b87-131">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="12b87-132">同样，如果逻辑表达式中的左侧表达式的 `OrElse` 计算结果为 `True` ，则执行将继续执行下一行代码，而不计算正确的表达式，因为左侧表达式已经验证了整个表达式。</span><span class="sxs-lookup"><span data-stu-id="12b87-132">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="12b87-133">与非短路运算符的比较</span><span class="sxs-lookup"><span data-stu-id="12b87-133">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="12b87-134">相反，当使用逻辑运算符和时，将计算逻辑运算符的两侧 `And` `Or` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-134">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="12b87-135">下面的示例对此进行了演示。</span><span class="sxs-lookup"><span data-stu-id="12b87-135">The following example illustrates this.</span></span>  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 <span data-ttu-id="12b87-136">前面的示例将调用， `testFunction()` 即使左侧表达式的计算结果为 `False` 。</span><span class="sxs-lookup"><span data-stu-id="12b87-136">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="12b87-137">括号中的表达式</span><span class="sxs-lookup"><span data-stu-id="12b87-137">Parenthetical Expressions</span></span>  
 <span data-ttu-id="12b87-138">您可以使用括号来控制布尔表达式的计算顺序。</span><span class="sxs-lookup"><span data-stu-id="12b87-138">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="12b87-139">用括号括起来的表达式首先计算。</span><span class="sxs-lookup"><span data-stu-id="12b87-139">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="12b87-140">对于多个级别的嵌套，将优先顺序授予最深层嵌套的表达式。</span><span class="sxs-lookup"><span data-stu-id="12b87-140">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="12b87-141">在括号内，计算按照运算符优先级的规则进行。</span><span class="sxs-lookup"><span data-stu-id="12b87-141">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="12b87-142">有关详细信息，请参阅[Visual Basic 中的运算符优先级](../../../language-reference/operators/operator-precedence.md)。</span><span class="sxs-lookup"><span data-stu-id="12b87-142">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12b87-143">另请参阅</span><span class="sxs-lookup"><span data-stu-id="12b87-143">See also</span></span>

- [<span data-ttu-id="12b87-144">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="12b87-144">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="12b87-145">值的比较</span><span class="sxs-lookup"><span data-stu-id="12b87-145">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="12b87-146">语句</span><span class="sxs-lookup"><span data-stu-id="12b87-146">Statements</span></span>](../statements.md)
- [<span data-ttu-id="12b87-147">比较运算符</span><span class="sxs-lookup"><span data-stu-id="12b87-147">Comparison Operators</span></span>](../../../language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="12b87-148">运算符的有效组合</span><span class="sxs-lookup"><span data-stu-id="12b87-148">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="12b87-149">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="12b87-149">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="12b87-150">布尔数据类型</span><span class="sxs-lookup"><span data-stu-id="12b87-150">Boolean Data Type</span></span>](../../../language-reference/data-types/boolean-data-type.md)
