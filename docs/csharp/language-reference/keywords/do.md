---
description: do - C# 参考
title: do - C# 参考
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 601231f23a58e8af8339a733677f0bbd92bb4ffc
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89126952"
---
# <a name="do-c-reference"></a><span data-ttu-id="36d61-103">do（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="36d61-103">do (C# Reference)</span></span>

<span data-ttu-id="36d61-104">在指定的布尔表达式的计算结果为 `true` 时，`do` 语句会执行一条语句或一个语句块。</span><span class="sxs-lookup"><span data-stu-id="36d61-104">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="36d61-105">由于在每次执行循环之后都会计算此表达式，所以 `do-while` 循环会执行一次或多次。</span><span class="sxs-lookup"><span data-stu-id="36d61-105">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="36d61-106">这不同于 [while](while.md) 循环（该循环执行零次或多次）。</span><span class="sxs-lookup"><span data-stu-id="36d61-106">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="36d61-107">在 `do` 语句块中的任何点，都可使用 [break](break.md) 语句中断循环。</span><span class="sxs-lookup"><span data-stu-id="36d61-107">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="36d61-108">可通过使用 [continue](continue.md) 语句直接步入 `while` 表达式的计算部分。</span><span class="sxs-lookup"><span data-stu-id="36d61-108">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="36d61-109">如果表达式计算结果为 `true`，则继续执行循环中的第一个语句。</span><span class="sxs-lookup"><span data-stu-id="36d61-109">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="36d61-110">否则，将在循环后的第一个语句处继续执行。</span><span class="sxs-lookup"><span data-stu-id="36d61-110">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="36d61-111">还可以使用 [goto](goto.md)、[return](return.md) 或 [throw](throw.md) 语句退出 `do-while` 循环。</span><span class="sxs-lookup"><span data-stu-id="36d61-111">You can also exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="36d61-112">示例</span><span class="sxs-lookup"><span data-stu-id="36d61-112">Example</span></span>

<span data-ttu-id="36d61-113">下面的示例演示 `do` 语句的用法。</span><span class="sxs-lookup"><span data-stu-id="36d61-113">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="36d61-114">选择“运行”以运行示例代码  。</span><span class="sxs-lookup"><span data-stu-id="36d61-114">Select **Run** to run the example code.</span></span> <span data-ttu-id="36d61-115">然后可以修改代码并再次运行它。</span><span class="sxs-lookup"><span data-stu-id="36d61-115">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](snippets/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="36d61-116">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="36d61-116">C# language specification</span></span>

<span data-ttu-id="36d61-117">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的 [do 语句](~/_csharplang/spec/statements.md#the-do-statement)部分。</span><span class="sxs-lookup"><span data-stu-id="36d61-117">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="36d61-118">请参阅</span><span class="sxs-lookup"><span data-stu-id="36d61-118">See also</span></span>

- [<span data-ttu-id="36d61-119">C# 参考</span><span class="sxs-lookup"><span data-stu-id="36d61-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="36d61-120">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="36d61-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="36d61-121">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="36d61-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="36d61-122">while 语句</span><span class="sxs-lookup"><span data-stu-id="36d61-122">while statement</span></span>](while.md)
