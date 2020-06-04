---
title: << 运算符
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 1128b32a739e7dbf3893dcd19b37247cd4643c85
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370630"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="535f3-102">\<\<运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="535f3-102">\<\< Operator (Visual Basic)</span></span>
<span data-ttu-id="535f3-103">对位模式执行算术左移位运算。</span><span class="sxs-lookup"><span data-stu-id="535f3-103">Performs an arithmetic left shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="535f3-104">语法</span><span class="sxs-lookup"><span data-stu-id="535f3-104">Syntax</span></span>  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a><span data-ttu-id="535f3-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="535f3-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="535f3-106">必需。</span><span class="sxs-lookup"><span data-stu-id="535f3-106">Required.</span></span> <span data-ttu-id="535f3-107">整数数值。</span><span class="sxs-lookup"><span data-stu-id="535f3-107">Integral numeric value.</span></span> <span data-ttu-id="535f3-108">对该位模式进行移位的结果。</span><span class="sxs-lookup"><span data-stu-id="535f3-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="535f3-109">数据类型与 `pattern` 的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="535f3-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="535f3-110">必需。</span><span class="sxs-lookup"><span data-stu-id="535f3-110">Required.</span></span> <span data-ttu-id="535f3-111">整型数值表达式。</span><span class="sxs-lookup"><span data-stu-id="535f3-111">Integral numeric expression.</span></span> <span data-ttu-id="535f3-112">要进行移位的位模式。</span><span class="sxs-lookup"><span data-stu-id="535f3-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="535f3-113">数据类型必须为整型（`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`）。</span><span class="sxs-lookup"><span data-stu-id="535f3-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="535f3-114">必需。</span><span class="sxs-lookup"><span data-stu-id="535f3-114">Required.</span></span> <span data-ttu-id="535f3-115">数值表达式。</span><span class="sxs-lookup"><span data-stu-id="535f3-115">Numeric expression.</span></span> <span data-ttu-id="535f3-116">要将该位模式移位的位数。</span><span class="sxs-lookup"><span data-stu-id="535f3-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="535f3-117">数据类型必须为 `Integer` 或扩展到 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="535f3-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="535f3-118">备注</span><span class="sxs-lookup"><span data-stu-id="535f3-118">Remarks</span></span>  
 <span data-ttu-id="535f3-119">算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。</span><span class="sxs-lookup"><span data-stu-id="535f3-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="535f3-120">在算术左移位中，将丢弃超出结果数据类型范围的位，并将在右侧空出的位位置设置为零。</span><span class="sxs-lookup"><span data-stu-id="535f3-120">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
 <span data-ttu-id="535f3-121">若要防止移位比结果可以容纳的位数多，Visual Basic 用与的 `amount` 数据类型相对应的大小掩码来屏蔽的值 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="535f3-121">To prevent a shift by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask that corresponds to the data type of `pattern`.</span></span> <span data-ttu-id="535f3-122">这些值的二进制和均用于移位量。</span><span class="sxs-lookup"><span data-stu-id="535f3-122">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="535f3-123">大小掩码如下：</span><span class="sxs-lookup"><span data-stu-id="535f3-123">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="535f3-124">数据类型`pattern`</span><span class="sxs-lookup"><span data-stu-id="535f3-124">Data type of `pattern`</span></span>|<span data-ttu-id="535f3-125">大小掩码（十进制）</span><span class="sxs-lookup"><span data-stu-id="535f3-125">Size mask (decimal)</span></span>|<span data-ttu-id="535f3-126">大小掩码（十六进制）</span><span class="sxs-lookup"><span data-stu-id="535f3-126">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="535f3-127">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="535f3-127">`SByte`, `Byte`</span></span>|<span data-ttu-id="535f3-128">7</span><span class="sxs-lookup"><span data-stu-id="535f3-128">7</span></span>|<span data-ttu-id="535f3-129">&H00000007</span><span class="sxs-lookup"><span data-stu-id="535f3-129">&H00000007</span></span>|  
