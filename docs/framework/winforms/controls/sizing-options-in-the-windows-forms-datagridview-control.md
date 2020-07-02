---
title: DataGridView 控件中的调整大小选项
description: 了解 Windows 窗体 DataGridView 控件中的调整大小选项。 DataGridView 行、列和标头会因不同的匹配项而改变大小。
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: 8ddf72c412db74df35bc3f035ff05d1e7e9738d1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85613717"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows 窗体 DataGridView 控件中的大小调整选项
<xref:System.Windows.Forms.DataGridView>由于发生了许多不同的情况，行、列和标头可能会改变大小。 下表显示了这些情况。  
  
|出现次数|描述|  
|----------------|-----------------|  
|用户调整大小|用户可以通过拖动或双击行、列或标题分隔线来调整大小。|  
|控件调整大小|在列填充模式下，当控件的宽度发生变化时，列宽将更改;例如，当控件停靠在其父窗体上并且用户调整窗体的大小时。|  
|单元格值更改|在基于内容的自动调整大小模式下，调整大小以适应新的显示值。|  
|方法调用|基于编程内容的大小调整使你可以基于方法调用时的单元格值进行机会调整大小。|  
|属性设置|你还可以设置特定的高度和宽度值。|  
  
 默认情况下，将启用用户大小调整，禁用自动调整大小，并剪裁宽度超过其列的单元值。  
  
 下表显示了可用于调整默认行为或使用特定大小调整选项实现特定效果的方案。  
  
|方案|实现|  
|--------------|--------------------|  
|使用列填充模式，在占用整个控件宽度的列中显示大小类似的数据，而不显示水平滚动条。|将 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。|  
|使用具有不同大小的显示值的列填充模式。|将 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 通过设置列 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 属性或 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 在使用数据填充控件后调用控件方法来初始化相对列宽。|  
|使用具有不同重要性的值的列填充模式。|将 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 属性设置为 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>。 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>为必须始终显示某些数据的列设置较大的值，或者为特定列使用填充模式之外的调整大小选项。|  
|使用列填充模式可避免显示控件背景。|将 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 最后一列的属性设置为 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> ，并对其他列使用其他调整大小选项。 如果其他列使用太多的可用空间，请设置 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> 最后一列的属性。|  
|显示固定宽度的列，例如图标或 ID 列。|<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> 对于列，将设置为和 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A> <xref:System.Windows.Forms.DataGridViewTriState.False> 。 通过设置 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> 属性或 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A> 在使用数据填充控件后调用控件方法来初始化其宽度。|  
|当单元格内容更改时自动调整大小，以避免剪辑和优化空间的使用。|将自动调整大小属性设置为一个值，该值表示基于内容的大小调整模式。 若要避免在处理大量数据时出现性能损失，请使用只计算显示行的调整大小模式。|  
|调整大小以适合显示行中的值，以避免在使用多行时出现性能下降。|使用自动大小调整或编程大小调整模式枚举值。 若要在滚动时调整大小以适应新显示的行中的值，请在事件处理程序中调用调整大小方法 <xref:System.Windows.Forms.DataGridView.Scroll> 。 若要自定义用户双击大小，以便仅显示的行中的值确定新大小，请在 <xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick> 或事件处理程序中调用调整大小方法 <xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick> 。|  
|仅在特定时间调整大小以适合单元格内容，以避免性能下降或启用用户调整大小。|在事件处理程序中调用基于内容的大小调整方法。 例如，使用 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 事件在绑定后初始化大小，并处理 <xref:System.Windows.Forms.DataGridView.CellValidated> 或 <xref:System.Windows.Forms.DataGridView.CellValueChanged> 事件以调整大小以对绑定数据源中的用户编辑或更改进行补偿。|  
|调整多行单元格内容的行高。|确保列宽适用于显示文本段落，并使用自动或基于内容的编程行大小调整来调整高度。 还应确保使用单元样式值显示具有多行内容的单元格 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> <xref:System.Windows.Forms.DataGridViewTriState.True> 。<br /><br /> 通常，您将使用自动列大小调整模式来维护列宽，或在调整行高之前将其设置为特定宽度。|  
  
## <a name="resizing-with-the-mouse"></a>用鼠标调整大小  
 默认情况下，用户可以根据单元格值调整不使用自动调整大小模式的行、列和标头的大小。 若要防止用户调整其他模式（如列填充模式）的大小，请设置以下一个或多个 <xref:System.Windows.Forms.DataGridView> 属性：  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 还可以通过设置各个行或列的属性，防止用户调整它们的大小 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 。 默认情况下， <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 属性值基于 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A> 列的属性值和 <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A> 行的属性值。 但是，如果将显式设置 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 为 <xref:System.Windows.Forms.DataGridViewTriState.True> 或 <xref:System.Windows.Forms.DataGridViewTriState.False> ，则指定的值将覆盖该行或列的控件值。 设置 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 为 <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 以还原继承。  
  
 由于 <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 还原值继承，因此 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 属性永远不会返回 <xref:System.Windows.Forms.DataGridViewTriState.NotSet> 值，除非行或列尚未添加到 <xref:System.Windows.Forms.DataGridView> 控件中。 如果需要确定是否 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 继承行或列的属性值，请检查其 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 属性。 如果 <xref:System.Windows.Forms.DataGridViewElement.State%2A> 值包括 <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet> 标志，则 <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A> 不会继承属性值。  
  
