---
title: 如何使用指针复制字节数组 - C# 编程指南
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397410"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="7e53d-102">如何使用指针复制字节数组（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="7e53d-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="7e53d-103">下面的示例使用指针将字节从一个数组复制到另一个数组。</span><span class="sxs-lookup"><span data-stu-id="7e53d-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="7e53d-104">此示例使用 [unsafe](../../language-reference/keywords/unsafe.md) 关键字，使你可以在 `Copy` 方法中使用指针。</span><span class="sxs-lookup"><span data-stu-id="7e53d-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="7e53d-105">[fixed](../../language-reference/keywords/fixed-statement.md) 语句用于声明指向源数组和目标数组的指针。</span><span class="sxs-lookup"><span data-stu-id="7e53d-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="7e53d-106">`fixed` 语句将源数组和目标数组的位置固定  在内存中，以便它们不会被垃圾回收所移动。</span><span class="sxs-lookup"><span data-stu-id="7e53d-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="7e53d-107">当完成 `fixed` 块后，将取消固定数组的内存块。</span><span class="sxs-lookup"><span data-stu-id="7e53d-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="7e53d-108">因为此示例中的 `Copy` 方法使用 `unsafe` 关键字，所以必须使用 [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) 编译器选项对其进行编译。</span><span class="sxs-lookup"><span data-stu-id="7e53d-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="7e53d-109">此示例使用索引而非第二个非托管的指针访问这两个数组的元素。</span><span class="sxs-lookup"><span data-stu-id="7e53d-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="7e53d-110">`pSource` 和 `pTarget` 指针的声明固定数组。</span><span class="sxs-lookup"><span data-stu-id="7e53d-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="7e53d-111">从 C# 7.3 开始可以使用此功能。</span><span class="sxs-lookup"><span data-stu-id="7e53d-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="7e53d-112">示例</span><span class="sxs-lookup"><span data-stu-id="7e53d-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="7e53d-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="7e53d-113">See also</span></span>

- [<span data-ttu-id="7e53d-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7e53d-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7e53d-115">不安全代码和指针</span><span class="sxs-lookup"><span data-stu-id="7e53d-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="7e53d-116">-unsafe（C# 编译器选项）</span><span class="sxs-lookup"><span data-stu-id="7e53d-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="7e53d-117">垃圾回收</span><span class="sxs-lookup"><span data-stu-id="7e53d-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
