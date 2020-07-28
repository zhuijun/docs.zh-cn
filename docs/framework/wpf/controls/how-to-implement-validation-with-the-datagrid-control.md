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
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="9354c-103">如何：使用 DataGrid 控件实现验证</span><span class="sxs-lookup"><span data-stu-id="9354c-103">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="9354c-104"><xref:System.Windows.Controls.DataGrid>控件使您可以在单元和行级别执行验证。</span><span class="sxs-lookup"><span data-stu-id="9354c-104">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="9354c-105">使用单元格级验证时，可以在用户更新值时验证绑定数据对象的各个属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-105">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="9354c-106">通过行级验证，用户将更改提交到行时，可以验证整个数据对象。</span><span class="sxs-lookup"><span data-stu-id="9354c-106">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="9354c-107">你还可以为验证错误提供自定义的视觉反馈，或使用控件提供的默认视觉反馈 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="9354c-107">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="9354c-108">以下过程描述如何将验证规则应用于 <xref:System.Windows.Controls.DataGrid> 绑定并自定义视觉反馈。</span><span class="sxs-lookup"><span data-stu-id="9354c-108">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="9354c-109">验证单个单元值</span><span class="sxs-lookup"><span data-stu-id="9354c-109">To validate individual cell values</span></span>  
  
