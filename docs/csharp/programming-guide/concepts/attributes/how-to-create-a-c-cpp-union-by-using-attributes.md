---
title: 如何使用特性创建 C/C++ 联合 (C#)
description: 了解如何使用 C# 中的属性自定义结构在内存中的布局方式。 此示例实现来自 C/C++ 的 union 的等效项。
ms.date: 07/20/2015
ms.assetid: 85f35e56-26e0-4d31-9f3a-89bd4005e71a
ms.openlocfilehash: 766a070105441630dfd8fecf7b9f68fa6818fe50
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925067"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-c"></a><span data-ttu-id="d0e1d-104">如何使用特性创建 C/C++ 联合 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1d-104">How to create a C/C++ union by using attributes (C#)</span></span>

<span data-ttu-id="d0e1d-105">通过使用特性，可自定义结构在内存中的布局方式。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-105">By using attributes, you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="d0e1d-106">例如，可使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 特性在 C/C++ 中创建所谓的联合。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-106">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="d0e1d-107">示例</span><span class="sxs-lookup"><span data-stu-id="d0e1d-107">Example</span></span>

<span data-ttu-id="d0e1d-108">在此代码段中，`TestUnion` 的所有字段均从内存中的同一位置开始。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-108">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestUnion
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public byte b;
}
```

## <a name="example"></a><span data-ttu-id="d0e1d-109">示例</span><span class="sxs-lookup"><span data-stu-id="d0e1d-109">Example</span></span>

<span data-ttu-id="d0e1d-110">下面是另一个示例，其中的字段从不同的显式设置位置开始。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-110">The following is another example where fields start at different explicitly set locations.</span></span>

```csharp
// Add a using directive for System.Runtime.InteropServices.

[System.Runtime.InteropServices.StructLayout(LayoutKind.Explicit)]
struct TestExplicit
{
    [System.Runtime.InteropServices.FieldOffset(0)]
    public long lg;

    [System.Runtime.InteropServices.FieldOffset(0)]
    public int i1;

    [System.Runtime.InteropServices.FieldOffset(4)]
    public int i2;

    [System.Runtime.InteropServices.FieldOffset(8)]
    public double d;

    [System.Runtime.InteropServices.FieldOffset(12)]
    public char c;

    [System.Runtime.InteropServices.FieldOffset(14)]
    public byte b;
}
```

<span data-ttu-id="d0e1d-111">两个整数字段 `i1` 和 `i2` 共享与 `lg` 相同的内存位置。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-111">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="d0e1d-112">使用平台调用时，这种对结构布局的控制很有用。</span><span class="sxs-lookup"><span data-stu-id="d0e1d-112">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d0e1d-113">请参阅</span><span class="sxs-lookup"><span data-stu-id="d0e1d-113">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="d0e1d-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="d0e1d-114">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="d0e1d-115">特性</span><span class="sxs-lookup"><span data-stu-id="d0e1d-115">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="d0e1d-116">反射 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1d-116">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="d0e1d-117">特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1d-117">Attributes (C#)</span></span>](index.md)
- [<span data-ttu-id="d0e1d-118">创建自定义特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1d-118">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="d0e1d-119">使用反射访问特性 (C#)</span><span class="sxs-lookup"><span data-stu-id="d0e1d-119">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)
