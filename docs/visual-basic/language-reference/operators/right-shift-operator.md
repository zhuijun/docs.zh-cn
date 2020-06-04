---
title: '>> 运算符'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 10b07da22b8b43d6a966fa7c334ac6a0ef4b430d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406361"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="a7ef9-102">>> 运算符（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a7ef9-102">>> Operator (Visual Basic)</span></span>
<span data-ttu-id="a7ef9-103">对位模式执行算术右移位运算。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-103">Performs an arithmetic right shift on a bit pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ef9-104">语法</span><span class="sxs-lookup"><span data-stu-id="a7ef9-104">Syntax</span></span>  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a><span data-ttu-id="a7ef9-105">组成部分</span><span class="sxs-lookup"><span data-stu-id="a7ef9-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="a7ef9-106">必需。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-106">Required.</span></span> <span data-ttu-id="a7ef9-107">整数数值。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-107">Integral numeric value.</span></span> <span data-ttu-id="a7ef9-108">对该位模式进行移位的结果。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-108">The result of shifting the bit pattern.</span></span> <span data-ttu-id="a7ef9-109">数据类型与 `pattern` 的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-109">The data type is the same as that of `pattern`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="a7ef9-110">必需。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-110">Required.</span></span> <span data-ttu-id="a7ef9-111">整型数值表达式。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-111">Integral numeric expression.</span></span> <span data-ttu-id="a7ef9-112">要进行移位的位模式。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-112">The bit pattern to be shifted.</span></span> <span data-ttu-id="a7ef9-113">数据类型必须为整型（`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long` 或 `ULong`）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-113">The data type must be an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="a7ef9-114">必需。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-114">Required.</span></span> <span data-ttu-id="a7ef9-115">数值表达式。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-115">Numeric expression.</span></span> <span data-ttu-id="a7ef9-116">要将该位模式移位的位数。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-116">The number of bits to shift the bit pattern.</span></span> <span data-ttu-id="a7ef9-117">数据类型必须为 `Integer` 或扩展到 `Integer`。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-117">The data type must be `Integer` or widen to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7ef9-118">备注</span><span class="sxs-lookup"><span data-stu-id="a7ef9-118">Remarks</span></span>  
 <span data-ttu-id="a7ef9-119">算术移位不是循环的，这意味着，不会在另一端重新引入结果的末尾以外的位。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-119">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="a7ef9-120">在算术右移位中，将丢弃超出最右位位置的位，并将最左侧的（符号）位传播到左端空出的位位置。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-120">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost (sign) bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="a7ef9-121">这意味着，如果 `pattern` 具有负值，空出位置将设置为 1; 否则，将设置为零。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-121">This means that if `pattern` has a negative value, the vacated positions are set to one; otherwise they are set to zero.</span></span>  
  
 <span data-ttu-id="a7ef9-122">请注意，数据类型 `Byte` 、 `UShort` 、 `UInteger` 和 `ULong` 都是无符号的，因此没有要传播的符号位。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-122">Note that the data types `Byte`, `UShort`, `UInteger`, and `ULong` are unsigned, so there is no sign bit to propagate.</span></span> <span data-ttu-id="a7ef9-123">如果 `pattern` 为任何无符号类型，空出的位置始终设置为零。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-123">If `pattern` is of any unsigned type, the vacated positions are always set to zero.</span></span>  
  
 <span data-ttu-id="a7ef9-124">若要防止移位比结果可容纳的位数多，Visual Basic `amount` 用与的数据类型相对应的大小掩码来屏蔽的值 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-124">To prevent shifting by more bits than the result can hold, Visual Basic masks the value of `amount` with a size mask corresponding to the data type of `pattern`.</span></span> <span data-ttu-id="a7ef9-125">这些值的二进制和均用于移位量。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-125">The binary AND of these values is used for the shift amount.</span></span> <span data-ttu-id="a7ef9-126">大小掩码如下：</span><span class="sxs-lookup"><span data-stu-id="a7ef9-126">The size masks are as follows:</span></span>  
  
