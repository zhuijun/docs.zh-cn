---
title: ScrollViewer 概述
description: 了解 ScrollViewer 控件，该控件可用于在 Windows Presentation Foundation 的应用程序中滚动内容。 请参阅使用示例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], ScrollViewer
- ScrollViewer control [WPF], about ScrollViewer control
ms.assetid: 94a13b94-cfdf-4b12-a1aa-90cb50c6e9b9
ms.openlocfilehash: 1ef680bb004315a2b523814714d5533535d044e5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164643"
---
# <a name="scrollviewer-overview"></a>ScrollViewer 概述
用户界面中的内容通常比计算机屏幕的显示区域大。 <xref:System.Windows.Controls.ScrollViewer>控件提供了一种简便的方式来实现在应用程序中滚动内容 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 。 本主题介绍 <xref:System.Windows.Controls.ScrollViewer> 元素并提供多个用法示例。  
  
<a name="what_is_a_scrollviewer_element"></a>
## <a name="the-scrollviewer-control"></a>ScrollViewer 控件  
 在应用程序中，有两个可用于滚动的预定义元素 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ： <xref:System.Windows.Controls.Primitives.ScrollBar> 和 <xref:System.Windows.Controls.ScrollViewer> 。 <xref:System.Windows.Controls.ScrollViewer>控件封装水平和垂直 <xref:System.Windows.Controls.Primitives.ScrollBar> 元素以及内容容器（如元素），以便 <xref:System.Windows.Controls.Panel> 在可滚动区域中显示其他可见元素。 必须生成自定义对象，才能将 <xref:System.Windows.Controls.Primitives.ScrollBar> 元素用于内容滚动。 但是，您可以单独使用该 <xref:System.Windows.Controls.ScrollViewer> 元素，因为它是一个封装功能的复合控件 <xref:System.Windows.Controls.Primitives.ScrollBar> 。  
  
 <xref:System.Windows.Controls.ScrollViewer>控件对鼠标和键盘命令做出响应，并定义了许多方法，通过预先确定的增量来滚动内容。 可以使用 <xref:System.Windows.Controls.ScrollViewer.ScrollChanged> 事件检测 <xref:System.Windows.Controls.ScrollViewer> 状态更改。  
  
 <xref:System.Windows.Controls.ScrollViewer>只能有一个子元素（通常是 <xref:System.Windows.Controls.Panel> 可承载元素集合的元素） <xref:System.Windows.Controls.Panel.Children%2A> 。 <xref:System.Windows.Controls.ContentPresenter.Content%2A>属性定义的唯一子级 <xref:System.Windows.Controls.ScrollViewer> 。  
  
<a name="scrollviewer_physical_vs_logical"></a>
## <a name="physical-vs-logical-scrolling"></a>物理滚动与逻辑滚动  
 物理滚动用于按预设的物理增量（通常按以像素为单位声明的值）滚动内容。 逻辑滚动用于滚动到逻辑树中的下一项。 物理滚动是大多数元素的默认滚动行为 <xref:System.Windows.Controls.Panel> 。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 同时支持这两种类型的滚动。  
  
