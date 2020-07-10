---
title: DataGridView 控件概述
description: 了解如何使用 Windows 窗体 DataGridView 控件显示和编辑多种不同类型的数据源中的表格数据。
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174609"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView 控件概述（Windows 窗体）
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> 控件取代了 <xref:System.Windows.Forms.DataGrid> 控件并添加了功能；但是，可以选择保留 <xref:System.Windows.Forms.DataGrid> 控件以实现向后兼容并供将来使用。 有关详细信息，请参阅 [Windows 窗体 DataGridView 控件与 DataGrid 控件之间的区别](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)。  
  
 借助 <xref:System.Windows.Forms.DataGridView> 控件，可以显示和编辑多种不同类型的数据源中的表格数据。  
  
 将数据绑定到 <xref:System.Windows.Forms.DataGridView> 控件非常简单直观，在许多情况下，只需设置 <xref:System.Windows.Forms.DataGridView.DataSource%2A> 属性即可。 绑定到包含多个列表或表的数据源时，请将 <xref:System.Windows.Forms.DataGridView.DataMember%2A> 属性设置为指定要绑定到的列表或表的字符串。  
  
 该 <xref:System.Windows.Forms.DataGridView> 控件支持标准 Windows 窗体数据绑定模型，因此它将绑定到以下列表中所述的类的实例：  
  
- 实现接口的任何类 <xref:System.Collections.IList> ，包括一维数组。  
  
- 实现接口的任何类 <xref:System.ComponentModel.IListSource> ，如 <xref:System.Data.DataTable> 和 <xref:System.Data.DataSet> 类。  
  
- 实现接口的任何类 <xref:System.ComponentModel.IBindingList> ，如 <xref:System.ComponentModel.BindingList%601> 类。  
  
- 实现接口的任何类 <xref:System.ComponentModel.IBindingListView> ，如 <xref:System.Windows.Forms.BindingSource> 类。  
  
 <xref:System.Windows.Forms.DataGridView> <xref:System.ComponentModel.ICustomTypeDescriptor> 如果在返回的对象上实现，则控件支持将数据绑定到由这些接口返回的对象的公共属性或由接口返回的 properties 集合。  
  
 通常，你将绑定到一个 <xref:System.Windows.Forms.BindingSource> 组件，并将该 <xref:System.Windows.Forms.BindingSource> 组件绑定到另一个数据源，或者使用业务对象来填充它。 <xref:System.Windows.Forms.BindingSource>组件是首选数据源，因为它可以绑定到各种数据源，并可自动解决许多数据绑定问题。 有关详细信息，请参阅[BindingSource Component](bindingsource-component.md)。  
  
 该 <xref:System.Windows.Forms.DataGridView> 控件还可以用于*未绑定*模式，无基础数据存储区。 有关使用未绑定控件的代码示例 <xref:System.Windows.Forms.DataGridView> ，请参阅[演练：创建未绑定的 Windows 窗体 DataGridView 控件](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)。  
  
 <xref:System.Windows.Forms.DataGridView>控件高度可配置且可扩展，并且提供了许多属性、方法和事件来自定义其外观和行为。 如果希望 Windows 窗体应用程序显示表格数据，请考虑在 <xref:System.Windows.Forms.DataGridView> 其他人之前使用控件 (例如， <xref:System.Windows.Forms.DataGrid>) 。 如果要显示只读值的小网格，或者如果你要使用户能够编辑包含数百万条记录的表，则该 <xref:System.Windows.Forms.DataGridView> 控件将为你提供一个易于编程的、内存有效的解决方案。  
  
## <a name="in-this-section"></a>本节内容  
 [DataGridView 控件技术摘要](datagridview-control-technology-summary-windows-forms.md)  
 汇总了 <xref:System.Windows.Forms.DataGridView> 控件概念和相关类的用法。  
  
 [DataGridView 控件体系结构](datagridview-control-architecture-windows-forms.md)  
 描述控件的体系结构 <xref:System.Windows.Forms.DataGridView> ，并说明其类型层次结构和继承结构。  
  
 [DataGridView 控件方案](datagridview-control-scenarios-windows-forms.md)  
 描述使用控件的最常见方案 <xref:System.Windows.Forms.DataGridView> 。  
  
 [DataGridView 控件代码目录](datagridview-control-code-directory-windows-forms.md)  
 提供有关各种任务的文档中的代码示例的链接 <xref:System.Windows.Forms.DataGridView> 。 这些示例按任务类型进行分类。  
  
## <a name="related-sections"></a>相关章节  
 [Windows 窗体 DataGridView 控件中的列类型](column-types-in-the-windows-forms-datagridview-control.md)  
 讨论 <xref:System.Windows.Forms.DataGridView> 用于显示信息以及允许用户修改或添加信息的 Windows 窗体控件中的列类型。  
  
 [在 Windows 窗体 DataGridView 控件中显示数据](displaying-data-in-the-windows-forms-datagridview-control.md)  
 提供一些主题，描述如何手动或从外部数据源向控件填充数据。  
  
 [自定义 Windows 窗体 DataGridView 控件](customizing-the-windows-forms-datagridview-control.md)  
 提供一些主题，介绍自定义绘制 <xref:System.Windows.Forms.DataGridView> 单元格和行，以及创建派生的单元、列和行类型。  
  
 [Windows 窗体 DataGridView 控件中的性能优化](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 提供一些主题，介绍如何在使用大量数据时，有效地使用控件以避免性能问题。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView 控件](datagridview-control-windows-forms.md)
- [Windows 窗体 DataGridView 控件中的默认功能](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Windows 窗体 DataGridView 控件中的默认键盘和鼠标处理](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
