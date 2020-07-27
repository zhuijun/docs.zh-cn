---
title: GridView 概述
description: 了解 Windows Presentation Foundation ListView 控件的样式和模板。 修改 System.windows.controls.controltemplate>，为控件指定独特的外观。
ms.date: 03/30/2017
helpviewer_keywords:
- GridView view mode [WPF]
- ListView controls [WPF], GridView view mode
- controls [WPF], ListView
ms.assetid: b2d02267-32b3-40ce-8e9f-06972d8749d9
ms.openlocfilehash: 02a2182ef1fc893107e434f431b9fbe0b3fbcd08
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165929"
---
# <a name="gridview-overview"></a>GridView 概述
<xref:System.Windows.Controls.GridView>视图模式是控件的一个视图模式 <xref:System.Windows.Controls.ListView> 。 <xref:System.Windows.Controls.GridView>类及其支持类使你和你的用户可以在通常使用按钮作为交互式列标题的表中查看项集合。 本主题介绍 <xref:System.Windows.Controls.GridView> 类并概述其用法。  

<a name="DefiningaListViewthatusesGridViewView"></a>
## <a name="what-is-a-gridview-view"></a>什么是 GridView 视图？  
 <xref:System.Windows.Controls.GridView>视图模式通过将数据字段绑定到列并通过显示列标题来标识字段，来显示数据项的列表。 默认 <xref:System.Windows.Controls.GridView> 样式实现按钮作为列标题。 通过使用列标题的按钮，你可以实现重要的用户交互功能;例如，用户可以单击列标题，按 <xref:System.Windows.Controls.GridView> 特定列的内容对数据进行排序。  
  
> [!NOTE]
> <xref:System.Windows.Controls.GridView>用于列标题的按钮控件派生自 <xref:System.Windows.Controls.Primitives.ButtonBase> 。  
  
 下图显示内容的 <xref:System.Windows.Controls.GridView> 视图 <xref:System.Windows.Controls.ListView> 。  

 ![显示 ListView 内容的 GridView 视图的屏幕截图。](./media/gridview-overview/styled-listview-content.png)  
  
 <xref:System.Windows.Controls.GridView>列由对象表示 <xref:System.Windows.Controls.GridViewColumn> ，这些对象可以根据其内容自动调整大小。 您也可以根据需要将显式设置 <xref:System.Windows.Controls.GridViewColumn> 为特定宽度。 可通过拖动列标题之间的手柄重设列的大小。 你还可以动态添加、移除、替换和重新排列列，因为此功能已内置于中 <xref:System.Windows.Controls.GridView> 。 但是， <xref:System.Windows.Controls.GridView> 不能直接更新它所显示的数据。  
  
 下面的示例演示如何定义 <xref:System.Windows.Controls.GridView> 用于显示员工数据的。 在此示例中， <xref:System.Windows.Controls.ListView> 将定义 `EmployeeInfoDataSource` 为 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 。 将 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> <xref:System.Windows.Controls.GridViewColumn> 内容绑定到数据类别的属性定义 `EmployeeInfoDataSource` 。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 下图显示了上一示例创建的表格。 GridView 控件显示 System.windows.controls.itemscontrol.itemssource 对象中的数据：

 ![显示带有 GridView 输出的 ListView 的屏幕截图。](./media/gridview-overview/listview-gridview-output.jpg)  
  
<a name="GridViewLayoutandStyle"></a>
## <a name="gridview-layout-and-style"></a>GridView 布局和样式  
 的列单元格和列标题 <xref:System.Windows.Controls.GridViewColumn> 具有相同的宽度。 默认情况下，每一列都根据其内容来调整宽度大小。 也可以选择将列设置为固定宽度。  
  
 相关的数据内容显示在水平行中。 例如，在上图中，每个员工的姓氏、名字和 ID 号显示为一组，因为它们显示在一个水平行中。  
  
