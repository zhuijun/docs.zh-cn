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
# <a name="weak-event-patterns"></a>弱事件模式
在应用程序中，附加到事件源的处理程序可能不会与附加了该处理程序的侦听器对象一起销毁。 这种情况可能会导致内存泄漏。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]引入了一种可用于解决此问题的设计模式，方法是为特定事件提供一个专用的管理器类，并在该事件的侦听器上实现一个接口。 此设计模式称为*弱事件模式*。  
  
## <a name="why-implement-the-weak-event-pattern"></a>为什么要实现弱事件模式？  
 侦听事件可能会导致内存泄漏。 侦听事件的典型方法是使用特定于语言的语法，将处理程序附加到源上的事件。 例如，在 c # 中，该语法为： `source.SomeEvent += new SomeEventHandler(MyEventHandler)` 。  
  
 此方法可创建从事件源到事件侦听器的强引用。 通常情况下，附加侦听器的事件处理程序会导致侦听器具有对象生存期，该生存期受源的对象生存期影响（除非显式移除事件处理程序）。 但在某些情况下，您可能希望侦听器的对象生存期由其他因素控制，如当前是否属于应用程序的可视化树，而不是源的生存期。 只要源对象生存期超出侦听器的对象生存期，一般事件模式会导致内存泄漏：侦听器的活动时间比预期时间长。  
  
 弱事件模式旨在解决此内存泄漏问题。 当侦听器需要注册事件时，可以使用弱事件模式，但侦听器不会明确知道何时取消注册。 如果源的对象生存期超出侦听器的有用对象生存期，还可以使用弱事件模式。 （在这种情况下，*很有用*由您决定。）弱事件模式允许侦听器注册并接收事件，而不会以任何方式影响侦听器的对象生存期特性。 实际上，来自源的隐含引用不确定侦听器是否符合垃圾回收的条件。 引用是弱引用，因此是弱事件模式和相关 Api 的命名。 侦听器可以进行垃圾回收或销毁，并且源可以继续，而不会将构成处理程序引用保留给现在已销毁的对象。  
  
## <a name="who-should-implement-the-weak-event-pattern"></a>谁应该实现弱事件模式？  
 实现弱事件模式主要是为了使控件作者感兴趣。 作为控件作者，您主要负责控制您的控件的行为和包含以及它对插入它的应用程序的影响。 这包括控件对象生存期行为，尤其是处理所述的内存泄漏问题。  
  
 某些方案本身就是应用弱事件模式。 这种情况是数据绑定。 在数据绑定中，源对象通常完全独立于侦听器对象，后者是绑定的目标。 数据绑定的许多方面 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 已经在如何实现事件的方式上应用了弱事件模式。  
  
## <a name="how-to-implement-the-weak-event-pattern"></a>如何实现弱事件模式  
 有三种方法可以实现弱事件模式。 下表列出了这三种方法，并提供了有关何时使用每种方法的一些指导。  
  
