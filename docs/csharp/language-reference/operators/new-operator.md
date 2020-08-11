---
title: new 运算符 - C# 参考
ms.date: 06/25/2019
f1_keywords:
- new_CSharpKeyword
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 42128cf23fe2410bf33bb40131843325939646de
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916761"
---
# <a name="new-operator-c-reference"></a><span data-ttu-id="06ab7-102">new 运算符（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="06ab7-102">new operator (C# reference)</span></span>

<span data-ttu-id="06ab7-103">`new` 运算符创建类型的新实例。</span><span class="sxs-lookup"><span data-stu-id="06ab7-103">The `new` operator creates a new instance of a type.</span></span>

<span data-ttu-id="06ab7-104">`new` 关键字还可用作[成员声明修饰符](../keywords/new-modifier.md)或[泛型类型约束](../keywords/new-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="06ab7-104">You can also use the `new` keyword as a [member declaration modifier](../keywords/new-modifier.md) or a [generic type constraint](../keywords/new-constraint.md).</span></span>

## <a name="constructor-invocation"></a><span data-ttu-id="06ab7-105">构造函数调用</span><span class="sxs-lookup"><span data-stu-id="06ab7-105">Constructor invocation</span></span>

<span data-ttu-id="06ab7-106">要创建类型的新实例，通常使用 `new` 运算符调用该类型的某个[构造函数](../../programming-guide/classes-and-structs/constructors.md)：</span><span class="sxs-lookup"><span data-stu-id="06ab7-106">To create a new instance of a type, you typically invoke one of the [constructors](../../programming-guide/classes-and-structs/constructors.md) of that type using the `new` operator:</span></span>

[!code-csharp-interactive[invoke constructor](snippets/shared/NewOperator.cs#Constructor)]

<span data-ttu-id="06ab7-107">可以使用带有 `new` 运算符的[对象或集合初始值设定项](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)实例化和初始化一个语句中的对象，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="06ab7-107">You can use an [object or collection initializer](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) with the `new` operator to instantiate and initialize an object in one statement, as the following example shows:</span></span>

[!code-csharp-interactive[constructor with initializer](snippets/shared/NewOperator.cs#ConstructorWithInitializer)]

## <a name="array-creation"></a><span data-ttu-id="06ab7-108">数组创建</span><span class="sxs-lookup"><span data-stu-id="06ab7-108">Array creation</span></span>

<span data-ttu-id="06ab7-109">还可以使用 `new` 运算符创建数组实例，如下例所示：</span><span class="sxs-lookup"><span data-stu-id="06ab7-109">You also use the `new` operator to create an array instance, as the following example shows:</span></span>

[!code-csharp-interactive[create array](snippets/shared/NewOperator.cs#Array)]

<span data-ttu-id="06ab7-110">使用数组初始化语法创建数组实例，并在一个语句中使用元素填充该实例。</span><span class="sxs-lookup"><span data-stu-id="06ab7-110">Use array initialization syntax to create an array instance and populate it with elements in one statement.</span></span> <span data-ttu-id="06ab7-111">以下示例显示可以执行该操作的各种方法：</span><span class="sxs-lookup"><span data-stu-id="06ab7-111">The following example shows various ways how you can do that:</span></span>

[!code-csharp-interactive[initialize array](snippets/shared/NewOperator.cs#ArrayInitialization)]

<span data-ttu-id="06ab7-112">有关数组的详细信息，请参阅[数组](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="06ab7-112">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

## <a name="instantiation-of-anonymous-types"></a><span data-ttu-id="06ab7-113">匿名类型的实例化</span><span class="sxs-lookup"><span data-stu-id="06ab7-113">Instantiation of anonymous types</span></span>

<span data-ttu-id="06ab7-114">要创建[匿名类型](../../programming-guide/classes-and-structs/anonymous-types.md)的实例，请使用 `new` 运算符和对象初始值设定项语法：</span><span class="sxs-lookup"><span data-stu-id="06ab7-114">To create an instance of an [anonymous type](../../programming-guide/classes-and-structs/anonymous-types.md), use the `new` operator and object initializer syntax:</span></span>

[!code-csharp-interactive[anonymous type](snippets/shared/NewOperator.cs#AnonymousType)]

## <a name="destruction-of-type-instances"></a><span data-ttu-id="06ab7-115">类型实例的析构</span><span class="sxs-lookup"><span data-stu-id="06ab7-115">Destruction of type instances</span></span>

<span data-ttu-id="06ab7-116">无需销毁此前创建的类型实例。</span><span class="sxs-lookup"><span data-stu-id="06ab7-116">You don't have to destroy earlier created type instances.</span></span> <span data-ttu-id="06ab7-117">引用和值类型的实例将自动销毁。</span><span class="sxs-lookup"><span data-stu-id="06ab7-117">Instances of both reference and value types are destroyed automatically.</span></span> <span data-ttu-id="06ab7-118">包含值类型的上下文销毁后，值类型的实例随之销毁。</span><span class="sxs-lookup"><span data-stu-id="06ab7-118">Instances of value types are destroyed as soon as the context that contains them is destroyed.</span></span> <span data-ttu-id="06ab7-119">在引用类型的最后一次引用被删除后，[垃圾回收器](../../../standard/garbage-collection/index.md)会在某个非指定的时间销毁其实例。</span><span class="sxs-lookup"><span data-stu-id="06ab7-119">Instances of reference types are destroyed by the [garbage collector](../../../standard/garbage-collection/index.md) at some unspecified time after the last reference to them is removed.</span></span>

<span data-ttu-id="06ab7-120">对于包含非托管资源的类型实例（例如，文件句柄），建议采用确定性的清理来确保尽快释放其包含的资源。</span><span class="sxs-lookup"><span data-stu-id="06ab7-120">For type instances that contain unmanaged resources, for example, a file handle, it's recommended to employ deterministic clean-up to ensure that the resources they contain are released as soon as possible.</span></span> <span data-ttu-id="06ab7-121">有关详细信息，请参阅 <xref:System.IDisposable?displayProperty=nameWithType> API 参考和 [using 语句](../keywords/using-statement.md)一文。</span><span class="sxs-lookup"><span data-stu-id="06ab7-121">For more information, see the <xref:System.IDisposable?displayProperty=nameWithType> API reference and the [using statement](../keywords/using-statement.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="06ab7-122">运算符可重载性</span><span class="sxs-lookup"><span data-stu-id="06ab7-122">Operator overloadability</span></span>

<span data-ttu-id="06ab7-123">用户定义的类型不能重载 `new` 运算符。</span><span class="sxs-lookup"><span data-stu-id="06ab7-123">A user-defined type cannot overload the `new` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06ab7-124">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="06ab7-124">C# language specification</span></span>

<span data-ttu-id="06ab7-125">有关详细信息，请参阅 [C# 语言规范](~/_csharplang/spec/introduction.md)的 [new 运算符](~/_csharplang/spec/expressions.md#the-new-operator)部分。</span><span class="sxs-lookup"><span data-stu-id="06ab7-125">For more information, see [The new operator](~/_csharplang/spec/expressions.md#the-new-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06ab7-126">请参阅</span><span class="sxs-lookup"><span data-stu-id="06ab7-126">See also</span></span>

- [<span data-ttu-id="06ab7-127">C# 参考</span><span class="sxs-lookup"><span data-stu-id="06ab7-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="06ab7-128">C# 运算符和表达式</span><span class="sxs-lookup"><span data-stu-id="06ab7-128">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="06ab7-129">对象和集合初始值设定项</span><span class="sxs-lookup"><span data-stu-id="06ab7-129">Object and collection initializers</span></span>](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)
