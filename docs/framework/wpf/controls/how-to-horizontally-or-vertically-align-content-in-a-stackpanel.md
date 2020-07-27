---
title: 如何：在 StackPanel 中水平或垂直对齐内容
description: 了解如何在 Windows Presentation Foundation System.windows.controls.stackpanel> 和子内容的 HorizontalAlignment 和 VerticalAlignment 中调整内容方向。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167635"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a><span data-ttu-id="02edb-103">如何：在 StackPanel 中水平或垂直对齐内容</span><span class="sxs-lookup"><span data-stu-id="02edb-103">How to: Horizontally or Vertically Align Content in a StackPanel</span></span>
<span data-ttu-id="02edb-104">此示例演示如何调整 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 元素内内容的 <xref:System.Windows.Controls.StackPanel> ，以及如何调整 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 子内容的和。</span><span class="sxs-lookup"><span data-stu-id="02edb-104">This example shows how to adjust the <xref:System.Windows.Controls.StackPanel.Orientation%2A> of content within a <xref:System.Windows.Controls.StackPanel> element, and also how to adjust the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> of child content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02edb-105">示例</span><span class="sxs-lookup"><span data-stu-id="02edb-105">Example</span></span>  
 <span data-ttu-id="02edb-106">下面的示例在中创建三个 <xref:System.Windows.Controls.ListBox> 元素 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="02edb-106">The following example creates three <xref:System.Windows.Controls.ListBox> elements in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="02edb-107">每个都 <xref:System.Windows.Controls.ListBox> 表示的 <xref:System.Windows.Controls.StackPanel.Orientation%2A> 、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和属性的可能值 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> 。</span><span class="sxs-lookup"><span data-stu-id="02edb-107">Each <xref:System.Windows.Controls.ListBox> represents the possible values of the <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> properties of a <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="02edb-108">当用户在任何元素中选择某个值时 <xref:System.Windows.Controls.ListBox> ，的关联属性 <xref:System.Windows.Controls.StackPanel> 及其子 <xref:System.Windows.Controls.Button> 元素将发生更改。</span><span class="sxs-lookup"><span data-stu-id="02edb-108">When a user selects a value in any of the <xref:System.Windows.Controls.ListBox> elements, the associated property of the <xref:System.Windows.Controls.StackPanel> and its child <xref:System.Windows.Controls.Button> elements change.</span></span>  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="02edb-109">下面的代码隐藏文件定义了对与选择更改关联的事件所做的更改 <xref:System.Windows.Controls.ListBox> 。</span><span class="sxs-lookup"><span data-stu-id="02edb-109">The following code-behind file defines the changes to the events that are associated with the <xref:System.Windows.Controls.ListBox> selection changes.</span></span> <span data-ttu-id="02edb-110"><xref:System.Windows.Controls.StackPanel>由标识 <xref:System.Windows.FrameworkElement.Name%2A> `sp1` 。</span><span class="sxs-lookup"><span data-stu-id="02edb-110"><xref:System.Windows.Controls.StackPanel> is identified by the <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.</span></span>  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="02edb-111">另请参阅</span><span class="sxs-lookup"><span data-stu-id="02edb-111">See also</span></span>

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [<span data-ttu-id="02edb-112">面板概述</span><span class="sxs-lookup"><span data-stu-id="02edb-112">Panels Overview</span></span>](panels-overview.md)
