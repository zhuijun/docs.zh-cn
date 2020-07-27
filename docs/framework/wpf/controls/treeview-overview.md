---
title: TreeView 概述
description: 了解 Windows Presentation Foundation TreeView 控件如何使用节点显示层次结构中的信息，包括简单的示例。
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: 6ef77febdd3facb7c7e1af566841c2a1aeaff810
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164540"
---
# <a name="treeview-overview"></a>TreeView 概述
<xref:System.Windows.Controls.TreeView>控件提供了使用可折叠节点在层次结构中显示信息的方法。 本主题介绍 <xref:System.Windows.Controls.TreeView> 和 <xref:System.Windows.Controls.TreeViewItem> 控件，并提供其用法的简单示例。  

<a name="Simple_TreeView_Control"></a>
## <a name="what-is-a-treeview"></a>什么是 TreeView？  
 <xref:System.Windows.Controls.TreeView>是 <xref:System.Windows.Controls.ItemsControl> 使用控件嵌套项的 <xref:System.Windows.Controls.TreeViewItem> 。 下面的示例创建一个 <xref:System.Windows.Controls.TreeView> 。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>
## <a name="creating-a-treeview"></a>创建 TreeView  
 <xref:System.Windows.Controls.TreeView>控件包含控件的层次结构 <xref:System.Windows.Controls.TreeViewItem> 。 <xref:System.Windows.Controls.TreeViewItem>控件是 <xref:System.Windows.Controls.HeaderedItemsControl> 具有 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 集合的。  
  
 如果你 <xref:System.Windows.Controls.TreeView> 使用定义 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，则可以显式定义 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 控件的内容 <xref:System.Windows.Controls.TreeViewItem> 和组成其集合的项。 上图演示了此方法。  
  
 您还可以指定 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 作为数据源，然后指定 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 来定义 <xref:System.Windows.Controls.TreeViewItem> 内容。  
  
 若要定义控件的布局 <xref:System.Windows.Controls.TreeViewItem> ，还可以使用 <xref:System.Windows.HierarchicalDataTemplate> 对象。 有关详细信息和示例，请参阅[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 如果某个项不是 <xref:System.Windows.Controls.TreeViewItem> 控件，则在显示该控件时，该控件将自动包含在控件中 <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.Controls.TreeView> 。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>
## <a name="expanding-and-collapsing-a-treeviewitem"></a>展开和折叠 TreeViewItem  
 如果用户展开 <xref:System.Windows.Controls.TreeViewItem> ，则 <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 属性设置为 `true` 。 你还可以 <xref:System.Windows.Controls.TreeViewItem> 通过将 <xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> 属性设置为 `true` （展开）或 `false` （折叠）来展开或折叠没有任何直接用户操作的。 此属性发生更改时， <xref:System.Windows.Controls.TreeViewItem.Expanded> 将 <xref:System.Windows.Controls.TreeViewItem.Collapsed> 发生或事件。  
  
 在 <xref:System.Windows.FrameworkElement.BringIntoView%2A> 控件上调用方法时 <xref:System.Windows.Controls.TreeViewItem> ，将 <xref:System.Windows.Controls.TreeViewItem> 展开及其父 <xref:System.Windows.Controls.TreeViewItem> 控件。 如果 <xref:System.Windows.Controls.TreeViewItem> 不可见或部分可见，则 <xref:System.Windows.Controls.TreeView> 滚动以使其可见。  
  
<a name="TreeViewItem_Selection"></a>
## <a name="treeviewitem-selection"></a>TreeViewItem 选择  
 当用户单击 <xref:System.Windows.Controls.TreeViewItem> 控件以选择它时，将 <xref:System.Windows.Controls.TreeViewItem.Selected> 发生事件，并将其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 属性设置为 `true` 。 <xref:System.Windows.Controls.TreeViewItem>还会成为 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 控件的 <xref:System.Windows.Controls.TreeView> 。 相反，当选择从控件更改时 <xref:System.Windows.Controls.TreeViewItem> ，它的 <xref:System.Windows.Controls.TreeViewItem.Unselected> 事件发生，并且其 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 属性设置为 `false` 。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>控件的属性 <xref:System.Windows.Controls.TreeView> 为只读属性; 因此，不能对其进行显式设置。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>如果用户单击 <xref:System.Windows.Controls.TreeViewItem> 控件或 <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> 控件上的属性设置为，则设置属性 `true` <xref:System.Windows.Controls.TreeViewItem> 。  
  
 使用 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> 属性指定 <xref:System.Windows.Controls.TreeView.SelectedValue%2A> 的 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> 。 有关详细信息，请参阅[使用 SelectedValue、SelectedValuePath 和 SelectedItem](how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)。  
  
 可以在事件上注册事件处理程序 <xref:System.Windows.Controls.TreeView.SelectedItemChanged> ，以便确定所选更改的时间 <xref:System.Windows.Controls.TreeViewItem> 。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>向事件处理程序提供的指定 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> （这是上一个选择）和 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> （当前所选内容）。 如果应用程序或用户未进行上一个或当前选择，则任一值都可能为 `null`。  
  
<a name="TreeView_Style"></a>
## <a name="treeview-style"></a>TreeView 样式  
 控件的默认样式将 <xref:System.Windows.Controls.TreeView> 其放在 <xref:System.Windows.Controls.StackPanel> 包含控件的对象中 <xref:System.Windows.Controls.ScrollViewer> 。 当你为设置 <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> 了和属性时 <xref:System.Windows.Controls.TreeView> ，将使用这些值来调整用于 <xref:System.Windows.Controls.StackPanel> 显示的对象的大小 <xref:System.Windows.Controls.TreeView> 。 如果要显示的内容大于显示区域，则 <xref:System.Windows.Controls.ScrollViewer> 会自动显示，以便用户可以滚动浏览 <xref:System.Windows.Controls.TreeView> 内容。  
  
 若要自定义控件的外观 <xref:System.Windows.Controls.TreeViewItem> ，请将 <xref:System.Windows.FrameworkElement.Style%2A> 属性设置为自定义 <xref:System.Windows.Style> 。  
  
 下面的示例演示如何 <xref:System.Windows.Controls.Control.Foreground%2A> 使用设置控件的和 <xref:System.Windows.Controls.Control.FontSize%2A> 属性值 <xref:System.Windows.Controls.TreeViewItem> <xref:System.Windows.FrameworkElement.Style%2A> 。  
  
 [!code-xaml[TreeViewSimple#8](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>
## <a name="adding-images-and-other-content-to-treeview-items"></a>向 TreeView 项添加图像和其他内容  
 可以在的内容中包含多个对象 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> 。 若要在内容中包含多个对象，请将 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> 对象置于布局控件内，如 <xref:System.Windows.Controls.Panel> 或 <xref:System.Windows.Controls.StackPanel> 。  
  
 下面的示例演示如何将的定义 <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> <xref:System.Windows.Controls.TreeViewItem> 为 <xref:System.Windows.Controls.CheckBox> ，并将其 <xref:System.Windows.Controls.TextBlock> 同时包含在 <xref:System.Windows.Controls.DockPanel> 控件中。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 下面的示例演示如何定义， <xref:System.Windows.DataTemplate> 其中包含包含 <xref:System.Windows.Controls.Image> <xref:System.Windows.Controls.TextBlock> 在控件中的和 <xref:System.Windows.Controls.DockPanel> 。 您可以使用 <xref:System.Windows.DataTemplate> 为设置 <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> 或 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.TreeViewItem> 。  
  
 [!code-xaml[TreeViewDataBinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [操作指南主题](treeview-how-to-topics.md)
- [WPF 内容模型](wpf-content-model.md)
