---
title: 图形和多媒体
description: 发现 Windows Presentation Foundation 的媒体功能（WPF）。 向应用程序添加图形、转换效果、声音和视频。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: ba52e78564484f7714ab0035a5e1861766b72bbf
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853686"
---
# <a name="graphics-and-multimedia"></a>图形和多媒体

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 为多媒体、矢量图形、动画和内容复合提供支持，使开发者可以轻松生成有趣的用户界面和内容。 使用 Visual Studio，可以创建矢量图形或复杂的动画并将媒体集成到应用程序中。

本主题介绍 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 的图形、动画和媒体功能，可用于向应用程序添加图形、转换效果、声音和视频。

> [!NOTE]
> 强烈建议不要在 Windows 服务中使用 WPF 类型。 如果尝试在 Windows 服务中使用 WPF 类型，该服务可能无法按预期工作。

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>WPF 4 中的图形和多媒体新增功能

进行了与图形和动画相关的多项更改。

- 布局舍入

  当对象边缘落在像素设备中间位置时，与 DPI 无关的图形系统可以创建呈现项目，如模糊或半透明边缘。 WPF 的以前版本包含像素捕捉以帮助处理这种情况。 Silverlight 2 引入了布局舍入，这是移动元素以使边缘落在整个像素边界上的另一种方法。 WPF 现在支持对上的附加属性进行布局舍入 <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> <xref:System.Windows.FrameworkElement> 。

- 缓存复合

  通过使用新的 <xref:System.Windows.Media.BitmapCache> 和 <xref:System.Windows.Media.BitmapCacheBrush> 类，您可以将可视化树的复杂部分作为位图进行缓存，并大大改进渲染时间。 位图仍然能够响应用户输入（如鼠标单击），并且可以像任何画笔一样将其绘制到其他元素上。

- 像素着色器 3 支持

  WPF 4 构建于 <xref:System.Windows.Media.Effects.ShaderEffect> wpf 3.5 SP1 中引入的支持之上，通过允许应用程序使用像素着色器（PS）版本3.0 编写效果。 PS 3.0 着色器模型比 PS 2.0 更复杂，从而允许在支持的硬件上使用更多效果。

- 缓动函数

  可以使用缓动函数增强动画，从而提供对动画行为的额外控制。 例如，可以将应用于 <xref:System.Windows.Media.Animation.ElasticEase> 动画以为动画提供 springy 的行为。 有关详细信息，请参阅命名空间中的缓动类型 <xref:System.Windows.Media.Animation> 。

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>图形和呈现

WPF 包括对高质量2D 图形的支持。 功能包括画笔、几何、图像、形状和转换。 有关详细信息，请参阅[图形](graphics.md)。 图形元素的呈现基于 <xref:System.Windows.Media.Visual> 类。 屏幕上的视觉对象的结构由可视化树描述。 有关详细信息，请参阅 [WPF 图形呈现概述](wpf-graphics-rendering-overview.md)。

### <a name="2d-shapes"></a>二维形状

WPF 提供了一个库，其中列出了常用的矢量绘制的二维形状（如矩形和椭圆），如下图所示。

![显示省略号和矩形的关系图。](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

这些内部的 WPF 形状并不只是形状：它们是用于实现大多数常见控件（包括键盘和鼠标输入）的许多功能的可编程元素。 下面的示例演示如何处理 <xref:System.Windows.UIElement.MouseUp> 通过单击元素引发的事件 <xref:System.Windows.Shapes.Ellipse> 。

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

下图显示前面的 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 标记和代码隐藏的输出。

![将显示一个消息框，指出 "您单击了椭圆！"](./media/index/messagebox-text-output.png)

有关详细信息，请参阅 [WPF 中的形状和基本绘图概述](shapes-and-basic-drawing-in-wpf-overview.md)。 有关介绍性示例，请参阅[形状元素示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。

### <a name="2d-geometries"></a>二维几何图形

如果 WPF 提供的二维形状还不够，则可以使用几何图形和路径的 WPF 支持创建自己的。 下图显示了如何使用几何图形来创建形状、作为绘图画笔以及剪辑其他 WPF 元素。

![显示如何使用几何图形来创建形状的屏幕截图。](./media/index/use-geometries-create-shapes.png)

有关详细信息，请参阅[几何概述](geometry-overview.md)。 有关介绍性示例，请参阅 [Geometry 示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)。

### <a name="2d-effects"></a>2D 效果

WPF 提供了一系列2D 类，您可以使用它来创建各种效果。 WPF 的2D 呈现功能提供了绘制 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 具有渐变、位图、绘图和视频的元素的功能，并使用旋转、缩放和倾斜操作对其进行操作。 下图提供了可通过使用 WPF 画笔实现的多种效果的示例。

![显示不同 WPF 画笔和画图元素的插图。](./media/index/brushes-paint-elements.png)

有关详细信息，请参阅 [WPF 画笔概述](wpf-brushes-overview.md)。 有关详细信息，请参阅[画笔示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)。

<a name="rendering"></a>

## <a name="3d-rendering"></a>三维呈现

WPF 提供一组三维渲染功能，这些功能与 WPF 中的2D 图形支持集成，以便您能够创建更激动人心的布局、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 和数据可视化。 在一种极端情况下，WPF 允许您将2D 图像呈现到三维形状的图面上，如下图所示。

![显示具有不同纹理的三维形状的示例屏幕截图。](./media/index/visual-three-dimensional-shape.png)

有关详细信息，请参阅[三维图形概述](3-d-graphics-overview.md)。 有关介绍性示例，请参阅[3D 实体示例](https://go.microsoft.com/fwlink/?LinkID=159964)。

<a name="animation"></a>

## <a name="animation"></a>动画

使用动画，可以让控件和元素变大、抖动、旋转和淡出，并创建有趣的转换等。 因为 WPF 使你可以对大多数属性进行动画处理，因此，你不仅可以对大多数 WPF 对象进行动画处理，还可以使用 WPF 对你创建的自定义对象进行动画处理。

![动画处理多维数据集的屏幕截图。](./media/index/animate-custom-objects.png)

有关详细信息，请参阅 [动画概述](animation-overview.md)。 有关介绍性示例，请参阅[动画示例库](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)。

<a name="media"></a>

## <a name="media"></a>媒体

图像、视频和音频是传达信息和用户体验的富媒体方法。

### <a name="images"></a>映像

图像（包括图标、背景甚至动画部分）是大部分应用程序的核心部分。 由于你经常需要使用图像，因此 WPF 公开了以各种方式使用它们的功能。 下图显示其中一种方法。

![样式设置示例屏幕截图](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

有关详细信息，请参阅 [图像概述](imaging-overview.md)。

### <a name="video-and-audio"></a>视频和音频

WPF 图形功能的核心功能是为使用多媒体提供本机支持，其中包括视频和音频。 以下示例介绍如何将媒体播放器插入到应用程序中。

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>能够播放视频和音频，并且具有足够的可扩展性，使您可以轻松地创建自定义 Ui。

有关详细信息，请参阅[多媒体概述](multimedia-overview.md)。

## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [二维图形和图像处理](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [WPF 中的形状和基本图形概述](shapes-and-basic-drawing-in-wpf-overview.md)
- [使用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)
- [使用图像、图形和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)
- [动画和计时帮助主题](animation-and-timing-how-to-topics.md)
- [三维图形概述](3-d-graphics-overview.md)
- [多媒体概述](multimedia-overview.md)
