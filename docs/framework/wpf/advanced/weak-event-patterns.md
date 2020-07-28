---
title: 弱事件模式
description: 了解 Windows Presentation Foundation 弱事件模式，它解决未销毁的处理程序的问题，避免内存泄漏。
ms.date: 03/30/2017
helpviewer_keywords:
- weak event pattern implementation [WPF]
- event handlers [WPF], weak event pattern
- IWeakEventListener interface [WPF]
ms.assetid: e7c62920-4812-4811-94d8-050a65c856f6
ms.openlocfilehash: 75c6888c8ac20c41d13e3787005377c75248c5d9
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168269"
---
# <a name="weak-event-patterns"></a><span data-ttu-id="bce3f-103">弱事件模式</span><span class="sxs-lookup"><span data-stu-id="bce3f-103">Weak Event Patterns</span></span>
<span data-ttu-id="bce3f-104">在应用程序中，附加到事件源的处理程序可能不会与附加了该处理程序的侦听器对象一起销毁。</span><span class="sxs-lookup"><span data-stu-id="bce3f-104">In applications, it is possible that handlers that are attached to event sources will not be destroyed in coordination with the listener object that attached the handler to the source.</span></span> <span data-ttu-id="bce3f-105">这种情况可能会导致内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="bce3f-105">This situation can lead to memory leaks.</span></span> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="bce3f-106">引入了一种可用于解决此问题的设计模式，方法是为特定事件提供一个专用的管理器类，并在该事件的侦听器上实现一个接口。</span><span class="sxs-lookup"><span data-stu-id="bce3f-106">introduces a design pattern that can be used to address this issue, by providing a dedicated manager class for particular events and implementing an interface on listeners for that event.</span></span> <span data-ttu-id="bce3f-107">此设计模式称为*弱事件模式*。</span><span class="sxs-lookup"><span data-stu-id="bce3f-107">This design pattern is known as the *weak event pattern*.</span></span>  
  
