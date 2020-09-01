---
description: override 修饰符 - C# 参考
title: override 修饰符 - C# 参考
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134453"
---
# <a name="override-c-reference"></a><span data-ttu-id="2aa77-103">override（C# 参考）</span><span class="sxs-lookup"><span data-stu-id="2aa77-103">override (C# Reference)</span></span>

<span data-ttu-id="2aa77-104">扩展或修改继承的方法、属性、索引器或事件的抽象或虚拟实现需要 `override` 修饰符。</span><span class="sxs-lookup"><span data-stu-id="2aa77-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="2aa77-105">示例</span><span class="sxs-lookup"><span data-stu-id="2aa77-105">Example</span></span>

<span data-ttu-id="2aa77-106">在此示例中，`Square` 类必须提供 `GetArea` 的重写实现，因为 `GetArea` 继承自抽象 `Shape` 类：</span><span class="sxs-lookup"><span data-stu-id="2aa77-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="2aa77-107">`override` 方法提供从基类继承的成员的新实现。</span><span class="sxs-lookup"><span data-stu-id="2aa77-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="2aa77-108">通过 `override` 声明重写的方法称为重写基方法。</span><span class="sxs-lookup"><span data-stu-id="2aa77-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="2aa77-109">重写基方法必须具有与 `override` 方法相同的签名。</span><span class="sxs-lookup"><span data-stu-id="2aa77-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="2aa77-110">有关继承的信息，请参阅[继承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="2aa77-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="2aa77-111">不能重写非虚方法或静态方法。</span><span class="sxs-lookup"><span data-stu-id="2aa77-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="2aa77-112">重写基方法必须是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="2aa77-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="2aa77-113">`override` 声明不能更改 `virtual` 方法的可访问性。</span><span class="sxs-lookup"><span data-stu-id="2aa77-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="2aa77-114">`override` 方法和 `virtual` 方法必须具有相同[级别访问修饰符](access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="2aa77-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="2aa77-115">不能使用 `new`、`static` 或 `virtual` 修饰符修改 `override` 方法。</span><span class="sxs-lookup"><span data-stu-id="2aa77-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="2aa77-116">重写属性声明必须指定与继承的属性完全相同的访问修饰符、类型和名称，并且重写的属性必须是 `virtual`、`abstract` 或 `override`。</span><span class="sxs-lookup"><span data-stu-id="2aa77-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="2aa77-117">有关如何使用 `override` 关键字的详细信息，请参阅[使用 Override 和 New 关键字进行版本控制](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)和[了解何时使用 Override 和 New 关键字](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)。</span><span class="sxs-lookup"><span data-stu-id="2aa77-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="2aa77-118">示例</span><span class="sxs-lookup"><span data-stu-id="2aa77-118">Example</span></span>

<span data-ttu-id="2aa77-119">此示例定义一个名为 `Employee` 的基类和一个名为 `SalesEmployee` 的派生类。</span><span class="sxs-lookup"><span data-stu-id="2aa77-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="2aa77-120">`SalesEmployee` 类包含一个额外字段 `salesbonus`，并且重写方法 `CalculatePay` 以将它考虑在内。</span><span class="sxs-lookup"><span data-stu-id="2aa77-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="2aa77-121">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="2aa77-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2aa77-122">请参阅</span><span class="sxs-lookup"><span data-stu-id="2aa77-122">See also</span></span>

- [<span data-ttu-id="2aa77-123">C# 参考</span><span class="sxs-lookup"><span data-stu-id="2aa77-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2aa77-124">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="2aa77-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2aa77-125">继承</span><span class="sxs-lookup"><span data-stu-id="2aa77-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="2aa77-126">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="2aa77-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2aa77-127">修饰符</span><span class="sxs-lookup"><span data-stu-id="2aa77-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2aa77-128">abstract</span><span class="sxs-lookup"><span data-stu-id="2aa77-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="2aa77-129">virtual</span><span class="sxs-lookup"><span data-stu-id="2aa77-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="2aa77-130">new（修饰符）</span><span class="sxs-lookup"><span data-stu-id="2aa77-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="2aa77-131">多态性</span><span class="sxs-lookup"><span data-stu-id="2aa77-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