- <span data-ttu-id="9354c-110">指定与列一起使用的绑定上的一个或多个验证规则。</span><span class="sxs-lookup"><span data-stu-id="9354c-110">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="9354c-111">这类似于验证简单控件中的数据，如[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="9354c-111">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../desktop-wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="9354c-112">下面的示例演示了一个 <xref:System.Windows.Controls.DataGrid> 控件，该控件具有四列绑定到业务对象的不同属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-112">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="9354c-113">三列 <xref:System.Windows.Controls.ExceptionValidationRule> 通过将 <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> 属性设置为来指定 `true` 。</span><span class="sxs-lookup"><span data-stu-id="9354c-113">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="9354c-114">如果用户输入的值无效（如课程 ID 列中的非整数），则单元格的周围会出现一个红色边框。</span><span class="sxs-lookup"><span data-stu-id="9354c-114">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="9354c-115">您可以按照以下过程中所述更改此默认验证反馈。</span><span class="sxs-lookup"><span data-stu-id="9354c-115">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="9354c-116">自定义单元验证反馈</span><span class="sxs-lookup"><span data-stu-id="9354c-116">To customize cell validation feedback</span></span>  
  
- <span data-ttu-id="9354c-117">将列的 <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> 属性设置为适用于列编辑控件的样式。</span><span class="sxs-lookup"><span data-stu-id="9354c-117">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="9354c-118">由于编辑控件是在运行时创建的，因此不能 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> 像使用简单控件那样使用附加属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-118">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="9354c-119">下面的示例通过添加使用验证规则由三列共享的错误样式来更新上一个示例。</span><span class="sxs-lookup"><span data-stu-id="9354c-119">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="9354c-120">当用户输入无效值时，样式将更改单元格背景色并添加工具提示。</span><span class="sxs-lookup"><span data-stu-id="9354c-120">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="9354c-121">请注意，使用触发器来确定是否存在验证错误。</span><span class="sxs-lookup"><span data-stu-id="9354c-121">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="9354c-122">这是必需的，因为当前没有专用于单元的错误模板。</span><span class="sxs-lookup"><span data-stu-id="9354c-122">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="9354c-123">可以通过替换列使用的来实现更广泛的自定义 <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9354c-123">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="9354c-124">验证单个行中的多个值</span><span class="sxs-lookup"><span data-stu-id="9354c-124">To validate multiple values in a single row</span></span>  
  
1. <span data-ttu-id="9354c-125">实现一个 <xref:System.Windows.Controls.ValidationRule> 子类，该子类检查绑定数据对象的多个属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-125">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="9354c-126">在 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法实现中，将 `value` 参数值强制转换为 <xref:System.Windows.Data.BindingGroup> 实例。</span><span class="sxs-lookup"><span data-stu-id="9354c-126">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="9354c-127">然后，你可以通过属性访问数据对象 <xref:System.Windows.Data.BindingGroup.Items%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9354c-127">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="9354c-128">下面的示例演示了此过程，用于验证 `StartDate` 对象的属性值是否 `Course` 早于其 `EndDate` 属性值。</span><span class="sxs-lookup"><span data-stu-id="9354c-128">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. <span data-ttu-id="9354c-129">将验证规则添加到 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> 集合。</span><span class="sxs-lookup"><span data-stu-id="9354c-129">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="9354c-130"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>属性提供对 <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> 实例的属性的直接访问 <xref:System.Windows.Data.BindingGroup> ，该实例对控件使用的所有绑定进行分组。</span><span class="sxs-lookup"><span data-stu-id="9354c-130">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="9354c-131">下面的示例 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> 在 XAML 中设置属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-131">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="9354c-132"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>属性设置为， <xref:System.Windows.Controls.ValidationStep.UpdatedValue> 以便仅在更新绑定数据对象后进行验证。</span><span class="sxs-lookup"><span data-stu-id="9354c-132">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="9354c-133">如果用户指定的结束日期早于开始日期，则行标题中会出现红色感叹号（！）。</span><span class="sxs-lookup"><span data-stu-id="9354c-133">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="9354c-134">您可以按照以下过程中所述更改此默认验证反馈。</span><span class="sxs-lookup"><span data-stu-id="9354c-134">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="9354c-135">自定义行验证反馈</span><span class="sxs-lookup"><span data-stu-id="9354c-135">To customize row validation feedback</span></span>  
  
- <span data-ttu-id="9354c-136">设置 <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> 属性。</span><span class="sxs-lookup"><span data-stu-id="9354c-136">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="9354c-137">此属性使您可以为各个控件自定义行验证反馈 <xref:System.Windows.Controls.DataGrid> 。</span><span class="sxs-lookup"><span data-stu-id="9354c-137">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="9354c-138">还可以通过使用隐式行样式设置属性，来影响多个控件 <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="9354c-138">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="9354c-139">下面的示例将默认行验证反馈替换为更直观的指示器。</span><span class="sxs-lookup"><span data-stu-id="9354c-139">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="9354c-140">如果用户输入的值无效，则行标题中将显示一个带有白色感叹号的红色圆圈。</span><span class="sxs-lookup"><span data-stu-id="9354c-140">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="9354c-141">这会对行和单元格验证错误发生。</span><span class="sxs-lookup"><span data-stu-id="9354c-141">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="9354c-142">关联的错误消息将显示在工具提示中。</span><span class="sxs-lookup"><span data-stu-id="9354c-142">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="9354c-143">示例</span><span class="sxs-lookup"><span data-stu-id="9354c-143">Example</span></span>  
 <span data-ttu-id="9354c-144">下面的示例提供了单元和行验证的完整演示。</span><span class="sxs-lookup"><span data-stu-id="9354c-144">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="9354c-145">`Course`类提供一个示例数据对象，该对象实现 <xref:System.ComponentModel.IEditableObject> 以支持事务。</span><span class="sxs-lookup"><span data-stu-id="9354c-145">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="9354c-146"><xref:System.Windows.Controls.DataGrid>控件与进行交互 <xref:System.ComponentModel.IEditableObject> ，使用户能够通过按 ESC 来还原更改。</span><span class="sxs-lookup"><span data-stu-id="9354c-146">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9354c-147">如果使用 Visual Basic，请在 Mainwindow.xaml 的第一行中将替换 `x:Class="DataGridValidation.MainWindow"` 为 `x:Class="MainWindow"` 。</span><span class="sxs-lookup"><span data-stu-id="9354c-147">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="9354c-148">若要测试验证，请尝试以下操作：</span><span class="sxs-lookup"><span data-stu-id="9354c-148">To test the validation, try the following:</span></span>  
  
- <span data-ttu-id="9354c-149">在 "课程 ID" 列中，输入一个非整数值。</span><span class="sxs-lookup"><span data-stu-id="9354c-149">In the Course ID column, enter a non-integer value.</span></span>  
  
- <span data-ttu-id="9354c-150">在 "结束日期" 列中，输入早于开始日期的日期。</span><span class="sxs-lookup"><span data-stu-id="9354c-150">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
- <span data-ttu-id="9354c-151">删除课程 ID、开始日期或结束日期中的值。</span><span class="sxs-lookup"><span data-stu-id="9354c-151">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
- <span data-ttu-id="9354c-152">若要撤消无效的单元值，请将光标放在单元格中，然后按 ESC 键。</span><span class="sxs-lookup"><span data-stu-id="9354c-152">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
- <span data-ttu-id="9354c-153">若要在当前单元格处于编辑模式时撤消对整行所做的更改，请按 ESC 键两次。</span><span class="sxs-lookup"><span data-stu-id="9354c-153">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
- <span data-ttu-id="9354c-154">发生验证错误时，请将鼠标指针移动到行标题中的指示器上方，以查看关联的错误消息。</span><span class="sxs-lookup"><span data-stu-id="9354c-154">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="9354c-155">请参阅</span><span class="sxs-lookup"><span data-stu-id="9354c-155">See also</span></span>

- <xref:System.Windows.Controls.DataGrid>
- [<span data-ttu-id="9354c-156">DataGrid</span><span class="sxs-lookup"><span data-stu-id="9354c-156">DataGrid</span></span>](datagrid.md)
- [<span data-ttu-id="9354c-157">数据绑定</span><span class="sxs-lookup"><span data-stu-id="9354c-157">Data Binding</span></span>](../../../desktop-wpf/data/data-binding-overview.md)
- [<span data-ttu-id="9354c-158">实现绑定验证</span><span class="sxs-lookup"><span data-stu-id="9354c-158">Implement Binding Validation</span></span>](../data/how-to-implement-binding-validation.md)
- [<span data-ttu-id="9354c-159">在自定义对象上实现验证逻辑</span><span class="sxs-lookup"><span data-stu-id="9354c-159">Implement Validation Logic on Custom Objects</span></span>](../data/how-to-implement-validation-logic-on-custom-objects.md)
