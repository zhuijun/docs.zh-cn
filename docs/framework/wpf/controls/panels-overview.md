---
title: 面板概述
description: Windows Presentation Foundation 提供了控制元素呈现的预定义面板元素。 了解如何构建自定义 Panel 元素。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF], about Panel control
- controls [WPF], Panel
ms.assetid: f73644af-9941-4611-8754-6d4cef03fc44
ms.openlocfilehash: 7f3f6948de28f50dc6470a7dfc1a5bad67e57c79
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167766"
---
# <a name="panels-overview"></a>面板概述
<xref:System.Windows.Controls.Panel>元素是控制元素（其大小和尺寸、位置以及其子内容的排列）的呈现的组件。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供了许多预定义的 <xref:System.Windows.Controls.Panel> 元素以及构造自定义元素的功能 <xref:System.Windows.Controls.Panel> 。  
  
 本主题包含以下各节：  
  
- [Panel 类](#Panels_view_from_10000_feet)  
  
- [Panel 元素公共成员](#Panels_declared_members)  
  
- [派生 Panel 元素](#Panels_derived_elements)  
  
- [用户界面 Panel](#Panels_main_UI_elements)  
  
- [嵌套 Panel 元素](#Panels_nested_panel_elements)  
  
- [自定义 Panel 元素](#Panels_custom_panel_elements)  
  
- [本地化/全球化支持](#Panels_global_localization)  
  
<a name="Panels_view_from_10000_feet"></a>
## <a name="the-panel-class"></a>Panel 类  
 <xref:System.Windows.Controls.Panel>是中提供布局支持的所有元素的基类 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 。 派生 <xref:System.Windows.Controls.Panel> 元素用于在和代码中放置和排列元素 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 包含一套全面的派生面板实现，可支持许多复杂的布局。 这些派生类公开可实现大部分标准 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 方案的属性和方法。 找不到满足其需求的子排列行为的开发人员可以通过重写和方法来创建新的布局 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 。 有关自定义布局行为的详细信息，请参阅[自定义 Panel 元素](#Panels_custom_panel_elements)。  
  
<a name="Panels_declared_members"></a>
## <a name="panel-common-members"></a>Panel 公共成员  
 所有 <xref:System.Windows.Controls.Panel> 元素都支持定义的基本大小调整和定位属性 <xref:System.Windows.FrameworkElement> ，包括、、、 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 、 <xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.LayoutTransform%2A> 。 有关定义的定位属性的其他信息 <xref:System.Windows.FrameworkElement> ，请参阅[对齐、边距和填充概述](../advanced/alignment-margins-and-padding-overview.md)。  
  
 <xref:System.Windows.Controls.Panel>公开更重要的其他属性，这些属性对于理解和使用布局非常重要。 <xref:System.Windows.Controls.Panel.Background%2A>属性用于使用填充派生面板元素边界之间的区域 <xref:System.Windows.Media.Brush> 。 <xref:System.Windows.Controls.Panel.Children%2A>表示由组成的元素的子集合 <xref:System.Windows.Controls.Panel> 。 <xref:System.Windows.Controls.Panel.InternalChildren%2A>表示集合的内容 <xref:System.Windows.Controls.Panel.Children%2A> 和数据绑定生成的成员。 两者均由 <xref:System.Windows.Controls.UIElementCollection> 父级中承载的子元素组成 <xref:System.Windows.Controls.Panel> 。  
  
 面板还公开了 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 可用于在派生中实现分层顺序的附加属性 <xref:System.Windows.Controls.Panel> 。 具有较高值的面板集合的成员将 <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 出现在值较小的面板上 <xref:System.Windows.Controls.Panel.ZIndex%2A?displayProperty=nameWithType> 。 这对于的面板（如） <xref:System.Windows.Controls.Canvas> 和 <xref:System.Windows.Controls.Grid> 允许子共享同一坐标空间的面板特别有用。  
  
 <xref:System.Windows.Controls.Panel>还定义了 <xref:System.Windows.Controls.Panel.OnRender%2A> 方法，该方法可用于重写的默认呈现行为 <xref:System.Windows.Controls.Panel> 。  
  
#### <a name="attached-properties"></a>附加属性  
 派生面板元素广泛使用附加属性。 附加属性是一种专用化的依赖项属性，不具有传统的公共语言运行时（CLR）属性 "包装器"。 附加属性在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 中具有特殊化的语法，可在后面的几个示例中看到。  
  
 附加属性的一个用途是允许子元素存储实际上由父元素定义的属性的唯一值。 此功能的一项应用是让子元素通知父级它们希望如何在 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中呈现，这对应用程序布局非常有用。 有关详细信息，请参阅[附加属性概述](../advanced/attached-properties-overview.md)。  
  
<a name="Panels_derived_elements"></a>
## <a name="derived-panel-elements"></a>派生 Panel 元素  
 许多对象都派生自 <xref:System.Windows.Controls.Panel> ，但并不是所有对象都要用作根布局提供程序。 有六个已定义的面板类（ <xref:System.Windows.Controls.Canvas> 、、、、 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel> 和 <xref:System.Windows.Controls.WrapPanel> ）专门用于创建应用程序 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。  
  
 每个面板元素都封装自己的特殊功能，如下表所示。  
  
|元素名称|是否为 UI 面板？|说明|  
|------------------|---------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|是|定义一个区域，可在其中通过相对于区域的坐标以显式方式来定位子元素 <xref:System.Windows.Controls.Canvas> 。|  
|<xref:System.Windows.Controls.DockPanel>|是|定义一个区域，从中可以按相对位置水平或垂直排列各个子元素。|  
|<xref:System.Windows.Controls.Grid>|是|定义一个由列和行组成的灵活网格区域。 的子元素 <xref:System.Windows.Controls.Grid> 可使用属性精确定位 <xref:System.Windows.FrameworkElement.Margin%2A> 。|  
|<xref:System.Windows.Controls.StackPanel>|是|将子元素排列成水平或垂直的一行。|  
|<xref:System.Windows.Controls.Primitives.TabPanel>|否|处理中选项卡按钮的布局 <xref:System.Windows.Controls.TabControl> 。|  
|<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|否|排列控件中的内容 <xref:System.Windows.Controls.ToolBar> 。|  
|<xref:System.Windows.Controls.Primitives.UniformGrid>|否|<xref:System.Windows.Controls.Primitives.UniformGrid>用于在网格中的所有单元格大小相等的情况排列子元素。|  
|<xref:System.Windows.Controls.VirtualizingPanel>|否|为可以“虚拟化”其子级集合的面板提供基类。|  
|<xref:System.Windows.Controls.VirtualizingStackPanel>|是|在水平或垂直方向上将内容排列为一行并使其虚拟化。|  
|<xref:System.Windows.Controls.WrapPanel>|是|<xref:System.Windows.Controls.WrapPanel>按从左至右的顺序位置定位子元素，在包含框的边缘处将内容分解到下一行。 后续排序按照从上到下或从右到左的顺序进行，具体取决于 <xref:System.Windows.Controls.WrapPanel.Orientation%2A> 属性的值。|  
  
<a name="Panels_main_UI_elements"></a>
## <a name="user-interface-panels"></a>用户界面 Panel  
 中提供了六个面板类 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，这些面板类经过优化，可支持 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 方案： <xref:System.Windows.Controls.Canvas> 、 <xref:System.Windows.Controls.DockPanel> 、 <xref:System.Windows.Controls.Grid> 、、 <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.VirtualizingStackPanel> 和 <xref:System.Windows.Controls.WrapPanel> 。 这些面板元素易于使用、功能齐全并且可扩展，足以适用于大多数应用程序。  
  
 每个派生 <xref:System.Windows.Controls.Panel> 元素都以不同方式对待大小约束。 了解如何 <xref:System.Windows.Controls.Panel> 在水平方向或垂直方向上处理约束可以使布局更具可预测性。  
  
|**面板名称**|**x 维度**|**y 维度**|  
|--------------------|----------------------|----------------------|  
|<xref:System.Windows.Controls.Canvas>|按内容约束|按内容约束|  
|<xref:System.Windows.Controls.DockPanel>|约束|约束|  
|<xref:System.Windows.Controls.StackPanel>（垂直方向）|约束|按内容约束|  
|<xref:System.Windows.Controls.StackPanel>（水平方向）|按内容约束|约束|  
|<xref:System.Windows.Controls.Grid>|约束|受约束，在 <xref:System.Windows.GridUnitType.Auto> 应用于行和列的情况下除外|  
|<xref:System.Windows.Controls.WrapPanel>|按内容约束|按内容约束|  
  
 可在下方找到其中每种元素的更多详细说明和使用示例。  
  
<a name="Panels_overview_Canvas_subsection"></a>
### <a name="canvas"></a>画布  
 <xref:System.Windows.Controls.Canvas>元素可根据绝对*x*和*y*坐标定位内容。 元素可以在唯一位置绘制；或者，如果元素占用了相同坐标，则这些元素在标记中显示的顺序决定它们的绘制顺序。  
  
 <xref:System.Windows.Controls.Canvas>提供对的最灵活的布局支持 <xref:System.Windows.Controls.Panel> 。 "高度" 和 "宽度" 属性用于定义画布的面积，并为内的元素分配相对于父区域的绝对坐标 <xref:System.Windows.Controls.Canvas> 。 四个附加属性：、 <xref:System.Windows.Controls.Canvas.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Top%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Canvas.Right%2A?displayProperty=nameWithType> 和 <xref:System.Windows.Controls.Canvas.Bottom%2A?displayProperty=nameWithType> ，允许在中对对象放置进行精细控制 <xref:System.Windows.Controls.Canvas> ，使开发人员能够在屏幕上精确地定位和排列元素。  
  
#### <a name="cliptobounds-within-a-canvas"></a>Canvas 内 ClipToBounds  
 <xref:System.Windows.Controls.Canvas>可以将子元素定位在屏幕上的任何位置，甚至可以定位在其自身定义和之外的坐标处 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> 。 而且， <xref:System.Windows.Controls.Canvas> 不受其子级的大小的影响。 因此，子元素可以过度绘制父元素外边框外的其他元素 <xref:System.Windows.Controls.Canvas> 。 的默认行为 <xref:System.Windows.Controls.Canvas> 是允许在父项的边界之外绘制子级 <xref:System.Windows.Controls.Canvas> 。 如果不需要此行为，则 <xref:System.Windows.UIElement.ClipToBounds%2A> 可以将属性设置为 `true` 。 这会导致 <xref:System.Windows.Controls.Canvas> 剪裁到其自身大小。 <xref:System.Windows.Controls.Canvas>是唯一的布局元素，它允许在其边界之外绘制子级。  
  
 [宽度属性比较示例](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)中以图形方式展示了此行为。  
  
#### <a name="defining-and-using-a-canvas"></a>定义和使用 Canvas  
 <xref:System.Windows.Controls.Canvas>只需使用或代码，即可实例化 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。 下面的示例演示如何使用 <xref:System.Windows.Controls.Canvas> 来绝对定位内容。 此代码生成三个 100 像素正方形。 第一个正方形为红色，其左上角的 (*x, y*) 位置指定为 (0, 0)。 第二个正方形为绿色，其左上角位置为 (100, 100)，在第一个正方形的右下方。 第三个正方形为蓝色，其左上角为 (50, 50)，因此包含了第一个正方形的右下四分之一部分和第二个正方形的左上四分之一部分。 由于第三个正方形最后布置，因此它看起来在另外两个正方形上方，即，重叠部分采用第三个正方形的颜色。  
  
 [!code-csharp[CanvasOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasOvwSample/CSharp/Canvas_Ovw_Sample.cs#1)]
 [!code-vb[CanvasOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasOvwSample/VisualBasic/canvas_vb.vb#1)]
 [!code-xaml[CanvasOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/CanvasOvwSample/XAML/default.xaml#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![典型的 Canvas 元素。](./media/panel-intro-canvas.PNG "panel_intro_canvas")  
  
<a name="Panels_overview_DockPanel_subsection"></a>
### <a name="dockpanel"></a>DockPanel  
 <xref:System.Windows.Controls.DockPanel>元素使用 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 在子 content 元素中设置的附加属性，沿容器边缘放置内容。 当 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 设置为 <xref:System.Windows.Controls.Dock.Top> 或时 <xref:System.Windows.Controls.Dock.Bottom> ，它将每个子元素的上方或下方放置。 当 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType> 设置为 <xref:System.Windows.Controls.Dock.Left> 或时 <xref:System.Windows.Controls.Dock.Right> ，它将子元素定位到彼此的左侧或右侧。 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A>属性确定作为的子元素添加的最后一个元素的位置 <xref:System.Windows.Controls.DockPanel> 。  
  
 您可以使用 <xref:System.Windows.Controls.DockPanel> 来定位一组相关的控件，例如一组按钮。 或者，您可以使用它来创建 "平移" [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，类似于在 Microsoft Outlook 中找到的。  
  
#### <a name="sizing-to-content"></a>按内容调整大小  
 如果 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.FrameworkElement.Width%2A> 未指定其和属性，则 <xref:System.Windows.Controls.DockPanel> 调整其内容的大小。 大小可以增大或减小以容纳其子元素的大小。 但是，如果指定了这些属性，但没有足够的空间用于下一个指定的子元素，则 <xref:System.Windows.Controls.DockPanel> 不会显示该子元素或后续的子元素，也不会度量后续的子元素。  
  
#### <a name="lastchildfill"></a>LastChildFill  
 默认情况下，元素的最后一个子 <xref:System.Windows.Controls.DockPanel> 元素将 "填充" 剩余的未分配空间。 如果不需要此行为，请将 <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> 属性设置为 `false` 。  
  
#### <a name="defining-and-using-a-dockpanel"></a>定义和使用 DockPanel  
 下面的示例演示如何使用对空间进行分区 <xref:System.Windows.Controls.DockPanel> 。 <xref:System.Windows.Controls.Border>添加了五个元素作为父级的子级 <xref:System.Windows.Controls.DockPanel> 。 每个都使用不同的定位属性 <xref:System.Windows.Controls.DockPanel> 来分区空间。 最后一个元素"填充"剩余的未分配空间。  
  
 [!code-cpp[DockPanelOvwSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/DockPanelOvwSample/CPP/DockPanel_Ovw_Sample.cpp#1)]
 [!code-csharp[DockPanelOvwSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DockPanelOvwSample/CSharp/DockPanel_Ovw_Sample.cs#1)]
 [!code-vb[DockPanelOvwSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DockPanelOvwSample/VisualBasic/dockpanel_vb.vb#1)]
 [!code-xaml[DockPanelOvwSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/DockPanelOvwSample/XAML/default.xaml#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![典型的 DockPanel 方案。](./media/panel-intro-dockpanel.PNG "panel_intro_dockpanel")  
  
<a name="Panels_overview_Grid_subsection"></a>
### <a name="grid"></a>Grid  
 <xref:System.Windows.Controls.Grid>元素合并绝对定位和表格数据控件的功能。 <xref:System.Windows.Controls.Grid>利用，您可以轻松地定位和样式元素。 <xref:System.Windows.Controls.Grid>允许您定义灵活的行分组和列分组，甚至提供一种在多个元素之间共享大小调整信息的机制 <xref:System.Windows.Controls.Grid> 。  
  
#### <a name="how-is-grid-different-from-table"></a>网格与表格有何不同？  
 <xref:System.Windows.Documents.Table>和 <xref:System.Windows.Controls.Grid> 共享一些通用功能，但每个功能最适合于不同的方案。 <xref:System.Windows.Documents.Table>旨在在流内容中使用（有关流内容的详细信息，请参阅[流文档概述](../advanced/flow-document-overview.md)）。 网格最适合在表单中（主要在流内容以外的任意位置）使用。 在中 <xref:System.Windows.Documents.FlowDocument> ， <xref:System.Windows.Documents.Table> 支持流内容行为，如分页、列重排和内容选择，而不支持 <xref:System.Windows.Controls.Grid> 。 <xref:System.Windows.Controls.Grid>另一方面，最好是在之外使用， <xref:System.Windows.Documents.FlowDocument> 因为这样做的原因很多 <xref:System.Windows.Controls.Grid> ，包括基于行和列索引添加元素 <xref:System.Windows.Documents.Table> 。 <xref:System.Windows.Controls.Grid>元素允许将子内容分层，允许多个元素存在于单个 "单元" 中。 <xref:System.Windows.Documents.Table>不支持分层。 的子元素 <xref:System.Windows.Controls.Grid> 可相对于其 "单元格" 边界区域进行绝对定位。 <xref:System.Windows.Documents.Table>不支持此功能。 最后， <xref:System.Windows.Controls.Grid> 比更轻量 <xref:System.Windows.Documents.Table> 。  
  
#### <a name="sizing-behavior-of-columns-and-rows"></a>列和行的大小调整行为  
 在中定义的列和行 <xref:System.Windows.Controls.Grid> 可以利用 <xref:System.Windows.GridUnitType.Star> 大小调整，以便按比例分配剩余空间。 如果 <xref:System.Windows.GridUnitType.Star> 选择作为行或列的高度或宽度，则该列或行会获得剩余可用空间的加权比例。 这与不同 <xref:System.Windows.GridUnitType.Auto> ，后者将基于列或行中内容的大小均匀分配空间。 在使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 时，此值以 `*` 或 `2*` 的形式表示。 在第一种情况下，行或列将得到一倍的可用空间，在第二种情况下，将得到两倍的可用空间，依此类推。 通过将此方法组合到一起，可以按比例分配空间 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ，并将 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> `Stretch` 布局空间分区为屏幕空间的百分比。 <xref:System.Windows.Controls.Grid>是唯一可以采用这种方式分布空间的布局面板。  
  
#### <a name="defining-and-using-a-grid"></a>定义和使用 Grid  
 下面的示例演示如何生成类似于在 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Windows "开始" 菜单上提供的 "运行" 对话框中找到的。  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![典型的网格元素。](./media/avalon-run-dialog.PNG "avalon_run_dialog")  
  
<a name="Panels_overview_StackPanel_subsection"></a>
### <a name="stackpanel"></a>StackPanel  
 <xref:System.Windows.Controls.StackPanel>利用，你可以按分配的方向 "stack" 元素。 默认堆叠方向为垂直方向。 <xref:System.Windows.Controls.StackPanel.Orientation%2A>属性可用于控制内容流。  
  
#### <a name="stackpanel-vs-dockpanel"></a>System.windows.controls.stackpanel> 与 System.windows.controls.dockpanel>  
 尽管 <xref:System.Windows.Controls.DockPanel> 还可以 "stack" 子元素， <xref:System.Windows.Controls.DockPanel> 但 <xref:System.Windows.Controls.StackPanel> 在某些使用方案中不会产生类似的结果。 例如，子元素的顺序可能会影响其在中的大小，而不会影响中的大小 <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.StackPanel> 。 这是因为 <xref:System.Windows.Controls.StackPanel> 在中的堆栈方向上测量 <xref:System.Double.PositiveInfinity> ，而 <xref:System.Windows.Controls.DockPanel> 仅测量可用大小。  
  
 以下示例演示此主要区别。  
  
 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
 通过此图像可以看到呈现行为的区别。  
  
 ![屏幕快照：StackPanel 与 DockPanel 对比屏幕快照](./media/layout-smiley-stackpanel.PNG "layout_smiley_stackpanel")  
  
#### <a name="defining-and-using-a-stackpanel"></a>定义和使用 StackPanel  
 下面的示例演示如何使用 <xref:System.Windows.Controls.StackPanel> 创建一组垂直定位的按钮。 对于水平定位，请将 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 属性设置为 <xref:System.Windows.Controls.Orientation.Horizontal> 。  
  
 [!code-csharp[StackPanel_ovw2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanel_ovw2/CSharp/StackPanel_Ovw_Sample2.cs#1)]
 [!code-vb[StackPanel_ovw2#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanel_ovw2/VisualBasic/StackPanelOvw.vb#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![典型的 StackPanel 元素。](./media/panel-intro-stackpanel.PNG "panel_intro_stackpanel")  
  
<a name="Panels_overview_VirtualizingStackPanel_subsection"></a>
#### <a name="virtualizingstackpanel"></a>VirtualizingStackPanel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]还提供了 <xref:System.Windows.Controls.StackPanel> 元素的变体，该元素自动 "虚拟化" 数据绑定的子内容。 在此上下文中，“虚拟化”一词指的是一种技术：通过此技术根据屏幕上哪些项可见，从较多的数据项中生成一个元素子集。 如果在指定时刻只有少量 UI 元素位于屏幕上，则此时生成大量 UI 元素需要占用大量内存和处理器。 <xref:System.Windows.Controls.VirtualizingStackPanel>（通过提供的功能 <xref:System.Windows.Controls.VirtualizingPanel> ）计算可见项，并 <xref:System.Windows.Controls.ItemContainerGenerator> 从 <xref:System.Windows.Controls.ItemsControl> （如 <xref:System.Windows.Controls.ListBox> 或 <xref:System.Windows.Controls.ListView> ）使用来仅创建可见项的元素。  
  
 <xref:System.Windows.Controls.VirtualizingStackPanel>元素自动设置为控件的宿主，如 <xref:System.Windows.Controls.ListBox> 。 承载数据绑定集合时，只要内容在的边界内，内容就会自动虚拟化 <xref:System.Windows.Controls.ScrollViewer> 。 在承载许多子项时，这将大幅提高性能。  
  
 下面的标记演示了如何使用 <xref:System.Windows.Controls.VirtualizingStackPanel> 作为项宿主。 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizingProperty?displayProperty=nameWithType>若要进行虚拟化，附加的属性必须设置为 `true` （默认值）。  
  
 [!code-xaml[VirtualizingStackPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/VirtualizingStackPanel_Intro/CS/default.xaml#1)]  
  
<a name="Panels_overview_WrapPanel"></a>
### <a name="wrappanel"></a>WrapPanel  
 <xref:System.Windows.Controls.WrapPanel>用于按从左到右的顺序位置定位子元素，并在到达其父容器的边缘时将内容分解到下一行。 内容可以设置为水平或垂直方向。 <xref:System.Windows.Controls.WrapPanel>对于简单的流动方案非常有用 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。 它还可以用来将统一大小调整应用于其所有子元素。  
  
 下面的示例演示如何创建 <xref:System.Windows.Controls.WrapPanel> 以显示在 <xref:System.Windows.Controls.Button> 到达其容器边缘时换行的控件。  
  
 [!code-cpp[WrapPanel_Intro#1](~/samples/snippets/cpp/VS_Snippets_Wpf/WrapPanel_Intro/CPP/WrapPanel_Code.cpp#1)]
 [!code-csharp[WrapPanel_Intro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WrapPanel_Intro/CSharp/WrapPanel_Code.cs#1)]
 [!code-vb[WrapPanel_Intro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WrapPanel_Intro/VisualBasic/WrapPanel_vb.vb#1)]
 [!code-xaml[WrapPanel_Intro#1](~/samples/snippets/xaml/VS_Snippets_Wpf/WrapPanel_Intro/XAML/default.xaml#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![典型的 WrapPanel 元素。](./media/wrappanel-element.PNG "WrapPanel_Element")  
  
<a name="Panels_nested_panel_elements"></a>
## <a name="nested-panel-elements"></a>嵌套 Panel 元素  
 <xref:System.Windows.Controls.Panel>元素可以相互嵌套，以便生成复杂的布局。 这在某些情况下非常有用，在这种情况下 <xref:System.Windows.Controls.Panel> ，一个是的一部分 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ，但可能不满足的其他部分的需求 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。  
  
 对于应用程序可以支持的嵌套数量，并没有实际限制，但通常最好限制应用程序仅使用预期布局实际所需的面板。 在许多情况下， <xref:System.Windows.Controls.Grid> 可以使用元素，而不是嵌套面板，因为它具有作为布局容器的灵活性。 这可以通过将不必要的元素排除在树以外来提高应用程序的性能。  
  
 下面的示例演示如何创建一个 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 利用嵌套元素的，以便 <xref:System.Windows.Controls.Panel> 实现特定的布局。 在此特定情况下， <xref:System.Windows.Controls.DockPanel> 元素用于提供 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 结构，嵌套 <xref:System.Windows.Controls.StackPanel> 元素、 <xref:System.Windows.Controls.Grid> 和 <xref:System.Windows.Controls.Canvas> 用于在父元素内精确定位子元素 <xref:System.Windows.Controls.DockPanel> 。  
  
 [!code-csharp[Nested_Panels#1](~/samples/snippets/csharp/VS_Snippets_Wpf/Nested_Panels/CSharp/nestedpanels.cs#1)]
 [!code-vb[Nested_Panels#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Nested_Panels/VisualBasic/nestedpanels.vb#1)]  
  
 经编译的应用程序产生新的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]，外观如下。  
  
 ![利用嵌套面板的 UI。](./media/nested-panels.PNG "nested_panels")  
  
<a name="Panels_custom_panel_elements"></a>
## <a name="custom-panel-elements"></a>自定义 Panel 元素  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供灵活的布局控件数组时，还可以通过重写和方法来实现自定义布局行为 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 。 可以通过在这些重写方法内定义新的位置行为来实现自定义大小调整和位置。  
  
 同样， <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Grid> 可以通过重写其和方法来定义基于派生类（如或）的自定义布局行为 <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> <xref:System.Windows.FrameworkElement.MeasureOverride%2A> 。  
  
 下面的标记演示如何创建自定义 <xref:System.Windows.Controls.Panel> 元素。 此新 <xref:System.Windows.Controls.Panel> 定义为 `PlotPanel` ，它支持通过使用硬编码*x*和*y*坐标来定位子元素。 在此示例中， <xref:System.Windows.Shapes.Rectangle> 元素（未显示）定位于绘图点50（*x*）和50（*y*）。  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
 若要查看更复杂的自定义面板实现，请参阅[创建自定义内容换行面板示例](https://go.microsoft.com/fwlink/?LinkID=159979)。  
  
<a name="Panels_global_localization"></a>
## <a name="localizationglobalization-support"></a>本地化/全球化支持  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 支持多种有助于创建可本地化的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 的功能。  
  
 所有 panel 元素都以本机方式支持 <xref:System.Windows.FrameworkElement.FlowDirection%2A> 属性，该属性可用于根据用户的区域设置或语言设置动态地重新流动内容。 有关详细信息，请参阅 <xref:System.Windows.FrameworkElement.FlowDirection%2A>。  
  
 <xref:System.Windows.Window.SizeToContent%2A>属性提供了一种机制，使应用程序开发人员能够预测本地化需求 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 使用 <xref:System.Windows.SizeToContent.WidthAndHeight> 此属性的值，父级 <xref:System.Windows.Window> 始终动态调整大小以适应内容，并且不受人工高度或宽度限制的限制。  
  
 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Grid> 和 <xref:System.Windows.Controls.StackPanel> 都是可本地化的不错选择 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 。 <xref:System.Windows.Controls.Canvas>这并不是一个不错的选择，因为它以绝对方式定位内容，因此很难进行本地化。  
  
 有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 使用可本地化的用户界面（ui）创建应用程序的其他信息，请参阅[使用自动布局概述](../advanced/use-automatic-layout-overview.md)。  
  
## <a name="see-also"></a>另请参阅

- [演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [WPF 布局库示例](https://go.microsoft.com/fwlink/?LinkID=160054)
- [布局](../advanced/layout.md)
- [WPF 控件库示例](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
- [Alignment、Margin 和 Padding 概述](../advanced/alignment-margins-and-padding-overview.md)
- [创建自定义内容换行面板示例](https://go.microsoft.com/fwlink/?LinkID=159979)
- [附加属性概述](../advanced/attached-properties-overview.md)
- [使用自动布局概述](../advanced/use-automatic-layout-overview.md)
- [布局和示例](../advanced/optimizing-performance-layout-and-design.md)
