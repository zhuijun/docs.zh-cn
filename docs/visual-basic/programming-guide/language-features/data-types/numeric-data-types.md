---
title: 数值数据类型
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 317c0862953e7bb866faa4712d42dfd5995ecf35
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91086226"
---
# <a name="numeric-data-types-visual-basic"></a><span data-ttu-id="2a278-102">数值型数据类型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a278-102">Numeric Data Types (Visual Basic)</span></span>

<span data-ttu-id="2a278-103">Visual Basic 提供了几种 *数值数据类型* 来处理各种表示形式的数字。</span><span class="sxs-lookup"><span data-stu-id="2a278-103">Visual Basic supplies several *numeric data types* for handling numbers in various representations.</span></span> <span data-ttu-id="2a278-104">*整数* 类型仅表示 (正值、负值和零) 的整数 *，而非整数类型表示* 同时包含整数部分和小数部分的数字。</span><span class="sxs-lookup"><span data-stu-id="2a278-104">*Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="2a278-105">有关显示 Visual Basic 数据类型的并行比较的表，请参阅 [数据类型](../../../language-reference/data-types/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2a278-105">For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../language-reference/data-types/index.md).</span></span>  
  
## <a name="integral-numeric-types"></a><span data-ttu-id="2a278-106">整数数值类型</span><span class="sxs-lookup"><span data-stu-id="2a278-106">Integral Numeric Types</span></span>  

 <span data-ttu-id="2a278-107">*整数数据类型* 是指仅表示没有小数部分的数字的数据类型。</span><span class="sxs-lookup"><span data-stu-id="2a278-107">*Integral data types* are those that represent only numbers without fractional parts.</span></span>  
  
 <span data-ttu-id="2a278-108">*带符号*的整型数据类型为[SByte 数据类型](../../../language-reference/data-types/sbyte-data-type.md) (8 位) ， [Short 数据类型](../../../language-reference/data-types/short-data-type.md) (16 位) ， [Integer 数据类型](../../../language-reference/data-types/integer-data-type.md) (32 位) ， [Long 数据类型](../../../language-reference/data-types/long-data-type.md) (64-位) 。</span><span class="sxs-lookup"><span data-stu-id="2a278-108">The *signed* integral data types are [SByte Data Type](../../../language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../language-reference/data-types/long-data-type.md) (64-bit).</span></span> <span data-ttu-id="2a278-109">如果变量始终存储整数而不是小数，则将其声明为这些类型之一。</span><span class="sxs-lookup"><span data-stu-id="2a278-109">If a variable always stores integers rather than fractional numbers, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="2a278-110">*无符号*整型类型为[Byte 数据类型](../../../language-reference/data-types/byte-data-type.md) (8 位) ， [UShort 数据类型](../../../language-reference/data-types/ushort-data-type.md) (16 位) ， [UInteger 数据类型](../../../language-reference/data-types/uinteger-data-type.md) (32 位) ，以及[ULong 数据类型](../../../language-reference/data-types/ulong-data-type.md) (64-位) 。</span><span class="sxs-lookup"><span data-stu-id="2a278-110">The *unsigned* integral types are [Byte Data Type](../../../language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../language-reference/data-types/ulong-data-type.md) (64-bit).</span></span> <span data-ttu-id="2a278-111">如果变量包含二进制数据或未知性质的数据，则将其声明为这些类型之一。</span><span class="sxs-lookup"><span data-stu-id="2a278-111">If a variable contains binary data, or data of unknown nature, declare it as one of these types.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="2a278-112">性能</span><span class="sxs-lookup"><span data-stu-id="2a278-112">Performance</span></span>  

 <span data-ttu-id="2a278-113">与其他数据类型相比，算术运算比整型类型更快。</span><span class="sxs-lookup"><span data-stu-id="2a278-113">Arithmetic operations are faster with integral types than with other data types.</span></span> <span data-ttu-id="2a278-114">与 `Integer` Visual Basic 中的和类型相比，它们速度最快 `UInteger` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-114">They are fastest with the `Integer` and `UInteger` types in Visual Basic.</span></span>  
  
### <a name="large-integers"></a><span data-ttu-id="2a278-115">大整数</span><span class="sxs-lookup"><span data-stu-id="2a278-115">Large Integers</span></span>  

 <span data-ttu-id="2a278-116">如果需要保留大于 `Integer` 数据类型可以保留的整数，则可以改用 `Long` 数据类型。</span><span class="sxs-lookup"><span data-stu-id="2a278-116">If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead.</span></span> <span data-ttu-id="2a278-117">`Long` 变量可以包含从-9223372036854775808 到9223372036854775807的数字。</span><span class="sxs-lookup"><span data-stu-id="2a278-117">`Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807.</span></span> <span data-ttu-id="2a278-118">与的操作相比，其运行 `Long` 速度稍慢 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-118">Operations with `Long` are slightly slower than with `Integer`.</span></span>  
  
 <span data-ttu-id="2a278-119">如果需要更大的值，则可以使用 [Decimal 数据类型](../../../language-reference/data-types/decimal-data-type.md)。</span><span class="sxs-lookup"><span data-stu-id="2a278-119">If you need even larger values, you can use the [Decimal Data Type](../../../language-reference/data-types/decimal-data-type.md).</span></span> <span data-ttu-id="2a278-120">`Decimal`如果不使用任何小数位数，则可以在变量中保存从-79228162514264337593543950335 到79228162514264337593543950335的数字。</span><span class="sxs-lookup"><span data-stu-id="2a278-120">You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places.</span></span> <span data-ttu-id="2a278-121">但是，与 `Decimal` 任何其他数值数据类型相比，数字运算的速度要慢得多。</span><span class="sxs-lookup"><span data-stu-id="2a278-121">However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.</span></span>  
  
### <a name="small-integers"></a><span data-ttu-id="2a278-122">小整数</span><span class="sxs-lookup"><span data-stu-id="2a278-122">Small Integers</span></span>  

 <span data-ttu-id="2a278-123">如果不需要数据类型的完整范围 `Integer` ，可以使用 `Short` 数据类型，该数据类型可以包含从-32768 到32767的整数。</span><span class="sxs-lookup"><span data-stu-id="2a278-123">If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767.</span></span> <span data-ttu-id="2a278-124">对于最小整数范围， `SByte` 数据类型保存从-128 到127的整数。</span><span class="sxs-lookup"><span data-stu-id="2a278-124">For the smallest integer range, the `SByte` data type holds integers from -128 through 127.</span></span> <span data-ttu-id="2a278-125">如果有大量包含小整数的变量，则公共语言运行时有时可以 `Short` `SByte` 更有效地存储和变量，并节省内存消耗。</span><span class="sxs-lookup"><span data-stu-id="2a278-125">If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption.</span></span> <span data-ttu-id="2a278-126">不过，和的 `Short` 操作 `SByte` 在一定程度上比更慢 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-126">However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.</span></span>  
  
### <a name="unsigned-integers"></a><span data-ttu-id="2a278-127">无符号整数</span><span class="sxs-lookup"><span data-stu-id="2a278-127">Unsigned Integers</span></span>  

 <span data-ttu-id="2a278-128">如果你知道你的变量从不需要保存负数，则可以使用*无符号类型* `Byte` 、 `UShort` 、 `UInteger` 和 `ULong` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-128">If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`.</span></span> <span data-ttu-id="2a278-129">这些数据类型中的每个数据类型都可以保存两倍于其对应的带符号类型 (`SByte` 、 `Short` 、 `Integer` 和 `Long`) 。</span><span class="sxs-lookup"><span data-stu-id="2a278-129">Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`).</span></span> <span data-ttu-id="2a278-130">就性能而言，每个未签名的类型与其对应的已签名类型的有效性完全相同。</span><span class="sxs-lookup"><span data-stu-id="2a278-130">In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type.</span></span> <span data-ttu-id="2a278-131">特别是， `UInteger` 共享的 `Integer` 区别是所有基本数值数据类型都是最有效的。</span><span class="sxs-lookup"><span data-stu-id="2a278-131">In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.</span></span>  
  
## <a name="nonintegral-numeric-types"></a><span data-ttu-id="2a278-132">非整型数值类型</span><span class="sxs-lookup"><span data-stu-id="2a278-132">Nonintegral Numeric Types</span></span>  

 <span data-ttu-id="2a278-133">非*整型数据类型*是指具有整数部分和小数部分的数字。</span><span class="sxs-lookup"><span data-stu-id="2a278-133">*Nonintegral data types* are those that represent numbers with both integer and fractional parts.</span></span>  
  
 <span data-ttu-id="2a278-134">非整型数值数据类型为 `Decimal` (128 位固定点) ， [单数据类型](../../../language-reference/data-types/single-data-type.md) (32 位浮点) ， [双精度数据类型](../../../language-reference/data-types/double-data-type.md) (64 位浮点) 。</span><span class="sxs-lookup"><span data-stu-id="2a278-134">The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../language-reference/data-types/double-data-type.md) (64-bit floating point).</span></span> <span data-ttu-id="2a278-135">它们都是已签名的类型。</span><span class="sxs-lookup"><span data-stu-id="2a278-135">They are all signed types.</span></span> <span data-ttu-id="2a278-136">如果变量可以包含一个分数，则将其声明为这些类型之一。</span><span class="sxs-lookup"><span data-stu-id="2a278-136">If a variable can contain a fraction, declare it as one of these types.</span></span>  
  
 <span data-ttu-id="2a278-137">`Decimal` 不是浮点数据类型。</span><span class="sxs-lookup"><span data-stu-id="2a278-137">`Decimal` is not a floating-point data type.</span></span> <span data-ttu-id="2a278-138">`Decimal` 数字具有二进制整数值和整数比例因子，用于指定值的哪一部分是小数部分。</span><span class="sxs-lookup"><span data-stu-id="2a278-138">`Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.</span></span>  
  
 <span data-ttu-id="2a278-139">您可以使用 `Decimal` 变量作为 money 值。</span><span class="sxs-lookup"><span data-stu-id="2a278-139">You can use `Decimal` variables for money values.</span></span> <span data-ttu-id="2a278-140">优点是值的精度。</span><span class="sxs-lookup"><span data-stu-id="2a278-140">The advantage is the precision of the values.</span></span> <span data-ttu-id="2a278-141">`Double`数据类型的速度更快，需要的内存更少，但可能会产生舍入误差。</span><span class="sxs-lookup"><span data-stu-id="2a278-141">The `Double` data type is faster and requires less memory, but it is subject to rounding errors.</span></span> <span data-ttu-id="2a278-142">`Decimal`数据类型将完整准确性保留为28个小数位数。</span><span class="sxs-lookup"><span data-stu-id="2a278-142">The `Decimal` data type retains complete accuracy to 28 decimal places.</span></span>  
  
 <span data-ttu-id="2a278-143">浮点 (`Single` 和 `Double`) 数字的范围大于 `Decimal` 数字，但可能会受到舍入错误的限制。</span><span class="sxs-lookup"><span data-stu-id="2a278-143">Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors.</span></span> <span data-ttu-id="2a278-144">浮点类型支持的有效位数少于 `Decimal` ，但可表示更大的值。</span><span class="sxs-lookup"><span data-stu-id="2a278-144">Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.</span></span>  
  
 <span data-ttu-id="2a278-145">非整数数字值可以表示为 mmmEeee，其中 mmm 是有效位数) 的 (*尾数* ，而 eee 是 10) 幂的 *指数* (。</span><span class="sxs-lookup"><span data-stu-id="2a278-145">Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10).</span></span> <span data-ttu-id="2a278-146">非整数类型的最大正值是 7.9228162514264337593543950335 E + 28 for `Decimal` 、3.4028235 e + 38 for `Single` 和 1.79769313486231570 e + 308 （对于） `Double` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-146">The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.</span></span>  
  
