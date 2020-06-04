---
title: Single 数据类型
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: ecb0f5f6416a2dd4ddd6888cb80ed3ac11ee58df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415526"
---
# <a name="single-data-type-visual-basic"></a><span data-ttu-id="f0b2d-102">Single 数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0b2d-102">Single Data Type (Visual Basic)</span></span>

<span data-ttu-id="f0b2d-103">为负值，保留已签名的 IEEE 32 位（4字节）单精度浮点数，介于-3.4028235 E + 38 到-1.401298 E-45 之间，对于正值，为正值，从 1.401298 E-45 到 3.4028235 E + 38。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-103">Holds signed IEEE 32-bit (4-byte) single-precision floating-point numbers ranging in value from -3.4028235E+38 through -1.401298E-45 for negative values and from 1.401298E-45 through 3.4028235E+38 for positive values.</span></span> <span data-ttu-id="f0b2d-104">单精度数字存储实数的近似值。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-104">Single-precision numbers store an approximation of a real number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0b2d-105">备注</span><span class="sxs-lookup"><span data-stu-id="f0b2d-105">Remarks</span></span>  

 <span data-ttu-id="f0b2d-106">使用 `Single` 数据类型可包含不需要的完整数据宽度的浮点值 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-106">Use the `Single` data type to contain floating-point values that do not require the full data width of `Double`.</span></span> <span data-ttu-id="f0b2d-107">在某些情况下，公共语言运行时可以将变量紧密地打包在 `Single` 一起，并节省内存消耗。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-107">In some cases the common language runtime might be able to pack your `Single` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="f0b2d-108">`Single` 的默认值为 0。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-108">The default value of `Single` is 0.</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="f0b2d-109">编程提示</span><span class="sxs-lookup"><span data-stu-id="f0b2d-109">Programming Tips</span></span>  
  
- <span data-ttu-id="f0b2d-110">**Precision.**</span><span class="sxs-lookup"><span data-stu-id="f0b2d-110">**Precision.**</span></span> <span data-ttu-id="f0b2d-111">使用浮点数时，请记住，它们在内存中不一定有精确的表示形式。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-111">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="f0b2d-112">这可能会导致某些操作产生意外结果，如值比较和 `Mod` 运算符。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-112">This could lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="f0b2d-113">有关详细信息，请参阅[数据类型疑难解答](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-113">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
- <span data-ttu-id="f0b2d-114">**扩大.**</span><span class="sxs-lookup"><span data-stu-id="f0b2d-114">**Widening.**</span></span> <span data-ttu-id="f0b2d-115">`Single`数据类型扩大到 `Double` 。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-115">The `Single` data type widens to `Double`.</span></span> <span data-ttu-id="f0b2d-116">这意味着你可以转换 `Single` 为， `Double` 而不会遇到 <xref:System.OverflowException?displayProperty=nameWithType> 错误。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-116">This means you can convert `Single` to `Double` without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="f0b2d-117">**尾随零。**</span><span class="sxs-lookup"><span data-stu-id="f0b2d-117">**Trailing Zeros.**</span></span> <span data-ttu-id="f0b2d-118">浮点数据类型不包含尾随0字符的任何内部表示形式。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-118">The floating-point data types do not have any internal representation of trailing 0 characters.</span></span> <span data-ttu-id="f0b2d-119">例如，它们不区分4.2000 和4.2。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-119">For example, they do not distinguish between 4.2000 and 4.2.</span></span> <span data-ttu-id="f0b2d-120">因此，在显示或打印浮点值时，不会出现尾随0字符。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-120">Consequently, trailing 0 characters do not appear when you display or print floating-point values.</span></span>  
  
- <span data-ttu-id="f0b2d-121">**键入字符。**</span><span class="sxs-lookup"><span data-stu-id="f0b2d-121">**Type Characters.**</span></span> <span data-ttu-id="f0b2d-122">将文本类型字符 `F` 追加到文本会将其强制转换为 `Single` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-122">Appending the literal type character `F` to a literal forces it to the `Single` data type.</span></span> <span data-ttu-id="f0b2d-123">将标识符类型字符 `!` 追加到任何标识符会将其强制转换为 `Single`。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-123">Appending the identifier type character `!` to any identifier forces it to `Single`.</span></span>  
  
- <span data-ttu-id="f0b2d-124">**Framework 类型。**</span><span class="sxs-lookup"><span data-stu-id="f0b2d-124">**Framework Type.**</span></span> <span data-ttu-id="f0b2d-125">.NET Framework 中的对应类型是 <xref:System.Single?displayProperty=nameWithType> 结构。</span><span class="sxs-lookup"><span data-stu-id="f0b2d-125">The corresponding type in the .NET Framework is the <xref:System.Single?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b2d-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f0b2d-126">See also</span></span>

- <xref:System.Single?displayProperty=nameWithType>
- [<span data-ttu-id="f0b2d-127">数据类型</span><span class="sxs-lookup"><span data-stu-id="f0b2d-127">Data Types</span></span>](index.md)
- [<span data-ttu-id="f0b2d-128">Decimal 数据类型</span><span class="sxs-lookup"><span data-stu-id="f0b2d-128">Decimal Data Type</span></span>](decimal-data-type.md)
- [<span data-ttu-id="f0b2d-129">Double 数据类型</span><span class="sxs-lookup"><span data-stu-id="f0b2d-129">Double Data Type</span></span>](double-data-type.md)
- [<span data-ttu-id="f0b2d-130">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="f0b2d-130">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="f0b2d-131">转换摘要</span><span class="sxs-lookup"><span data-stu-id="f0b2d-131">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="f0b2d-132">有效使用数据类型</span><span class="sxs-lookup"><span data-stu-id="f0b2d-132">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="f0b2d-133">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="f0b2d-133">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
