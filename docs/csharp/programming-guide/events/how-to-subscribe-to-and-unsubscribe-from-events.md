---
title: 如何订阅和取消订阅事件 - C# 编程指南
ms.date: 07/20/2015
helpviewer_keywords:
- event handlers [C#], creating
- Code Editor, event handlers
- events [C#], creating using the IDE
ms.assetid: 6319f39f-282c-4173-8a62-6c4657cf51cd
ms.openlocfilehash: d917ea097cf9253a65c1907efdca71a640df9497
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240663"
---
# <a name="how-to-subscribe-to-and-unsubscribe-from-events-c-programming-guide"></a><span data-ttu-id="4476d-102">如何订阅和取消订阅事件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="4476d-102">How to subscribe to and unsubscribe from events (C# Programming Guide)</span></span>
<span data-ttu-id="4476d-103">如果想编写引发事件时调用的自定义代码，则可以订阅由其他类发布的事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-103">You subscribe to an event that is published by another class when you want to write custom code that is called when that event is raised.</span></span> <span data-ttu-id="4476d-104">例如，可以订阅某个按钮的 `click` 事件，以使应用程序在用户单击该按钮时执行一些有用的操作。</span><span class="sxs-lookup"><span data-stu-id="4476d-104">For example, you might subscribe to a button's `click` event in order to make your application do something useful when the user clicks the button.</span></span>  
  
### <a name="to-subscribe-to-events-by-using-the-visual-studio-ide"></a><span data-ttu-id="4476d-105">使用 Visual Studio IDE 订阅事件</span><span class="sxs-lookup"><span data-stu-id="4476d-105">To subscribe to events by using the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="4476d-106">如果看不到“属性”窗口，请在“设计”视图中，右键单击要为其创建事件处理程序的窗体或控件，然后选择“属性”  。</span><span class="sxs-lookup"><span data-stu-id="4476d-106">If you cannot see the **Properties** window, in **Design** view, right-click the form or control for which you want to create an event handler, and select **Properties**.</span></span>  
  
2. <span data-ttu-id="4476d-107">在“属性”窗口的顶部，单击“事件”图标 。</span><span class="sxs-lookup"><span data-stu-id="4476d-107">On top of the **Properties** window, click the **Events** icon.</span></span>  
  
3. <span data-ttu-id="4476d-108">双击要创建的事件，例如 `Load` 事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-108">Double-click the event that you want to create, for example the `Load` event.</span></span>  
  
     <span data-ttu-id="4476d-109">Visual C# 会创建一个空事件处理程序方法，并将其添加到你的代码中。</span><span class="sxs-lookup"><span data-stu-id="4476d-109">Visual C# creates an empty event handler method and adds it to your code.</span></span> <span data-ttu-id="4476d-110">或者，也可以在“代码”视图中手动添加代码。</span><span class="sxs-lookup"><span data-stu-id="4476d-110">Alternatively you can add the code manually in **Code** view.</span></span> <span data-ttu-id="4476d-111">例如，下面的代码行声明了一个在 `Form` 类引发 `Load` 事件时调用的事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="4476d-111">For example, the following lines of code declare an event handler method that will be called when the `Form` class raises the `Load` event.</span></span>  
  
     [!code-csharp[csProgGuideEvents#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#11)]  
  
     <span data-ttu-id="4476d-112">还会在项目的 Form1.Designer.cs 文件的 `InitializeComponent` 方法中自动生成订阅该事件所需的代码行。</span><span class="sxs-lookup"><span data-stu-id="4476d-112">The line of code that is required to subscribe to the event is also automatically generated in the `InitializeComponent` method in the Form1.Designer.cs file in your project.</span></span> <span data-ttu-id="4476d-113">该代码行类似于：</span><span class="sxs-lookup"><span data-stu-id="4476d-113">It resembles this:</span></span>  
  
    ```csharp
    this.Load += new System.EventHandler(this.Form1_Load);  
    ```  
  
### <a name="to-subscribe-to-events-programmatically"></a><span data-ttu-id="4476d-114">以编程方式订阅事件</span><span class="sxs-lookup"><span data-stu-id="4476d-114">To subscribe to events programmatically</span></span>  
  
1. <span data-ttu-id="4476d-115">定义一个事件处理程序方法，其签名与该事件的委托签名匹配。</span><span class="sxs-lookup"><span data-stu-id="4476d-115">Define an event handler method whose signature matches the delegate signature for the event.</span></span> <span data-ttu-id="4476d-116">例如，如果事件基于 <xref:System.EventHandler> 委托类型，则下面的代码表示方法存根：</span><span class="sxs-lookup"><span data-stu-id="4476d-116">For example, if the event is based on the <xref:System.EventHandler> delegate type, the following code represents the method stub:</span></span>  
  
    ```csharp
    void HandleCustomEvent(object sender, CustomEventArgs a)  
    {  
       // Do something useful here.  
    }  
    ```  
  
2. <span data-ttu-id="4476d-117">使用加法赋值运算符 (`+=`) 来为事件附加事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="4476d-117">Use the addition assignment operator (`+=`) to attach an event handler to the event.</span></span> <span data-ttu-id="4476d-118">在下面的示例中，假设名为 `publisher` 的对象拥有一个名为 `RaiseCustomEvent` 的事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-118">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent`.</span></span> <span data-ttu-id="4476d-119">请注意，订户类需要引用发行者类才能订阅其事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-119">Note that the subscriber class needs a reference to the publisher class in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="4476d-120">请注意，前面的语法是 C# 2.0 中的新语法。</span><span class="sxs-lookup"><span data-stu-id="4476d-120">Note that the previous syntax is new in C# 2.0.</span></span> <span data-ttu-id="4476d-121">此语法完全等效于必须使用 `new` 关键字显式创建封装委托的 C# 1.0 语法：</span><span class="sxs-lookup"><span data-stu-id="4476d-121">It is exactly equivalent to the C# 1.0 syntax in which the encapsulating delegate must be explicitly created by using the `new` keyword:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += new CustomEventHandler(HandleCustomEvent);  
    ```  
  
     <span data-ttu-id="4476d-122">还可以使用 [Lambda 表达式](../statements-expressions-operators/lambda-expressions.md)来指定事件处理程序：</span><span class="sxs-lookup"><span data-stu-id="4476d-122">You can also use a [lambda expression](../statements-expressions-operators/lambda-expressions.md) to specify an event handler:</span></span>
  
    ```csharp
    public Form1()  
    {  
        InitializeComponent();  
        this.Click += (s,e) =>
            {
                MessageBox.Show(((MouseEventArgs)e).Location.ToString());
            };
    }  
    ```  
  
### <a name="to-subscribe-to-events-by-using-an-anonymous-method"></a><span data-ttu-id="4476d-123">使用匿名方法订阅事件</span><span class="sxs-lookup"><span data-stu-id="4476d-123">To subscribe to events by using an anonymous method</span></span>  
  
- <span data-ttu-id="4476d-124">如果以后不必取消订阅某个事件，则可以使用加法赋值运算符 (`+=`) 将匿名方法附加到此事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-124">If you will not have to unsubscribe to an event later, you can use the addition assignment operator (`+=`) to attach an anonymous method to the event.</span></span> <span data-ttu-id="4476d-125">在下面的示例中，假设名为 `publisher` 的对象拥有一个名为 `RaiseCustomEvent` 的事件，并且还定义了一个 `CustomEventArgs` 类以承载某些类型的专用事件信息。</span><span class="sxs-lookup"><span data-stu-id="4476d-125">In the following example, assume that an object named `publisher` has an event named `RaiseCustomEvent` and that a `CustomEventArgs` class has also been defined to carry some kind of specialized event information.</span></span> <span data-ttu-id="4476d-126">请注意，订户类需要引用 `publisher` 才能订阅其事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-126">Note that the subscriber class needs a reference to `publisher` in order to subscribe to its events.</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent += delegate(object o, CustomEventArgs e)  
    {  
      string s = o.ToString() + " " + e.ToString();  
      Console.WriteLine(s);  
    };  
    ```  
  
     <span data-ttu-id="4476d-127">请务必注意，如果使用匿名函数订阅事件，事件的取消订阅过程将比较麻烦。</span><span class="sxs-lookup"><span data-stu-id="4476d-127">It is important to notice that you cannot easily unsubscribe from an event if you used an anonymous function to subscribe to it.</span></span> <span data-ttu-id="4476d-128">这种情况下若要取消订阅，必须返回到该事件的订阅代码，将该匿名方法存储在委托变量中，然后将此委托添加到该事件中。</span><span class="sxs-lookup"><span data-stu-id="4476d-128">To unsubscribe in this scenario, it is necessary to go back to the code where you subscribe to the event, store the anonymous method in a delegate variable, and then add the delegate to the event.</span></span> <span data-ttu-id="4476d-129">一般来说，如果必须在后面的代码中取消订阅某个事件，则建议不要使用匿名函数订阅此事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-129">In general, we recommend that you do not use anonymous functions to subscribe to events if you will have to unsubscribe from the event at some later point in your code.</span></span> <span data-ttu-id="4476d-130">有关匿名函数的详细信息，请参阅[匿名函数](../statements-expressions-operators/anonymous-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="4476d-130">For more information about anonymous functions, see [Anonymous Functions](../statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="unsubscribing"></a><span data-ttu-id="4476d-131">取消订阅</span><span class="sxs-lookup"><span data-stu-id="4476d-131">Unsubscribing</span></span>  
 <span data-ttu-id="4476d-132">若要防止在引发事件时调用事件处理程序，请取消订阅该事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-132">To prevent your event handler from being invoked when the event is raised, unsubscribe from the event.</span></span> <span data-ttu-id="4476d-133">为了防止资源泄露，应在释放订户对象之前取消订阅事件。</span><span class="sxs-lookup"><span data-stu-id="4476d-133">In order to prevent resource leaks, you should unsubscribe from events before you dispose of a subscriber object.</span></span> <span data-ttu-id="4476d-134">在取消订阅事件之前，在发布对象中作为该事件的基础的多播委托会引用封装了订户的事件处理程序的委托。</span><span class="sxs-lookup"><span data-stu-id="4476d-134">Until you unsubscribe from an event, the multicast delegate that underlies the event in the publishing object has a reference to the delegate that encapsulates the subscriber's event handler.</span></span> <span data-ttu-id="4476d-135">只要发布对象保持该引用，垃圾回收功能就不会删除订户对象。</span><span class="sxs-lookup"><span data-stu-id="4476d-135">As long as the publishing object holds that reference, garbage collection will not delete your subscriber object.</span></span>  
  
#### <a name="to-unsubscribe-from-an-event"></a><span data-ttu-id="4476d-136">取消订阅事件</span><span class="sxs-lookup"><span data-stu-id="4476d-136">To unsubscribe from an event</span></span>  
  
- <span data-ttu-id="4476d-137">使用减法赋值运算符 (`-=`) 取消订阅事件：</span><span class="sxs-lookup"><span data-stu-id="4476d-137">Use the subtraction assignment operator (`-=`) to unsubscribe from an event:</span></span>  
  
    ```csharp
    publisher.RaiseCustomEvent -= HandleCustomEvent;  
    ```  
  
     <span data-ttu-id="4476d-138">所有订户都取消订阅事件后，发行者类中的事件实例将设置为 `null`。</span><span class="sxs-lookup"><span data-stu-id="4476d-138">When all subscribers have unsubscribed from an event, the event instance in the publisher class is set to `null`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4476d-139">请参阅</span><span class="sxs-lookup"><span data-stu-id="4476d-139">See also</span></span>

- [<span data-ttu-id="4476d-140">事件</span><span class="sxs-lookup"><span data-stu-id="4476d-140">Events</span></span>](./index.md)
- [<span data-ttu-id="4476d-141">event</span><span class="sxs-lookup"><span data-stu-id="4476d-141">event</span></span>](../../language-reference/keywords/event.md)
- [<span data-ttu-id="4476d-142">如何发布符合 .NET 准则的事件</span><span class="sxs-lookup"><span data-stu-id="4476d-142">How to publish events that conform to .NET Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)
- [<span data-ttu-id="4476d-143">- 和 -= 运算符</span><span class="sxs-lookup"><span data-stu-id="4476d-143">- and -= operators</span></span>](../../language-reference/operators/subtraction-operator.md)
- [<span data-ttu-id="4476d-144">+ 和 += 运算符</span><span class="sxs-lookup"><span data-stu-id="4476d-144">+ and += operators</span></span>](../../language-reference/operators/addition-operator.md)
