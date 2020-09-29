---
title: 如何实现自定义事件访问器 - C# 编程指南
description: 了解如何实现自定义事件访问器。 查看代码示例和其他可用资源。
ms.date: 07/20/2015
helpviewer_keywords:
- accessors [C#], event accessors
- add accessor [C#]
- events [C#], add accessor
- events [C#], remove accessor
- remove accessor [C#]
ms.assetid: bf903abf-03a4-4f7b-ab6b-b7e59bc2ee1e
ms.openlocfilehash: 41c9bd255bf66cd914982b6044c4acaef66b8fcf
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167556"
---
# <a name="how-to-implement-custom-event-accessors-c-programming-guide"></a><span data-ttu-id="03ee0-104">如何实现自定义事件访问器（C# 编程指南）</span><span class="sxs-lookup"><span data-stu-id="03ee0-104">How to implement custom event accessors (C# Programming Guide)</span></span>

<span data-ttu-id="03ee0-105">事件是一种特殊的多播委托，只能从声明它的类中进行调用。</span><span class="sxs-lookup"><span data-stu-id="03ee0-105">An event is a special kind of multicast delegate that can only be invoked from within the class that  it is declared in.</span></span> <span data-ttu-id="03ee0-106">客户端代码通过提供对应在引发事件时调用的方法的引用来订阅事件。</span><span class="sxs-lookup"><span data-stu-id="03ee0-106">Client code subscribes to the event by providing a reference to a method that should be invoked when the event is fired.</span></span> <span data-ttu-id="03ee0-107">这些方法通过事件访问器添加到委托的调用列表中，事件访问器类似于属性访问器，不同之处在于事件访问器命名为 `add` 和 `remove`。</span><span class="sxs-lookup"><span data-stu-id="03ee0-107">These methods are added to the delegate's invocation list through event accessors, which resemble property accessors, except that event accessors are named `add` and `remove`.</span></span> <span data-ttu-id="03ee0-108">在大多数情况下，无需提供自定义事件访问器。</span><span class="sxs-lookup"><span data-stu-id="03ee0-108">In most cases, you do not have to supply custom event accessors.</span></span> <span data-ttu-id="03ee0-109">如果代码中没有提供自定义事件访问器，编译器将自动添加它们。</span><span class="sxs-lookup"><span data-stu-id="03ee0-109">When no custom event accessors are supplied in your code, the compiler will add them automatically.</span></span> <span data-ttu-id="03ee0-110">但在某些情况下，可能需要提供自定义行为。</span><span class="sxs-lookup"><span data-stu-id="03ee0-110">However, in some cases you may have to provide custom behavior.</span></span> <span data-ttu-id="03ee0-111">主题[如何实现接口事件](./how-to-implement-interface-events.md)中介绍了这样一种情况。</span><span class="sxs-lookup"><span data-stu-id="03ee0-111">One such case is shown in the topic [How to implement interface events](./how-to-implement-interface-events.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="03ee0-112">示例</span><span class="sxs-lookup"><span data-stu-id="03ee0-112">Example</span></span>  

 <span data-ttu-id="03ee0-113">下面的示例演示如何实现自定义的 add 和 remove 事件访问器。</span><span class="sxs-lookup"><span data-stu-id="03ee0-113">The following example shows how to implement custom add and remove event accessors.</span></span> <span data-ttu-id="03ee0-114">虽然可以替换访问器内的任何代码，但建议先锁定事件，再添加或删除新的事件处理程序方法。</span><span class="sxs-lookup"><span data-stu-id="03ee0-114">Although you can substitute any code inside the accessors, we recommend that you lock the event before you add or remove a new event handler method.</span></span>  
  
[!code-csharp[IDrawingObject.OnDraw](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#IDrawingObjectOnDraw)]  
  
## <a name="see-also"></a><span data-ttu-id="03ee0-115">请参阅</span><span class="sxs-lookup"><span data-stu-id="03ee0-115">See also</span></span>

- [<span data-ttu-id="03ee0-116">事件</span><span class="sxs-lookup"><span data-stu-id="03ee0-116">Events</span></span>](./index.md)
- [<span data-ttu-id="03ee0-117">event</span><span class="sxs-lookup"><span data-stu-id="03ee0-117">event</span></span>](../../language-reference/keywords/event.md)
