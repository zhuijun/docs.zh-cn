---
title: '* 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409307"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="722f7-102">\* 运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722f7-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="722f7-103">使两个数字相乘。</span><span class="sxs-lookup"><span data-stu-id="722f7-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="722f7-104">语法</span><span class="sxs-lookup"><span data-stu-id="722f7-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="722f7-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="722f7-105">Parts</span></span>  
  
|<span data-ttu-id="722f7-106">术语</span><span class="sxs-lookup"><span data-stu-id="722f7-106">Term</span></span>|<span data-ttu-id="722f7-107">定义</span><span class="sxs-lookup"><span data-stu-id="722f7-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="722f7-108">必需。</span><span class="sxs-lookup"><span data-stu-id="722f7-108">Required.</span></span> <span data-ttu-id="722f7-109">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="722f7-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="722f7-110">必需。</span><span class="sxs-lookup"><span data-stu-id="722f7-110">Required.</span></span> <span data-ttu-id="722f7-111">任何数值表达式。</span><span class="sxs-lookup"><span data-stu-id="722f7-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="722f7-112">结果</span><span class="sxs-lookup"><span data-stu-id="722f7-112">Result</span></span>  
 <span data-ttu-id="722f7-113">结果是和的乘积 `number1` `number2` 。</span><span class="sxs-lookup"><span data-stu-id="722f7-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="722f7-114">支持的类型</span><span class="sxs-lookup"><span data-stu-id="722f7-114">Supported Types</span></span>  
 <span data-ttu-id="722f7-115">所有数值类型，包括无符号和浮点类型和 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="722f7-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="722f7-116">备注</span><span class="sxs-lookup"><span data-stu-id="722f7-116">Remarks</span></span>  
 <span data-ttu-id="722f7-117">结果的数据类型取决于操作数的类型。</span><span class="sxs-lookup"><span data-stu-id="722f7-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="722f7-118">下表显示了如何确定结果的数据类型。</span><span class="sxs-lookup"><span data-stu-id="722f7-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="722f7-119">操作数数据类型</span><span class="sxs-lookup"><span data-stu-id="722f7-119">Operand data types</span></span>|<span data-ttu-id="722f7-120">Result 数据类型</span><span class="sxs-lookup"><span data-stu-id="722f7-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="722f7-121">这两个表达式均为整型数据类型（[SByte](../data-types/sbyte-data-type.md)、 [Byte](../data-types/byte-data-type.md)、 [Short](../data-types/short-data-type.md)、 [UShort](../data-types/ushort-data-type.md)、 [Integer](../data-types/integer-data-type.md)、 [UInteger](../data-types/uinteger-data-type.md)、 [Long](../data-types/long-data-type.md)、 [ULong](../data-types/ulong-data-type.md)）</span><span class="sxs-lookup"><span data-stu-id="722f7-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="722f7-122">适用于和的数据类型的数值数据类型 `number1` `number2` 。</span><span class="sxs-lookup"><span data-stu-id="722f7-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="722f7-123">请参阅[运算符结果的数据类型](data-types-of-operator-results.md)中的 "整数算法" 表。</span><span class="sxs-lookup"><span data-stu-id="722f7-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="722f7-124">两个表达式都是[小数](../data-types/decimal-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="722f7-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="722f7-125">这两个表达式都是[单](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="722f7-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="722f7-126">这两个表达式都是浮点数据类型（ `Single` 或[Double](../data-types/double-data-type.md)），但不能同时使用这两种类型 `Single` （注意不是 `Decimal` 浮点数据类型）</span><span class="sxs-lookup"><span data-stu-id="722f7-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="722f7-127">如果表达式的计算结果不为[空](../nothing.md)，则将其视为零。</span><span class="sxs-lookup"><span data-stu-id="722f7-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="722f7-128">重载</span><span class="sxs-lookup"><span data-stu-id="722f7-128">Overloading</span></span>  
 <span data-ttu-id="722f7-129">`*`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="722f7-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="722f7-130">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="722f7-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="722f7-131">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="722f7-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="722f7-132">示例</span><span class="sxs-lookup"><span data-stu-id="722f7-132">Example</span></span>  
 <span data-ttu-id="722f7-133">此示例使用 `*` 运算符将两个数字相乘。</span><span class="sxs-lookup"><span data-stu-id="722f7-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="722f7-134">结果就是两个操作数的乘积。</span><span class="sxs-lookup"><span data-stu-id="722f7-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="722f7-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="722f7-135">See also</span></span>

- [<span data-ttu-id="722f7-136">\* = 运算符</span><span class="sxs-lookup"><span data-stu-id="722f7-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="722f7-137">算术运算符</span><span class="sxs-lookup"><span data-stu-id="722f7-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="722f7-138">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="722f7-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="722f7-139">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="722f7-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="722f7-140">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="722f7-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
