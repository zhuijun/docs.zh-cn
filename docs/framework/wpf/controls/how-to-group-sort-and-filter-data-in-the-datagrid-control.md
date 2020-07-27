---
title: 如何：在 DataGrid 控件中对数据进行分组、排序和筛选
description: 了解如何将 Windows Presentation Foundation DataGrid 控件绑定到支持在视图中对数据进行分组、排序和筛选的 CollectionView。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
ms.openlocfilehash: 072e5a104a91faa40bb54f2a3fc4ed6188e1112e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167674"
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a>如何：在 DataGrid 控件中对数据进行分组、排序和筛选

通常， <xref:System.Windows.Controls.DataGrid> 通过对数据进行分组、排序和筛选来以不同的方式查看数据是非常有用的。 若要对中的数据进行分组、排序和筛选 <xref:System.Windows.Controls.DataGrid> ，请将其绑定到 <xref:System.Windows.Data.CollectionView> 支持这些函数的。 然后，你可以在中处理数据， <xref:System.Windows.Data.CollectionView> 而不会影响基础数据源数据。 集合视图中的更改会反映在 <xref:System.Windows.Controls.DataGrid> 用户界面（UI）中。

<xref:System.Windows.Data.CollectionView>类为实现接口的数据源提供了分组和排序功能 <xref:System.Collections.IEnumerable> 。 <xref:System.Windows.Data.CollectionViewSource>利用类，您可以 <xref:System.Windows.Data.CollectionView> 从 XAML 中设置的属性。

在此示例中，对象的集合 `Task` 绑定到 <xref:System.Windows.Data.CollectionViewSource> 。 用作的 <xref:System.Windows.Data.CollectionViewSource> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> 。 分组、排序和筛选是在上执行的， <xref:System.Windows.Data.CollectionViewSource> 并显示在 <xref:System.Windows.Controls.DataGrid> UI 中。

![DataGrid 中的分组数据](././media/wpf-datagridgroups.png "WPF_DataGridGroups")DataGrid 中的分组数据

## <a name="using-a-collectionviewsource-as-an-itemssource"></a>使用 CollectionViewSource 作为 System.windows.controls.itemscontrol.itemssource

若要对控件中的数据进行分组、排序和筛选 <xref:System.Windows.Controls.DataGrid> ，请将绑定 <xref:System.Windows.Controls.DataGrid> 到 <xref:System.Windows.Data.CollectionView> 支持这些函数的。 在此示例中，将 <xref:System.Windows.Controls.DataGrid> 绑定到为 <xref:System.Windows.Data.CollectionViewSource> 对象的提供这些函数的 <xref:System.Collections.Generic.List%601> `Task` 。

### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a>将 DataGrid 绑定到 CollectionViewSource

