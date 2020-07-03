---
title: 使用纯色和渐变进行绘制概述
description: 了解如何使用对象绘制 Windows Presentation Foundation （WPF）中的纯色、线性渐变和径向渐变。
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- painting with gradients [WPF]
- gradients [WPF], painting with
- brushes [WPF], painting with solid colors
- brushes [WPF], painting with gradients
- painting with solid colors [WPF]
ms.assetid: f5b182f3-c5c7-4cbe-9f2f-65e690d08255
ms.openlocfilehash: 957593d758afda06db106c99f6695294d4f84f73
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853673"
---
# <a name="painting-with-solid-colors-and-gradients-overview"></a>使用纯色和渐变进行绘制概述

本主题说明如何使用 <xref:System.Windows.Media.SolidColorBrush> 、 <xref:System.Windows.Media.LinearGradientBrush> 和 <xref:System.Windows.Media.RadialGradientBrush> 对象绘制纯色、线性渐变和径向渐变。

<a name="solidcolor"></a>

## <a name="painting-an-area-with-a-solid-color"></a>使用纯色绘制区域

在任何平台中，最常见的操作之一是使用纯色绘制区域 <xref:System.Windows.Media.Color> 。 为了完成此任务， [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供了 <xref:System.Windows.Media.SolidColorBrush> 类。 以下各节介绍使用绘制的不同方式 <xref:System.Windows.Media.SolidColorBrush> 。

<a name="solidcolorinxaml"></a>

### <a name="using-a-solidcolorbrush-in-xaml"></a>在“XAML”中使用 SolidColorBrush

若要在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中使用纯色绘制某个区域，请使用以下选项之一。

- 按照名称选择预定义的纯色画笔。  例如，可以将按钮设置 <xref:System.Windows.Controls.Control.Background%2A> 为 "Red" 或 "MediumBlue"。  有关其他预定义纯色画笔的列表，请参见类的静态属性 <xref:System.Windows.Media.Brushes> 。 下面是一个示例。

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushNamedColor1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushnamedcolor1xaml)]

- 通过指定红色、绿色和蓝色的分量从 32 位调色板中选择一种颜色，以合并为单个纯色。  从 32 位调色板指定一种颜色的格式为“*#rrggbb*”，其中 *rr* 为两位十六进制数，用于指定红色的相对量，*gg* 指定绿色的相对量，*bb* 指定蓝色的相对量。  此外，该颜色可指定为“#*aarrggbb*”，其中，*aa* 指定该颜色的 *alpha* 值或透明度。 使用此方法能够创建部分透明的颜色。  在下面的示例中， <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 使用十六进制表示法将的设置为完全不透明的红色。

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushHex1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushhex1xaml)]

- 使用属性标记语法描述 <xref:System.Windows.Media.SolidColorBrush> 。 此语法更详细，并且能够指定其他设置，例如画笔的不透明度。 在下面的示例中， <xref:System.Windows.Controls.Control.Background%2A> 将两个 <xref:System.Windows.Controls.Button> 元素的属性设置为完全不透明的红色。 第一个画笔的颜色使用预定义的颜色名称描述。 第二个画笔的颜色使用十六进制表示法描述。

  [!code-xaml[BrushOverviewExamples_snip#SolidColorBrushPropertyTag1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/SolidColorBrushExample.xaml#solidcolorbrushpropertytag1xaml)]

<a name="solidcolorsincode"></a>

### <a name="painting-with-a-solidcolorbrush-in-code"></a>在代码中使用 SolidColorBrush 进行绘制

若要在代码中使用纯色绘制某个区域，请使用下列选项之一。

- 使用类提供的预定义画笔之一 <xref:System.Windows.Media.Brushes> 。 在下面的示例中，将 <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Button> 设置为 <xref:System.Windows.Media.Brushes.Red%2A> 。

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedBrush1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedbrush1csharp)]

