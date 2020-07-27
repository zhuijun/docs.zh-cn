---
title: 如何：设置 TextBox 控件的文本内容
description: 了解如何使用 Text 属性设置 Windows Presentation Foundation TextBox 控件的初始文本内容。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168042"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>如何：设置 TextBox 控件的文本内容

此示例演示如何使用 <xref:System.Windows.Controls.TextBox.Text%2A> 属性来设置控件的初始文本内容 <xref:System.Windows.Controls.TextBox> 。

> [!NOTE]
> 尽管该 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 示例的版本可以在 `<TextBox.Text>` 每个按钮内容的文本周围使用标记 <xref:System.Windows.Controls.TextBox> ，但这并不是必需的，因为将 <xref:System.Windows.Controls.TextBox> 特性应用于 <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox.Text%2A> 属性。 有关详细信息，请参阅[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。

## <a name="example"></a>示例

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>示例

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>另请参阅

- [TextBox 概述](textbox-overview.md)
- [RichTextBox 概述](richtextbox-overview.md)
