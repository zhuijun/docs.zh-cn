---
description: continue 语句 - C# 参考
title: continue 语句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- continue_CSharpKeyword
- continue
helpviewer_keywords:
- continue keyword [C#]
ms.assetid: 8a5ac96f-f98a-4519-b32d-345847ed7be0
ms.openlocfilehash: 76578b0ad7e2b969609fbf50df1f9ab7de6e5097
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128434"
---
# <a name="continue-c-reference"></a><span data-ttu-id="e2fa0-103">continue（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="e2fa0-103">continue (C# Reference)</span></span>

<span data-ttu-id="e2fa0-104">`continue` 语句将控制传递到其中出现的封闭 [while](./while.md)、[do](./do.md)、[for](./for.md) 或 [foreach](./foreach-in.md) 语句的下一次迭代。</span><span class="sxs-lookup"><span data-stu-id="e2fa0-104">The `continue` statement passes control to the next iteration of the enclosing [while](./while.md), [do](./do.md), [for](./for.md), or [foreach](./foreach-in.md) statement in which it appears.</span></span>

## <a name="example"></a><span data-ttu-id="e2fa0-105">示例</span><span class="sxs-lookup"><span data-stu-id="e2fa0-105">Example</span></span>

<span data-ttu-id="e2fa0-106">在本示例中，计数器最初是从 1 到 10 进行计数。</span><span class="sxs-lookup"><span data-stu-id="e2fa0-106">In this example, a counter is initialized to count from 1 to 10.</span></span> <span data-ttu-id="e2fa0-107">通过结合使用 `continue` 语句和表达式 `(i < 9)`，跳过 `continue` 和 `for` 主体末尾之间的语句。</span><span class="sxs-lookup"><span data-stu-id="e2fa0-107">By using the `continue` statement in conjunction with the expression `(i < 9)`, the statements between `continue` and the end of the `for` body are skipped.</span></span>

[!code-csharp[csrefKeywordsJump#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#3)]

## <a name="c-language-specification"></a><span data-ttu-id="e2fa0-108">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="e2fa0-108">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e2fa0-109">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2fa0-109">See also</span></span>

- [<span data-ttu-id="e2fa0-110">C# 参考</span><span class="sxs-lookup"><span data-stu-id="e2fa0-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e2fa0-111">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e2fa0-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2fa0-112">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="e2fa0-112">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e2fa0-113">break 语句</span><span class="sxs-lookup"><span data-stu-id="e2fa0-113">break Statement</span></span>](/cpp/cpp/break-statement-cpp)
