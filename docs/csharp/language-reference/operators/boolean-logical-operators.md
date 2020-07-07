---
title: 布尔逻辑运算符 - C# 参考
description: 了解使用布尔操作数执行逻辑非、逻辑与、逻辑或和逻辑异或运算的 C# 运算符。
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: a19c804c624153ef608885bc6493537302275765
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618189"
---
# <a name="boolean-logical-operators-c-reference"></a><span data-ttu-id="fd6df-103">布尔逻辑运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="fd6df-103">Boolean logical operators (C# reference)</span></span>

<span data-ttu-id="fd6df-104">以下运算符使用 [bool](../builtin-types/bool.md) 操作数执行逻辑运算：</span><span class="sxs-lookup"><span data-stu-id="fd6df-104">The following operators perform logical operations with [bool](../builtin-types/bool.md) operands:</span></span>

- <span data-ttu-id="fd6df-105">一元 [`!`（逻辑非）](#logical-negation-operator-)运算符。</span><span class="sxs-lookup"><span data-stu-id="fd6df-105">Unary [`!` (logical negation)](#logical-negation-operator-) operator.</span></span>
- <span data-ttu-id="fd6df-106">二元 [`&`（逻辑与）](#logical-and-operator-)、[`|`（逻辑或）](#logical-or-operator-)和 [`^`（逻辑异或）](#logical-exclusive-or-operator-)运算符。</span><span class="sxs-lookup"><span data-stu-id="fd6df-106">Binary [`&` (logical AND)](#logical-and-operator-), [`|` (logical OR)](#logical-or-operator-), and [`^` (logical exclusive OR)](#logical-exclusive-or-operator-) operators.</span></span> <span data-ttu-id="fd6df-107">这些运算符始终计算两个操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-107">Those operators always evaluate both operands.</span></span>
- <span data-ttu-id="fd6df-108">二元 [`&&`（条件逻辑与）](#conditional-logical-and-operator-)和 [`||`（条件逻辑或）](#conditional-logical-or-operator-)运算符。</span><span class="sxs-lookup"><span data-stu-id="fd6df-108">Binary [`&&` (conditional logical AND)](#conditional-logical-and-operator-) and [`||` (conditional logical OR)](#conditional-logical-or-operator-) operators.</span></span> <span data-ttu-id="fd6df-109">这些运算符仅在必要时才计算右侧操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-109">Those operators evaluate the right-hand operand only if it's necessary.</span></span>

<span data-ttu-id="fd6df-110">对于[整型数值类型](../builtin-types/integral-numeric-types.md)的操作数，`&`、`|` 和 `^` 运算符执行位逻辑运算。</span><span class="sxs-lookup"><span data-stu-id="fd6df-110">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&`, `|`, and `^` operators perform bitwise logical operations.</span></span> <span data-ttu-id="fd6df-111">有关详细信息，请参阅[位运算符和移位运算符](bitwise-and-shift-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-111">For more information, see [Bitwise and shift operators](bitwise-and-shift-operators.md).</span></span>

## <a name="logical-negation-operator-"></a><span data-ttu-id="fd6df-112">逻辑非运算符 !</span><span class="sxs-lookup"><span data-stu-id="fd6df-112">Logical negation operator !</span></span>

<span data-ttu-id="fd6df-113">一元前缀 `!` 运算符计算操作数的逻辑非。</span><span class="sxs-lookup"><span data-stu-id="fd6df-113">The unary prefix `!` operator computes logical negation of its operand.</span></span> <span data-ttu-id="fd6df-114">也就是说，如果操作数的计算结果为 `false`，它生成 `true`；如果操作数的计算结果为 `true`，它生成 `false`：</span><span class="sxs-lookup"><span data-stu-id="fd6df-114">That is, it produces `true`, if the operand evaluates to `false`, and `false`, if the operand evaluates to `true`:</span></span>

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

<span data-ttu-id="fd6df-115">从 C# 8.0 起，一元后缀 `!` 运算符为 [null 包容运算符](null-forgiving.md)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-115">Beginning with C# 8.0, the unary postfix `!` operator is the [null-forgiving operator](null-forgiving.md).</span></span>

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a> <span data-ttu-id="fd6df-116">逻辑 AND 运算符 &amp;</span><span class="sxs-lookup"><span data-stu-id="fd6df-116">Logical AND operator &amp;</span></span>

<span data-ttu-id="fd6df-117">`&` 运算符计算操作数的逻辑与。</span><span class="sxs-lookup"><span data-stu-id="fd6df-117">The `&` operator computes the logical AND of its operands.</span></span> <span data-ttu-id="fd6df-118">如果 `x` 和 `y` 的计算结果都为 `true`，则 `x & y` 的结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-118">The result of `x & y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="fd6df-119">否则，结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-119">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="fd6df-120">即使左侧操作数计算结果为 `false`，`&` 运算符也会计算这两个操作数，而在这种情况下，无论右侧操作数的值为何，运算结果都为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-120">The `&` operator evaluates both operands even if the left-hand operand evaluates to `false`, so that the operation result is `false` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="fd6df-121">在下面的示例中，`&` 运算符的右侧操作数是方法调用，无论左侧操作数的值如何，都会执行方法调用：</span><span class="sxs-lookup"><span data-stu-id="fd6df-121">In the following example, the right-hand operand of the `&` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

<span data-ttu-id="fd6df-122">[条件逻辑 AND 运算符](#conditional-logical-and-operator-) `&&` 也计算操作数的逻辑 AND，但如果左侧操作数的计算结果为 `false`，它就不会计算右侧操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-122">The [conditional logical AND operator](#conditional-logical-and-operator-) `&&` also computes the logical AND of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `false`.</span></span>

<span data-ttu-id="fd6df-123">对于[整型数值类型](../builtin-types/integral-numeric-types.md)的操作数，`&` 运算符计算其操作数的[位逻辑 AND](bitwise-and-shift-operators.md#logical-and-operator-)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-123">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `&` operator computes the [bitwise logical AND](bitwise-and-shift-operators.md#logical-and-operator-) of its operands.</span></span> <span data-ttu-id="fd6df-124">一元 `&` 运算符是 [address-of 运算符](pointer-related-operators.md#address-of-operator-)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-124">The unary `&` operator is the [address-of operator](pointer-related-operators.md#address-of-operator-).</span></span>

## <a name="logical-exclusive-or-operator-"></a><span data-ttu-id="fd6df-125">逻辑异或运算符 ^</span><span class="sxs-lookup"><span data-stu-id="fd6df-125">Logical exclusive OR operator ^</span></span>

<span data-ttu-id="fd6df-126">`^` 运算符计算操作数的逻辑异或（亦称为“逻辑 XOR”）。</span><span class="sxs-lookup"><span data-stu-id="fd6df-126">The `^` operator computes the logical exclusive OR, also known as the logical XOR, of its operands.</span></span> <span data-ttu-id="fd6df-127">如果 `x` 计算结果为 `true` 且 `y` 计算结果为 `false`，或者 `x` 计算结果为 `false` 且 `y` 计算结果为 `true`，那么 `x ^ y` 的结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-127">The result of `x ^ y` is `true` if `x` evaluates to `true` and `y` evaluates to `false`, or `x` evaluates to `false` and `y` evaluates to `true`.</span></span> <span data-ttu-id="fd6df-128">否则，结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-128">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fd6df-129">也就是说，对于 `bool` 操作数，`^` 运算符的计算结果与[不等运算符](equality-operators.md#inequality-operator-) `!=` 相同。</span><span class="sxs-lookup"><span data-stu-id="fd6df-129">That is, for the `bool` operands, the `^` operator computes the same result as the [inequality operator](equality-operators.md#inequality-operator-) `!=`.</span></span>

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

<span data-ttu-id="fd6df-130">对于[整型数值类型](../builtin-types/integral-numeric-types.md)的操作数，`^` 运算符计算其操作数的[位逻辑异或](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-130">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `^` operator computes the [bitwise logical exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) of its operands.</span></span>

## <a name="logical-or-operator-"></a><span data-ttu-id="fd6df-131">逻辑或运算符 |</span><span class="sxs-lookup"><span data-stu-id="fd6df-131">Logical OR operator |</span></span>

<span data-ttu-id="fd6df-132">`|` 运算符计算操作数的逻辑或。</span><span class="sxs-lookup"><span data-stu-id="fd6df-132">The `|` operator computes the logical OR of its operands.</span></span> <span data-ttu-id="fd6df-133">如果 `x` 或 `y` 的计算结果为 `true`，则 `x | y` 的结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-133">The result of `x | y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="fd6df-134">否则，结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-134">Otherwise, the result is `false`.</span></span>

<span data-ttu-id="fd6df-135">即使左侧操作数计算结果为 `true`，`|` 运算符也会计算这两个操作数，而在这种情况下，无论右侧操作数的值为何，运算结果都为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-135">The `|` operator evaluates both operands even if the left-hand operand evaluates to `true`, so that the operation result is `true` regardless of the value of the right-hand operand.</span></span>

<span data-ttu-id="fd6df-136">在下面的示例中，`|` 运算符的右侧操作数是方法调用，无论左侧操作数的值如何，都会执行方法调用：</span><span class="sxs-lookup"><span data-stu-id="fd6df-136">In the following example, the right-hand operand of the `|` operator is a method call, which is performed regardless of the value of the left-hand operand:</span></span>

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

<span data-ttu-id="fd6df-137">[条件逻辑 OR 运算符](#conditional-logical-or-operator-) `||` 也计算操作数的逻辑 OR，但如果左侧操作数的计算结果为 `true`，它就不会计算右侧操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-137">The [conditional logical OR operator](#conditional-logical-or-operator-) `||` also computes the logical OR of its operands, but doesn't evaluate the right-hand operand if the left-hand operand evaluates to `true`.</span></span>

<span data-ttu-id="fd6df-138">对于[整型数值类型](../builtin-types/integral-numeric-types.md)的操作数，`|` 运算符计算其操作数的[位逻辑 OR](bitwise-and-shift-operators.md#logical-or-operator-)。</span><span class="sxs-lookup"><span data-stu-id="fd6df-138">For operands of the [integral numeric types](../builtin-types/integral-numeric-types.md), the `|` operator computes the [bitwise logical OR](bitwise-and-shift-operators.md#logical-or-operator-) of its operands.</span></span>

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a> <span data-ttu-id="fd6df-139">条件逻辑 AND 运算符 &amp;&amp;</span><span class="sxs-lookup"><span data-stu-id="fd6df-139">Conditional logical AND operator &amp;&amp;</span></span>

<span data-ttu-id="fd6df-140">条件逻辑与运算符 `&&`（亦称为“短路”逻辑与运算符）计算操作数的逻辑与。</span><span class="sxs-lookup"><span data-stu-id="fd6df-140">The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator, computes the logical AND of its operands.</span></span> <span data-ttu-id="fd6df-141">如果 `x` 和 `y` 的计算结果都为 `true`，则 `x && y` 的结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-141">The result of `x && y` is `true` if both `x` and `y` evaluate to `true`.</span></span> <span data-ttu-id="fd6df-142">否则，结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-142">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fd6df-143">如果 `x` 的计算结果为 `false`，则不计算 `y`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-143">If `x` evaluates to `false`, `y` is not evaluated.</span></span>

<span data-ttu-id="fd6df-144">在下面的示例中，`&&` 运算符的右侧操作数是方法调用，如果左侧操作数的计算结果为 `false`，就不执行方法调用：</span><span class="sxs-lookup"><span data-stu-id="fd6df-144">In the following example, the right-hand operand of the `&&` operator is a method call, which isn't performed if the left-hand operand evaluates to `false`:</span></span>

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

<span data-ttu-id="fd6df-145">[逻辑 AND 运算符](#logical-and-operator-) `&` 也计算操作数的逻辑 AND，但始终计算两个操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-145">The [logical AND operator](#logical-and-operator-) `&` also computes the logical AND of its operands, but always evaluates both operands.</span></span>

## <a name="conditional-logical-or-operator-"></a><span data-ttu-id="fd6df-146">条件逻辑或运算符 ||</span><span class="sxs-lookup"><span data-stu-id="fd6df-146">Conditional logical OR operator ||</span></span>

<span data-ttu-id="fd6df-147">条件逻辑或运算符 `||`（亦称为“短路”逻辑或运算符）计算操作数的逻辑或。</span><span class="sxs-lookup"><span data-stu-id="fd6df-147">The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator, computes the logical OR of its operands.</span></span> <span data-ttu-id="fd6df-148">如果 `x` 或 `y` 的计算结果为 `true`，则 `x || y` 的结果为 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-148">The result of `x || y` is `true` if either `x` or `y` evaluates to `true`.</span></span> <span data-ttu-id="fd6df-149">否则，结果为 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-149">Otherwise, the result is `false`.</span></span> <span data-ttu-id="fd6df-150">如果 `x` 的计算结果为 `true`，则不计算 `y`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-150">If `x` evaluates to `true`, `y` is not evaluated.</span></span>

<span data-ttu-id="fd6df-151">在下面的示例中，`||` 运算符的右侧操作数是方法调用，如果左侧操作数的计算结果为 `true`，就不执行方法调用：</span><span class="sxs-lookup"><span data-stu-id="fd6df-151">In the following example, the right-hand operand of the `||` operator is a method call, which isn't performed if the left-hand operand evaluates to `true`:</span></span>

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

<span data-ttu-id="fd6df-152">[逻辑 OR 运算符](#logical-or-operator-) `|` 也计算操作数的逻辑 OR，但始终计算两个操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-152">The [logical OR operator](#logical-or-operator-) `|` also computes the logical OR of its operands, but always evaluates both operands.</span></span>

## <a name="nullable-boolean-logical-operators"></a><span data-ttu-id="fd6df-153">可以为 null 的布尔逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-153">Nullable Boolean logical operators</span></span>

<span data-ttu-id="fd6df-154">对于 `bool?` 操作数，[`&`（逻辑与）](#logical-and-operator-)和 [`|`（逻辑或）](#logical-or-operator-)运算符支持三值逻辑，如下所示：</span><span class="sxs-lookup"><span data-stu-id="fd6df-154">For `bool?` operands, the [`&` (logical AND)](#logical-and-operator-) and [`|` (logical OR)](#logical-or-operator-) operators support the three-valued logic as follows:</span></span>

- <span data-ttu-id="fd6df-155">仅当其两个操作数的计算结果都为 `true` 时，`&` 运算符才生成 `true`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-155">The `&` operator produces `true` only if both its operands evaluate to `true`.</span></span> <span data-ttu-id="fd6df-156">如果 `x` 或 `y` 的计算结果为 `false`，则 `x & y` 将生成 `false`（即使另一个操作数的计算结果为 `null`）。</span><span class="sxs-lookup"><span data-stu-id="fd6df-156">If either `x` or `y` evaluates to `false`, `x & y` produces `false` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="fd6df-157">否则，`x & y` 的结果为 `null`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-157">Otherwise, the result of `x & y` is `null`.</span></span>

- <span data-ttu-id="fd6df-158">仅当其两个操作数的计算结果都为 `false` 时，`|` 运算符才生成 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-158">The `|` operator produces `false` only if both its operands evaluate to `false`.</span></span> <span data-ttu-id="fd6df-159">如果 `x` 或 `y` 的计算结果为 `true`，则 `x | y` 将生成 `true`（即使另一个操作数的计算结果为 `null`）。</span><span class="sxs-lookup"><span data-stu-id="fd6df-159">If either `x` or `y` evaluates to `true`, `x | y` produces `true` (even if another operand evaluates to `null`).</span></span> <span data-ttu-id="fd6df-160">否则，`x | y` 的结果为 `null`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-160">Otherwise, the result of `x | y` is `null`.</span></span>

<span data-ttu-id="fd6df-161">下表显示了该语义：</span><span class="sxs-lookup"><span data-stu-id="fd6df-161">The following table presents that semantics:</span></span>

|<span data-ttu-id="fd6df-162">x</span><span class="sxs-lookup"><span data-stu-id="fd6df-162">x</span></span>|<span data-ttu-id="fd6df-163">y</span><span class="sxs-lookup"><span data-stu-id="fd6df-163">y</span></span>|<span data-ttu-id="fd6df-164">x 和 y</span><span class="sxs-lookup"><span data-stu-id="fd6df-164">x&y</span></span>|<span data-ttu-id="fd6df-165">x&#124;y</span><span class="sxs-lookup"><span data-stu-id="fd6df-165">x&#124;y</span></span>|  
|----|----|----|----|  
|<span data-ttu-id="fd6df-166">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-166">true</span></span>|<span data-ttu-id="fd6df-167">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-167">true</span></span>|<span data-ttu-id="fd6df-168">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-168">true</span></span>|<span data-ttu-id="fd6df-169">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-169">true</span></span>|  
|<span data-ttu-id="fd6df-170">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-170">true</span></span>|<span data-ttu-id="fd6df-171">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-171">false</span></span>|<span data-ttu-id="fd6df-172">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-172">false</span></span>|<span data-ttu-id="fd6df-173">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-173">true</span></span>|  
|<span data-ttu-id="fd6df-174">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-174">true</span></span>|<span data-ttu-id="fd6df-175">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-175">null</span></span>|<span data-ttu-id="fd6df-176">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-176">null</span></span>|<span data-ttu-id="fd6df-177">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-177">true</span></span>|  
|<span data-ttu-id="fd6df-178">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-178">false</span></span>|<span data-ttu-id="fd6df-179">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-179">true</span></span>|<span data-ttu-id="fd6df-180">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-180">false</span></span>|<span data-ttu-id="fd6df-181">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-181">true</span></span>|  
|<span data-ttu-id="fd6df-182">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-182">false</span></span>|<span data-ttu-id="fd6df-183">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-183">false</span></span>|<span data-ttu-id="fd6df-184">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-184">false</span></span>|<span data-ttu-id="fd6df-185">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-185">false</span></span>|  
|<span data-ttu-id="fd6df-186">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-186">false</span></span>|<span data-ttu-id="fd6df-187">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-187">null</span></span>|<span data-ttu-id="fd6df-188">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-188">false</span></span>|<span data-ttu-id="fd6df-189">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-189">null</span></span>|  
|<span data-ttu-id="fd6df-190">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-190">null</span></span>|<span data-ttu-id="fd6df-191">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-191">true</span></span>|<span data-ttu-id="fd6df-192">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-192">null</span></span>|<span data-ttu-id="fd6df-193">true</span><span class="sxs-lookup"><span data-stu-id="fd6df-193">true</span></span>|  
|<span data-ttu-id="fd6df-194">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-194">null</span></span>|<span data-ttu-id="fd6df-195">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-195">false</span></span>|<span data-ttu-id="fd6df-196">false</span><span class="sxs-lookup"><span data-stu-id="fd6df-196">false</span></span>|<span data-ttu-id="fd6df-197">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-197">null</span></span>|  
|<span data-ttu-id="fd6df-198">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-198">null</span></span>|<span data-ttu-id="fd6df-199">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-199">null</span></span>|<span data-ttu-id="fd6df-200">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-200">null</span></span>|<span data-ttu-id="fd6df-201">null</span><span class="sxs-lookup"><span data-stu-id="fd6df-201">null</span></span>|  

<span data-ttu-id="fd6df-202">这些运算符的行为不同于值类型可以为 null 的典型运算符行为。</span><span class="sxs-lookup"><span data-stu-id="fd6df-202">The behavior of those operators differs from the typical operator behavior with nullable value types.</span></span> <span data-ttu-id="fd6df-203">通常情况下，为值类型的操作数定义的运算符也能与值类型可以为 null 的相应操作数一起使用。</span><span class="sxs-lookup"><span data-stu-id="fd6df-203">Typically, an operator which is defined for operands of a value type can be also used with operands of the corresponding nullable value type.</span></span> <span data-ttu-id="fd6df-204">如果其任一操作数的计算结果为 `null`，此类运算符都会生成 `null`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-204">Such an operator produces `null` if any of its operands evaluates to `null`.</span></span> <span data-ttu-id="fd6df-205">不过，即使操作数之一的计算结果为 `null`，`&` 和 `|` 运算符也可以生成非 null。</span><span class="sxs-lookup"><span data-stu-id="fd6df-205">However, the `&` and `|` operators can produce non-null even if one of the operands evaluates to `null`.</span></span> <span data-ttu-id="fd6df-206">有关值类型可为空的运算符行为的详细信息，请参阅[可为空的值类型](../builtin-types/nullable-value-types.md)一文的[提升的运算符](../builtin-types/nullable-value-types.md#lifted-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="fd6df-206">For more information about the operator behavior with nullable value types, see the [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) section of the [Nullable value types](../builtin-types/nullable-value-types.md) article.</span></span>

<span data-ttu-id="fd6df-207">此外，你还可以将 `!` 和 `^` 运算符与 `bool?` 操作数结合使用，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="fd6df-207">You can also use the `!` and `^` operators with `bool?` operands, as the following example shows:</span></span>

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

<span data-ttu-id="fd6df-208">条件逻辑运算符 `&&` 和 `||` 不支持 `bool?` 操作数。</span><span class="sxs-lookup"><span data-stu-id="fd6df-208">The conditional logical operators `&&` and `||` don't support `bool?` operands.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="fd6df-209">复合赋值</span><span class="sxs-lookup"><span data-stu-id="fd6df-209">Compound assignment</span></span>

<span data-ttu-id="fd6df-210">对于二元运算符 `op`，窗体的复合赋值表达式</span><span class="sxs-lookup"><span data-stu-id="fd6df-210">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="fd6df-211">等效于</span><span class="sxs-lookup"><span data-stu-id="fd6df-211">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="fd6df-212">不同的是 `x` 只计算一次。</span><span class="sxs-lookup"><span data-stu-id="fd6df-212">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="fd6df-213">`&`、`|` 和 `^` 运算符支持复合赋值，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="fd6df-213">The `&`, `|`, and `^` operators support compound assignment, as the following example shows:</span></span>

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> <span data-ttu-id="fd6df-214">条件逻辑运算符 `&&` 和 `||` 不支持复合赋值。</span><span class="sxs-lookup"><span data-stu-id="fd6df-214">The conditional logical operators `&&` and `||` don't support compound assignment.</span></span>

## <a name="operator-precedence"></a><span data-ttu-id="fd6df-215">运算符优先级</span><span class="sxs-lookup"><span data-stu-id="fd6df-215">Operator precedence</span></span>

<span data-ttu-id="fd6df-216">以下列表按优先级从高到低的顺序对逻辑运算符进行排序：</span><span class="sxs-lookup"><span data-stu-id="fd6df-216">The following list orders logical operators starting from the highest precedence to the lowest:</span></span>

- <span data-ttu-id="fd6df-217">逻辑非运算符 `!`</span><span class="sxs-lookup"><span data-stu-id="fd6df-217">Logical negation operator `!`</span></span>
- <span data-ttu-id="fd6df-218">逻辑与运算符 `&`</span><span class="sxs-lookup"><span data-stu-id="fd6df-218">Logical AND operator `&`</span></span>
- <span data-ttu-id="fd6df-219">逻辑异或运算符 `^`</span><span class="sxs-lookup"><span data-stu-id="fd6df-219">Logical exclusive OR operator `^`</span></span>
- <span data-ttu-id="fd6df-220">逻辑或运算符 `|`</span><span class="sxs-lookup"><span data-stu-id="fd6df-220">Logical OR operator `|`</span></span>
- <span data-ttu-id="fd6df-221">条件逻辑与运算符 `&&`</span><span class="sxs-lookup"><span data-stu-id="fd6df-221">Conditional logical AND operator `&&`</span></span>
- <span data-ttu-id="fd6df-222">条件逻辑或运算符 `||`</span><span class="sxs-lookup"><span data-stu-id="fd6df-222">Conditional logical OR operator `||`</span></span>

<span data-ttu-id="fd6df-223">使用括号 `()` 可以更改运算符优先级决定的计算顺序：</span><span class="sxs-lookup"><span data-stu-id="fd6df-223">Use parentheses, `()`, to change the order of evaluation imposed by operator precedence:</span></span>

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

<span data-ttu-id="fd6df-224">要了解按优先级排序的完整 C# 运算符列表，请参阅 [C# 运算符](index.md#operator-precedence)一文中的[运算符优先级](index.md)部分。</span><span class="sxs-lookup"><span data-stu-id="fd6df-224">For the complete list of C# operators ordered by precedence level, see the [Operator precedence](index.md#operator-precedence) section of the [C# operators](index.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="fd6df-225">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="fd6df-225">Operator overloadability</span></span>

<span data-ttu-id="fd6df-226">用户定义类型可以[重载](operator-overloading.md)`!`、`&`、`|` 和 `^` 运算符。</span><span class="sxs-lookup"><span data-stu-id="fd6df-226">A user-defined type can [overload](operator-overloading.md) the `!`, `&`, `|`, and `^` operators.</span></span> <span data-ttu-id="fd6df-227">重载二元运算符时，对应的复合赋值运算符也会隐式重载。</span><span class="sxs-lookup"><span data-stu-id="fd6df-227">When a binary operator is overloaded, the corresponding compound assignment operator is also implicitly overloaded.</span></span> <span data-ttu-id="fd6df-228">用户定义类型不能显式重载复合赋值运算符。</span><span class="sxs-lookup"><span data-stu-id="fd6df-228">A user-defined type cannot explicitly overload a compound assignment operator.</span></span>

<span data-ttu-id="fd6df-229">用户定义类型无法重载条件逻辑运算符 `&&` 和 `||`。</span><span class="sxs-lookup"><span data-stu-id="fd6df-229">A user-defined type cannot overload the conditional logical operators `&&` and `||`.</span></span> <span data-ttu-id="fd6df-230">不过，如果用户定义类型以某种方式重载 [true 和 false 运算符](true-false-operators.md)以及 `&` 或 `|` 运算符，可以对相应类型的操作数执行 `&&` 或 `||` 运算。</span><span class="sxs-lookup"><span data-stu-id="fd6df-230">However, if a user-defined type overloads the [true and false operators](true-false-operators.md) and the `&` or `|` operator in a certain way, the `&&` or `||` operation, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="fd6df-231">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[用户定义条件逻辑运算符](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="fd6df-231">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fd6df-232">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="fd6df-232">C# language specification</span></span>

<span data-ttu-id="fd6df-233">有关更多信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的以下部分：</span><span class="sxs-lookup"><span data-stu-id="fd6df-233">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="fd6df-234">逻辑非运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-234">Logical negation operator</span></span>](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [<span data-ttu-id="fd6df-235">逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-235">Logical operators</span></span>](~/_csharplang/spec/expressions.md#logical-operators)
- [<span data-ttu-id="fd6df-236">条件逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-236">Conditional logical operators</span></span>](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [<span data-ttu-id="fd6df-237">复合赋值</span><span class="sxs-lookup"><span data-stu-id="fd6df-237">Compound assignment</span></span>](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a><span data-ttu-id="fd6df-238">请参阅</span><span class="sxs-lookup"><span data-stu-id="fd6df-238">See also</span></span>

- [<span data-ttu-id="fd6df-239">C# 参考</span><span class="sxs-lookup"><span data-stu-id="fd6df-239">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fd6df-240">C# 运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-240">C# operators</span></span>](index.md)
- [<span data-ttu-id="fd6df-241">位运算符和移位运算符</span><span class="sxs-lookup"><span data-stu-id="fd6df-241">Bitwise and shift operators</span></span>](bitwise-and-shift-operators.md)