|方法|实现时间|  
|--------------|-----------------------|  
|使用现有弱事件管理器类|如果要订阅的事件有相应的 <xref:System.Windows.WeakEventManager> ，请使用现有的弱事件管理器。 有关 WPF 随附的弱事件管理器的列表，请参阅类中的继承层次结构 <xref:System.Windows.WeakEventManager> 。 由于包含的弱事件管理器受到限制，因此你可能需要选择其他方法之一。|  
|使用一般弱事件管理器类|<xref:System.Windows.WeakEventManager%602>如果现有不可 <xref:System.Windows.WeakEventManager> 用，则使用泛型，你需要一种简单的方法来实现，而你并不关心效率。 泛型 <xref:System.Windows.WeakEventManager%602> 比现有的或自定义的弱事件管理器效率更低。 例如，泛型类执行更多反射来发现事件的名称中的事件。 此外，使用泛型注册事件的代码 <xref:System.Windows.WeakEventManager%602> 比使用现有的或自定义更详细 <xref:System.Windows.WeakEventManager> 。|  
|创建自定义弱事件管理器类|<xref:System.Windows.WeakEventManager>当现有不可用时创建自定义 <xref:System.Windows.WeakEventManager> ，并希望获得最佳效率。 使用自定义 <xref:System.Windows.WeakEventManager> 来订阅事件将更有效，但你会在一开始就开始编写更多的代码。|  
|使用第三方弱事件管理器|NuGet 具有[几个弱事件管理器](https://www.nuget.org/packages?q=weak+event+manager&prerel=false)，而许多 WPF 框架还支持该模式（例如，请参阅[Prism 的有关松散耦合的事件订阅的文档](https://github.com/PrismLibrary/Prism-Documentation/blob/master/docs/wpf/legacy/Communication.md#subscribing-to-events)）。|

 以下各节介绍如何实现弱事件模式。  出于此讨论的目的，要订阅的事件具有以下特征。  
  
- 事件名称为 `SomeEvent` 。  
  
- 此事件由 `EventSource` 类引发。  
  
- 事件处理程序的类型为： `SomeEventEventHandler` （或 `EventHandler<SomeEventEventArgs>` ）。  
  
- 事件将类型的参数传递 `SomeEventEventArgs` 给事件处理程序。  
  
### <a name="using-an-existing-weak-event-manager-class"></a>使用现有弱事件管理器类  
  
1. 查找现有的弱事件管理器。  
  
     有关 WPF 随附的弱事件管理器的列表，请参阅类中的继承层次结构 <xref:System.Windows.WeakEventManager> 。  
  
2. 使用新的弱事件管理器而不是正常的事件挂钩。  
  
     例如，如果您的代码使用以下模式来订阅事件：  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     将其更改为以下模式：  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同样，如果你的代码使用以下模式来取消订阅事件：  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     将其更改为以下模式：  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
### <a name="using-the-generic-weak-event-manager-class"></a>使用一般弱事件管理器类  
  
1. 使用泛型 <xref:System.Windows.WeakEventManager%602> 类而不是正常的事件挂钩。  
  
     当你使用 <xref:System.Windows.WeakEventManager%602> 注册事件侦听器时，可以将事件源和 <xref:System.EventArgs> 类型作为类型参数提供给类并调用， <xref:System.Windows.WeakEventManager%602.AddHandler%2A> 如下面的代码所示：  
  
    ```csharp  
    WeakEventManager<EventSource, SomeEventEventArgs>.AddHandler(source, "SomeEvent", source_SomeEvent);  
    ```  
  
### <a name="creating-a-custom-weak-event-manager-class"></a>创建自定义弱事件管理器类  
  
1. 将以下类模板复制到您的项目中。  
  
     此类继承自 <xref:System.Windows.WeakEventManager> 类。  
  
     [!code-csharp[WeakEvents#WeakEventManagerTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/WeakEvents/CSharp/WeakEventManagerTemplate.cs#weakeventmanagertemplate)]  
  
2. 将 `SomeEventWeakEventManager` 名称替换为自己的名称。  
  
3. 将前面所述的三个名称替换为事件的相应名称。 （ `SomeEvent` 、 `EventSource` 和 `SomeEventEventArgs` ）  
  
4. 将弱事件管理器类的可见性（公共/内部/私有）设置为与其管理的事件相同的可见性。  
  
5. 使用新的弱事件管理器而不是正常的事件挂钩。  
  
     例如，如果您的代码使用以下模式来订阅事件：  
  
    ```csharp  
    source.SomeEvent += new SomeEventEventHandler(OnSomeEvent);  
    ```  
  
     将其更改为以下模式：  
  
    ```csharp  
    SomeEventWeakEventManager.AddHandler(source, OnSomeEvent);  
    ```  
  
     同样，如果代码使用以下模式取消订阅事件：  
  
    ```csharp  
    source.SomeEvent -= new SomeEventEventHandler(OnSome);  
    ```  
  
     将其更改为以下模式：  
  
    ```csharp  
    SomeEventWeakEventManager.RemoveHandler(source, OnSomeEvent);  
    ```  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.WeakEventManager>
- <xref:System.Windows.IWeakEventListener>
- [路由事件概述](routed-events-overview.md)
- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
