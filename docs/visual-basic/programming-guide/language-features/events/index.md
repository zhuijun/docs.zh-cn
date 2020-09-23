---
title: 事件
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 15ab02c20c1baf0fbc9087bfe2e75ec97acd0734
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057931"
---
# <a name="events-visual-basic"></a><span data-ttu-id="f261b-102">事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f261b-102">Events (Visual Basic)</span></span>

<span data-ttu-id="f261b-103">虽然你可以将 Visual Studio 项目可视化为一系列按顺序执行的过程，但实际上，大多数程序都是事件驱动型的，这意味着执行流是由称为 *事件*的外部事件确定的。</span><span class="sxs-lookup"><span data-stu-id="f261b-103">While you might visualize a Visual Studio project as a series of procedures that execute in a sequence, in reality, most programs are event driven—meaning the flow of execution is determined by external occurrences called *events*.</span></span>  
  
 <span data-ttu-id="f261b-104">事件是一种信号，可指示应用程序某重要事件已发生。</span><span class="sxs-lookup"><span data-stu-id="f261b-104">An event is a signal that informs an application that something important has occurred.</span></span> <span data-ttu-id="f261b-105">例如，当用户单击窗体控件时，窗体会引发 `Click` 事件，并调用可处理此事件的过程。</span><span class="sxs-lookup"><span data-stu-id="f261b-105">For example, when a user clicks a control on a form, the form can raise a `Click` event and call a procedure that handles the event.</span></span> <span data-ttu-id="f261b-106">借助事件，各个不同的任务还可以相互通信。</span><span class="sxs-lookup"><span data-stu-id="f261b-106">Events also allow separate tasks to communicate.</span></span> <span data-ttu-id="f261b-107">例如，应用程序执行的排序任务与主应用程序是分开的。</span><span class="sxs-lookup"><span data-stu-id="f261b-107">Say, for example, that your application performs a sort task separately from the main application.</span></span> <span data-ttu-id="f261b-108">如果用户取消排序，应用程序便会发送 cancel 事件，指示停止排序过程。</span><span class="sxs-lookup"><span data-stu-id="f261b-108">If a user cancels the sort, your application can send a cancel event instructing the sort process to stop.</span></span>  
  
## <a name="event-terms-and-concepts"></a><span data-ttu-id="f261b-109">事件术语和概念</span><span class="sxs-lookup"><span data-stu-id="f261b-109">Event Terms and Concepts</span></span>  

 <span data-ttu-id="f261b-110">本部分介绍与 Visual Basic 中的事件一起使用的术语和概念。</span><span class="sxs-lookup"><span data-stu-id="f261b-110">This section describes the terms and concepts used with events in Visual Basic.</span></span>  
  
### <a name="declaring-events"></a><span data-ttu-id="f261b-111">声明事件</span><span class="sxs-lookup"><span data-stu-id="f261b-111">Declaring Events</span></span>  

 <span data-ttu-id="f261b-112">可以使用 `Event` 关键字在类、结构、模块和接口中声明事件，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="f261b-112">You declare events within classes, structures, modules, and interfaces using the `Event` keyword, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a><span data-ttu-id="f261b-113">引发事件</span><span class="sxs-lookup"><span data-stu-id="f261b-113">Raising Events</span></span>  

 <span data-ttu-id="f261b-114">事件类似于消息，指示某重要事件已发生。</span><span class="sxs-lookup"><span data-stu-id="f261b-114">An event is like a message announcing that something important has occurred.</span></span> <span data-ttu-id="f261b-115">广播消息的行为称为*引发*事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-115">The act of broadcasting the message is called *raising* the event.</span></span> <span data-ttu-id="f261b-116">在 Visual Basic 中，将引发包含语句的事件 `RaiseEvent` ，如以下示例中所示：</span><span class="sxs-lookup"><span data-stu-id="f261b-116">In Visual Basic, you raise events with the `RaiseEvent` statement, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 <span data-ttu-id="f261b-117">必须在声明事件的类、模块或结构范围内引发事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-117">Events must be raised within the scope of the class, module, or structure where they are declared.</span></span> <span data-ttu-id="f261b-118">例如，派生类不能引发继承自基类的事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-118">For example, a derived class cannot raise events inherited from a base class.</span></span>  
  
