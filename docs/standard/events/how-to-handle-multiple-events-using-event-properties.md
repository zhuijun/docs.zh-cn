---
title: 如何：使用事件属性处理多个事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- event properties [.NET Framework]
- multiple events [.NET Framework]
- event handling [.NET Framework], with multiple events
- events [.NET Framework], multiple
ms.assetid: 30047cba-e2fd-41c6-b9ca-2ad7a49003db
ms.openlocfilehash: c5be541c1a40c5d16a0502e76adef24f6a41cc89
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288467"
---
# <a name="how-to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="b41a8-102">如何：使用事件属性处理多个事件</span><span class="sxs-lookup"><span data-stu-id="b41a8-102">How to: Handle Multiple Events Using Event Properties</span></span>
<span data-ttu-id="b41a8-103">若要使用事件属性，请在引发事件的类中定义事件属性，然后在处理事件的类中设置事件属性的委托。</span><span class="sxs-lookup"><span data-stu-id="b41a8-103">To use event properties, you define the event properties in the class that raises the events, and then set the delegates for the event properties in classes that handle the events.</span></span> <span data-ttu-id="b41a8-104">若要在类中实现多个事件属性，此类必须在内部存储和维护为每个事件定义的委托。</span><span class="sxs-lookup"><span data-stu-id="b41a8-104">To implement multiple event properties in a class, the class must internally store and maintain the delegate defined for each event.</span></span> <span data-ttu-id="b41a8-105">典型的方法是实现通过事件键索引的委托集合。</span><span class="sxs-lookup"><span data-stu-id="b41a8-105">A typical approach is to implement a delegate collection that is indexed by an event key.</span></span>  
  
 <span data-ttu-id="b41a8-106">若要存储每个事件的委托，则可以使用 <xref:System.ComponentModel.EventHandlerList> 类，或实现自己的集合。</span><span class="sxs-lookup"><span data-stu-id="b41a8-106">To store the delegates for each event, you can use the <xref:System.ComponentModel.EventHandlerList> class, or implement your own collection.</span></span> <span data-ttu-id="b41a8-107">集合类必须基于事件键提供用于设置、访问和检索事件处理程序委托的方法。</span><span class="sxs-lookup"><span data-stu-id="b41a8-107">The collection class must provide methods for setting, accessing, and retrieving the event handler delegate based on the event key.</span></span> <span data-ttu-id="b41a8-108">例如，可以使用 <xref:System.Collections.Hashtable> 类，或从 <xref:System.Collections.DictionaryBase> 类中派生一个自定义的类。</span><span class="sxs-lookup"><span data-stu-id="b41a8-108">For example, you could use a <xref:System.Collections.Hashtable> class, or derive a custom class from the <xref:System.Collections.DictionaryBase> class.</span></span> <span data-ttu-id="b41a8-109">委托集合的实现细节不需要在你的类的外部公开。</span><span class="sxs-lookup"><span data-stu-id="b41a8-109">The implementation details of the delegate collection do not need to be exposed outside your class.</span></span>  
  
 <span data-ttu-id="b41a8-110">类中的每个事件属性都定义了一个 add 访问器方法和一个 remove 访问器方法。</span><span class="sxs-lookup"><span data-stu-id="b41a8-110">Each event property within the class defines an add accessor method and a remove accessor method.</span></span> <span data-ttu-id="b41a8-111">事件属性的 add 访问器将输入委托实例添加到委托集合。</span><span class="sxs-lookup"><span data-stu-id="b41a8-111">The add accessor for an event property adds the input delegate instance to the delegate collection.</span></span> <span data-ttu-id="b41a8-112">事件属性的 remove 访问器将输入委托实例从委托集合中移除。</span><span class="sxs-lookup"><span data-stu-id="b41a8-112">The remove accessor for an event property removes the input delegate instance from the delegate collection.</span></span> <span data-ttu-id="b41a8-113">事件属性访问器使用的预定义的事件属性键来将实例添加到委托集合或从中将实例移除。</span><span class="sxs-lookup"><span data-stu-id="b41a8-113">The event property accessors use the predefined key for the event property to add and remove instances from the delegate collection.</span></span>  
  
### <a name="to-handle-multiple-events-using-event-properties"></a><span data-ttu-id="b41a8-114">使用事件属性处理多个事件</span><span class="sxs-lookup"><span data-stu-id="b41a8-114">To handle multiple events using event properties</span></span>  
  
1. <span data-ttu-id="b41a8-115">定义引发事件的类中的委托集合。</span><span class="sxs-lookup"><span data-stu-id="b41a8-115">Define a delegate collection within the class that raises the events.</span></span>  
  
2. <span data-ttu-id="b41a8-116">定义每个事件的键。</span><span class="sxs-lookup"><span data-stu-id="b41a8-116">Define a key for each event.</span></span>  
  
3. <span data-ttu-id="b41a8-117">定义引发事件的类中的事件属性。</span><span class="sxs-lookup"><span data-stu-id="b41a8-117">Define the event properties in the class that raises the events.</span></span>  
  
4. <span data-ttu-id="b41a8-118">使用委托集合实现添加和移除事件属性的 add 和 remove 访问器方法。</span><span class="sxs-lookup"><span data-stu-id="b41a8-118">Use the delegate collection to implement the add and remove accessor methods for the event properties.</span></span>  
  
5. <span data-ttu-id="b41a8-119">使用公共事件属性来添加和移除处理事件的类中的事件处理程序委托。</span><span class="sxs-lookup"><span data-stu-id="b41a8-119">Use the public event properties to add and remove event handler delegates in the classes that handle the events.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b41a8-120">示例</span><span class="sxs-lookup"><span data-stu-id="b41a8-120">Example</span></span>  
 <span data-ttu-id="b41a8-121">下面的 C# 示例实现事件属性 `MouseDown` 和 `MouseUp`，其中使用 <xref:System.ComponentModel.EventHandlerList> 来存储每个事件的委托。</span><span class="sxs-lookup"><span data-stu-id="b41a8-121">The following C# example implements the event properties `MouseDown` and `MouseUp`, using an <xref:System.ComponentModel.EventHandlerList> to store each event's delegate.</span></span> <span data-ttu-id="b41a8-122">事件属性构造的关键字是粗体类型。</span><span class="sxs-lookup"><span data-stu-id="b41a8-122">The keywords of the event property constructs are in bold type.</span></span>  
  
 [!code-cpp[Conceptual.Events.Other#31](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.events.other/cpp/example3.cpp#31)]
 [!code-csharp[Conceptual.Events.Other#31](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.events.other/cs/example3.cs#31)]
 [!code-vb[Conceptual.Events.Other#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.events.other/vb/example3.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="b41a8-123">另请参阅</span><span class="sxs-lookup"><span data-stu-id="b41a8-123">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList?displayProperty=nameWithType>
- [<span data-ttu-id="b41a8-124">事件</span><span class="sxs-lookup"><span data-stu-id="b41a8-124">Events</span></span>](index.md)
- <xref:System.Web.UI.Control.Events%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b41a8-125">如何：声明自定义事件以节省内存</span><span class="sxs-lookup"><span data-stu-id="b41a8-125">How to: Declare Custom Events To Conserve Memory</span></span>](../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)
