---
title: 内置类型 - C# 参考
description: 了解 C# 内置值类型和引用类型
ms.date: 02/04/2020
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 3366f718cd83a28f475fae9b4e65ce37fe7d8c7b
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803192"
---
# <a name="built-in-types-c-reference"></a><span data-ttu-id="2a1f5-103">内置类型（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2a1f5-103">Built-in types (C# reference)</span></span>

<span data-ttu-id="2a1f5-104">下表列出了 C# 内置[值](value-types.md)类型：</span><span class="sxs-lookup"><span data-stu-id="2a1f5-104">The following table lists the C# built-in [value](value-types.md) types:</span></span>

|<span data-ttu-id="2a1f5-105">C# 类型关键字</span><span class="sxs-lookup"><span data-stu-id="2a1f5-105">C# type keyword</span></span>|<span data-ttu-id="2a1f5-106">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="2a1f5-106">.NET type</span></span>|
|--------------|-------------------------|
|[`bool`](bool.md)|<xref:System.Boolean?displayProperty=nameWithType>|
|[`byte`](integral-numeric-types.md)|<xref:System.Byte?displayProperty=nameWithType>|
|[`sbyte`](integral-numeric-types.md)|<xref:System.SByte?displayProperty=nameWithType>|
|[`char`](char.md)|<xref:System.Char?displayProperty=nameWithType>|
|[`decimal`](floating-point-numeric-types.md)|<xref:System.Decimal?displayProperty=nameWithType>|
|[`double`](floating-point-numeric-types.md)|<xref:System.Double?displayProperty=nameWithType>|
|[`float`](floating-point-numeric-types.md)|<xref:System.Single?displayProperty=nameWithType>|
|[`int`](integral-numeric-types.md)|<xref:System.Int32?displayProperty=nameWithType>|
|[`uint`](integral-numeric-types.md)|<xref:System.UInt32?displayProperty=nameWithType>|
|[`long`](integral-numeric-types.md)|<xref:System.Int64?displayProperty=nameWithType>|
|[`ulong`](integral-numeric-types.md)|<xref:System.UInt64?displayProperty=nameWithType>|
|[`short`](integral-numeric-types.md)|<xref:System.Int16?displayProperty=nameWithType>|
|[`ushort`](integral-numeric-types.md)|<xref:System.UInt16?displayProperty=nameWithType>|

<span data-ttu-id="2a1f5-107">下表列出了 C# 内置[引用](../keywords/reference-types.md)类型：</span><span class="sxs-lookup"><span data-stu-id="2a1f5-107">The following table lists the C# built-in [reference](../keywords/reference-types.md) types:</span></span>

|<span data-ttu-id="2a1f5-108">C# 类型关键字</span><span class="sxs-lookup"><span data-stu-id="2a1f5-108">C# type keyword</span></span>|<span data-ttu-id="2a1f5-109">.NET 类型</span><span class="sxs-lookup"><span data-stu-id="2a1f5-109">.NET type</span></span>|
|--------------|-------------------------|
|[`object`](reference-types.md#the-object-type)|<xref:System.Object?displayProperty=nameWithType>|
|[`string`](reference-types.md#the-string-type)|<xref:System.String?displayProperty=nameWithType>|
|[`dynamic`](reference-types.md#the-dynamic-type)|<xref:System.Object?displayProperty=nameWithType>|

<span data-ttu-id="2a1f5-110">在上表中，左侧列中的每个 C# 类型关键字都是相应 .NET 类型的别名。</span><span class="sxs-lookup"><span data-stu-id="2a1f5-110">In the preceding tables, each C# type keyword from the left column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="2a1f5-111">它们是可互换的。</span><span class="sxs-lookup"><span data-stu-id="2a1f5-111">They are interchangeable.</span></span> <span data-ttu-id="2a1f5-112">例如，以下声明声明了相同类型的变量：</span><span class="sxs-lookup"><span data-stu-id="2a1f5-112">For example, the following declarations declare variables of the same type:</span></span>

```csharp
int a = 123;
System.Int32 b = 123;
```

<span data-ttu-id="2a1f5-113">[`void`](void.md) 关键字表示缺少类型。</span><span class="sxs-lookup"><span data-stu-id="2a1f5-113">The [`void`](void.md) keyword represents the absence of a type.</span></span> <span data-ttu-id="2a1f5-114">将其用作不返回值的方法的返回类型。</span><span class="sxs-lookup"><span data-stu-id="2a1f5-114">You use it as the return type of a method that doesn't return a value.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a1f5-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="2a1f5-115">See also</span></span>

- [<span data-ttu-id="2a1f5-116">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2a1f5-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2a1f5-117">C# 类型的默认值</span><span class="sxs-lookup"><span data-stu-id="2a1f5-117">Default values of C# types</span></span>](default-values.md)