### <a name="event-senders"></a><span data-ttu-id="f261b-119">事件发送方</span><span class="sxs-lookup"><span data-stu-id="f261b-119">Event Senders</span></span>  

 <span data-ttu-id="f261b-120">所有能够引发事件的对象都是*事件发送方*，亦称为“*事件源*”。</span><span class="sxs-lookup"><span data-stu-id="f261b-120">Any object capable of raising an event is an *event sender*, also known as an *event source*.</span></span> <span data-ttu-id="f261b-121">例如，窗体、控件和用户定义对象都是事件发送方。</span><span class="sxs-lookup"><span data-stu-id="f261b-121">Forms, controls, and user-defined objects are examples of event senders.</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="f261b-122">事件处理程序</span><span class="sxs-lookup"><span data-stu-id="f261b-122">Event Handlers</span></span>  

 <span data-ttu-id="f261b-123">*事件处理程序*是在相应事件发生时调用的过程。</span><span class="sxs-lookup"><span data-stu-id="f261b-123">*Event handlers* are procedures that are called when a corresponding event occurs.</span></span> <span data-ttu-id="f261b-124">可以将签名一致的任意有效子例程用作事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-124">You can use any valid subroutine with a matching signature as an event handler.</span></span> <span data-ttu-id="f261b-125">不过，不能将函数用作事件处理程序，因为它不能向事件源返回值。</span><span class="sxs-lookup"><span data-stu-id="f261b-125">You cannot use a function as an event handler, however, because it cannot return a value to the event source.</span></span>  
  
 <span data-ttu-id="f261b-126">Visual Basic 对事件处理程序使用标准命名约定，这些事件处理程序将事件发送方的名称、下划线和事件的名称组合在一起。</span><span class="sxs-lookup"><span data-stu-id="f261b-126">Visual Basic uses a standard naming convention for event handlers that combines the name of the event sender, an underscore, and the name of the event.</span></span> <span data-ttu-id="f261b-127">例如，`button1` 按钮的 `Click` 事件将命名为 `Sub button1_Click`。</span><span class="sxs-lookup"><span data-stu-id="f261b-127">For example, the `Click` event of a button named `button1` would be named `Sub button1_Click`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f261b-128">我们建议在为你自己的事件定义事件处理程序时采用此命名约定，但这不是一项强制性要求；可以命名任意有效的子例程名称。</span><span class="sxs-lookup"><span data-stu-id="f261b-128">We recommend that you use this naming convention when defining event handlers for your own events, but it is not required; you can use any valid subroutine name.</span></span>  
  
## <a name="associating-events-with-event-handlers"></a><span data-ttu-id="f261b-129">关联事件与事件处理程序</span><span class="sxs-lookup"><span data-stu-id="f261b-129">Associating Events with Event Handlers</span></span>  

 <span data-ttu-id="f261b-130">必须先使用 `Handles` 或 `AddHandler` 语句关联事件处理程序与事件，然后才能使用事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-130">Before an event handler becomes usable, you must first associate it with an event by using either the `Handles` or `AddHandler` statement.</span></span>  
  
### <a name="withevents-and-the-handles-clause"></a><span data-ttu-id="f261b-131">WithEvents 和 Handles 子句</span><span class="sxs-lookup"><span data-stu-id="f261b-131">WithEvents and the Handles Clause</span></span>  

 <span data-ttu-id="f261b-132">使用 `WithEvents` 语句和 `Handles` 子句，可以声明性的方式指定事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-132">The `WithEvents` statement and `Handles` clause provide a declarative way of specifying event handlers.</span></span> <span data-ttu-id="f261b-133">使用 `WithEvents` 关键字声明的对象引发的事件可以由使用 `Handles` 语句针对相应事件指定的任意过程进行处理，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="f261b-133">An event raised by an object declared with the `WithEvents` keyword can be handled by any procedure with a `Handles` statement for that event, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 <span data-ttu-id="f261b-134">`WithEvents` 语句和 `Handles` 子句通常是事件处理程序的最佳选择，因为它们使用的声明性语法简化了事件处理程序的编码、读取和调试。</span><span class="sxs-lookup"><span data-stu-id="f261b-134">The `WithEvents` statement and the `Handles` clause are often the best choice for event handlers because the declarative syntax they use makes event handling easier to code, read and debug.</span></span> <span data-ttu-id="f261b-135">不过，请注意，使用 `WithEvents` 变量还要遵循以下限制：</span><span class="sxs-lookup"><span data-stu-id="f261b-135">However, be aware of the following limitations on the use of `WithEvents` variables:</span></span>  
  
