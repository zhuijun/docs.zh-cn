---
title: 如何：使用 DataGrid 控件实现验证
description: 了解 Windows Presentation Foundation DataGrid 控件如何同时在单元和行级别执行验证，并提供验证错误的反馈。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: a6fe3693f94c3f554e96bc167b572cf854a1a34a
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167606"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>如何：使用 DataGrid 控件实现验证
<xref:System.Windows.Controls.DataGrid>控件使您可以在单元和行级别执行验证。 使用单元格级验证时，可以在用户更新值时验证绑定数据对象的各个属性。 通过行级验证，用户将更改提交到行时，可以验证整个数据对象。 你还可以为验证错误提供自定义的视觉反馈，或使用控件提供的默认视觉反馈 <xref:System.Windows.Controls.DataGrid> 。  
  
 以下过程描述如何将验证规则应用于 <xref:System.Windows.Controls.DataGrid> 绑定并自定义视觉反馈。  
  
### <a name="to-validate-individual-cell-values"></a>验证单个单元值  
  
- 指定与列一起使用的绑定上的一个或多个验证规则。 这类似于验证简单控件中的数据，如[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)中所述。  
  
     下面的示例演示了一个 <xref:System.Windows.Controls.DataGrid> 控件，该控件具有四列绑定到业务对象的不同属性。 三列 <xref:System.Windows.Controls.ExceptionValidationRule> 通过将 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 属性设置为来指定 `true` 。  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     如果用户输入的值无效（如课程 ID 列中的非整数），则单元格的周围会出现一个红色边框。 您可以按照以下过程中所述更改此默认验证反馈。  
  
### <a name="to-customize-cell-validation-feedback"></a>自定义单元验证反馈  
  
- 将列的 <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> 属性设置为适用于列编辑控件的样式。 由于编辑控件是在运行时创建的，因此不能 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> 像使用简单控件那样使用附加属性。  
  
     下面的示例通过添加使用验证规则由三列共享的错误样式来更新上一个示例。 当用户输入无效值时，样式将更改单元格背景色并添加工具提示。 请注意，使用触发器来确定是否存在验证错误。 这是必需的，因为当前没有专用于单元的错误模板。  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     可以通过替换列使用的来实现更广泛的自定义 <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> 。  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>验证单个行中的多个值  
  
1. 实现一个 <xref:System.Windows.Controls.ValidationRule> 子类，该子类检查绑定数据对象的多个属性。 在 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法实现中，将 `value` 参数值强制转换为 <xref:System.Windows.Data.BindingGroup> 实例。 然后，你可以通过属性访问数据对象 <xref:System.Windows.Data.BindingGroup.Items%2A> 。  
  
     下面的示例演示了此过程，用于验证 `StartDate` 对象的属性值是否 `Course` 早于其 `EndDate` 属性值。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. 将验证规则添加到 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> 集合。 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>属性提供对 <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> 实例的属性的直接访问 <xref:System.Windows.Data.BindingGroup> ，该实例对控件使用的所有绑定进行分组。  
  
     下面的示例 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> 在 XAML 中设置属性。 <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>属性设置为， <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 以便仅在更新绑定数据对象后进行验证。  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     如果用户指定的结束日期早于开始日期，则行标题中会出现红色感叹号（！）。 您可以按照以下过程中所述更改此默认验证反馈。  
  
### <a name="to-customize-row-validation-feedback"></a>自定义行验证反馈  
  
- 设置 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 属性。 此属性使您可以为各个控件自定义行验证反馈 <xref:System.Windows.Controls.DataGrid> 。 还可以通过使用隐式行样式设置属性，来影响多个控件 <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> 。  
  
     下面的示例将默认行验证反馈替换为更直观的指示器。 如果用户输入的值无效，则行标题中将显示一个带有白色感叹号的红色圆圈。 这会对行和单元格验证错误发生。 关联的错误消息将显示在工具提示中。  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>示例  
 下面的示例提供了单元和行验证的完整演示。 `Course`类提供一个示例数据对象，该对象实现 <xref:System.ComponentModel.IEditableObject> 以支持事务。 <xref:System.Windows.Controls.DataGrid>控件与进行交互 <xref:System.ComponentModel.IEditableObject> ，使用户能够通过按 ESC 来还原更改。  
  
> [!NOTE]
> 如果使用 Visual Basic，请在 Mainwindow.xaml 的第一行中将替换 `x:Class="DataGridValidation.MainWindow"` 为 `x:Class="MainWindow"` 。  
  
 若要测试验证，请尝试以下操作：  
  
- 在 "课程 ID" 列中，输入一个非整数值。  
  
- 在 "结束日期" 列中，输入早于开始日期的日期。  
  
- 删除课程 ID、开始日期或结束日期中的值。  
  
- 若要撤消无效的单元值，请将光标放在单元格中，然后按 ESC 键。  
  
- 若要在当前单元格处于编辑模式时撤消对整行所做的更改，请按 ESC 键两次。  
  
- 发生验证错误时，请将鼠标指针移动到行标题中的指示器上方，以查看关联的错误消息。  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [数据绑定](../../../desktop-wpf/data/data-binding-overview.md)
- [实现绑定验证](../data/how-to-implement-binding-validation.md)
- [在自定义对象上实现验证逻辑](../data/how-to-implement-validation-logic-on-custom-objects.md)
