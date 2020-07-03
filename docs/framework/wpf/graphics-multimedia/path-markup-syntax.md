---
title: 路径标记语法
description: 了解可用于在 Windows Presentation Foundation （WPF）中指定精简路径几何图形的强大且复杂的迷你语言。
ms.date: 03/30/2017
helpviewer_keywords:
- attribute usage in XAML [WPF]
- XAML [WPF], attribute usage
- graphics [WPF], PathGeometry class
- XAML [WPF], object element usage
ms.assetid: b8586241-a02d-486e-9223-e1e98e047f41
ms.openlocfilehash: 6d2778522b622f0b0dcb59673e793a6d772a4b4f
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853653"
---
# <a name="path-markup-syntax"></a>路径标记语法
在 WPF 的 "[形状和基本绘图" 概述](shapes-and-basic-drawing-in-wpf-overview.md)和[几何概述](geometry-overview.md)中讨论了路径，不过，本主题详细介绍了可用于指定路径几何的强大且复杂的迷你语言（使用简洁地） [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。  
  
<a name="prerequisites"></a>
## <a name="prerequisites"></a>必备条件  
 若要了解本主题，应熟悉对象的基本功能 <xref:System.Windows.Media.Geometry> 。 有关详细信息，请参阅[几何概述](geometry-overview.md)。  
  
<a name="abouthisdocument"></a>
## <a name="streamgeometry-and-pathfigurecollection-mini-languages"></a>StreamGeometry and PathFigureCollection Mini-Languages  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供两个提供用于描述几何路径的迷你语言的类： <xref:System.Windows.Media.StreamGeometry> 和 <xref:System.Windows.Media.PathFigureCollection> 。  
  
- <xref:System.Windows.Media.StreamGeometry>设置类型的属性（ <xref:System.Windows.Media.Geometry> 如 <xref:System.Windows.UIElement.Clip%2A> 属性） <xref:System.Windows.UIElement> 或 <xref:System.Windows.Shapes.Path.Data%2A> 元素的属性时，请使用迷你语言 <xref:System.Windows.Shapes.Path> 。 下面的示例使用特性语法创建 <xref:System.Windows.Media.StreamGeometry> 。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMStreamGeometryAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmstreamgeometryattributesyntaxinline)]  
  
