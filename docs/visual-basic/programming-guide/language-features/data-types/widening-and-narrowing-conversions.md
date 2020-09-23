---
title: Widening and Narrowing Conversions
ms.date: 07/20/2015
helpviewer_keywords:
- widening conversions [Visual Basic]
- narrowing conversions [Visual Basic]
- conversions [Visual Basic], type
- data types [Visual Basic], changing
- variables [Visual Basic], changing data type
- conversions [Visual Basic], exceptions during conversion
- type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], data type
- conversions [Visual Basic], narrowing
- type conversion [Visual Basic], narrowing
- data type conversion [Visual Basic], widening
- data type conversion [Visual Basic], narrowing
- changing data types [Visual Basic]
- type conversion [Visual Basic], widening
- data type conversion [Visual Basic], exceptions during conversion
- conversions [Visual Basic], widening
ms.assetid: 058c3152-6c28-4268-af44-2209e774f0bd
ms.openlocfilehash: c0e10f5593ce5c81002233516444e415571541f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058529"
---
# <a name="widening-and-narrowing-conversions-visual-basic"></a><span data-ttu-id="90b40-102">扩大转换和收缩转换 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90b40-102">Widening and Narrowing Conversions (Visual Basic)</span></span>

<span data-ttu-id="90b40-103">类型转换的一个重要注意事项是转换的结果是否在目标数据类型的范围内。</span><span class="sxs-lookup"><span data-stu-id="90b40-103">An important consideration with a type conversion is whether the result of the conversion is within the range of the destination data type.</span></span>  
  
 <span data-ttu-id="90b40-104">*扩大转换*将值更改为数据类型，可允许原始数据的任何可能值。</span><span class="sxs-lookup"><span data-stu-id="90b40-104">A *widening conversion* changes a value to a data type that can allow for any possible value of the original data.</span></span>  <span data-ttu-id="90b40-105">扩大转换保留源值，但可以更改其表示形式。</span><span class="sxs-lookup"><span data-stu-id="90b40-105">Widening conversions preserve the source value but can change its representation.</span></span> <span data-ttu-id="90b40-106">如果从整型转换为或从整型转换为，则会发生这种情况 `Decimal` `Char` `String` 。</span><span class="sxs-lookup"><span data-stu-id="90b40-106">This occurs if you convert from an integral type to `Decimal`, or from `Char` to `String`.</span></span>  
  
 <span data-ttu-id="90b40-107">*“收缩转换”* 将值更改为可能无法保存某些可能值的数据类型。</span><span class="sxs-lookup"><span data-stu-id="90b40-107">A *narrowing conversion* changes a value to a data type that might not be able to hold some of the possible values.</span></span> <span data-ttu-id="90b40-108">例如，当将小数值转换为整型时，将对其进行舍入，并且将转换为的数值类型 `Boolean` 减小为 `True` 或 `False` 。</span><span class="sxs-lookup"><span data-stu-id="90b40-108">For example, a fractional value is rounded when it is converted to an integral type, and a numeric type being converted to `Boolean` is reduced to either `True` or `False`.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="90b40-109">扩大转换</span><span class="sxs-lookup"><span data-stu-id="90b40-109">Widening Conversions</span></span>  

 <span data-ttu-id="90b40-110">下表显示了标准扩大转换。</span><span class="sxs-lookup"><span data-stu-id="90b40-110">The following table shows the standard widening conversions.</span></span>  
  
