---
title: 如何：检测 TextBox 中的文本何时更改
description: 了解当 TextBox 控件中的文本在 Windows Presentation Foundation 应用程序中发生更改时，如何使用 TextChanged 事件运行方法。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1e054380a8c77d32e6bb4adbbcb032e531bbefd0
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166222"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>如何：检测 TextBox 中的文本何时更改

此示例演示一种在 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 控件中的文本发生更改时使用事件执行方法的一种方法 <xref:System.Windows.Controls.TextBox> 。

在包含要监视其更改的控件的代码隐藏类中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> ，插入每当事件激发时要调用的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。  此方法的签名必须与委托所需的签名相匹配 <xref:System.Windows.Controls.TextChangedEventHandler> 。

只要 <xref:System.Windows.Controls.TextBox> 用户或以编程方式更改控件的内容，就会调用事件处理程序。

> [!NOTE]
> 此事件在 <xref:System.Windows.Controls.TextBox> 创建控件时和最初用文本填充时引发。

## <a name="example"></a>示例

在 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 定义控件的中 <xref:System.Windows.Controls.TextBox> ， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 使用与事件处理程序方法名称匹配的值指定特性。

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>示例

在包含要监视其更改的控件的代码隐藏类中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] <xref:System.Windows.Controls.TextBox> ，插入每当事件激发时要调用的方法 <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 。  此方法的签名必须与委托所需的签名相匹配 <xref:System.Windows.Controls.TextChangedEventHandler> 。

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

只要 <xref:System.Windows.Controls.TextBox> 用户或以编程方式更改控件的内容，就会调用事件处理程序。

> [!NOTE]
> 此事件在 <xref:System.Windows.Controls.TextBox> 创建控件时和最初用文本填充时引发。

注释

## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox 概述](textbox-overview.md)
- [RichTextBox 概述](richtextbox-overview.md)
