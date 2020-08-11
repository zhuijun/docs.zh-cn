---
title: '?: 运算符 - C# 参考'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: fcde0476935108122d7f7e825d701e48952873f6
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916849"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8187a-102">?: 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="8187a-102">?: operator (C# reference)</span></span>

<span data-ttu-id="8187a-103">条件运算符 (`?:`) 也被称为三元条件运算符，用于计算布尔表达式，并根据布尔表达式的计算结果为 `true` 还是 `false` 来返回两个表达式中的一个结果。</span><span class="sxs-lookup"><span data-stu-id="8187a-103">The conditional operator `?:`, also known as the ternary conditional operator, evaluates a Boolean expression and returns the result of one of the two expressions, depending on whether the Boolean expression evaluates to `true` or `false`.</span></span>

<span data-ttu-id="8187a-104">条件运算符的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8187a-104">The syntax for the conditional operator is as follows:</span></span>

```csharp
condition ? consequent : alternative
```

<span data-ttu-id="8187a-105">`condition` 表达式的计算结果必须为 `true` 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="8187a-105">The `condition` expression must evaluate to `true` or `false`.</span></span> <span data-ttu-id="8187a-106">若 `condition` 的计算结果为 `true`，将计算 `consequent`，其结果成为运算结果。</span><span class="sxs-lookup"><span data-stu-id="8187a-106">If `condition` evaluates to `true`, the `consequent` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8187a-107">若 `condition` 的计算结果为 `false`，将计算 `alternative`，其结果成为运算结果。</span><span class="sxs-lookup"><span data-stu-id="8187a-107">If `condition` evaluates to `false`, the `alternative` expression is evaluated, and its result becomes the result of the operation.</span></span> <span data-ttu-id="8187a-108">只会计算 `consequent` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="8187a-108">Only `consequent` or `alternative` is evaluated.</span></span>

<span data-ttu-id="8187a-109">`consequent` 和 `alternative` 的类型必须相同，或者必须存在从一种类型到另一种类型的隐式转换。</span><span class="sxs-lookup"><span data-stu-id="8187a-109">The type of `consequent` and `alternative` must be the same, or there must be an implicit conversion from one type to the other.</span></span>

<span data-ttu-id="8187a-110">条件运算符为右联运算符，即形式的表达式</span><span class="sxs-lookup"><span data-stu-id="8187a-110">The conditional operator is right-associative, that is, an expression of the form</span></span>

```csharp
a ? b : c ? d : e
```

<span data-ttu-id="8187a-111">计算结果为</span><span class="sxs-lookup"><span data-stu-id="8187a-111">is evaluated as</span></span>

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> <span data-ttu-id="8187a-112">可以使用以下助记键设备记住条件运算符的计算方式：</span><span class="sxs-lookup"><span data-stu-id="8187a-112">You can use the following mnemonic device to remember how the conditional operator is evaluated:</span></span>
>
> ```text
> is this condition true ? yes : no
> ```

<span data-ttu-id="8187a-113">下面的示例演示条件运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="8187a-113">The following example demonstrates the usage of the conditional operator:</span></span>

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a><span data-ttu-id="8187a-114">ref 条件表达式</span><span class="sxs-lookup"><span data-stu-id="8187a-114">Conditional ref expression</span></span>

<span data-ttu-id="8187a-115">从 C# 7.2 开始，可通过 ref 条件表达式有条件地分配 [ref local](../keywords/ref.md#ref-locals) 或 [ref readonly local](../keywords/ref.md#ref-readonly-locals) 变量。</span><span class="sxs-lookup"><span data-stu-id="8187a-115">Beginning with C# 7.2, a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable can be assigned conditionally with the conditional ref expression.</span></span> <span data-ttu-id="8187a-116">还可以使用 ref 条件表达式作为[引用返回值](../keywords/ref.md#reference-return-values)或 [`ref` 方法参数](../keywords/ref.md#passing-an-argument-by-reference)。</span><span class="sxs-lookup"><span data-stu-id="8187a-116">You can also use the conditional ref expression as a [reference return value](../keywords/ref.md#reference-return-values) or as a [`ref` method argument](../keywords/ref.md#passing-an-argument-by-reference).</span></span>

<span data-ttu-id="8187a-117">ref 条件表达式的语法如下所示：</span><span class="sxs-lookup"><span data-stu-id="8187a-117">The syntax for the conditional ref expression is as follows:</span></span>

```csharp
condition ? ref consequent : ref alternative
```

<span data-ttu-id="8187a-118">ref 条件表达式与原始的条件运算符相似，仅计算两个表达式其中之一：`consequent` 或 `alternative`。</span><span class="sxs-lookup"><span data-stu-id="8187a-118">Like the original conditional operator, the conditional ref expression evaluates only one of the two expressions: either `consequent` or `alternative`.</span></span>

<span data-ttu-id="8187a-119">在 ref 条件表达式中，`consequent` 和 `alternative` 的类型必须相同。</span><span class="sxs-lookup"><span data-stu-id="8187a-119">In the case of the conditional ref expression, the type of `consequent` and `alternative` must be the same.</span></span>

<span data-ttu-id="8187a-120">下面的示例演示 ref 条件表达式的用法：</span><span class="sxs-lookup"><span data-stu-id="8187a-120">The following example demonstrates the usage of the conditional ref expression:</span></span>

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a><span data-ttu-id="8187a-121">条件运算符和 `if..else` 语句</span><span class="sxs-lookup"><span data-stu-id="8187a-121">Conditional operator and an `if..else` statement</span></span>

<span data-ttu-id="8187a-122">需要根据条件计算值时，使用条件运算符而不是 [if-else](../keywords/if-else.md) 语句可以使代码更简洁。</span><span class="sxs-lookup"><span data-stu-id="8187a-122">Use of the conditional operator instead of an [if-else](../keywords/if-else.md) statement might result in more concise code in cases when you need conditionally to compute a value.</span></span> <span data-ttu-id="8187a-123">下面的示例演示了将整数归类为负数或非负数的两种方法：</span><span class="sxs-lookup"><span data-stu-id="8187a-123">The following example demonstrates two ways to classify an integer as negative or nonnegative:</span></span>

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a><span data-ttu-id="8187a-124">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="8187a-124">Operator overloadability</span></span>

<span data-ttu-id="8187a-125">用户定义类型不能重载条件运算符。</span><span class="sxs-lookup"><span data-stu-id="8187a-125">A user-defined type cannot overload the conditional operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="8187a-126">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="8187a-126">C# language specification</span></span>

<span data-ttu-id="8187a-127">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的[条件运算符](~/_csharplang/spec/expressions.md#conditional-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="8187a-127">For more information, see the [Conditional operator](~/_csharplang/spec/expressions.md#conditional-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="8187a-128">有关条件 ref 表达式的详细信息，请参阅[功能建议说明](~/_csharplang/proposals/csharp-7.2/conditional-ref.md)。</span><span class="sxs-lookup"><span data-stu-id="8187a-128">For more information about the conditional ref expression, see the [feature proposal note](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8187a-129">请参阅</span><span class="sxs-lookup"><span data-stu-id="8187a-129">See also</span></span>

- [<span data-ttu-id="8187a-130">C# 参考</span><span class="sxs-lookup"><span data-stu-id="8187a-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="8187a-131">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="8187a-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="8187a-132">if-else 语句</span><span class="sxs-lookup"><span data-stu-id="8187a-132">if-else statement</span></span>](../keywords/if-else.md)
- <span data-ttu-id="8187a-133">[?. 和 ?[] 运算符](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="8187a-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="8187a-134">?? 和 ??= 运算符</span><span class="sxs-lookup"><span data-stu-id="8187a-134">?? and ??= operators</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="8187a-135">ref 关键字</span><span class="sxs-lookup"><span data-stu-id="8187a-135">ref keyword</span></span>](../keywords/ref.md)