- <xref:System.Windows.Media.PathFigureCollection>当设置的属性时，请使用迷你语言 <xref:System.Windows.Media.PathGeometry.Figures%2A> <xref:System.Windows.Media.PathGeometry> 。 下面的示例使用特性语法为创建 <xref:System.Windows.Media.PathFigureCollection> <xref:System.Windows.Media.PathGeometry> 。  
  
     [!code-xaml[GeometrySample_snip_XAML#GraphicsMMPathFigureCollectionAttributeSyntaxInline](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample_snip_XAML/CS/MiniLanguageExample.xaml#graphicsmmpathfigurecollectionattributesyntaxinline)]  
  
 从前面的示例中可以看出，两种微型语言非常相似。 在可以使用的任何情况下，始终都可以使用， <xref:System.Windows.Media.PathGeometry> 因此， <xref:System.Windows.Media.StreamGeometry> 您应该使用哪一种？ 如果在 <xref:System.Windows.Media.StreamGeometry> 创建后不需要修改路径，则使用; <xref:System.Windows.Media.PathGeometry> 如果确实需要修改路径，请使用。  
  
 有关和对象之间的差异的详细信息 <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> ，请参阅[几何概述](geometry-overview.md)。  
  
### <a name="a-note-about-white-space"></a>有关空格的注意事项  
 为简洁起见，随后的语法部分中显示一个空格，但在显示一个空格的地方，多个空格也可以接受。  
  
 不一定要用逗号或空格来分隔两个数字，但这种情况只能在生成的字符串明确时执行。 例如， `2..3` 实际上是两个数字： "2"。 和“.3”。 同样， `2-3` 为 "2" 和 "-3"。 命令前面或后面也无需加空格。  
  
### <a name="syntax"></a>语法  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的特性用法语法由一个 <xref:System.Windows.Media.StreamGeometry> 可选 <xref:System.Windows.Media.FillRule> 值和一个或多个图形说明组成。  
  
|StreamGeometry XAML 属性用法|  
|-----------------------------------------|  
|`<`*object* *属性* `="` [ `fillRule` ] `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]的特性用法语法 <xref:System.Windows.Media.PathFigureCollection> 由一个或多个图形说明组成。  
  
|PathFigureCollection XAML Attribute Usage|  
|-----------------------------------------------|  
|`<`*object* *属性* `="` `figureDescription` [ `figureDescription` ] *`" ... />`|  
  
|术语|说明|  
|----------|-----------------|  
|*fillRule*|<xref:System.Windows.Media.FillRule?displayProperty=nameWithType><br /><br /> 指定是否 <xref:System.Windows.Media.StreamGeometry> 使用 <xref:System.Windows.Media.FillRule.EvenOdd> 或 <xref:System.Windows.Media.FillRule.Nonzero> <xref:System.Windows.Media.PathGeometry.FillRule%2A> 。<br /><br /> -   `F0`指定 <xref:System.Windows.Media.FillRule.EvenOdd> 填充规则。<br />-   `F1`指定 <xref:System.Windows.Media.FillRule.Nonzero> 填充规则。<br /><br /> 如果省略此命令，则子路径将使用默认行为，即 <xref:System.Windows.Media.FillRule.EvenOdd> 。 如果指定该命令，须先设置命令。|  
|*figureDescription*|图形由一个移动命令，绘制命令和一个可选的关闭命令组成。<br /><br /> `moveCommand` `drawCommands`  `[` `closeCommand` `]`|  
|*moveCommand*|用于指定图形起点的移动命令。 请参阅[移动命令](#themovecommand)部分。|  
|*drawCommands*|用于描述图形内容的一个或多个绘图命令。 请参阅[绘图命令](#drawcommands)部分。|  
|*closeCommand*|用于关闭图形的可选关闭命令。 请参阅[关闭命令](#closecommand)部分。|  
  
<a name="themovecommand"></a>
## <a name="move-command"></a>移动命令  
 指定新图形的起点。  
  
|语法|  
|------------|  
|`M` *startPoint*<br /><br /> - 或 -<br /><br /> `m` *startPoint*|  
  
|术语|说明|  
|----------|-----------------|  
|*startPoint*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 新图形的起点。|  
  
 大写字母 `M` 指示是一个 `startPoint` 绝对值; 一个小写的 `m` 指示 `startPoint` 是与前一个点的偏移量，如果不存在，则为（0，0）。 如果在移动命令之后列出多个点，可以绘制一条连接到这些点的直线，尽管已指定了直线命令。  
  
<a name="drawcommands"></a>
## <a name="draw-commands"></a>绘制命令  
 绘制命令可以由几个形状命令组成。 以下形状命令可用：直线、水平线、竖线、三次贝塞尔曲线、二次贝塞尔曲线、平滑三次贝塞尔曲线、平滑二次贝塞尔曲线和椭圆弧。  
  
 可以使用大写或小写字母输入每个命令：大写字母表示绝对值，小写字母表示相对值：该线段的控制点相对于前面示例的终点。 如果按顺序输入同一类型的多个命令，则可以忽略重复的命令条目;例如， `L 100,200 300,400` 等效于 `L 100,200 L 300,400` 。 下表描述了**移动**和**绘制**命令。  
  
### <a name="line-command"></a>直线命令  
 在当前点和指定的终点之间创建一条直线。 `l 20 30`和 `L 20,30` 是有效**行**命令的示例。  
  
|语法|  
|------------|  
|`L`*终结点*<br /><br /> - 或 -<br /><br /> `l`*终结点*|  
  
|术语|说明|  
|----------|-----------------|  
|*终结点*|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 线条的终点。|  

大写字母 `L` 指示是一个 `endPoint` 绝对值; 一个小写的 `l` 指示 `endPoint` 是与前一个点的偏移量，如果不存在，则为（0，0）。

### <a name="horizontal-line-command"></a>水平线命令  
 在当前点和指定的 x 坐标之间创建一条水平线。 `H 90` 是有效水平线命令的示例。

|语法|  
|------------|  
|`H`  *x-blade*<br /><br /> - 或 -<br /><br /> `h`  *x-blade*|  
  
|术语|说明|  
|----------|-----------------|  
|*x*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 线条终点的 x 坐标。|  
  
大写字母 `H` 指示是一个 `x` 绝对值; 一个小写的 `h` 指示 `x` 是与前一个点的偏移量，如果不存在，则为（0，0）。
  
### <a name="vertical-line-command"></a>竖线命令  
 在当前点和指定的 y 坐标之间创建一条竖线。 `v 90` 是有效竖线命令的示例。

|语法|  
|------------|  
|`V`  *误差*<br /><br /> - 或 -<br /><br /> `v`  *误差*|  
  
|术语|说明|  
|----------|-----------------|  
|*误差*|<xref:System.Double?displayProperty=nameWithType><br /><br /> 直线终点的 y 坐标。|  

大写字母 `V` 指示是一个 `y` 绝对值; 一个小写的 `v` 指示 `y` 是与前一个点的偏移量，如果不存在，则为（0，0）。  

### <a name="cubic-bezier-curve-command"></a>三次贝塞尔曲线命令  
 使用两个指定的控制点（ `controlPoint` 1 和2），在当前点和指定的终点之间创建三次方贝塞尔曲线 `controlPoint` 。 `C 100,200 200,400 300,200` 是有效曲线命令的示例。  
  
|语法|  
|------------|  
|`C``controlPoint`1 `controlPoint` 2`endPoint`<br /><br /> - 或 -<br /><br /> `c``controlPoint`1 `controlPoint` 2`endPoint`|  
  
|术语|说明|  
|----------|-----------------|  
|`controlPoint`1|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的第一个控制点，它决定曲线的起始切线。|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的第二个控制点，它决定曲线的结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="quadratic-bezier-curve-command"></a>二次贝塞尔曲线命令  
 使用指定的控制点（）在当前点和指定的终点之间创建二次贝塞尔曲线 `controlPoint` 。 `q 100,200 300,200` 为有效二次贝塞尔曲线命令的示例。  
  
|语法|  
|------------|  
|`Q` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `q` `controlPoint` `endPoint`|  
  
|术语|说明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，它决定曲线的开始和结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="smooth-cubic-bezier-curve-command"></a>平滑三次贝塞尔曲线命令  
 在当前点和指定的终点之间创建三次贝塞尔曲线。 假设第一控制点为相对当前点前一命令的第二控制点的反射。 如果没有前一命令或如果前一命令不是三次贝塞尔曲线命令或平滑三次贝塞尔曲线命令，则假设第一个控制点与当前点重合。 第二个控制点是曲线结束点的控制点，由 `controlPoint` 2 指定。 例如， `S 100,200 200,300` 是有效的平滑三次贝塞尔曲线命令。  
  
|语法|  
|------------|  
|`S``controlPoint`2`endPoint`<br /><br /> - 或 -<br /><br /> `s``controlPoint`2`endPoint`|  
  
|术语|说明|  
|----------|-----------------|  
|`controlPoint`2|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，它决定曲线的结束切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="smooth-quadratic-bezier-curve-command"></a>平滑二次贝塞尔曲线命令  
 在当前点和指定的终点之间创建二次贝塞尔曲线。 假设控制点为相对于当前点前一命令的控制点的反射。 如果没有前一命令或如果前一命令不是二次贝塞尔曲线命令或平滑二次贝塞尔曲线命令，则控制点与当前点重合。  
  
|语法|  
|------------|  
|`T` `controlPoint` `endPoint`<br /><br /> - 或 -<br /><br /> `t` `controlPoint` `endPoint`|  
  
|术语|说明|  
|----------|-----------------|  
|`controlPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 曲线的控制点，决定曲线的起点和曲线的切线。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制曲线将通过的点。|  
  
### <a name="elliptical-arc-command"></a>椭圆弧命令  
 在当前点和指定的终点之间创建一个椭圆弧。  
  
|语法|  
|------------|  
|`A` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`<br /><br /> - 或 -<br /><br /> `a` `size` `rotationAngle` `isLargeArcFlag` `sweepDirectionFlag` `endPoint`|  
  
|术语|说明|  
|----------|-----------------|  
|`size`|<xref:System.Windows.Size?displayProperty=nameWithType><br /><br /> 圆弧的 x 轴和 y 轴半径。|  
|`rotationAngle`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 椭圆的旋转，以度为单位。|  
|`isLargeArcFlag`|如果圆弧角度应为 180 度或更大，请设置为 1，否则设置为 0。|  
|`sweepDirectionFlag`|如果以正角方向绘制圆弧，请设置为 1；否则设置为 0。|  
|`endPoint`|<xref:System.Windows.Point?displayProperty=nameWithType><br /><br /> 绘制弧将通过的点。|  
  
<a name="closecommand"></a>
## <a name="the-close-command"></a>关闭命令  
 结束当前图形，并创建一条将当前点连接到图形起点的直线。 此命令可以在图形最后一段与第一段之间创建一条连接线（角）。  
  
|语法|  
|------------|  
|`Z`<br /><br /> - 或 -<br /><br /> `z`|  

<a name="pointsyntax"></a>
## <a name="point-syntax"></a>点语法  
 描述点（0，0）是左上角的点的 x 和 y 坐标。
  
|语法|  
|------------|  
|`x` `,` `y`<br /><br /> - 或 -<br /><br /> `x` `y`|  
  
|术语|说明|  
|----------|-----------------|  
|`x`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 该点的 x 坐标。|  
|`y`|<xref:System.Double?displayProperty=nameWithType><br /><br /> 该点的 y 坐标。|  
  
<a name="specialvalues"></a>
## <a name="special-values"></a>特殊值  
 除了标准数值外，还可使用以下特殊值。 这些值区分大小写。  
  
 无穷大  
 表示 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> 。  
  
 -Infinity  
 表示 <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 。  
  
 NaN  
 表示 <xref:System.Double.NaN?displayProperty=nameWithType> 。  
  
 也可使用科学计数法。 例如，`+1.e17` 是有效值。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.StreamGeometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.PathFigureCollection>
- [WPF 中的形状和基本图形概述](shapes-and-basic-drawing-in-wpf-overview.md)
- [Geometry 概述](geometry-overview.md)
- [操作指南主题](geometries-how-to-topics.md)
