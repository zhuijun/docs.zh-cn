---
title: 如何：创建多行 TextBox 控件
description: 了解如何使用 XAML 定义文本框控件，该控件可扩展以容纳 Windows Presentation Foundation 应用程序中的多个文本行。
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166252"
---
# <a name="how-to-create-a-multiline-textbox-control"></a><span data-ttu-id="eb92a-103">如何：创建多行 TextBox 控件</span><span class="sxs-lookup"><span data-stu-id="eb92a-103">How to: Create a Multiline TextBox Control</span></span>
<span data-ttu-id="eb92a-104">此示例演示如何使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 来定义一个 <xref:System.Windows.Controls.TextBox> 控件，该控件将自动展开以容纳多个文本行。</span><span class="sxs-lookup"><span data-stu-id="eb92a-104">This example shows how to use [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to define a <xref:System.Windows.Controls.TextBox> control that will automatically expand to accommodate multiple lines of text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb92a-105">示例</span><span class="sxs-lookup"><span data-stu-id="eb92a-105">Example</span></span>  
 <span data-ttu-id="eb92a-106"><xref:System.Windows.Controls.TextBox.TextWrapping%2A>如果将属性设置为 "**换**行"，则在到达控件边缘时，输入的文本会换行到新行 <xref:System.Windows.Controls.TextBox> ， <xref:System.Windows.Controls.TextBox> 如有必要，将自动展开控件以包含新行的空间。</span><span class="sxs-lookup"><span data-stu-id="eb92a-106">Setting the <xref:System.Windows.Controls.TextBox.TextWrapping%2A> attribute to **Wrap** will cause entered text to wrap to a new line when the edge of the <xref:System.Windows.Controls.TextBox> control is reached, automatically expanding the <xref:System.Windows.Controls.TextBox> control to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="eb92a-107">如果将 <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> 属性设置为**true** ，则在按下 RETURN 键时将插入一个新行，并在必要时再次自动展开 <xref:System.Windows.Controls.TextBox> 以包含新行的空间。</span><span class="sxs-lookup"><span data-stu-id="eb92a-107">Setting the <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> attribute to **true** causes a new line to be inserted when the RETURN key is pressed, once again automatically expanding the <xref:System.Windows.Controls.TextBox> to include room for a new line, if necessary.</span></span>  
  
 <span data-ttu-id="eb92a-108"><xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>特性可向添加滚动条 <xref:System.Windows.Controls.TextBox> ，因此，如果的内容 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.TextBox> 超出环绕它的框架或窗口的大小，则可以滚动。</span><span class="sxs-lookup"><span data-stu-id="eb92a-108">The <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> attribute adds a scroll bar to the <xref:System.Windows.Controls.TextBox>, so that the contents of the <xref:System.Windows.Controls.TextBox> can be scrolled through if the <xref:System.Windows.Controls.TextBox> expands beyond the size of the frame or window that encloses it.</span></span>  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="eb92a-109">另请参阅</span><span class="sxs-lookup"><span data-stu-id="eb92a-109">See also</span></span>

- <xref:System.Windows.TextWrapping>
- [<span data-ttu-id="eb92a-110">TextBox 概述</span><span class="sxs-lookup"><span data-stu-id="eb92a-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="eb92a-111">RichTextBox 概述</span><span class="sxs-lookup"><span data-stu-id="eb92a-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