- <xref:System.Windows.Media.SolidColorBrush>使用结构创建并设置其 <xref:System.Windows.Media.SolidColorBrush.Color%2A> 属性 <xref:System.Windows.Media.Color> 。 您可以使用类中的预定义颜色， <xref:System.Windows.Media.Colors> 也可以 <xref:System.Windows.Media.Color> 使用静态 <xref:System.Windows.Media.Color.FromArgb%2A> 方法创建。

  下面的示例演示如何 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> 使用预定义的颜色设置的属性。

  [!code-csharp[BrushOverviewExamples_snip#SolidColorBrushPredefinedColor1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushpredefinedcolor1csharp)]

静态 <xref:System.Windows.Media.Color.FromArgb%2A> 使您能够指定颜色的 alpha、红色、绿色和蓝色值。 每个值的常规范围介于 0 与 255 之间。 例如：alpha 值为 0 表示某种颜色完全透明，而值为 255 则表示该颜色完全不透明。 同样地，红色值为 0 表示某种颜色里没有红色，而值为 255 则表示某种颜色里红色最多。  在下面的示例中，画笔的颜色通过指定 alpha、红色、绿色和蓝色值描述。

[!code-csharp[BrushOverviewExamples_snip#SolidColorBrushfromArgbExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushfromargbexample1csharp)]

有关指定颜色的其他方式，请参阅 <xref:System.Windows.Media.Color> 参考主题。

<a name="gradient"></a>

## <a name="painting-an-area-with-a-gradient"></a>使用渐变绘制区域

渐变画笔使用沿轴相互混合的多种颜色绘制区域。 可以使用它们创建光和影的效果，使控件具有三维外观。 还可以使用它们来模拟玻璃、镶边、水和其他光滑表面。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供了两种类型的渐变画笔： <xref:System.Windows.Media.LinearGradientBrush> 和 <xref:System.Windows.Media.RadialGradientBrush> 。

<a name="lineargradientbrush"></a>

## <a name="linear-gradients"></a>线性渐变

<xref:System.Windows.Media.LinearGradientBrush>使用沿直线（*渐变轴*）定义的渐变绘制区域。  使用对象指定渐变的颜色及其在渐变轴上的位置 <xref:System.Windows.Media.GradientStop> 。  还可以修改渐变轴，从而能够创建水平和垂直渐变以及反转渐变方向。 渐变轴将在下一节中介绍。 默认情况下，将创建对角渐变。

下面的示例显示了使用四种颜色创建线性渐变的代码。

[!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]

此代码生成以下渐变：

![对角线方向线性渐变](./media/wcpsdk-graphicsmm-diaglgradient-nolabel.jpg "wcpsdk_graphicsmm_diaglgradient_nolabel")

> [!NOTE]
> 本主题中的渐变示例使用默认坐标系统来设置起点和终点。 默认坐标系与范围框相关：0 表示范围框为 0%，1 表示范围框为 100%。 您可以通过将属性设置为值来更改此坐标系统 <xref:System.Windows.Media.GradientBrush.MappingMode%2A> <xref:System.Windows.Media.BrushMappingMode.Absolute> 。 绝对坐标系与范围框无关。 值直接在本地空间中解释。

<xref:System.Windows.Media.GradientStop>是渐变画笔的基本构建基块。  梯度停止点指定 <xref:System.Windows.Media.GradientStop.Color%2A> <xref:System.Windows.Media.GradientStop.Offset%2A> 沿渐变轴的。

- 梯度停止点的 <xref:System.Windows.Media.GradientStop.Color%2A> 属性指定梯度停止点的颜色。 您可以使用预定义的颜色（由 <xref:System.Windows.Media.Colors> 类提供）或通过指定 ScRGB 或 ARGB 值设置颜色。 在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 中，还可以使用十六进制表示法描述一种颜色。 有关详细信息，请参阅 <xref:System.Windows.Media.Color> 结构。

- 梯度停止点的 <xref:System.Windows.Media.GradientStop.Offset%2A> 属性指定梯度停止点在渐变轴上的位置。 偏移量是 <xref:System.Double> 从0到1的范围。 梯度停止点的偏移值越接近 0，颜色就越接近渐变的起点。 梯度停止点的偏移值越接近 1，颜色就越接近渐变的终点。

渐变停点之间每个点的颜色均以两个边界渐变停点指定的颜色组合呈线性相互融合。 下图突出显示了上一示例中的梯度停止点。 圆圈标记梯度停止点的位置，虚线显示渐变轴。

![线性渐变中的渐变停止点](./media/wcpsdk-graphicsmm-4gradientstops.png "wcpsdk_graphicsmm_4gradientstops")

第一个梯度停止点指定偏移量 `0.0` 处的颜色为黄色。  第二个梯度停止点指定偏移量 `0.25` 处的颜色为红色。  这两个点之间的点在沿渐变轴由左向右移动时，颜色渐渐由黄色变为红色。  第三个梯度停止点指定偏移量 `0.75` 处的颜色为蓝色。  第二个和第三个梯度停止点之间的点渐渐由红色变为蓝色。 第四个梯度停止点指定偏移量 `1.0` 处的颜色为浅绿色。 第三个和第四个梯度停止点之间的点渐渐由蓝色变为浅绿色。

<a name="gradientaxis"></a>

### <a name="the-gradient-axis"></a>渐变轴

如前文中提到，线性渐变画笔的梯度停止点位于一条线上，即渐变轴上。 您可以使用画笔的和属性更改线条的方向和大小 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 。 通过操作画笔 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> ，您可以创建水平和垂直渐变、反转渐变方向、紧缩渐变传播等。

默认情况下，线性渐变画笔的 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 相对于所绘制的区域。 点 (0,0) 表示正在绘制的区域的左上角，点 (1,1) 表示绘制区域的右下角。 的默认值 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush> 为（0，0），其默认值 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 为（1，1），这将创建从左上角开始的对角渐变，并将其扩展到正在绘制的区域的右下角。 下图显示了带有默认和的线性渐变画笔的渐变轴 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 。

![对角线方向线性渐变的渐变轴](./media/wcpsdk-graphicsmm-diagonalgradientaxis.png "wcpsdk_graphicsmm_diagonalgradientaxis")

下面的示例演示如何通过指定画笔的和来创建水平渐变 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> 。 请注意，渐变停止点与前面示例中的停止相同;只需更改 <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> 和 <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> ，渐变已从对角线变为水平。

[!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]

下图显示了创建的渐变。 渐变轴用虚线标记，梯度停止点用圆圈标记。

![水平方向线性渐变的渐变轴](./media/wcpsdk-graphicsmm-horizontalgradient.jpg "wcpsdk_graphicsmm_horizontalgradient")

下一个示例演示如何创建垂直渐变。

[!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]

下图显示了创建的渐变。 渐变轴用虚线标记，梯度停止点用圆圈标记。

![垂直渐变的渐变轴](./media/wcpsdk-graphicsmm-verticalgradient.jpg "wcpsdk_graphicsmm_verticalgradient")

<a name="radialgradients"></a>

## <a name="radial-gradients"></a>径向渐变

像一样 <xref:System.Windows.Media.LinearGradientBrush> ，用 <xref:System.Windows.Media.RadialGradientBrush> 沿轴混合的颜色绘制区域。 前面的示例演示线性渐变画笔的轴是一条直线。 径向渐变画笔的轴由圆圈定义；它的颜色从原点开始向外“辐射”。

在下面的示例中，用径向渐变画笔绘制矩形内部。

[!code-xaml[GradientBrushExamples_snip#RadialGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/RadialGradientBrushExample.xaml#radialgradient1xaml)]

[!code-csharp[GradientBrushExamples_snip#RadialGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/RadialGradientBrushExample.cs#radialgradient1csharp)]

下图显示了上一示例中创建的渐变。 画笔的梯度停止点得到突出显示。 请注意，虽然结果不同，但该示例中梯度停止点与前面几个线性渐变画笔示例中的梯度停止点相同。

![径向渐变中的渐变停止点](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")

<xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A>指定径向渐变画笔的渐变轴的起点。 渐变轴从渐变原点向渐变圆辐射开来。 画笔的渐变圆由其 <xref:System.Windows.Media.RadialGradientBrush.Center%2A> 、 <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> 和 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 属性定义。

下图显示了具有不同 <xref:System.Windows.Media.RadialGradientBrush.GradientOrigin%2A> 、 <xref:System.Windows.Media.RadialGradientBrush.Center%2A> 、 <xref:System.Windows.Media.RadialGradientBrush.RadiusX%2A> 和设置的多个径向渐变 <xref:System.Windows.Media.RadialGradientBrush.RadiusY%2A> 。

![RadialGradientBrush 设置](./media/wcpsdk-graphicsmm-originscirclesandradii.gif "wcpsdk_graphicsmm_originscirclesandradii")具有不同 System.windows.media.radialgradientbrush.gradientorigin、Center、RadiusX 和 RadiusY 设置的具有。

<a name="specifyinggradientcolors"></a>

## <a name="specifying-transparent-or-partially-transparent-gradient-stops"></a>指定透明或部分透明的梯度停止点

因为梯度停止点不提供 opacity 属性，所以必须在标记中使用 ARGB 十六进制表示法指定颜色的 alpha 通道，或使用 <xref:System.Windows.Media.Color.FromScRgb%2A?displayProperty=nameWithType> 方法来创建透明或部分透明的梯度停止点。 下面的几节介绍如何在 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 和代码中创建部分透明的梯度停止点。

<a name="argbsyntax"></a>

### <a name="specifying-color-opacity-in-xaml"></a>在“XAML”中指定颜色不透明度

在中 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ，可以使用 ARGB 十六进制表示法来指定各个颜色的不透明度。 ARGB 十六进制表示法使用以下语法：

`#` **aa** *rrggbb*

上一行中的 *aa* 表示用于指定颜色不透明度的两位十六进制值。 *rr*、*gg* 和 *bb* 分别表示用于指定颜色中的红色、绿色和蓝色量的两位十六进制值。 每个十六进制数字介于 0-9 或 A-F 之间。 0 是最小值，F 是最大值。 00 的 alpha 值指定完全透明的颜色，而 FF 的 alpha 值创建完全不透明的颜色。  在下面的示例中，使用十六进制 ARGB 表示法指定两种颜色。 第一种为部分透明（alpha 值为 x20），而第二种为完全不透明。

[!code-xaml[GradientBrushExamples_snip#TransparentGradientStopExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/GradientStopsExample.xaml#transparentgradientstopexample1xaml)]

<a name="fromscrgbsyntax"></a>

### <a name="specifying-color-opacity-in-code"></a>在代码中指定颜色的不透明度

使用代码时，静态 <xref:System.Windows.Media.Color.FromArgb%2A> 方法使您能够在创建颜色时指定 alpha 值。 方法采用类型的四个参数 <xref:System.Byte> 。 第一个参数指定颜色的 alpha 通道；其他三个参数指定颜色的红色值、绿色值和蓝色值。 每个值应介于 0 与 255 之间（含 0 和 255）。 alpha 值为 0 表示颜色完全透明，alpha 值为 255 表示颜色完全不透明。 在下面的示例中， <xref:System.Windows.Media.Color.FromArgb%2A> 方法用于产生两种颜色。 第一种颜色为部分透明（alpha 值为 32），而第二种颜色为完全不透明。

[!code-csharp[GradientBrushExamples_snip#TransparentGradientStopExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/GradientStopsExample.cs#transparentgradientstopexample1csharp)]

或者，您可以使用 <xref:System.Windows.Media.Color.FromScRgb%2A> 方法，该方法使您可以使用 ScRGB 值创建颜色。

<a name="otherbrushes"></a>

## <a name="painting-with-images-drawings-visuals-and-patterns"></a>使用图像、绘图、Visual 和模式进行绘制

<xref:System.Windows.Media.ImageBrush>、 <xref:System.Windows.Media.DrawingBrush> 和 <xref:System.Windows.Media.VisualBrush> 类使你能够使用图像、绘图或视觉对象绘制区域。 有关使用图像、绘图和模式进行绘制的详细信息，请参阅[使用图像、绘图和 Visual 进行绘制](painting-with-images-drawings-and-visuals.md)。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- [使用图像、图形和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
- [Brush 变换概述](brush-transformation-overview.md)
- [图形呈现层](../advanced/graphics-rendering-tiers.md)
