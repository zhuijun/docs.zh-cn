---
title: 事件
description: '了解 F # 事件如何使你能够将函数调用与用户操作关联，这在 GUI 编程中非常重要。'
ms.date: 05/16/2016
ms.openlocfilehash: 682686ba58d0f7a56e7da2585e6507ccd0156a44
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854927"
---
# <a name="events"></a><span data-ttu-id="0819e-103">事件</span><span class="sxs-lookup"><span data-stu-id="0819e-103">Events</span></span>

<span data-ttu-id="0819e-104">事件允许您将函数调用与用户操作关联，并且是 GUI 编程的关键所在。</span><span class="sxs-lookup"><span data-stu-id="0819e-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="0819e-105">事件也可以由应用程序或操作系统触发。</span><span class="sxs-lookup"><span data-stu-id="0819e-105">Events can also be triggered by your applications or by the operating system.</span></span>

> [!NOTE]
> <span data-ttu-id="0819e-106">F # 的 docs.microsoft.com API 参考未完成。</span><span class="sxs-lookup"><span data-stu-id="0819e-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="0819e-107">如果遇到任何断开的链接，请参阅[F # 核心库文档](https://fsharp.github.io/fsharp-core-docs/)。</span><span class="sxs-lookup"><span data-stu-id="0819e-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="handling-events"></a><span data-ttu-id="0819e-108">处理事件</span><span class="sxs-lookup"><span data-stu-id="0819e-108">Handling Events</span></span>

<span data-ttu-id="0819e-109">当您使用诸如 Windows 窗体或 Windows Presentation Foundation (WPF) 之类的 GUI 库时，应用程序中的大部分代码都是针对该库预定义的事件运行的。</span><span class="sxs-lookup"><span data-stu-id="0819e-109">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="0819e-110">这些预定义事件是诸如窗体和控件等 GUI 类的成员。</span><span class="sxs-lookup"><span data-stu-id="0819e-110">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="0819e-111">通过引用有意义的特定命名事件（例如，`Click` 类的 `Form` 事件）并调用 `Add` 方法，您可以向预先存在的事件（例如按钮单击）中添加自定义行为，如下面的代码所示。</span><span class="sxs-lookup"><span data-stu-id="0819e-111">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="0819e-112">如果您从 F# Interactive 运行此事件，请忽略对 `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)` 的调用。</span><span class="sxs-lookup"><span data-stu-id="0819e-112">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="0819e-113">`Add` 方法的类型为 `('a -> unit) -> unit`。</span><span class="sxs-lookup"><span data-stu-id="0819e-113">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="0819e-114">因此，事件处理程序方法将接受一个参数（通常为事件自变量），并返回 `unit`。</span><span class="sxs-lookup"><span data-stu-id="0819e-114">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="0819e-115">前面的示例显示了 lambda 表达式形式的事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0819e-115">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="0819e-116">事件处理程序也可以为函数值，如下面的代码示例所示。</span><span class="sxs-lookup"><span data-stu-id="0819e-116">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="0819e-117">下面的代码示例还显示了事件处理程序参数的用法，这些参数提供特定于事件类型的信息。</span><span class="sxs-lookup"><span data-stu-id="0819e-117">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="0819e-118">对于 `MouseMove` 事件，系统将传递 `System.Windows.Forms.MouseEventArgs` 对象，其中包含指针的 `X` 和 `Y` 位置。</span><span class="sxs-lookup"><span data-stu-id="0819e-118">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="0819e-119">创建自定义事件</span><span class="sxs-lookup"><span data-stu-id="0819e-119">Creating Custom Events</span></span>

