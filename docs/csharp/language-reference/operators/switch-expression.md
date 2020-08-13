---
title: switch 表达式 - C# 参考
description: 了解如何将 C# switch 表达式用于模式匹配和其他数据自检
ms.date: 03/19/2020
ms.openlocfilehash: 2249afc1ff1cc81e9ad423d910ebb95df8c787d4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916657"
---
# <a name="switch-expression-c-reference"></a><span data-ttu-id="0f1a6-103">switch 表达式（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="0f1a6-103">switch expression (C# reference)</span></span>

<span data-ttu-id="0f1a6-104">本文介绍 C# 8.0 中引入的 `switch` 表达式。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-104">This article covers the `switch` expression, introduced in C# 8.0.</span></span> <span data-ttu-id="0f1a6-105">有关 `switch` 语句的详细信息，请参阅[语句](../keywords/index.md)部分中关于 [`switch` 语句](../keywords/switch.md)的文章。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-105">For information on the `switch` statement, see the article on the [`switch` statement](../keywords/switch.md) in the [statements](../keywords/index.md) section.</span></span>

## <a name="basic-example"></a><span data-ttu-id="0f1a6-106">基本示例</span><span class="sxs-lookup"><span data-stu-id="0f1a6-106">Basic example</span></span>

<span data-ttu-id="0f1a6-107">`switch` 表达式在表达式上下文中提供与 `switch` 类似的语义。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-107">The `switch` expression provides for `switch`-like semantics in an expression context.</span></span> <span data-ttu-id="0f1a6-108">当 switch arm 生成值时，它提供简洁的语法。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-108">It provides a concise syntax when the switch arms produce a value.</span></span> <span data-ttu-id="0f1a6-109">下面的示例显示了 switch 表达式的结构。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-109">The following example shows the structure of a switch expression.</span></span> <span data-ttu-id="0f1a6-110">它将联机地图中表示视觉方向的 `enum` 中的值转换为相应的基本方位：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-110">It translates values from an `enum` representing visual directions in an online map to the corresponding cardinal direction:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetBasicStructure":::

<span data-ttu-id="0f1a6-111">前面的示例展示了 switch 表达式的基本元素：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-111">The preceding sample shows the basic elements of a switch expression:</span></span>

- <span data-ttu-id="0f1a6-112">*范围表达式*：前面的示例使用变量 `direction` 作为范围表达式。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-112">The *range expression*: The preceding example uses the variable `direction` as the range expression.</span></span>
- <span data-ttu-id="0f1a6-113">*switch expression arm*：每个 switch expression arm 都包含一个模式、  一个可选的 case guard  、`=>` 标记和一个表达式  。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-113">The *switch expression arms*: Each switch expression arm contains a *pattern*, an optional *case guard*, the `=>` token, and an *expression*.</span></span>

<span data-ttu-id="0f1a6-114">switch 表达式  的结果是第一个 switch expression arm  的表达式的值，该 switch expression arm 的模式  与范围表达式  匹配，并且它的 case guard  （如果存在）求值为 `true`。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-114">The result of the *switch expression* is the value of the expression of the first *switch expression arm* whose *pattern* matches the *range expression* and whose *case guard*, if present, evaluates to `true`.</span></span> <span data-ttu-id="0f1a6-115">`=>` 标记右侧的表达式不能是表达式语句。 </span><span class="sxs-lookup"><span data-stu-id="0f1a6-115">The *expression* on the right of the `=>` token can't be an expression statement.</span></span>

<span data-ttu-id="0f1a6-116">switch expression arm  按文本顺序求值。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-116">The *switch expression arms* are evaluated in text order.</span></span> <span data-ttu-id="0f1a6-117">如果无法选择较低的 switch expression arm  ，编译器会发出错误，因为较高的 switch expression arm  匹配其所有值。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-117">The compiler issues an error when a lower *switch expression arm* can't be chosen because a higher *switch expression arm* matches all its values.</span></span>

## <a name="patterns-and-case-guards"></a><span data-ttu-id="0f1a6-118">模式和 case guard</span><span class="sxs-lookup"><span data-stu-id="0f1a6-118">Patterns and case guards</span></span>

