---
title: 算术运算符
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: 023e479736285aa2d04509e05f49fe930cb4721d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91090074"
---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="f515d-102">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f515d-102">Arithmetic Operators in Visual Basic</span></span>

<span data-ttu-id="f515d-103">算术运算符用于执行许多常见的算术运算，这些运算涉及到用文本、变量、其他表达式、函数和属性调用和常量表示的数值的计算。</span><span class="sxs-lookup"><span data-stu-id="f515d-103">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="f515d-104">同时，采用算术运算符进行分类的是位移位运算符，它在操作数的各个位级别上起作用，并将其位模式向左或向右移动。</span><span class="sxs-lookup"><span data-stu-id="f515d-104">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="f515d-105">算术运算</span><span class="sxs-lookup"><span data-stu-id="f515d-105">Arithmetic Operations</span></span>  

 <span data-ttu-id="f515d-106">您可以使用 [+ 运算符](../../../language-reference/operators/addition-operator.md)将两个值一起添加到表达式中，或用 [-Operator (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)进行减法运算，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="f515d-106">You can add two values in an expression together with the [+ Operator](../../../language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 <span data-ttu-id="f515d-107">求反还使用 [-Operator (Visual Basic) ](../../../language-reference/operators/subtraction-operator.md)，但只有一个操作数，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="f515d-107">Negation also uses the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 <span data-ttu-id="f515d-108">乘法和除法分别使用 [\* 运算符](../../../language-reference/operators/multiplication-operator.md) 和 [/运算符 (Visual Basic) ](../../../language-reference/operators/floating-point-division-operator.md)，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="f515d-108">Multiplication and division use the [\* Operator](../../../language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 <span data-ttu-id="f515d-109">幂运算使用 [^ 运算符](../../../language-reference/operators/exponentiation-operator.md)，如下面的示例所示。</span><span class="sxs-lookup"><span data-stu-id="f515d-109">Exponentiation uses the [^ Operator](../../../language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 <span data-ttu-id="f515d-110">使用 [\ 运算符 (Visual Basic) ](../../../language-reference/operators/integer-division-operator.md)执行整数除法运算。</span><span class="sxs-lookup"><span data-stu-id="f515d-110">Integer division is carried out using the [\ Operator (Visual Basic)](../../../language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="f515d-111">整数除法返回商，即表示除数可以分为被除数的次数的整数，而不考虑任何余数。</span><span class="sxs-lookup"><span data-stu-id="f515d-111">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="f515d-112">除数和被除数都必须是整型 (、、、、、、 `SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` 和 `ULong`) 。</span><span class="sxs-lookup"><span data-stu-id="f515d-112">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="f515d-113">所有其他类型必须首先转换为整型类型。</span><span class="sxs-lookup"><span data-stu-id="f515d-113">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="f515d-114">下面的示例演示了整数除法。</span><span class="sxs-lookup"><span data-stu-id="f515d-114">The following example demonstrates integer division.</span></span>  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 <span data-ttu-id="f515d-115">使用 [Mod 运算符](../../../language-reference/operators/mod-operator.md)执行取模运算。</span><span class="sxs-lookup"><span data-stu-id="f515d-115">Modulus arithmetic is performed using the [Mod Operator](../../../language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="f515d-116">此运算符返回将除数除以整数次后所得的余数。</span><span class="sxs-lookup"><span data-stu-id="f515d-116">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="f515d-117">如果除数和被除数均为整型类型，则返回的值是整型。</span><span class="sxs-lookup"><span data-stu-id="f515d-117">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="f515d-118">如果除数和被除数为浮点类型，则返回的值也是浮点型。</span><span class="sxs-lookup"><span data-stu-id="f515d-118">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="f515d-119">下例演示此行为。</span><span class="sxs-lookup"><span data-stu-id="f515d-119">The following example demonstrates this behavior.</span></span>  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="f515d-120">尝试被零除</span><span class="sxs-lookup"><span data-stu-id="f515d-120">Attempted Division by Zero</span></span>  

 <span data-ttu-id="f515d-121">被零除具有不同的结果，具体取决于所涉及的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f515d-121">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="f515d-122">在整数除法 (`SByte` 、 `Byte` 、 `Short` 、 `UShort` 、 `Integer` 、 `UInteger` 、 `Long` 、 `ULong`) ，.NET Framework 将引发 <xref:System.DivideByZeroException> 异常。</span><span class="sxs-lookup"><span data-stu-id="f515d-122">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the .NET Framework throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="f515d-123">在或数据类型的除法运算中 `Decimal` `Single` ，.NET Framework 也会引发 <xref:System.DivideByZeroException> 异常。</span><span class="sxs-lookup"><span data-stu-id="f515d-123">In division operations on the `Decimal` or `Single` data type, the .NET Framework also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="f515d-124">在涉及数据类型的浮点除法中 `Double` ，不会引发异常，并且结果是表示、或的类成员 <xref:System.Double.NaN> <xref:System.Double.PositiveInfinity> <xref:System.Double.NegativeInfinity> ，具体取决于被除数。</span><span class="sxs-lookup"><span data-stu-id="f515d-124">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="f515d-125">下表总结了试图将值除以零的各种结果 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-125">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="f515d-126">被除数数据类型</span><span class="sxs-lookup"><span data-stu-id="f515d-126">Dividend data type</span></span>|<span data-ttu-id="f515d-127">除数数据类型</span><span class="sxs-lookup"><span data-stu-id="f515d-127">Divisor data type</span></span>|<span data-ttu-id="f515d-128">股利值</span><span class="sxs-lookup"><span data-stu-id="f515d-128">Dividend value</span></span>|<span data-ttu-id="f515d-129">结果</span><span class="sxs-lookup"><span data-stu-id="f515d-129">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="f515d-130">0</span><span class="sxs-lookup"><span data-stu-id="f515d-130">0</span></span>|<span data-ttu-id="f515d-131"><xref:System.Double.NaN> (不是数学定义的数字) </span><span class="sxs-lookup"><span data-stu-id="f515d-131"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="f515d-132">> 0</span><span class="sxs-lookup"><span data-stu-id="f515d-132">> 0</span></span>|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|<span data-ttu-id="f515d-133">\< 0</span><span class="sxs-lookup"><span data-stu-id="f515d-133">\< 0</span></span>|<xref:System.Double.NegativeInfinity>|  
  
 <span data-ttu-id="f515d-134">捕获 <xref:System.DivideByZeroException> 异常时，可以使用其成员帮助处理异常。</span><span class="sxs-lookup"><span data-stu-id="f515d-134">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="f515d-135">例如， <xref:System.Exception.Message%2A> 属性包含异常的消息文本。</span><span class="sxs-lookup"><span data-stu-id="f515d-135">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="f515d-136">有关详细信息，请参阅 [Try...Catch...Finally 语句](../../../language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f515d-136">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="f515d-137">移位运算</span><span class="sxs-lookup"><span data-stu-id="f515d-137">Bit-Shift Operations</span></span>  

 <span data-ttu-id="f515d-138">移位运算对位模式执行算术移位运算。</span><span class="sxs-lookup"><span data-stu-id="f515d-138">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="f515d-139">模式包含在左侧的操作数中，而右侧的操作数指定了要将模式移位到的位置数。</span><span class="sxs-lookup"><span data-stu-id="f515d-139">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="f515d-140">您可以用 [>> 运算符](../../../language-reference/operators/right-shift-operator.md) 将模式向右移动，或将 [<< 运算符](../../../language-reference/operators/left-shift-operator.md)左移。</span><span class="sxs-lookup"><span data-stu-id="f515d-140">You can shift the pattern to the right with the [>> Operator](../../../language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="f515d-141">模式操作数的数据类型必须是、、 `SByte` `Byte` `Short` 、 `UShort` 、、、 `Integer` `UInteger` `Long` 或 `ULong` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-141">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="f515d-142">移位量操作数的数据类型必须为 `Integer` 或必须扩大到 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-142">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="f515d-143">算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。</span><span class="sxs-lookup"><span data-stu-id="f515d-143">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="f515d-144">移位后空出的位位置设置如下：</span><span class="sxs-lookup"><span data-stu-id="f515d-144">The bit positions vacated by a shift are set as follows:</span></span>  
  
- <span data-ttu-id="f515d-145">对于算术左移，为0</span><span class="sxs-lookup"><span data-stu-id="f515d-145">0 for an arithmetic left shift</span></span>  
  
- <span data-ttu-id="f515d-146">如果为负数，则为0</span><span class="sxs-lookup"><span data-stu-id="f515d-146">0 for an arithmetic right shift of a positive number</span></span>  
  
- <span data-ttu-id="f515d-147">0表示无符号数据类型的算术右移位 (`Byte` 、 `UShort` 、 `UInteger` 、 `ULong`) </span><span class="sxs-lookup"><span data-stu-id="f515d-147">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
- <span data-ttu-id="f515d-148">1表示负数 (`SByte` 、 `Short` 、 `Integer` 或 `Long`) 的算术右移位</span><span class="sxs-lookup"><span data-stu-id="f515d-148">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="f515d-149">下面的示例将 `Integer` 值向左和向右移位。</span><span class="sxs-lookup"><span data-stu-id="f515d-149">The following example shifts an `Integer` value both left and right.</span></span>  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 <span data-ttu-id="f515d-150">算术移位从不产生溢出异常。</span><span class="sxs-lookup"><span data-stu-id="f515d-150">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="f515d-151">按位运算</span><span class="sxs-lookup"><span data-stu-id="f515d-151">Bitwise Operations</span></span>  

 <span data-ttu-id="f515d-152">除了作为逻辑运算符外，、 `Not` 、 `Or` `And` 和还会在 `Xor` 对数值使用时执行按位运算。</span><span class="sxs-lookup"><span data-stu-id="f515d-152">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="f515d-153">有关详细信息，请参阅 [Visual Basic 中逻辑与按位运算符](logical-and-bitwise-operators.md)中的 "位运算"。</span><span class="sxs-lookup"><span data-stu-id="f515d-153">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="f515d-154">类型安全</span><span class="sxs-lookup"><span data-stu-id="f515d-154">Type Safety</span></span>  

 <span data-ttu-id="f515d-155">操作数通常应为同一类型。</span><span class="sxs-lookup"><span data-stu-id="f515d-155">Operands should normally be of the same type.</span></span> <span data-ttu-id="f515d-156">例如，如果您正在使用变量执行加法操作 `Integer` ，则应将其添加到另一个 `Integer` 变量，并且应将结果分配给类型的变量 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-156">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="f515d-157">确保良好的类型安全编码做法的一种方法是使用 [Option Strict 语句](../../../language-reference/statements/option-strict-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="f515d-157">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="f515d-158">如果设置 `Option Strict On` ，则 Visual Basic 会自动执行 *类型安全* 转换。</span><span class="sxs-lookup"><span data-stu-id="f515d-158">If you set `Option Strict On`, Visual Basic automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="f515d-159">例如，如果尝试将 `Integer` 变量添加到 `Double` 变量并将值分配给 `Double` 变量，则操作会正常进行，因为 `Integer` 值可以转换为， `Double` 而不会丢失数据。</span><span class="sxs-lookup"><span data-stu-id="f515d-159">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="f515d-160">另一方面，类型不安全的转换将导致编译器错误 `Option Strict On` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-160">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="f515d-161">例如，如果尝试将 `Integer` 变量添加到 `Double` 变量并将值分配给 `Integer` 变量，则编译器错误将会出现，因为 `Double` 变量不能隐式转换为类型 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f515d-161">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="f515d-162">但是，如果您设置 `Option Strict Off` ，则 Visual Basic 允许进行隐式收缩转换，但它们可能会导致数据或精度意外丢失。</span><span class="sxs-lookup"><span data-stu-id="f515d-162">If you set `Option Strict Off`, however, Visual Basic allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="f515d-163">出于此原因，我们建议你在 `Option Strict On` 编写生产代码时使用。</span><span class="sxs-lookup"><span data-stu-id="f515d-163">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="f515d-164">有关详细信息，请参阅 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)。</span><span class="sxs-lookup"><span data-stu-id="f515d-164">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f515d-165">请参阅</span><span class="sxs-lookup"><span data-stu-id="f515d-165">See also</span></span>

- [<span data-ttu-id="f515d-166">算术运算符</span><span class="sxs-lookup"><span data-stu-id="f515d-166">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="f515d-167">移位运算符</span><span class="sxs-lookup"><span data-stu-id="f515d-167">Bit Shift Operators</span></span>](../../../language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="f515d-168">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f515d-168">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="f515d-169">串联运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f515d-169">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="f515d-170">Visual Basic 中的逻辑运算符和位运算符</span><span class="sxs-lookup"><span data-stu-id="f515d-170">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="f515d-171">运算符的有效组合</span><span class="sxs-lookup"><span data-stu-id="f515d-171">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
