---
title: 控件
description: 了解 Windows Presentation Foundation 常见的 UI 组件（称为控件），但它可能不会从控件类继承。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: c3d9d3a38cf5f84e21df195e113e264e5a4ac025
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165854"
---
# <a name="controls"></a>控制
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]附带了许多在几乎每个 Windows 应用程序中使用的常用 UI 组件，例如、、、 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu> 和 <xref:System.Windows.Controls.ListBox> 。 以前，这些对象称为控件。 尽管 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] SDK 继续使用术语 "控制" 来松散表示应用程序中表示可见对象的任何类，但请务必注意，类不需要从类继承就能 <xref:System.Windows.Controls.Control> 看到可见的状态。 从 <xref:System.Windows.Controls.Control> 类继承的类包含一个 <xref:System.Windows.Controls.ControlTemplate>，它允许控件的使用方在无需创建新子类的情况下从根本上改变控件的外观。  本主题讨论中的控件（它们都从类继承，而不是从类继承的控件 <xref:System.Windows.Controls.Control> ）通常在中使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>创建控件的实例  
 您可以使用或代码将控件添加到应用程序 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。  下面的示例演示如何创建一个向用户询问其姓名的简单应用程序。  此示例将创建六个控件：中的两个标签、两个文本框和两个按钮 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 所有控件均可使用相似方式创建。  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 以下示例在代码中创建相同的应用程序。 为简洁起见，已从示例中排除了的创建 <xref:System.Windows.Controls.Grid> `grid1` 。 `grid1`具有与前面的示例中所示相同的列和行定义 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>更改控件的外观  
 更改控件的外观以适应应用程序的外观，这是很常见的操作。 可以根据要达到的效果，通过执行以下操作之一来更改控件的外观：  
  
- 更改控件的属性值。  
  
- <xref:System.Windows.Style>为控件创建一个。  
  
- 为控件创建一个新 <xref:System.Windows.Controls.ControlTemplate> 的。  
  
### <a name="changing-a-controls-property-value"></a>更改控件的属性值  
 许多控件都具有允许您更改控件显示方式的属性，例如的 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 。 您可以在和代码中设置值属性 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。 下面的示例在 <xref:System.Windows.Controls.Control.Background%2A> 中设置 <xref:System.Windows.Controls.Control.FontSize%2A> 的、和 <xref:System.Windows.Controls.Control.FontWeight%2A> 属性 <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 。  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 下面的示例在代码中设置相同的属性。  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>为控件创建样式  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使您能够通过创建来指定控件批发的外观，而不是在应用程序中设置每个实例的属性 <xref:System.Windows.Style> 。 下面的示例创建一个在 <xref:System.Windows.Style> <xref:System.Windows.Controls.Button> 应用程序中应用于每个的。 <xref:System.Windows.Style>定义通常在中定义 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.ResourceDictionary> ，如 <xref:System.Windows.FrameworkElement.Resources%2A> 的属性 <xref:System.Windows.FrameworkElement> 。  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 您还可以通过将键分配给样式并在控件的属性中指定该键，将样式仅应用于特定类型的特定控件 `Style` 。  有关样式的详细信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
