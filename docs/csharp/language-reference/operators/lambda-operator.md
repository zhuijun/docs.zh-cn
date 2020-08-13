---
title: => 运算符 - C# 参考
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: b72b058c1709e7a643a70233cc3289d5d9165ca4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916800"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0acf2-102">=> 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="0acf2-102">=> operator (C# reference)</span></span>

<span data-ttu-id="0acf2-103">`=>` 令牌支持两种形式：作为 [lambda 运算符](#lambda-operator)、作为成员名称的分隔符和[表达式主体定义](#expression-body-definition)中的成员实现。</span><span class="sxs-lookup"><span data-stu-id="0acf2-103">The `=>` token is supported in two forms: as the [lambda operator](#lambda-operator) and as a separator of a member name and the member implementation in an [expression body definition](#expression-body-definition).</span></span>

## <a name="lambda-operator"></a><span data-ttu-id="0acf2-104">lambda 运算符</span><span class="sxs-lookup"><span data-stu-id="0acf2-104">Lambda operator</span></span>

<span data-ttu-id="0acf2-105">在 [lambda 表达式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)中，lambda 运算符 `=>` 将左侧的输入参数与右侧的 lambda 主体分开。</span><span class="sxs-lookup"><span data-stu-id="0acf2-105">In [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md), the lambda operator `=>` separates the input parameters on the left side from the lambda body on the right side.</span></span>

<span data-ttu-id="0acf2-106">以下示例使用带有方法语法的 [LINQ](../../programming-guide/concepts/linq/index.md) 功能来演示 lambda 表达式的用法：</span><span class="sxs-lookup"><span data-stu-id="0acf2-106">The following example uses the [LINQ](../../programming-guide/concepts/linq/index.md) feature with method syntax to demonstrate the usage of lambda expressions:</span></span>

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

<span data-ttu-id="0acf2-107">lambda 表达式的输入参数在编译时是强类型。</span><span class="sxs-lookup"><span data-stu-id="0acf2-107">Input parameters of a lambda expression are strongly typed at compile time.</span></span> <span data-ttu-id="0acf2-108">当编译器可以推断输入参数的类型时，如前面的示例所示，可以省略类型声明。</span><span class="sxs-lookup"><span data-stu-id="0acf2-108">When the compiler can infer the types of input parameters, like in the preceding example, you may omit type declarations.</span></span> <span data-ttu-id="0acf2-109">如果需要指定输入参数的类型，则必须对每个参数执行类型声明，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="0acf2-109">If you need to specify the type of input parameters, you must do that for each parameter, as the following example shows:</span></span>

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

<span data-ttu-id="0acf2-110">以下示例显示如何在没有输入参数的情况下定义 lambda 表达式：</span><span class="sxs-lookup"><span data-stu-id="0acf2-110">The following example shows how to define a lambda expression without input parameters:</span></span>

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

<span data-ttu-id="0acf2-111">有关详细信息，请参阅 [Lambda 表达式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0acf2-111">For more information, see [Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>

## <a name="expression-body-definition"></a><span data-ttu-id="0acf2-112">表达式主体定义</span><span class="sxs-lookup"><span data-stu-id="0acf2-112">Expression body definition</span></span>

<span data-ttu-id="0acf2-113">表达式主体定义具有下列常规语法：</span><span class="sxs-lookup"><span data-stu-id="0acf2-113">An expression body definition has the following general syntax:</span></span>

```csharp
member => expression;
```

<span data-ttu-id="0acf2-114">其中 `expression` 是有效的表达式。</span><span class="sxs-lookup"><span data-stu-id="0acf2-114">where `expression` is a valid expression.</span></span> <span data-ttu-id="0acf2-115">`expression` 的返回类型必须可隐式转换为成员的返回类型。</span><span class="sxs-lookup"><span data-stu-id="0acf2-115">The return type of `expression` must be implicitly convertible to the member's return type.</span></span> <span data-ttu-id="0acf2-116">如果成员的返回类型为 `void`，或者如果成员是构造函数、终结器、属性或索引器 `set` 访问器，则 `expression` 必须为[语句表达式](~/_csharplang/spec/statements.md#expression-statements)。</span><span class="sxs-lookup"><span data-stu-id="0acf2-116">If the member's return type is `void` or if the member is a constructor, a finalizer, or a property or indexer `set` accessor, `expression` must be a [*statement expression*](~/_csharplang/spec/statements.md#expression-statements).</span></span> <span data-ttu-id="0acf2-117">由于表达式的结果被丢弃，该表达式的返回类型可以是任何类型。</span><span class="sxs-lookup"><span data-stu-id="0acf2-117">Because the expression's result is discarded, the return type of that expression can be any type.</span></span>

<span data-ttu-id="0acf2-118">以下示例演示了用于 `Person.ToString` 方法的表达式主体定义：</span><span class="sxs-lookup"><span data-stu-id="0acf2-118">The following example shows an expression body definition for a `Person.ToString` method:</span></span>

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

<span data-ttu-id="0acf2-119">它是以下方法定义的简写版：</span><span class="sxs-lookup"><span data-stu-id="0acf2-119">It's a shorthand version of the following method definition:</span></span>

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

<span data-ttu-id="0acf2-120">自 C#6 起，支持方法、运算符和只读属性的表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="0acf2-120">Expression body definitions for methods, operators, and read-only properties are supported beginning with C# 6.</span></span> <span data-ttu-id="0acf2-121">自 C# 7.0 起，支持构造函数、终结器、属性和索引器访问器的表达式主体定义。</span><span class="sxs-lookup"><span data-stu-id="0acf2-121">Expression body definitions for constructors, finalizers, and property and indexer accessors are supported beginning with C# 7.0.</span></span>

<span data-ttu-id="0acf2-122">有关详细信息，请参阅 “[Expression-bodied 成员](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)”。</span><span class="sxs-lookup"><span data-stu-id="0acf2-122">For more information, see [Expression-bodied members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="0acf2-123">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="0acf2-123">Operator overloadability</span></span>

<span data-ttu-id="0acf2-124">不能重载 `=>` 运算符。</span><span class="sxs-lookup"><span data-stu-id="0acf2-124">The `=>` operator cannot be overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0acf2-125">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="0acf2-125">C# language specification</span></span>

<span data-ttu-id="0acf2-126">有关 lambda 运算符的详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的[匿名函数表达式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="0acf2-126">For more information about the lambda operator, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0acf2-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="0acf2-127">See also</span></span>

- [<span data-ttu-id="0acf2-128">C# 参考</span><span class="sxs-lookup"><span data-stu-id="0acf2-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0acf2-129">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="0acf2-129">C# operators and expressions</span></span>](index.md)