1. 创建实现接口的数据集合 <xref:System.Collections.IEnumerable> 。

    如果使用 <xref:System.Collections.Generic.List%601> 创建集合，则应创建一个继承自的新类， <xref:System.Collections.Generic.List%601> 而不是实例化实例 <xref:System.Collections.Generic.List%601> 。 这使您可以将数据绑定到 XAML 中的集合。

    > [!NOTE]
    > 集合中的对象必须实现更改的 <xref:System.ComponentModel.INotifyPropertyChanged> 接口和接口，以便 <xref:System.ComponentModel.IEditableObject> <xref:System.Windows.Controls.DataGrid> 正确响应属性更改和编辑。 有关详细信息，请参阅[实现属性更改通知](../data/how-to-implement-property-change-notification.md)。

    [!code-csharp[DataGrid_GroupSortFilter#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
    [!code-vb[DataGrid_GroupSortFilter#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]

2. 在 XAML 中，创建集合类的实例并设置[X：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)。

3. 在 XAML 中，创建类的实例 <xref:System.Windows.Data.CollectionViewSource> ，设置[x：Key 指令](../../../desktop-wpf/xaml-services/xkey-directive.md)，并将集合类的实例设置为 <xref:System.Windows.Data.CollectionViewSource.Source%2A> 。

    [!code-xaml[DataGrid_GroupSortFilter#201](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]

4. 创建类的实例 <xref:System.Windows.Controls.DataGrid> ，并将 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 属性设置为 <xref:System.Windows.Data.CollectionViewSource> 。

    [!code-xaml[DataGrid_GroupSortFilter#002](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]

5. 若要 <xref:System.Windows.Data.CollectionViewSource> 从代码访问，请使用 <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> 方法获取对的引用 <xref:System.Windows.Data.CollectionViewSource> 。

    [!code-csharp[DataGrid_GroupSortFilter#102](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
    [!code-vb[DataGrid_GroupSortFilter#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]

## <a name="grouping-items-in-a-datagrid"></a>对 DataGrid 中的项进行分组

若要指定如何在中对项进行分组 <xref:System.Windows.Controls.DataGrid> ，可以使用 <xref:System.Windows.Data.PropertyGroupDescription> 类型对 "源" 视图中的项进行分组。

### <a name="to-group-items-in-a-datagrid-using-xaml"></a>使用 XAML 对 DataGrid 中的项进行分组

1. 创建一个 <xref:System.Windows.Data.PropertyGroupDescription> 指定要按其进行分组的属性的。 可以在 XAML 或代码中指定属性。

   1. 在 XAML 中，将设置 <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> 为要按其进行分组的属性的名称。

   2. 在 "代码" 中，将 "分组依据" 属性的名称传递到构造函数。

2. 将添加 <xref:System.Windows.Data.PropertyGroupDescription> 到 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> 集合中。

3. 向集合中添加的其他实例， <xref:System.Windows.Data.PropertyGroupDescription> <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 以添加更多级别的分组。

    [!code-xaml[DataGrid_GroupSortFilter#012](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]
    [!code-csharp[DataGrid_GroupSortFilter#112](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
    [!code-vb[DataGrid_GroupSortFilter#112](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]

4. 若要删除组，请 <xref:System.Windows.Data.PropertyGroupDescription> 从集合中删除 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。

5. 若要删除所有组，请调用 <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> 集合的方法 <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> 。

    [!code-csharp[DataGrid_GroupSortFilter#114](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
    [!code-vb[DataGrid_GroupSortFilter#114](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]

当项在中分组后 <xref:System.Windows.Controls.DataGrid> ，您可以定义一个 <xref:System.Windows.Controls.GroupStyle> 指定每个组的外观的。 <xref:System.Windows.Controls.GroupStyle>通过将其添加到 DataGrid 的集合来应用 <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> 。 如果有多个级别的分组，则可以对每个组级别应用不同的样式。 样式按其定义顺序进行应用。 例如，如果您定义两种样式，则第一个样式将应用于顶层行组。 第二个样式将应用于第二级和下的所有行组。 的 <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.GroupStyle> 是 <xref:System.Windows.Data.CollectionViewGroup> 组所表示的。

### <a name="to-change-the-appearance-of-row-group-headers"></a>更改行组标题的外观

1. 创建 <xref:System.Windows.Controls.GroupStyle> 用于定义行组外观的。

2. 将放入 <xref:System.Windows.Controls.GroupStyle> `<DataGrid.GroupStyle>` 标记中。

    [!code-xaml[DataGrid_GroupSortFilter#003](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]

## <a name="sorting-items-in-a-datagrid"></a>对 DataGrid 中的项进行排序

若要指定如何在中对项进行排序 <xref:System.Windows.Controls.DataGrid> ，可以使用 <xref:System.ComponentModel.SortDescription> 类型对 "源" 视图中的项进行排序。

### <a name="to-sort-items-in-a-datagrid"></a>对 DataGrid 中的项进行排序

1. 创建一个 <xref:System.ComponentModel.SortDescription> ，它指定要按其排序的属性。 可以在 XAML 或代码中指定属性。

    1. 在 XAML 中，将设置 <xref:System.ComponentModel.SortDescription.PropertyName%2A> 为要作为排序依据的属性的名称。

    2. 在代码中，传递要排序的属性的名称，并传递 <xref:System.ComponentModel.ListSortDirection> 给构造函数。

2. 将添加 <xref:System.ComponentModel.SortDescription> 到 <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> 集合中。

3. 向集合中添加的其他实例 <xref:System.ComponentModel.SortDescription> <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> ，以按其他属性排序。

    [!code-xaml[DataGrid_GroupSortFilter#011](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]
    [!code-csharp[DataGrid_GroupSortFilter#211](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
    [!code-vb[DataGrid_GroupSortFilter#211](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]

## <a name="filtering-items-in-a-datagrid"></a>筛选 DataGrid 中的项

若要使用筛选中的项 <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Data.CollectionViewSource> ，请在事件的处理程序中提供筛选逻辑 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。

### <a name="to-filter-items-in-a-datagrid"></a>筛选 DataGrid 中的项

1. 为事件添加处理程序 <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> 。

2. 在 <xref:System.Windows.Data.CollectionViewSource.Filter> 事件处理程序中，定义筛选逻辑。

    此筛选器将在每次刷新视图时应用。

    [!code-xaml[DataGrid_GroupSortFilter#013](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]
    [!code-csharp[DataGrid_GroupSortFilter#113](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
    [!code-vb[DataGrid_GroupSortFilter#113](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]

或者，你可以 <xref:System.Windows.Controls.DataGrid> 通过创建提供筛选逻辑的方法并设置 <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> 属性以应用筛选器，来筛选中的项。 若要查看此方法的示例，请参阅[在视图中筛选数据](../data/how-to-filter-data-in-a-view.md)。

## <a name="example"></a>示例

下面的示例演示如何对中的数据进行分组、排序和筛选， `Task` <xref:System.Windows.Data.CollectionViewSource> 以及如何在中显示分组、排序和筛选后的 `Task` 数据 <xref:System.Windows.Controls.DataGrid> 。 用作的 <xref:System.Windows.Data.CollectionViewSource> <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> 。 分组、排序和筛选是在上执行的， <xref:System.Windows.Data.CollectionViewSource> 并显示在 <xref:System.Windows.Controls.DataGrid> UI 中。

若要测试此示例，需调整 DGGroupSortFilterExample 名称，使其与项目名称匹配。 如果使用 Visual Basic，则需要将的类名称更改为 <xref:System.Windows.Window> 以下项。

`<Window x:Class="MainWindow"`

[!code-xaml[DataGrid_GroupSortFilter#000](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]
[!code-csharp[DataGrid_GroupSortFilter#100](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
[!code-vb[DataGrid_GroupSortFilter#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]

## <a name="see-also"></a>另请参阅

- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [创建和绑定到 ObservableCollection](../data/how-to-create-and-bind-to-an-observablecollection.md)
- [筛选视图中的数据](../data/how-to-filter-data-in-a-view.md)
- [在视图中对数据进行排序](../data/how-to-sort-data-in-a-view.md)
- [在 XAML 中使用视图对数据进行排序和分组](../data/how-to-sort-and-group-data-using-a-view-in-xaml.md)
