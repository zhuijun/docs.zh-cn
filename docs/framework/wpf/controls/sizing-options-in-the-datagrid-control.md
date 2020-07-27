---
title: DataGrid 控件中的调整大小选项
description: 了解如何设置 Windows Presentation Foundation DataGrid 控件中的单个行和列，使其大小调整到其内容或特定值。
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 0f10e385cbf18a26989614363ca6cd9f92bc83ec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164741"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid 控件中的调整大小选项
可以使用各种选项来控制 <xref:System.Windows.Controls.DataGrid> 大小本身。 <xref:System.Windows.Controls.DataGrid>和中的单个行和列 <xref:System.Windows.Controls.DataGrid> 可设置为自动到其内容的大小，也可以设置为特定值。 默认情况下， <xref:System.Windows.Controls.DataGrid> 将会放大和缩小以适应其内容大小。  
  
## <a name="sizing-the-datagrid"></a>调整 DataGrid 大小  
  
### <a name="cautions-when-using-automatic-sizing"></a>使用自动调整大小时的注意事项  
 默认情况下，的 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 属性 <xref:System.Windows.Controls.DataGrid> 设置为 <xref:System.Double.NaN?displayProperty=nameWithType> （XAML 中的 " `Auto` "），并且 <xref:System.Windows.Controls.DataGrid> 将调整为其内容的大小。  
  
 当放置在不限制其子级大小的容器中时（例如 <xref:System.Windows.Controls.Canvas> 或 <xref:System.Windows.Controls.StackPanel> ）， <xref:System.Windows.Controls.DataGrid> 将延伸到超出容器的可见边界，且不会显示滚动条。 此条件有可用性和性能方面的影响。  
  
 绑定到数据集时，如果 <xref:System.Windows.FrameworkElement.Height%2A> 的 <xref:System.Windows.Controls.DataGrid> 不受限制，它将继续为绑定数据集中的每个数据项添加一行。 这可能会导致 <xref:System.Windows.Controls.DataGrid> 添加行时，在应用程序的可见边界之外增长。 <xref:System.Windows.Controls.DataGrid>在这种情况下，将不会显示滚动条，因为它 <xref:System.Windows.FrameworkElement.Height%2A> 将继续增长以容纳新行。  
  
 为中的每行创建一个对象 <xref:System.Windows.Controls.DataGrid> 。 如果你使用的是一个大型数据集，并且你允许 <xref:System.Windows.Controls.DataGrid> 自动调整其大小，则创建大量对象可能会影响你的应用程序的性能。  
  
 若要在使用大型数据集时避免这些问题，建议您专门设置的，或将 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Controls.DataGrid> 其放在将限制其的容器中 <xref:System.Windows.FrameworkElement.Height%2A> ，例如 <xref:System.Windows.Controls.Grid> 。 当受到 <xref:System.Windows.FrameworkElement.Height%2A> 限制时， <xref:System.Windows.Controls.DataGrid> 将仅创建将在其指定范围内容纳的行， <xref:System.Windows.FrameworkElement.Height%2A> 并根据需要回收这些行以显示新数据。  
  
### <a name="setting-the-datagrid-size"></a>设置 DataGrid 大小  
 <xref:System.Windows.Controls.DataGrid>可以设置为指定边界内的自动大小，也可以 <xref:System.Windows.Controls.DataGrid> 设置为特定大小。 下表显示可以设置以控制大小的属性 <xref:System.Windows.Controls.DataGrid> 。  
  
|属性|说明|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|设置的特定高度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|设置的高度上限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>将垂直增长，直到达到此高度。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|设置的高度的下限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>将垂直收缩，直到达到此高度。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|设置的特定宽度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|设置的宽度的上限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>将水平增长，直到达到此宽度。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|设置的宽度的下限 <xref:System.Windows.Controls.DataGrid> 。 <xref:System.Windows.Controls.DataGrid>将水平收缩，直到达到此宽度。|  
  
## <a name="sizing-rows-and-row-headers"></a>调整行和行标题的大小  
  
### <a name="datagrid-rows"></a>DataGrid 行  
 默认情况下， <xref:System.Windows.Controls.DataGrid> 行的 <xref:System.Windows.FrameworkElement.Height%2A> 属性设置为 <xref:System.Double.NaN?displayProperty=nameWithType> （ `Auto` 在 XAML 中为 ""），行高将扩展为其内容的大小。 <xref:System.Windows.Controls.DataGrid>可以通过设置属性来指定中所有行的高度 <xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType> 。 用户可以通过拖动行标题分隔线来更改行高。  
  
