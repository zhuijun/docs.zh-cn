---
description: break 语句 - C# 参考
title: break 语句 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- break
- break_CSharpKeyword
helpviewer_keywords:
- break keyword [C#]
ms.assetid: be2571ed-efb0-4965-b122-81e5b09db0b9
ms.openlocfilehash: 7fd05889f684f7a2282de8222e1195898dead5b9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134739"
---
# <a name="break-c-reference"></a><span data-ttu-id="13363-103">break（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="13363-103">break (C# Reference)</span></span>

<span data-ttu-id="13363-104">`break` 语句将终止其所在位置的最接近封闭循环或 [switch](./switch.md) 语句。</span><span class="sxs-lookup"><span data-stu-id="13363-104">The `break` statement terminates the closest enclosing loop or [switch](./switch.md) statement in which it appears.</span></span> <span data-ttu-id="13363-105">控制权将传递给已终止语句后面的语句（若有）。</span><span class="sxs-lookup"><span data-stu-id="13363-105">Control is passed to the statement that follows the terminated statement, if any.</span></span>

## <a name="example"></a><span data-ttu-id="13363-106">示例</span><span class="sxs-lookup"><span data-stu-id="13363-106">Example</span></span>

<span data-ttu-id="13363-107">在此示例中，条件语句包含一个应从 1 计数到 100 的计数器；但 `break` 语句在计数器计数到 4 后终止了循环。</span><span class="sxs-lookup"><span data-stu-id="13363-107">In this example, the conditional statement contains a counter that is supposed to count from 1 to 100; however, the `break` statement terminates the loop after 4 counts.</span></span>

[!code-csharp[csrefKeywordsJump#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#1)]

## <a name="example"></a><span data-ttu-id="13363-108">示例</span><span class="sxs-lookup"><span data-stu-id="13363-108">Example</span></span>

<span data-ttu-id="13363-109">本示例演示 `break` 在 [switch](./switch.md) 语句中的用法。</span><span class="sxs-lookup"><span data-stu-id="13363-109">This example demonstrates the use of `break` in a [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#2)]

<span data-ttu-id="13363-110">如果输入 `4`，则输出为：</span><span class="sxs-lookup"><span data-stu-id="13363-110">If you entered `4`, the output would be:</span></span>

```console
Enter your selection (1, 2, or 3): 4
Sorry, invalid selection.
```

## <a name="example"></a><span data-ttu-id="13363-111">示例</span><span class="sxs-lookup"><span data-stu-id="13363-111">Example</span></span>

<span data-ttu-id="13363-112">在此示例中，`break` 语句用于中断内层嵌套循环，并将控制权返回给外层循环。</span><span class="sxs-lookup"><span data-stu-id="13363-112">In this example, the `break` statement is used to break out of an inner nested loop, and return control to the outer loop.</span></span> <span data-ttu-id="13363-113">控件在嵌套循环中仅向上返回一级__。</span><span class="sxs-lookup"><span data-stu-id="13363-113">Control is _only_ returned one level up in the nested loops.</span></span>

[!code-csharp[csrefKeywordsJump#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#7)]

## <a name="example"></a><span data-ttu-id="13363-114">示例</span><span class="sxs-lookup"><span data-stu-id="13363-114">Example</span></span>

<span data-ttu-id="13363-115">在本例中，`break` 语句仅用于在循环的每次迭代中脱离当前分支。</span><span class="sxs-lookup"><span data-stu-id="13363-115">In this example, the `break` statement is only used to break out of the current branch during each iteration of the loop.</span></span> <span data-ttu-id="13363-116">循环本身不受属于嵌套 [switch](./switch.md) 语句的 `break` 实例的影响。</span><span class="sxs-lookup"><span data-stu-id="13363-116">The loop itself is unaffected by the instances of `break` that belong to the nested [switch](./switch.md) statement.</span></span>

[!code-csharp[csrefKeywordsJump#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="13363-117">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="13363-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="13363-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="13363-118">See also</span></span>

- [<span data-ttu-id="13363-119">C# 参考</span><span class="sxs-lookup"><span data-stu-id="13363-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="13363-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="13363-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="13363-121">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="13363-121">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="13363-122">switch</span><span class="sxs-lookup"><span data-stu-id="13363-122">switch</span></span>](./switch.md)