<a name="DefiningandStylingColumnsinaGridView"></a>
### <a name="defining-and-styling-columns-in-a-gridview"></a>在 GridView 中定义列并设置其样式  
 定义要在中显示的数据字段时，请 <xref:System.Windows.Controls.GridViewColumn> 使用 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> 、 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 或 <xref:System.Windows.Controls.GridViewColumn.CellTemplateSelector%2A> 属性。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>属性优先于任何一个模板属性。  
  
 若要指定的列中的内容对齐方式 <xref:System.Windows.Controls.GridView> ，请定义 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 。 不要将 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> 和 <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> 属性用于 <xref:System.Windows.Controls.ListView> 通过使用显示的内容 <xref:System.Windows.Controls.GridView> 。  
  
 若要指定列标题的模板和样式属性，请使用 <xref:System.Windows.Controls.GridView> 、 <xref:System.Windows.Controls.GridViewColumn> 和 <xref:System.Windows.Controls.GridViewColumnHeader> 类。 有关详细信息，请参阅 [GridView 列标题的样式和模板概述](gridview-column-header-styles-and-templates-overview.md)。  
  
<a name="AddingVisualElementstoaGridViewView"></a>
### <a name="adding-visual-elements-to-a-gridview"></a>将可视元素添加到 GridView  
 若要将视觉元素（如 <xref:System.Windows.Controls.CheckBox> 和 <xref:System.Windows.Controls.Button> 控件）添加到 <xref:System.Windows.Controls.GridView> 视图模式，请使用模板或样式。  
  
 如果将可视元素显式定义为数据项，则它在中只能出现一次 <xref:System.Windows.Controls.GridView> 。 之所以存在此限制，是因为元素只能有一个父级，因此，只能在可视化树中出现一次。  
  
<a name="StylingRowsinaGridViewView"></a>
### <a name="styling-rows-in-a-gridview"></a>设置 GridView 中的行的样式  
 使用 <xref:System.Windows.Controls.GridViewRowPresenter> 和 <xref:System.Windows.Controls.GridViewHeaderRowPresenter> 类来设置和显示的行 <xref:System.Windows.Controls.GridView> 。 有关如何在视图模式下样式行的示例 <xref:System.Windows.Controls.GridView> ，请参阅在[实现 GridView 的 ListView 中为行样式](how-to-style-a-row-in-a-listview-that-implements-a-gridview.md)。  
  
<a name="AlignmentIssuesWhenUsingItemContainerStyle"></a>
### <a name="alignment-issues-when-you-use-itemcontainerstyle"></a>使用 ItemContainerStyle 时的对齐问题  
 若要防止列标题和单元格之间出现对齐问题，请不要设置属性或指定一个对中的项的宽度产生影响的模板 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 。 例如，不要设置 <xref:System.Windows.FrameworkElement.Margin%2A> 属性，或指定 <xref:System.Windows.Controls.ControlTemplate> ，将添加 <xref:System.Windows.Controls.CheckBox> 到 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> 在控件上定义的 <xref:System.Windows.Controls.ListView> 。 而是在定义视图模式的类上直接指定影响列宽的属性和模板 <xref:System.Windows.Controls.GridView> 。  
  
 例如，若要 <xref:System.Windows.Controls.CheckBox> 在视图模式下将添加到行中 <xref:System.Windows.Controls.GridView> ，请将添加 <xref:System.Windows.Controls.CheckBox> 到 <xref:System.Windows.DataTemplate> ，然后将 <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> 属性设置为 <xref:System.Windows.DataTemplate> 。  
  
<a name="InteractingwithaGridViewControl"></a>
## <a name="user-interactions-with-a-gridview"></a>与 GridView 的用户交互  
 <xref:System.Windows.Controls.GridView>在应用程序中使用时，用户可以与进行交互，并修改的格式设置 <xref:System.Windows.Controls.GridView> 。 例如，用户可以对列重新排序、重设列的大小、选择表中的项以及滚动查看内容。 还可定义当用户单击列标题按钮时响应的事件处理程序。 事件处理程序可以执行一些操作，例如，根据列的内容对中显示的数据进行排序 <xref:System.Windows.Controls.GridView> 。  
  
 以下列表更详细地讨论了使用 <xref:System.Windows.Controls.GridView> 进行用户交互的功能：  
  
