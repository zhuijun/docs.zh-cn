---
title: Type Conversion Functions
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 5c0cfae01da02222d0827e81ec1ed35ce353ead1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415370"
---
# <a name="type-conversion-functions-visual-basic"></a><span data-ttu-id="f9532-102">类型转换函数 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f9532-102">Type Conversion Functions (Visual Basic)</span></span>

<span data-ttu-id="f9532-103">这些函数是内联编译的，这意味着转换代码是用于计算表达式的代码的一部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-103">These functions are compiled inline, meaning the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="f9532-104">有时不会调用过程来完成转换，从而提高性能。</span><span class="sxs-lookup"><span data-stu-id="f9532-104">Sometimes there is no call to a procedure to accomplish the conversion, which improves performance.</span></span> <span data-ttu-id="f9532-105">每个函数都将表达式强制转换为特定的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f9532-105">Each function coerces an expression to a specific data type.</span></span>

## <a name="syntax"></a><span data-ttu-id="f9532-106">语法</span><span class="sxs-lookup"><span data-stu-id="f9532-106">Syntax</span></span>

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a><span data-ttu-id="f9532-107">组成部分</span><span class="sxs-lookup"><span data-stu-id="f9532-107">Part</span></span>

`expression`  
<span data-ttu-id="f9532-108">必需。</span><span class="sxs-lookup"><span data-stu-id="f9532-108">Required.</span></span> <span data-ttu-id="f9532-109">源数据类型的任何表达式。</span><span class="sxs-lookup"><span data-stu-id="f9532-109">Any expression of the source data type.</span></span>

## <a name="return-value-data-type"></a><span data-ttu-id="f9532-110">返回值数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-110">Return Value Data Type</span></span>

<span data-ttu-id="f9532-111">函数名称确定它返回的值的数据类型，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="f9532-111">The function name determines the data type of the value it returns, as shown in the following table.</span></span>

