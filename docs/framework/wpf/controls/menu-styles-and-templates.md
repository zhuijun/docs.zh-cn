---
title: Menu 样式和模板
description: 了解 Windows Presentation Foundation 菜单控件的样式和模板。 修改 System.windows.controls.controltemplate>，为控件指定独特的外观。
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: 5187e4a479609686e39e043808931141ca52078c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164545"
---
# <a name="menu-styles-and-templates"></a>Menu 样式和模板
本主题描述控件的样式和模板 <xref:System.Windows.Controls.Menu> 。 您可以修改默认值 <xref:System.Windows.Controls.ControlTemplate> ，为控件指定独特的外观。 有关详细信息，请参阅为[控件创建模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)。  
  
## <a name="menu-parts"></a>菜单部件  
 <xref:System.Windows.Controls.Menu>控件没有任何命名部分。  
  
 为创建时 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> ，模板可能包含 <xref:System.Windows.Controls.ItemsPresenter> 内的 <xref:System.Windows.Controls.ScrollViewer> 。 （ <xref:System.Windows.Controls.ItemsPresenter> 显示中的每一项 <xref:System.Windows.Controls.Menu> ; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。  如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子级 <xref:System.Windows.Controls.ScrollViewer> ，则必须指定 <xref:System.Windows.Controls.ItemsPresenter> 名称 `ItemsPresenter` 。  
  
## <a name="menu-states"></a>菜单状态  
 下表列出了控件的可视状态 <xref:System.Windows.Controls.Menu> 。  
  
|VisualState 名称|VisualStateGroup 名称|说明|  
|-|-|-|  
|有效|ValidationStates|控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件具有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件没有焦点。|  
  
## <a name="menuitem-parts"></a>MenuItem 部分  
 下表列出了控件的已命名部件 <xref:System.Windows.Controls.Menu> 。  
  
|组成部分|类型|说明|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|子菜单的区域。|  
  
 为创建时 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> ，模板可能包含 <xref:System.Windows.Controls.ItemsPresenter> 内的 <xref:System.Windows.Controls.ScrollViewer> 。 （ <xref:System.Windows.Controls.ItemsPresenter> 显示中的每一项 <xref:System.Windows.Controls.MenuItem> ; <xref:System.Windows.Controls.ScrollViewer> 允许在控件中滚动）。  如果不 <xref:System.Windows.Controls.ItemsPresenter> 是的直接子级 <xref:System.Windows.Controls.ScrollViewer> ，则必须指定 <xref:System.Windows.Controls.ItemsPresenter> 名称 `ItemsPresenter` 。  
  
## <a name="menuitem-states"></a>MenuItem 状态  
 下表列出了控件的可视状态 <xref:System.Windows.Controls.MenuItem> 。  
  
|VisualState 名称|VisualStateGroup 名称|说明|  
|-|-|-|  
|有效|ValidationStates|控件使用 <xref:System.Windows.Controls.Validation> 类， <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 附加属性为 `false` 。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件具有焦点。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>附加属性是 `true` 控件没有焦点。|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>Menu 和 MenuItem System.windows.controls.controltemplate> 示例  
 下面的示例演示如何为控件定义 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Menu> 。  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 下面的示例演示如何为控件定义 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.MenuItem> 。  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 下面的示例定义了 `MenuScrollViewer` ，在前面的示例中使用了。  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 这些 <xref:System.Windows.Controls.ControlTemplate> 示例使用以下一个或多个资源。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 有关完整示例，请参阅[使用 ControlTemplates 设置样式示例](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [Control 样式和模板](control-styles-and-templates.md)
- [控件自定义](control-customization.md)
- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [创建控件模板](../../../desktop-wpf/themes/how-to-create-apply-template.md)
