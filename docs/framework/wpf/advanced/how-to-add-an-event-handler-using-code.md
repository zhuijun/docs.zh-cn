---
title: 如何：使用代码添加事件处理程序
description: 使用此示例来了解如何使用代码将事件处理程序添加到 Windows Presentation Foundation 中的元素，而不是使用 XAML 来声明它。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- event handlers [WPF], adding
- XAML [WPF], adding event handlers
ms.assetid: 269c61e0-6bd9-4291-9bed-1c5ee66da486
ms.openlocfilehash: b36969f7a65ccbf6c9d03b22767d9eacdc177ad1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166371"
---
# <a name="how-to-add-an-event-handler-using-code"></a><span data-ttu-id="ce364-103">如何：使用代码添加事件处理程序</span><span class="sxs-lookup"><span data-stu-id="ce364-103">How to: Add an Event Handler Using Code</span></span>
<span data-ttu-id="ce364-104">此示例演示如何使用代码将事件处理程序添加到元素。</span><span class="sxs-lookup"><span data-stu-id="ce364-104">This example shows how to add an event handler to an element by using code.</span></span>  
  
 <span data-ttu-id="ce364-105">如果要向元素添加一个事件处理程序 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，并且已加载包含该元素的标记页，则必须使用代码添加该处理程序。</span><span class="sxs-lookup"><span data-stu-id="ce364-105">If you want to add an event handler to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] element, and the markup page that contains the element has already been loaded, you must add the handler using code.</span></span> <span data-ttu-id="ce364-106">或者，如果您正在使用代码完全构建应用程序的元素树，而不使用声明任何元素 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，则可以调用特定的方法将事件处理程序添加到构造的元素树中。</span><span class="sxs-lookup"><span data-stu-id="ce364-106">Alternatively, if you are building up the element tree for an application entirely using code and not declaring any elements using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can call specific methods to add event handlers to the constructed element tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce364-107">示例</span><span class="sxs-lookup"><span data-stu-id="ce364-107">Example</span></span>  
 <span data-ttu-id="ce364-108">下面的示例将新的添加 <xref:System.Windows.Controls.Button> 到最初在中定义的现有页 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ce364-108">The following example adds a new <xref:System.Windows.Controls.Button> to an existing page that is initially defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="ce364-109">代码隐藏文件实现事件处理程序方法，然后将该方法作为的新事件处理程序添加到中 <xref:System.Windows.Controls.Button> 。</span><span class="sxs-lookup"><span data-stu-id="ce364-109">A code-behind file implements an event handler method and then adds that method as a new event handler on the <xref:System.Windows.Controls.Button>.</span></span>  
  
 <span data-ttu-id="ce364-110">C # 示例使用 `+=` 运算符为事件分配处理程序。</span><span class="sxs-lookup"><span data-stu-id="ce364-110">The C# example uses the `+=` operator to assign a handler to an event.</span></span> <span data-ttu-id="ce364-111">这是用于在公共语言运行时（CLR）事件处理模型中分配处理程序的同一运算符。</span><span class="sxs-lookup"><span data-stu-id="ce364-111">This is the same operator that is used to assign a handler in the common language runtime (CLR) event handling model.</span></span> <span data-ttu-id="ce364-112">Microsoft Visual Basic 不支持将此运算符作为添加事件处理程序的方法。</span><span class="sxs-lookup"><span data-stu-id="ce364-112">Microsoft Visual Basic does not support this operator as a means of adding event handlers.</span></span> <span data-ttu-id="ce364-113">而是需要以下两种方法之一：</span><span class="sxs-lookup"><span data-stu-id="ce364-113">It instead requires one of two techniques:</span></span>  
  
- <span data-ttu-id="ce364-114">结合使用 <xref:System.Windows.UIElement.AddHandler%2A> 方法和 `AddressOf` 运算符来引用事件处理程序实现。</span><span class="sxs-lookup"><span data-stu-id="ce364-114">Use the <xref:System.Windows.UIElement.AddHandler%2A> method, together with an `AddressOf` operator, to reference the event handler implementation.</span></span>  
  
- <span data-ttu-id="ce364-115">在 `Handles` 事件处理程序定义中使用关键字。</span><span class="sxs-lookup"><span data-stu-id="ce364-115">Use the `Handles` keyword as part of the event handler definition.</span></span> <span data-ttu-id="ce364-116">此处未显示此方法;请参阅[Visual Basic 和 WPF 事件处理](visual-basic-and-wpf-event-handling.md)。</span><span class="sxs-lookup"><span data-stu-id="ce364-116">This technique is not shown here; see [Visual Basic and WPF Event Handling](visual-basic-and-wpf-event-handling.md).</span></span>  
  
 [!code-xaml[RoutedEventAddRemoveHandler#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventAddRemoveHandler#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventAddRemoveHandler/VisualBasic/default.xaml.vb#handler)]  
  
> [!NOTE]
> <span data-ttu-id="ce364-117">在初始分析页中添加事件处理程序 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 要简单得多。</span><span class="sxs-lookup"><span data-stu-id="ce364-117">Adding an event handler in the initially parsed [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page is much simpler.</span></span> <span data-ttu-id="ce364-118">在要添加事件处理程序的对象元素中，添加一个与你要处理的事件的名称相匹配的属性。</span><span class="sxs-lookup"><span data-stu-id="ce364-118">Within the object element where you want to add the event handler, add an attribute that matches the name of the event that you want to handle.</span></span> <span data-ttu-id="ce364-119">然后，将该属性的值指定为在该页的代码隐藏文件中定义的事件处理程序方法的名称 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="ce364-119">Then specify the value of that attribute as the name of the event handler method that you defined in the code-behind file of the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] page.</span></span> <span data-ttu-id="ce364-120">有关详细信息，请参阅[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)或[路由事件概述](routed-events-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ce364-120">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md) or [Routed Events Overview](routed-events-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce364-121">另请参阅</span><span class="sxs-lookup"><span data-stu-id="ce364-121">See also</span></span>

- [<span data-ttu-id="ce364-122">路由事件概述</span><span class="sxs-lookup"><span data-stu-id="ce364-122">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="ce364-123">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="ce364-123">How-to Topics</span></span>](events-how-to-topics.md)