- <span data-ttu-id="f261b-136">不能将 `WithEvents` 变量用作对象变量。</span><span class="sxs-lookup"><span data-stu-id="f261b-136">You cannot use a `WithEvents` variable as an object variable.</span></span> <span data-ttu-id="f261b-137">也就是说，不能将其声明为 `Object`，必须在声明变量时指定类名。</span><span class="sxs-lookup"><span data-stu-id="f261b-137">That is, you cannot declare it as `Object`—you must specify the class name when you declare the variable.</span></span>  
  
- <span data-ttu-id="f261b-138">由于共享事件不与类实例相关联，因此不能使用 `WithEvents` 以声明方式处理共享事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-138">Because shared events are not tied to class instances, you cannot use `WithEvents` to declaratively handle shared events.</span></span> <span data-ttu-id="f261b-139">同样，不能使用 `WithEvents` 或 `Handles` 处理 `Structure` 中的事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-139">Similarly, you cannot use `WithEvents` or `Handles` to handle events from a `Structure`.</span></span> <span data-ttu-id="f261b-140">在这两种情况下，均可使用 `AddHandler` 语句处理这些事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-140">In both cases, you can use the `AddHandler` statement to handle those events.</span></span>  
  
- <span data-ttu-id="f261b-141">无法创建 `WithEvents` 变量的数组。</span><span class="sxs-lookup"><span data-stu-id="f261b-141">You cannot create arrays of `WithEvents` variables.</span></span>  
  
 <span data-ttu-id="f261b-142">`WithEvents` 变量允许一个事件处理程序处理一种或多种事件，也允许一个或多个事件处理程序处理同一种事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-142">`WithEvents` variables allow a single event handler to handle one or more kind of event, or one or more event handlers to handle the same kind of event.</span></span>  
  
 <span data-ttu-id="f261b-143">虽然 `Handles` 子句是关联事件与事件处理程序的标准方法，但只能在编译时关联事件与事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-143">Although the `Handles` clause is the standard way of associating an event with an event handler, it is limited to associating events with event handlers at compile time.</span></span>  
  
 <span data-ttu-id="f261b-144">在某些情况下，例如，对于与窗体或控件关联的事件，Visual Basic 会自动将空事件处理程序置入，并将其与事件相关联。</span><span class="sxs-lookup"><span data-stu-id="f261b-144">In some cases, such as with events associated with forms or controls, Visual Basic automatically stubs out an empty event handler and associates it with an event.</span></span> <span data-ttu-id="f261b-145">例如，当你在设计模式下双击窗体上的命令按钮时，Visual Basic 将为命令按钮创建一个空的事件处理程序和一个 `WithEvents` 变量，如以下代码所示：</span><span class="sxs-lookup"><span data-stu-id="f261b-145">For example, when you double-click a command button on a form in design mode, Visual Basic creates an empty event handler and a `WithEvents` variable for the command button, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a><span data-ttu-id="f261b-146">AddHandler 和 RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="f261b-146">AddHandler and RemoveHandler</span></span>  

 <span data-ttu-id="f261b-147">`AddHandler` 语句与 `Handles` 子句类似，两者都允许指定事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-147">The `AddHandler` statement is similar to the `Handles` clause in that both allow you to specify an event handler.</span></span> <span data-ttu-id="f261b-148">不同之处在于，`AddHandler` 与 `RemoveHandler` 结合使用比 `Handles` 子句更具灵活性，你可以动态添加、删除和更改与事件关联的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="f261b-148">However, `AddHandler`, used with `RemoveHandler`, provides greater flexibility than the `Handles` clause, allowing you to dynamically add, remove, and change the event handler associated with an event.</span></span> <span data-ttu-id="f261b-149">若要处理共享事件或结构中的事件，必须使用 `AddHandler`。</span><span class="sxs-lookup"><span data-stu-id="f261b-149">If you want to handle shared events or events from a structure, you must use `AddHandler`.</span></span>  
  
 <span data-ttu-id="f261b-150">`AddHandler` 需要使用两个自变量：事件发送方（如控件）引发的事件的名称和计算结果为委托的表达式。</span><span class="sxs-lookup"><span data-stu-id="f261b-150">`AddHandler` takes two arguments: the name of an event from an event sender such as a control, and an expression that evaluates to a delegate.</span></span> <span data-ttu-id="f261b-151">使用 `AddHandler` 时，无需显式指定委托类，因为 `AddressOf` 语句始终返回对委托的引用。</span><span class="sxs-lookup"><span data-stu-id="f261b-151">You do not need to explicitly specify the delegate class when using `AddHandler`, since the `AddressOf` statement always returns a reference to the delegate.</span></span> <span data-ttu-id="f261b-152">下面的示例将事件处理程序与对象引发的事件相关联：</span><span class="sxs-lookup"><span data-stu-id="f261b-152">The following example associates an event handler with an event raised by an object:</span></span>  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 <span data-ttu-id="f261b-153">`RemoveHandler` 用于解除事件与事件处理程序的关联，所用语法与 `AddHandler` 一样。</span><span class="sxs-lookup"><span data-stu-id="f261b-153">`RemoveHandler`, which disconnects an event from an event handler, uses the same syntax as `AddHandler`.</span></span> <span data-ttu-id="f261b-154">例如：</span><span class="sxs-lookup"><span data-stu-id="f261b-154">For example:</span></span>  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 <span data-ttu-id="f261b-155">在以下示例中，事件处理程序与事件相关联，且此事件已引发。</span><span class="sxs-lookup"><span data-stu-id="f261b-155">In the following example, an event handler is associated with an event, and the event is raised.</span></span> <span data-ttu-id="f261b-156">事件处理程序捕获此事件并显示消息。</span><span class="sxs-lookup"><span data-stu-id="f261b-156">The event handler catches the event and displays a message.</span></span>  
  
 <span data-ttu-id="f261b-157">然后删除第一个事件处理程序，并将另一个事件处理程序与此事件相关联。</span><span class="sxs-lookup"><span data-stu-id="f261b-157">Then the first event handler is removed and a different event handler is associated with the event.</span></span> <span data-ttu-id="f261b-158">当此事件再次引发时，显示不同的消息。</span><span class="sxs-lookup"><span data-stu-id="f261b-158">When the event is raised again, a different message is displayed.</span></span>  
  
 <span data-ttu-id="f261b-159">最后删除第二个事件处理程序，然后第三次引发此事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-159">Finally, the second event handler is removed and the event is raised for a third time.</span></span> <span data-ttu-id="f261b-160">因为不再有事件处理程序与此事件相关联，所以不会执行任何操作。</span><span class="sxs-lookup"><span data-stu-id="f261b-160">Because there is no longer an event handler associated with the event, no action is taken.</span></span>  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a><span data-ttu-id="f261b-161">处理继承自基类的事件</span><span class="sxs-lookup"><span data-stu-id="f261b-161">Handling Events Inherited from a Base Class</span></span>  

 <span data-ttu-id="f261b-162">*派生类*继承了基类特征的类，可以使用 `Handles MyBase` 语句处理基类引发的事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-162">*Derived classes*—classes that inherit characteristics from a base class—can handle events raised by their base class using the `Handles MyBase` statement.</span></span>  
  
