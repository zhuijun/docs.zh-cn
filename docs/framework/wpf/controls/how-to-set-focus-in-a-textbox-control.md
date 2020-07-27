---
title: 如何：设置 TextBox 控件中的焦点
description: 了解如何使用 Focus 方法在 Windows Presentation Foundation TextBox 控件上设置焦点。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: e107c22a3c5b701e02cbc8506d10fa35ee15c79d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168057"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>如何：设置 TextBox 控件中的焦点
此示例演示如何使用 <xref:System.Windows.UIElement.Focus%2A> 方法在控件上设置焦点 <xref:System.Windows.Controls.TextBox> 。  
  
## <a name="example"></a>示例  
 下面的 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 示例介绍一个 <xref:System.Windows.Controls.TextBox> 名为*tbFocusMe*的简单控件。  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>示例  
 下面的示例调用 <xref:System.Windows.UIElement.Focus%2A> 方法，以将焦点设置到 <xref:System.Windows.Controls.TextBox> 名为*tbFocusMe*的控件上。  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox 概述](textbox-overview.md)
- [RichTextBox 概述](richtextbox-overview.md)
