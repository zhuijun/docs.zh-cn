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
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a><span data-ttu-id="0f237-103">如何：设置 TextBox 控件的文本内容</span><span class="sxs-lookup"><span data-stu-id="0f237-103">How to: Set the Text Content of a TextBox Control</span></span>

<span data-ttu-id="0f237-104">此示例演示如何使用 <xref:System.Windows.Controls.TextBox.Text%2A> 属性来设置控件的初始文本内容 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0f237-104">This example shows how to use the <xref:System.Windows.Controls.TextBox.Text%2A> property to set the initial text contents of a <xref:System.Windows.Controls.TextBox> control.</span></span>

> [!NOTE]
> <span data-ttu-id="0f237-105">尽管该 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 示例的版本可以在 `<TextBox.Text>` 每个按钮内容的文本周围使用标记 <xref:System.Windows.Controls.TextBox> ，但这并不是必需的，因为将 <xref:System.Windows.Controls.TextBox> 特性应用于 <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox.Text%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="0f237-105">Although the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] version of the example could use the `<TextBox.Text>` tags around the text of each button's <xref:System.Windows.Controls.TextBox> content, it is not necessary because the <xref:System.Windows.Controls.TextBox> applies the <xref:System.Windows.Markup.ContentPropertyAttribute> attribute to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="0f237-106">有关详细信息，请参阅[XAML 概述（WPF）](../../../desktop-wpf/fundamentals/xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="0f237-106">For more information, see [XAML Overview (WPF)](../../../desktop-wpf/fundamentals/xaml.md).</span></span>

## <a name="example"></a><span data-ttu-id="0f237-107">示例</span><span class="sxs-lookup"><span data-stu-id="0f237-107">Example</span></span>

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a><span data-ttu-id="0f237-108">示例</span><span class="sxs-lookup"><span data-stu-id="0f237-108">Example</span></span>

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a><span data-ttu-id="0f237-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="0f237-109">See also</span></span>

- [<span data-ttu-id="0f237-110">TextBox 概述</span><span class="sxs-lookup"><span data-stu-id="0f237-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="0f237-111">RichTextBox 概述</span><span class="sxs-lookup"><span data-stu-id="0f237-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
