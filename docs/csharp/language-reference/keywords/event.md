---
description: event - C# 参考
title: event - C# 参考
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 5e75fec12390cb694126c5bec684c40caa378915
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139094"
---
# <a name="event-c-reference"></a><span data-ttu-id="c7206-103">event (C# 参考)</span><span class="sxs-lookup"><span data-stu-id="c7206-103">event (C# reference)</span></span>

<span data-ttu-id="c7206-104">`event` 关键字用于声明发布服务器类中的事件。</span><span class="sxs-lookup"><span data-stu-id="c7206-104">The `event` keyword is used to declare an event in a publisher class.</span></span>

## <a name="example"></a><span data-ttu-id="c7206-105">示例</span><span class="sxs-lookup"><span data-stu-id="c7206-105">Example</span></span>

<span data-ttu-id="c7206-106">下面的示例演示如何声明和引发使用 <xref:System.EventHandler> 作为基础委托类型的事件。</span><span class="sxs-lookup"><span data-stu-id="c7206-106">The following example shows how to declare and raise an event that uses <xref:System.EventHandler> as the underlying delegate type.</span></span> <span data-ttu-id="c7206-107">有关演示如何使用泛型 <xref:System.EventHandler%601> 委托类型以及如何订阅事件并创建事件处理程序方法的完整的代码示例，请参阅[如何发布符合 .NET Framework 准则的事件](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-107">For the complete code example that also shows how to use the generic <xref:System.EventHandler%601> delegate type and how to subscribe to an event and create an event handler method, see [How to publish events that conform to .NET Framework Guidelines](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).</span></span>

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

<span data-ttu-id="c7206-108">事件是一种特殊的多播委托，仅可以从声明事件的类或结构（发布服务器类）中对其进行调用。</span><span class="sxs-lookup"><span data-stu-id="c7206-108">Events are a special kind of multicast delegate that can only be invoked from within the class or struct where they are declared (the publisher class).</span></span> <span data-ttu-id="c7206-109">如果其他类或结构订阅该事件，则在发布服务器类引发该事件时，将调用其事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="c7206-109">If other classes or structs subscribe to the event, their event handler methods will be called when the publisher class raises the event.</span></span> <span data-ttu-id="c7206-110">有关详细信息和代码示例，请参阅[事件](../../programming-guide/events/index.md)和[委托](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-110">For more information and code examples, see [Events](../../programming-guide/events/index.md) and [Delegates](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="c7206-111">可以将事件标记为[public](./public.md)、[private](./private.md)、[protected](./protected.md)、[internal](./internal.md)、[protected internal](./protected-internal.md) 或 [private protected](./private-protected.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-111">Events can be marked as [public](./public.md), [private](./private.md), [protected](./protected.md), [internal](./internal.md), [protected internal](./protected-internal.md), or [private protected](./private-protected.md).</span></span> <span data-ttu-id="c7206-112">这些访问修饰符定义该类的用户访问该事件的方式。</span><span class="sxs-lookup"><span data-stu-id="c7206-112">These access modifiers define how users of the class can access the event.</span></span> <span data-ttu-id="c7206-113">有关详细信息，请参阅[访问修饰符](../../programming-guide/classes-and-structs/access-modifiers.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-113">For more information, see [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="keywords-and-events"></a><span data-ttu-id="c7206-114">关键字和事件</span><span class="sxs-lookup"><span data-stu-id="c7206-114">Keywords and events</span></span>

<span data-ttu-id="c7206-115">下列关键字应用于事件。</span><span class="sxs-lookup"><span data-stu-id="c7206-115">The following keywords apply to events.</span></span>

|<span data-ttu-id="c7206-116">关键字</span><span class="sxs-lookup"><span data-stu-id="c7206-116">Keyword</span></span>|<span data-ttu-id="c7206-117">说明</span><span class="sxs-lookup"><span data-stu-id="c7206-117">Description</span></span>|<span data-ttu-id="c7206-118">更多信息</span><span class="sxs-lookup"><span data-stu-id="c7206-118">For more information</span></span>|
|-------------|-----------------|--------------------------|
|[<span data-ttu-id="c7206-119">static</span><span class="sxs-lookup"><span data-stu-id="c7206-119">static</span></span>](./static.md)|<span data-ttu-id="c7206-120">使事件可供调用方在任何时候进行调用，即使不存在类的实例。</span><span class="sxs-lookup"><span data-stu-id="c7206-120">Makes the event available to callers at any time, even if no instance of the class exists.</span></span>|[<span data-ttu-id="c7206-121">静态类和静态类成员</span><span class="sxs-lookup"><span data-stu-id="c7206-121">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[<span data-ttu-id="c7206-122">virtual</span><span class="sxs-lookup"><span data-stu-id="c7206-122">virtual</span></span>](./virtual.md)|<span data-ttu-id="c7206-123">允许派生类使用[重写](./override.md)关键字重写事件行为。</span><span class="sxs-lookup"><span data-stu-id="c7206-123">Allows derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span>|[<span data-ttu-id="c7206-124">继承</span><span class="sxs-lookup"><span data-stu-id="c7206-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)|
|[<span data-ttu-id="c7206-125">sealed</span><span class="sxs-lookup"><span data-stu-id="c7206-125">sealed</span></span>](./sealed.md)|<span data-ttu-id="c7206-126">指定对于派生类，它不再是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="c7206-126">Specifies that for derived classes it is no longer virtual.</span></span>||
|[<span data-ttu-id="c7206-127">abstract</span><span class="sxs-lookup"><span data-stu-id="c7206-127">abstract</span></span>](./abstract.md)|<span data-ttu-id="c7206-128">编译器不会生成 `add` 和 `remove` 事件访问器块，因此派生类必须提供其自己的实现。</span><span class="sxs-lookup"><span data-stu-id="c7206-128">The compiler will not generate the `add` and `remove` event accessor blocks and therefore derived classes must provide their own implementation.</span></span>||

<span data-ttu-id="c7206-129">可以通过使用[静态](./static.md)关键字将事件声明为静态事件。</span><span class="sxs-lookup"><span data-stu-id="c7206-129">An event may be declared as a static event by using the [static](./static.md) keyword.</span></span> <span data-ttu-id="c7206-130">这可使事件可供调用方在任何时候进行调用，即使不存在类的实例。</span><span class="sxs-lookup"><span data-stu-id="c7206-130">This makes the event available to callers at any time, even if no instance of the class exists.</span></span> <span data-ttu-id="c7206-131">有关详细信息，请参阅[静态类和静态类成员](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-131">For more information, see [Static Classes and Static Class Members](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>

<span data-ttu-id="c7206-132">可以通过使用[虚拟](./virtual.md)关键字将事件标记为虚事件。</span><span class="sxs-lookup"><span data-stu-id="c7206-132">An event can be marked as a virtual event by using the [virtual](./virtual.md) keyword.</span></span> <span data-ttu-id="c7206-133">这可使派生类使用[重写](./override.md)关键字重写事件行为。</span><span class="sxs-lookup"><span data-stu-id="c7206-133">This enables derived classes to override the event behavior by using the [override](./override.md) keyword.</span></span> <span data-ttu-id="c7206-134">有关详细信息，请参阅[继承](../../programming-guide/classes-and-structs/inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="c7206-134">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span> <span data-ttu-id="c7206-135">重写虚拟事件的事件也可以为[密封](./sealed.md)，指定对于派生类，它不再是虚拟的。</span><span class="sxs-lookup"><span data-stu-id="c7206-135">An event overriding a virtual event can also be [sealed](./sealed.md), which specifies that for derived classes it is no longer virtual.</span></span> <span data-ttu-id="c7206-136">最后，可以声明事件为[抽象](./abstract.md)，这意味着编译器将不会生成 `add` 和 `remove` 事件访问器块。</span><span class="sxs-lookup"><span data-stu-id="c7206-136">Lastly, an event can be declared [abstract](./abstract.md), which means that the compiler will not generate the `add` and `remove` event accessor blocks.</span></span> <span data-ttu-id="c7206-137">因此，派生类必须提供其自己的实现。</span><span class="sxs-lookup"><span data-stu-id="c7206-137">Therefore derived classes must provide their own implementation.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7206-138">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="c7206-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c7206-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="c7206-139">See also</span></span>

- [<span data-ttu-id="c7206-140">C# 参考</span><span class="sxs-lookup"><span data-stu-id="c7206-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7206-141">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="c7206-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7206-142">C# 关键字</span><span class="sxs-lookup"><span data-stu-id="c7206-142">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c7206-143">add</span><span class="sxs-lookup"><span data-stu-id="c7206-143">add</span></span>](./add.md)
- [<span data-ttu-id="c7206-144">remove</span><span class="sxs-lookup"><span data-stu-id="c7206-144">remove</span></span>](./remove.md)
- [<span data-ttu-id="c7206-145">修饰符</span><span class="sxs-lookup"><span data-stu-id="c7206-145">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c7206-146">如何合并委托（多播委托）</span><span class="sxs-lookup"><span data-stu-id="c7206-146">How to combine delegates (Multicast Delegates)</span></span>](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