|<span data-ttu-id="90b40-111">数据类型</span><span class="sxs-lookup"><span data-stu-id="90b40-111">Data type</span></span>|<span data-ttu-id="90b40-112">扩大到数据类型 <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-112">Widens to data types <sup>1</sup></span></span>|  
|---|---|  
|[<span data-ttu-id="90b40-113">SByte</span><span class="sxs-lookup"><span data-stu-id="90b40-113">SByte</span></span>](../../../language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="90b40-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="90b40-114">`SByte`, `Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="90b40-115">Byte</span><span class="sxs-lookup"><span data-stu-id="90b40-115">Byte</span></span>](../../../language-reference/data-types/byte-data-type.md)|<span data-ttu-id="90b40-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="90b40-116">`Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="90b40-117">Short</span><span class="sxs-lookup"><span data-stu-id="90b40-117">Short</span></span>](../../../language-reference/data-types/short-data-type.md)|<span data-ttu-id="90b40-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="90b40-118">`Short`, `Integer`, `Long`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="90b40-119">UShort</span><span class="sxs-lookup"><span data-stu-id="90b40-119">UShort</span></span>](../../../language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="90b40-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="90b40-120">`UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`</span></span>|  
|[<span data-ttu-id="90b40-121">整数</span><span class="sxs-lookup"><span data-stu-id="90b40-121">Integer</span></span>](../../../language-reference/data-types/integer-data-type.md)|<span data-ttu-id="90b40-122">`Integer`、 `Long` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-122">`Integer`, `Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="90b40-123">UInteger</span><span class="sxs-lookup"><span data-stu-id="90b40-123">UInteger</span></span>](../../../language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="90b40-124">`UInteger`、 `Long` 、 `ULong` 、 `Decimal` 、 `Single` 、 `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-124">`UInteger`, `Long`, `ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="90b40-125">Long</span><span class="sxs-lookup"><span data-stu-id="90b40-125">Long</span></span>](../../../language-reference/data-types/long-data-type.md)|<span data-ttu-id="90b40-126">`Long`， `Decimal` ， `Single` ， `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-126">`Long`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="90b40-127">ULong</span><span class="sxs-lookup"><span data-stu-id="90b40-127">ULong</span></span>](../../../language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="90b40-128">`ULong`， `Decimal` ， `Single` ， `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-128">`ULong`, `Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="90b40-129">小数</span><span class="sxs-lookup"><span data-stu-id="90b40-129">Decimal</span></span>](../../../language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="90b40-130">`Decimal`， `Single` ， `Double` <sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="90b40-130">`Decimal`, `Single`, `Double`<sup>2</sup></span></span>|  
|[<span data-ttu-id="90b40-131">单精度</span><span class="sxs-lookup"><span data-stu-id="90b40-131">Single</span></span>](../../../language-reference/data-types/single-data-type.md)|<span data-ttu-id="90b40-132">`Single`, `Double`</span><span class="sxs-lookup"><span data-stu-id="90b40-132">`Single`, `Double`</span></span>|  
|[<span data-ttu-id="90b40-133">双精度</span><span class="sxs-lookup"><span data-stu-id="90b40-133">Double</span></span>](../../../language-reference/data-types/double-data-type.md)|`Double`|  
|<span data-ttu-id="90b40-134">枚举类型 ([枚举](../../../language-reference/statements/enum-statement.md)) </span><span class="sxs-lookup"><span data-stu-id="90b40-134">Any enumerated type ([Enum](../../../language-reference/statements/enum-statement.md))</span></span>|<span data-ttu-id="90b40-135">它的基础整型类型和基础类型扩展到的任何类型。</span><span class="sxs-lookup"><span data-stu-id="90b40-135">Its underlying integral type and any type to which the underlying type widens.</span></span>|  
|[<span data-ttu-id="90b40-136">Char</span><span class="sxs-lookup"><span data-stu-id="90b40-136">Char</span></span>](../../../language-reference/data-types/char-data-type.md)|<span data-ttu-id="90b40-137">`Char`, `String`</span><span class="sxs-lookup"><span data-stu-id="90b40-137">`Char`, `String`</span></span>|  
|<span data-ttu-id="90b40-138">`Char` 数组</span><span class="sxs-lookup"><span data-stu-id="90b40-138">`Char` array</span></span>|<span data-ttu-id="90b40-139">`Char` 组成 `String`</span><span class="sxs-lookup"><span data-stu-id="90b40-139">`Char` array, `String`</span></span>|  
|<span data-ttu-id="90b40-140">任何类型</span><span class="sxs-lookup"><span data-stu-id="90b40-140">Any type</span></span>|[<span data-ttu-id="90b40-141">Object</span><span class="sxs-lookup"><span data-stu-id="90b40-141">Object</span></span>](../../../language-reference/data-types/object-data-type.md)|  
|<span data-ttu-id="90b40-142">任何派生类型</span><span class="sxs-lookup"><span data-stu-id="90b40-142">Any derived type</span></span>|<span data-ttu-id="90b40-143">它派生自的任何基类型 <sup>3</sup>。</span><span class="sxs-lookup"><span data-stu-id="90b40-143">Any base type from which it is derived <sup>3</sup>.</span></span>|  
|<span data-ttu-id="90b40-144">任何类型</span><span class="sxs-lookup"><span data-stu-id="90b40-144">Any type</span></span>|<span data-ttu-id="90b40-145">它所实现的任何接口。</span><span class="sxs-lookup"><span data-stu-id="90b40-145">Any interface it implements.</span></span>|  
|[<span data-ttu-id="90b40-146">没</span><span class="sxs-lookup"><span data-stu-id="90b40-146">Nothing</span></span>](../../../language-reference/nothing.md)|<span data-ttu-id="90b40-147">任何数据类型或对象类型。</span><span class="sxs-lookup"><span data-stu-id="90b40-147">Any data type or object type.</span></span>|  
  
 <span data-ttu-id="90b40-148"><sup>1</sup> 根据定义，每个数据类型扩大到自身。</span><span class="sxs-lookup"><span data-stu-id="90b40-148"><sup>1</sup> By definition, every data type widens to itself.</span></span>  
  
 <span data-ttu-id="90b40-149"><sup>2</sup> 从、、、 `Integer` `UInteger` `Long` `ULong` 或 `Decimal` 到或的 `Single` 转换 `Double` 可能会导致精度损失，但绝不会损失。</span><span class="sxs-lookup"><span data-stu-id="90b40-149"><sup>2</sup> Conversions from `Integer`, `UInteger`, `Long`, `ULong`, or `Decimal` to `Single` or `Double` might result in loss of precision, but never in loss of magnitude.</span></span> <span data-ttu-id="90b40-150">在这种意义上，它们不会导致信息丢失。</span><span class="sxs-lookup"><span data-stu-id="90b40-150">In this sense they do not incur information loss.</span></span>  
  
 <span data-ttu-id="90b40-151"><sup>3</sup> 从派生类型到它的某个基类型的转换都是扩大的。</span><span class="sxs-lookup"><span data-stu-id="90b40-151"><sup>3</sup> It might seem surprising that a conversion from a derived type to one of its base types is widening.</span></span> <span data-ttu-id="90b40-152">理由是，派生类型包含基类型的所有成员，因此它限定为基类型的实例。</span><span class="sxs-lookup"><span data-stu-id="90b40-152">The justification is that the derived type contains all the members of the base type, so it qualifies as an instance of the base type.</span></span> <span data-ttu-id="90b40-153">相反，基类型不包含由派生类型定义的任何新成员。</span><span class="sxs-lookup"><span data-stu-id="90b40-153">In the opposite direction, the base type does not contain any new members defined by the derived type.</span></span>  
  
 <span data-ttu-id="90b40-154">扩大转换始终会在运行时成功，不会导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="90b40-154">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="90b40-155">无论 [选项 Strict 语句](../../../language-reference/statements/option-strict-statement.md) 是否将类型检查开关设置为或，都可以始终隐式执行它们 `On` `Off` 。</span><span class="sxs-lookup"><span data-stu-id="90b40-155">You can always perform them implicitly, whether the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `On` or to `Off`.</span></span>  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="90b40-156">收缩转换</span><span class="sxs-lookup"><span data-stu-id="90b40-156">Narrowing Conversions</span></span>  

 <span data-ttu-id="90b40-157">标准收缩转换包括：</span><span class="sxs-lookup"><span data-stu-id="90b40-157">The standard narrowing conversions include the following:</span></span>  
  
