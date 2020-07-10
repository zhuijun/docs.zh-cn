---
title: 控件中的边距和填充
description: 了解如何在 Windows 窗体控件中添加边距和填充属性。
ms.date: 03/30/2017
helpviewer_keywords:
- Padding property [Windows Forms]
- layout [Windows Forms], margins and padding
- Windows Forms, layout
- Margin property [Windows Forms]
ms.assetid: 3781b5a1-3085-4072-bed0-44670c23ffdc
ms.openlocfilehash: 4279f39bb4f89fbda8be472f49c8e60853abcac6
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174479"
---
# <a name="margin-and-padding-in-windows-forms-controls"></a>Windows 窗体控件中的边距和填充
在窗体上精确地放置控件对于许多应用程序而言是高优先级。 <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间给你提供许多布局功能来实现此目的。 其中两个最重要的功能是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 属性。  
  
 <xref:System.Windows.Forms.Control.Margin%2A> 属性定义控件周围的空间，该空间使其他控件与该控件的边框保持指定的距离。  
  
 <xref:System.Windows.Forms.Control.Padding%2A> 属性定义控件内部的空间，该空间使控件的内容（例如，其 <xref:System.Windows.Forms.Control.Text%2A> 属性的值）与该控件的边框保持指定的距离。  
  
 下图显示控件上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 属性。  
  
 ![Windows 窗体控件的填充和边距](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")  
  
 Visual Studio 中具有对此功能的设计时支持。 另请参阅[演练：通过填充、边距和 AutoSize 属性排放 Windows 窗体控件](windows-forms-controls-padding-autosize.md)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
