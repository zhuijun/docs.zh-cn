---
title: "byte（C# 参考）"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- byte
- byte_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8ef7494e2a8a1463d37cff77d1dacebec8182b66
ms.contentlocale: zh-cn
ms.lasthandoff: 07/28/2017

---
# <a name="byte-c-reference"></a><span data-ttu-id="62321-102">byte（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="62321-102">byte (C# Reference)</span></span>

<span data-ttu-id="62321-103">`byte` 表示存储下表所示值的整型类型。</span><span class="sxs-lookup"><span data-stu-id="62321-103">`byte` denotes an integral type that stores values as indicated in the following table.</span></span>  
  
|<span data-ttu-id="62321-104">类型</span><span class="sxs-lookup"><span data-stu-id="62321-104">Type</span></span>|<span data-ttu-id="62321-105">范围</span><span class="sxs-lookup"><span data-stu-id="62321-105">Range</span></span>|<span data-ttu-id="62321-106">大小</span><span class="sxs-lookup"><span data-stu-id="62321-106">Size</span></span>|<span data-ttu-id="62321-107">.NET Framework 类型</span><span class="sxs-lookup"><span data-stu-id="62321-107">.NET Framework type</span></span>|  
|----------|-----------|----------|-------------------------|  
|`byte`|<span data-ttu-id="62321-108">0 到 255</span><span class="sxs-lookup"><span data-stu-id="62321-108">0 to 255</span></span>|<span data-ttu-id="62321-109">无符号的 8 位整数</span><span class="sxs-lookup"><span data-stu-id="62321-109">Unsigned 8-bit integer</span></span>|<xref:System.Byte?displayProperty=fullName>|  
  
## <a name="literals"></a><span data-ttu-id="62321-110">文本</span><span class="sxs-lookup"><span data-stu-id="62321-110">Literals</span></span>  

 <span data-ttu-id="62321-111">可以通过为其分配十进制文本、十六进制文本或（从 C# 7 开始）二进制文本来声明和初始化 `byte` 变量。</span><span class="sxs-lookup"><span data-stu-id="62321-111">You can declare and initialize a `byte` variable by assigning a decimal literal, a hexadecimal literal, or (starting with C# 7) a binary literal to it.</span></span> <span data-ttu-id="62321-112">如果整数文本在 `byte` 范围之外（即，如果它小于 <xref:System.Byte.MinValue?displayProperty=fullName> 或大于 <xref:System.Byte.MaxValue?displayProperty=fullName>），会发生编译错误。</span><span class="sxs-lookup"><span data-stu-id="62321-112">If the integer literal is outside the range of `byte` (that is, if it is less than <xref:System.Byte.MinValue?displayProperty=fullName> or greater than <xref:System.Byte.MaxValue?displayProperty=fullName>), a compilation error occurs.</span></span>

<span data-ttu-id="62321-113">在以下示例中，等于 201、表示为十进制、十六进制和二进制文本的整数从 [int](../../../csharp/language-reference/keywords/int.md) 隐式转换为 `byte` 值。</span><span class="sxs-lookup"><span data-stu-id="62321-113">In the following example, integers equal to 201 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [int](../../../csharp/language-reference/keywords/int.md) to `byte` values.</span></span>    
  
<span data-ttu-id="62321-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span><span class="sxs-lookup"><span data-stu-id="62321-114">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]</span></span>  

> [!NOTE] 
> <span data-ttu-id="62321-115">使用前缀 `0x` 或 `0X` 表示十六进制文本，使用前缀 `0b` 或 `0B` 表示二进制文本。</span><span class="sxs-lookup"><span data-stu-id="62321-115">You use the prefix `0x` or `0X` to denote a hexadecimal literal and the prefix `0b` or `0B` to denote a binary literal.</span></span> <span data-ttu-id="62321-116">十进制文本没有前缀。</span><span class="sxs-lookup"><span data-stu-id="62321-116">Decimal literals have no prefix.</span></span>

<span data-ttu-id="62321-117">从 C# 7 开始，还可以使用下划线字符 `_` 作为数字分隔符，以增强可读性，如下例所示。</span><span class="sxs-lookup"><span data-stu-id="62321-117">Starting with C# 7, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

<span data-ttu-id="62321-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span><span class="sxs-lookup"><span data-stu-id="62321-118">[!code-cs[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]</span></span>  
 
