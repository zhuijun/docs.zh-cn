---
title: 画笔概述
description: 了解如何通过在 Windows Presentation Foundation （WPF）中通过渐变和模式使用简单的纯色颜色进行绘制来阐明概念。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], about brushes
ms.assetid: ecea1955-420b-45c6-bf43-c1404c072c41
ms.openlocfilehash: 9bfd702d7a5a9d807e2b922874119c2bb2e68f39
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853718"
---
# <a name="wpf-brushes-overview"></a><span data-ttu-id="bedc0-103">WPF 画笔概述</span><span class="sxs-lookup"><span data-stu-id="bedc0-103">WPF Brushes Overview</span></span>
<span data-ttu-id="bedc0-104">屏幕上可见的所有内容都可见，因为它是由画笔绘制的。</span><span class="sxs-lookup"><span data-stu-id="bedc0-104">Everything visible on your screen is visible because it was painted by a brush.</span></span> <span data-ttu-id="bedc0-105">例如，画笔用于描述按钮的背景、文本的前景和形状的填充效果。</span><span class="sxs-lookup"><span data-stu-id="bedc0-105">For example, a brush is used to describe the background of a button, the foreground of text, and the fill of a shape.</span></span> <span data-ttu-id="bedc0-106">本主题介绍了利用画笔进行绘制的概念 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] ，并提供了示例。</span><span class="sxs-lookup"><span data-stu-id="bedc0-106">This topic introduces the concepts of painting with [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] brushes and provides examples.</span></span> <span data-ttu-id="bedc0-107">借助画笔，可以利用任意内容（从简单的纯色到复杂的图案和图像集）绘制 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 对象。</span><span class="sxs-lookup"><span data-stu-id="bedc0-107">Brushes enable you to paint [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] objects with anything from simple, solid colors to complex sets of patterns and images.</span></span>  
  
