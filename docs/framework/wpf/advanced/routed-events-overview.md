---
title: 路由事件概述
description: 了解 Windows Presentation Foundation 中的路由事件，包括如何通过元素树路由事件以及如何创建自定义路由事件。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached events [WPF]
- grouped button set [WPF]
- routed events [WPF]
- events [WPF], routed
- tunneling [WPF]
- events [WPF], attached
- routing strategies for events [WPF]
- button set [WPF], grouped
- bubbling [WPF]
ms.assetid: 1a2189ae-13b4-45b0-b12c-8de2e49c29d2
ms.openlocfilehash: d18b511a4886c68922cccac14942eb54e5735a71
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164805"
---
# <a name="routed-events-overview"></a>路由事件概述

本主题描述 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中路由事件的概念。 本主题定义路由事件术语、描述路由事件如何通过元素树来路由、概述如何处理路由事件，并介绍如何创建你自己的自定义路由事件。

<a name="prerequisites"></a>

## <a name="prerequisites"></a>先决条件

本主题假定您具有公共语言运行时（CLR）和面向对象的编程的基本知识，以及如何将元素之间的关系概念 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 化为树的概念。 若要理解本主题中的示例，你还应当了解 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 并知道如何编写非常基本的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序或页。 有关详细信息，请参阅[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)和[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。

<a name="routing"></a>

## <a name="what-is-a-routed-event"></a>什么是路由事件？

可以从功能或实现的角度来理解路由事件。 此处对这两种定义均进行了说明，因为有的用户认为前者更有用，有的用户认为后者更有用。

功能定义：路由事件是一种可以针对元素树中的多个侦听器（而不是仅针对引发该事件的对象）调用处理程序的事件。

实现定义：路由事件是由类的实例支持的 CLR 事件，由 <xref:System.Windows.RoutedEvent> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 事件系统进行处理。

典型的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 应用程序中包含许多元素。 无论这些元素是在代码中创建还是在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中声明，它们存在于彼此关联的元素树关系中。 根据事件的定义，事件路由可以按两种方向之一传播，但是通常会在元素树中从源元素向上“浮升”，直到它到达元素树的根（通常是页面或窗口）。 如果你以前用过 DHTML 对象模型，则可能会熟悉这个浮升概念。

请思考下面的简单元素树：

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

此元素树生成类似如下的内容：

!["是"、"否" 和 "取消" 按钮](./media/routedevent-ovw-1.gif "RoutedEvent_ovw_1")

在这个简化的元素树中，事件的源 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 是一个 <xref:System.Windows.Controls.Button> 元素，而 <xref:System.Windows.Controls.Button> 单击的是有机会处理事件的第一个元素。 但如果附加到的处理程序对 <xref:System.Windows.Controls.Button> 事件不起作用，则该事件将向上冒泡到 <xref:System.Windows.Controls.Button> 元素树中的父级（即） <xref:System.Windows.Controls.StackPanel> 。 事件可能会冒泡到 <xref:System.Windows.Controls.Border> ，然后再冒泡到元素树的页根（未显示）。

换句话说，此事件的事件路由 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 是：

Button-->StackPanel-->Border-->...

### <a name="top-level-scenarios-for-routed-events"></a>路由事件的顶级方案

下面简要概述了引发路由事件的方案，以及为什么典型的 CLR 事件对于这些方案来说是不够的：

**控件的撰写和封装：**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的各个控件都有一个丰富的内容模型。 例如，可以将图像置于内 <xref:System.Windows.Controls.Button> ，这会有效地扩展按钮的可视化树。 但是，添加的图像不得中断导致按钮响应 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 其内容的命中测试行为，即使用户单击了在技术上包含图像的部分像素也是如此。

**单一处理程序附件点：** 在 Windows 窗体中，你必须多次附加相同的处理程序，以处理可能会从多个元素引发的事件。 借助路由事件，可以只附加该处理程序一次（如上例中所示），并在必要时使用处理程序逻辑来确定该事件的源位置。 例如，这可以是前面显示的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的处理程序：

[!code-csharp[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#groupbuttoncodebehind)]
[!code-vb[EventOvwSupport#GroupButtonCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#groupbuttoncodebehind)]

**类处理：** 路由事件允许使用由类定义的静态处理程序。 此类处理程序能够抢在任何附加的实例处理程序之前处理事件。

**引用事件，而不反射：** 某些代码和标记技术需要能标识特定事件的方法。 路由事件将 <xref:System.Windows.RoutedEvent> 字段作为标识符创建，这提供了一种可靠的事件标识技术，不需要静态或运行时反射。

### <a name="how-routed-events-are-implemented"></a>路由事件的实现方式

路由事件是由类的实例提供支持 <xref:System.Windows.RoutedEvent> 并向事件系统注册的 CLR 事件 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 <xref:System.Windows.RoutedEvent>从注册获得的实例通常作为 `public` `static` `readonly` 类的字段成员保留，此类成员注册并因此 "拥有" 路由事件。 与名称相同的 CLR 事件（有时称为 "包装" 事件）的连接是通过重写 `add` CLR 事件的和实现来完成的 `remove` 。 通常，`add` 和 `remove` 保留为隐式默认值，该默认值使用特定于语言的相应事件语法来添加和删除该事件的处理程序。 路由事件支持和连接机制在概念上类似于依赖属性是由 <xref:System.Windows.DependencyProperty> 类支持并向属性系统注册的 CLR 属性 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。

下面的示例演示自定义 `Tap` 路由事件的声明，其中包括标识符字段的注册和公开以及 <xref:System.Windows.RoutedEvent> `add` CLR 事件的和 `remove` 实现 `Tap` 。

[!code-csharp[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#addremovehandler)]
[!code-vb[RoutedEventCustom#AddRemoveHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#addremovehandler)]

### <a name="routed-event-handlers-and-xaml"></a>路由事件处理程序和 XAML

若要使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 为事件添加处理程序，可将该事件的名称声明为用作事件侦听器的元素的属性。 该属性的值是所实现的处理程序方法的名称，该方法必须存在于代码隐藏文件的分部类中。

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]添加路由事件处理程序的语法与添加路由事件处理程序的语法相同，因为您实际上是将处理程序添加到 CLR 事件包装器，后者在下面具有路由事件实现。 有关在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中添加事件处理程序的详细信息，请参阅 [XAML 概述 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)。

<a name="routing_strategies"></a>

## <a name="routing-strategies"></a>路由策略

路由事件使用以下三种路由策略之一：

- **浮升：** 调用事件源上的事件处理程序。 路由事件随后会路由到后续的父级元素，直到到达元素树的根。 大多数路由事件都使用浮升路由策略。 浮升路由事件通常用于报告来自不同控件或其他 UI 元素的输入或状态变化。

- **直接：** 只有源元素本身才有机会调用处理程序以进行响应。 这类似于 Windows 窗体用于事件的 "路由"。 但是，与标准 CLR 事件不同，直接路由事件支持类处理（在下一节中介绍类处理），并可由 <xref:System.Windows.EventSetter> 和使用 <xref:System.Windows.EventTrigger> 。

- **隧道：** 最初将调用元素树的根处的事件处理程序。 随后，路由事件将朝着路由事件的源节点元素（即引发路由事件的元素）方向，沿路由线路传播到后续的子元素。 合成控件的过程中通常会使用或处理隧道路由事件，通过这种方式，可以有意地禁止复合部件中的事件，或者将其替换为特定于整个控件的事件。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中提供的输入事件通常是以隧道/浮升对实现的。 隧道事件有时又称作预览事件，这是由该对所使用的命名约定决定的。

<a name="why_use"></a>

## <a name="why-use-routed-events"></a>为什么使用路由事件？

作为应用程序开发人员，你不需要始终了解或关注要处理的事件是否作为路由事件实现。 路由事件具有特殊的行为，但是，如果在引发该行为的元素上处理事件，则该行为通常会不可见。

如果使用以下任一建议方案，路由事件的功能将得到充分发挥：在公用根处定义公用处理程序、合成自己的控件或者定义自己的自定义控件类。

路由事件侦听器和路由事件源不必在其层次结构中共享公用事件。 Any <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 可以是任何路由事件的事件侦听器。 因此，可以将整个工作 API 集中可用的完整路由事件集用作概念 "接口"，应用程序中的不同元素可以交换事件信息。 路由事件的这个“接口”概念特别适用于输入事件。

路由事件还可以用于通过元素树进行通信，因为事件的事件数据会保留到路由中的每个元素中。 一个元素可以更改事件数据中的某些内容，该更改将用于路由中的下一个元素。

除了路由方面以外，还有两个原因，任何给定事件都 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 可能作为路由事件实现，而不是作为标准 CLR 事件实现。 如果要实现自己的事件，则可能也需要考虑这些原则：

- 某些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 样式和模板化功能（如 <xref:System.Windows.EventSetter> 和） <xref:System.Windows.EventTrigger> 要求引用的事件是路由事件。 前面提到的事件标识符方案就是这样的。

- 路由事件支持类处理机制，类可以通过该机制来指定静态方法，这些静态方法能够在任何已注册的实例处理程序访问路由事件之前，处理这些路由事件。 这在控件设计中非常有用，因为类可以强制执行事件驱动的类行为，以防它们在处理实例上的事件时被意外禁止。

本主题将用单独的章节来讨论上述每个因素。

<a name="event_handing"></a>

## <a name="adding-and-implementing-an-event-handler-for-a-routed-event"></a>为路由事件添加和实现事件处理程序

若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中添加事件处理程序，只需将事件名称作为属性添加到元素中，并将属性值设置为用来实现相应委托的事件处理程序的名称，如下面的示例中所示。

[!code-xaml[EventOvwSupport#SimplestSyntax](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#simplestsyntax)]

`b1SetColor`是所实现的处理程序的名称，其中包含处理事件的代码 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 。 `b1SetColor`必须具有与委托相同的签名 <xref:System.Windows.RoutedEventHandler> ，这是事件的事件处理程序委托 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 。 所有路由事件处理程序委托的第一个参数都指定要向其中添加事件处理程序的元素，第二个参数指定事件的数据。

[!code-csharp[EventOvwSupport#SimpleHandlerA](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#simplehandlera)]
[!code-vb[EventOvwSupport#SimpleHandlerA](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#simplehandlera)]

<xref:System.Windows.RoutedEventHandler>基本路由事件处理程序委托。 对于针对某些控件或方案的专用路由事件，要用于路由事件处理程序的委托还可能会变得更加专用化，以便可以传输专用的事件数据。 例如，在常见的输入方案中，可以处理 <xref:System.Windows.UIElement.DragEnter> 路由事件。 处理程序应实现 <xref:System.Windows.DragEventHandler> 委托。 使用最具体的委托，可以 <xref:System.Windows.DragEventArgs> 在处理程序中处理，并读取 <xref:System.Windows.DragEventArgs.Data%2A> 属性，其中包含拖动操作的剪贴板有效负载。

有关如何使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 向元素中添加事件处理程序的完整示例，请参阅[处理路由事件](how-to-handle-a-routed-event.md)。

在用代码创建的应用程序中为路由事件添加处理程序非常简单。 路由事件处理程序始终可以通过 helper 方法添加 <xref:System.Windows.UIElement.AddHandler%2A> （与现有的支持调用相同的方法 `add` ）。但是，现有 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 路由事件通常具有 `add` 和逻辑的后备实现， `remove` 这些实现允许路由事件的处理程序通过特定于语言的事件语法来添加，该语法比 helper 方法更直观。 下面是 Helper 方法的示例用法：

[!code-csharp[EventOvwSupport#AddHandlerCode](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlercode)]
[!code-vb[EventOvwSupport#AddHandlerCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlercode)]

下一个示例演示了 c # 运算符语法（Visual Basic 的运算符语法略有不同，因为它处理取消引用）：

[!code-csharp[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml.cs#addhandlerplusequals)]
[!code-vb[EventOvwSupport#AddHandlerPlusEquals](~/samples/snippets/visualbasic/VS_Snippets_Wpf/EventOvwSupport/visualbasic/default.xaml.vb#addhandlerplusequals)]

有关如何在代码中添加事件处理程序的示例，请参阅[使用代码添加事件处理程序](how-to-add-an-event-handler-using-code.md)。

如果使用 Visual Basic，则还可以使用 `Handles` 关键字将处理程序添加为处理程序声明的一部分。 有关详细信息，请参阅 [Visual Basic 和 WPF 事件处理](visual-basic-and-wpf-event-handling.md)。

<a name="concept_handled"></a>

### <a name="the-concept-of-handled"></a>“已处理”概念

所有路由事件都共享一个公用事件数据基类 <xref:System.Windows.RoutedEventArgs> 。 <xref:System.Windows.RoutedEventArgs>定义 <xref:System.Windows.RoutedEventArgs.Handled%2A> 属性，该属性采用布尔值。 属性的目的 <xref:System.Windows.RoutedEventArgs.Handled%2A> 是使任何事件处理程序沿路由，将路由事件标记为已*处理*，方法是将的值设置 <xref:System.Windows.RoutedEventArgs.Handled%2A> 为 `true` 。 处理程序在路由上的某个元素处对共享事件数据进行处理之后，这些数据将再次报告给路由上的每个侦听器。

的值 <xref:System.Windows.RoutedEventArgs.Handled%2A> 影响路由事件在沿路由进一步传播时的报告或处理方式。 如果 <xref:System.Windows.RoutedEventArgs.Handled%2A> 是 `true` 路由事件的事件数据中的，则通常不会再为该特定事件实例调用在其他元素上侦听该路由事件的处理程序。 这条规则对以下两类处理程序均适用：在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中附加的处理程序；由特定于语言的事件处理程序附加语法（如 `+=` 或 `Handles`）添加的处理程序。 对于大多数常见的处理程序方案，通过将设置为来将事件标记为已处理， <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` 将 "停止" 路由用于隧道路由或冒泡路由，还用于通过类处理程序在路由中的某个点处理的任何事件。

但是，有一个 "handledEventsToo" 机制，侦听器仍可以运行处理程序来响应 <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` 事件数据中的路由事件。 换言之，将事件数据标记为“已处理”并不会真的停止事件路由。 只能在代码中或在中使用 handledEventsToo 机制 <xref:System.Windows.EventSetter> ：

- 在代码中，请调用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 方法添加处理程序，而不是使用适用于常规 CLR 事件的特定于语言的事件语法 <xref:System.Windows.UIElement.AddHandler%28System.Windows.RoutedEvent%2CSystem.Delegate%2CSystem.Boolean%29> 。 请将 `handledEventsToo` 的值指定为 `true`。

- 在中 <xref:System.Windows.EventSetter> ，将 <xref:System.Windows.EventSetter.HandledEventsToo%2A> 特性设置为 `true` 。

除了 <xref:System.Windows.RoutedEventArgs.Handled%2A> 状态在路由事件中生成的行为外，的概念 <xref:System.Windows.RoutedEventArgs.Handled%2A> 还影响了应如何设计应用程序并编写事件处理程序代码。 您可以将概念化为 <xref:System.Windows.RoutedEventArgs.Handled%2A> 由路由事件公开的简单协议。 你确切地了解如何使用此协议，但如何使用的值的概念设计 <xref:System.Windows.RoutedEventArgs.Handled%2A> 如下：

- 如果路由事件标记为“已处理”，则它不必由该路由中的其他元素再次处理。

- 如果路由事件未标记为已处理，则之前沿路由的其他侦听器选择不注册处理程序，或已注册的处理程序选择不操作事件数据并将设置 <xref:System.Windows.RoutedEventArgs.Handled%2A> 为 `true` 。 （或者，可能当前侦听器是路由中的第一个点。）当前侦听器上的处理程序现在有三个可能的操作课程：

  - 不执行任何操作；该事件保持未处理状态，该事件将路由到下一个侦听器。

  - 执行代码以响应该事件，但是所执行的操作被视为不足以保证将事件标记为“已处理”。 该事件将路由到下一个侦听器。

  - 执行代码以响应该事件。 在传递到处理程序的事件数据中将该事件标记为“已处理”，因为所执行的操作被视为不足以保证将该事件标记为“已处理”。 该事件仍将路由到下一个侦听器，但 <xref:System.Windows.RoutedEventArgs.Handled%2A> = `true` 在其事件数据中，只有 `handledEventsToo` 侦听器才能调用进一步的处理程序。

此概念设计由前面提到的路由行为加强：更难（尽管代码或样式中仍有可能）附加处理路由事件的处理程序，即使路由上的以前处理程序已设置为也是如此 <xref:System.Windows.RoutedEventArgs.Handled%2A> `true` 。

有关 <xref:System.Windows.RoutedEventArgs.Handled%2A> 路由事件的类处理的详细信息，以及有关何时适当地将路由事件标记为的建议， <xref:System.Windows.RoutedEventArgs.Handled%2A> 请参阅将[路由事件标记为已处理和类处理](marking-routed-events-as-handled-and-class-handling.md)。

在应用程序中，相当常见的做法是只针对引发浮升路由事件的对象来处理该事件，而根本不考虑事件的路由特征。 但是，在事件数据中将路由事件标记为“已处理”仍是一个不错的做法，因为这样可以防止元素树中位置更高的元素也对同一个路由事件附加了处理程序而出现意外的副作用。

<a name="class_handlers"></a>

## <a name="class-handlers"></a>类处理程序

如果要定义从中派生的类 <xref:System.Windows.DependencyObject> ，则还可以为作为类的声明或继承的事件成员的路由事件定义和附加类处理程序。 每当路由事件到达其路由中的元素实例时，都会先调用类处理程序，然后再调用附加到该类某个实例的任何实例侦听器处理程序。

有些 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 控件对某些路由事件具有固有的类处理。 路由事件可能看起来从未引发过，但实际上正对其进行类处理，如果使用某些技术，路由事件还是可以由实例处理程序进行处理。 此外，许多基类和控件会公开可用来替代类处理行为的虚拟方法。 若要深入了解如何解决不需要的类处理以及如何在自定义类中定义自己的类处理，请参阅[将路由事件标记为“已处理”和类处理](marking-routed-events-as-handled-and-class-handling.md)。

<a name="attached_events"></a>

## <a name="attached-events-in-wpf"></a>WPF 中的附加事件

[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 语言还定义了一个名为附加事件的特殊类型的事件。** 使用附加事件，可以将特定事件的处理程序添加到任意元素中。 处理事件的元素不必定义或继承附加事件，可能引发事件的对象和用来处理实例的目标也都不必将该事件定义为类成员，或将其作为类成员来“拥有”。

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 输入系统广泛使用附加事件。 但是，几乎所有的附加事件都是通过基本元素转发的。 输入事件随后会显示为作为基本元素类成员的等效非附加路由事件。 例如， <xref:System.Windows.Input.Mouse.MouseDown?displayProperty=nameWithType> 可以通过使用来更轻松地处理基础附加事件， <xref:System.Windows.UIElement> <xref:System.Windows.UIElement.MouseDown> <xref:System.Windows.UIElement> 而不是在或代码中处理附加事件语法 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。

有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中附加事件的详细信息，请参阅[附加事件概述](attached-events-overview.md)。

<a name="Qualifying_Event_Names_in_XAML_for_Anticipated_Routing"></a>

## <a name="qualified-event-names-in-xaml"></a>XAML 中的限定事件名称

为子元素所引发的路由事件附加处理程序是另一个语法用法，它与 typename.eventname 附加事件语法相似，但它并非严格意义上的附加事件用法。**** 可以向公用父级附加处理程序以利用事件路由，即使公用父级可能没有作为成员的相关路由事件，也是如此。 请再次思考下面的示例：

[!code-xaml[EventOvwSupport#GroupButton](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/default.xaml#groupbutton)]

此处，添加处理程序的父元素侦听器是 <xref:System.Windows.Controls.StackPanel> 。 但是，它将为已声明的路由事件添加处理程序，并将由 <xref:System.Windows.Controls.Button> 类引发（ <xref:System.Windows.Controls.Primitives.ButtonBase> 实际上，但可 <xref:System.Windows.Controls.Button> 通过继承实现）。 <xref:System.Windows.Controls.Button>"拥有" 事件，但路由事件系统允许任何路由事件的处理程序连接到任何 <xref:System.Windows.UIElement> 或 <xref:System.Windows.ContentElement> 实例侦听器，这些侦听器可能会为公共语言运行时（CLR）事件附加侦听器。 对于这些限定的事件特性名来说，默认的 xmlns 命名空间通常是默认的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] xmlns 命名空间，但是还可以为自定义路由事件指定带有前缀的命名空间。 有关 xmlns 的详细信息，请参阅 [WPF XAML 的 XAML 命名空间和命名空间映射](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)。

<a name="how_event_processing_works"></a>

## <a name="wpf-input-events"></a>WPF 输入事件

路由事件在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 平台中的常见应用之一是用于事件输入。 在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，按照约定，隧道路由事件的名称以单词“Preview”开头。 输入事件通常成对出现，一个是浮升事件，另一个是隧道事件。 例如， <xref:System.Windows.ContentElement.KeyDown> 事件和 <xref:System.Windows.ContentElement.PreviewKeyDown> 事件具有相同的签名，前者是冒泡输入事件，后者是隧道输入事件。 偶尔，输入事件只有浮升版本，或者有可能只有直接路由版本。 在文档中，路由事件主题交叉引用具有备用路由策略的类似路由事件（如果存在这类路由事件），托管的引用页面中的相关部分阐明每个路由事件的路由策略。

实现成对出现的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 输入事件，使来自输入的单个用户操作（如按鼠标按钮）按顺序引发该对中的两个路由事件。 首先引发隧道事件并沿路由传播。 然后引发浮升事件并沿路由传播。 这两个事件以字面方式共享相同的事件数据实例，因为 <xref:System.Windows.UIElement.RaiseEvent%2A> 引发冒泡事件的实现类中的方法调用会侦听隧道事件中的事件数据，并在新引发的事件中重用它。 具有隧道事件处理程序的侦听器首先获得将路由事件标记为“已处理”的机会（首先是类处理程序，然后是实例处理程序）。 如果隧道路由中的某个元素将路由事件标记为“已处理”，则会针对浮升事件发送已处理的事件数据，而且将不调用等效的浮升输入事件的附加典型处理程序。 已处理的浮升事件看起来好像尚未引发。 此处理行为对于控件合成非常有用，因为在此情况下你可能希望所有基于命中测试的输入事件或者所有基于焦点的输入事件都由最终的控件（而不是它的复合部件）报告。 作为可支持控件类的代码的一部分，最后一个控件元素靠近合成中的根，因此将有机会首先对隧道事件进行类处理，或者有机会将该路由事件“替换”为更针对控件的事件。

为了说明输入事件处理的工作方式，请思考下面的输入事件示例。 在下面的树插图中， `leaf element #2` 是和事件的源 `PreviewMouseDown` `MouseDown` ：

![事件路由示意图](./media/routed-events-overview/input-event-routing.png)

事件的处理顺序如下所述：

1. 针对根元素处理 `PreviewMouseDown`（隧道）。

2. 针对中间元素 #1 处理 `PreviewMouseDown`（隧道）。

3. 针对源元素 #2 处理 `PreviewMouseDown`（隧道）。

4. 针对源元素 #2 处理 `MouseDown`（浮升）。

5. 针对中间元素 #1 处理 `MouseDown`（浮升）。

6. 针对根元素处理 `MouseDown`（浮升）。

路由事件处理程序委托提供对以下两个对象的引用：引发该事件的对象以及在其中调用处理程序的对象。 在其中调用处理程序的对象是由 `sender` 参数报告的对象。 事件数据中的属性报告第一次引发事件的对象 <xref:System.Windows.RoutedEventArgs.Source%2A> 。 路由事件仍可由相同的对象引发和处理，在这种情况下， `sender` 和 <xref:System.Windows.RoutedEventArgs.Source%2A> 是相同的（事件处理示例列表中的步骤3和4就是这种情况）。

由于隧道和冒泡，父元素会接收输入事件，其中， <xref:System.Windows.RoutedEventArgs.Source%2A> 是其子元素之一。 如果知道源元素是什么，则可以通过访问属性来标识源元素 <xref:System.Windows.RoutedEventArgs.Source%2A> 。

通常，在标记输入事件后 <xref:System.Windows.RoutedEventArgs.Handled%2A> ，不会调用进一步的处理程序。 通常，一旦调用了用来对输入事件的含义进行特定于应用程序的逻辑处理的处理程序，就应当将输入事件标记为“已处理”。

这种关于状态的常规语句的例外 <xref:System.Windows.RoutedEventArgs.Handled%2A> 情况是：注册到特意忽略 <xref:System.Windows.RoutedEventArgs.Handled%2A> 事件数据状态的输入事件处理程序仍将在任一路由上调用。 有关详细信息，请参阅[预览事件](preview-events.md)或[将路由事件标记为“已处理”和类处理](marking-routed-events-as-handled-and-class-handling.md)。

通常，隧道事件和浮升事件之间的共享事件数据模型以及先引发隧道事件后引发浮升事件的顺序引发并非适用于所有的路由事件的概念。 该行为的实现取决于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 输入设备选择引发和连接输入事件对的具体方式。 实现你自己的输入事件是一个高级方案，但是你也可以选择针对自己的输入事件遵循该模型。

一些类选择对某些输入事件进行类处理，其目的通常是重新定义用户驱动的特定输入事件在该控件中的含义并引发新事件。 有关详细信息，请参阅[将路由事件标记为“已处理”和类处理](marking-routed-events-as-handled-and-class-handling.md)。

有关输入以及在典型的应用程序方案中输入和事件如何交互的详细信息，请参阅[输入概述](input-overview.md)。

<a name="events_styles"></a>

## <a name="eventsetters-and-eventtriggers"></a>EventSetter 和 EventTrigger

在样式中，可以通过使用在标记中包含一些预声明 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 的事件处理语法 <xref:System.Windows.EventSetter> 。 在应用样式时，所引用的处理程序会添加到带样式的实例中。 只能 <xref:System.Windows.EventSetter> 为路由事件声明。 下面是一个示例。 请注意，此处引用的 `b1SetColor` 方法位于代码隐藏文件中。

[!code-xaml[EventOvwSupport#XAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/EventOvwSupport/CSharp/page2.xaml#xaml2)]

这里获得的优势在于，样式可能包含大量其他可应用于应用程序中任何按钮的信息，并且， <xref:System.Windows.EventSetter> 将作为该样式的一部分，即使在标记级别也是如此。 此外， <xref:System.Windows.EventSetter> 抽象方法会从一般的应用程序和页标记中进一步进一步命名处理程序。

合并的路由事件和动画功能的另一个专用语法 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 是 <xref:System.Windows.EventTrigger> 。 与一样 <xref:System.Windows.EventSetter> ，仅路由事件可用于 <xref:System.Windows.EventTrigger> 。 通常， <xref:System.Windows.EventTrigger> 将声明为样式的一部分，但是 <xref:System.Windows.EventTrigger> 也可以在页级元素上声明为集合的一部分 <xref:System.Windows.FrameworkElement.Triggers%2A> ，或者在中声明 <xref:System.Windows.Controls.ControlTemplate> 。 <xref:System.Windows.EventTrigger>利用，您可以指定一个 <xref:System.Windows.Media.Animation.Storyboard> 每当路由事件在其路由中到达为该事件声明的元素时运行的 <xref:System.Windows.EventTrigger> 。 <xref:System.Windows.EventTrigger>除了处理事件并导致其启动现有情节提要外，的优点是 <xref:System.Windows.EventTrigger> 可以更好地控制情节提要及其运行时行为。 有关详细信息，请参阅[在情节提要启动之后使用事件触发器来控制情节提要](../graphics-multimedia/how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)。

<a name="more_about"></a>

## <a name="more-about-routed-events"></a>有关路由事件的更多信息

本主题主要从以下角度讨论路由事件：描述基本概念；就如何以及何时响应各种基元素和控件中已经存在的路由事件提供指南。 但是，你可以在自定义类上创建自己的路由事件以及所有必要的支持（如专用的事件数据类和委托）。 路由事件所有者可以是任何类，但路由事件必须由或派生类引发和处理 <xref:System.Windows.UIElement> 才能 <xref:System.Windows.ContentElement> 发挥作用。 有关自定义事件的详细信息，请参阅[创建自定义路由事件](how-to-create-a-custom-routed-event.md)。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.EventManager>
- <xref:System.Windows.RoutedEvent>
- <xref:System.Windows.RoutedEventArgs>
- [将路由事件标记为“已处理”和“类处理”](marking-routed-events-as-handled-and-class-handling.md)
- [输入概述](input-overview.md)
- [命令概述](commanding-overview.md)
- [自定义依赖项属性](custom-dependency-properties.md)
- [WPF 中的树](trees-in-wpf.md)
- [弱事件模式](weak-event-patterns.md)
