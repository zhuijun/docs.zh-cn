---
title: 如何：绘制椭圆或圆
description: 了解如何使用 Windows Presentation Foundation （WPF）中的轮廓粗细和内部颜色的选项绘制椭圆或圆。
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853561"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="53857-103">如何：绘制椭圆或圆</span><span class="sxs-lookup"><span data-stu-id="53857-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="53857-104">此示例演示如何使用元素绘制省略号和圆 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="53857-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="53857-105">若要绘制一个椭圆，请创建一个 <xref:System.Windows.Shapes.Ellipse> 元素，并指定其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 。</span><span class="sxs-lookup"><span data-stu-id="53857-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="53857-106">使用其 <xref:System.Windows.Shapes.Shape.Fill%2A> 属性指定 <xref:System.Windows.Media.Brush> 用来绘制椭圆内部的。</span><span class="sxs-lookup"><span data-stu-id="53857-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="53857-107">使用其 <xref:System.Windows.Shapes.Shape.Stroke%2A> 属性指定 <xref:System.Windows.Media.Brush> 用来绘制椭圆轮廓的。</span><span class="sxs-lookup"><span data-stu-id="53857-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="53857-108"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>属性指定椭圆轮廓的粗细。</span><span class="sxs-lookup"><span data-stu-id="53857-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="53857-109">若要绘制一个圆，请使 <xref:System.Windows.FrameworkElement.Width%2A> 元素的和彼此 <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> 相等。</span><span class="sxs-lookup"><span data-stu-id="53857-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="53857-110">下面的示例在中绘制四个 <xref:System.Windows.Shapes.Ellipse> 元素 <xref:System.Windows.Controls.Canvas> 。</span><span class="sxs-lookup"><span data-stu-id="53857-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53857-111">示例</span><span class="sxs-lookup"><span data-stu-id="53857-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="53857-112">虽然此示例使用 <xref:System.Windows.Controls.Canvas> 来包含省略号，但你可以将椭圆形元素（和所有其他形状元素）与 <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Control> 支持非文本内容的任何或一起使用。</span><span class="sxs-lookup"><span data-stu-id="53857-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="53857-113">此示例摘自一个更大的示例;有关完整示例，请参阅[形状元素示例](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)。</span><span class="sxs-lookup"><span data-stu-id="53857-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53857-114">另请参阅</span><span class="sxs-lookup"><span data-stu-id="53857-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="53857-115">形状元素示例</span><span class="sxs-lookup"><span data-stu-id="53857-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