<span data-ttu-id="0f1a6-119">switch expression arm 支持许多模式。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-119">Many patterns are supported in switch expression arms.</span></span> <span data-ttu-id="0f1a6-120">前面的示例使用常量模式。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-120">The preceding example uses a *constant pattern*.</span></span> <span data-ttu-id="0f1a6-121">常量模式将范围表达式与一个值进行比较。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-121">A *constant pattern* compares the range expression to a value.</span></span> <span data-ttu-id="0f1a6-122">该值必须是编译时常量。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-122">That value must be a compile-time constant.</span></span> <span data-ttu-id="0f1a6-123">类型模式  将范围表达式与已知类型进行比较。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-123">The *type pattern* compares the range expression to a known type.</span></span> <span data-ttu-id="0f1a6-124">下面的示例从序列中检索第三个元素。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-124">The following example retrieves the third element from a sequence.</span></span> <span data-ttu-id="0f1a6-125">它使用基于序列类型的不同方法：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-125">It uses different methods based on the type of the sequence:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetTypePattern":::

<span data-ttu-id="0f1a6-126">模式可以是递归模式，其中模式会测试一个类型，如果该类型匹配，则该模式将匹配范围表达式上的一个或多个属性值。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-126">Patterns can be recursive, where a pattern tests a type, and if that type matches, the pattern matches one or more property values on the range expression.</span></span> <span data-ttu-id="0f1a6-127">可以使用递归模式来扩展前面的示例。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-127">You can use recursive patterns to extend the preceding example.</span></span> <span data-ttu-id="0f1a6-128">为包含少于 3 个元素的数组添加 switch expression arm。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-128">You add switch expression arms for arrays that have fewer than 3 elements.</span></span> <span data-ttu-id="0f1a6-129">下面的示例演示了递归模式：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-129">Recursive patterns are shown in the following example:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetRecursivePattern":::

<span data-ttu-id="0f1a6-130">递归模式可以检查范围表达式的属性，但不能执行任意代码。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-130">Recursive patterns can examine properties of the range expression, but can't execute arbitrary code.</span></span> <span data-ttu-id="0f1a6-131">你可以使用 `when` 子句中指定的 case guard  为其他序列类型提供类似的检查：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-131">You can use a *case guard*, specified in a `when` clause, to provide similar checks for other sequence types:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetGuardCase":::

<span data-ttu-id="0f1a6-132">最后，可以添加 `_` 模式和 `null` 模式，以捕获不由任何其他 switch expression arm 处理的参数。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-132">Finally, you can add the `_` pattern and the `null` pattern to catch arguments that aren't processed by any other switch expression arm.</span></span> <span data-ttu-id="0f1a6-133">这会使 switch 表达式穷尽  ，这意味着将处理范围表达式的任何可能的值。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-133">That makes the switch expression *exhaustive*, meaning any possible value of the range expression is handled.</span></span> <span data-ttu-id="0f1a6-134">下面的示例添加了这些 expression arm：</span><span class="sxs-lookup"><span data-stu-id="0f1a6-134">The following example adds those expression arms:</span></span>

:::code language="csharp" source="snippets/shared/SwitchExpressions.cs" id="SnippetExhaustive":::

<span data-ttu-id="0f1a6-135">前面的示例添加了 `null` 模式，并将 `IEnumerable<T>` 类型模式更改为 `_` 模式。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-135">The preceding example adds a `null` pattern, and changes the `IEnumerable<T>` type pattern to a `_` pattern.</span></span> <span data-ttu-id="0f1a6-136">`null` 模式提供 null 检查作为 switch expression arm。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-136">The `null` pattern provides a null check as a switch expression arm.</span></span> <span data-ttu-id="0f1a6-137">该 arm 的表达式引发 <xref:System.ArgumentNullException>。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-137">The expression for that arm throws an <xref:System.ArgumentNullException>.</span></span> <span data-ttu-id="0f1a6-138">`_` 模式与先前的 arm 未匹配的所有输入相匹配。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-138">The `_` pattern matches all inputs that haven't been matched by previous arms.</span></span> <span data-ttu-id="0f1a6-139">它必须在 `null` 检查之后执行，否则将与 `null` 输入匹配。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-139">It must come after the `null` check, or it would match `null` inputs.</span></span>

<span data-ttu-id="0f1a6-140">可以参阅 C# 语言规范建议，了解有关[递归模式](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression)的详细信息。</span><span class="sxs-lookup"><span data-stu-id="0f1a6-140">You can read more in the C# language spec proposal for [recursive patterns](~/_csharplang/proposals/csharp-8.0/patterns.md#switch-expression).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f1a6-141">请参阅</span><span class="sxs-lookup"><span data-stu-id="0f1a6-141">See also</span></span>

- [<span data-ttu-id="0f1a6-142">C# 参考</span><span class="sxs-lookup"><span data-stu-id="0f1a6-142">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0f1a6-143">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="0f1a6-143">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="0f1a6-144">模式匹配</span><span class="sxs-lookup"><span data-stu-id="0f1a6-144">Pattern matching</span></span>](../../pattern-matching.md)