## <a name="automatic-sizing"></a>自动调整大小  
 控件中有两种自动调整大小的类型 <xref:System.Windows.Forms.DataGridView> ：列填充模式和基于内容的自动调整大小。  
  
 列填充模式使控件中的可见列填充控件的显示区域的宽度。 有关此模式的详细信息，请参阅[Windows 窗体 DataGridView 控件中的列填充模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)。  
  
 您还可以配置行、列和标头以自动调整其大小以适应其单元格内容。 在这种情况下，只要单元格内容发生更改，就会发生大小调整。  
  
> [!NOTE]
> 如果使用虚拟模式在自定义数据缓存中维护单元值，则当用户编辑单元值时，将自动调整大小，但当你在事件处理程序外部更改缓存的值时，将不会发生这种情况 <xref:System.Windows.Forms.DataGridView.CellValuePushed> 。 在这种情况下，请调用 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> 方法来强制控件更新单元格的显示，并应用当前的自动调整大小模式。  
  
 如果对一个维度仅启用了基于内容的自动调整大小（即，对于行而不是列）或列（而不是行）， <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 则还会启用大小调整，只要其他维度发生变化。 例如，如果将行而不是列配置为自动调整大小并 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 启用，则用户可以拖动列分隔线来更改列的宽度，行高会自动调整，以便仍完全显示单元格内容。  
  
 如果将行和列配置为基于内容的自动调整大小并 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> 启用，则当 <xref:System.Windows.Forms.DataGridView> 单元格内容发生更改时，控件将调整大小，并将在计算新大小时使用理想的单元格高度与宽度的比率。  
  
 若要为标头和行以及不重写控件值的列配置大小调整模式，请设置以下一个或多个 <xref:System.Windows.Forms.DataGridView> 属性：  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 若要为个别列覆盖控件的列大小调整模式，请将其 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 属性设置为以外的值 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> 。 列的大小调整模式实际上由其 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> 属性确定。 此属性的值基于列的 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 属性值，除非该值为 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet> ，在这种情况下，将继承控件的 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> 值。  
  
 使用基于内容的自动调整大小，在处理大量数据时务必小心。 若要避免性能损失，请使用自动大小调整模式，这些模式仅基于显示的行计算大小，而不是分析控件中的每一行。 为了获得最佳性能，请改用编程大小调整，以便在特定时间（例如，在加载新数据后立即）调整大小。  
  
 基于内容的自动调整大小模式不会影响通过将行或列或属性设置为而隐藏的行、列或标头 <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> <xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> `false` 。 例如，如果某个列在自动调整大小以容纳大单元值之后隐藏，则隐藏列将不会更改其大小（如果删除包含大单元值的行）。 当可见性更改时不会进行自动调整大小，因此， <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> 将列属性更改回后， `true` 不会强制它根据其当前内容重新计算其大小。  
  
 基于编程内容的大小调整会影响行、列和标头，而不考虑它们的可见性。  
  
## <a name="programmatic-resizing"></a>以编程方式调整大小  
 禁用自动调整大小后，可以通过以下属性以编程方式设置行、列或标题的精确宽度或高度：  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 你还可以使用下列方法以编程方式调整行、列和标头的大小以适应其内容：  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 这些方法一次调整行、列或标头的大小，而不是将其配置为连续调整大小。 新大小将自动计算，以显示所有单元格内容而不进行剪辑。 但是，当你以编程方式调整具有属性值的列的大小时，将 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> 使用基于内容的计算宽度按比例调整列 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> 属性值，然后根据这些新比例计算实际的列宽，以便所有列都填充控件的可用显示区域。  
  
 以编程方式调整大小有助于避免连续调整大小时的性能下降。 它还可为用户可调整大小的行、列和标头以及列填充模式提供初始大小。  
  
 通常会在特定时间调用编程大小调整方法。 例如，可以在加载数据后立即以编程方式调整所有列的大小，也可以在修改特定单元格值后以编程方式调整特定行的大小。  
  
## <a name="customizing-content-based-sizing-behavior"></a>自定义基于内容的大小调整行为  
 可以在使用派生 <xref:System.Windows.Forms.DataGridView> 的单元格、行和列类型时，通过重写 <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType> 、 <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType> 或 <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType> 方法或通过在派生控件中调用受保护的调整大小方法重载 <xref:System.Windows.Forms.DataGridView> 来自定义大小调整行为。 受保护的调整大小方法重载设计为成对工作以实现理想的单元格高度与宽度的比率，以避免过于宽或高度的单元格。 例如，如果调用 `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)` 方法的重载 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A> 并 `false` 为参数传入值 <xref:System.Boolean> ，则重载将计算行中单元格的理想高度和宽度，但它只会调整行高。 然后，必须调用 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> 方法，将列宽调整为计算得出的理想。  
  
## <a name="content-based-sizing-options"></a>基于内容的大小调整选项  
 对于基于内容的大小调整，大小调整属性和方法使用的枚举具有相似的值。 使用这些值可以限制用于计算首选大小的单元格。 对于所有大小调整枚举，名称引用显示单元的值将其计算限制为显示的行中的单元格。 在处理大量行时，排除行有助于避免性能下降。 还可以将计算限制为标头或 nonheader 单元中的单元值。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [调整 Windows 窗体 DataGridView 控件中列和行的大小](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的列填充模式](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [如何：设置 Windows 窗体 DataGridView 控件的大小调整模式](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