|<span data-ttu-id="a7ef9-127">数据类型`pattern`</span><span class="sxs-lookup"><span data-stu-id="a7ef9-127">Data type of `pattern`</span></span>|<span data-ttu-id="a7ef9-128">大小掩码（十进制）</span><span class="sxs-lookup"><span data-stu-id="a7ef9-128">Size mask (decimal)</span></span>|<span data-ttu-id="a7ef9-129">大小掩码（十六进制）</span><span class="sxs-lookup"><span data-stu-id="a7ef9-129">Size mask (hexadecimal)</span></span>|  
|----------------------------|---------------------------|-------------------------------|  
|<span data-ttu-id="a7ef9-130">`SByte`, `Byte`</span><span class="sxs-lookup"><span data-stu-id="a7ef9-130">`SByte`, `Byte`</span></span>|<span data-ttu-id="a7ef9-131">7</span><span class="sxs-lookup"><span data-stu-id="a7ef9-131">7</span></span>|<span data-ttu-id="a7ef9-132">&H00000007</span><span class="sxs-lookup"><span data-stu-id="a7ef9-132">&H00000007</span></span>|  
|<span data-ttu-id="a7ef9-133">`Short`, `UShort`</span><span class="sxs-lookup"><span data-stu-id="a7ef9-133">`Short`, `UShort`</span></span>|<span data-ttu-id="a7ef9-134">15</span><span class="sxs-lookup"><span data-stu-id="a7ef9-134">15</span></span>|<span data-ttu-id="a7ef9-135">&H0000000F</span><span class="sxs-lookup"><span data-stu-id="a7ef9-135">&H0000000F</span></span>|  
|<span data-ttu-id="a7ef9-136">`Integer`, `UInteger`</span><span class="sxs-lookup"><span data-stu-id="a7ef9-136">`Integer`, `UInteger`</span></span>|<span data-ttu-id="a7ef9-137">31</span><span class="sxs-lookup"><span data-stu-id="a7ef9-137">31</span></span>|<span data-ttu-id="a7ef9-138">&H0000001F</span><span class="sxs-lookup"><span data-stu-id="a7ef9-138">&H0000001F</span></span>|  
|<span data-ttu-id="a7ef9-139">`Long`, `ULong`</span><span class="sxs-lookup"><span data-stu-id="a7ef9-139">`Long`, `ULong`</span></span>|<span data-ttu-id="a7ef9-140">63</span><span class="sxs-lookup"><span data-stu-id="a7ef9-140">63</span></span>|<span data-ttu-id="a7ef9-141">&H0000003F</span><span class="sxs-lookup"><span data-stu-id="a7ef9-141">&H0000003F</span></span>|  
  
 <span data-ttu-id="a7ef9-142">如果 `amount` 为零，则的值与的 `result` 值相同 `pattern` 。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-142">If `amount` is zero, the value of `result` is identical to the value of `pattern`.</span></span> <span data-ttu-id="a7ef9-143">如果 `amount` 为负，则将其视为无符号值并使用适当的大小掩码屏蔽。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-143">If `amount` is negative, it is taken as an unsigned value and masked with the appropriate size mask.</span></span>  
  
 <span data-ttu-id="a7ef9-144">算术移位从不产生溢出异常。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-144">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a7ef9-145">重载</span><span class="sxs-lookup"><span data-stu-id="a7ef9-145">Overloading</span></span>  
 <span data-ttu-id="a7ef9-146">`>>`运算符可以*重载*，这意味着当操作数具有该类或结构的类型时，该类或结构可以重新定义其行为。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-146">The `>>` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a7ef9-147">如果你的代码在该类或结构上使用此运算符，请确保了解其重新定义的行为。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-147">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="a7ef9-148">有关详细信息，请参阅 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-148">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7ef9-149">示例</span><span class="sxs-lookup"><span data-stu-id="a7ef9-149">Example</span></span>  
 <span data-ttu-id="a7ef9-150">下面的示例使用 `>>` 运算符对整数值执行算术右移位运算。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-150">The following example uses the `>>` operator to perform arithmetic right shifts on integral values.</span></span> <span data-ttu-id="a7ef9-151">结果始终与要移动的表达式的数据类型相同。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-151">The result always has the same data type as that of the expression being shifted.</span></span>  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 <span data-ttu-id="a7ef9-152">上述示例的结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7ef9-152">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="a7ef9-153">`result1`为2560（0000 1010 0000 0000）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-153">`result1` is 2560 (0000 1010 0000 0000).</span></span>  
  
- <span data-ttu-id="a7ef9-154">`result2`为160（0000 0000 1010 0000）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-154">`result2` is 160 (0000 0000 1010 0000).</span></span>  
  
- <span data-ttu-id="a7ef9-155">`result3`为2（0000 0000 0000 0010）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-155">`result3` is 2 (0000 0000 0000 0010).</span></span>  
  
- <span data-ttu-id="a7ef9-156">`result4`为640（0000 0010 1000 0000）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-156">`result4` is 640 (0000 0010 1000 0000).</span></span>  
  
- <span data-ttu-id="a7ef9-157">`result5`为0（向右移动15个位数）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-157">`result5` is 0 (shifted 15 places to the right).</span></span>  
  
 <span data-ttu-id="a7ef9-158">的移位量 `result4` 计算为18和15，这等于2。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-158">The shift amount for `result4` is calculated as 18 AND 15, which equals 2.</span></span>  
  
 <span data-ttu-id="a7ef9-159">下面的示例演示如何对负值进行算术移位运算。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-159">The following example shows arithmetic shifts on a negative value.</span></span>  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 <span data-ttu-id="a7ef9-160">上述示例的结果如下所示：</span><span class="sxs-lookup"><span data-stu-id="a7ef9-160">The results of the preceding example are as follows:</span></span>  
  
- <span data-ttu-id="a7ef9-161">`negresult1`为-512 （1111 1110 0000 0000）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-161">`negresult1` is -512 (1111 1110 0000 0000).</span></span>  
  
- <span data-ttu-id="a7ef9-162">`negresult2`为-1 （对符号位进行传播）。</span><span class="sxs-lookup"><span data-stu-id="a7ef9-162">`negresult2` is -1 (the sign bit is propagated).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ef9-163">另请参阅</span><span class="sxs-lookup"><span data-stu-id="a7ef9-163">See also</span></span>

- [<span data-ttu-id="a7ef9-164">移位运算符</span><span class="sxs-lookup"><span data-stu-id="a7ef9-164">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="a7ef9-165">赋值运算符</span><span class="sxs-lookup"><span data-stu-id="a7ef9-165">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="a7ef9-166">>>= 运算符</span><span class="sxs-lookup"><span data-stu-id="a7ef9-166">>>= Operator</span></span>](right-shift-assignment-operator.md)
- [<span data-ttu-id="a7ef9-167">Visual Basic 中的运算符优先级</span><span class="sxs-lookup"><span data-stu-id="a7ef9-167">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="a7ef9-168">按功能列出的运算符</span><span class="sxs-lookup"><span data-stu-id="a7ef9-168">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="a7ef9-169">算术运算符 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7ef9-169">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