#### <a name="the-iscrollinfo-interface"></a>IScrollInfo 接口  
 <xref:System.Windows.Controls.Primitives.IScrollInfo>接口表示或派生控件内的主滚动区域 <xref:System.Windows.Controls.ScrollViewer> 。 接口定义滚动属性和方法，这些属性和方法可由 <xref:System.Windows.Controls.Panel> 需要按逻辑单元（而不是物理增量）滚动的元素实现。 将的实例强制转换 <xref:System.Windows.Controls.Primitives.IScrollInfo> 为派生的 <xref:System.Windows.Controls.Panel> ，然后使用其滚动方法，可提供一种方法来滚动到子集合中的下一个逻辑单元，而不是按像素增量滚动到下一个逻辑单元。 默认情况下， <xref:System.Windows.Controls.ScrollViewer> 控件支持按物理单位滚动。  
  
 <xref:System.Windows.Controls.StackPanel>和 <xref:System.Windows.Controls.VirtualizingStackPanel> 都实现 <xref:System.Windows.Controls.Primitives.IScrollInfo> 并本机支持逻辑滚动。 对于本机支持逻辑滚动的布局控件，你仍可以通过将中的主机元素包装 <xref:System.Windows.Controls.Panel> 在中 <xref:System.Windows.Controls.ScrollViewer> 并将属性设置 <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> 为来 `false` 实现物理滚动。  
  
 下面的代码示例演示如何将的实例强制转换 <xref:System.Windows.Controls.Primitives.IScrollInfo> 为 <xref:System.Windows.Controls.StackPanel> ，并使用由接口定义的内容滚动方法（ <xref:System.Windows.Controls.Primitives.IScrollInfo.LineUp%2A> 和 <xref:System.Windows.Controls.Primitives.IScrollInfo.LineDown%2A> ）。  
  
 [!code-csharp[IScrollInfoMethods#3](~/samples/snippets/csharp/VS_Snippets_Wpf/IScrollInfoMethods/CSharp/Window1.xaml.cs#3)]
 [!code-vb[IScrollInfoMethods#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IScrollInfoMethods/VisualBasic/Window1.xaml.vb#3)]  
  
<a name="scrollviewer_markup_syntax_and_sample"></a>
## <a name="defining-and-using-a-scrollviewer-element"></a>定义和使用 ScrollViewer 元素  
 下面的示例 <xref:System.Windows.Controls.ScrollViewer> 在包含一些文本和一个矩形的窗口中创建一个。 <xref:System.Windows.Controls.Primitives.ScrollBar>元素只有在必要时才会出现。 当调整窗口的大小时， <xref:System.Windows.Controls.Primitives.ScrollBar> 元素将显示并消失，因为和属性的更新 <xref:System.Windows.Controls.ScrollViewer.ComputedHorizontalScrollBarVisibility%2A> 值 <xref:System.Windows.Controls.ScrollViewer.ComputedVerticalScrollBarVisibility%2A> 。  
  
 [!code-cpp[ScrollViewer#1](~/samples/snippets/cpp/VS_Snippets_Wpf/ScrollViewer/CPP/ScrollViewer_wcp.cpp#1)]
 [!code-csharp[ScrollViewer#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewer/CSharp/ScrollViewer_wcp.cs#1)]
 [!code-vb[ScrollViewer#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewer/VisualBasic/ScrollViewer.vb#1)]
 [!code-xaml[ScrollViewer#1](~/samples/snippets/xaml/VS_Snippets_Wpf/ScrollViewer/XAML/Pane1.xaml#1)]  
  
<a name="scrollviewer_styling_scrollviewer"></a>
## <a name="styling-a-scrollviewer"></a>设置 ScrollViewer 的样式  
 与 Windows Presentation Foundation 中的所有控件一样， <xref:System.Windows.Controls.ScrollViewer> 可以设置样式以便更改控件的默认呈现行为。 有关控件样式设置的其他信息，请参阅[样式设置和模板化](../../../desktop-wpf/fundamentals/styles-templates-overview.md)。  
  
<a name="scrollviewer_scroll_vs_paginate"></a>
## <a name="paginating-documents"></a>对文档进行分页  
 对于文档内容，一种替代滚动的方法是选择支持分页的文档容器。 <xref:System.Windows.Documents.FlowDocument>适用于设计为承载于查看控件中的文档，如 <xref:System.Windows.Controls.FlowDocumentPageViewer> 支持跨多个页面对内容进行分页的文档，从而不需要进行滚动。 <xref:System.Windows.Controls.DocumentViewer>提供用于查看内容的解决方案 <xref:System.Windows.Documents.FixedDocument> ，该解决方案使用传统滚动显示显示区域外的内容。  
  
 有关文档格式和演示选项的其他信息，请参阅 [WPF 中的文档](../advanced/documents-in-wpf.md)。  
  
## <a name="see-also"></a>请参阅

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.Primitives.ScrollBar>
- <xref:System.Windows.Controls.Primitives.IScrollInfo>
- [如何：创建滚动查看器](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms752352(v=vs.90))
- [WPF 中的文档](../advanced/documents-in-wpf.md)
- [ScrollBar 样式和模板](scrollbar-styles-and-templates.md)
- [控制](../advanced/optimizing-performance-controls.md)
