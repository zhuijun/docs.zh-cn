---
title: ^ 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: e139becf74ae367266a23513e18d0bdbdd24cdea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371383"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="13d1d-102">^ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d1d-102">^ Operator (Visual Basic)</span></span>

<span data-ttu-id="13d1d-103">以一个数字为底、另一数字为幂求值。</span><span class="sxs-lookup"><span data-stu-id="13d1d-103">Raises a number to the power of another number.</span></span>

## <a name="syntax"></a><span data-ttu-id="13d1d-104">语法</span><span class="sxs-lookup"><span data-stu-id="13d1d-104">Syntax</span></span>

```vb
number ^ exponent
```

## <a name="parts"></a><span data-ttu-id="13d1d-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="13d1d-105">Parts</span></span>

`number`\
<span data-ttu-id="13d1d-106">必需。</span><span class="sxs-lookup"><span data-stu-id="13d1d-106">Required.</span></span> <span data-ttu-id="13d1d-107">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="13d1d-107">Any numeric expression.</span></span>

`exponent`\
<span data-ttu-id="13d1d-108">必需。</span><span class="sxs-lookup"><span data-stu-id="13d1d-108">Required.</span></span> <span data-ttu-id="13d1d-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="13d1d-109">Any numeric expression.</span></span>

## <a name="result"></a><span data-ttu-id="13d1d-110">结果</span><span class="sxs-lookup"><span data-stu-id="13d1d-110">Result</span></span>

<span data-ttu-id="13d1d-111">结果会 `number` 引发的次幂 `exponent` ，总是作为 `Double` 值。</span><span class="sxs-lookup"><span data-stu-id="13d1d-111">The result is `number` raised to the power of `exponent`, always as a `Double` value.</span></span>

## <a name="supported-types"></a><span data-ttu-id="13d1d-112">支持的类型</span><span class="sxs-lookup"><span data-stu-id="13d1d-112">Supported Types</span></span>

<span data-ttu-id="13d1d-113">`Double`.</span><span class="sxs-lookup"><span data-stu-id="13d1d-113">`Double`.</span></span> <span data-ttu-id="13d1d-114">任何不同类型的操作数都转换为 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="13d1d-114">Operands of any different type are converted to `Double`.</span></span>

## <a name="remarks"></a><span data-ttu-id="13d1d-115">备注</span><span class="sxs-lookup"><span data-stu-id="13d1d-115">Remarks</span></span>

<span data-ttu-id="13d1d-116">Visual Basic 总是对[Double 数据类型](../data-types/double-data-type.md)执行幂运算。</span><span class="sxs-lookup"><span data-stu-id="13d1d-116">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span>

<span data-ttu-id="13d1d-117">的值 `exponent` 可以是小数、负数或同时为两者。</span><span class="sxs-lookup"><span data-stu-id="13d1d-117">The value of `exponent` can be fractional, negative, or both.</span></span>

<span data-ttu-id="13d1d-118">如果在单个表达式中执行了多个幂运算，则会 `^` 按从左至右的顺序计算运算符。</span><span class="sxs-lookup"><span data-stu-id="13d1d-118">When more than one exponentiation is performed in a single expression, the `^` operator is evaluated as it is encountered from left to right.</span></span>

> [!NOTE]
> <span data-ttu-id="13d1d-119">`^`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="13d1d-119">The `^` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="13d1d-120">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="13d1d-120">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="13d1d-121">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="13d1d-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="13d1d-122">示例</span><span class="sxs-lookup"><span data-stu-id="13d1d-122">Example</span></span>

<span data-ttu-id="13d1d-123">下面的示例使用运算符来计算 `^` 指数的幂。</span><span class="sxs-lookup"><span data-stu-id="13d1d-123">The following example uses the `^` operator to raise a number to the power of an exponent.</span></span> <span data-ttu-id="13d1d-124">结果是第一个操作数的次幂。</span><span class="sxs-lookup"><span data-stu-id="13d1d-124">The result is the first operand raised to the power of the second.</span></span>

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

<span data-ttu-id="13d1d-125">前面的示例生成了以下结果：</span><span class="sxs-lookup"><span data-stu-id="13d1d-125">The preceding example produces the following results:</span></span>

<span data-ttu-id="13d1d-126">`exp1`设置为4（2 squared）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-126">`exp1` is set to 4 (2 squared).</span></span>

<span data-ttu-id="13d1d-127">`exp2`设置为19683（3个立方，然后是该值的立方）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-127">`exp2` is set to 19683 (3 cubed, then that value cubed).</span></span>

<span data-ttu-id="13d1d-128">`exp3`设置为-125 （-5 的立方）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-128">`exp3` is set to -125 (-5 cubed).</span></span>

<span data-ttu-id="13d1d-129">`exp4`设置为625（-5 到第四次幂）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-129">`exp4` is set to 625 (-5 to the fourth power).</span></span>

<span data-ttu-id="13d1d-130">`exp5`设置为2（多维数据集的第8个）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-130">`exp5` is set to 2 (cube root of 8).</span></span>

<span data-ttu-id="13d1d-131">`exp6`设置为0.5 （1.0 除以8的 cube 根）。</span><span class="sxs-lookup"><span data-stu-id="13d1d-131">`exp6` is set to 0.5 (1.0 divided by the cube root of 8).</span></span>

<span data-ttu-id="13d1d-132">请注意前面示例的表达式中的括号的重要性。</span><span class="sxs-lookup"><span data-stu-id="13d1d-132">Note the importance of the parentheses in the expressions in the preceding example.</span></span> <span data-ttu-id="13d1d-133">由于*运算符优先级*，Visual Basic 通常在 `^` 任何其他运算符（甚至一元运算符）之前执行运算符 `–` 。</span><span class="sxs-lookup"><span data-stu-id="13d1d-133">Because of *operator precedence*, Visual Basic normally performs the `^` operator before any others, even the unary `–` operator.</span></span> <span data-ttu-id="13d1d-134">如果 `exp4` 和的 `exp6` 计算结果没有括号，则会生成以下结果：</span><span class="sxs-lookup"><span data-stu-id="13d1d-134">If `exp4` and `exp6` had been calculated without parentheses, they would have produced the following results:</span></span>

<span data-ttu-id="13d1d-135">`exp4 = -5 ^ 4`将计算为–（5到第四次幂），这会导致-625。</span><span class="sxs-lookup"><span data-stu-id="13d1d-135">`exp4 = -5 ^ 4` would be calculated as –(5 to the fourth power), which would result in -625.</span></span>

<span data-ttu-id="13d1d-136">`exp6 = 8 ^ -1.0 / 3.0`将计算为（8到-1 个幂，即0.125）除以3.0，这将导致0.041666666666666666666666666666667。</span><span class="sxs-lookup"><span data-stu-id="13d1d-136">`exp6 = 8 ^ -1.0 / 3.0` would be calculated as (8 to the –1 power, or 0.125) divided by 3.0, which would result in 0.041666666666666666666666666666667.</span></span>

## <a name="see-also"></a><span data-ttu-id="13d1d-137">另请参阅</span><span class="sxs-lookup"><span data-stu-id="13d1d-137">See also</span></span>

- [<span data-ttu-id="13d1d-138">^ = 运算符</span><span class="sxs-lookup"><span data-stu-id="13d1d-138">^= Operator</span></span>](exponentiation-assignment-operator.md)
- [<span data-ttu-id="13d1d-139">算术运算符</span><span class="sxs-lookup"><span data-stu-id="13d1d-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="13d1d-140">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="13d1d-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="13d1d-141">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="13d1d-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="13d1d-142">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13d1d-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