### <a name="performance"></a><span data-ttu-id="2a278-147">性能</span><span class="sxs-lookup"><span data-stu-id="2a278-147">Performance</span></span>  

 <span data-ttu-id="2a278-148">`Double` 是最有效的小数数据类型，因为当前平台上的处理器以双精度执行浮点运算。</span><span class="sxs-lookup"><span data-stu-id="2a278-148">`Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="2a278-149">但是，与整数类型（例如）相比，具有的操作的 `Double` 速度并不像 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="2a278-149">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
### <a name="small-magnitudes"></a><span data-ttu-id="2a278-150">小型度</span><span class="sxs-lookup"><span data-stu-id="2a278-150">Small Magnitudes</span></span>  

 <span data-ttu-id="2a278-151">对于具有最小可能的最大度量值的数字 (最接近 0) ， `Double` 变量可以将数字保存为小的 4.94065645841246544 e-324 for 负值，并将 4.94065645841246544 e-324 用于正值。</span><span class="sxs-lookup"><span data-stu-id="2a278-151">For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.</span></span>  
  
### <a name="small-fractional-numbers"></a><span data-ttu-id="2a278-152">小小数值</span><span class="sxs-lookup"><span data-stu-id="2a278-152">Small Fractional Numbers</span></span>  

 <span data-ttu-id="2a278-153">如果不需要数据类型的完整范围 `Double` ，可以使用 `Single` 数据类型，该数据类型可以保存-3.4028235 e + 38 到 3.4028235 e + 38 之间的浮点数。</span><span class="sxs-lookup"><span data-stu-id="2a278-153">If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38.</span></span> <span data-ttu-id="2a278-154">对于负值，变量的最小度为 `Single` -1.401298 e-45; 对于正值，则为 1.401298 e-45。</span><span class="sxs-lookup"><span data-stu-id="2a278-154">The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values.</span></span> <span data-ttu-id="2a278-155">如果有大量包含较小浮点数的变量，则公共语言运行时有时可以 `Single` 更有效地存储变量，并节省内存消耗。</span><span class="sxs-lookup"><span data-stu-id="2a278-155">If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a278-156">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a278-156">See also</span></span>

- [<span data-ttu-id="2a278-157">基本数据类型</span><span class="sxs-lookup"><span data-stu-id="2a278-157">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="2a278-158">字符数据类型</span><span class="sxs-lookup"><span data-stu-id="2a278-158">Character Data Types</span></span>](character-data-types.md)
- [<span data-ttu-id="2a278-159">杂项数据类型</span><span class="sxs-lookup"><span data-stu-id="2a278-159">Miscellaneous Data Types</span></span>](miscellaneous-data-types.md)
- [<span data-ttu-id="2a278-160">数据类型疑难解答</span><span class="sxs-lookup"><span data-stu-id="2a278-160">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="2a278-161">如何：调用需要使用无符号类型的 Windows 函数</span><span class="sxs-lookup"><span data-stu-id="2a278-161">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
