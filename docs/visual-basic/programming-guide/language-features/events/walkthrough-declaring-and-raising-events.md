---
title: 声明和引发事件
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 3da60014d7ac95189c5d56c3e339ff1b054a40dc
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405088"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="aebff-102">演练：声明和引发事件 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aebff-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="aebff-103">本演练演示如何声明和引发名为的类的事件 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="aebff-104">完成这些步骤后，你可能需要阅读相关主题[演练：处理事件](walkthrough-handling-events.md)，其中演示了如何使用对象中的事件 `Widget` 在应用程序中提供状态信息。</span><span class="sxs-lookup"><span data-stu-id="aebff-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="aebff-105">小组件类</span><span class="sxs-lookup"><span data-stu-id="aebff-105">The Widget Class</span></span>  
 <span data-ttu-id="aebff-106">假设你有一个 `Widget` 类。</span><span class="sxs-lookup"><span data-stu-id="aebff-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="aebff-107">你的 `Widget` 类有一个可能需要很长时间才能执行的方法，并且你希望你的应用程序能够提供某种类型的完成指示器。</span><span class="sxs-lookup"><span data-stu-id="aebff-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="aebff-108">当然，您可以使 `Widget` 对象显示一个完成百分比对话框，但随后在您使用该类的每个项目中都将出现该对话框 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="aebff-109">对象设计的一个很好的原则是让使用对象的应用程序处理用户界面，除非对象的全部用途是管理窗体或对话框。</span><span class="sxs-lookup"><span data-stu-id="aebff-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="aebff-110">的用途 `Widget` 是执行其他任务，因此最好添加一个 `PercentDone` 事件并让调用 `Widget` 的方法的过程处理该事件并显示状态更新。</span><span class="sxs-lookup"><span data-stu-id="aebff-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="aebff-111">`PercentDone`事件还可以提供取消任务的机制。</span><span class="sxs-lookup"><span data-stu-id="aebff-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="aebff-112">生成本主题的代码示例</span><span class="sxs-lookup"><span data-stu-id="aebff-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="aebff-113">打开一个新的 Visual Basic Windows 应用程序项目，并创建一个名为的窗体 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="aebff-114">向添加两个按钮和一个标签 `Form1` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="aebff-115">按下表所示命名对象。</span><span class="sxs-lookup"><span data-stu-id="aebff-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="aebff-116">对象</span><span class="sxs-lookup"><span data-stu-id="aebff-116">Object</span></span>|<span data-ttu-id="aebff-117">Property</span><span class="sxs-lookup"><span data-stu-id="aebff-117">Property</span></span>|<span data-ttu-id="aebff-118">设置</span><span class="sxs-lookup"><span data-stu-id="aebff-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="aebff-119">启动任务</span><span class="sxs-lookup"><span data-stu-id="aebff-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="aebff-120">取消</span><span class="sxs-lookup"><span data-stu-id="aebff-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="aebff-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="aebff-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="aebff-122">lblPercentDone，0</span><span class="sxs-lookup"><span data-stu-id="aebff-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="aebff-123">在 "**项目**" 菜单上，选择 "**添加类**"，将名为的类添加 `Widget.vb` 到项目。</span><span class="sxs-lookup"><span data-stu-id="aebff-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="aebff-124">为小组件类声明事件</span><span class="sxs-lookup"><span data-stu-id="aebff-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="aebff-125">使用 `Event` 关键字声明类中的事件 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="aebff-126">请注意，事件可以具有 `ByVal` 和 `ByRef` 参数，如 `Widget` 事件所示 `PercentDone` ：</span><span class="sxs-lookup"><span data-stu-id="aebff-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="aebff-127">调用对象收到 `PercentDone` 事件时，该 `Percent` 参数包含已完成的任务的百分比。</span><span class="sxs-lookup"><span data-stu-id="aebff-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="aebff-128">`Cancel`参数可以设置为 `True` ，以取消引发事件的方法。</span><span class="sxs-lookup"><span data-stu-id="aebff-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aebff-129">可以声明事件自变量，就像处理过程的参数一样，但有以下例外：事件不能包含 `Optional` 或 `ParamArray` 参数，并且事件没有返回值。</span><span class="sxs-lookup"><span data-stu-id="aebff-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="aebff-130">此 `PercentDone` 事件由 `LongTask` 类的方法引发 `Widget` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="aebff-131">`LongTask`采用两个参数：方法在经过一段时间后进行工作，并在暂停之前的最小时间间隔内 `LongTask` 引发 `PercentDone` 事件。</span><span class="sxs-lookup"><span data-stu-id="aebff-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="aebff-132">引发 PercentDone 事件</span><span class="sxs-lookup"><span data-stu-id="aebff-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="aebff-133">若要简化对 `Timer` 此类使用的属性的访问，请将 `Imports` 语句添加到类模块的 "声明" 部分的顶部、语句的上方 `Class Widget` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="aebff-134">将以下代码添加到 `Widget` 类：</span><span class="sxs-lookup"><span data-stu-id="aebff-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="aebff-135">当应用程序调用 `LongTask` 方法时， `Widget` 类 `PercentDone` 每秒引发一次事件 `MinimumInterval` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="aebff-136">当事件返回时，将 `LongTask` 检查 `Cancel` 参数是否设置为 `True` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="aebff-137">此处有一些免责声明是必需的。</span><span class="sxs-lookup"><span data-stu-id="aebff-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="aebff-138">为简单起见，该 `LongTask` 过程假定您事先知道任务将花多长时间。</span><span class="sxs-lookup"><span data-stu-id="aebff-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="aebff-139">几乎不会出现这种情况。</span><span class="sxs-lookup"><span data-stu-id="aebff-139">This is almost never the case.</span></span> <span data-ttu-id="aebff-140">将任务划分为偶大的块可能比较困难，通常，用户最重要的是，用户只需经过一段时间，就能看出发生了什么情况。</span><span class="sxs-lookup"><span data-stu-id="aebff-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="aebff-141">在此示例中，可能已发现另一个缺陷。</span><span class="sxs-lookup"><span data-stu-id="aebff-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="aebff-142">`Timer`属性返回从午夜开始经过的秒数; 因此，如果该应用程序在午夜之前启动，则会停滞。</span><span class="sxs-lookup"><span data-stu-id="aebff-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="aebff-143">更仔细地测量时间的方法会将这类边界情况（例如这种情况）考虑在内，或使用属性（例如）来避免这种情况 `Now` 。</span><span class="sxs-lookup"><span data-stu-id="aebff-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="aebff-144">由于 `Widget` 该类可以引发事件，因此你可以转到下一个演练。</span><span class="sxs-lookup"><span data-stu-id="aebff-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="aebff-145">[演练：处理事件](walkthrough-handling-events.md)演示如何使用将 `WithEvents` 事件处理程序与 `PercentDone` 事件关联。</span><span class="sxs-lookup"><span data-stu-id="aebff-145">[Walkthrough: Handling Events](walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aebff-146">另请参阅</span><span class="sxs-lookup"><span data-stu-id="aebff-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="aebff-147">演练：处理事件</span><span class="sxs-lookup"><span data-stu-id="aebff-147">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)
- [<span data-ttu-id="aebff-148">事件</span><span class="sxs-lookup"><span data-stu-id="aebff-148">Events</span></span>](index.md)
