---
title: + 和 += 运算符 - C# 参考
ms.date: 04/23/2020
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: f1db0054ad2411bfe23f10b64bc2727a71ad7463
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916951"
---
# <a name="-and--operators-c-reference"></a><span data-ttu-id="7239f-102">+ 和 += 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="7239f-102">+ and += operators (C# reference)</span></span>

<span data-ttu-id="7239f-103">内置[整型](../builtin-types/integral-numeric-types.md)和[浮点](../builtin-types/floating-point-numeric-types.md)数值类型、[字符串](../builtin-types/reference-types.md#the-string-type)类型以及[委托](../builtin-types/reference-types.md#the-delegate-type)类型支持 `+` 和 `+=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="7239f-103">The `+` and `+=` operators are supported by the built-in [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types, the [string](../builtin-types/reference-types.md#the-string-type) type, and [delegate](../builtin-types/reference-types.md#the-delegate-type) types.</span></span>

<span data-ttu-id="7239f-104">有关算术 `+` 运算符的信息，请参阅[一元加和减运算符](arithmetic-operators.md#unary-plus-and-minus-operators)和[算术运算符](arithmetic-operators.md)文章的[加法运算符 +](arithmetic-operators.md#addition-operator-) 部分。</span><span class="sxs-lookup"><span data-stu-id="7239f-104">For information about the arithmetic `+` operator, see the [Unary plus and minus operators](arithmetic-operators.md#unary-plus-and-minus-operators) and [Addition operator +](arithmetic-operators.md#addition-operator-) sections of the [Arithmetic operators](arithmetic-operators.md) article.</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="7239f-105">字符串串联</span><span class="sxs-lookup"><span data-stu-id="7239f-105">String concatenation</span></span>

<span data-ttu-id="7239f-106">当其中的一个操作数是[字符串](../builtin-types/reference-types.md#the-string-type)类型或两个操作数都是字符串类型时，`+` 运算符将其操作数的字符串表示形式（`null` 的字符串表示形式）串联在一起：</span><span class="sxs-lookup"><span data-stu-id="7239f-106">When one or both operands are of type [string](../builtin-types/reference-types.md#the-string-type), the `+` operator concatenates the string representations of its operands (the string representation of `null` is an empty string):</span></span>

[!code-csharp-interactive[string concatenation](snippets/shared/AdditionOperator.cs#AddStrings)]

<span data-ttu-id="7239f-107">从 C# 6 开始，[字符串内插](../tokens/interpolated.md)提供了格式化字符串更为便捷的方式：</span><span class="sxs-lookup"><span data-stu-id="7239f-107">Beginning with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](snippets/shared/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="7239f-108">委托组合</span><span class="sxs-lookup"><span data-stu-id="7239f-108">Delegate combination</span></span>

<span data-ttu-id="7239f-109">对于[委托](../builtin-types/reference-types.md#the-delegate-type)类型相同的操作数，`+` 运算符在调用时返回新的委托实例，调用左侧的操作数，然后调用右侧的操作数。</span><span class="sxs-lookup"><span data-stu-id="7239f-109">For operands of the same [delegate](../builtin-types/reference-types.md#the-delegate-type) type, the `+` operator returns a new delegate instance that, when invoked, invokes the left-hand operand and then invokes the right-hand operand.</span></span> <span data-ttu-id="7239f-110">如果任何操作数均为 `null`，则 `+` 运算符将返回另一个操作数（也可能是 `null`）的值。</span><span class="sxs-lookup"><span data-stu-id="7239f-110">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="7239f-111">下面的示例演示如何组合使用委托和 `+` 运算符：</span><span class="sxs-lookup"><span data-stu-id="7239f-111">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](snippets/shared/AdditionOperator.cs#AddDelegates)]

<span data-ttu-id="7239f-112">若要执行委托删除，请使用 [`-` 运算符](subtraction-operator.md#delegate-removal)。</span><span class="sxs-lookup"><span data-stu-id="7239f-112">To perform delegate removal, use the [`-` operator](subtraction-operator.md#delegate-removal).</span></span>

<span data-ttu-id="7239f-113">有关委托类型的详细信息，请参阅[委托](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7239f-113">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="addition-assignment-operator-"></a><span data-ttu-id="7239f-114">加法赋值运算符 +=</span><span class="sxs-lookup"><span data-stu-id="7239f-114">Addition assignment operator +=</span></span>

<span data-ttu-id="7239f-115">使用 `+=` 运算符的表达式，例如</span><span class="sxs-lookup"><span data-stu-id="7239f-115">An expression using the `+=` operator, such as</span></span>

```csharp
x += y
```

<span data-ttu-id="7239f-116">等效于</span><span class="sxs-lookup"><span data-stu-id="7239f-116">is equivalent to</span></span>

```csharp
x = x + y
```

<span data-ttu-id="7239f-117">不同的是 `x` 只计算一次。</span><span class="sxs-lookup"><span data-stu-id="7239f-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="7239f-118">下面的示例演示 `+=` 运算符的用法：</span><span class="sxs-lookup"><span data-stu-id="7239f-118">The following example demonstrates the usage of the `+=` operator:</span></span>

[!code-csharp-interactive[+= examples](snippets/shared/AdditionOperator.cs#AddAndAssign)]

<span data-ttu-id="7239f-119">在订阅[事件](../keywords/event.md)时，还可以使用 `+=` 运算符来指定事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="7239f-119">You also use the `+=` operator to specify an event handler method when you subscribe to an [event](../keywords/event.md).</span></span> <span data-ttu-id="7239f-120">有关详细信息，请参阅[如何：订阅和取消订阅事件](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="7239f-120">For more information, see [How to: subscribe to and unsubscribe from events](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="7239f-121">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="7239f-121">Operator overloadability</span></span>

<span data-ttu-id="7239f-122">用户定义的类型可以[重载](operator-overloading.md)`+` 运算符。</span><span class="sxs-lookup"><span data-stu-id="7239f-122">A user-defined type can [overload](operator-overloading.md) the `+` operator.</span></span> <span data-ttu-id="7239f-123">重载二元 `+` 运算符后，也会隐式重载 `+=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="7239f-123">When a binary `+` operator is overloaded, the `+=` operator is also implicitly overloaded.</span></span> <span data-ttu-id="7239f-124">用户定义类型不能显式重载 `+=` 运算符。</span><span class="sxs-lookup"><span data-stu-id="7239f-124">A user-defined type cannot explicitly overload the `+=` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7239f-125">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="7239f-125">C# language specification</span></span>

<span data-ttu-id="7239f-126">有关详细信息，请参阅[C# 语言规范](~/_csharplang/spec/introduction.md)的[一元加运算符](~/_csharplang/spec/expressions.md#unary-plus-operator)和[加法运算符](~/_csharplang/spec/expressions.md#addition-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="7239f-126">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7239f-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="7239f-127">See also</span></span>

- [<span data-ttu-id="7239f-128">C# 参考</span><span class="sxs-lookup"><span data-stu-id="7239f-128">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7239f-129">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="7239f-129">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="7239f-130">如何连接多个字符串</span><span class="sxs-lookup"><span data-stu-id="7239f-130">How to concatenate multiple strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="7239f-131">事件</span><span class="sxs-lookup"><span data-stu-id="7239f-131">Events</span></span>](../../programming-guide/events/index.md)
- [<span data-ttu-id="7239f-132">算术运算符</span><span class="sxs-lookup"><span data-stu-id="7239f-132">Arithmetic operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="7239f-133">- 和 -= 运算符</span><span class="sxs-lookup"><span data-stu-id="7239f-133">- and -= operators</span></span>](subtraction-operator.md)
