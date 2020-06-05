---
title: 如何：声明自定义事件以节省内存
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: c9a049d3f15d5620152f064888a97bd0be5d46b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405126"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="a9e78-102">如何：声明自定义事件以节省内存 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9e78-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="a9e78-103">在以下几种情况下，应用程序很重要的是应用程序保持其内存使用率较低。</span><span class="sxs-lookup"><span data-stu-id="a9e78-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="a9e78-104">自定义事件允许应用程序仅对它处理的事件使用内存。</span><span class="sxs-lookup"><span data-stu-id="a9e78-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="a9e78-105">默认情况下，当类声明事件时，编译器会为字段分配内存以存储事件信息。</span><span class="sxs-lookup"><span data-stu-id="a9e78-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="a9e78-106">如果某个类有许多未使用的事件，则它们将不必要地占用内存。</span><span class="sxs-lookup"><span data-stu-id="a9e78-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="a9e78-107">您可以使用自定义事件来更仔细地管理内存使用情况，而不是使用 Visual Basic 提供的事件的默认实现。</span><span class="sxs-lookup"><span data-stu-id="a9e78-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e78-108">示例</span><span class="sxs-lookup"><span data-stu-id="a9e78-108">Example</span></span>  
 <span data-ttu-id="a9e78-109">在此示例中，类使用 <xref:System.ComponentModel.EventHandlerList> 存储在字段中的类的一个实例 `Events` 存储有关正在使用的事件的信息。</span><span class="sxs-lookup"><span data-stu-id="a9e78-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="a9e78-110"><xref:System.ComponentModel.EventHandlerList>类是用于保存委托的优化列表类。</span><span class="sxs-lookup"><span data-stu-id="a9e78-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="a9e78-111">类中的所有事件使用 `Events` 字段跟踪处理每个事件的方法。</span><span class="sxs-lookup"><span data-stu-id="a9e78-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e78-112">请参阅</span><span class="sxs-lookup"><span data-stu-id="a9e78-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="a9e78-113">事件</span><span class="sxs-lookup"><span data-stu-id="a9e78-113">Events</span></span>](index.md)
- [<span data-ttu-id="a9e78-114">如何：声明自定义事件以避免阻止</span><span class="sxs-lookup"><span data-stu-id="a9e78-114">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