|<span data-ttu-id="f9532-112">功能名称</span><span class="sxs-lookup"><span data-stu-id="f9532-112">Function name</span></span>|<span data-ttu-id="f9532-113">返回数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-113">Return data type</span></span>|<span data-ttu-id="f9532-114">参数的范围 `expression`</span><span class="sxs-lookup"><span data-stu-id="f9532-114">Range for `expression` argument</span></span>|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[<span data-ttu-id="f9532-115">布尔数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-115">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)|<span data-ttu-id="f9532-116">任何有效 `Char` 的或 `String` 数值表达式。</span><span class="sxs-lookup"><span data-stu-id="f9532-116">Any valid `Char` or `String` or numeric expression.</span></span>|
|`CByte`|[<span data-ttu-id="f9532-117">Byte 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-117">Byte Data Type</span></span>](../data-types/byte-data-type.md)|<span data-ttu-id="f9532-118"><xref:System.Byte.MinValue?displayProperty=nameWithType>（0）到 <xref:System.Byte.MaxValue?displayProperty=nameWithType> （255）（无符号）; 小数部分被舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-118"><xref:System.Byte.MinValue?displayProperty=nameWithType> (0) through <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-119">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到字节转换的性能 `CByte` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-119">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to byte conversion with the `CByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-120">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-120">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CChar`|[<span data-ttu-id="f9532-121">Char 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-121">Char Data Type</span></span>](../data-types/char-data-type.md)|<span data-ttu-id="f9532-122">任何有效的 `Char` 或 `String` 表达式; 只转换第一个字符 `String` ; 值可以是0到65535（无符号）。</span><span class="sxs-lookup"><span data-stu-id="f9532-122">Any valid `Char` or `String` expression; only first character of a `String` is converted; value can be 0 through 65535 (unsigned).</span></span>|
|`CDate`|[<span data-ttu-id="f9532-123">Date 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-123">Date Data Type</span></span>](../data-types/date-data-type.md)|<span data-ttu-id="f9532-124">任何有效的日期和时间表示形式。</span><span class="sxs-lookup"><span data-stu-id="f9532-124">Any valid representation of a date and time.</span></span>|
|`CDbl`|[<span data-ttu-id="f9532-125">Double 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-125">Double Data Type</span></span>](../data-types/double-data-type.md)|<span data-ttu-id="f9532-126">-1.79769313486231570 e + 308 到-4.94065645841246544 E-324 for 负值;4.94065645841246544 e-324 到 1.79769313486231570 E + 308 的正值。</span><span class="sxs-lookup"><span data-stu-id="f9532-126">-1.79769313486231570E+308 through -4.94065645841246544E-324 for negative values; 4.94065645841246544E-324 through 1.79769313486231570E+308 for positive values.</span></span>|
|`CDec`|[<span data-ttu-id="f9532-127">Decimal 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-127">Decimal Data Type</span></span>](../data-types/decimal-data-type.md)|<span data-ttu-id="f9532-128">对于零缩放数字，为 +/-79228162514264337593543950335，即无小数位的数字。</span><span class="sxs-lookup"><span data-stu-id="f9532-128">+/-79,228,162,514,264,337,593,543,950,335 for zero-scaled numbers, that is, numbers with no decimal places.</span></span> <span data-ttu-id="f9532-129">对于包含28位小数位数的数字，范围为 +/-7.9228162514264337593543950335。</span><span class="sxs-lookup"><span data-stu-id="f9532-129">For numbers with 28 decimal places, the range is +/-7.9228162514264337593543950335.</span></span> <span data-ttu-id="f9532-130">可能的最小非零数字为0.0000000000000000000000000001 （+/-1E-28）。</span><span class="sxs-lookup"><span data-stu-id="f9532-130">The smallest possible non-zero number is 0.0000000000000000000000000001 (+/-1E-28).</span></span>|
|`CInt`|[<span data-ttu-id="f9532-131">Integer 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-131">Integer Data Type</span></span>](../data-types/integer-data-type.md)|<span data-ttu-id="f9532-132"><xref:System.Int32.MinValue?displayProperty=nameWithType>（-2147483648）到 <xref:System.Int32.MaxValue?displayProperty=nameWithType> （2147483647），小数部分将舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-132"><xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) through <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2,147,483,647); fractional parts are rounded.<sup>1</sup></span></span> <br/><br/><span data-ttu-id="f9532-133">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到整数的转换性能 `CInt` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-133">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to integer conversion with the `CInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-134">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-134">See the [CInt Example](#cint-example) section for an example.</span></span> |
|`CLng`|[<span data-ttu-id="f9532-135">Long 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-135">Long Data Type</span></span>](../data-types/long-data-type.md)|<span data-ttu-id="f9532-136"><xref:System.Int64.MinValue?displayProperty=nameWithType>（-9223372036854775808）到 <xref:System.Int64.MaxValue?displayProperty=nameWithType> （9223372036854775807），小数部分将舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-136"><xref:System.Int64.MinValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) through <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-137">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到64位整数转换的性能 `CLng` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-137">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 64-bit integer conversion with the `CLng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-138">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-138">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CObj`|[<span data-ttu-id="f9532-139">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="f9532-139">Object Data Type</span></span>](../data-types/object-data-type.md)|<span data-ttu-id="f9532-140">任何有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="f9532-140">Any valid expression.</span></span>|
|`CSByte`|[<span data-ttu-id="f9532-141">SByte 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-141">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)|<span data-ttu-id="f9532-142"><xref:System.SByte.MinValue?displayProperty=nameWithType>（-128）到 <xref:System.SByte.MaxValue?displayProperty=nameWithType> （127），小数部分将舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-142"><xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) through <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-143">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到带符号字节转换的性能 `CSByte` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-143">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to signed byte conversion with the `CSByte` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-144">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-144">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CShort`|[<span data-ttu-id="f9532-145">Short 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-145">Short Data Type</span></span>](../data-types/short-data-type.md)|<span data-ttu-id="f9532-146"><xref:System.Int16.MinValue?displayProperty=nameWithType>（-32768）到 <xref:System.Int16.MaxValue?displayProperty=nameWithType> （32767），小数部分将舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-146"><xref:System.Int16.MinValue?displayProperty=nameWithType> (-32,768) through <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32,767); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-147">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到16位整数转换的性能 `CShort` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-147">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to 16-bit integer conversion with the `CShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-148">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-148">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CSng`|[<span data-ttu-id="f9532-149">Single 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-149">Single Data Type</span></span>](../data-types/single-data-type.md)|<span data-ttu-id="f9532-150">-3.402823 e + 38 到-1.401298 E-45 for 负值;1.401298 e-45 到 3.402823 E + 38 表示正值。</span><span class="sxs-lookup"><span data-stu-id="f9532-150">-3.402823E+38 through -1.401298E-45 for negative values; 1.401298E-45 through 3.402823E+38 for positive values.</span></span>|
|`CStr`|[<span data-ttu-id="f9532-151">String 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-151">String Data Type</span></span>](../data-types/string-data-type.md)|<span data-ttu-id="f9532-152">`CStr`根据 `expression` 参数返回。</span><span class="sxs-lookup"><span data-stu-id="f9532-152">Returns for `CStr` depend on the `expression` argument.</span></span> <span data-ttu-id="f9532-153">请参阅[CStr 函数的返回值](return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="f9532-153">See [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>|
|`CUInt`|[<span data-ttu-id="f9532-154">UInteger 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-154">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)|<span data-ttu-id="f9532-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType>（0）到 <xref:System.UInt32.MaxValue?displayProperty=nameWithType> （4294967295）（无符号）; 小数部分被舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-155"><xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4,294,967,295) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-156">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到无符号整数转换的性能; 有关 `CUInt` 详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-156">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned integer conversion with the `CUInt` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-157">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-157">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CULng`|[<span data-ttu-id="f9532-158">ULong 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-158">ULong Data Type</span></span>](../data-types/ulong-data-type.md)|<span data-ttu-id="f9532-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType>（0）到 <xref:System.UInt64.MaxValue?displayProperty=nameWithType> （18446744073709551615）（无符号）; 小数部分被舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-159"><xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-160">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到无符号长整数转换的性能; 有关 `CULng` 详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-160">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned long integer conversion with the `CULng` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-161">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-161">See the [CInt Example](#cint-example) section for an example.</span></span>|
|`CUShort`|[<span data-ttu-id="f9532-162">UShort 数据类型</span><span class="sxs-lookup"><span data-stu-id="f9532-162">UShort Data Type</span></span>](../data-types/ushort-data-type.md)|<span data-ttu-id="f9532-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType>（0）到 <xref:System.UInt16.MaxValue?displayProperty=nameWithType> （65535）（无符号）; 小数部分被舍入。<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="f9532-163"><xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) through <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65,535) (unsigned); fractional parts are rounded.<sup>1</sup></span></span><br/><br/><span data-ttu-id="f9532-164">从 Visual Basic 15.8 开始，Visual Basic 通过函数优化浮点到无符号16位整数转换的性能 `CUShort` ; 有关详细信息，请参阅 "[备注](#remarks)" 部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-164">Starting with Visual Basic 15.8, Visual Basic optimizes the performance of floating-point to unsigned 16-bit integer conversion with the `CUShort` function; see the [Remarks](#remarks) section for more information.</span></span> <span data-ttu-id="f9532-165">有关示例，请参阅[CInt 示例](#cint-example)部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-165">See the [CInt Example](#cint-example) section for an example.</span></span>|

<span data-ttu-id="f9532-166"><sup>1</sup>小数部分可服从一种特殊类型的舍入，称为 "*银行家舍入*"。</span><span class="sxs-lookup"><span data-stu-id="f9532-166"><sup>1</sup> Fractional parts can be subject to a special type of rounding called *banker's rounding*.</span></span> <span data-ttu-id="f9532-167">有关详细信息，请参阅 "备注"。</span><span class="sxs-lookup"><span data-stu-id="f9532-167">See "Remarks" for more information.</span></span>

## <a name="remarks"></a><span data-ttu-id="f9532-168">备注</span><span class="sxs-lookup"><span data-stu-id="f9532-168">Remarks</span></span>

<span data-ttu-id="f9532-169">作为一种规则，应优先使用 Visual Basic 类型转换函数，以对 `ToString()` <xref:System.Convert> 类或单个类型结构或类等 .NET Framework 方法。</span><span class="sxs-lookup"><span data-stu-id="f9532-169">As a rule, you should use the Visual Basic type conversion functions in preference to the .NET Framework methods such as `ToString()`, either on the <xref:System.Convert> class or on an individual type structure or class.</span></span> <span data-ttu-id="f9532-170">Visual Basic 函数旨在实现与 Visual Basic 代码的最佳交互，并使源代码更简单、更易于阅读。</span><span class="sxs-lookup"><span data-stu-id="f9532-170">The Visual Basic functions are designed for optimal interaction with Visual Basic code, and they also make your source code shorter and easier to read.</span></span> <span data-ttu-id="f9532-171">此外，.NET Framework 转换方法不会始终产生与 Visual Basic 函数相同的结果，例如，转换 `Boolean` 为时 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-171">In addition, the .NET Framework conversion methods do not always produce the same results as the Visual Basic functions, for example when converting `Boolean` to `Integer`.</span></span> <span data-ttu-id="f9532-172">有关详细信息，请参阅[数据类型疑难解答](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f9532-172">For more information, see [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

<span data-ttu-id="f9532-173">从 Visual Basic 15.8 开始，当你将 <xref:System.Single> <xref:System.Double> 以下方法返回的或值传递给整数转换函数之一（ `CByte` 、 `CShort` 、、 `CInt` `CLng` 、 `CSByte` `CUShort` `CUInt` `CULng` 、、、）时，将优化浮点到整数转换的性能：</span><span class="sxs-lookup"><span data-stu-id="f9532-173">Starting with Visual Basic 15.8, the performance of floating-point-to-integer conversion is optimized when you pass the <xref:System.Single> or <xref:System.Double> value returned by the following methods to one of the integer conversion functions (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

<span data-ttu-id="f9532-174">此优化允许执行大量整数转换的代码最多运行两次。</span><span class="sxs-lookup"><span data-stu-id="f9532-174">This optimization allows code that does a large number of integer conversions to run up to twice as fast.</span></span> <span data-ttu-id="f9532-175">下面的示例阐释了这些优化的浮点到整数转换：</span><span class="sxs-lookup"><span data-stu-id="f9532-175">The following example illustrates these optimized floating-point-to-integer conversions:</span></span>

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a><span data-ttu-id="f9532-176">行为</span><span class="sxs-lookup"><span data-stu-id="f9532-176">Behavior</span></span>

- <span data-ttu-id="f9532-177">**强制.**</span><span class="sxs-lookup"><span data-stu-id="f9532-177">**Coercion.**</span></span> <span data-ttu-id="f9532-178">通常，可以使用数据类型转换函数将操作的结果强制转换为特定的数据类型，而不是默认的数据类型。</span><span class="sxs-lookup"><span data-stu-id="f9532-178">In general, you can use the data type conversion functions to coerce the result of an operation to a particular data type rather than the default data type.</span></span> <span data-ttu-id="f9532-179">例如， `CDec` 在通常会发生单精度、双精度或整数算法的情况下使用来强制进行十进制算法。</span><span class="sxs-lookup"><span data-stu-id="f9532-179">For example, use `CDec` to force decimal arithmetic in cases where single-precision, double-precision, or integer arithmetic would normally take place.</span></span>

- <span data-ttu-id="f9532-180">**转换失败。**</span><span class="sxs-lookup"><span data-stu-id="f9532-180">**Failed Conversions.**</span></span> <span data-ttu-id="f9532-181">如果 `expression` 传递给函数的超出了要转换的数据类型的范围，则 <xref:System.OverflowException> 会发生。</span><span class="sxs-lookup"><span data-stu-id="f9532-181">If the `expression` passed to the function is outside the range of the data type to which it is to be converted, an <xref:System.OverflowException> occurs.</span></span>

- <span data-ttu-id="f9532-182">**小数部分。**</span><span class="sxs-lookup"><span data-stu-id="f9532-182">**Fractional Parts.**</span></span> <span data-ttu-id="f9532-183">将非整数值转换为整型类型时，整数转换函数（ `CByte` 、、、、、、 `CInt` `CLng` `CSByte` `CShort` `CUInt` `CULng` 和 `CUShort` ）将删除小数部分，并将值舍入到最接近的整数。</span><span class="sxs-lookup"><span data-stu-id="f9532-183">When you convert a nonintegral value to an integral type, the integer conversion functions (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, and `CUShort`) remove the fractional part and round the value to the closest integer.</span></span>

     <span data-ttu-id="f9532-184">如果小数部分正好为0.5，则整数转换函数会将其舍入到最接近的偶数。</span><span class="sxs-lookup"><span data-stu-id="f9532-184">If the fractional part is exactly 0.5, the integer conversion functions round it to the nearest even integer.</span></span> <span data-ttu-id="f9532-185">例如，0.5 舍入为0，1.5 和2.5 都舍入到2。</span><span class="sxs-lookup"><span data-stu-id="f9532-185">For example, 0.5 rounds to 0, and 1.5 and 2.5 both round to 2.</span></span> <span data-ttu-id="f9532-186">这有时称为 "*银行家舍入*"，它的目的是为了弥补在一起添加多个这类数字时可能累积的偏差。</span><span class="sxs-lookup"><span data-stu-id="f9532-186">This is sometimes called *banker's rounding*, and its purpose is to compensate for a bias that could accumulate when adding many such numbers together.</span></span>

     <span data-ttu-id="f9532-187">`CInt`和 `CLng` 不同于 <xref:Microsoft.VisualBasic.Conversion.Int%2A> 和 <xref:Microsoft.VisualBasic.Conversion.Fix%2A> 函数，它们截断而不是舍入数字的小数部分。</span><span class="sxs-lookup"><span data-stu-id="f9532-187">`CInt` and `CLng` differ from the <xref:Microsoft.VisualBasic.Conversion.Int%2A> and <xref:Microsoft.VisualBasic.Conversion.Fix%2A> functions, which truncate, rather than round, the fractional part of a number.</span></span> <span data-ttu-id="f9532-188">同样， `Fix` 和 `Int` 总是返回与传入的数据类型相同的值。</span><span class="sxs-lookup"><span data-stu-id="f9532-188">Also, `Fix` and `Int` always return a value of the same data type as you pass in.</span></span>

- <span data-ttu-id="f9532-189">**日期/时间转换。**</span><span class="sxs-lookup"><span data-stu-id="f9532-189">**Date/Time Conversions.**</span></span> <span data-ttu-id="f9532-190">使用 <xref:Microsoft.VisualBasic.Information.IsDate%2A> 函数确定是否可将值转换为日期和时间。</span><span class="sxs-lookup"><span data-stu-id="f9532-190">Use the <xref:Microsoft.VisualBasic.Information.IsDate%2A> function to determine if a value can be converted to a date and time.</span></span> <span data-ttu-id="f9532-191">`CDate`识别日期文本和时间文本，而不是数值。</span><span class="sxs-lookup"><span data-stu-id="f9532-191">`CDate` recognizes date literals and time literals but not numeric values.</span></span> <span data-ttu-id="f9532-192">若要将 6.0 Visual Basic `Date` 值转换为 `Date` Visual Basic 2005 或更高版本中的值，可以使用 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="f9532-192">To convert a Visual Basic 6.0 `Date` value to a `Date` value in Visual Basic 2005 or later versions, you can use the <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="f9532-193">**非特定日期/时间值。**</span><span class="sxs-lookup"><span data-stu-id="f9532-193">**Neutral Date/Time Values.**</span></span> <span data-ttu-id="f9532-194">[日期数据类型](../data-types/date-data-type.md)始终包含日期和时间信息。</span><span class="sxs-lookup"><span data-stu-id="f9532-194">The [Date Data Type](../data-types/date-data-type.md) always contains both date and time information.</span></span> <span data-ttu-id="f9532-195">出于类型转换的目的，Visual Basic 将1/1/0001 （第1年1月1日）视为日期的*非特定值*，00:00:00 （午夜）为时间的非特定值。</span><span class="sxs-lookup"><span data-stu-id="f9532-195">For purposes of type conversion, Visual Basic considers 1/1/0001 (January 1 of the year 1) to be a *neutral value* for the date, and 00:00:00 (midnight) to be a neutral value for the time.</span></span> <span data-ttu-id="f9532-196">如果将值转换 `Date` 为字符串，则不 `CStr` 会在结果字符串中包含非特定值。</span><span class="sxs-lookup"><span data-stu-id="f9532-196">If you convert a `Date` value to a string, `CStr` does not include neutral values in the resulting string.</span></span> <span data-ttu-id="f9532-197">例如，如果转换 `#January 1, 0001 9:30:00#` 为字符串，则结果为 "9:30:00 AM"; 日期信息将被取消。</span><span class="sxs-lookup"><span data-stu-id="f9532-197">For example, if you convert `#January 1, 0001 9:30:00#` to a string, the result is "9:30:00 AM"; the date information is suppressed.</span></span> <span data-ttu-id="f9532-198">但是，日期信息仍以原始值的形式存在 `Date` ，可以通过函数（如 function）恢复 <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> 。</span><span class="sxs-lookup"><span data-stu-id="f9532-198">However, the date information is still present in the original `Date` value and can be recovered with functions such as <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> function.</span></span>

- <span data-ttu-id="f9532-199">**区分区域性。**</span><span class="sxs-lookup"><span data-stu-id="f9532-199">**Culture Sensitivity.**</span></span> <span data-ttu-id="f9532-200">涉及字符串的类型转换函数根据应用程序的当前区域性设置执行转换。</span><span class="sxs-lookup"><span data-stu-id="f9532-200">The type conversion functions involving strings perform conversions based on the current culture settings for the application.</span></span> <span data-ttu-id="f9532-201">例如， `CDate` 根据系统的区域设置识别日期格式。</span><span class="sxs-lookup"><span data-stu-id="f9532-201">For example, `CDate` recognizes date formats according to the locale setting of your system.</span></span> <span data-ttu-id="f9532-202">必须以正确的顺序为你的区域设置提供日期、月份和年份，否则可能无法正确解释日期。</span><span class="sxs-lookup"><span data-stu-id="f9532-202">You must provide the day, month, and year in the correct order for your locale, or the date might not be interpreted correctly.</span></span> <span data-ttu-id="f9532-203">如果长日期格式包含一周内的字符串（如 "星期三"），则不能识别该格式。</span><span class="sxs-lookup"><span data-stu-id="f9532-203">A long date format is not recognized if it contains a day-of-the-week string, such as "Wednesday".</span></span>

     <span data-ttu-id="f9532-204">如果需要转换为或从值的字符串表示形式转换而不是由区域设置指定的格式，则不能使用 Visual Basic 类型转换函数。</span><span class="sxs-lookup"><span data-stu-id="f9532-204">If you need to convert to or from a string representation of a value in a format other than the one specified by your locale, you cannot use the Visual Basic type conversion functions.</span></span> <span data-ttu-id="f9532-205">为此，请使用 `ToString(IFormatProvider)` `Parse(String, IFormatProvider)` 该值类型的和方法。</span><span class="sxs-lookup"><span data-stu-id="f9532-205">To do this, use the `ToString(IFormatProvider)` and `Parse(String, IFormatProvider)` methods of that value's type.</span></span> <span data-ttu-id="f9532-206">例如，在将 <xref:System.Double.Parse%2A?displayProperty=nameWithType> 字符串转换为时使用，在将 `Double` 类型的 <xref:System.Double.ToString%2A?displayProperty=nameWithType> 值转换 `Double` 为字符串时使用。</span><span class="sxs-lookup"><span data-stu-id="f9532-206">For example, use <xref:System.Double.Parse%2A?displayProperty=nameWithType> when converting a string to a `Double`, and use <xref:System.Double.ToString%2A?displayProperty=nameWithType> when converting a value of type `Double` to a string.</span></span>

## <a name="ctype-function"></a><span data-ttu-id="f9532-207">CType Function</span><span class="sxs-lookup"><span data-stu-id="f9532-207">CType Function</span></span>

<span data-ttu-id="f9532-208">[CType 函数](ctype-function.md)使用第二个参数， `typename` 并将其 `expression` 强制 `typename` 转换为，其中 `typename` 可以是存在有效转换的任何数据类型、结构、类或接口。</span><span class="sxs-lookup"><span data-stu-id="f9532-208">The [CType Function](ctype-function.md) takes a second argument, `typename`, and coerces `expression` to `typename`, where `typename` can be any data type, structure, class, or interface to which there exists a valid conversion.</span></span>

<span data-ttu-id="f9532-209">有关 `CType` 与其他类型转换关键字的比较，请参阅[DirectCast 运算符](../operators/directcast-operator.md)和[TryCast 运算符](../operators/trycast-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="f9532-209">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../operators/directcast-operator.md) and [TryCast Operator](../operators/trycast-operator.md).</span></span>

## <a name="cbool-example"></a><span data-ttu-id="f9532-210">CBool 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-210">CBool Example</span></span>

<span data-ttu-id="f9532-211">下面的示例使用 `CBool` 函数将表达式转换为 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="f9532-211">The following example uses the `CBool` function to convert expressions to `Boolean` values.</span></span> <span data-ttu-id="f9532-212">如果表达式的计算结果为非零值 `CBool` ， `True` 则返回; 否则返回 `False` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-212">If an expression evaluates to a nonzero value, `CBool` returns `True`; otherwise, it returns `False`.</span></span>

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a><span data-ttu-id="f9532-213">CByte 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-213">CByte Example</span></span>

<span data-ttu-id="f9532-214">下面的示例使用 `CByte` 函数将表达式转换为 `Byte` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-214">The following example uses the `CByte` function to convert an expression to a `Byte`.</span></span>

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a><span data-ttu-id="f9532-215">CChar 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-215">CChar Example</span></span>

<span data-ttu-id="f9532-216">下面的示例使用 `CChar` 函数将表达式的第一个字符转换 `String` 为 `Char` 类型。</span><span class="sxs-lookup"><span data-stu-id="f9532-216">The following example uses the `CChar` function to convert the first character of a `String` expression to a `Char` type.</span></span>

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

<span data-ttu-id="f9532-217">的输入参数 `CChar` 必须是数据类型 `Char` 或 `String` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-217">The input argument to `CChar` must be of data type `Char` or `String`.</span></span> <span data-ttu-id="f9532-218">不能使用将 `CChar` 数字转换为字符，因为 `CChar` 无法接受数值数据类型。</span><span class="sxs-lookup"><span data-stu-id="f9532-218">You cannot use `CChar` to convert a number to a character, because `CChar` cannot accept a numeric data type.</span></span> <span data-ttu-id="f9532-219">下面的示例获取一个表示码位（字符代码）的数字，并将其转换为相应的字符。</span><span class="sxs-lookup"><span data-stu-id="f9532-219">The following example obtains a number representing a code point (character code) and converts it to the corresponding character.</span></span> <span data-ttu-id="f9532-220">它使用 <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> 函数来获取数字的字符串，将 `CInt` 字符串转换为类型 `Integer` ，并 `ChrW` 将数字转换为类型 `Char` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-220">It uses the <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> function to obtain the string of digits, `CInt` to convert the string to type `Integer`, and `ChrW` to convert the number to type `Char`.</span></span>

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a><span data-ttu-id="f9532-221">CDate 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-221">CDate Example</span></span>

<span data-ttu-id="f9532-222">下面的示例使用 `CDate` 函数将字符串转换为 `Date` 值。</span><span class="sxs-lookup"><span data-stu-id="f9532-222">The following example uses the `CDate` function to convert strings to `Date` values.</span></span> <span data-ttu-id="f9532-223">通常，不建议将日期和时间作为字符串进行硬编码（如本示例所示）。</span><span class="sxs-lookup"><span data-stu-id="f9532-223">In general, hard-coding dates and times as strings (as shown in this example) is not recommended.</span></span> <span data-ttu-id="f9532-224">改为使用日期文本和时间文本（如 #Feb 12、1969 # 和 #4： 45:23 PM #）。</span><span class="sxs-lookup"><span data-stu-id="f9532-224">Use date literals and time literals, such as #Feb 12, 1969# and #4:45:23 PM#, instead.</span></span>

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a><span data-ttu-id="f9532-225">CDbl 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-225">CDbl Example</span></span>

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a><span data-ttu-id="f9532-226">CDec 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-226">CDec Example</span></span>

<span data-ttu-id="f9532-227">下面的示例使用 `CDec` 函数将数值转换为 `Decimal` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-227">The following example uses the `CDec` function to convert a numeric value to `Decimal`.</span></span>

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a><span data-ttu-id="f9532-228">CInt 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-228">CInt Example</span></span>

<span data-ttu-id="f9532-229">下面的示例使用 `CInt` 函数将值转换为 `Integer` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-229">The following example uses the `CInt` function to convert a value to `Integer`.</span></span>

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a><span data-ttu-id="f9532-230">CLng 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-230">CLng Example</span></span>

<span data-ttu-id="f9532-231">下面的示例使用 `CLng` 函数将值转换为 `Long` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-231">The following example uses the `CLng` function to convert values to `Long`.</span></span>

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a><span data-ttu-id="f9532-232">CObj 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-232">CObj Example</span></span>

<span data-ttu-id="f9532-233">下面的示例使用 `CObj` 函数将数值转换为 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-233">The following example uses the `CObj` function to convert a numeric value to `Object`.</span></span> <span data-ttu-id="f9532-234">`Object`变量本身只包含一个四字节指针，该指针指向 `Double` 赋给它的值。</span><span class="sxs-lookup"><span data-stu-id="f9532-234">The `Object` variable itself contains only a four-byte pointer, which points to the `Double` value assigned to it.</span></span>

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a><span data-ttu-id="f9532-235">CSByte 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-235">CSByte Example</span></span>

<span data-ttu-id="f9532-236">下面的示例使用 `CSByte` 函数将数值转换为 `SByte` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-236">The following example uses the `CSByte` function to convert a numeric value to `SByte`.</span></span>

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a><span data-ttu-id="f9532-237">CShort 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-237">CShort Example</span></span>

<span data-ttu-id="f9532-238">下面的示例使用 `CShort` 函数将数值转换为 `Short` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-238">The following example uses the `CShort` function to convert a numeric value to `Short`.</span></span>

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a><span data-ttu-id="f9532-239">CSng 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-239">CSng Example</span></span>

<span data-ttu-id="f9532-240">下面的示例使用 `CSng` 函数将值转换为 `Single` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-240">The following example uses the `CSng` function to convert values to `Single`.</span></span>

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a><span data-ttu-id="f9532-241">CStr 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-241">CStr Example</span></span>

<span data-ttu-id="f9532-242">下面的示例使用 `CStr` 函数将数值转换为 `String` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-242">The following example uses the `CStr` function to convert a numeric value to `String`.</span></span>

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

<span data-ttu-id="f9532-243">下面的示例使用 `CStr` 函数将值转换 `Date` 为 `String` 值。</span><span class="sxs-lookup"><span data-stu-id="f9532-243">The following example uses the `CStr` function to convert `Date` values to `String` values.</span></span>

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

<span data-ttu-id="f9532-244">`CStr`始终以 `Date` 标准短格式呈现当前区域设置的值，例如 "6/15/2003 4:35:47 PM"。</span><span class="sxs-lookup"><span data-stu-id="f9532-244">`CStr` always renders a `Date` value in the standard short format for the current locale, for example, "6/15/2003 4:35:47 PM".</span></span> <span data-ttu-id="f9532-245">但是，会 `CStr` 禁止在日期和时间00:00:00 的*非特定值*1/1/0001。</span><span class="sxs-lookup"><span data-stu-id="f9532-245">However, `CStr` suppresses the *neutral values* of 1/1/0001 for the date and 00:00:00 for the time.</span></span>

<span data-ttu-id="f9532-246">有关返回的值的详细信息 `CStr` ，请参阅[CStr 函数的返回值](return-values-for-the-cstr-function.md)。</span><span class="sxs-lookup"><span data-stu-id="f9532-246">For more detail on the values returned by `CStr`, see [Return Values for the CStr Function](return-values-for-the-cstr-function.md).</span></span>

## <a name="cuint-example"></a><span data-ttu-id="f9532-247">CUInt 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-247">CUInt Example</span></span>

<span data-ttu-id="f9532-248">下面的示例使用 `CUInt` 函数将数值转换为 `UInteger` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-248">The following example uses the `CUInt` function to convert a numeric value to `UInteger`.</span></span>

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a><span data-ttu-id="f9532-249">CULng 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-249">CULng Example</span></span>

<span data-ttu-id="f9532-250">下面的示例使用 `CULng` 函数将数值转换为 `ULong` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-250">The following example uses the `CULng` function to convert a numeric value to `ULong`.</span></span>

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a><span data-ttu-id="f9532-251">CUShort 示例</span><span class="sxs-lookup"><span data-stu-id="f9532-251">CUShort Example</span></span>

<span data-ttu-id="f9532-252">下面的示例使用 `CUShort` 函数将数值转换为 `UShort` 。</span><span class="sxs-lookup"><span data-stu-id="f9532-252">The following example uses the `CUShort` function to convert a numeric value to `UShort`.</span></span>

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a><span data-ttu-id="f9532-253">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f9532-253">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="f9532-254">转换函数</span><span class="sxs-lookup"><span data-stu-id="f9532-254">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="f9532-255">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="f9532-255">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
