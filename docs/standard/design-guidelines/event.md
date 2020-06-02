---
title: 事件设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: 852c99b1a41691911f7ae82d3b8104526811757d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289819"
---
# <a name="event-design"></a><span data-ttu-id="33e31-102">事件设计</span><span class="sxs-lookup"><span data-stu-id="33e31-102">Event Design</span></span>
<span data-ttu-id="33e31-103">事件是最常用的回调形式（构造，允许框架调入用户代码）。</span><span class="sxs-lookup"><span data-stu-id="33e31-103">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="33e31-104">其他回调机制包括采用委托、虚拟成员和基于接口的插件的成员。可用性研究的数据表明，大多数开发人员比使用其他回调机制更喜欢使用事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-104">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="33e31-105">事件与 Visual Studio 和多种语言完美集成。</span><span class="sxs-lookup"><span data-stu-id="33e31-105">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="33e31-106">需要注意的是，有两组事件：在系统状态发生更改之前引发的事件（称为前期事件）和状态更改后引发的事件（称为后期事件）。</span><span class="sxs-lookup"><span data-stu-id="33e31-106">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="33e31-107">预事件的一个示例是 `Form.Closing` ，在关闭窗体前引发。</span><span class="sxs-lookup"><span data-stu-id="33e31-107">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="33e31-108">后事件的一个示例是 `Form.Closed` ，它在窗体关闭后引发。</span><span class="sxs-lookup"><span data-stu-id="33e31-108">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="33e31-109">✔️对事件（而不是 "火灾" 或 "trigger"）使用术语 "引发"。</span><span class="sxs-lookup"><span data-stu-id="33e31-109">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="33e31-110">✔️使用 <xref:System.EventHandler%601?displayProperty=nameWithType> 而不是手动创建要用作事件处理程序的新委托。</span><span class="sxs-lookup"><span data-stu-id="33e31-110">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="33e31-111">✔️考虑使用 <xref:System.EventArgs> 作为事件参数的子类，除非你完全确保该事件从不需要将任何数据传递到事件处理方法，在这种情况下，你可以直接使用该 `EventArgs` 类型。</span><span class="sxs-lookup"><span data-stu-id="33e31-111">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="33e31-112">如果直接使用发送 API `EventArgs` ，则永远不能添加与事件一起使用的任何数据，而不会破坏兼容性。</span><span class="sxs-lookup"><span data-stu-id="33e31-112">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="33e31-113">如果使用子类（即使最初完全为空），则在需要时可以将属性添加到子类。</span><span class="sxs-lookup"><span data-stu-id="33e31-113">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="33e31-114">✔️使用受保护的虚拟方法引发每个事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-114">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="33e31-115">这仅适用于未密封的类上的非静态事件，而不适用于结构、密封类或静态事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-115">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="33e31-116">此方法的目的是为派生类提供一种使用替代来处理事件的方法。</span><span class="sxs-lookup"><span data-stu-id="33e31-116">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="33e31-117">重写是处理派生类中的基类事件的更灵活、更快、更自然的方式。</span><span class="sxs-lookup"><span data-stu-id="33e31-117">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="33e31-118">按照约定，方法的名称应以 "On" 开头，后面跟有事件的名称。</span><span class="sxs-lookup"><span data-stu-id="33e31-118">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="33e31-119">派生类可以选择不在其重写中调用方法的基实现。</span><span class="sxs-lookup"><span data-stu-id="33e31-119">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="33e31-120">为此，请不要在基类正常工作所需的方法中包括任何处理。</span><span class="sxs-lookup"><span data-stu-id="33e31-120">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="33e31-121">✔️会对引发事件的受保护方法执行一个参数。</span><span class="sxs-lookup"><span data-stu-id="33e31-121">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="33e31-122">应将参数命名为 `e` ，并将其类型化为事件参数类。</span><span class="sxs-lookup"><span data-stu-id="33e31-122">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="33e31-123">❌引发非静态事件时，不要将 null 作为发件人传递。</span><span class="sxs-lookup"><span data-stu-id="33e31-123">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="33e31-124">✔️在引发静态事件时将 null 作为发件人传递。</span><span class="sxs-lookup"><span data-stu-id="33e31-124">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="33e31-125">❌引发事件时，请勿传递 null 作为事件数据参数。</span><span class="sxs-lookup"><span data-stu-id="33e31-125">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="33e31-126">`EventArgs.Empty`如果不想将任何数据传递到事件处理方法，则应传递。</span><span class="sxs-lookup"><span data-stu-id="33e31-126">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="33e31-127">开发人员希望此参数不为 null。</span><span class="sxs-lookup"><span data-stu-id="33e31-127">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="33e31-128">✔️考虑引发最终用户可以取消的事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-128">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="33e31-129">这仅适用于预事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-129">This only applies to pre-events.</span></span>

 <span data-ttu-id="33e31-130">使用 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> 或其子类作为事件参数，以允许最终用户取消事件。</span><span class="sxs-lookup"><span data-stu-id="33e31-130">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="33e31-131">自定义事件处理程序设计</span><span class="sxs-lookup"><span data-stu-id="33e31-131">Custom Event Handler Design</span></span>
 <span data-ttu-id="33e31-132">有些情况下 `EventHandler<T>` ，不能使用，例如当框架需要使用早期版本的 CLR 时，这种情况不支持泛型。</span><span class="sxs-lookup"><span data-stu-id="33e31-132">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="33e31-133">在这种情况下，可能需要设计和开发自定义事件处理程序委托。</span><span class="sxs-lookup"><span data-stu-id="33e31-133">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="33e31-134">✔️使用 void 的返回类型作为事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="33e31-134">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="33e31-135">事件处理程序可以调用多个事件处理方法（可能在多个对象上）。</span><span class="sxs-lookup"><span data-stu-id="33e31-135">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="33e31-136">如果允许事件处理方法返回值，则每个事件调用都有多个返回值。</span><span class="sxs-lookup"><span data-stu-id="33e31-136">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="33e31-137">✔️使用 `object` 作为事件处理程序的第一个参数的类型，并调用它 `sender` 。</span><span class="sxs-lookup"><span data-stu-id="33e31-137">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="33e31-138">✔️使用 <xref:System.EventArgs?displayProperty=nameWithType> 或其子类作为事件处理程序的第二个参数的类型，并调用它 `e` 。</span><span class="sxs-lookup"><span data-stu-id="33e31-138">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="33e31-139">❌在事件处理程序中，不能有两个以上的参数。</span><span class="sxs-lookup"><span data-stu-id="33e31-139">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="33e31-140">*部分©2005，2009 Microsoft Corporation。保留所有权利。*</span><span class="sxs-lookup"><span data-stu-id="33e31-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="33e31-141">*皮尔逊教育，Inc. 的经许可重印权限[：从框架设计指导原则：用于可重复使用的 .Net 库的约定、惯例和模式、第2版](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)By Krzysztof Cwalina 和 Brad Abrams，发布十月22，2008，作为 Microsoft Windows 开发系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="33e31-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="33e31-142">另请参阅</span><span class="sxs-lookup"><span data-stu-id="33e31-142">See also</span></span>

- [<span data-ttu-id="33e31-143">成员设计准则</span><span class="sxs-lookup"><span data-stu-id="33e31-143">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="33e31-144">框架设计准则</span><span class="sxs-lookup"><span data-stu-id="33e31-144">Framework Design Guidelines</span></span>](index.md)