<span data-ttu-id="0819e-120">F # 事件由 F #[事件类](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9)表示，此类实现[IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862)接口。</span><span class="sxs-lookup"><span data-stu-id="0819e-120">F# events are represented by the F# [Event](https://msdn.microsoft.com/library/f3b47c8a-4ee5-4ce8-9a72-ad305a17c4b9) class, which implements the [IEvent](https://msdn.microsoft.com/library/8dbca0df-f8a1-40bd-8d50-aa26f6a8b862) interface.</span></span> <span data-ttu-id="0819e-121">`IEvent`本身是一个接口，它合并了两个其他接口（ `System.IObservable<'T>` 和[IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a)）的功能。</span><span class="sxs-lookup"><span data-stu-id="0819e-121">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://msdn.microsoft.com/library/3d849465-6b8e-4fc5-b36c-2941d734268a).</span></span> <span data-ttu-id="0819e-122">因此，在其他语言中，`Event` 具有委托的同等功能，以及来自 `IObservable` 的附加功能，这意味着 F# 事件支持事件筛选并使用 F# 第一类函数和 lambda 表达式作为事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0819e-122">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="0819e-123">此功能在[事件模块](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7)中提供。</span><span class="sxs-lookup"><span data-stu-id="0819e-123">This functionality is provided in the [Event module](https://msdn.microsoft.com/library/8b883baa-a460-4840-9baa-de8260351bc7).</span></span>