- <span data-ttu-id="90b40-158">上表中的扩大转换的反向方向 (除了每个类型扩大到自身) </span><span class="sxs-lookup"><span data-stu-id="90b40-158">The reverse directions of the widening conversions in the preceding table (except that every type widens to itself)</span></span>  
  
- <span data-ttu-id="90b40-159">[布尔值](../../../language-reference/data-types/boolean-data-type.md)和任何数值类型之间的任意方向转换</span><span class="sxs-lookup"><span data-stu-id="90b40-159">Conversions in either direction between [Boolean](../../../language-reference/data-types/boolean-data-type.md) and any numeric type</span></span>  
  
- <span data-ttu-id="90b40-160">从任何数值类型到任何枚举类型的转换都 (`Enum`) </span><span class="sxs-lookup"><span data-stu-id="90b40-160">Conversions from any numeric type to any enumerated type (`Enum`)</span></span>  
  
- <span data-ttu-id="90b40-161">在[字符串](../../../language-reference/data-types/string-data-type.md)和任何数值类型、 `Boolean` 或[日期](../../../language-reference/data-types/date-data-type.md)之间的任意方向转换</span><span class="sxs-lookup"><span data-stu-id="90b40-161">Conversions in either direction between [String](../../../language-reference/data-types/string-data-type.md) and any numeric type, `Boolean`, or [Date](../../../language-reference/data-types/date-data-type.md)</span></span>  
  
