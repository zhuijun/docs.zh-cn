---
title: DataGridView 控件和 DataGrid 控件之间的差异
description: 了解 Windows 窗体 DataGridView 和 DataGrid 控件功能之间的不同之处，以及它们的体系结构之间的差异。
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174583"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Windows 窗体 DataGridView 控件和 DataGrid 控件之间的区别
<xref:System.Windows.Forms.DataGridView>控件是替换控件的新控件 <xref:System.Windows.Forms.DataGrid> 。 <xref:System.Windows.Forms.DataGridView>控件提供了许多控件中缺少的基本功能和高级功能 <xref:System.Windows.Forms.DataGrid> 。 此外，控件的体系结构 <xref:System.Windows.Forms.DataGridView> 使得扩展和自定义比控件更容易 <xref:System.Windows.Forms.DataGrid> 。  
  
 下表描述了控件中的一些主要功能，这些功能在控件中 <xref:System.Windows.Forms.DataGridView> 是不存在的 <xref:System.Windows.Forms.DataGrid> 。  
  
|DataGridView 控件功能|说明|  
|----------------------------------|-----------------|  
|多列类型|<xref:System.Windows.Forms.DataGridView>控件提供的内置列类型比控件更多 <xref:System.Windows.Forms.DataGrid> 。 这些列类型满足最常见方案的需求，但也比控件中的列类型更易于扩展或替换 <xref:System.Windows.Forms.DataGrid> 。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)。|  
|显示数据的多种方式|<xref:System.Windows.Forms.DataGrid>控件限制为显示来自外部数据源的数据。 <xref:System.Windows.Forms.DataGridView>不过，控件可以显示存储在控件中的未绑定数据、绑定数据源中的数据，或者将绑定和未绑定的数据组合在一起。 你还可以在控件中实现虚拟模式 <xref:System.Windows.Forms.DataGridView> ，以提供自定义数据管理。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的数据显示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)。|  
|自定义数据显示的多种方式|<xref:System.Windows.Forms.DataGridView>控件提供许多属性和事件，使您可以指定数据的格式和显示方式。 例如，您可以根据所包含的数据更改单元格、行和列的外观，也可以用另一种类型的等效数据替换一种数据类型的数据。 有关详细信息，请参阅[Windows 窗体 DataGridView 控件中的数据格式设置](data-formatting-in-the-windows-forms-datagridview-control.md)。|  
|用于更改单元格、行、列和标题外观和行为的多种选项|使用 <xref:System.Windows.Forms.DataGridView> 控件，可以通过多种方式处理单个网格组件。 例如，您可以冻结行和列以防止它们滚动;隐藏行、列和标头;更改行、列和标头大小的调整方式;更改用户做出选择的方式;和提供单个单元格、行和列的工具提示和快捷菜单。|  
  
 <xref:System.Windows.Forms.DataGrid>保留控件以实现向后兼容性和特殊需求。 几乎所有目的都应该使用 <xref:System.Windows.Forms.DataGridView> 控件。 控件中提供的唯一可用于 <xref:System.Windows.Forms.DataGrid> 控件的功能 <xref:System.Windows.Forms.DataGridView> 是一个控件中两个相关表中的信息的分层显示。 您必须使用两个 <xref:System.Windows.Forms.DataGridView> 控件显示主/从关系中的两个表中的信息。  
  
## <a name="upgrading-to-the-datagridview-control"></a>升级到 DataGridView 控件  
 如果现有应用程序 <xref:System.Windows.Forms.DataGrid> 在简单的数据绑定方案中使用控件，而没有自定义项，则只需将旧控件替换为新控件即可。 这两个控件都使用标准 Windows 窗体数据绑定体系结构，因此 <xref:System.Windows.Forms.DataGridView> 控件将显示绑定数据，无需其他配置。 但是，你可能希望通过将数据绑定到组件来利用数据绑定改进，然后可以将数据绑定 <xref:System.Windows.Forms.BindingSource> 到 <xref:System.Windows.Forms.DataGridView> 控件。 有关详细信息，请参阅[BindingSource Component](bindingsource-component.md)。  
  
 由于 <xref:System.Windows.Forms.DataGridView> 控件具有一个全新的体系结构，因此没有直接的转换路径，使你能够将 <xref:System.Windows.Forms.DataGrid> 自定义项用于 <xref:System.Windows.Forms.DataGridView> 控件。 <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> 不过，由于新控件中提供了内置功能，因此很有必要对控件进行许多自定义。 如果已为要用于控件的控件创建自定义列类型 <xref:System.Windows.Forms.DataGrid> <xref:System.Windows.Forms.DataGridView> ，则必须使用新的体系结构再次实现它们。 有关详细信息，请参阅[自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控件](datagridview-control-windows-forms.md)
- [DataGrid 控件](datagrid-control-windows-forms.md)
- [BindingSource 组件](bindingsource-component.md)
- [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的单元格样式](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的数据显示模式](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的数据格式设置](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的大小调整选项](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的列排序模式](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的选择模式](selection-modes-in-the-windows-forms-datagridview-control.md)
- [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)
