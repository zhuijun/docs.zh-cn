---
title: '\ 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: cf2dc66532925d56cea6fd141f44a245bc2dd8dd
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873392"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8ecd6-102">\ 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ecd6-102">\ Operator (Visual Basic)</span></span>

<span data-ttu-id="8ecd6-103">使两个数字相除，返回整数结果。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecd6-104">语法</span><span class="sxs-lookup"><span data-stu-id="8ecd6-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="8ecd6-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="8ecd6-105">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="8ecd6-106">必需。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-106">Required.</span></span> <span data-ttu-id="8ecd6-107">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="8ecd6-108">必需。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-108">Required.</span></span> <span data-ttu-id="8ecd6-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="8ecd6-110">支持的类型</span><span class="sxs-lookup"><span data-stu-id="8ecd6-110">Supported Types</span></span>  

 <span data-ttu-id="8ecd6-111">所有数值类型，包括无符号和浮点类型和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="8ecd6-112">结果</span><span class="sxs-lookup"><span data-stu-id="8ecd6-112">Result</span></span>  

 <span data-ttu-id="8ecd6-113">结果是除以的整数商 `expression1` `expression2` ，它放弃了余数并仅保留整数部分。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="8ecd6-114">这称为 " *截断*"。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="8ecd6-115">Result 数据类型是适用于和的数据类型的数值类型 `expression1` `expression2` 。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="8ecd6-116">请参阅 [运算符结果的数据类型](data-types-of-operator-results.md)中的 "整数算法" 表。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="8ecd6-117">[/运算符 (Visual Basic) ](floating-point-division-operator.md)返回完整商，这将保留小数部分的剩余部分。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-117">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ecd6-118">备注</span><span class="sxs-lookup"><span data-stu-id="8ecd6-118">Remarks</span></span>  

 <span data-ttu-id="8ecd6-119">在执行除法运算之前，Visual Basic 会尝试将任何浮点数值表达式转换为 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="8ecd6-120">如果 `Option Strict` 为 `On` ，则会发生编译器错误。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="8ecd6-121">如果 `Option Strict` 为 `Off` ， <xref:System.OverflowException> 则当值超出 [Long 数据类型](../data-types/long-data-type.md)的范围时，可能会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="8ecd6-122">转换为的 `Long` 还服从于 *银行家的舍入*。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="8ecd6-123">有关详细信息，请参阅 [类型转换函数](../functions/type-conversion-functions.md)中的 "小数部分"。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="8ecd6-124">如果 `expression1` 或的 `expression2` 计算结果不为 [空](../nothing.md)，则将其视为零。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-124">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="8ecd6-125">尝试被零除</span><span class="sxs-lookup"><span data-stu-id="8ecd6-125">Attempted Division by Zero</span></span>  

 <span data-ttu-id="8ecd6-126">如果 `expression2` 计算结果为零，则 `\` 运算符会引发 <xref:System.DivideByZeroException> 异常。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="8ecd6-127">对于操作数的所有数值数据类型都是如此。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ecd6-128">`\`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8ecd6-129">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8ecd6-130">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ecd6-131">示例</span><span class="sxs-lookup"><span data-stu-id="8ecd6-131">Example</span></span>  

 <span data-ttu-id="8ecd6-132">下面的示例使用 `\` 运算符来执行整数除法。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="8ecd6-133">结果是一个整数，表示两个操作数的整数商，余数被丢弃。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="8ecd6-134">前面的示例中的表达式分别返回值2、3、33和-22。</span><span class="sxs-lookup"><span data-stu-id="8ecd6-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecd6-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8ecd6-135">See also</span></span>

- [<span data-ttu-id="8ecd6-136">\\= 运算符</span><span class="sxs-lookup"><span data-stu-id="8ecd6-136">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="8ecd6-137">/Operator (Visual Basic) </span><span class="sxs-lookup"><span data-stu-id="8ecd6-137">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="8ecd6-138">Option Strict 语句</span><span class="sxs-lookup"><span data-stu-id="8ecd6-138">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="8ecd6-139">算术运算符</span><span class="sxs-lookup"><span data-stu-id="8ecd6-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="8ecd6-140">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="8ecd6-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="8ecd6-141">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="8ecd6-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="8ecd6-142">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ecd6-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