- <span data-ttu-id="90b40-162">从数据类型或对象类型转换为派生自它的类型</span><span class="sxs-lookup"><span data-stu-id="90b40-162">Conversions from a data type or object type to a type derived from it</span></span>  
  
 <span data-ttu-id="90b40-163">收缩转换在运行时并不总是成功，可能会失败或导致数据丢失。</span><span class="sxs-lookup"><span data-stu-id="90b40-163">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="90b40-164">如果目标数据类型无法接收正在转换的值，则会发生错误。</span><span class="sxs-lookup"><span data-stu-id="90b40-164">An error occurs if the destination data type cannot receive the value being converted.</span></span> <span data-ttu-id="90b40-165">例如，数字转换可能会导致溢出。</span><span class="sxs-lookup"><span data-stu-id="90b40-165">For example, a numeric conversion can result in an overflow.</span></span> <span data-ttu-id="90b40-166">编译器不允许隐式执行收缩转换，除非 [Option Strict 语句](../../../language-reference/statements/option-strict-statement.md) 将类型检查开关设置为 `Off` 。</span><span class="sxs-lookup"><span data-stu-id="90b40-166">The compiler does not allow you to perform narrowing conversions implicitly unless the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md) sets the type checking switch to `Off`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90b40-167">禁止将从集合中的元素转换 `For Each…Next` 为循环控制变量的收缩转换错误。</span><span class="sxs-lookup"><span data-stu-id="90b40-167">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="90b40-168">有关详细信息和示例，请参阅中的 "收缩转换" 一节 [。下一语句](../../../language-reference/statements/for-each-next-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="90b40-168">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="when-to-use-narrowing-conversions"></a><span data-ttu-id="90b40-169">何时使用收缩转换</span><span class="sxs-lookup"><span data-stu-id="90b40-169">When to Use Narrowing Conversions</span></span>  

 <span data-ttu-id="90b40-170">如果知道源值可转换为目标数据类型，而不会出错或丢失数据，则可以使用收缩转换。</span><span class="sxs-lookup"><span data-stu-id="90b40-170">You use a narrowing conversion when you know the source value can be converted to the destination data type without error or data loss.</span></span> <span data-ttu-id="90b40-171">例如，如果你有一个 `String` 知道包含 "True" 或 "False" 的，则可以使用 `CBool` 关键字将其转换为 `Boolean` 。</span><span class="sxs-lookup"><span data-stu-id="90b40-171">For example, if you have a `String` that you know contains either "True" or "False," you can use the `CBool` keyword to convert it to `Boolean`.</span></span>  
  
## <a name="exceptions-during-conversion"></a><span data-ttu-id="90b40-172">转换过程中的异常</span><span class="sxs-lookup"><span data-stu-id="90b40-172">Exceptions During Conversion</span></span>  

 <span data-ttu-id="90b40-173">因为扩大转换始终会成功，所以它们不会引发异常。</span><span class="sxs-lookup"><span data-stu-id="90b40-173">Because widening conversions always succeed, they do not throw exceptions.</span></span> <span data-ttu-id="90b40-174">收缩转换在失败时，通常会引发以下异常：</span><span class="sxs-lookup"><span data-stu-id="90b40-174">Narrowing conversions, when they fail, most commonly throw the following exceptions:</span></span>  
  