<span data-ttu-id="0819e-124">若要像任何其他 .NET Framework 事件一样为某个类创建事件，请向该类添加一个 `let` 绑定，用于将 `Event` 定义为类中的字段。</span><span class="sxs-lookup"><span data-stu-id="0819e-124">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="0819e-125">您可以将所需的事件参数类型指定为类型参数，或将其保留为空，让编译器推断出相应的类型。</span><span class="sxs-lookup"><span data-stu-id="0819e-125">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="0819e-126">还必须定义一个将事件公开为 CLI 事件的事件成员。</span><span class="sxs-lookup"><span data-stu-id="0819e-126">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="0819e-127">此成员应具有[CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333)属性。</span><span class="sxs-lookup"><span data-stu-id="0819e-127">This member should have the [CLIEvent](https://msdn.microsoft.com/library/d359f1dd-ffa5-42fb-8808-b4c8131a0333) attribute.</span></span> <span data-ttu-id="0819e-128">它的声明方式与属性类似，其实现只是对事件的[发布](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e)属性的调用。</span><span class="sxs-lookup"><span data-stu-id="0819e-128">It is declared like a property and its implementation is just a call to the [Publish](https://msdn.microsoft.com/library/b0fdaad5-25e5-43d0-9c0c-ce37c4aeb68e) property of the event.</span></span> <span data-ttu-id="0819e-129">类用户可使用已发布事件的 `Add` 方法来添加处理程序。</span><span class="sxs-lookup"><span data-stu-id="0819e-129">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="0819e-130">`Add` 方法的参数可以为 lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="0819e-130">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="0819e-131">你可以使用事件的 `Trigger` 属性来引发事件，并将自变量传递给处理程序函数。</span><span class="sxs-lookup"><span data-stu-id="0819e-131">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="0819e-132">下面的代码示例阐释了这一点。</span><span class="sxs-lookup"><span data-stu-id="0819e-132">The following code example illustrates this.</span></span> <span data-ttu-id="0819e-133">在此示例中，事件的推断类型参数是一个元组，它表示 lambda 表达式的参数。</span><span class="sxs-lookup"><span data-stu-id="0819e-133">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="0819e-134">输出如下所示。</span><span class="sxs-lookup"><span data-stu-id="0819e-134">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="0819e-135">此处阐释了 `Event` 模块提供的附加功能。</span><span class="sxs-lookup"><span data-stu-id="0819e-135">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="0819e-136">下面的代码示例阐释了 `Event.create` 的基本用法：创建一个事件和一个触发器方法，添加两个 Lambda 表达式形式的事件处理程序，然后触发该事件来执行这两个 Lambda 表达式。</span><span class="sxs-lookup"><span data-stu-id="0819e-136">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="0819e-137">上述代码的输出结果如下。</span><span class="sxs-lookup"><span data-stu-id="0819e-137">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="0819e-138">处理事件流</span><span class="sxs-lookup"><span data-stu-id="0819e-138">Processing Event Streams</span></span>

<span data-ttu-id="0819e-139">您可以使用模块中的函数[Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) `Event` 以高度自定义的方式来处理事件流，而不是仅通过使用 event 函数为事件添加事件处理程序。</span><span class="sxs-lookup"><span data-stu-id="0819e-139">Instead of just adding an event handler for an event by using the [Event.add](https://msdn.microsoft.com/library/10670d3b-8d47-4f6e-b8df-ebc6f64ef4fd) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="0819e-140">为此，可以使用前向管道 (`|>`) 以及事件作为一系列函数调用中的第一个值，并使用 `Event` 模块函数作为后续的函数调用。</span><span class="sxs-lookup"><span data-stu-id="0819e-140">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="0819e-141">下面的代码示例显示如何设置仅在某些情况下才会为其调用事件处理程序的事件。</span><span class="sxs-lookup"><span data-stu-id="0819e-141">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="0819e-142">可[观察模块](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227)包含可在可观察对象上操作的类似函数。</span><span class="sxs-lookup"><span data-stu-id="0819e-142">The [Observable module](https://msdn.microsoft.com/library/16b8610b-b30a-4df7-aa99-d9d352276227) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="0819e-143">可观测对象与事件类似，但只有在其本身被订阅时才会主动订阅事件。</span><span class="sxs-lookup"><span data-stu-id="0819e-143">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="0819e-144">实现 Interface 事件</span><span class="sxs-lookup"><span data-stu-id="0819e-144">Implementing an Interface Event</span></span>

<span data-ttu-id="0819e-145">在开发 UI 组件时，你通常会先创建继承自现有窗体或控件的新窗体或新控件。</span><span class="sxs-lookup"><span data-stu-id="0819e-145">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="0819e-146">事件经常是在接口上定义的，在此情况下，你必须实现接口才能实现事件。</span><span class="sxs-lookup"><span data-stu-id="0819e-146">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="0819e-147">`System.ComponentModel.INotifyPropertyChanged` 接口定义单个 `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` 事件。</span><span class="sxs-lookup"><span data-stu-id="0819e-147">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="0819e-148">以下代码演示如何实现此继承接口定义的事件：</span><span class="sxs-lookup"><span data-stu-id="0819e-148">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="0819e-149">若要在构造函数中挂钩事件，代码会有点复杂，因为事件挂钩必须位于其他构造函数的 `then` 块中，如下面的示例所示：</span><span class="sxs-lookup"><span data-stu-id="0819e-149">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property %s changed its value to %s" args.PropertyName newValue

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="0819e-150">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0819e-150">See also</span></span>

- [<span data-ttu-id="0819e-151">成员</span><span class="sxs-lookup"><span data-stu-id="0819e-151">Members</span></span>](index.md)
- [<span data-ttu-id="0819e-152">处理和引发事件</span><span class="sxs-lookup"><span data-stu-id="0819e-152">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="0819e-153">Lambda 表达式： `fun` 关键字</span><span class="sxs-lookup"><span data-stu-id="0819e-153">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
- [<span data-ttu-id="0819e-154">控件。事件模块</span><span class="sxs-lookup"><span data-stu-id="0819e-154">Control.Event Module</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event-module-%5bfsharp%5d)
- [<span data-ttu-id="0819e-155">控件。事件&#60; 不&#62; 类</span><span class="sxs-lookup"><span data-stu-id="0819e-155">Control.Event&#60;'T&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27t%5d-class-%5bfsharp%5d)
- [<span data-ttu-id="0819e-156">Control. Event&#60; "Delegate，" Args&#62; 类</span><span class="sxs-lookup"><span data-stu-id="0819e-156">Control.Event&#60;'Delegate,'Args&#62; Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/control.event%5b%27delegate%2c%27args%5d-class-%5bfsharp%5d)
