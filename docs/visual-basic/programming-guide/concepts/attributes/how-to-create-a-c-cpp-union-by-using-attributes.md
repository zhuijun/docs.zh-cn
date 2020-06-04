---
title: 如何：使用特性创建 C + + + 联合
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: ebab0ad947f776932f9379af3969e369eeec1941
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400676"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="678ec-102">如何：使用特性创建 C/C++ 联合 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ec-102">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="678ec-103">通过使用特性，可自定义结构在内存中的布局方式。</span><span class="sxs-lookup"><span data-stu-id="678ec-103">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="678ec-104">例如，可使用 `StructLayout(LayoutKind.Explicit)` 和 `FieldOffset` 特性在 C/C++ 中创建所谓的联合。</span><span class="sxs-lookup"><span data-stu-id="678ec-104">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="678ec-105">示例</span><span class="sxs-lookup"><span data-stu-id="678ec-105">Example</span></span>

<span data-ttu-id="678ec-106">在此代码段中，`TestUnion` 的所有字段均从内存中的同一位置开始。</span><span class="sxs-lookup"><span data-stu-id="678ec-106">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a><span data-ttu-id="678ec-107">示例</span><span class="sxs-lookup"><span data-stu-id="678ec-107">Example</span></span>

<span data-ttu-id="678ec-108">下面是另一个示例，其中的字段从不同的显式设置位置开始。</span><span class="sxs-lookup"><span data-stu-id="678ec-108">The following is another example where fields start at different explicitly set locations.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

<span data-ttu-id="678ec-109">两个整数字段 `i1` 和 `i2` 共享与 `lg` 相同的内存位置。</span><span class="sxs-lookup"><span data-stu-id="678ec-109">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="678ec-110">使用平台调用时，这种对结构布局的控制很有用。</span><span class="sxs-lookup"><span data-stu-id="678ec-110">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="678ec-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="678ec-111">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="678ec-112">Visual Basic 编程指南</span><span class="sxs-lookup"><span data-stu-id="678ec-112">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="678ec-113">特性</span><span class="sxs-lookup"><span data-stu-id="678ec-113">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="678ec-114">反射 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ec-114">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="678ec-115">特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ec-115">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- [<span data-ttu-id="678ec-116">创建自定义特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ec-116">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)
- [<span data-ttu-id="678ec-117">使用反射访问特性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="678ec-117">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)
