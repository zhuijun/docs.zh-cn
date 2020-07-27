---
title: ListView 概述
description: 了解 Windows Presentation Foundation ListView 控件，该控件提供基础结构以显示不同布局或视图中的数据项。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164558"
---
# <a name="listview-overview"></a>ListView 概述
<xref:System.Windows.Controls.ListView>控件提供基础结构，以显示不同布局或视图中的一组数据项。 例如，用户可能需要在表格中显示数据项，并同时对表格的列进行排序。  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>什么是 ListView？  
 <xref:System.Windows.Controls.ListView>控件是 <xref:System.Windows.Controls.ItemsControl> 从派生的 <xref:System.Windows.Controls.ListBox> 。 通常，其项是数据集合的成员，并表示为 <xref:System.Windows.Controls.ListViewItem> 对象。 <xref:System.Windows.Controls.ListViewItem>是一个 <xref:System.Windows.Controls.ContentControl> ，只能包含一个子元素。 但是，该子元素可以是任何视觉元素。  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>为 ListView 定义视图模式  
 若要为控件的内容指定视图模式 <xref:System.Windows.Controls.ListView> ，请设置 <xref:System.Windows.Controls.ListView.View%2A> 属性。 提供的一个视图模式 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 为 <xref:System.Windows.Controls.GridView> ，它在具有可自定义列的表中显示数据项的集合。  
  
 下面的示例演示如何为 <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView> 显示雇员信息的控件定义。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下图演示上一个示例的数据显示方式。  
  
 ![显示带有 GridView 输出的 ListView 的屏幕截图。](./media/gridview-overview/listview-gridview-output.jpg)  
  
 您可以通过定义从类继承的类来创建自定义视图模式 <xref:System.Windows.Controls.ViewBase> 。 <xref:System.Windows.Controls.ViewBase>类提供创建自定义视图所需的基础结构。 有关如何创建自定义视图的详细信息，请参阅[为 ListView 创建自定义视图模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>将数据绑定到 ListView  
 使用 <xref:System.Windows.Controls.ItemsControl.Items%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性为控件指定项 <xref:System.Windows.Controls.ListView> 。 下面的示例将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性设置为一个被调用的数据集合 `EmployeeInfoDataSource` 。  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 在中 <xref:System.Windows.Controls.GridView> ， <xref:System.Windows.Controls.GridViewColumn> 对象将绑定到指定的数据字段。 下面的示例 <xref:System.Windows.Controls.GridViewColumn> 通过为属性指定，将对象绑定到数据字段 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 您还可以指定 <xref:System.Windows.Data.Binding> 作为 <xref:System.Windows.DataTemplate> 定义的一部分，您可以使用该定义来对列中的单元格进行样式。 在下面的示例中， <xref:System.Windows.DataTemplate> 用来标识的将 <xref:System.Windows.ResourceKey> 为设置 <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn> 。 请注意，此示例未定义， <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 因为这样做会重写指定的绑定 <xref:System.Windows.DataTemplate> 。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>为实现 GridView 的 ListView 设置样式  
 <xref:System.Windows.Controls.ListView>控件包含 <xref:System.Windows.Controls.ListViewItem> 对象，这些对象表示显示的数据项。 可使用以下属性定义数据项的内容和样式：  
  
- 在 <xref:System.Windows.Controls.ListView> 控件上，使用 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> 和 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 属性。  
  
- 在 <xref:System.Windows.Controls.ListViewItem> 控件上，使用 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> 属性。  
  
 若要避免中的单元格之间的对齐问题 <xref:System.Windows.Controls.GridView> ，请不要使用 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 设置属性或添加影响中项的宽度的内容 <xref:System.Windows.Controls.ListView> 。 例如，在中设置属性时，可能会出现对齐问题 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 。 若要指定属性或定义影响中的项的宽度的内容 <xref:System.Windows.Controls.GridView> ，请使用 <xref:System.Windows.Controls.GridView> 类及其相关类的属性，如 <xref:System.Windows.Controls.GridViewColumn> 。  
  
 有关如何使用 <xref:System.Windows.Controls.GridView> 及其支持类的详细信息，请参阅[GridView 概述](gridview-overview.md)。  
  
 如果 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 为 <xref:System.Windows.Controls.ListView> 控件定义，并定义 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> ，则必须在样式中包含，以便 <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 能够正常工作。  
  
 不要将 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 属性用于 <xref:System.Windows.Controls.ListView> 通过使用显示的内容 <xref:System.Windows.Controls.GridView> 。 若要指定的列中的内容对齐方式 <xref:System.Windows.Controls.GridView> ，请定义 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>共享同一视图模式  
 两个 <xref:System.Windows.Controls.ListView> 控件不能同时共享同一个视图模式。 如果尝试使用与多个控件相同的视图模式，则 <xref:System.Windows.Controls.ListView> 会出现异常。  
  
 若要指定可以同时使用多个视图模式 <xref:System.Windows.Controls.ListView> ，请使用模板或样式。
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>创建自定义视图模式  
 自定义的视图（如） <xref:System.Windows.Controls.GridView> 派生自 <xref:System.Windows.Controls.ViewBase> 抽象类，该类提供了用于显示作为对象表示的数据项的工具 <xref:System.Windows.Controls.ListViewItem> 。
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView 概述](gridview-overview.md)
- [操作指南主题](listview-how-to-topics.md)
- [控制](../advanced/optimizing-performance-controls.md)
