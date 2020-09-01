---
description: goto 语句 - C# 参考
title: goto 语句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- goto_CSharpKeyword
- goto
helpviewer_keywords:
- goto keyword [C#]
ms.assetid: 2c03c9c1-8119-44ef-b740-fb3d287a42fe
ms.openlocfilehash: de95e477bd7e76f549130643c8d4b70a0e2f015c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128421"
---
# <a name="goto-c-reference"></a><span data-ttu-id="7258e-103">goto（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="7258e-103">goto (C# Reference)</span></span>

<span data-ttu-id="7258e-104">`goto` 语句将程序控制直接传递给标记语句。</span><span class="sxs-lookup"><span data-stu-id="7258e-104">The `goto` statement transfers the program control directly to a labeled statement.</span></span>

<span data-ttu-id="7258e-105">`goto` 的一个通常用法是将控制传递给特定的 switch-case 标签或 `switch` 语句中的默认标签。</span><span class="sxs-lookup"><span data-stu-id="7258e-105">A common use of `goto` is to transfer control to a specific switch-case label or the default label in a `switch` statement.</span></span>

<span data-ttu-id="7258e-106">`goto` 语句还用于跳出深嵌套循环。</span><span class="sxs-lookup"><span data-stu-id="7258e-106">The `goto` statement is also useful to get out of deeply nested loops.</span></span>

## <a name="example"></a><span data-ttu-id="7258e-107">示例</span><span class="sxs-lookup"><span data-stu-id="7258e-107">Example</span></span>

<span data-ttu-id="7258e-108">下面的示例演示了 `goto` 在 [switch](switch.md) 语句中的使用。</span><span class="sxs-lookup"><span data-stu-id="7258e-108">The following example demonstrates using `goto` in a [switch](switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#4)]

## <a name="example"></a><span data-ttu-id="7258e-109">示例</span><span class="sxs-lookup"><span data-stu-id="7258e-109">Example</span></span>

<span data-ttu-id="7258e-110">下面的示例演示了使用 `goto` 跳出嵌套循环。</span><span class="sxs-lookup"><span data-stu-id="7258e-110">The following example demonstrates using `goto` to break out from nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#5)]

## <a name="c-language-specification"></a><span data-ttu-id="7258e-111">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7258e-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7258e-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="7258e-112">See also</span></span>

- [<span data-ttu-id="7258e-113">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7258e-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7258e-114">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="7258e-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7258e-115">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="7258e-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7258e-116">goto 语句 (C++)</span><span class="sxs-lookup"><span data-stu-id="7258e-116">goto Statement (C++)</span></span>](/cpp/cpp/goto-statement-cpp)
