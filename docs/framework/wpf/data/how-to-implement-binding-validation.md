---
title: 如何：实现绑定验证
description: 了解在 Windows Presentation Foundation （WPF）中输入无效值时，如何使用绑定验证向用户提供视觉反馈。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
ms.openlocfilehash: 0813be9f79a83a9dae26db1dadb58b5e973339fd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617877"
---
# <a name="how-to-implement-binding-validation"></a>如何：实现绑定验证

此示例演示如何使用 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 和样式触发器来提供可视反馈，以便在输入无效值时根据自定义验证规则通知用户。

## <a name="example"></a>示例

下面的示例中的的文本内容 <xref:System.Windows.Controls.TextBox> 绑定到 `Age` 名为的绑定源对象的属性（类型为 int） `ods` 。 该绑定设置为使用名为 `AgeRangeRule` 的验证规则，以便当用户输入了非数值字符或输入的值小于 21 或者大于 130 时，文本框旁边将显示一个红色感叹号，并且当用户将鼠标移动到该文本框上时，将显示包含错误消息的工具提示。

[!code-xaml[BindValidation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]

下面的示例演示了的实现 `AgeRangeRule` ，该实现继承自 <xref:System.Windows.Controls.ValidationRule> ，并重写 <xref:System.Windows.Controls.ValidationRule.Validate%2A> 方法。 对 `Int32.Parse` 值调用方法，以确保它不包含任何无效字符。 <xref:System.Windows.Controls.ValidationRule.Validate%2A>方法返回一个 <xref:System.Windows.Controls.ValidationResult> ，该整数指示此值是否有效，这是因为在分析期间是否捕获到了异常以及 age 值是否超出了下限。

[!code-csharp[BindValidation#3](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]
[!code-vb[BindValidation#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindValidation/VisualBasic/AgeRangeRule.vb#3)]

下面的示例演示了一个自定义 <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` ，它将创建一个红色感叹号来通知用户验证错误。 控件模板用于重新定义控件的外观。

[!code-xaml[BindValidation#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]

如下面的示例中所示，将 <xref:System.Windows.Controls.ToolTip> 使用名为的样式创建显示错误消息的 `textBoxInError` 。 如果的值 <xref:System.Windows.Controls.Validation.HasError%2A> 为 `true` ，则触发器将当前的工具提示设置 <xref:System.Windows.Controls.TextBox> 为第一个验证错误。 将 <xref:System.Windows.Data.Binding.RelativeSource%2A> 设置为 <xref:System.Windows.Data.RelativeSourceMode.Self> ，以引用当前元素。

[!code-xaml[BindValidation#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]

有关完整的示例，请参阅[绑定验证示例](https://github.com/Microsoft/WPF-Samples/tree/master/Data%20Binding/BindValidation)。
  
请注意，如果未提供自定义 <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> 的默认错误模板，则会出现验证错误时向用户提供视觉反馈。 有关详细信息，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)中的“数据验证”。 另外，[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 还提供了内置验证规则，该规则捕获在更新绑定源属性期间引发的异常。 有关详细信息，请参阅 <xref:System.Windows.Controls.ExceptionValidationRule>。

## <a name="see-also"></a>请参阅

- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [操作指南主题](data-binding-how-to-topics.md)
