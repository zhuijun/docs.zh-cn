---
description: true 和 false 运算符 - C# 参考
title: true 和 false 运算符 - C# 参考
ms.date: 12/10/2018
helpviewer_keywords:
- false operator [C#]
- true operator [C#]
ms.assetid: 81a888fd-011e-4589-b242-6c261fea505e
ms.openlocfilehash: f20f71e31c77c035c48702f01208c5b29c90109c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132373"
---
# <a name="true-and-false-operators-c-reference"></a><span data-ttu-id="d58c0-103">true 和 false 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="d58c0-103">true and false operators (C# reference)</span></span>

<span data-ttu-id="d58c0-104">`true` 运算符返回 [bool](../builtin-types/bool.md) 值 `true`，以指明其操作数一定为 true。</span><span class="sxs-lookup"><span data-stu-id="d58c0-104">The `true` operator returns the [bool](../builtin-types/bool.md) value `true` to indicate that its operand is definitely true.</span></span> <span data-ttu-id="d58c0-105">`false` 运算符返回 `bool` 值 `true`，以指明其操作数一定为 false。</span><span class="sxs-lookup"><span data-stu-id="d58c0-105">The `false` operator returns the `bool` value `true` to indicate that its operand is definitely false.</span></span> <span data-ttu-id="d58c0-106">无法确保 `true` 和 `false` 运算符互补。</span><span class="sxs-lookup"><span data-stu-id="d58c0-106">The `true` and `false` operators are not guaranteed to complement each other.</span></span> <span data-ttu-id="d58c0-107">也就是说，`true` 和 `false` 运算符可能同时针对同一个操作数返回 `bool` 值 `false`。</span><span class="sxs-lookup"><span data-stu-id="d58c0-107">That is, both the `true` and `false` operator might return the `bool` value `false` for the same operand.</span></span> <span data-ttu-id="d58c0-108">如果某类型定义这两个运算符之一，它还必须定义另一个运算符。</span><span class="sxs-lookup"><span data-stu-id="d58c0-108">If a type defines one of the two operators, it must also define another operator.</span></span>

> [!TIP]
> <span data-ttu-id="d58c0-109">如需支持三值逻辑（例如，在使用支持三值布尔类型的数据库时），请使用 `bool?` 类型。</span><span class="sxs-lookup"><span data-stu-id="d58c0-109">Use the `bool?` type, if you need to support the three-valued logic (for example, when you work with databases that support a three-valued Boolean type).</span></span> <span data-ttu-id="d58c0-110">C# 提供 `&` 和 `|` 运算符，它们通过 `bool?` 操作数支持三值逻辑。</span><span class="sxs-lookup"><span data-stu-id="d58c0-110">C# provides the `&` and `|` operators that support the three-valued logic with the `bool?` operands.</span></span> <span data-ttu-id="d58c0-111">有关详细信息，请参阅[布尔逻辑运算符](boolean-logical-operators.md)一文的[可以为 null 的布尔逻辑运算符](boolean-logical-operators.md#nullable-boolean-logical-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="d58c0-111">For more information, see the [Nullable Boolean logical operators](boolean-logical-operators.md#nullable-boolean-logical-operators) section of the [Boolean logical operators](boolean-logical-operators.md) article.</span></span>

## <a name="boolean-expressions"></a><span data-ttu-id="d58c0-112">布尔表达式</span><span class="sxs-lookup"><span data-stu-id="d58c0-112">Boolean expressions</span></span>

<span data-ttu-id="d58c0-113">包含已定义 `true` 运算符的类型可以是 [if](../keywords/if-else.md)、[do](../keywords/do.md)、[while](../keywords/while.md) 和 [for](../keywords/for.md) 语句以及[条件运算符 `?:`](conditional-operator.md) 中控制条件表达式的结果的类型。</span><span class="sxs-lookup"><span data-stu-id="d58c0-113">A type with the defined `true` operator can be the type of a result of a controlling conditional expression in the [if](../keywords/if-else.md), [do](../keywords/do.md), [while](../keywords/while.md), and [for](../keywords/for.md) statements and in the [conditional operator `?:`](conditional-operator.md).</span></span> <span data-ttu-id="d58c0-114">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [Boolean 表达式](~/_csharplang/spec/expressions.md#boolean-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="d58c0-114">For more information, see the [Boolean expressions](~/_csharplang/spec/expressions.md#boolean-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="user-defined-conditional-logical-operators"></a><span data-ttu-id="d58c0-115">用户定义的条件逻辑运算符</span><span class="sxs-lookup"><span data-stu-id="d58c0-115">User-defined conditional logical operators</span></span>

<span data-ttu-id="d58c0-116">如果包含已定义 `true` 和 `false` 运算符的类型以某种方式[重载](operator-overloading.md)[逻辑 OR 运算符](boolean-logical-operators.md#logical-or-operator-) `|` 或[逻辑 AND 运算符](boolean-logical-operators.md#logical-and-operator-) `&`，可以对相应类型的操作数分别执行[条件逻辑 OR 运算符](boolean-logical-operators.md#conditional-logical-or-operator-) `||` 或[条件逻辑 AND 运算符](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` 运算。</span><span class="sxs-lookup"><span data-stu-id="d58c0-116">If a type with the defined `true` and `false` operators [overloads](operator-overloading.md) the [logical OR operator](boolean-logical-operators.md#logical-or-operator-) `|` or the [logical AND operator](boolean-logical-operators.md#logical-and-operator-) `&` in a certain way, the [conditional logical OR operator](boolean-logical-operators.md#conditional-logical-or-operator-) `||` or [conditional logical AND operator](boolean-logical-operators.md#conditional-logical-and-operator-) `&&`, respectively, can be evaluated for the operands of that type.</span></span> <span data-ttu-id="d58c0-117">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[用户定义条件逻辑运算符](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators)部分。</span><span class="sxs-lookup"><span data-stu-id="d58c0-117">For more information, see the [User-defined conditional logical operators](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="example"></a><span data-ttu-id="d58c0-118">示例</span><span class="sxs-lookup"><span data-stu-id="d58c0-118">Example</span></span>

<span data-ttu-id="d58c0-119">下面的示例演示了定义 `true` 和 `false` 运算符的类型。</span><span class="sxs-lookup"><span data-stu-id="d58c0-119">The following example presents the type that defines both `true` and `false` operators.</span></span> <span data-ttu-id="d58c0-120">此外，该类型还重载了逻辑 AND 运算符 `&`，因此，也可以对相应类型的操作数计算运算符 `&&`。</span><span class="sxs-lookup"><span data-stu-id="d58c0-120">The type also overloads the logical AND operator `&` in such a way that the `&&` operator also can be evaluated for the operands of that type.</span></span>

[!code-csharp[true and false operators example](snippets/shared/TrueFalseOperators.cs)]

<span data-ttu-id="d58c0-121">请注意 `&&` 运算符的短路行为。</span><span class="sxs-lookup"><span data-stu-id="d58c0-121">Notice the short-circuiting behavior of the `&&` operator.</span></span> <span data-ttu-id="d58c0-122">当 `GetFuelLaunchStatus` 方法返回 `LaunchStatus.Red` 时，不会进行计算的 `&&` 运算符的右侧操作数。</span><span class="sxs-lookup"><span data-stu-id="d58c0-122">When the `GetFuelLaunchStatus` method returns `LaunchStatus.Red`, the right-hand operand of the `&&` operator is not evaluated.</span></span> <span data-ttu-id="d58c0-123">这是因为 `LaunchStatus.Red` 一定为 false。</span><span class="sxs-lookup"><span data-stu-id="d58c0-123">That is because `LaunchStatus.Red` is definitely false.</span></span> <span data-ttu-id="d58c0-124">然后，逻辑 AND 运算符的结果不依赖右侧操作数的值。</span><span class="sxs-lookup"><span data-stu-id="d58c0-124">Then the result of the logical AND doesn't depend on the value of the right-hand operand.</span></span> <span data-ttu-id="d58c0-125">示例的输出如下所示：</span><span class="sxs-lookup"><span data-stu-id="d58c0-125">The output of the example is as follows:</span></span>

```console
Getting fuel launch status...
Wait!
```

## <a name="see-also"></a><span data-ttu-id="d58c0-126">另请参阅</span><span class="sxs-lookup"><span data-stu-id="d58c0-126">See also</span></span>

- [<span data-ttu-id="d58c0-127">C# 参考</span><span class="sxs-lookup"><span data-stu-id="d58c0-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d58c0-128">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="d58c0-128">C# operators and expressions</span></span>](index.md)
