---
title: ComboBox 样式和模板
description: 了解 Windows Presentation Foundation ComboBox 控件的样式和模板。 修改 System.windows.controls.controltemplate>，为控件指定独特的外观。
ms.date: 03/30/2017
helpviewer_keywords:
- ComboBox [WPF], styles and templates
- states [WPF], ComboBox
- ControlTemplate [WPF], ComboBox
- styles [WPF], ComboBox
- templates [WPF], ComboBox
- parts [WPF], ComboBox
ms.assetid: b0662fa1-16d7-4320-b26b-c1804e565a44
ms.openlocfilehash: 5e929bafeaf849b4b5682a17ca51cb0aab963613
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165912"
---
# <a name="combobox-styles-and-templates"></a>ComboBox 样式和模板
本主题描述控件的样式和模板 <xref:System.Windows.Controls.ComboBox> 。 您可以修改默认值 <xref:System.Windows.Controls.ControlTemplate> ，为控件指定独特的外观。 有关详细信息，请参阅为[控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="combobox-parts"></a>ComboBox 部分  
 下表列出了控件的已命名部件 <xref:System.Windows.Controls.ComboBox> 。  
  
|组成部分|类型|说明|  
|-|-|-|  
|PART_EditableTextBox|<xref:System.Windows.Controls.TextBox>|包含的文本 <xref:System.Windows.Controls.ComboBox> 。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|包含组合框中的项的下拉。|  
  
 为创建时 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> ，模板可能包含 <xref:System.Windows.Controls.ItemsPresenter> 内的 <xref:System.Windows.Controls.ScrollViewer> 。 （ <xref:System.Windows.Controls.ItemsPresenter> 显示中的每一项 <xref:System.Windows.Controls.ComboBox> ; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。  如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子级 <xref:System.Windows.Controls.ScrollViewer> ，则必须指定 <xref:System.Windows.Controls.ItemsPresenter> 名称 `ItemsPresenter` 。  
  
## <a name="combobox-states"></a>ComboBox 状态  
 下表列出了控件的状态 <xref:System.Windows.Controls.ComboBox> 。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|普通|CommonStates|默认状态。|  
|已禁用|CommonStates|已禁用控件。|  
|MouseOver|CommonStates|鼠标指针位于 <xref:System.Windows.Controls.ComboBox> 控件上方。|  
|已设定焦点|FocusStates|控件有焦点。|  
|失去焦点|FocusStates|控件没有焦点。|  
|FocusedDropDown|FocusStates|的下拉箭头 <xref:System.Windows.Controls.ComboBox> 。|  
|有效|ValidationStates|控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性为 `true` ，并且控件具有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性为 `true` ，并且该控件没有焦点。|  
|可编辑|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 属性为 `true`。|  
|不可编辑|EditStates|<xref:System.Windows.Controls.ComboBox.IsEditable%2A> 属性为 `false`。|  
  
## <a name="comboboxitem-parts"></a>ComboBoxItem 部件  
 <xref:System.Windows.Controls.ComboBoxItem>控件没有任何命名部分。  
  
## <a name="comboboxitem-states"></a>ComboBoxItem 状态  
 下表列出了控件的状态 <xref:System.Windows.Controls.ComboBoxItem> 。  
  
|VisualState 名称|VisualStateGroup 名称|描述|  
|-|-|-|  
|普通|CommonStates|默认状态。|  
|已禁用|CommonStates|已禁用控件。|  
|MouseOver|CommonStates|鼠标指针位于 <xref:System.Windows.Controls.ComboBoxItem> 控件上方。|  
|已设定焦点|FocusStates|控件有焦点。|  
|失去焦点|FocusStates|控件没有焦点。|  
|选定|SelectionStates|当前已选定该项。|  
|未选定|SelectionStates|未选定该项。|  
|SelectedUnfocused|SelectionStates|该项已选定，但没有焦点。|  
|有效|ValidationStates|控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性为 `true` ，并且控件具有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加的属性为 `true` ，并且该控件没有焦点。|  
  
## <a name="combobox-controltemplate-example"></a>ComboBox System.windows.controls.controltemplate> 示例  
 下面的示例演示如何为 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.ComboBox> 控件和关联的类型定义。  
  
 [!code-xaml[ControlTemplateExamples#ComboBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#combobox)]  
  
 上一示例使用了一个或多个以下资源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Control 样式和模板](control-styles-and-templates.md)
- [控件自定义](control-customization.md)
- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [创建控件模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)