## <a name="why-implement-the-weak-event-pattern"></a><span data-ttu-id="bce3f-108">为什么要实现弱事件模式？</span><span class="sxs-lookup"><span data-stu-id="bce3f-108">Why Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="bce3f-109">侦听事件可能会导致内存泄漏。</span><span class="sxs-lookup"><span data-stu-id="bce3f-109">Listening for events can lead to memory leaks.</span></span> <span data-ttu-id="bce3f-110">侦听事件的典型方法是使用特定于语言的语法，将处理程序附加到源上的事件。</span><span class="sxs-lookup"><span data-stu-id="bce3f-110">The typical technique for listening to an event is to use the language-specific syntax that attaches a handler to an event on a source.</span></span> <span data-ttu-id="bce3f-111">例如，在 c # 中，该语法为： `source.SomeEvent += new SomeEventHandler(MyEventHandler)` 。</span><span class="sxs-lookup"><span data-stu-id="bce3f-111">For example, in C#, that syntax is: `source.SomeEvent += new SomeEventHandler(MyEventHandler)`.</span></span>  
  
 <span data-ttu-id="bce3f-112">此方法可创建从事件源到事件侦听器的强引用。</span><span class="sxs-lookup"><span data-stu-id="bce3f-112">This technique creates a strong reference from the event source to the event listener.</span></span> <span data-ttu-id="bce3f-113">通常情况下，附加侦听器的事件处理程序会导致侦听器具有对象生存期，该生存期受源的对象生存期影响（除非显式移除事件处理程序）。</span><span class="sxs-lookup"><span data-stu-id="bce3f-113">Ordinarily, attaching an event handler for a listener causes the listener to have an object lifetime that is influenced by the object lifetime of the source (unless the event handler is explicitly removed).</span></span> <span data-ttu-id="bce3f-114">但在某些情况下，您可能希望侦听器的对象生存期由其他因素控制，如当前是否属于应用程序的可视化树，而不是源的生存期。</span><span class="sxs-lookup"><span data-stu-id="bce3f-114">But in certain circumstances, you might want the object lifetime of the listener to be controlled by other factors, such as whether it currently belongs to the visual tree of the application, and not by the lifetime of the source.</span></span> <span data-ttu-id="bce3f-115">只要源对象生存期超出侦听器的对象生存期，一般事件模式会导致内存泄漏：侦听器的活动时间比预期时间长。</span><span class="sxs-lookup"><span data-stu-id="bce3f-115">Whenever the source object lifetime extends beyond the object lifetime of the listener, the normal event pattern leads to a memory leak: the listener is kept alive longer than intended.</span></span>  
  
 <span data-ttu-id="bce3f-116">弱事件模式旨在解决此内存泄漏问题。</span><span class="sxs-lookup"><span data-stu-id="bce3f-116">The weak event pattern is designed to solve this memory leak problem.</span></span> <span data-ttu-id="bce3f-117">当侦听器需要注册事件时，可以使用弱事件模式，但侦听器不会明确知道何时取消注册。</span><span class="sxs-lookup"><span data-stu-id="bce3f-117">The weak event pattern can be used whenever a listener needs to register for an event, but the listener does not explicitly know when to unregister.</span></span> <span data-ttu-id="bce3f-118">如果源的对象生存期超出侦听器的有用对象生存期，还可以使用弱事件模式。</span><span class="sxs-lookup"><span data-stu-id="bce3f-118">The weak event pattern can also be used whenever the object lifetime of the source exceeds the useful object lifetime of the listener.</span></span> <span data-ttu-id="bce3f-119">（在这种情况下，*很有用*由您决定。）弱事件模式允许侦听器注册并接收事件，而不会以任何方式影响侦听器的对象生存期特性。</span><span class="sxs-lookup"><span data-stu-id="bce3f-119">(In this case, *useful* is determined by you.) The weak event pattern allows the listener to register for and receive the event without affecting the object lifetime characteristics of the listener in any way.</span></span> <span data-ttu-id="bce3f-120">实际上，来自源的隐含引用不确定侦听器是否符合垃圾回收的条件。</span><span class="sxs-lookup"><span data-stu-id="bce3f-120">In effect, the implied reference from the source does not determine whether the listener is eligible for garbage collection.</span></span> <span data-ttu-id="bce3f-121">引用是弱引用，因此是弱事件模式和相关 Api 的命名。</span><span class="sxs-lookup"><span data-stu-id="bce3f-121">The reference is a weak reference, thus the naming of the weak event pattern and the related APIs.</span></span> <span data-ttu-id="bce3f-122">侦听器可以进行垃圾回收或销毁，并且源可以继续，而不会将构成处理程序引用保留给现在已销毁的对象。</span><span class="sxs-lookup"><span data-stu-id="bce3f-122">The listener can be garbage collected or otherwise destroyed, and the source can continue without retaining noncollectible handler references to a now destroyed object.</span></span>  
  
## <a name="who-should-implement-the-weak-event-pattern"></a><span data-ttu-id="bce3f-123">谁应该实现弱事件模式？</span><span class="sxs-lookup"><span data-stu-id="bce3f-123">Who Should Implement the Weak Event Pattern?</span></span>  
 <span data-ttu-id="bce3f-124">实现弱事件模式主要是为了使控件作者感兴趣。</span><span class="sxs-lookup"><span data-stu-id="bce3f-124">Implementing the weak event pattern is interesting primarily for control authors.</span></span> <span data-ttu-id="bce3f-125">作为控件作者，您主要负责控制您的控件的行为和包含以及它对插入它的应用程序的影响。</span><span class="sxs-lookup"><span data-stu-id="bce3f-125">As a control author, you are largely responsible for the behavior and containment of your control and the impact it has on applications in which it is inserted.</span></span> <span data-ttu-id="bce3f-126">这包括控件对象生存期行为，尤其是处理所述的内存泄漏问题。</span><span class="sxs-lookup"><span data-stu-id="bce3f-126">This includes the control object lifetime behavior, in particular the handling of the described memory leak problem.</span></span>  
  
 <span data-ttu-id="bce3f-127">某些方案本身就是应用弱事件模式。</span><span class="sxs-lookup"><span data-stu-id="bce3f-127">Certain scenarios inherently lend themselves to the application of the weak event pattern.</span></span> <span data-ttu-id="bce3f-128">这种情况是数据绑定。</span><span class="sxs-lookup"><span data-stu-id="bce3f-128">One such scenario is data binding.</span></span> <span data-ttu-id="bce3f-129">在数据绑定中，源对象通常完全独立于侦听器对象，后者是绑定的目标。</span><span class="sxs-lookup"><span data-stu-id="bce3f-129">In data binding, it is common for the source object to be completely independent of the listener object, which is a target of a binding.</span></span> <span data-ttu-id="bce3f-130">数据绑定的许多方面 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 已经在如何实现事件的方式上应用了弱事件模式。</span><span class="sxs-lookup"><span data-stu-id="bce3f-130">Many aspects of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] data binding already have the weak event pattern applied in how the events are implemented.</span></span>  
  