- <span data-ttu-id="90b40-175"><xref:System.InvalidCastException> -如果在这两个类型之间未定义转换</span><span class="sxs-lookup"><span data-stu-id="90b40-175"><xref:System.InvalidCastException> — if no conversion is defined between the two types</span></span>  
  
- <span data-ttu-id="90b40-176"><xref:System.OverflowException> - (整型类型仅) 转换后的值对于目标类型来说太大</span><span class="sxs-lookup"><span data-stu-id="90b40-176"><xref:System.OverflowException> — (integral types only) if the converted value is too large for the target type</span></span>  
  
 <span data-ttu-id="90b40-177">如果某个类或结构定义一个 [CType 函数](../../../language-reference/functions/ctype-function.md) ，该函数将充当与该类或结构之间的转换运算符， `CType` 则可能会引发它认为合适的任何异常。</span><span class="sxs-lookup"><span data-stu-id="90b40-177">If a class or structure defines a [CType Function](../../../language-reference/functions/ctype-function.md) to serve as a conversion operator to or from that class or structure, that `CType` can throw any exception it deems appropriate.</span></span> <span data-ttu-id="90b40-178">此外，这 `CType` 可能会调用 Visual Basic 函数或 .NET Framework 方法，进而可能引发各种异常。</span><span class="sxs-lookup"><span data-stu-id="90b40-178">In addition, that `CType` might call Visual Basic functions or .NET Framework methods, which in turn could throw a variety of exceptions.</span></span>  
  
## <a name="changes-during-reference-type-conversions"></a><span data-ttu-id="90b40-179">引用类型转换期间的更改</span><span class="sxs-lookup"><span data-stu-id="90b40-179">Changes During Reference Type Conversions</span></span>  

 <span data-ttu-id="90b40-180">从 *引用类型* 进行的转换只复制指向值的指针。</span><span class="sxs-lookup"><span data-stu-id="90b40-180">A conversion from a *reference type* copies only the pointer to the value.</span></span> <span data-ttu-id="90b40-181">值本身既不会进行复制，也不会更改。</span><span class="sxs-lookup"><span data-stu-id="90b40-181">The value itself is neither copied nor changed in any way.</span></span> <span data-ttu-id="90b40-182">唯一可以更改的是保存指针的变量的数据类型。</span><span class="sxs-lookup"><span data-stu-id="90b40-182">The only thing that can change is the data type of the variable holding the pointer.</span></span> <span data-ttu-id="90b40-183">在下面的示例中，数据类型从派生类转换为其基类，但这两个变量现在指向的对象是不变的。</span><span class="sxs-lookup"><span data-stu-id="90b40-183">In the following example, the data type is converted from the derived class to its base class, but the object that both variables now point to is unchanged.</span></span>  
  
```vb  
' Assume class cSquare inherits from class cShape.  
Dim shape As cShape  
Dim square As cSquare = New cSquare  
' The following statement performs a widening  
' conversion from a derived class to its base class.  
shape = square  
```  
  
## <a name="see-also"></a><span data-ttu-id="90b40-184">请参阅</span><span class="sxs-lookup"><span data-stu-id="90b40-184">See also</span></span>

- [<span data-ttu-id="90b40-185">数据类型</span><span class="sxs-lookup"><span data-stu-id="90b40-185">Data Types</span></span>](index.md)
- [<span data-ttu-id="90b40-186">Visual Basic 中的类型转换</span><span class="sxs-lookup"><span data-stu-id="90b40-186">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="90b40-187">隐式转换和显式转换</span><span class="sxs-lookup"><span data-stu-id="90b40-187">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="90b40-188">字符串和其他类型之间的转换</span><span class="sxs-lookup"><span data-stu-id="90b40-188">Conversions Between Strings and Other Types</span></span>](conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="90b40-189">如何：在 Visual Basic 中将一个对象转换为其他类型</span><span class="sxs-lookup"><span data-stu-id="90b40-189">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="90b40-190">数组转换</span><span class="sxs-lookup"><span data-stu-id="90b40-190">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="90b40-191">数据类型</span><span class="sxs-lookup"><span data-stu-id="90b40-191">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="90b40-192">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="90b40-192">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
