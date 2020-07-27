---
title: Alignment、Margin 和 Padding 概述
description: 了解在 Windows Presentation Foundation 应用程序中控制子元素位置的 HorizontalAlignment、边距、填充和 VerticalAlignment。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- margins [WPF]
- padding [WPF]
- aligning [WPF]
ms.assetid: 9c6a2009-9b86-4e40-8605-0a2664dc3973
ms.openlocfilehash: 832325086c85a7b044876e825d93e0b680a0b99c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165881"
---
# <a name="alignment-margins-and-padding-overview"></a>Alignment、Margin 和 Padding 概述
<xref:System.Windows.FrameworkElement>类公开几个用于精确定位子元素的属性。 本主题讨论四个最重要的属性： <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 、 <xref:System.Windows.FrameworkElement.Margin%2A> 、 <xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 。 了解这些属性的作用非常重要，因为这些属性是控制元素在 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 应用程序中的位置的基础。  

<a name="wcpsdk_layout_amp_introduction"></a>
## <a name="introduction-to-element-positioning"></a>元素定位简介  
 可使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 通过多种方式来定位元素。 但是，即使只是选择正确的元素，也不会获得理想的布局 <xref:System.Windows.Controls.Panel> 。 对定位进行精细控制需要了解、、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 属性。  
  
 下图显示了一个采用若干定位属性的布局方案。  
  
 ![WPF 定位属性示例](./media/layout-margins-padding-alignment-graphic1.PNG "layout_margins_padding_alignment_graphic1")  
  
 乍一看， <xref:System.Windows.Controls.Button> 此图中的元素可能显示为随机放置。 但是，其位置实际上是通过使用边距、对齐和填充加以精确控制的。  
  
 下面的示例描述如何创建上图中的布局。 <xref:System.Windows.Controls.Border>元素封装父，其 <xref:System.Windows.Controls.StackPanel> 值为 <xref:System.Windows.Controls.Border.Padding%2A> 15 个与设备无关的像素。 此帐户用于 <xref:System.Windows.Media.Brushes.LightBlue%2A> 环绕子项的窄带区 <xref:System.Windows.Controls.StackPanel> 。 的子元素 <xref:System.Windows.Controls.StackPanel> 用于演示本主题中详细介绍的各个定位属性。 三个 <xref:System.Windows.Controls.Button> 元素用于演示 <xref:System.Windows.FrameworkElement.Margin%2A> 和 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 属性。  
  
 [!code-csharp[MPALayoutSampleIntro#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutSampleIntro/CSharp/MPA_Layout_Sample_Intro.cs#1)]
 [!code-vb[MPALayoutSampleIntro#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutSampleIntro/VisualBasic/MPALayoutIntro.vb#1)]  
  
 通过下图可以仔细查看上例中使用的各个定位属性。 本主题的后面各节更详细地介绍了如何使用各个定位属性。  
  
 ![用屏幕调用&#45;输出定位属性](./media/layout-margins-padding-alignment-graphic2.PNG "layout_margins_padding_alignment_graphic2")  
  
<a name="wcpsdk_layout_amp_alignment_properties"></a>
## <a name="understanding-alignment-properties"></a>了解 Alignment 属性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 属性描述应如何将子元素定位到父元素的已分配布局空间内。 结合使用这些属性可精确定位子元素。 例如，的子元素 <xref:System.Windows.Controls.DockPanel> 可以指定四个不同的水平对齐方式： <xref:System.Windows.HorizontalAlignment.Left> 、 <xref:System.Windows.HorizontalAlignment.Right> 、或 <xref:System.Windows.HorizontalAlignment.Center> ，或以 <xref:System.Windows.HorizontalAlignment.Stretch> 填充可用空间。 类似的值可用于垂直定位。  
  
> [!NOTE]
> 元素的显式设置 <xref:System.Windows.FrameworkElement.Height%2A> 和 <xref:System.Windows.FrameworkElement.Width%2A> 属性优先于 <xref:System.Windows.HorizontalAlignment.Stretch> 属性值。 如果尝试将 <xref:System.Windows.FrameworkElement.Height%2A> 、和的值设置为， <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 则会 `Stretch` 忽略请求中的结果 `Stretch` 。  
  
<a name="wcpsdk_layout_amp_horizontalalignment_properties"></a>
### <a name="horizontalalignment-property"></a>HorizontalAlignment 属性  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>属性声明要应用于子元素的水平对齐特征。 下表显示了属性的每个可能值 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 。  
  
|成员|描述|  
|------------|-----------------|  
|<xref:System.Windows.HorizontalAlignment.Left>|子元素与父元素的已分配布局空间的左端对齐。|  
|<xref:System.Windows.HorizontalAlignment.Center>|子元素与父元素的已分配布局空间的中心对齐。|  
|<xref:System.Windows.HorizontalAlignment.Right>|子元素与父元素的已分配布局空间的右端对齐。|  
|<xref:System.Windows.HorizontalAlignment.Stretch>（默认）|拉伸子元素以填充父元素的已分配布局空间。 显式 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值优先。|  
  
 下面的示例演示如何将属性应用 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 到 <xref:System.Windows.Controls.Button> 元素。 显示每个特性值，以便更好地阐释各种呈现行为。  
  
 [!code-csharp[MPALayoutHorizontalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/CSharp/MPA_Layout_HorizontalAlignment.cs#2)]
 [!code-vb[MPALayoutHorizontalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutHorizontalAlignment/VisualBasic/MPA_Layout_HorizontalAlignment.vb#2)]  
  
 以上代码将产生与下图类似的布局。 图中显示每个值的定位效果 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 。  
  
 ![HorizontalAlignment 示例](./media/layout-horizontal-alignment-graphic.PNG "layout_horizontal_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_verticalalignment_properties"></a>
### <a name="verticalalignment-property"></a>VerticalAlignment 属性  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>属性描述要应用于子元素的垂直对齐特征。 下表显示了属性的每个可能值 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 。  
  
|成员|描述|  
|------------|-----------------|  
|<xref:System.Windows.VerticalAlignment.Top>|子元素与父元素的已分配布局空间的顶端对齐。|  
|<xref:System.Windows.VerticalAlignment.Center>|子元素与父元素的已分配布局空间的中心对齐。|  
|<xref:System.Windows.VerticalAlignment.Bottom>|子元素与父元素的已分配布局空间的底端对齐。|  
|<xref:System.Windows.VerticalAlignment.Stretch>（默认）|拉伸子元素以填充父元素的已分配布局空间。 显式 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值优先。|  
  
 下面的示例演示如何将属性应用 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 到 <xref:System.Windows.Controls.Button> 元素。 显示每个特性值，以便更好地阐释各种呈现行为。 出于本示例的目的， <xref:System.Windows.Controls.Grid> 具有可视网格线的元素用作父级，以更好地说明每个属性值的布局行为。  
  
 [!code-csharp[MPALayoutVerticalAlignment#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MPALayoutVerticalAlignment/CSharp/MPA_Layout_VerticalAlignment.cs#2)]
 [!code-vb[MPALayoutVerticalAlignment#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MPALayoutVerticalAlignment/VisualBasic/MPA_Layout_VerticalAlignment.vb#2)]
 [!code-xaml[MPALayoutVerticalAlignment#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MPALayoutVerticalAlignment/XAML/default.xaml#2)]  
  
 以上代码将产生与下图类似的布局。 图中显示每个值的定位效果 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 。  
  
 ![VerticalAlignment 属性示例](./media/layout-vertical-alignment-graphic.PNG "layout_vertical_alignment_graphic")  
  
<a name="wcpsdk_layout_amp_margin_properties"></a>
## <a name="understanding-margin-properties"></a>了解 Margin 属性  
 <xref:System.Windows.FrameworkElement.Margin%2A>属性描述元素及其子元素和同级之间的距离。 <xref:System.Windows.FrameworkElement.Margin%2A>通过使用类似的语法，值可以是统一的 `Margin="20"` 。 使用此语法时，将对 <xref:System.Windows.FrameworkElement.Margin%2A> 元素应用20个与设备无关的统一像素。 <xref:System.Windows.FrameworkElement.Margin%2A>值还可以采用四个非重复值的形式，每个值描述要应用于左侧、顶部、右侧和底部（按顺序）的不同边距，如 `Margin="0,10,5,25"` 。 正确使用 <xref:System.Windows.FrameworkElement.Margin%2A> 属性可以非常精确地控制元素的呈现位置以及其邻居元素和子元素的呈现位置。  
  
> [!NOTE]
> 非零边距将应用于元素的和之外的 <xref:System.Windows.FrameworkElement.ActualWidth%2A> 空间 <xref:System.Windows.FrameworkElement.ActualHeight%2A> 。  
  
 下面的示例演示如何在一组元素周围应用统一 <xref:System.Windows.Controls.Button> 的边距。 <xref:System.Windows.Controls.Button>元素在每个方向上均匀地分布在十个像素的边距缓冲区中。  
  
 [!code-cpp[MarginPaddingAlignmentSample#1](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#1)]
 [!code-csharp[MarginPaddingAlignmentSample#1](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#1)]
 [!code-vb[MarginPaddingAlignmentSample#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#1)]
 [!code-xaml[MarginPaddingAlignmentSample#1](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#1)]  
  
 在许多情况下，不适合使用统一边距。 对于这些情况，可应用非统一间距。 下面的示例演示如何将非统一边距间距应用于子元素。 按此顺序描述边距：左端、顶端、右端和底端。  
  
 [!code-cpp[MarginPaddingAlignmentSample#2](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#2)]
 [!code-csharp[MarginPaddingAlignmentSample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#2)]
 [!code-vb[MarginPaddingAlignmentSample#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#2)]
 [!code-xaml[MarginPaddingAlignmentSample#2](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#2)]  
  
<a name="wcpsdk_layout_amp_padding_properties"></a>
## <a name="understanding-the-padding-property"></a>了解 Padding 属性  
 填充 <xref:System.Windows.FrameworkElement.Margin%2A> 在大多数方面类似于。 仅在几个类上公开填充属性，这主要是为了方便： <xref:System.Windows.Documents.Block> 、 <xref:System.Windows.Controls.Border> 、 <xref:System.Windows.Controls.Control> 和 <xref:System.Windows.Controls.TextBlock> 是公开空白属性的类的示例。 <xref:System.Windows.Controls.Border.Padding%2A>属性按指定的值增大子元素的有效大小 <xref:System.Windows.Thickness> 。  
  
 下面的示例演示如何将应用于 <xref:System.Windows.Controls.Border.Padding%2A> 父 <xref:System.Windows.Controls.Border> 元素。  
  
 [!code-cpp[MarginPaddingAlignmentSample#3](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#3)]
 [!code-csharp[MarginPaddingAlignmentSample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#3)]
 [!code-vb[MarginPaddingAlignmentSample#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#3)]
 [!code-xaml[MarginPaddingAlignmentSample#3](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#3)]  
  
<a name="wcpsdk_layout_amp_summary"></a>
## <a name="using-alignment-margins-and-padding-in-an-application"></a>在应用程序中使用 Alignment、Margins 和 Padding  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>、 <xref:System.Windows.FrameworkElement.Margin%2A> 、 <xref:System.Windows.Controls.Border.Padding%2A> 和 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 提供创建复杂的所需的定位控件 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 。 可利用每个属性的作用来更改子元素定位，以便能够灵活地创建动态应用程序和用户体验。  
  
 下面的示例演示本主题中详述的各个概念。 此示例在本主题的第一个示例中的基础结构上构建，此示例将一个 <xref:System.Windows.Controls.Grid> 元素添加为 <xref:System.Windows.Controls.Border> 第一个示例中的的子元素。 <xref:System.Windows.Controls.Border.Padding%2A>应用于父 <xref:System.Windows.Controls.Border> 元素。 <xref:System.Windows.Controls.Grid>用于在三个子元素之间对空间进行分区 <xref:System.Windows.Controls.StackPanel> 。 <xref:System.Windows.Controls.Button>再次使用元素显示和的各种效果 <xref:System.Windows.FrameworkElement.Margin%2A> <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 。 <xref:System.Windows.Controls.TextBlock>向每个元素添加元素 <xref:System.Windows.Controls.ColumnDefinition> 可更好地定义应用于 <xref:System.Windows.Controls.Button> 每个列中的元素的各种属性。  
  
 [!code-cpp[MarginPaddingAlignmentSample#4](~/samples/snippets/cpp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CPP/Margin_Padding_Alignment_Sample.cpp#4)]
 [!code-csharp[MarginPaddingAlignmentSample#4](~/samples/snippets/csharp/VS_Snippets_Wpf/MarginPaddingAlignmentSample/CSharp/Margin_Padding_Alignment_Sample.cs#4)]
 [!code-vb[MarginPaddingAlignmentSample#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarginPaddingAlignmentSample/VisualBasic/MarginPaddingAlignment.vb#4)]
 [!code-xaml[MarginPaddingAlignmentSample#4](~/samples/snippets/xaml/VS_Snippets_Wpf/MarginPaddingAlignmentSample/XAML/default.xaml#4)]  
  
 编译后，前面的应用程序生成类似于下图的 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]。 各种属性值的效果在元素间的间距中很明显，每个列中的元素的重要属性值显示在 <xref:System.Windows.Controls.TextBlock> 元素中。  
  
 ![一个应用程序中的几个定位属性](./media/layout-margins-padding-aligment-graphic3.PNG "layout_margins_padding_aligment_graphic3")  
  
<a name="wcpsdk_layout_amp_alignment_whatsnext"></a>
## <a name="whats-next"></a>后续步骤  
 通过定位类定义的属性 <xref:System.Windows.FrameworkElement> ，可以在应用程序中对元素位置进行精细控制 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 。 至此你已了解多种方法，可使用这些方法更好地通过 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 来定位元素。  
  
 我们还提供了一些附加资源，这些资源更详细地介绍 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 布局。 [面板概述](../controls/panels-overview.md)主题包含有关各种元素的更多详细信息 <xref:System.Windows.Controls.Panel> 。 主题[演练：我的第一个 WPF 桌面应用程序](../getting-started/walkthrough-my-first-wpf-desktop-application.md)引入了使用布局元素定位组件并将其操作绑定到数据源的高级方法。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- <xref:System.Windows.FrameworkElement.Margin%2A>
- [面板概述](../controls/panels-overview.md)
- [布局](layout.md)
- [WPF 布局库示例](https://go.microsoft.com/fwlink/?LinkID=160054)
