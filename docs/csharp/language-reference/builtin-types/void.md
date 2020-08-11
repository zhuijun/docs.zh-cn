---
title: void - C# 参考
ms.date: 02/11/2020
f1_keywords:
- void_CSharpKeyword
- void
- (void)
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: faf1cea4d02ba042cd9fee1cfa6d18168c49dd61
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854979"
---
# <a name="void-c-reference"></a><span data-ttu-id="9ec03-102">void（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="9ec03-102">void (C# reference)</span></span>

<span data-ttu-id="9ec03-103">可以将 `void` 用作[方法](../../programming-guide/classes-and-structs/methods.md)（或[本地函数](../../programming-guide/classes-and-structs/local-functions.md)）的返回类型来指定该方法不返回值。</span><span class="sxs-lookup"><span data-stu-id="9ec03-103">You use `void` as the return type of a [method](../../programming-guide/classes-and-structs/methods.md) (or a [local function](../../programming-guide/classes-and-structs/local-functions.md)) to specify that the method doesn't return a value.</span></span>

[!code-csharp[void method](snippets/VoidType.cs#VoidExample)]

<span data-ttu-id="9ec03-104">还可以将 `void` 用作引用类型来声明指向未知类型的指针。</span><span class="sxs-lookup"><span data-stu-id="9ec03-104">You can also use `void` as a referent type to declare a pointer to an unknown type.</span></span> <span data-ttu-id="9ec03-105">有关详细信息，请参阅[指针类型](../../programming-guide/unsafe-code-pointers/pointer-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9ec03-105">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="9ec03-106">不能将 `void` 用作变量的类型。</span><span class="sxs-lookup"><span data-stu-id="9ec03-106">You cannot use `void` as the type of a variable.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ec03-107">另请参阅</span><span class="sxs-lookup"><span data-stu-id="9ec03-107">See also</span></span>

- [<span data-ttu-id="9ec03-108">C# 参考</span><span class="sxs-lookup"><span data-stu-id="9ec03-108">C# reference</span></span>](../index.md)
- <xref:System.Void?displayProperty=nameWithType>
