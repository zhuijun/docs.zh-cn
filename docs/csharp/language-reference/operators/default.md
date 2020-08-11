---
title: default value 表达式 - C# 参考
description: 使用 default value 表达式可获取类型的默认值
ms.date: 03/13/2020
f1_keywords:
- default_CSharpKeyword
- default
helpviewer_keywords:
- default keyword [C#]
ms.openlocfilehash: f03971efa87bf03967c79512e44d22134dd80c17
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916869"
---
# <a name="default-value-expressions-c-reference"></a><span data-ttu-id="814d4-103">default value 表达式（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="814d4-103">default value expressions (C# reference)</span></span>

<span data-ttu-id="814d4-104">default value 表达式生成类型的[默认值](../builtin-types/default-values.md)。</span><span class="sxs-lookup"><span data-stu-id="814d4-104">A default value expression produces the [default value](../builtin-types/default-values.md) of a type.</span></span> <span data-ttu-id="814d4-105">有两种类型的 default value 表达式：[default 运算符](#default-operator)调用和 [default 文本](#default-literal)。</span><span class="sxs-lookup"><span data-stu-id="814d4-105">There are two kinds of default value expressions: the [default operator](#default-operator) call and a [default literal](#default-literal).</span></span>

<span data-ttu-id="814d4-106">你还可以将 `default` 关键字用作 [`switch` 语句](../keywords/switch.md)中的默认用例标签。</span><span class="sxs-lookup"><span data-stu-id="814d4-106">You also use the `default` keyword as the default case label within a [`switch` statement](../keywords/switch.md).</span></span>

## <a name="default-operator"></a><span data-ttu-id="814d4-107">default 运算符</span><span class="sxs-lookup"><span data-stu-id="814d4-107">default operator</span></span>

<span data-ttu-id="814d4-108">`default` 运算符的实参必须是类型或类型形参的名称，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="814d4-108">The argument to the `default` operator must be the name of a type or a type parameter, as the following example shows:</span></span>

[!code-csharp-interactive[default of T](snippets/shared/DefaultOperator.cs#WithOperand)]

## <a name="default-literal"></a><span data-ttu-id="814d4-109">default 文本</span><span class="sxs-lookup"><span data-stu-id="814d4-109">default literal</span></span>

<span data-ttu-id="814d4-110">从 C# 7.1 开始，当编译器可以推断表达式类型时，可以使用 `default` 文本生成类型的默认值。</span><span class="sxs-lookup"><span data-stu-id="814d4-110">Beginning with C# 7.1, you can use the `default` literal to produce the default value of a type when the compiler can infer the expression type.</span></span> <span data-ttu-id="814d4-111">`default` 文本表达式生成与 `default(T)` 表达式（其中，`T` 是推断的类型）相同的值。</span><span class="sxs-lookup"><span data-stu-id="814d4-111">The `default` literal expression produces the same value as the `default(T)` expression where `T` is the inferred type.</span></span> <span data-ttu-id="814d4-112">可以在以下任一情况下使用 `default` 文本：</span><span class="sxs-lookup"><span data-stu-id="814d4-112">You can use the `default` literal in any of the following cases:</span></span>

- <span data-ttu-id="814d4-113">对变量进行赋值或初始化时。</span><span class="sxs-lookup"><span data-stu-id="814d4-113">In the assignment or initialization of a variable.</span></span>
- <span data-ttu-id="814d4-114">在声明[可选方法参数](../../methods.md#optional-parameters-and-arguments)的默认值时。</span><span class="sxs-lookup"><span data-stu-id="814d4-114">In the declaration of the default value for an [optional method parameter](../../methods.md#optional-parameters-and-arguments).</span></span>
- <span data-ttu-id="814d4-115">在方法调用中提供参数值时。</span><span class="sxs-lookup"><span data-stu-id="814d4-115">In a method call to provide an argument value.</span></span>
- <span data-ttu-id="814d4-116">在 [`return` 语句](../keywords/return.md)中或作为[表达式主体成员](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)中的表达式时。</span><span class="sxs-lookup"><span data-stu-id="814d4-116">In a [`return` statement](../keywords/return.md) or as an expression in an [expression-bodied member](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).</span></span>

<span data-ttu-id="814d4-117">下面的示例演示 `default` 文本的用法：</span><span class="sxs-lookup"><span data-stu-id="814d4-117">The following example shows the usage of the `default` literal:</span></span>

[!code-csharp-interactive[default literal](snippets/shared/DefaultOperator.cs#DefaultLiteral)]

## <a name="c-language-specification"></a><span data-ttu-id="814d4-118">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="814d4-118">C# language specification</span></span>

<span data-ttu-id="814d4-119">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [默认值表达式](~/_csharplang/spec/expressions.md#default-value-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="814d4-119">For more information, see the [Default value expressions](~/_csharplang/spec/expressions.md#default-value-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="814d4-120">有关 `default` 文本的详细信息，请参阅[功能建议说明](~/_csharplang/proposals/csharp-7.1/target-typed-default.md)。</span><span class="sxs-lookup"><span data-stu-id="814d4-120">For more information about the `default` literal, see the [feature proposal note](~/_csharplang/proposals/csharp-7.1/target-typed-default.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="814d4-121">请参阅</span><span class="sxs-lookup"><span data-stu-id="814d4-121">See also</span></span>

- [<span data-ttu-id="814d4-122">C# 参考</span><span class="sxs-lookup"><span data-stu-id="814d4-122">C# reference</span></span>](../index.md)
- [<span data-ttu-id="814d4-123">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="814d4-123">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="814d4-124">C# 类型的默认值</span><span class="sxs-lookup"><span data-stu-id="814d4-124">Default values of C# types</span></span>](../builtin-types/default-values.md)
- [<span data-ttu-id="814d4-125">.NET 中的泛型</span><span class="sxs-lookup"><span data-stu-id="814d4-125">Generics in .NET</span></span>](../../../standard/generics/index.md)