### <a name="datagrid-row-headers"></a>DataGrid 行标题  
 若要显示行标题， <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 属性必须设置为 <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType> 。 默认情况下，将显示行标题，并自动调整其大小以适应其内容。 可以通过设置属性，将行标题指定为特定的宽度 <xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType> 。  
  
## <a name="sizing-columns-and-column-headers"></a>调整列和列标题的大小  
  
### <a name="datagrid-columns"></a>DataGrid 列  
 <xref:System.Windows.Controls.DataGrid>使用和结构的值 <xref:System.Windows.Controls.DataGridLength> <xref:System.Windows.Controls.DataGridLengthUnitType> 来指定绝对或自动调整大小模式。  
  
 下表显示了结构提供的值 <xref:System.Windows.Controls.DataGridLengthUnitType> 。  
  
|名称|说明|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|默认的自动调整大小模式根据 <xref:System.Windows.Controls.DataGrid> 单元格和列标题的内容调整列的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|基于单元格的自动调整大小模式根据 <xref:System.Windows.Controls.DataGrid> 列中单元格的内容（不包括列标题）来调整列的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|基于标头的自动调整大小模式 <xref:System.Windows.Controls.DataGrid> 仅基于列标题的内容调整列的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|基于像素的大小调整模式 <xref:System.Windows.Controls.DataGrid> 基于提供的数值调整列的大小。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星形调整大小模式用于按加权比例分布可用空间。<br /><br /> 在 XAML 中，星号值表示为 n *，其中 n 表示数值。 1与 \* 等效 \* 。 例如，如果中的两个列的 <xref:System.Windows.Controls.DataGrid> 宽度为 \* 和 2 \* ，则第一列将接收一个部分可用空间，第二列将接收可用空间的两个部分。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>类可用于在数值或字符串值与值之间转换数据 <xref:System.Windows.Controls.DataGridLength> 。  
  
 默认情况下， <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> 属性设置为 <xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A> ， <xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType> 属性设置为 <xref:System.Windows.Controls.DataGridLength.Auto%2A> 。 当调整大小模式设置为 <xref:System.Windows.Controls.DataGridLength.Auto%2A> 或时 <xref:System.Windows.Controls.DataGridLength.SizeToCells%2A> ，列会增长到其最宽可见内容的宽度。 滚动时，如果大于当前列大小的内容滚动到视图中，则这些大小调整模式将导致列展开。 在内容滚动出视图后，列将不会收缩。  
  
 还可以将中的列 <xref:System.Windows.Controls.DataGrid> 设置为仅在指定边界内自动调整大小，或者可以将列设置为特定大小。 下表显示了可设置为控制列大小的属性。  
  
|属性|说明|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|设置中所有列的上限 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|设置单个列的上限。 重写 <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|设置中所有列的下限 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|设置单个列的下限。 重写 <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|设置中所有列的特定宽度 <xref:System.Windows.Controls.DataGrid> 。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|设置单个列的特定宽度。 重写 <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>。|  
  
### <a name="datagrid-column-headers"></a>DataGrid 列标题  
 默认情况下， <xref:System.Windows.Controls.DataGrid> 将显示列标题。 若要隐藏列标题，则 <xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A> 必须将属性设置为 <xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType> 或 <xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType> 。 默认情况下，当显示列标题时，它们会自动调整大小以适应其内容。 可以通过设置属性来为列标题提供特定的高度 <xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType> 。  
  
### <a name="resizing-with-the-mouse"></a>用鼠标调整大小  
 用户可以 <xref:System.Windows.Controls.DataGrid> 通过拖动行标题或列标题分隔线来调整行和列的大小。 <xref:System.Windows.Controls.DataGrid>还支持通过双击行标题或列标题分隔符来自动调整行和列的大小。 若要防止用户调整特定列的大小，请将 <xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType> 单个列的属性设置为 `false` 。 若要防止用户调整所有列的大小，请将 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType> 属性设置为 `false` 。 若要防止用户调整所有行的大小，请将 <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType> 属性设置为 `false` 。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
