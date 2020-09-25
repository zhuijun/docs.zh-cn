---
title: 事件 - C# 编程指南
description: 了解事件。 类或对象可以通过事件向其他类或对象通知发生的相关事情。
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 14c18006e393dece5d32d30c2a727d797515c779
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167452"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="e2d92-104">事件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="e2d92-104">Events (C# Programming Guide)</span></span>

<span data-ttu-id="e2d92-105">[类](../../language-reference/keywords/class.md) 或对象可以通过事件向其他类或对象通知发生的相关事情。</span><span class="sxs-lookup"><span data-stu-id="e2d92-105">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="e2d92-106">发送（或引发）事件的类称为“发布者”，接收（或处理）事件的类称为“订阅者”。</span><span class="sxs-lookup"><span data-stu-id="e2d92-106">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="e2d92-107">在典型的 C# Windows 窗体或 Web 应用程序中，可订阅由按钮和列表框等控件引发的事件。</span><span class="sxs-lookup"><span data-stu-id="e2d92-107">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="e2d92-108">可以使用 Visual C# 集成开发环境 (IDE) 来浏览控件发布的事件，并选择想要处理的事件。</span><span class="sxs-lookup"><span data-stu-id="e2d92-108">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="e2d92-109">借助 IDE，可轻松自动添加空白事件处理程序方法以及要订阅该事件的代码。</span><span class="sxs-lookup"><span data-stu-id="e2d92-109">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="e2d92-110">有关详细信息，请参阅[如何订阅和取消订阅事件](./how-to-subscribe-to-and-unsubscribe-from-events.md)。</span><span class="sxs-lookup"><span data-stu-id="e2d92-110">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="e2d92-111">事件概述</span><span class="sxs-lookup"><span data-stu-id="e2d92-111">Events Overview</span></span>  

 <span data-ttu-id="e2d92-112">事件具有以下属性：</span><span class="sxs-lookup"><span data-stu-id="e2d92-112">Events have the following properties:</span></span>  
  
- <span data-ttu-id="e2d92-113">发行者确定何时引发事件；订户确定对事件作出何种响应。</span><span class="sxs-lookup"><span data-stu-id="e2d92-113">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="e2d92-114">一个事件可以有多个订户。</span><span class="sxs-lookup"><span data-stu-id="e2d92-114">An event can have multiple subscribers.</span></span> <span data-ttu-id="e2d92-115">订户可以处理来自多个发行者的多个事件。</span><span class="sxs-lookup"><span data-stu-id="e2d92-115">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="e2d92-116">没有订户的事件永远也不会引发。</span><span class="sxs-lookup"><span data-stu-id="e2d92-116">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="e2d92-117">事件通常用于表示用户操作，例如单击按钮或图形用户界面中的菜单选项。</span><span class="sxs-lookup"><span data-stu-id="e2d92-117">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="e2d92-118">当事件具有多个订户时，引发该事件时会同步调用事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="e2d92-118">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="e2d92-119">若要异步调用事件，请参阅 “[使用异步方式调用同步方法](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)”。</span><span class="sxs-lookup"><span data-stu-id="e2d92-119">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="e2d92-120">在 .NET 类库中，事件基于 <xref:System.EventHandler> 委托和 <xref:System.EventArgs> 基类。</span><span class="sxs-lookup"><span data-stu-id="e2d92-120">In the .NET class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2d92-121">相关章节</span><span class="sxs-lookup"><span data-stu-id="e2d92-121">Related Sections</span></span>  

 <span data-ttu-id="e2d92-122">有关详细信息，请参见:</span><span class="sxs-lookup"><span data-stu-id="e2d92-122">For more information, see:</span></span>  
  
- [<span data-ttu-id="e2d92-123">如何订阅和取消订阅事件</span><span class="sxs-lookup"><span data-stu-id="e2d92-123">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="e2d92-124">如何发布符合 .NET 准则的事件</span><span class="sxs-lookup"><span data-stu-id="e2d92-124">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="e2d92-125">如何在派生类中引发基类事件</span><span class="sxs-lookup"><span data-stu-id="e2d92-125">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="e2d92-126">如何实现接口事件</span><span class="sxs-lookup"><span data-stu-id="e2d92-126">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="e2d92-127">如何实现自定义事件访问器</span><span class="sxs-lookup"><span data-stu-id="e2d92-127">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="e2d92-128">C# 语言规范</span><span class="sxs-lookup"><span data-stu-id="e2d92-128">C# Language Specification</span></span>  

<span data-ttu-id="e2d92-129">有关详细信息，请参阅 [C# 语言规范](/dotnet/csharp/language-reference/language-specification/introduction)中的[事件](~/_csharplang/spec/classes.md#events)。</span><span class="sxs-lookup"><span data-stu-id="e2d92-129">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="e2d92-130">该语言规范是 C# 语法和用法的权威资料。</span><span class="sxs-lookup"><span data-stu-id="e2d92-130">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="e2d92-131">重要章节</span><span class="sxs-lookup"><span data-stu-id="e2d92-131">Featured Book Chapters</span></span>  

 <span data-ttu-id="e2d92-132">[C# 3.0 手册（第三版）：面向 C# 3.0 程序员的超过 250 个解决方案](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))中的[委托、事件和 Lambda 表达式](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="e2d92-132">[Delegates, Events, and Lambda Expressions](/previous-versions/visualstudio/visual-studio-2008/ff518994(v=orm.10)) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](/previous-versions/visualstudio/visual-studio-2008/ff518995(v=orm.10))</span></span>  
  
 <span data-ttu-id="e2d92-133">[学习 C# 3.0：掌握 C# 3.0 基础知识](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))中的[委托和事件](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10))</span><span class="sxs-lookup"><span data-stu-id="e2d92-133">[Delegates and Events](/previous-versions/visualstudio/visual-studio-2008/ff652490(v=orm.10)) in [Learning C# 3.0: Master the fundamentals of C# 3.0](/previous-versions/visualstudio/visual-studio-2008/ff652493(v=orm.10))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d92-134">请参阅</span><span class="sxs-lookup"><span data-stu-id="e2d92-134">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="e2d92-135">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="e2d92-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e2d92-136">委托</span><span class="sxs-lookup"><span data-stu-id="e2d92-136">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="e2d92-137">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="e2d92-137">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)