## <a name="how-to-implement-the-weak-event-pattern"></a><span data-ttu-id="bce3f-131">如何实现弱事件模式</span><span class="sxs-lookup"><span data-stu-id="bce3f-131">How to Implement the Weak Event Pattern</span></span>  
 <span data-ttu-id="bce3f-132">有三种方法可以实现弱事件模式。</span><span class="sxs-lookup"><span data-stu-id="bce3f-132">There are three ways to implement weak event pattern.</span></span> <span data-ttu-id="bce3f-133">下表列出了这三种方法，并提供了有关何时使用每种方法的一些指导。</span><span class="sxs-lookup"><span data-stu-id="bce3f-133">The following table lists the three approaches and provides some guidance for when you should use each.</span></span>  
  
|<span data-ttu-id="bce3f-134">方法</span><span class="sxs-lookup"><span data-stu-id="bce3f-134">Approach</span></span>|<span data-ttu-id="bce3f-135">实现时间</span><span class="sxs-lookup"><span data-stu-id="bce3f-135">When to Implement</span></span>|  
|--------------|-----------------------|  
|<span data-ttu-id="bce3f-136">使用现有弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-136">Use an existing weak event manager class</span></span>|<span data-ttu-id="bce3f-137">如果要订阅的事件有相应的 <xref:System.Windows.WeakEventManager> ，请使用现有的弱事件管理器。</span><span class="sxs-lookup"><span data-stu-id="bce3f-137">If the event you want to subscribe to has a corresponding <xref:System.Windows.WeakEventManager>, use the existing weak event manager.</span></span> <span data-ttu-id="bce3f-138">有关 WPF 随附的弱事件管理器的列表，请参阅类中的继承层次结构 <xref:System.Windows.WeakEventManager> 。</span><span class="sxs-lookup"><span data-stu-id="bce3f-138">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span> <span data-ttu-id="bce3f-139">由于包含的弱事件管理器受到限制，因此你可能需要选择其他方法之一。</span><span class="sxs-lookup"><span data-stu-id="bce3f-139">Because the included weak event managers are limited, you will probably need to choose one of the other approaches.</span></span>|  
|<span data-ttu-id="bce3f-140">使用一般弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-140">Use a generic weak event manager class</span></span>|<span data-ttu-id="bce3f-141"><xref:System.Windows.WeakEventManager%602>如果现有不可 <xref:System.Windows.WeakEventManager> 用，则使用泛型，你需要一种简单的方法来实现，而你并不关心效率。</span><span class="sxs-lookup"><span data-stu-id="bce3f-141">Use a generic <xref:System.Windows.WeakEventManager%602> when an existing <xref:System.Windows.WeakEventManager> is not available, you want an easy way to implement, and you are not concerned about efficiency.</span></span> <span data-ttu-id="bce3f-142">泛型 <xref:System.Windows.WeakEventManager%602> 比现有的或自定义的弱事件管理器效率更低。</span><span class="sxs-lookup"><span data-stu-id="bce3f-142">The generic <xref:System.Windows.WeakEventManager%602> is less efficient than an existing or custom weak event manager.</span></span> <span data-ttu-id="bce3f-143">例如，泛型类执行更多反射来发现事件的名称中的事件。</span><span class="sxs-lookup"><span data-stu-id="bce3f-143">For example, the generic class does more reflection to discover the event given the event's name.</span></span> <span data-ttu-id="bce3f-144">此外，使用泛型注册事件的代码 <xref:System.Windows.WeakEventManager%602> 比使用现有的或自定义更详细 <xref:System.Windows.WeakEventManager> 。</span><span class="sxs-lookup"><span data-stu-id="bce3f-144">Also, the code to register the event by using the generic <xref:System.Windows.WeakEventManager%602> is more verbose than using an existing or custom <xref:System.Windows.WeakEventManager>.</span></span>|  
|<span data-ttu-id="bce3f-145">创建自定义弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-145">Create a custom weak event manager class</span></span>|<span data-ttu-id="bce3f-146"><xref:System.Windows.WeakEventManager>当现有不可用时创建自定义 <xref:System.Windows.WeakEventManager> ，并希望获得最佳效率。</span><span class="sxs-lookup"><span data-stu-id="bce3f-146">Create a custom <xref:System.Windows.WeakEventManager> when an existing <xref:System.Windows.WeakEventManager> is not available and you want the best efficiency.</span></span> <span data-ttu-id="bce3f-147">使用自定义 <xref:System.Windows.WeakEventManager> 来订阅事件将更有效，但你会在一开始就开始编写更多的代码。</span><span class="sxs-lookup"><span data-stu-id="bce3f-147">Using a custom <xref:System.Windows.WeakEventManager> to subscribe to an event will be more efficient, but you do incur the cost of writing more code at the beginning.</span></span>|  
|<span data-ttu-id="bce3f-148">使用第三方弱事件管理器</span><span class="sxs-lookup"><span data-stu-id="bce3f-148">Use a third-party weak event manager</span></span>|<span data-ttu-id="bce3f-149">NuGet 具有[几个弱事件管理器](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)，而许多 WPF 框架还支持该模式（例如，请参阅[Prism 的有关松散耦合的事件订阅的文档](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)）。</span><span class="sxs-lookup"><span data-stu-id="bce3f-149">NuGet has [several weak event managers](https://www.nuget.org/packages?q=weak+event+manager&prerel=false) and many WPF frameworks also support the pattern (for instance, see [Prism's documentation on loosely coupled event subscription](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)).</span></span>|

 <span data-ttu-id="bce3f-150">以下各节介绍如何实现弱事件模式。</span><span class="sxs-lookup"><span data-stu-id="bce3f-150">The following sections describe how to implement the weak event pattern.</span></span>  <span data-ttu-id="bce3f-151">出于此讨论的目的，要订阅的事件具有以下特征。</span><span class="sxs-lookup"><span data-stu-id="bce3f-151">For purposes of this discussion, the event to subscribe to has the following characteristics.</span></span>  
  
- <span data-ttu-id="bce3f-152">事件名称为 `SomeEvent` 。</span><span class="sxs-lookup"><span data-stu-id="bce3f-152">The event name is `SomeEvent`.</span></span>  
  
- <span data-ttu-id="bce3f-153">此事件由 `EventSource` 类引发。</span><span class="sxs-lookup"><span data-stu-id="bce3f-153">The event is raised by the `EventSource` class.</span></span>  
  
- <span data-ttu-id="bce3f-154">事件处理程序的类型为： `SomeEventEventHandler` （或 `EventHandler<SomeEventEventArgs>` ）。</span><span class="sxs-lookup"><span data-stu-id="bce3f-154">The event handler has type: `SomeEventEventHandler` (or `EventHandler<SomeEventEventArgs>`).</span></span>  
  
- <span data-ttu-id="bce3f-155">事件将类型的参数传递 `SomeEventEventArgs` 给事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="bce3f-155">The event passes a parameter of type `SomeEventEventArgs` to the event handlers.</span></span>  
  
### <a name="using-an-existing-weak-event-manager-class"></a><span data-ttu-id="bce3f-156">使用现有弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-156">Using an Existing Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="bce3f-157">查找现有的弱事件管理器。</span><span class="sxs-lookup"><span data-stu-id="bce3f-157">Find an existing weak event manager.</span></span>  
  
     <span data-ttu-id="bce3f-158">有关 WPF 随附的弱事件管理器的列表，请参阅类中的继承层次结构 <xref:System.Windows.WeakEventManager> 。</span><span class="sxs-lookup"><span data-stu-id="bce3f-158">For a list of weak event managers that are included with WPF, see the inheritance hierarchy in the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
2. <span data-ttu-id="bce3f-159">使用新的弱事件管理器而不是正常的事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="bce3f-159">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="bce3f-160">例如，如果您的代码使用以下模式来订阅事件：</span><span class="sxs-lookup"><span data-stu-id="bce3f-160">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="bce3f-161">将其更改为以下模式：</span><span class="sxs-lookup"><span data-stu-id="bce3f-161">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="bce3f-162">同样，如果你的代码使用以下模式来取消订阅事件：</span><span class="sxs-lookup"><span data-stu-id="bce3f-162">Similarly, if your code uses the following pattern to unsubscribe from an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="bce3f-163">将其更改为以下模式：</span><span class="sxs-lookup"><span data-stu-id="bce3f-163">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a><span data-ttu-id="bce3f-164">使用一般弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-164">Using the Generic Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="bce3f-165">使用泛型 <xref:System.Windows.WeakEventManager%602> 类而不是正常的事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="bce3f-165">Use the generic <xref:System.Windows.WeakEventManager%602> class instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="bce3f-166">当你使用 <xref:System.Windows.WeakEventManager%602> 注册事件侦听器时，可以将事件源和 <xref:System.EventArgs> 类型作为类型参数提供给类并调用， <xref:System.Windows.WeakEventManager%602.AddHandler%2A> 如下面的代码所示：</span><span class="sxs-lookup"><span data-stu-id="bce3f-166">When you use <xref:System.Windows.WeakEventManager%602> to register event listeners, you supply the event source and <xref:System.EventArgs> type as the type parameters to the class and call <xref:System.Windows.WeakEventManager%602.AddHandler%2A> as shown in the following code:</span></span>  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a><span data-ttu-id="bce3f-167">创建自定义弱事件管理器类</span><span class="sxs-lookup"><span data-stu-id="bce3f-167">Creating a Custom Weak Event Manager Class</span></span>  
  
1. <span data-ttu-id="bce3f-168">将以下类模板复制到您的项目中。</span><span class="sxs-lookup"><span data-stu-id="bce3f-168">Copy the following class template to your project.</span></span>  
  
     <span data-ttu-id="bce3f-169">此类继承自 <xref:System.Windows.WeakEventManager> 类。</span><span class="sxs-lookup"><span data-stu-id="bce3f-169">This class inherits from the <xref:System.Windows.WeakEventManager> class.</span></span>  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. <span data-ttu-id="bce3f-170">将 `SomeEventWeakEventManager` 名称替换为自己的名称。</span><span class="sxs-lookup"><span data-stu-id="bce3f-170">Replace the `SomeEventWeakEventManager` name with your own name.</span></span>  
  
3. <span data-ttu-id="bce3f-171">将前面所述的三个名称替换为事件的相应名称。</span><span class="sxs-lookup"><span data-stu-id="bce3f-171">Replace the three names described previously with the corresponding names for your event.</span></span> <span data-ttu-id="bce3f-172">（ `SomeEvent` 、 `EventSource` 和 `SomeEventEventArgs` ）</span><span class="sxs-lookup"><span data-stu-id="bce3f-172">(`SomeEvent`, `EventSource`, and `SomeEventEventArgs`)</span></span>  
  
4. <span data-ttu-id="bce3f-173">将弱事件管理器类的可见性（公共/内部/私有）设置为与其管理的事件相同的可见性。</span><span class="sxs-lookup"><span data-stu-id="bce3f-173">Set the visibility (public / internal / private) of the weak event manager class to the same visibility as event it manages.</span></span>  
  
5. <span data-ttu-id="bce3f-174">使用新的弱事件管理器而不是正常的事件挂钩。</span><span class="sxs-lookup"><span data-stu-id="bce3f-174">Use the new weak event manager instead of the normal event hookup.</span></span>  
  
     <span data-ttu-id="bce3f-175">例如，如果您的代码使用以下模式来订阅事件：</span><span class="sxs-lookup"><span data-stu-id="bce3f-175">For example, if your code uses the following pattern to subscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     <span data-ttu-id="bce3f-176">将其更改为以下模式：</span><span class="sxs-lookup"><span data-stu-id="bce3f-176">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     <span data-ttu-id="bce3f-177">同样，如果代码使用以下模式取消订阅事件：</span><span class="sxs-lookup"><span data-stu-id="bce3f-177">Similarly, if your code uses the following pattern to unsubscribe to an event:</span></span>  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     <span data-ttu-id="bce3f-178">将其更改为以下模式：</span><span class="sxs-lookup"><span data-stu-id="bce3f-178">Change it to the following pattern:</span></span>  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bce3f-179">请参阅</span><span class="sxs-lookup"><span data-stu-id="bce3f-179">See also</span></span>

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [<span data-ttu-id="bce3f-180">路由事件概述</span><span class="sxs-lookup"><span data-stu-id="bce3f-180">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="bce3f-181">数据绑定概述</span><span class="sxs-lookup"><span data-stu-id="bce3f-181">Data Binding Overview</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
