---
title: 优化控件性能
description: Windows Presentation Foundation 包含许多 Windows 应用程序中使用的常用组件。 了解如何提高用户界面性能。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: de348dd93e5710b5b81af035ec7aa56e01dc4981
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168302"
---
# <a name="optimizing-performance-controls"></a>优化性能：控件

Windows Presentation Foundation （WPF）包含许多 Windows 应用程序中使用的常用用户界面（UI）组件。 本主题包含提高 UI 性能的技术。

## <a name="displaying-large-data-sets"></a>显示大型数据集

WPF 控件（如 <xref:System.Windows.Controls.ListView> 和） <xref:System.Windows.Controls.ComboBox> 用于显示应用程序中的项列表。 如果要显示的列表较大，则应用程序性能可能受到影响。 这是因为标准布局系统会为每个与列表控件关联的项创建布局容器，并计算其布局大小和位置。 通常，无需同时显示所有项，而是显示子集，然后用户滚动浏览列表。 这种情况下，使用 UI 虚拟化** 具有意义，这意味着生成项容器，且项的关联布局计算会推迟，直到项可见时。

UI 虚拟化是列表控件的一个重要方面。 不应混淆 UI 虚拟化和数据虚拟化。 UI 虚拟化在内存中仅存储可见项，但在数据绑定方案中会存储内存中的整个数据结构。 相反，数据虚拟化仅存储内存中屏幕上可见的数据项。

默认情况下，会在 <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.ListBox> 其列表项绑定到数据时为和控件启用 UI 虚拟化。 <xref:System.Windows.Controls.TreeView>可以通过将 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> 附加属性设置为来启用虚拟化 `true` 。 如果要为派生自的自定义控件 <xref:System.Windows.Controls.ItemsControl> 或使用类的现有项控件（如）启用 UI 虚拟化 <xref:System.Windows.Controls.StackPanel> ， <xref:System.Windows.Controls.ComboBox> 则可以将设置 <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> 为 <xref:System.Windows.Controls.VirtualizingStackPanel> 并将设置 <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> 为 `true` 。 遗憾的是，可对没有实现虚拟化的控件禁用 UI 虚拟化。 以下为禁用 UI 虚拟化的条件列表。

- 项容器直接添加到中 <xref:System.Windows.Controls.ItemsControl> 。 例如，如果应用程序将对象显式添加 <xref:System.Windows.Controls.ListBoxItem> 到 <xref:System.Windows.Controls.ListBox> ，则不 <xref:System.Windows.Controls.ListBox> 会将对象虚拟化 <xref:System.Windows.Controls.ListBoxItem> 。

- 中的项容器 <xref:System.Windows.Controls.ItemsControl> 的类型不同。 例如， <xref:System.Windows.Controls.Menu> 使用 <xref:System.Windows.Controls.Separator> 对象的不能实现项回收，因为 <xref:System.Windows.Controls.Menu> 包含类型为和的对象 <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.MenuItem> 。

- 将设置 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 为 `false` 。

- 将设置 <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> 为 `false` 。

虚拟化项容器时需要考虑到一个重要因素，即是否具有与属于项的项容器相关联的其他状态信息。 这种情况下，必须保存其他状态。 例如，你可能有一个包含在控件中的项， <xref:System.Windows.Controls.Expander> 并且该 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 状态绑定到项的容器，而不是绑定到项本身。 当对新项重用容器时，的当前值 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 将用于新项。 此外，旧项丢失了正确的 <xref:System.Windows.Controls.Expander.IsExpanded%2A> 值。

当前，无任何 WPF 控件提供对数据虚拟化的内置支持。

## <a name="container-recycling"></a>容器回收

在从继承的控件的 .NET Framework 3.5 SP1 中添加的 UI 虚拟化优化 <xref:System.Windows.Controls.ItemsControl> 是*容器回收，* 这还可以提高滚动性能。 当 <xref:System.Windows.Controls.ItemsControl> 填充使用 UI 虚拟化的时，它会为滚动到视图中的每个项创建一个项容器，并为每个滚动到视图之外的项销毁项容器。 *容器回收*使控件可以为不同数据项重复使用现有项容器，以便在用户滚动时不会不断创建和销毁项容器 <xref:System.Windows.Controls.ItemsControl> 。 可以通过将附加属性设置为来选择启用项目回收 <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> <xref:System.Windows.Controls.VirtualizationMode.Recycling> 。

<xref:System.Windows.Controls.ItemsControl>支持虚拟化的任何都可以使用容器回收。 有关如何在上启用容器回收的示例 <xref:System.Windows.Controls.ListBox> ，请参阅[改善 ListBox 的滚动性能](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md)。

## <a name="supporting-bidirectional-virtualization"></a>支持双向虚拟化

<xref:System.Windows.Controls.VirtualizingStackPanel>以水平或垂直方式为一个方向的 UI 虚拟化提供内置支持。 如果要对控件使用双向虚拟化，必须实现扩展类的自定义面板 <xref:System.Windows.Controls.VirtualizingStackPanel> 。 <xref:System.Windows.Controls.VirtualizingStackPanel>类公开了虚方法，例如 <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A> 、 <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A> 、 <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> 和 <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> 。利用这些虚方法，你可以检测列表的可见部分中的更改并相应地对其进行处理。

## <a name="optimizing-templates"></a>优化模板

可视化树包含应用程序中所有可视元素。 除直接创建的对象外，它还包括由于模板扩展而产生的对象。 例如，在创建时 <xref:System.Windows.Controls.Button> ，还会 <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter> 在可视化树中获取和对象。 如果尚未优化模板控件，则要在可视化树中创建大量不必要的额外对象。 有关可视化树的详细信息，请参见 [WPF 图形呈现概述](../graphics-multimedia/wpf-graphics-rendering-overview.md)。

## <a name="deferred-scrolling"></a>延迟滚动

默认情况下，用户拖动滚动条上的滚动块时，内容视图会不断更新。 如果控件中滚动较慢，请考虑使用延迟滚动。 在延迟滚动中，仅在用户释放滚动块时才会更新内容。

若要实现延迟滚动，请将 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> 属性设置为 `true` 。 <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>是附加属性，可在 <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.ScrollViewer> 其控件模板中设置的任何控件上进行设置。

## <a name="controls-that-implement-performance-features"></a>实现性能功能的控件

下表列出了显示数据的常见控件及其性能功能支持。 有关如何启用这些功能的信息，请参阅先前章节。

|控制|虚拟化|容器回收|延迟滚动|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|可启用|可启用|可启用|
|<xref:System.Windows.Controls.ContextMenu>|可启用|可启用|可启用|
|<xref:System.Windows.Controls.DocumentViewer>|不可用|不可用|可启用|
|<xref:System.Windows.Controls.ListBox>|默认|可启用|可启用|
|<xref:System.Windows.Controls.ListView>|默认|可启用|可启用|
|<xref:System.Windows.Controls.TreeView>|可启用|可启用|可启用|
|<xref:System.Windows.Controls.ToolBar>|不可用|不可用|可启用|

> [!NOTE]
> 有关如何在上启用虚拟化和容器回收的示例 <xref:System.Windows.Controls.TreeView> ，请参阅[提高 TreeView 的性能](../controls/how-to-improve-the-performance-of-a-treeview.md)。

## <a name="see-also"></a>另请参阅

- [布局](layout.md)
- [布局和示例](optimizing-performance-layout-and-design.md)
- [数据绑定](optimizing-performance-data-binding.md)
- [控制](../controls/index.md)
- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [演练：在 WPF 应用程序中缓存应用程序数据](walkthrough-caching-application-data-in-a-wpf-application.md)
