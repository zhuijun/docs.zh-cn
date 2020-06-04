---
title: 如何发布符合 .NET Framework 准则的事件 - C# 编程指南
ms.date: 05/26/2020
helpviewer_keywords:
- events [C#], implementation guidelines
ms.assetid: 9310ae16-8627-44a2-b08c-05e5976202b1
ms.openlocfilehash: 137e52b80703491a4528a3eddc7fa12f9dce6f52
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144794"
---
# <a name="how-to-publish-events-that-conform-to-net-framework-guidelines-c-programming-guide"></a><span data-ttu-id="8ee3b-102">如何发布符合 .NET Framework 准则的事件（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="8ee3b-102">How to publish events that conform to .NET Framework Guidelines (C# Programming Guide)</span></span>

<span data-ttu-id="8ee3b-103">下面的过程演示了如何将遵循标准 .NET Framework 模式的事件添加到类和结构中。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-103">The following procedure demonstrates how to add events that follow the standard .NET Framework pattern to your classes and structs.</span></span> <span data-ttu-id="8ee3b-104">.NET Framework 类库中的所有事件均基于 <xref:System.EventHandler> 委托，定义如下：</span><span class="sxs-lookup"><span data-stu-id="8ee3b-104">All events in the .NET Framework class library are based on the <xref:System.EventHandler> delegate, which is defined as follows:</span></span>

```csharp
public delegate void EventHandler(object sender, EventArgs e);
```

> [!NOTE]
> <span data-ttu-id="8ee3b-105">.NET Framework 2.0 引入了泛型版本的委托 <xref:System.EventHandler%601>。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-105">The .NET Framework 2.0 introduces a generic version of this delegate, <xref:System.EventHandler%601>.</span></span> <span data-ttu-id="8ee3b-106">下例演示了如何使用这两个版本。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-106">The following examples show how to use both versions.</span></span>

<span data-ttu-id="8ee3b-107">尽管定义的类中的事件可基于任何有效委托类型，甚至是返回值的委托，但一般还是建议使用 <xref:System.EventHandler> 使事件基于 .NET Framework 模式，如下例中所示。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-107">Although events in classes that you define can be based on any valid delegate type, even delegates that return a value, it is generally recommended that you base your events on the .NET Framework pattern by using <xref:System.EventHandler>, as shown in the following example.</span></span>

<span data-ttu-id="8ee3b-108">名称 `EventHandler` 可能导致一些混淆，因为它不会实际处理事件。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-108">The name `EventHandler` can lead to a bit of confusion as it doesn't actually handle the event.</span></span> <span data-ttu-id="8ee3b-109"><xref:System.EventHandler> 和泛型 <xref:System.EventHandler%601> 均为委托类型。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-109">The <xref:System.EventHandler>, and generic <xref:System.EventHandler%601> are delegate types.</span></span> <span data-ttu-id="8ee3b-110">其签名与委托定义匹配的方法或 Lambda 表达式是事件处理程序，并将在引发事件时调用。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-110">A method or lambda expression whose signature matches the delegate definition is the *event handler* and will be invoked when the event is raised.</span></span>

### <a name="to-publish-events-based-on-the-eventhandler-pattern"></a><span data-ttu-id="8ee3b-111">发布基于 EventHandler 模式的事件</span><span class="sxs-lookup"><span data-stu-id="8ee3b-111">To publish events based on the EventHandler pattern</span></span>

1. <span data-ttu-id="8ee3b-112">（如果无需随事件一起发送自定义数据，请跳过此步骤转到步骤 3a。）将自定义数据的类声明为对发布服务器和订阅者类均可见的范围。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-112">(Skip this step and go to Step 3a if you do not have to send custom data with your event.) Declare the class for your custom data at a scope that is visible to both your publisher and subscriber classes.</span></span> <span data-ttu-id="8ee3b-113">然后添加所需成员以保留自定义事件数据。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-113">Then add the required members to hold your custom event data.</span></span> <span data-ttu-id="8ee3b-114">在此示例中，将返回一个简单的字符串。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-114">In this example, a simple string is returned.</span></span>

    ```csharp
    public class CustomEventArgs : EventArgs
    {
        public CustomEventArgs(string message)
        {
            Message = message;
        }

        public string Message { get; set; }
    }
    ```

2. <span data-ttu-id="8ee3b-115">（如果使用的是泛型版本 <xref:System.EventHandler%601>，请跳过此步骤。）声明发布类中的委托。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-115">(Skip this step if you are using the generic version of <xref:System.EventHandler%601>.) Declare a delegate in your publishing class.</span></span> <span data-ttu-id="8ee3b-116">为其指定以 `EventHandler` 结尾的名称。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-116">Give it a name that ends with `EventHandler`.</span></span> <span data-ttu-id="8ee3b-117">第二个参数指定自定义 `EventArgs` 类型。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-117">The second parameter specifies your custom `EventArgs` type.</span></span>

    ```csharp
    public delegate void CustomEventHandler(object sender, CustomEventArgs args);
    ```

3. <span data-ttu-id="8ee3b-118">使用下列步骤之一来声明发布类中的事件。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-118">Declare the event in your publishing class by using one of the following steps.</span></span>

    1. <span data-ttu-id="8ee3b-119">如果没有任何自定义 EventArgs 类，事件类型将为非泛型 EventHandler 委托。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-119">If you have no custom EventArgs class, your Event type will be the non-generic EventHandler delegate.</span></span> <span data-ttu-id="8ee3b-120">你无需声明该委托，因为它已在创建 C# 项目时包括的 <xref:System> 命名空间中声明。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-120">You do not have to declare the delegate because it is already declared in the <xref:System> namespace that is included when you create your C# project.</span></span> <span data-ttu-id="8ee3b-121">将以下代码添加到发布服务器类。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-121">Add the following code to your publisher class.</span></span>

        ```csharp
        public event EventHandler RaiseCustomEvent;
        ```

    2. <span data-ttu-id="8ee3b-122">如果使用非泛型版本 <xref:System.EventHandler> 并且具有派生自 <xref:System.EventArgs> 的自定义类，请声明发布类中的事件，并将步骤 2 中的委托用作类型。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-122">If you are using the non-generic version of <xref:System.EventHandler> and you have a custom class derived from <xref:System.EventArgs>, declare your event inside your publishing class and use your delegate from step 2 as the type.</span></span>

        ```csharp
        public event CustomEventHandler RaiseCustomEvent;
        ```

    3. <span data-ttu-id="8ee3b-123">如果使用泛型版本，则无需自定义委托。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-123">If you are using the generic version, you do not need a custom delegate.</span></span> <span data-ttu-id="8ee3b-124">而是在发布类中，将事件类型指定为 `EventHandler<CustomEventArgs>`，替换尖括号中自定义类的名称。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-124">Instead, in your publishing class, you specify your event type as `EventHandler<CustomEventArgs>`, substituting the name of your own class between the angle brackets.</span></span>

        ```csharp
        public event EventHandler<CustomEventArgs> RaiseCustomEvent;
        ```

## <a name="example"></a><span data-ttu-id="8ee3b-125">示例</span><span class="sxs-lookup"><span data-stu-id="8ee3b-125">Example</span></span>

<span data-ttu-id="8ee3b-126">下例通过使用自定义 EventArgs 类和 <xref:System.EventHandler%601> 作为事件类型来演示之前的步骤。</span><span class="sxs-lookup"><span data-stu-id="8ee3b-126">The following example demonstrates the previous steps by using a custom EventArgs class and <xref:System.EventHandler%601> as the event type.</span></span>

[!code-csharp[csProgGuideEvents#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#2)]

## <a name="see-also"></a><span data-ttu-id="8ee3b-127">请参阅</span><span class="sxs-lookup"><span data-stu-id="8ee3b-127">See also</span></span>

- <xref:System.Delegate>
- [<span data-ttu-id="8ee3b-128">C# 编程指南</span><span class="sxs-lookup"><span data-stu-id="8ee3b-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8ee3b-129">事件</span><span class="sxs-lookup"><span data-stu-id="8ee3b-129">Events</span></span>](index.md)
- [<span data-ttu-id="8ee3b-130">委托</span><span class="sxs-lookup"><span data-stu-id="8ee3b-130">Delegates</span></span>](../delegates/index.md)
