---
description: delegate 运算符 - C# 参考
title: delegate 运算符 - C# 参考
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 1dfaaf40c0f5a19534adef3be7e3c917bc95c4a8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122246"
---
# <a name="delegate-operator-c-reference"></a><span data-ttu-id="f247e-103">delegate 运算符 -（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="f247e-103">delegate operator (C# reference)</span></span>

<span data-ttu-id="f247e-104">`delegate` 运算符创建一个可以转换为委托类型的匿名方法：</span><span class="sxs-lookup"><span data-stu-id="f247e-104">The `delegate` operator creates an anonymous method that can be converted to a delegate type:</span></span>

[!code-csharp-interactive[anonymous method](snippets/shared/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> <span data-ttu-id="f247e-105">从 C# 3 开始，lambda 表达式提供了一种更简洁和富有表现力的方式来创建匿名函数。</span><span class="sxs-lookup"><span data-stu-id="f247e-105">Beginning with C# 3, lambda expressions provide a more concise and expressive way to create an anonymous function.</span></span> <span data-ttu-id="f247e-106">使用 [=> 运算符](lambda-operator.md)构造 lambda 表达式：</span><span class="sxs-lookup"><span data-stu-id="f247e-106">Use the [=> operator](lambda-operator.md) to construct a lambda expression:</span></span>
>
> [!code-csharp-interactive[lambda expression](snippets/shared/DelegateOperator.cs#Lambda)]
>
> <span data-ttu-id="f247e-107">有关 lambda 表达式功能的更多信息（例如，如何捕获外部变量），请参阅 [lambda 表达式](lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="f247e-107">For more information about features of lambda expressions, for example, capturing outer variables, see [Lambda expressions](lambda-expressions.md).</span></span>

<span data-ttu-id="f247e-108">使用 `delegate` 运算符时，可以省略参数列表。</span><span class="sxs-lookup"><span data-stu-id="f247e-108">When you use the `delegate` operator, you might omit the parameter list.</span></span> <span data-ttu-id="f247e-109">如果这样做，可以将创建的匿名方法转换为具有任何参数列表的委托类型，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="f247e-109">If you do that, the created anonymous method can be converted to a delegate type with any list of  parameters, as the following example shows:</span></span>

[!code-csharp-interactive[no parameter list](snippets/shared/DelegateOperator.cs#WithoutParameterList)]

<span data-ttu-id="f247e-110">这是 lambda 表达式不支持的匿名方法的唯一功能。</span><span class="sxs-lookup"><span data-stu-id="f247e-110">That's the only functionality of anonymous methods that is not supported by lambda expressions.</span></span> <span data-ttu-id="f247e-111">在所有其他情况下，lambda 表达式是编写内联代码的首选方法。</span><span class="sxs-lookup"><span data-stu-id="f247e-111">In all other cases, a lambda expression is a preferred way to write inline code.</span></span>

<span data-ttu-id="f247e-112">还可以使用 `delegate` 关键字声明[委托类型](../builtin-types/reference-types.md#the-delegate-type)。</span><span class="sxs-lookup"><span data-stu-id="f247e-112">You also use the `delegate` keyword to declare a [delegate type](../builtin-types/reference-types.md#the-delegate-type).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f247e-113">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="f247e-113">C# language specification</span></span>

<span data-ttu-id="f247e-114">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)中的 [匿名函数表达式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)部分。</span><span class="sxs-lookup"><span data-stu-id="f247e-114">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f247e-115">另请参阅</span><span class="sxs-lookup"><span data-stu-id="f247e-115">See also</span></span>

- [<span data-ttu-id="f247e-116">C# 参考</span><span class="sxs-lookup"><span data-stu-id="f247e-116">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f247e-117">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="f247e-117">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="f247e-118">=> 运算符</span><span class="sxs-lookup"><span data-stu-id="f247e-118">=> operator</span></span>](lambda-operator.md)
