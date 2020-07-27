---
title: Layout
description: 了解 Windows Presentation Foundation 布局系统中发生布局计算的方式和时间。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 0db3f2a6cbabc610362435d64de3fc970f01a73c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164770"
---
# <a name="layout"></a>Layout

本主题介绍 Windows Presentation Foundation （WPF）布局系统。 了解布局计算的发生方式和时间是在 WPF 中创建用户界面所必需的。

本主题包含以下各节：

- [元素边界框](#LayoutSystem_BoundingBox)

- [布局系统](#LayoutSystem_Overview)

- [测量和排列子元素](#LayoutSystem_Measure_Arrange)

- [面板元素和自定义布局行为](#LayoutSystem_PanelsCustom)

- [布局性能注意事项](#LayoutSystem_Performance)

- [子像素渲染和布局舍入](#LayoutSystem_LayoutRounding)

- [后续操作](#LayoutSystem_whatsnext)

<a name="LayoutSystem_BoundingBox"></a>

## <a name="element-bounding-boxes"></a>元素边界框

在 WPF 中考虑布局时，必须了解环绕所有元素的边界框。 <xref:System.Windows.FrameworkElement>布局系统所使用的每个都可以被视为一个将其插入到布局中的矩形。 <xref:System.Windows.Controls.Primitives.LayoutInformation>类返回元素的布局分配或槽的边界。 矩形的大小通过计算可用屏幕空间、任何约束的大小、特定于布局的属性（如边距和填充）以及父元素的单个行为来确定 <xref:System.Windows.Controls.Panel> 。 处理此数据时，布局系统能够计算特定的所有子级的位置 <xref:System.Windows.Controls.Panel> 。 务必记住，在父元素上定义的大小调整特征（如 <xref:System.Windows.Controls.Border> ）会影响其子级。

下图显示了一个简单的布局。

![屏幕截图，显示一个典型网格，未叠加边界框。](./media/layout/grid-no-bounding-box-superimpose.png)

可以通过使用以下 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 实现此布局。

[!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]

单个 <xref:System.Windows.Controls.TextBlock> 元素承载于中 <xref:System.Windows.Controls.Grid> 。 尽管文本仅填充第一列的左上角，但的分配空间 <xref:System.Windows.Controls.TextBlock> 实际上更大。 <xref:System.Windows.FrameworkElement>可以使用方法检索 any 的边界框 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> 。 下图显示了元素的边界框 <xref:System.Windows.Controls.TextBlock> 。

![显示 TextBlock 边界框现在可见的屏幕截图。](./media/layout/visible-textblock-bounding-box.png)

如黄色矩形所示，为元素分配的空间 <xref:System.Windows.Controls.TextBlock> 实际上远远大于显示的空间。 随着附加元素添加到 <xref:System.Windows.Controls.Grid> ，此分配可能会缩小或展开，具体取决于所添加元素的类型和大小。

的布局槽 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Shapes.Path> 通过使用方法转换为 <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> 。 此方法可用于显示元素的边界框。

[!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
[!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]

<a name="LayoutSystem_Overview"></a>

## <a name="the-layout-system"></a>布局系统

简单地说，布局是一个递归系统，实现对元素进行大小调整、定位和绘制。 更具体地说，layout 描述了测量和排列元素集合成员的过程 <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> 。 布局是一个密集的过程。 <xref:System.Windows.Controls.Panel.Children%2A>集合越大，必须进行的计算数量就越多。 还可以根据拥有集合的元素所定义的布局行为，引入复杂性 <xref:System.Windows.Controls.Panel> 。 相对较简单的（如），其 <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Canvas> 性能明显高于更复杂的 <xref:System.Windows.Controls.Panel> ，例如 <xref:System.Windows.Controls.Grid> 。

每次子级 <xref:System.Windows.UIElement> 更改其位置时，布局系统就有可能触发一个新的传递。 因此，了解哪些事件会调用布局系统就很重要，因为不必要的调用可能导致应用程序性能变差。 下面描述调用布局系统时发生的过程。

1. 子元素 <xref:System.Windows.UIElement> 通过首先测量其核心属性来开始布局过程。

2. 计算在上定义的大小调整属性 <xref:System.Windows.FrameworkElement> ，如 <xref:System.Windows.FrameworkElement.Width%2A> 、 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Margin%2A> 。

3. <xref:System.Windows.Controls.Panel>应用特定的逻辑，如 <xref:System.Windows.Controls.Dock> 方向或堆叠 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 。

4. 测量所有子级后排列内容。

5. <xref:System.Windows.Controls.Panel.Children%2A>集合在屏幕上绘制。

6. 如果 <xref:System.Windows.Controls.Panel.Children%2A> 向集合添加了其他、 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 应用了或调用了方法，则会再次调用该过程 <xref:System.Windows.UIElement.UpdateLayout%2A> 。

以下各节更详细地定义了此过程及其调用方式。

<a name="LayoutSystem_Measure_Arrange"></a>

## <a name="measuring-and-arranging-children"></a>测量和排列子元素

布局系统为集合的每个成员完成两个传递 <xref:System.Windows.Controls.Panel.Children%2A> 、一个度量值处理和一个排列处理过程。 每个子元素都 <xref:System.Windows.Controls.Panel> 提供自己的 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 方法来实现其自己的特定布局行为。

在度量值处理过程中，将对集合中的每个成员 <xref:System.Windows.Controls.Panel.Children%2A> 进行计算。 此过程首先调用 <xref:System.Windows.UIElement.Measure%2A> 方法。 此方法在父元素的实现中调用 <xref:System.Windows.Controls.Panel> ，无需显式调用即可进行布局。

首先，计算的本机大小属性 <xref:System.Windows.UIElement> ，例如 <xref:System.Windows.UIElement.Clip%2A> 和 <xref:System.Windows.UIElement.Visibility%2A> 。 这会生成一个名为 `constraintSize` 的值，该值将传递给 <xref:System.Windows.FrameworkElement.MeasureCore%2A> 。

其次，会处理在上定义的框架属性 <xref:System.Windows.FrameworkElement> ，这会影响的值 `constraintSize` 。 这些属性通常描述基础的大小调整特征 <xref:System.Windows.UIElement> ，例如，、、 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.Style%2A> 。 其中每个属性都可以更改显示元素所需的空间。 <xref:System.Windows.FrameworkElement.MeasureOverride%2A>然后，将 `constraintSize` 作为参数调用。

> [!NOTE]
> 和和的属性之间存在差异 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> <xref:System.Windows.FrameworkElement.ActualWidth%2A> 。 例如， <xref:System.Windows.FrameworkElement.ActualHeight%2A> 属性是基于其他高度输入和布局系统的计算值。 此值是由布局系统本身基于实际呈现传递设置的，因此可能会略微滞后于属性的设置值，例如 <xref:System.Windows.FrameworkElement.Height%2A> ，作为输入更改的基础。
>
> 由于 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 是一个计算值，因此应注意到，由于布局系统的各种操作，可能会有多个或增量报告的更改。 布局系统可能会计算子元素所需的测量空间、父元素的约束等。

度量值传递的最终目标是让子元素确定在 <xref:System.Windows.UIElement.DesiredSize%2A> 调用期间发生的 <xref:System.Windows.FrameworkElement.MeasureCore%2A> 。 <xref:System.Windows.UIElement.DesiredSize%2A>值由存储， <xref:System.Windows.UIElement.Measure%2A> 以便在内容排列传递过程中使用。

排列传递通过调用方法来开始 <xref:System.Windows.UIElement.Arrange%2A> 。 在排列过程中，父 <xref:System.Windows.Controls.Panel> 元素会生成一个表示子级边界的矩形。 此值将传递给 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 方法以进行处理。

<xref:System.Windows.FrameworkElement.ArrangeCore%2A>方法计算子级的 <xref:System.Windows.UIElement.DesiredSize%2A> ，并计算可能会影响元素呈现大小的任何其他边距。 <xref:System.Windows.FrameworkElement.ArrangeCore%2A>生成一个 `arrangeSize` ，它作为参数传递到 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 的方法 <xref:System.Windows.Controls.Panel> 。 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>生成 `finalSize` 子的。 最后， <xref:System.Windows.FrameworkElement.ArrangeCore%2A> 方法执行偏移量属性（如边距和对齐方式）的最终计算，并将子元素放在其布局槽内。 子元素不需要（并且通常不）填充整个分配空间。 然后，将控件返回到父级 <xref:System.Windows.Controls.Panel> ，并且布局过程已完成。

<a name="LayoutSystem_PanelsCustom"></a>

## <a name="panel-elements-and-custom-layout-behaviors"></a>面板元素和自定义布局行为

WPF 包含一组从派生的元素 <xref:System.Windows.Controls.Panel> 。 这些 <xref:System.Windows.Controls.Panel> 元素可以实现许多复杂的布局。 例如，可以通过使用元素轻松实现堆栈元素 <xref:System.Windows.Controls.StackPanel> ，而使用可以实现更复杂和更自由的流动布局 <xref:System.Windows.Controls.Canvas> 。

下表汇总了可用的布局 <xref:System.Windows.Controls.Panel> 元素。

|面板名称|说明|
|----------------|-----------------|
|<xref:System.Windows.Controls.Canvas>|定义一个区域，可在其中通过相对于区域的坐标以显式方式来定位子元素 <xref:System.Windows.Controls.Canvas> 。|
|<xref:System.Windows.Controls.DockPanel>|定义一个区域，从中可以按相对位置水平或垂直排列各个子元素。|
|<xref:System.Windows.Controls.Grid>|定义由列和行组成的灵活的网格区域。|
|<xref:System.Windows.Controls.StackPanel>|将子元素排列成水平或垂直的一行。|
|<xref:System.Windows.Controls.VirtualizingPanel>|为虚拟化其子数据集合的 <xref:System.Windows.Controls.Panel> 元素提供一个框架。 这是一个抽象类。|
|<xref:System.Windows.Controls.WrapPanel>|按从左到右的顺序位置定位子元素，在包含框的边缘处将内容切换到下一行。 后续排序按从上到下或从右到左的顺序进行，具体取决于 <xref:System.Windows.Controls.WrapPanel.Orientation%2A> 属性的值。|

对于需要使用任何预定义元素无法实现的布局的应用程序 <xref:System.Windows.Controls.Panel> ，可以通过继承和 <xref:System.Windows.Controls.Panel> 重写 <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 和方法来实现自定义布局行为 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> 。

<a name="LayoutSystem_Performance"></a>

## <a name="layout-performance-considerations"></a>布局性能注意事项

布局是一个递归过程。 集合中的每个子元素都将在 <xref:System.Windows.Controls.Panel.Children%2A> 每次调用布局系统的过程中得到处理。 因此，应避免在不必要时触发布局系统。 以下注意事项有助于实现更好的性能。

- 应注意哪些属性值更改会强制执行布局系统的递归更新。

  如果依赖属性的值可能导致布局系统被初始化，则会使用公共标志对该依赖属性进行标记。 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>和 <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> 提供了一些有用的线索，其中的属性值更改将强制布局系统进行递归更新。 通常，任何可能影响元素边界框大小的属性都应将 <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> 标志设置为 true。 有关详细信息，请参阅[依赖项属性概述](dependency-properties-overview.md)。

- 如果可能，请使用 <xref:System.Windows.UIElement.RenderTransform%2A> 而不是 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 。

  <xref:System.Windows.FrameworkElement.LayoutTransform%2A>可以是影响的内容的一种非常有用的方法 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。 但是，如果转换的效果不必影响其他元素的位置，则最好改用 <xref:System.Windows.UIElement.RenderTransform%2A> ，因为不 <xref:System.Windows.UIElement.RenderTransform%2A> 会调用布局系统。 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>应用其转换，并强制执行递归布局更新以考虑受影响元素的新位置。

- 避免不必要的调用 <xref:System.Windows.UIElement.UpdateLayout%2A> 。

  <xref:System.Windows.UIElement.UpdateLayout%2A>方法强制执行递归布局更新，并且通常不需要这样做。 除非你确定需要进行完整更新，否则请依赖布局系统为你调用此方法。

- 使用大型 <xref:System.Windows.Controls.Panel.Children%2A> 集合时，请考虑使用 <xref:System.Windows.Controls.VirtualizingStackPanel> 而不是常规 <xref:System.Windows.Controls.StackPanel> 。

  通过虚拟化子集合， <xref:System.Windows.Controls.VirtualizingStackPanel> 只会将对象保存在当前在父级的视区中。 因此，在大多数情况下，性能得到显著提高。

<a name="LayoutSystem_LayoutRounding"></a>

## <a name="sub-pixel-rendering-and-layout-rounding"></a>子像素渲染和布局舍入

WPF 图形系统使用与设备无关的单位来实现分辨率和设备独立性。 每个与设备无关的像素会自动调整为系统的每英寸点数（dpi）设置。 这为 WPF 应用程序提供了针对不同 dpi 设置的适当缩放，并使应用程序能够自动识别 dpi。

但是，这种 dpi 独立性可能会因为抗锯齿而产生不规则边缘渲染。 这些伪影通常被视为模糊或半透明边缘，当边缘的位置落在设备像素的中间而不是设备像素之间时，就可能出现。 布局系统提供了一种通过布局倒圆对此进行调整的方法。 布局舍入是布局系统在布局传递中舍入任何非整数像素值的情况。

默认情况下禁用布局舍入。 若要启用布局舍入，请将 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 属性设置为 `true` on any <xref:System.Windows.FrameworkElement> 。 因为它是一个依赖属性，所以该值将传播到可视化树中的所有子级。 若要为整个 UI 启用布局舍入， <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> 请 `true` 在根容器上设置为。 有关示例，请参见 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>。

<a name="LayoutSystem_whatsnext"></a>

## <a name="whats-next"></a>后续步骤

了解元素的测量和排列方式是了解布局的第一步。 有关可用元素的详细信息 <xref:System.Windows.Controls.Panel> ，请参阅[面板概述](../controls/panels-overview.md)。 若要更好地了解可能影响布局的各种定位属性，请参阅[对齐、边距和填充概述](alignment-margins-and-padding-overview.md)。 准备好将其全部放在轻型应用程序中时，请参阅[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [面板概述](../controls/panels-overview.md)
- [Alignment、Margin 和 Padding 概述](alignment-margins-and-padding-overview.md)
- [布局和示例](optimizing-performance-layout-and-design.md)