- **使用拖放方法对列重新排序。**  
  
     用户可以 <xref:System.Windows.Controls.GridView> 通过在列标题上按下鼠标左键，然后将该列拖到新位置，对中的列重新排序。 当用户拖动列标题时，将显示标题的浮动版本以及显示列的插入位置的黑色实线。  
  
     如果要修改标题的浮动版本的默认样式，请在 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> 属性设置为时，指定要触发的类型的 <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating> 。 有关详细信息，请参阅[为拖动的 GridView 列标题创建样式](how-to-create-a-style-for-a-dragged-gridview-column-header.md)。  
  
- **根据列的内容重设其大小。**  
  
     用户可双击列标题右侧的手柄来根据列的内容重设其大小。  
  
    > [!NOTE]
    > 可以将属性设置 <xref:System.Windows.Controls.GridViewColumn.Width%2A> 为， `Double.NaN` 以生成相同的效果。  
  
- **选择行项目。**  
  
     用户可以选择中的一个或多个项 <xref:System.Windows.Controls.GridView> 。  
  
     如果要更改 <xref:System.Windows.Style> 选定项的，请参阅[使用触发器为 ListView 中的选定项进行样式](how-to-use-triggers-to-style-selected-items-in-a-listview.md)。  
  
- **滚动查看最初未显示在屏幕上的内容。**  
  
     如果的大小不足 <xref:System.Windows.Controls.GridView> 以显示所有项，用户可以使用控件提供的滚动条水平或垂直滚动 <xref:System.Windows.Controls.ScrollViewer> 。 <xref:System.Windows.Controls.Primitives.ScrollBar>如果所有内容在特定方向上都可见，则隐藏。 列标题不会随着垂直滚动条滚动，但可水平滚动。  
  
- **通过单击列标题按钮与列交互。**  
  
     如果提供了排序算法，则当用户单击列标题按钮时，可以对列中显示的数据进行排序。  
  
     您可以处理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 列标题按钮的事件，以便提供排序算法等功能。 若要处理 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 单个列标题的事件，请在上设置一个事件处理程序 <xref:System.Windows.Controls.GridViewColumnHeader> 。 若要设置用于处理所有列标题的事件的事件处理程序 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ，请在控件上设置处理程序 <xref:System.Windows.Controls.ListView> 。  
  
<a name="Obtaining_Other_Custom_Views"></a>
## <a name="obtaining-other-custom-views"></a>获取其他自定义视图  
 <xref:System.Windows.Controls.GridView>派生自 <xref:System.Windows.Controls.ViewBase> 抽象类的类只是类的可能的视图模式之一 <xref:System.Windows.Controls.ListView> 。 您可以 <xref:System.Windows.Controls.ListView> 通过从类派生来为创建其他自定义视图 <xref:System.Windows.Controls.ViewBase> 。 有关自定义视图模式的示例，请参阅[为 ListView 创建自定义视图模式](how-to-create-a-custom-view-mode-for-a-listview.md)。  
  
<a name="GridViewSupportingClasses"></a>
## <a name="gridview-supporting-classes"></a>GridView 支持类  
 以下类支持 <xref:System.Windows.Controls.GridView> 视图模式。  
  
- <xref:System.Windows.Controls.GridViewColumn>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GridViewRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
  
- <xref:System.Windows.Controls.GridViewColumnCollection>  
  
- <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Controls.GridViewColumn>
- <xref:System.Windows.Controls.GridViewColumnHeader>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.ViewBase>
- [ListView 概述](listview-overview.md)
- [在标题获得单击时对 GridView 列进行排序](how-to-sort-a-gridview-column-when-a-header-is-clicked.md)
- [操作指南主题](listview-how-to-topics.md)