### <a name="creating-a-controltemplate"></a>创建 ControlTemplate  
 <xref:System.Windows.Style>利用，您可以一次对多个控件设置属性，但有时您可能需要通过创建来自定义的外观 <xref:System.Windows.Controls.Control> 超出您可以执行的操作 <xref:System.Windows.Style> 。 从类继承的类 <xref:System.Windows.Controls.Control> 具有一个 <xref:System.Windows.Controls.ControlTemplate> ，它定义的结构和外观 <xref:System.Windows.Controls.Control> 。 的 <xref:System.Windows.Controls.Control.Template%2A> 属性 <xref:System.Windows.Controls.Control> 是公共的，因此可以为 <xref:System.Windows.Controls.Control> 其指定一个与 <xref:System.Windows.Controls.ControlTemplate> 默认值不同的。 通常可以为指定新 <xref:System.Windows.Controls.ControlTemplate> 的， <xref:System.Windows.Controls.Control> 而不是从控件继承以自定义的外观 <xref:System.Windows.Controls.Control> 。  
  
 请考虑非常常见的控件 <xref:System.Windows.Controls.Button> 。  的主要行为 <xref:System.Windows.Controls.Button> 是使应用程序在用户单击它时执行某种操作。  默认情况下， <xref:System.Windows.Controls.Button> 中的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 显示为凸起矩形。  开发应用程序时，您可能希望利用的行为（即 <xref:System.Windows.Controls.Button> ，通过处理按钮的单击事件），但您可能会通过更改按钮的属性来更改按钮的外观。  在这种情况下，你可以创建一个新的 <xref:System.Windows.Controls.ControlTemplate> 。  
  
 下面的示例为创建一个 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Button> 。  <xref:System.Windows.Controls.ControlTemplate>创建一个 <xref:System.Windows.Controls.Button> 带圆角和渐变背景的。  <xref:System.Windows.Controls.ControlTemplate>包含一个 <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border.Background%2A> <xref:System.Windows.Media.LinearGradientBrush> 具有两个 <xref:System.Windows.Media.GradientStop> 对象的。  第一个 <xref:System.Windows.Media.GradientStop> 使用数据绑定将 <xref:System.Windows.Media.GradientStop.Color%2A> 的属性绑定 <xref:System.Windows.Media.GradientStop> 到按钮背景的颜色。  当设置 <xref:System.Windows.Controls.Control.Background%2A> 的属性时 <xref:System.Windows.Controls.Button> ，该值的颜色将用作第一个 <xref:System.Windows.Media.GradientStop> 。 有关数据绑定的详细信息，请参阅[数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)。 该示例还将创建一个 <xref:System.Windows.Trigger> ，它将在时更改的外观 <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> `true` 。  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> <xref:System.Windows.Controls.Control.Background%2A>的属性 <xref:System.Windows.Controls.Button> 必须设置为， <xref:System.Windows.Media.SolidColorBrush> 此示例才能正常工作。  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>订阅事件  
 您可以使用或代码订阅控件的事件 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，但只能在代码中处理事件。  下面的示例演示如何订阅的 `Click` 事件 <xref:System.Windows.Controls.Button> 。  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 下面的示例处理的 `Click` 事件 <xref:System.Windows.Controls.Button> 。  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>控件中的丰富内容  
 继承自类的大多数类 <xref:System.Windows.Controls.Control> 都具有包含丰富内容的容量。 例如， <xref:System.Windows.Controls.Label> 可以包含任何对象，如字符串、 <xref:System.Windows.Controls.Image> 或 <xref:System.Windows.Controls.Panel> 。  以下类提供对丰富内容的支持，并充当中大多数控件的基类 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。  
  
- <xref:System.Windows.Controls.ContentControl>--从此类继承的类的一些示例包括 <xref:System.Windows.Controls.Label> 、 <xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Controls.ToolTip> 。  
  
- <xref:System.Windows.Controls.ItemsControl>--从此类继承的类的一些示例包括 <xref:System.Windows.Controls.ListBox> 、 <xref:System.Windows.Controls.Menu> 和 <xref:System.Windows.Controls.Primitives.StatusBar> 。  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--从此类继承的类的一些示例包括 <xref:System.Windows.Controls.TabItem> 、 <xref:System.Windows.Controls.GroupBox> 和 <xref:System.Windows.Controls.Expander> 。  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--从此类继承的类的一些示例包括 <xref:System.Windows.Controls.MenuItem> 、 <xref:System.Windows.Controls.TreeViewItem> 和 <xref:System.Windows.Controls.ToolBar> 。  

 有关这些基类的详细信息，请参阅[WPF 内容模型](wpf-content-model.md)。  
  
## <a name="see-also"></a>另请参阅

- [样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [按类别分类的控件](controls-by-category.md)
- [控件库](control-library.md)
- [数据模板化概述](../data/data-templating-overview.md)
- [数据绑定概述](../../../desktop-wpf/data/data-binding-overview.md)
- [输入](../advanced/input-wpf.md)
- [启用命令](../advanced/how-to-enable-a-command.md)
- [演练：创建自定义的动画按钮](walkthroughs-create-a-custom-animated-button.md)
- [控件自定义](control-customization.md)