|<span data-ttu-id="535f3-130">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="535f3-130">`Short`, `UShort`</span></span>|<span data-ttu-id="535f3-131">15</span><span class="sxs-lookup"><span data-stu-id="535f3-131">15</span></span>|<span data-ttu-id="535f3-132">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="535f3-132">&H0000000F</span></span>|  
|<span data-ttu-id="535f3-133">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="535f3-133">`Integer`, `UInteger`</span></span>|<span data-ttu-id="535f3-134">31</span><span class="sxs-lookup"><span data-stu-id="535f3-134">31</span></span>|<span data-ttu-id="535f3-135">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="535f3-135">&H0000001F</span></span>|  
|<span data-ttu-id="535f3-136">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="535f3-136">`Long`, `ULong`</span></span>|<span data-ttu-id="535f3-137">63</span><span class="sxs-lookup"><span data-stu-id="535f3-137">63</span></span>|<span data-ttu-id="535f3-138">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="535f3-138">&H0000003F</span></span>|  
  
 <span data-ttu-id="535f3-139">如果 `amount` 为零，则的值与的 `result` 值相同 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="535f3-139">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="535f3-140">如果 `amount` 为负，则将其视为无符号值并使用适当的大小掩码屏蔽。</span><span class="sxs-lookup"><span data-stu-id="535f3-140">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="535f3-141">算术移位从不产生溢出异常。</span><span class="sxs-lookup"><span data-stu-id="535f3-141">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="535f3-142">`<<`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="535f3-142">The `<<` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="535f3-143">如果代码对这样的类或结构使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="535f3-143">If your code uses this operator on such a class or structure, be sure that you understand its redefined behavior.</span></span> <span data-ttu-id="535f3-144">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="535f3-144">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="535f3-145">示例</span><span class="sxs-lookup"><span data-stu-id="535f3-145">Example</span></span>  
 <span data-ttu-id="535f3-146">下面的示例使用 `<<` 运算符对整数值执行算术左移位。</span><span class="sxs-lookup"><span data-stu-id="535f3-146">The following example uses the `<<` operator to perform arithmetic left shifts on integral values.</span></span> <span data-ttu-id="535f3-147">结果始终与要移动的表达式的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="535f3-147">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 <span data-ttu-id="535f3-148">上述示例的结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="535f3-148">The results of the previous example are as follows:</span></span>  
  
- <span data-ttu-id="535f3-149">`result1`为192（0000 0000 1100 0000）。</span><span class="sxs-lookup"><span data-stu-id="535f3-149">`result1` is 192 (0000 0000 1100 0000).</span></span>  
  
- <span data-ttu-id="535f3-150">`result2`为3072（0000 1100 0000 0000）。</span><span class="sxs-lookup"><span data-stu-id="535f3-150">`result2` is 3072 (0000 1100 0000 0000).</span></span>  
  
- <span data-ttu-id="535f3-151">`result3`为-32768 （1000 0000 0000 0000）。</span><span class="sxs-lookup"><span data-stu-id="535f3-151">`result3` is -32768 (1000 0000 0000 0000).</span></span>  
  
- <span data-ttu-id="535f3-152">`result4`为384（0000 0001 1000 0000）。</span><span class="sxs-lookup"><span data-stu-id="535f3-152">`result4` is 384 (0000 0001 1000 0000).</span></span>  
  
- <span data-ttu-id="535f3-153">`result5`为0（向左移动15个位置）。</span><span class="sxs-lookup"><span data-stu-id="535f3-153">`result5` is 0 (shifted 15 places to the left).</span></span>  
  
 <span data-ttu-id="535f3-154">的移位量 `result4` 计算为17和15，这等于1。</span><span class="sxs-lookup"><span data-stu-id="535f3-154">The shift amount for `result4` is calculated as 17 AND 15, which equals 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="535f3-155">另请参阅</span><span class="sxs-lookup"><span data-stu-id="535f3-155">See also</span></span>

- [<span data-ttu-id="535f3-156">移位运算符</span><span class="sxs-lookup"><span data-stu-id="535f3-156">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="535f3-157">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="535f3-157">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="535f3-158"><<= 运算符</span><span class="sxs-lookup"><span data-stu-id="535f3-158"><<= Operator</span></span>](left-shift-assignment-operator.md)
- [<span data-ttu-id="535f3-159">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="535f3-159">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="535f3-160">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="535f3-160">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="535f3-161">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="535f3-161">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
