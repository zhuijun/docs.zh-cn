---
description: new 运算符 - C# 参考
title: new 运算符 - C# 参考
ms.date: 10/02/2020
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 3125f3d2c694dcfc5682ee482f3f76072ac3726d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609377"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="66c47-103">new 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="66c47-103">new operator (C# reference)</span></span>

<span data-ttu-id="66c47-104">`new` 运算符创建类型的新实例。</span><span class="sxs-lookup"><span data-stu-id="66c47-104">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="66c47-105">`new` 关键字还可用作[成员声明修饰符](../keywords/new-modifier.md)或[泛型类型约束](../keywords/new-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="66c47-105">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="66c47-106">构造函数调用</span><span class="sxs-lookup"><span data-stu-id="66c47-106">Constructor invocation</span></span>

<span data-ttu-id="66c47-107">要创建类型的新实例，通常使用 `new` 运算符调用该类型的某个[构造函数](../../programming-guide/classes-and-structs/constructors.md)：</span><span class="sxs-lookup"><span data-stu-id="66c47-107">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="66c47-108">可以使用带有 `new` 运算符的[对象或集合初始值设定项](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)实例化和初始化一个语句中的对象，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="66c47-108">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

<span data-ttu-id="66c47-109">从 C# 9.0 开始，构造调用表达式由目标确定类型。</span><span class="sxs-lookup"><span data-stu-id="66c47-109">Beginning with C# 9.0, constructor invocation expressions are target-typed.</span></span> <span data-ttu-id="66c47-110">也就是说，如果已知表达式的目标类型，则可以省略类型名称，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="66c47-110">That is, if a target type of an expression is known, you can omit a type name, as the following example shows:</span></span>

:::code language="csharp" source="snippets/shared/NewOperator.cs" id="SnippetTargetTyped":::

<span data-ttu-id="66c47-111">如前面的示例所示，在由目标确定类型的 `new` 表达式中始终使用括号。</span><span class="sxs-lookup"><span data-stu-id="66c47-111">As the preceding example shows, you always use parentheses in a target-typed `new` expression.</span></span>

<span data-ttu-id="66c47-112">如果 `new` 表达式的目标类型未知（例如使用 [`var`](../keywords/var.md) 关键字时），必须指定类型名称。</span><span class="sxs-lookup"><span data-stu-id="66c47-112">If a target type of a `new` expression is unknown (for example, when you use the [`var`](../keywords/var.md) keyword), you must specify a type name.</span></span>

## <a name="array-creation"></a><span data-ttu-id="66c47-113">数组创建</span><span class="sxs-lookup"><span data-stu-id="66c47-113">Array creation</span></span>

<span data-ttu-id="66c47-114">还可以使用 `new` 运算符创建数组实例，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="66c47-114">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="66c47-115">使用数组初始化语法创建数组实例，并在一个语句中使用元素填充该实例。</span><span class="sxs-lookup"><span data-stu-id="66c47-115">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="66c47-116">以下示例显示可以执行该操作的各种方法：</span><span class="sxs-lookup"><span data-stu-id="66c47-116">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="66c47-117">有关数组的详细信息，请参阅[数组](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="66c47-117">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="66c47-118">匿名类型的实例化</span><span class="sxs-lookup"><span data-stu-id="66c47-118">Instantiation of anonymous types</span></span>

<span data-ttu-id="66c47-119">要创建[匿名类型](../../programming-guide/classes-and-structs/anonymous-types.md)的实例，请使用 `new` 运算符和对象初始值设定项语法：</span><span class="sxs-lookup"><span data-stu-id="66c47-119">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="66c47-120">类型实例的析构</span><span class="sxs-lookup"><span data-stu-id="66c47-120">Destruction of type instances</span></span>

<span data-ttu-id="66c47-121">无需销毁此前创建的类型实例。</span><span class="sxs-lookup"><span data-stu-id="66c47-121">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="66c47-122">引用和值类型的实例将自动销毁。</span><span class="sxs-lookup"><span data-stu-id="66c47-122">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="66c47-123">包含值类型的上下文销毁后，值类型的实例随之销毁。</span><span class="sxs-lookup"><span data-stu-id="66c47-123">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="66c47-124">在引用类型的最后一次引用被删除后，[垃圾回收器](../../../standard/garbage-collection/index.md)会在某个非指定的时间销毁其实例。</span><span class="sxs-lookup"><span data-stu-id="66c47-124">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="66c47-125">对于包含非托管资源的类型实例（例如，文件句柄），建议采用确定性的清理来确保尽快释放其包含的资源。</span><span class="sxs-lookup"><span data-stu-id="66c47-125">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="66c47-126">有关详细信息，请参阅 <xref:System.IDisposable?displayProperty=nameWithType> API 参考和 [using 语句](../keywords/using-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="66c47-126">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="66c47-127">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="66c47-127">Operator overloadability</span></span>

<span data-ttu-id="66c47-128">用户定义的类型不能重载 `new` 运算符。</span><span class="sxs-lookup"><span data-stu-id="66c47-128">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="66c47-129">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="66c47-129">C# language specification</span></span>

<span data-ttu-id="66c47-130">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的 [new 运算符](~/_csharplang/spec/expressions.md#the-new-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="66c47-130">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="66c47-131">有关条件由目标确定类型的 `new` 表达式的详细信息，请参阅[功能建议说明](~/_csharplang/proposals/csharp-9.0/target-typed-new.md)。</span><span class="sxs-lookup"><span data-stu-id="66c47-131">For more information about a target-typed `new` expression, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/target-typed-new.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66c47-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="66c47-132">See also</span></span>

- [<span data-ttu-id="66c47-133">C# 参考</span><span class="sxs-lookup"><span data-stu-id="66c47-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="66c47-134">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="66c47-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="66c47-135">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="66c47-135">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