<a name="paintingwithbrush"></a>
## <a name="painting-with-a-brush"></a><span data-ttu-id="bedc0-108">使用画笔进行绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-108">Painting with a Brush</span></span>  
 <span data-ttu-id="bedc0-109"><xref:System.Windows.Media.Brush>"绘制" 带有其输出的区域。</span><span class="sxs-lookup"><span data-stu-id="bedc0-109">A <xref:System.Windows.Media.Brush> "paints" an area with its output.</span></span> <span data-ttu-id="bedc0-110">不同的画笔具有不同的输出类型。</span><span class="sxs-lookup"><span data-stu-id="bedc0-110">Different brushes have different types of output.</span></span> <span data-ttu-id="bedc0-111">某些画笔使用纯色绘制区域，其他画笔使用渐变、图案、图像或绘图。</span><span class="sxs-lookup"><span data-stu-id="bedc0-111">Some brushes paint an area with a solid color, others with a gradient, pattern, image, or drawing.</span></span> <span data-ttu-id="bedc0-112">下图显示了每种不同类型的示例 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-112">The following illustration shows examples of each of the different <xref:System.Windows.Media.Brush> types.</span></span>  
  
 <span data-ttu-id="bedc0-113">![画笔类型](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span><span class="sxs-lookup"><span data-stu-id="bedc0-113">![Brush types](./media/graphicsmm-brushtypes.jpg "graphicsmm_brushtypes")</span></span>  
<span data-ttu-id="bedc0-114">画笔示例</span><span class="sxs-lookup"><span data-stu-id="bedc0-114">Brush examples</span></span>  
  
 <span data-ttu-id="bedc0-115">大多数视觉对象使您能够指定如何绘制它们。</span><span class="sxs-lookup"><span data-stu-id="bedc0-115">Most visual objects enable you to specify how they are painted.</span></span> <span data-ttu-id="bedc0-116">下表列出了一些常用的对象和属性，您可以使用它们来使用 <xref:System.Windows.Media.Brush> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-116">The following table lists some common objects and properties with which you can use a <xref:System.Windows.Media.Brush>.</span></span>  
  
|<span data-ttu-id="bedc0-117">类</span><span class="sxs-lookup"><span data-stu-id="bedc0-117">Class</span></span>|<span data-ttu-id="bedc0-118">画笔属性</span><span class="sxs-lookup"><span data-stu-id="bedc0-118">Brush properties</span></span>|  
|-----------|----------------------|  
|<xref:System.Windows.Controls.Border>|<span data-ttu-id="bedc0-119"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span><span class="sxs-lookup"><span data-stu-id="bedc0-119"><xref:System.Windows.Controls.Border.BorderBrush%2A>, <xref:System.Windows.Controls.Border.Background%2A></span></span>|  
|<xref:System.Windows.Controls.Control>|<span data-ttu-id="bedc0-120"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span><span class="sxs-lookup"><span data-stu-id="bedc0-120"><xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A></span></span>|  
|<xref:System.Windows.Controls.Panel>|<xref:System.Windows.Controls.Panel.Background%2A>|  
|<xref:System.Windows.Media.Pen>|<xref:System.Windows.Media.Pen.Brush%2A>|  
|<xref:System.Windows.Shapes.Shape>|<span data-ttu-id="bedc0-121"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span><span class="sxs-lookup"><span data-stu-id="bedc0-121"><xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A></span></span>|  
|<xref:System.Windows.Controls.TextBlock>|<xref:System.Windows.Controls.TextBlock.Background%2A>|  
  
 <span data-ttu-id="bedc0-122">以下各节介绍了不同 <xref:System.Windows.Media.Brush> 类型，并提供了每种类型的示例。</span><span class="sxs-lookup"><span data-stu-id="bedc0-122">The following sections describe the different <xref:System.Windows.Media.Brush> types and provide an example of each.</span></span>  
  
<a name="paintwithsolidcolorbrush"></a>
## <a name="paint-with-a-solid-color"></a><span data-ttu-id="bedc0-123">使用纯色绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-123">Paint with a Solid Color</span></span>  
 <span data-ttu-id="bedc0-124"><xref:System.Windows.Media.SolidColorBrush>使用纯色绘制区域 <xref:System.Windows.Media.Color> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-124">A <xref:System.Windows.Media.SolidColorBrush> paints an area with a solid <xref:System.Windows.Media.Color>.</span></span> <span data-ttu-id="bedc0-125">可以通过多种方式指定的 <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> ：例如，可以指定其 alpha、红色、蓝色和绿色通道，或使用类提供的预定义颜色之一 <xref:System.Windows.Media.Colors> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-125">There are a variety of ways to specify the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush>: for example, you can specify its alpha, red, blue, and green channels or use one of the predefined color provided by the <xref:System.Windows.Media.Colors> class.</span></span>  
  
 <span data-ttu-id="bedc0-126">下面的示例使用 <xref:System.Windows.Media.SolidColorBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-126">The following example uses a <xref:System.Windows.Media.SolidColorBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-127">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-127">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-128">![使用 SolidColorBrush 绘制的矩形](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-128">![A rectangle painted using a SolidColorBrush](./media/graphicsmm-brush-ovw-solidcolorbrush.png "graphicsmm_brush_ovw_solidcolorbrush")</span></span>  
<span data-ttu-id="bedc0-129">使用 System.windows.media.solidcolorbrush> 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-129">A Rectangle painted using a SolidColorBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmsolidcolorbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmsolidcolorbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMSolidColorBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmsolidcolorbrushexampleinline)]  
  
 <span data-ttu-id="bedc0-130">有关类的详细信息 <xref:System.Windows.Media.SolidColorBrush> ，请参阅[采用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-130">For more information about the <xref:System.Windows.Media.SolidColorBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithlineargradientbrush"></a>
## <a name="paint-with-a-linear-gradient"></a><span data-ttu-id="bedc0-131">使用线性渐变绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-131">Paint with a Linear Gradient</span></span>  
 <span data-ttu-id="bedc0-132"><xref:System.Windows.Media.LinearGradientBrush>使用线性渐变绘制区域。</span><span class="sxs-lookup"><span data-stu-id="bedc0-132">A <xref:System.Windows.Media.LinearGradientBrush> paints an area with a linear gradient.</span></span> <span data-ttu-id="bedc0-133">线性渐变在线条（渐变轴）中混合了两种或多种颜色。</span><span class="sxs-lookup"><span data-stu-id="bedc0-133">A linear gradient blends two or more colors across a line, the gradient axis.</span></span> <span data-ttu-id="bedc0-134">使用 <xref:System.Windows.Media.GradientStop> 对象可以指定渐变中的颜色及其位置。</span><span class="sxs-lookup"><span data-stu-id="bedc0-134">You use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="bedc0-135">下面的示例使用 <xref:System.Windows.Media.LinearGradientBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-135">The following example uses a <xref:System.Windows.Media.LinearGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-136">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-136">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-137">![使用 LinearGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-137">![A rectangle painted using a LinearGradientBrush](./media/graphicsmm-brush-ovw-lineargradientbrush.jpg "graphicsmm_brush_ovw_lineargradientbrush")</span></span>  
<span data-ttu-id="bedc0-138">使用 LinearGradientBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-138">A Rectangle painted using a LinearGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmlineargradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmlineargradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMLinearGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmlineargradientbrushexampleinline)]  
  
 <span data-ttu-id="bedc0-139">有关类的详细信息 <xref:System.Windows.Media.LinearGradientBrush> ，请参阅[采用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-139">For more information about the <xref:System.Windows.Media.LinearGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithradialgradientbrush"></a>
## <a name="paint-with-a-radial-gradient"></a><span data-ttu-id="bedc0-140">使用径向渐变绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-140">Paint with a Radial Gradient</span></span>  
 <span data-ttu-id="bedc0-141"><xref:System.Windows.Media.RadialGradientBrush>使用径向渐变绘制区域。</span><span class="sxs-lookup"><span data-stu-id="bedc0-141">A <xref:System.Windows.Media.RadialGradientBrush> paints an area with a radial gradient.</span></span> <span data-ttu-id="bedc0-142">径向渐变跨一个圆混合两种或多种颜色。</span><span class="sxs-lookup"><span data-stu-id="bedc0-142">A radial gradient blends two or more colors across a circle.</span></span> <span data-ttu-id="bedc0-143">与类一样 <xref:System.Windows.Media.LinearGradientBrush> ，可以使用 <xref:System.Windows.Media.GradientStop> 对象指定渐变中的颜色及其位置。</span><span class="sxs-lookup"><span data-stu-id="bedc0-143">As with the <xref:System.Windows.Media.LinearGradientBrush> class, you use <xref:System.Windows.Media.GradientStop> objects to specify the colors in the gradient and their positions.</span></span>  
  
 <span data-ttu-id="bedc0-144">下面的示例使用 <xref:System.Windows.Media.RadialGradientBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-144">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-145">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-145">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-146">![使用 RadialGradientBrush 绘制的矩形](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-146">![A rectangle painted using a RadialGradientBrush](./media/graphicsmm-brush-ovw-radialgradientbrush.jpg "graphicsmm_brush_ovw_radialgradientbrush")</span></span>  
<span data-ttu-id="bedc0-147">使用 RadialGradientBrush 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-147">A Rectangle painted using a RadialGradientBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmradialgradientbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmradialgradientbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMRadialGradientBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmradialgradientbrushexampleinline)]  
  
 <span data-ttu-id="bedc0-148">有关类的详细信息 <xref:System.Windows.Media.RadialGradientBrush> ，请参阅[采用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-148">For more information about the <xref:System.Windows.Media.RadialGradientBrush> class, see [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="paintwithimage"></a>
## <a name="paint-with-an-image"></a><span data-ttu-id="bedc0-149">使用图像进行绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-149">Paint with an Image</span></span>  
 <span data-ttu-id="bedc0-150"><xref:System.Windows.Media.ImageBrush>使用绘制区域 <xref:System.Windows.Media.ImageSource> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-150">An <xref:System.Windows.Media.ImageBrush> paints an area with a <xref:System.Windows.Media.ImageSource>.</span></span>  
  
 <span data-ttu-id="bedc0-151">下面的示例使用 <xref:System.Windows.Media.ImageBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-151">The following example uses an <xref:System.Windows.Media.ImageBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-152">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-152">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-153">![使用 ImageBrush 绘制的矩形](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-153">![A Rectangle painted by an ImageBrush](./media/graphicsmm-brush-ovw-imagebrush.jpg "graphicsmm_brush_ovw_imagebrush")</span></span>  
<span data-ttu-id="bedc0-154">使用图像绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-154">A Rectangle painted using a Image</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmimagebrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmimagebrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMImageBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmimagebrushexampleinline)]  
  
 <span data-ttu-id="bedc0-155">有关类的详细信息 <xref:System.Windows.Media.ImageBrush> ，请参阅[利用图像、绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-155">For more information about the <xref:System.Windows.Media.ImageBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithdrawing"></a>
## <a name="paint-with-a-drawing"></a><span data-ttu-id="bedc0-156">使用绘图绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-156">Paint with a Drawing</span></span>  
 <span data-ttu-id="bedc0-157"><xref:System.Windows.Media.DrawingBrush>使用绘制区域 <xref:System.Windows.Media.Drawing> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-157">A <xref:System.Windows.Media.DrawingBrush> paints an area with a <xref:System.Windows.Media.Drawing>.</span></span> <span data-ttu-id="bedc0-158"><xref:System.Windows.Media.Drawing>可以包含形状、图像、文本和媒体。</span><span class="sxs-lookup"><span data-stu-id="bedc0-158">A <xref:System.Windows.Media.Drawing> can contain shapes, images, text, and media.</span></span>  
  
 <span data-ttu-id="bedc0-159">下面的示例使用 <xref:System.Windows.Media.DrawingBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-159">The following example uses a <xref:System.Windows.Media.DrawingBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-160">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-160">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-161">![使用 DrawingBrush 绘制的矩形](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-161">![A rectangle painted using a DrawingBrush](./media/graphicsmm-brush-ovw-drawingbrush.jpg "graphicsmm_brush_ovw_drawingbrush")</span></span>  
<span data-ttu-id="bedc0-162">使用 System.windows.media.drawingbrush> 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-162">A Rectangle painted using a DrawingBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmdrawingbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmdrawingbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMDrawingBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmdrawingbrushexampleinline)]  
  
 <span data-ttu-id="bedc0-163">有关类的详细信息 <xref:System.Windows.Media.DrawingBrush> ，请参阅[利用图像、绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-163">For more information about the <xref:System.Windows.Media.DrawingBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithvisual"></a>
## <a name="paint-with-a-visual"></a><span data-ttu-id="bedc0-164">使用视觉对象进行绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-164">Paint with a Visual</span></span>  
 <span data-ttu-id="bedc0-165"><xref:System.Windows.Media.VisualBrush>使用对象绘制区域 <xref:System.Windows.Media.Visual> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-165">A <xref:System.Windows.Media.VisualBrush> paints an area with a <xref:System.Windows.Media.Visual> object.</span></span> <span data-ttu-id="bedc0-166">可视化对象的示例包括 <xref:System.Windows.Controls.Button> 、 <xref:System.Windows.Controls.Page> 和 <xref:System.Windows.Controls.MediaElement> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-166">Examples of Visual objects include <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Page>, and <xref:System.Windows.Controls.MediaElement>.</span></span> <span data-ttu-id="bedc0-167"><xref:System.Windows.Media.VisualBrush>利用，还可以将应用程序的一个部分的内容投影到另一个区域; 这对于创建反射效果和屏幕的放大部分非常有用。</span><span class="sxs-lookup"><span data-stu-id="bedc0-167">A <xref:System.Windows.Media.VisualBrush> also enables you to project content from one portion of your application into another area; it's very useful for creating reflection effects and magnifying portions of the screen.</span></span>  
  
 <span data-ttu-id="bedc0-168">下面的示例使用 <xref:System.Windows.Media.VisualBrush> 绘制 <xref:System.Windows.Shapes.Shape.Fill%2A> 的 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-168">The following example uses a <xref:System.Windows.Media.VisualBrush> to paint the <xref:System.Windows.Shapes.Shape.Fill%2A> of a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="bedc0-169">下图显示了绘制的矩形。</span><span class="sxs-lookup"><span data-stu-id="bedc0-169">The following illustration shows the painted rectangle.</span></span>  
  
 <span data-ttu-id="bedc0-170">![使用 VisualBrush 绘制的矩形](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span><span class="sxs-lookup"><span data-stu-id="bedc0-170">![A rectangle painted using a VisualBrush](./media/graphicsmm-brush-ovw-visualbrush.jpg "graphicsmm_brush_ovw_visualbrush")</span></span>  
<span data-ttu-id="bedc0-171">使用 System.windows.media.visualbrush> 绘制的矩形</span><span class="sxs-lookup"><span data-stu-id="bedc0-171">A Rectangle painted using a VisualBrush</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTypesExample.cs#graphicsmmvisualbrushexampleinline)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtypesexample.vb#graphicsmmvisualbrushexampleinline)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMVisualBrushExampleInline](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTypesExample.xaml#graphicsmmvisualbrushexampleinline)]  
  
 <span data-ttu-id="bedc0-172">有关类的详细信息 <xref:System.Windows.Media.VisualBrush> ，请参阅[利用图像、绘图和视觉对象进行绘制](painting-with-images-drawings-and-visuals.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-172">For more information about the <xref:System.Windows.Media.VisualBrush> class, see [Painting with Images, Drawings, and Visuals](painting-with-images-drawings-and-visuals.md).</span></span>  
  
<a name="paintwithpredefinedbrushesandsystemcolors"></a>
## <a name="paint-using-predefined-and-system-brushes"></a><span data-ttu-id="bedc0-173">使用预定义画笔和系统画笔进行绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-173">Paint using Predefined and System Brushes</span></span>  
 <span data-ttu-id="bedc0-174">为方便起见，Windows Presentation Foundation （WPF）提供了一组预定义的和系统画笔，可用于绘制对象。</span><span class="sxs-lookup"><span data-stu-id="bedc0-174">For convenience, Windows Presentation Foundation (WPF) provides a set of predefined and system brushes that you can use to paint objects.</span></span>  
  
- <span data-ttu-id="bedc0-175">有关可用预定义画笔的列表，请参见 <xref:System.Windows.Media.Brushes> 类。</span><span class="sxs-lookup"><span data-stu-id="bedc0-175">For a list of available predefined brushes, see the <xref:System.Windows.Media.Brushes> class.</span></span> <span data-ttu-id="bedc0-176">有关演示如何使用预定义画笔的示例，请参阅[使用纯色绘制区域](how-to-paint-an-area-with-a-solid-color.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-176">For an example showing how to use a predefined brush, see [Paint an Area with a Solid Color](how-to-paint-an-area-with-a-solid-color.md).</span></span>  
  
- <span data-ttu-id="bedc0-177">有关可用系统画笔的列表，请参见 <xref:System.Windows.SystemColors> 类。</span><span class="sxs-lookup"><span data-stu-id="bedc0-177">For a list of available system brushes, see the <xref:System.Windows.SystemColors> class.</span></span> <span data-ttu-id="bedc0-178">有关示例，请参阅[使用系统画笔绘制区域](how-to-paint-an-area-with-a-system-brush.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-178">For an example, see [Paint an Area with a System Brush](how-to-paint-an-area-with-a-system-brush.md).</span></span>  
  
<a name="commonbrushfeatures"></a>
## <a name="common-brush-features"></a><span data-ttu-id="bedc0-179">常用画笔功能</span><span class="sxs-lookup"><span data-stu-id="bedc0-179">Common Brush Features</span></span>  
 <span data-ttu-id="bedc0-180"><xref:System.Windows.Media.Brush>对象提供 <xref:System.Windows.Media.Brush.Opacity%2A> 的属性可用于使画笔透明或部分透明。</span><span class="sxs-lookup"><span data-stu-id="bedc0-180"><xref:System.Windows.Media.Brush> objects provide an <xref:System.Windows.Media.Brush.Opacity%2A> property that can be used to make a brush transparent or partially transparent.</span></span> <span data-ttu-id="bedc0-181"><xref:System.Windows.Media.Brush.Opacity%2A>值0使画笔完全透明，而 <xref:System.Windows.Media.Brush.Opacity%2A> 值1则使画笔完全不透明。</span><span class="sxs-lookup"><span data-stu-id="bedc0-181">An <xref:System.Windows.Media.Brush.Opacity%2A> value of 0 makes a brush completely transparent, while an <xref:System.Windows.Media.Brush.Opacity%2A> value of 1 makes a brush completely opaque.</span></span> <span data-ttu-id="bedc0-182">下面的示例使用 <xref:System.Windows.Media.Brush.Opacity%2A> 属性，使 <xref:System.Windows.Media.SolidColorBrush> 25% 不透明。</span><span class="sxs-lookup"><span data-stu-id="bedc0-182">The following example uses the <xref:System.Windows.Media.Brush.Opacity%2A> property to make a <xref:System.Windows.Media.SolidColorBrush> 25 percent opaque.</span></span>  
  
 [!code-xaml[BrushOverviewExamples_snip#OpacityExample1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushOverviewExamples_snip/XAML/OpacityExample.xaml#opacityexample1xaml)]  
  
 [!code-csharp[BrushOverviewExamples_snip#OpacityExample1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushOverviewExamples_snip/CSharp/OpacityExample.cs#opacityexample1csharp)]  
  
 <span data-ttu-id="bedc0-183">如果画笔包含部分透明的颜色，则使用画笔的不透明度值组合颜色的不透明度值。</span><span class="sxs-lookup"><span data-stu-id="bedc0-183">If the brush contains colors that are partially transparent, the opacity value of the color is combined through multiplication with the opacity value of the brush.</span></span> <span data-ttu-id="bedc0-184">例如，如果画笔的不透明度值为0.5，并且画笔中使用的颜色的不透明度值为0.5，则输出颜色的不透明度值为0.25。</span><span class="sxs-lookup"><span data-stu-id="bedc0-184">For example, if a brush has an opacity value of 0.5 and a color used in the brush also has an opacity value of 0.5, the output color has an opacity value of 0.25.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bedc0-185">更改画笔的不透明度值比使用其属性更改整个元素的不透明度更为有效 <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-185">It's more efficient to change the opacity value of a brush than it is to change the opacity of an entire element using its <xref:System.Windows.UIElement.Opacity%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="bedc0-186">您可以使用画笔的或属性来旋转、缩放、倾斜和平移画笔的 <xref:System.Windows.Media.Brush.Transform%2A> 内容 <xref:System.Windows.Media.Brush.RelativeTransform%2A> 。</span><span class="sxs-lookup"><span data-stu-id="bedc0-186">You can rotate, scale, skew, and translate a brush's content by using its <xref:System.Windows.Media.Brush.Transform%2A> or <xref:System.Windows.Media.Brush.RelativeTransform%2A> properties.</span></span> <span data-ttu-id="bedc0-187">有关详细信息，请参阅[刷子转换概述](brush-transformation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-187">For more information, see [Brush Transformation Overview](brush-transformation-overview.md).</span></span>  
  
 <span data-ttu-id="bedc0-188">由于它们是 <xref:System.Windows.Media.Animation.Animatable> 对象，因此 <xref:System.Windows.Media.Brush> 可以对对象进行动画处理。</span><span class="sxs-lookup"><span data-stu-id="bedc0-188">Because they are <xref:System.Windows.Media.Animation.Animatable> objects, <xref:System.Windows.Media.Brush> objects can be animated.</span></span> <span data-ttu-id="bedc0-189">有关详细信息，请参阅 [动画概述](animation-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-189">For more information, see [Animation Overview](animation-overview.md).</span></span>  
  
<a name="freezable_features"></a>
### <a name="freezable-features"></a><span data-ttu-id="bedc0-190">Freezable 功能</span><span class="sxs-lookup"><span data-stu-id="bedc0-190">Freezable Features</span></span>  
 <span data-ttu-id="bedc0-191">由于该类继承自 <xref:System.Windows.Freezable> 类，因此 <xref:System.Windows.Media.Brush> 该类提供若干特殊功能： <xref:System.Windows.Media.Brush> 对象可以声明为[资源](../../../desktop-wpf/fundamentals/xaml-resources-define.md)、在多个对象之间共享以及进行克隆。</span><span class="sxs-lookup"><span data-stu-id="bedc0-191">Because it inherits from the <xref:System.Windows.Freezable> class, the <xref:System.Windows.Media.Brush> class provides several special features: <xref:System.Windows.Media.Brush> objects can be declared as [resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md), shared among multiple objects, and cloned.</span></span> <span data-ttu-id="bedc0-192">此外， <xref:System.Windows.Media.Brush> 除之外的所有类型都 <xref:System.Windows.Media.VisualBrush> 可以变为只读以提高性能并使其成为线程安全的。</span><span class="sxs-lookup"><span data-stu-id="bedc0-192">In addition, all the <xref:System.Windows.Media.Brush> types except <xref:System.Windows.Media.VisualBrush> can be made read-only to improve performance and made thread-safe.</span></span>  
  
 <span data-ttu-id="bedc0-193">有关对象提供的不同功能的详细信息 <xref:System.Windows.Freezable> ，请参阅可[冻结对象概述](../advanced/freezable-objects-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="bedc0-193">For more information about the different features provided by <xref:System.Windows.Freezable> objects, see [Freezable Objects Overview](../advanced/freezable-objects-overview.md).</span></span>  
  
 <span data-ttu-id="bedc0-194">有关无法冻结对象的原因的详细信息 <xref:System.Windows.Media.VisualBrush> ，请参阅 " <xref:System.Windows.Media.VisualBrush> 类型" 页。</span><span class="sxs-lookup"><span data-stu-id="bedc0-194">For more information on why <xref:System.Windows.Media.VisualBrush> objects cannot be frozen, see the <xref:System.Windows.Media.VisualBrush> type page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bedc0-195">另请参阅</span><span class="sxs-lookup"><span data-stu-id="bedc0-195">See also</span></span>

- <xref:System.Windows.Media.Brush>
- <xref:System.Windows.Media.Brushes>
- [<span data-ttu-id="bedc0-196">使用纯色和渐变进行绘制概述</span><span class="sxs-lookup"><span data-stu-id="bedc0-196">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="bedc0-197">使用图像、图形和视觉对象进行绘制</span><span class="sxs-lookup"><span data-stu-id="bedc0-197">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="bedc0-198">Freezable 对象概述</span><span class="sxs-lookup"><span data-stu-id="bedc0-198">Freezable Objects Overview</span></span>](../advanced/freezable-objects-overview.md)
- [<span data-ttu-id="bedc0-199">画笔示例</span><span class="sxs-lookup"><span data-stu-id="bedc0-199">Brushes Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)
- [<span data-ttu-id="bedc0-200">ImageBrush 示例</span><span class="sxs-lookup"><span data-stu-id="bedc0-200">ImageBrush Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)
- [<span data-ttu-id="bedc0-201">VisualBrush 示例</span><span class="sxs-lookup"><span data-stu-id="bedc0-201">VisualBrush Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush)
- [<span data-ttu-id="bedc0-202">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="bedc0-202">How-to Topics</span></span>](brushes-how-to-topics.md)
- [<span data-ttu-id="bedc0-203">其他性能建议</span><span class="sxs-lookup"><span data-stu-id="bedc0-203">Other Performance Recommendations</span></span>](../advanced/optimizing-performance-other-recommendations.md)
