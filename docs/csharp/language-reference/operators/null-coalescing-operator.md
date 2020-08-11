---
title: ?? 和 ??= 运算符 - C# 参考
ms.date: 09/10/2019
f1_keywords:
- ??_CSharpKeyword
- ??=_CSharpKeyword
helpviewer_keywords:
- null-coalescing operator [C#]
- ?? operator [C#]
- null-coalescing assignment [C#]
- ??= operator [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 58c60dad3badc62f850f737a3d210ec486809272
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916735"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="454f6-103">??</span><span class="sxs-lookup"><span data-stu-id="454f6-103">??</span></span> <span data-ttu-id="454f6-104">和 ??= 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="454f6-104">and ??= operators (C# reference)</span></span>

<span data-ttu-id="454f6-105">如果左操作数的值不为 `null`，则 null 合并运算符 `??` 返回该值；否则，它会计算右操作数并返回其结果。</span><span class="sxs-lookup"><span data-stu-id="454f6-105">The null-coalescing operator `??` returns the value of its left-hand operand if it isn't `null`; otherwise, it evaluates the right-hand operand and returns its result.</span></span> <span data-ttu-id="454f6-106">如果左操作数的计算结果为非 null，则 `??` 运算符不会计算其右操作数。</span><span class="sxs-lookup"><span data-stu-id="454f6-106">The `??` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

<span data-ttu-id="454f6-107">C# 8.0 及更高版本中可使用空合并赋值运算符 `??=`，该运算符仅在左侧操作数的求值结果为 `null` 时，才将其右侧操作数的值赋值给左操作数。</span><span class="sxs-lookup"><span data-stu-id="454f6-107">Available in C# 8.0 and later, the null-coalescing assignment operator `??=` assigns the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="454f6-108">如果左操作数的计算结果为非 null，则 `??=` 运算符不会计算其右操作数。</span><span class="sxs-lookup"><span data-stu-id="454f6-108">The `??=` operator doesn't evaluate its right-hand operand if the left-hand operand evaluates to non-null.</span></span>

[!code-csharp[null-coalescing assignment](snippets/shared/NullCoalescingOperator.cs#Assignment)]

<span data-ttu-id="454f6-109">`??=` 运算符的左操作数必须是变量、[属性](../../programming-guide/classes-and-structs/properties.md)或[索引器](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="454f6-109">The left-hand operand of the `??=` operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element.</span></span>

<span data-ttu-id="454f6-110">在 C# 7.3 及更早版本中，`??` 运算符左操作数的类型必须是[引用类型](../keywords/reference-types.md)或[可以为 null 的值类型](../builtin-types/nullable-value-types.md)。</span><span class="sxs-lookup"><span data-stu-id="454f6-110">In C# 7.3 and earlier, the type of the left-hand operand of the `??` operator must be either a [reference type](../keywords/reference-types.md) or a [nullable value type](../builtin-types/nullable-value-types.md).</span></span> <span data-ttu-id="454f6-111">从 C# 8.0 版本开始，该要求替换为以下内容：`??` 和 `??=` 运算符的左操作数的类型必须是可以为 null 的值类型。</span><span class="sxs-lookup"><span data-stu-id="454f6-111">Beginning with C# 8.0, that requirement is replaced with the following: the type of the left-hand operand of the `??` and `??=` operators cannot be a non-nullable value type.</span></span> <span data-ttu-id="454f6-112">特别是从 C# 8.0 开始，可以使用具有无约束类型参数的 null 合并运算符：</span><span class="sxs-lookup"><span data-stu-id="454f6-112">In particular, beginning with C# 8.0, you can use the null-coalescing operators with unconstrained type parameters:</span></span>

[!code-csharp[unconstrained type parameter](snippets/shared/NullCoalescingOperator.cs#UnconstrainedType)]

<span data-ttu-id="454f6-113">null 合并运算符是右结合运算符。</span><span class="sxs-lookup"><span data-stu-id="454f6-113">The null-coalescing operators are right-associative.</span></span> <span data-ttu-id="454f6-114">也就是说，是窗体的表达式</span><span class="sxs-lookup"><span data-stu-id="454f6-114">That is, expressions of the form</span></span>

```csharp
a ?? b ?? c
d ??= e ??= f
```

<span data-ttu-id="454f6-115">会像这样求值</span><span class="sxs-lookup"><span data-stu-id="454f6-115">are evaluated as</span></span>

```csharp
a ?? (b ?? c)
d ??= (e ??= f)
```

## <a name="examples"></a><span data-ttu-id="454f6-116">示例</span><span class="sxs-lookup"><span data-stu-id="454f6-116">Examples</span></span>

<span data-ttu-id="454f6-117">`??` 和 `??=` 运算符在以下应用场景中很有用：</span><span class="sxs-lookup"><span data-stu-id="454f6-117">The `??` and `??=` operators can be useful in the following scenarios:</span></span>

- <span data-ttu-id="454f6-118">在包含 [null 条件运算符 ?. 和 ?[]](member-access-operators.md#null-conditional-operators--and-) 的表达式中，当包含 null 条件运算的表达式结果为 `null` 时，可以使用 `??` 运算符来提供替代表达式用于求值：</span><span class="sxs-lookup"><span data-stu-id="454f6-118">In expressions with the [null-conditional operators ?. and ?[]](member-access-operators.md#null-conditional-operators--and-), you can use the `??` operator to provide an alternative expression to evaluate in case the result of the expression with null-conditional operations is `null`:</span></span>

  [!code-csharp-interactive[with null-conditional](snippets/shared/NullCoalescingOperator.cs#WithNullConditional)]

- <span data-ttu-id="454f6-119">当使用[可以为 null 值类型](../builtin-types/nullable-value-types.md)并且需要提供基础值类型的值时，可以使用 `??` 运算符指定当可以为 null 的类型的值为 `null` 时要提供的值：</span><span class="sxs-lookup"><span data-stu-id="454f6-119">When you work with [nullable value types](../builtin-types/nullable-value-types.md) and need to provide a value of an underlying value type, use the `??` operator to specify the value to provide in case a nullable type value is `null`:</span></span>

  [!code-csharp-interactive[with nullable types](snippets/shared/NullCoalescingOperator.cs#WithNullableTypes)]

  <span data-ttu-id="454f6-120">如果可以为 null 的类型的值为 `null` 时要使用的值应为基础值类型的默认值，请使用 <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="454f6-120">Use the <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> method if the value to be used when a nullable type value is `null` should be the default value of the underlying value type.</span></span>

- <span data-ttu-id="454f6-121">从 C# 7.0 开始，可以使用 [`throw` 表达式](../keywords/throw.md#the-throw-expression)作为 `??` 运算符的右操作数，以使参数检查代码更简洁：</span><span class="sxs-lookup"><span data-stu-id="454f6-121">Beginning with C# 7.0, you can use a [`throw` expression](../keywords/throw.md#the-throw-expression) as the right-hand operand of the `??` operator to make the argument-checking code more concise:</span></span>

  [!code-csharp[with throw expression](snippets/shared/NullCoalescingOperator.cs#WithThrowExpression)]

  <span data-ttu-id="454f6-122">前面的示例还演示了如何使用 [expression-bodied 成员](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)来定义属性。</span><span class="sxs-lookup"><span data-stu-id="454f6-122">The preceding example also demonstrates how to use [expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) to define a property.</span></span>

- <span data-ttu-id="454f6-123">从 C# 8.0 开始，可以使用 `??=` 运算符将这样的代码</span><span class="sxs-lookup"><span data-stu-id="454f6-123">Beginning with C# 8.0, you can use the `??=` operator to replace the code of the form</span></span>

  ```csharp
  if (variable is null)
  {
      variable = expression;
  }
  ```

  <span data-ttu-id="454f6-124">替换为以下代码：</span><span class="sxs-lookup"><span data-stu-id="454f6-124">with the following code:</span></span>

  ```csharp
  variable ??= expression;
  ```

## <a name="operator-overloadability"></a><span data-ttu-id="454f6-125">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="454f6-125">Operator overloadability</span></span>

<span data-ttu-id="454f6-126">运算符 `??` 和 `??=` 无法进行重载。</span><span class="sxs-lookup"><span data-stu-id="454f6-126">The operators `??` and `??=` cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="454f6-127">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="454f6-127">C# language specification</span></span>

<span data-ttu-id="454f6-128">有关 `??` 运算符的详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的 [null 合并运算符](~/_csharplang/spec/expressions.md#the-null-coalescing-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="454f6-128">For more information about the `??` operator, see [The null coalescing operator](~/_csharplang/spec/expressions.md#the-null-coalescing-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="454f6-129">有关 `??=` 运算符的详细信息，请参阅[功能建议说明](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md)。</span><span class="sxs-lookup"><span data-stu-id="454f6-129">For more information about the `??=` operator, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/null-coalescing-assignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="454f6-130">另请参阅</span><span class="sxs-lookup"><span data-stu-id="454f6-130">See also</span></span>

- [<span data-ttu-id="454f6-131">C# 参考</span><span class="sxs-lookup"><span data-stu-id="454f6-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="454f6-132">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="454f6-132">C# operators and expressions</span></span>](index.md)
- <span data-ttu-id="454f6-133">[?. 和 ?[] 运算符](member-access-operators.md#null-conditional-operators--and-)</span><span class="sxs-lookup"><span data-stu-id="454f6-133">[?. and ?[] operators](member-access-operators.md#null-conditional-operators--and-)</span></span>
- [<span data-ttu-id="454f6-134">?: 运算符</span><span class="sxs-lookup"><span data-stu-id="454f6-134">?: operator</span></span>](conditional-operator.md)