### <a name="to-handle-events-from-a-base-class"></a><span data-ttu-id="f261b-163">处理继承自基类的事件的具体操作</span><span class="sxs-lookup"><span data-stu-id="f261b-163">To handle events from a base class</span></span>  
  
- <span data-ttu-id="f261b-164">向事件处理程序过程的声明行添加 `Handles MyBase.`*eventname* 语句，在派生类中声明事件处理程序，其中 *eventname* 是要处理的继承自基类的事件名称。</span><span class="sxs-lookup"><span data-stu-id="f261b-164">Declare an event handler in the derived class by adding a `Handles MyBase.`*eventname* statement to the declaration line of your event-handler procedure, where *eventname* is the name of the event in the base class you are handling.</span></span> <span data-ttu-id="f261b-165">例如：</span><span class="sxs-lookup"><span data-stu-id="f261b-165">For example:</span></span>  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a><span data-ttu-id="f261b-166">相关章节</span><span class="sxs-lookup"><span data-stu-id="f261b-166">Related Sections</span></span>  
  
|<span data-ttu-id="f261b-167">Title</span><span class="sxs-lookup"><span data-stu-id="f261b-167">Title</span></span>|<span data-ttu-id="f261b-168">描述</span><span class="sxs-lookup"><span data-stu-id="f261b-168">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f261b-169">演练：声明和引发事件</span><span class="sxs-lookup"><span data-stu-id="f261b-169">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)|<span data-ttu-id="f261b-170">分步展示了如何声明和引发类事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-170">Provides a step-by-step description of how to declare and raise events for a class.</span></span>|  
|[<span data-ttu-id="f261b-171">演练：处理事件</span><span class="sxs-lookup"><span data-stu-id="f261b-171">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)|<span data-ttu-id="f261b-172">展示了如何编写事件处理程序过程。</span><span class="sxs-lookup"><span data-stu-id="f261b-172">Demonstrates how to write an event-handler procedure.</span></span>|  
|[<span data-ttu-id="f261b-173">如何：声明自定义事件以避免阻止</span><span class="sxs-lookup"><span data-stu-id="f261b-173">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)|<span data-ttu-id="f261b-174">介绍了如何定义允许异步调用事件处理程序的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-174">Demonstrates how to define a custom event that allows its event handlers to be called asynchronously.</span></span>|  
|[<span data-ttu-id="f261b-175">如何：声明自定义事件以节省内存</span><span class="sxs-lookup"><span data-stu-id="f261b-175">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)|<span data-ttu-id="f261b-176">介绍了如何定义仅在事件处理时占用内存的自定义事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-176">Demonstrates how to define a custom event that uses memory only when the event is handled.</span></span>|  
|[<span data-ttu-id="f261b-177">Visual Basic 中继承的事件处理程序疑难解答</span><span class="sxs-lookup"><span data-stu-id="f261b-177">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](troubleshooting-inherited-event-handlers.md)|<span data-ttu-id="f261b-178">列出了在继承的组件中使用事件处理程序时遇到的常见问题。</span><span class="sxs-lookup"><span data-stu-id="f261b-178">Lists common issues that arise with event handlers in inherited components.</span></span>|  
|[<span data-ttu-id="f261b-179">事件</span><span class="sxs-lookup"><span data-stu-id="f261b-179">Events</span></span>](../../../../standard/events/index.md)|<span data-ttu-id="f261b-180">提供 .NET Framework 中事件模型的概述。</span><span class="sxs-lookup"><span data-stu-id="f261b-180">Provides an overview of the event model in the .NET Framework.</span></span>|  
|[<span data-ttu-id="f261b-181">在 Windows 窗体中创建事件处理程序</span><span class="sxs-lookup"><span data-stu-id="f261b-181">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)|<span data-ttu-id="f261b-182">介绍了如何处理与 Windows 窗体对象关联的事件。</span><span class="sxs-lookup"><span data-stu-id="f261b-182">Describes how to work with events associated with Windows Forms objects.</span></span>|  
|[<span data-ttu-id="f261b-183">委托</span><span class="sxs-lookup"><span data-stu-id="f261b-183">Delegates</span></span>](../delegates/index.md)|<span data-ttu-id="f261b-184">概述了 Visual Basic 中的委托。</span><span class="sxs-lookup"><span data-stu-id="f261b-184">Provides an overview of delegates in Visual Basic.</span></span>|
