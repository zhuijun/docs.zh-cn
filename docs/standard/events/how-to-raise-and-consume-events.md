---
title: 如何：引发和使用事件
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- events [.NET Framework], raising
- raising events
- events [.NET Framework], samples
ms.assetid: 42afade7-3a02-4f2e-868b-95845f302f8f
ms.openlocfilehash: 4d0b24b8a6f1b914745d819b90b973752e32447c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279953"
---
# <a name="how-to-raise-and-consume-events"></a><span data-ttu-id="585fc-102">如何：引发和使用事件</span><span class="sxs-lookup"><span data-stu-id="585fc-102">How to: Raise and Consume Events</span></span>
<span data-ttu-id="585fc-103">本主题中的示例演示如何处理事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-103">The examples in this topic show how to work with events.</span></span> <span data-ttu-id="585fc-104">它们包含 <xref:System.EventHandler>、<xref:System.EventHandler%601> 委托和自定义委托的示例，用于说明包含数据和不包含数据的事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-104">They include examples of the <xref:System.EventHandler> delegate, the <xref:System.EventHandler%601> delegate, and a custom delegate, to illustrate events with and without data.</span></span>  
  
 <span data-ttu-id="585fc-105">这些示例使用[事件](index.md)一文中介绍的概念。</span><span class="sxs-lookup"><span data-stu-id="585fc-105">The examples use concepts described in the [Events](index.md) article.</span></span>  
  
## <a name="example"></a><span data-ttu-id="585fc-106">示例</span><span class="sxs-lookup"><span data-stu-id="585fc-106">Example</span></span>  
 <span data-ttu-id="585fc-107">第一个示例演示如何引发和使用一个没有数据的事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-107">The first example shows how to raise and consume an event that doesn't have data.</span></span> <span data-ttu-id="585fc-108">它包含一个名为 `Counter` 类，该类具有一个名为 `ThresholdReached` 的事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-108">It contains a class named `Counter` that has an event named `ThresholdReached`.</span></span> <span data-ttu-id="585fc-109">当计数器值等于或者超过阈值时，将引发此事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-109">This event is raised when a counter value equals or exceeds a threshold value.</span></span> <span data-ttu-id="585fc-110"><xref:System.EventHandler> 委托与此事件关联，因为没有提供任何事件数据。</span><span class="sxs-lookup"><span data-stu-id="585fc-110">The <xref:System.EventHandler> delegate is associated with the event, because no event data is provided.</span></span>  
  
 [!code-csharp[EventsOverview#5](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programnodata.cs#5)]
 [!code-vb[EventsOverview#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1nodata.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="585fc-111">示例</span><span class="sxs-lookup"><span data-stu-id="585fc-111">Example</span></span>  
 <span data-ttu-id="585fc-112">下一个示例演示如何引发和使用提供数据的事件。</span><span class="sxs-lookup"><span data-stu-id="585fc-112">The next example shows how to raise and consume an event that provides data.</span></span> <span data-ttu-id="585fc-113"><xref:System.EventHandler%601> 委托与此事件关联，示例还提供了一个自定义事件数据对象的实例。</span><span class="sxs-lookup"><span data-stu-id="585fc-113">The <xref:System.EventHandler%601> delegate is associated with the event, and an instance of a custom event data object is provided.</span></span>  
  
 [!code-cpp[EventsOverview#6](../../../samples/snippets/cpp/VS_Snippets_CLR/eventsoverview/cpp/programwithdata.cpp#6)]
 [!code-csharp[EventsOverview#6](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdata.cs#6)]
 [!code-vb[EventsOverview#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdata.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="585fc-114">示例</span><span class="sxs-lookup"><span data-stu-id="585fc-114">Example</span></span>  
 <span data-ttu-id="585fc-115">下一个示例演示如何声明事件的委托。</span><span class="sxs-lookup"><span data-stu-id="585fc-115">The next example shows how to declare a delegate for an event.</span></span> <span data-ttu-id="585fc-116">该委托名为 `ThresholdReachedEventHandler`。</span><span class="sxs-lookup"><span data-stu-id="585fc-116">The delegate is named `ThresholdReachedEventHandler`.</span></span> <span data-ttu-id="585fc-117">这只是一个示例。</span><span class="sxs-lookup"><span data-stu-id="585fc-117">This is just an illustration.</span></span> <span data-ttu-id="585fc-118">通常不需要为事件声名委托，因为可以使用 <xref:System.EventHandler> 或者 <xref:System.EventHandler%601> 委托。</span><span class="sxs-lookup"><span data-stu-id="585fc-118">Typically, you do not have to declare a delegate for an event, because you can use either the <xref:System.EventHandler> or the <xref:System.EventHandler%601> delegate.</span></span> <span data-ttu-id="585fc-119">只有在极少数情况下才应声明委托，例如，在向无法使用泛型的旧代码提供类时，就需要如此。</span><span class="sxs-lookup"><span data-stu-id="585fc-119">You should declare a delegate only in rare scenarios, such as making your class available to legacy code that cannot use generics.</span></span>  
  
 [!code-csharp[EventsOverview#7](../../../samples/snippets/csharp/VS_Snippets_CLR/eventsoverview/cs/programwithdelegate.cs#7)]
 [!code-vb[EventsOverview#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/eventsoverview/vb/module1withdelegate.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="585fc-120">另请参阅</span><span class="sxs-lookup"><span data-stu-id="585fc-120">See also</span></span>

- [<span data-ttu-id="585fc-121">事件</span><span class="sxs-lookup"><span data-stu-id="585fc-121">Events</span></span>](index.md)