## <a name="conversions"></a><span data-ttu-id="62321-119">转换</span><span class="sxs-lookup"><span data-stu-id="62321-119">Conversions</span></span>  
 <span data-ttu-id="62321-120">存在从 `byte` 到 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 的预定义隐式转换。</span><span class="sxs-lookup"><span data-stu-id="62321-120">There is a predefined implicit conversion from `byte` to [short](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), [ulong](../../../csharp/language-reference/keywords/ulong.md), [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), or [decimal](../../../csharp/language-reference/keywords/decimal.md).</span></span>  
  
 <span data-ttu-id="62321-121">不可将大存储大小的非文本数字类型隐式转换为 `byte`。</span><span class="sxs-lookup"><span data-stu-id="62321-121">You cannot implicitly convert non-literal numeric types of larger storage size to `byte`.</span></span> <span data-ttu-id="62321-122">有关整型类型存储大小的详细信息，请参阅[整型类型表](../../../csharp/language-reference/keywords/integral-types-table.md)。</span><span class="sxs-lookup"><span data-stu-id="62321-122">For more information on the storage sizes of integral types, see [Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md).</span></span> <span data-ttu-id="62321-123">以下面两个 `byte` 变量 `x` 和 `y` 为例：</span><span class="sxs-lookup"><span data-stu-id="62321-123">Consider, for example, the following two `byte` variables `x` and `y`:</span></span>  
  
```  
byte x = 10, y = 20;  
```  
  
 <span data-ttu-id="62321-124">以下赋值语句将产生一个编译器错误，原因是赋值运算符右侧的算术表达式在默认情况下的计算结果为 `int` 类型。</span><span class="sxs-lookup"><span data-stu-id="62321-124">The following assignment statement will produce a compilation error, because the arithmetic expression on the right-hand side of the assignment operator evaluates to `int` by default.</span></span>  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 <span data-ttu-id="62321-125">若要解决此问题，请使用强制转换：</span><span class="sxs-lookup"><span data-stu-id="62321-125">To fix this problem, use a cast:</span></span>  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 <span data-ttu-id="62321-126">但是，在目标变量具有相同或更大的存储大小时，也可以使用下列语句：</span><span class="sxs-lookup"><span data-stu-id="62321-126">It is possible though, to use the following statements where the destination variable has the same storage size or a larger storage size:</span></span>  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 <span data-ttu-id="62321-127">此外，不存在从浮点类型到 `byte` 类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="62321-127">Also, there is no implicit conversion from floating-point types to `byte`.</span></span> <span data-ttu-id="62321-128">例如，除非使用显式强制转换，否则以下语句将生成编译器错误：</span><span class="sxs-lookup"><span data-stu-id="62321-128">For example, the following statement generates a compiler error unless an explicit cast is used:</span></span>  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 <span data-ttu-id="62321-129">在调用重载方法时，必须使用转换。</span><span class="sxs-lookup"><span data-stu-id="62321-129">When calling overloaded methods, a cast must be used.</span></span> <span data-ttu-id="62321-130">以下面使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 参数的重载方法为例：</span><span class="sxs-lookup"><span data-stu-id="62321-130">Consider, for example, the following overloaded methods that use `byte` and [int](../../../csharp/language-reference/keywords/int.md) parameters:</span></span>  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 <span data-ttu-id="62321-131">使用 `byte` 强制转换可保证调用正确的类型，例如：</span><span class="sxs-lookup"><span data-stu-id="62321-131">Using the `byte` cast guarantees that the correct type is called, for example:</span></span>  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 <span data-ttu-id="62321-132">有关兼用浮点类型和整型类型的算术表达式的信息，请参阅 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。</span><span class="sxs-lookup"><span data-stu-id="62321-132">For information on arithmetic expressions with mixed floating-point types and integral types, see [float](../../../csharp/language-reference/keywords/float.md) and [double](../../../csharp/language-reference/keywords/double.md).</span></span>  
  
 <span data-ttu-id="62321-133">有关隐式数值转换规则的详细信息，请参阅[隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。</span><span class="sxs-lookup"><span data-stu-id="62321-133">For more information on implicit numeric conversion rules, see the [Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="62321-134">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="62321-134">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="62321-135">另请参阅</span><span class="sxs-lookup"><span data-stu-id="62321-135">See Also</span></span>  
 <span data-ttu-id="62321-136"><xref:System.Byte></span><span class="sxs-lookup"><span data-stu-id="62321-136"><xref:System.Byte></span></span>   
 <span data-ttu-id="62321-137">[C# 参考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="62321-137">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="62321-138">[C# 编程指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="62321-138">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="62321-139">[C# 关键字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="62321-139">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="62321-140">[整型类型表](../../../csharp/language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="62321-140">[Integral Types Table](../../../csharp/language-reference/keywords/integral-types-table.md) </span></span>  
 <span data-ttu-id="62321-141">[内置类型表](../../../csharp/language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="62321-141">[Built-In Types Table](../../../csharp/language-reference/keywords/built-in-types-table.md) </span></span>  
 <span data-ttu-id="62321-142">[隐式数值转换表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="62321-142">[Implicit Numeric Conversions Table](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
 [<span data-ttu-id="62321-143">显式数值转换表</span><span class="sxs-lookup"><span data-stu-id="62321-143">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
