---
title: 如何：绑定到方法
description: 按照以下示例，了解如何绑定到 Windows Presentation Foundation （WPF）中的对象的方法。
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 9501e6357203c21651e85f1d65059be1d70becf2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619593"
---
# <a name="how-to-bind-to-a-method"></a>如何：绑定到方法
下面的示例演示如何使用绑定到方法 <xref:System.Windows.Data.ObjectDataProvider> 。  
  
## <a name="example"></a>示例  
 在本示例中，`TemperatureScale` 是一个具有方法 `ConvertTemp` 的类，该方法接收两个参数（分别为 `double` 和 `enum` 类型的 `TempType)`），并将给定值从一个温标转换为另一个温标。 在下面的示例中， <xref:System.Windows.Data.ObjectDataProvider> 使用来实例化 `TemperatureScale` 对象。 将使用两个指定参数调用 `ConvertTemp` 方法。  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 现在方法可以作为资源使用，因此可绑定到其结果。 在下面的示例中，的 <xref:System.Windows.Controls.TextBox.Text%2A> 和的属性 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A> <xref:System.Windows.Controls.ComboBox> 绑定到了方法的两个参数。 这允许用户指定要转换的温度以及要转换自的温标。 请注意， <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A> 设置为， `true` 因为我们要绑定到 <xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A> 实例的属性 <xref:System.Windows.Data.ObjectDataProvider> ，而不是由 <xref:System.Windows.Data.ObjectDataProvider> （对象）包装的对象的属性 `TemperatureScale` 。  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.Label> 当用户修改的内容或所选内容时，最后一次更新的 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.ComboBox> 。  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 转换器 `DoubleToString` 使用 double，并按方向将其转换为字符串 <xref:System.Windows.Data.IValueConverter.Convert%2A> （从绑定源到绑定目标，这是 <xref:System.Windows.Controls.TextBox.Text%2A> 属性），并将 `string` `double` 在方向转换为 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A> 。  
  
 用于 `InvalidationCharacterRule` <xref:System.Windows.Controls.ValidationRule> 检查无效字符的。 默认错误模板为周围的红色边框 <xref:System.Windows.Controls.TextBox> ，当输入值不是双精度值时，将显示通知用户。  
  
## <a name="see-also"></a>请参阅

- [操作指南主题](data-binding-how-to-topics.md)
- [绑定到枚举](how-to-bind-to-an-enumeration.md)
