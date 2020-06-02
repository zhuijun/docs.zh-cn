---
title: 运算符重载
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 893b7d1f76dfb059a0ddca77dfd8654812e9ae12
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289728"
---
# <a name="operator-overloads"></a><span data-ttu-id="edf92-102">运算符重载</span><span class="sxs-lookup"><span data-stu-id="edf92-102">Operator Overloads</span></span>
<span data-ttu-id="edf92-103">运算符重载允许框架类型看起来像是内置语言基元。</span><span class="sxs-lookup"><span data-stu-id="edf92-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="edf92-104">尽管在某些情况下允许和有用，但应慎重使用运算符重载。</span><span class="sxs-lookup"><span data-stu-id="edf92-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="edf92-105">在许多情况下，运算符重载已经被滥用，例如，当框架设计器开始对应该为简单方法的操作使用运算符时。</span><span class="sxs-lookup"><span data-stu-id="edf92-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="edf92-106">以下准则可帮助您决定何时以及如何使用运算符重载。</span><span class="sxs-lookup"><span data-stu-id="edf92-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="edf92-107">❌避免定义运算符重载，但在应像基元（内置）类型的类型中除外。</span><span class="sxs-lookup"><span data-stu-id="edf92-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="edf92-108">✔️考虑在应感觉为基元类型的类型中定义运算符重载。</span><span class="sxs-lookup"><span data-stu-id="edf92-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="edf92-109">例如， <xref:System.String?displayProperty=nameWithType> 具有 `operator==` 并定义了 `operator!=` 。</span><span class="sxs-lookup"><span data-stu-id="edf92-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="edf92-110">✔️在表示数字的结构中定义运算符重载（如 <xref:System.Decimal?displayProperty=nameWithType> ）。</span><span class="sxs-lookup"><span data-stu-id="edf92-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="edf92-111">❌在定义运算符重载时不太刻意。</span><span class="sxs-lookup"><span data-stu-id="edf92-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="edf92-112">运算符重载非常有用，在这种情况下，操作的结果将是什么。</span><span class="sxs-lookup"><span data-stu-id="edf92-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="edf92-113">例如，可以 <xref:System.DateTime> 从一个中减去另一个 `DateTime` 并获取 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="edf92-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="edf92-114">但是，不适合使用逻辑联合运算符来联合两个数据库查询，或使用 shift 运算符将写入到流中。</span><span class="sxs-lookup"><span data-stu-id="edf92-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="edf92-115">❌除非至少有一个操作数为定义重载的类型，否则不要提供运算符重载。</span><span class="sxs-lookup"><span data-stu-id="edf92-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="edf92-116">✔️以对称方式重载运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="edf92-117">例如，如果你重载 `operator==` ，则还应重载 `operator!=` 。</span><span class="sxs-lookup"><span data-stu-id="edf92-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="edf92-118">同样，如果你重载 `operator<` ，则还应重载 `operator>` ，依此类推。</span><span class="sxs-lookup"><span data-stu-id="edf92-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="edf92-119">✔️考虑为具有对应于每个重载运算符的友好名称提供方法。</span><span class="sxs-lookup"><span data-stu-id="edf92-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="edf92-120">许多语言不支持运算符重载。</span><span class="sxs-lookup"><span data-stu-id="edf92-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="edf92-121">出于此原因，建议重载运算符的类型包含辅助方法，该方法具有提供等效功能的适当的特定于域的名称。</span><span class="sxs-lookup"><span data-stu-id="edf92-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="edf92-122">下表包含一个运算符列表和相应的友好方法名称。</span><span class="sxs-lookup"><span data-stu-id="edf92-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="edf92-123">C # 运算符符号</span><span class="sxs-lookup"><span data-stu-id="edf92-123">C# Operator Symbol</span></span>|<span data-ttu-id="edf92-124">元数据名称</span><span class="sxs-lookup"><span data-stu-id="edf92-124">Metadata Name</span></span>|<span data-ttu-id="edf92-125">友好名称</span><span class="sxs-lookup"><span data-stu-id="edf92-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="edf92-126">重载运算符 = =</span><span class="sxs-lookup"><span data-stu-id="edf92-126">Overloading Operator ==</span></span>
 <span data-ttu-id="edf92-127">重载 `operator ==` 非常复杂。</span><span class="sxs-lookup"><span data-stu-id="edf92-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="edf92-128">运算符的语义需要与其他一些成员（如）兼容 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="edf92-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="edf92-129">转换运算符</span><span class="sxs-lookup"><span data-stu-id="edf92-129">Conversion Operators</span></span>
 <span data-ttu-id="edf92-130">转换运算符是允许从一种类型转换为另一种类型的一元运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="edf92-131">运算符必须在操作数或返回类型上定义为静态成员。</span><span class="sxs-lookup"><span data-stu-id="edf92-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="edf92-132">有两种类型的转换运算符：隐式和显式。</span><span class="sxs-lookup"><span data-stu-id="edf92-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="edf92-133">❌如果最终用户不需要此类转换，请不要提供转换运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="edf92-134">❌不要定义类型的域之外的转换运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="edf92-135">例如，、 <xref:System.Int32> <xref:System.Double> 和 <xref:System.Decimal> 都是数值类型，而 <xref:System.DateTime> 不是。</span><span class="sxs-lookup"><span data-stu-id="edf92-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="edf92-136">因此，不应将转换运算符转换为 `Double(long)` `DateTime` 。</span><span class="sxs-lookup"><span data-stu-id="edf92-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="edf92-137">在这种情况下，构造函数是首选的。</span><span class="sxs-lookup"><span data-stu-id="edf92-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="edf92-138">❌如果转换可能有损，请不要提供隐式转换运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="edf92-139">例如，不应从到的隐式转换， `Double` `Int32` 因为的 `Double` 范围超出了 `Int32` 。</span><span class="sxs-lookup"><span data-stu-id="edf92-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="edf92-140">即使转换可能会有损，也可以提供显式转换运算符。</span><span class="sxs-lookup"><span data-stu-id="edf92-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="edf92-141">❌不从隐式强制转换引发异常。</span><span class="sxs-lookup"><span data-stu-id="edf92-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="edf92-142">最终用户很难了解发生的情况，因为他们可能不知道转换正在进行。</span><span class="sxs-lookup"><span data-stu-id="edf92-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="edf92-143"><xref:System.InvalidCastException?displayProperty=nameWithType>如果调用强制转换运算符导致了有损转换，并且该运算符的协定不允许有损转换，✔️将引发。</span><span class="sxs-lookup"><span data-stu-id="edf92-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="edf92-144">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="edf92-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="edf92-145">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="edf92-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="edf92-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="edf92-146">See also</span></span>

- [<span data-ttu-id="edf92-147">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="edf92-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="edf92-148">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="edf92-148">Framework Design Guidelines</span></span>](index.md)
