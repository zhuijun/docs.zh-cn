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
# <a name="margin-and-padding-in-windows-forms-controls"></a><span data-ttu-id="3f7d5-103">Windows 窗体控件中的边距和填充</span><span class="sxs-lookup"><span data-stu-id="3f7d5-103">Margin and Padding in Windows Forms Controls</span></span>
<span data-ttu-id="3f7d5-104">在窗体上精确地放置控件对于许多应用程序而言是高优先级。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-104">Precise placement of controls on your form is a high priority for many applications.</span></span> <span data-ttu-id="3f7d5-105"><xref:System.Windows.Forms?displayProperty=nameWithType> 命名空间给你提供许多布局功能来实现此目的。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-105">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace gives you many layout features to accomplish this.</span></span> <span data-ttu-id="3f7d5-106">其中两个最重要的功能是 <xref:System.Windows.Forms.Control.Margin%2A> 和 <xref:System.Windows.Forms.Control.Padding%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-106">Two of the most important are the <xref:System.Windows.Forms.Control.Margin%2A> and <xref:System.Windows.Forms.Control.Padding%2A> properties.</span></span>  
  
 <span data-ttu-id="3f7d5-107"><xref:System.Windows.Forms.Control.Margin%2A> 属性定义控件周围的空间，该空间使其他控件与该控件的边框保持指定的距离。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-107">The <xref:System.Windows.Forms.Control.Margin%2A> property defines the space around the control that keeps other controls a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="3f7d5-108"><xref:System.Windows.Forms.Control.Padding%2A> 属性定义控件内部的空间，该空间使控件的内容（例如，其 <xref:System.Windows.Forms.Control.Text%2A> 属性的值）与该控件的边框保持指定的距离。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-108">The <xref:System.Windows.Forms.Control.Padding%2A> property defines the space in the interior of a control that keeps the control's content (for example, the value of its <xref:System.Windows.Forms.Control.Text%2A> property) a specified distance from the control's borders.</span></span>  
  
 <span data-ttu-id="3f7d5-109">下图显示控件上的 <xref:System.Windows.Forms.Control.Padding%2A> 和 <xref:System.Windows.Forms.Control.Margin%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-109">The following illustration shows the <xref:System.Windows.Forms.Control.Padding%2A> and <xref:System.Windows.Forms.Control.Margin%2A> properties on a control.</span></span>  
  
 <span data-ttu-id="3f7d5-110">![Windows 窗体控件的填充和边距](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span><span class="sxs-lookup"><span data-stu-id="3f7d5-110">![Padding And Margin for Windows Forms Controls](./media/vs-winformpadmargin.gif "VS_WinFormPadMargin")</span></span>  
  
 <span data-ttu-id="3f7d5-111">Visual Studio 中具有对此功能的设计时支持。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-111">There is design-time support for this feature in Visual Studio.</span></span> <span data-ttu-id="3f7d5-112">另请参阅[演练：通过填充、边距和 AutoSize 属性排放 Windows 窗体控件](windows-forms-controls-padding-autosize.md)。</span><span class="sxs-lookup"><span data-stu-id="3f7d5-112">Also see [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](windows-forms-controls-padding-autosize.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7d5-113">另请参阅</span><span class="sxs-lookup"><span data-stu-id="3f7d5-113">See also</span></span>

- <xref:System.Windows.Forms.Control.AutoSize%2A>
- <xref:System.Windows.Forms.Control.Margin%2A>
- <xref:System.Windows.Forms.Control.Padding%2A>
- <xref:System.Windows.Forms.Control.LayoutEngine%2A>
- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
