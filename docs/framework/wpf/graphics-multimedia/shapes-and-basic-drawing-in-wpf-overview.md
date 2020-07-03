---
title: 形状和基本绘图概述
description: 在 Windows Presentation Foundation （WPF）中使用随时可用的形状和多层渲染服务增强用户界面。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853692"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="6dacc-103">WPF 中的形状和基本图形概述</span><span class="sxs-lookup"><span data-stu-id="6dacc-103">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="6dacc-104">本主题概述了如何使用对象进行绘制 <xref:System.Windows.Shapes.Shape> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-104">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="6dacc-105"><xref:System.Windows.Shapes.Shape>是的一种类型 <xref:System.Windows.UIElement> ，它使您能够在屏幕上绘制形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-105">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="6dacc-106">由于它们是 UI 元素，因此 <xref:System.Windows.Shapes.Shape> 可以在 <xref:System.Windows.Controls.Panel> 元素和大多数控件内使用对象。</span><span class="sxs-lookup"><span data-stu-id="6dacc-106">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="6dacc-107">为图形和绘制服务提供多层访问。</span><span class="sxs-lookup"><span data-stu-id="6dacc-107">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="6dacc-108">在顶层， <xref:System.Windows.Shapes.Shape> 对象易于使用，并提供许多有用的功能，如布局和参与 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 事件系统。</span><span class="sxs-lookup"><span data-stu-id="6dacc-108">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="6dacc-109">形状对象</span><span class="sxs-lookup"><span data-stu-id="6dacc-109">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="6dacc-110">提供了大量随时可用的 <xref:System.Windows.Shapes.Shape> 对象。</span><span class="sxs-lookup"><span data-stu-id="6dacc-110">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="6dacc-111">所有形状对象均从 <xref:System.Windows.Shapes.Shape> 类继承。</span><span class="sxs-lookup"><span data-stu-id="6dacc-111">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="6dacc-112">可用形状对象包括 <xref:System.Windows.Shapes.Ellipse> 、 <xref:System.Windows.Shapes.Line> 、 <xref:System.Windows.Shapes.Path> 、 <xref:System.Windows.Shapes.Polygon> 、 <xref:System.Windows.Shapes.Polyline> 和 <xref:System.Windows.Shapes.Rectangle> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-112">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="6dacc-113"><xref:System.Windows.Shapes.Shape>对象共享以下公共属性。</span><span class="sxs-lookup"><span data-stu-id="6dacc-113"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="6dacc-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>：描述如何绘制形状的轮廓。</span><span class="sxs-lookup"><span data-stu-id="6dacc-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="6dacc-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>：描述形状边框的粗细。</span><span class="sxs-lookup"><span data-stu-id="6dacc-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="6dacc-116"><xref:System.Windows.Shapes.Shape.Fill%2A>：描述如何绘制形状的内部。</span><span class="sxs-lookup"><span data-stu-id="6dacc-116"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="6dacc-117">用于指定坐标和顶点的数据属性，以与设备无关的像素来度量。</span><span class="sxs-lookup"><span data-stu-id="6dacc-117">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="6dacc-118">由于它们是从派生的 <xref:System.Windows.UIElement> ，因此可以在面板和大多数控件内使用形状对象。</span><span class="sxs-lookup"><span data-stu-id="6dacc-118">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="6dacc-119"><xref:System.Windows.Controls.Canvas>面板是创建复杂绘图的一个特别不错的选择，因为它支持其子对象的绝对定位。</span><span class="sxs-lookup"><span data-stu-id="6dacc-119">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="6dacc-120"><xref:System.Windows.Shapes.Line>利用类，您可以在两个点之间绘制一条线。</span><span class="sxs-lookup"><span data-stu-id="6dacc-120">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="6dacc-121">以下示例演示了指定线坐标和笔划属性的几种方法。</span><span class="sxs-lookup"><span data-stu-id="6dacc-121">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="6dacc-122">下图显示了呈现的 <xref:System.Windows.Shapes.Line> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-122">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="6dacc-123">![直线图示](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="6dacc-123">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="6dacc-124">尽管 <xref:System.Windows.Shapes.Line> 类提供了 <xref:System.Windows.Shapes.Shape.Fill%2A> 属性，但设置它不起作用，因为没有 <xref:System.Windows.Shapes.Line> 区域。</span><span class="sxs-lookup"><span data-stu-id="6dacc-124">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="6dacc-125">另一个常见的形状是 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-125">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="6dacc-126"><xref:System.Windows.Shapes.Ellipse>通过定义形状的 <xref:System.Windows.FrameworkElement.Width%2A> 和属性来创建 <xref:System.Windows.FrameworkElement.Height%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-126">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="6dacc-127">若要绘制一个圆，请指定 <xref:System.Windows.Shapes.Ellipse> 其 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 值相等的。</span><span class="sxs-lookup"><span data-stu-id="6dacc-127">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="6dacc-128">下图显示了呈现的的示例 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-128">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="6dacc-129">![椭圆图示](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="6dacc-129">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="6dacc-130">使用路径和几何图形</span><span class="sxs-lookup"><span data-stu-id="6dacc-130">Using Paths and Geometries</span></span>  
 <span data-ttu-id="6dacc-131"><xref:System.Windows.Shapes.Path>利用类，您可以绘制曲线和复杂形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-131">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="6dacc-132">这些曲线和形状使用对象进行描述 <xref:System.Windows.Media.Geometry> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-132">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="6dacc-133">若要使用 <xref:System.Windows.Shapes.Path> ，请创建 <xref:System.Windows.Media.Geometry> 并使用它来设置 <xref:System.Windows.Shapes.Path> 对象的 <xref:System.Windows.Shapes.Path.Data%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6dacc-133">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="6dacc-134">有多种 <xref:System.Windows.Media.Geometry> 可供选择的对象。</span><span class="sxs-lookup"><span data-stu-id="6dacc-134">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="6dacc-135"><xref:System.Windows.Media.LineGeometry>、 <xref:System.Windows.Media.RectangleGeometry> 和 <xref:System.Windows.Media.EllipseGeometry> 类描述相对简单的形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-135">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="6dacc-136">若要创建更复杂的形状或创建曲线，请使用 <xref:System.Windows.Media.PathGeometry> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-136">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="6dacc-137">PathGeometry and PathSegments</span><span class="sxs-lookup"><span data-stu-id="6dacc-137">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="6dacc-138"><xref:System.Windows.Media.PathGeometry>对象由一个或多个 <xref:System.Windows.Media.PathFigure> 对象组成，每个对象 <xref:System.Windows.Media.PathFigure> 表示不同的 "图形" 或形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-138"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="6dacc-139">每个 <xref:System.Windows.Media.PathFigure> 对象都由一个或多个 <xref:System.Windows.Media.PathSegment> 对象组成，每个对象表示图形或形状的连接部分。</span><span class="sxs-lookup"><span data-stu-id="6dacc-139">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="6dacc-140">段类型包括以下内容： <xref:System.Windows.Media.LineSegment> 、 <xref:System.Windows.Media.BezierSegment> 和 <xref:System.Windows.Media.ArcSegment> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-140">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="6dacc-141">在下面的示例中， <xref:System.Windows.Shapes.Path> 用于绘制二次贝塞尔曲线。</span><span class="sxs-lookup"><span data-stu-id="6dacc-141">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="6dacc-142">下图显示了呈现的形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-142">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="6dacc-143">![路径图示](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="6dacc-143">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="6dacc-144">有关 <xref:System.Windows.Media.PathGeometry> 和其他类的详细信息 <xref:System.Windows.Media.Geometry> ，请参阅[几何概述](geometry-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6dacc-144">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="6dacc-145">XAML 缩写语法</span><span class="sxs-lookup"><span data-stu-id="6dacc-145">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="6dacc-146">在中 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ，还可以使用特殊的缩写语法来描述 <xref:System.Windows.Shapes.Path> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-146">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="6dacc-147">以下示例中，使用了缩写语法绘制复杂的形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-147">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="6dacc-148">下图显示了一个呈现的 <xref:System.Windows.Shapes.Path> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-148">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="6dacc-149">![路径图示](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="6dacc-149">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="6dacc-150"><xref:System.Windows.Shapes.Path.Data%2A>特性字符串以 "moveto" 命令开头，由 M 指示，后者为的坐标系统中的路径建立起点 <xref:System.Windows.Controls.Canvas> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-150">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="6dacc-151"><xref:System.Windows.Shapes.Path>数据参数区分大小写。</span><span class="sxs-lookup"><span data-stu-id="6dacc-151"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="6dacc-152">大写 M 指示新的当前点的绝对位置。</span><span class="sxs-lookup"><span data-stu-id="6dacc-152">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="6dacc-153">小写字母 m 指示相对坐标。</span><span class="sxs-lookup"><span data-stu-id="6dacc-153">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="6dacc-154">第一段是一条三次贝塞尔曲线，该曲线以 (100,200) 开始，至 (400,175) 结束，使用 (100,25) 和 (400,350) 这两个控制点绘制。</span><span class="sxs-lookup"><span data-stu-id="6dacc-154">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="6dacc-155">此段由属性字符串中的 C 命令指示 <xref:System.Windows.Shapes.Path.Data%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-155">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="6dacc-156">同样，大写的 C 指示绝对路径；小写的 c 指示相对路径。</span><span class="sxs-lookup"><span data-stu-id="6dacc-156">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="6dacc-157">第二段以绝对水平“lineto”命令 H 开头，它指定绘制一条从前面的子路径的终点 (400,175) 到新终点 (280,175) 的直线。</span><span class="sxs-lookup"><span data-stu-id="6dacc-157">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="6dacc-158">由于它是水平的 "lineto" 命令，因此指定的值为*x*坐标。</span><span class="sxs-lookup"><span data-stu-id="6dacc-158">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="6dacc-159">有关完整的路径语法，请参阅 <xref:System.Windows.Shapes.Path.Data%2A> 引用和[使用 System.windows.media.pathgeometry> 创建形状](how-to-create-a-shape-by-using-a-pathgeometry.md)。</span><span class="sxs-lookup"><span data-stu-id="6dacc-159">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="6dacc-160">绘制形状</span><span class="sxs-lookup"><span data-stu-id="6dacc-160">Painting Shapes</span></span>  
 <span data-ttu-id="6dacc-161"><xref:System.Windows.Media.Brush>对象用于绘制形状的 <xref:System.Windows.Shapes.Shape.Stroke%2A> 和 <xref:System.Windows.Shapes.Shape.Fill%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-161"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="6dacc-162">在下面的示例中，指定了的笔划和填充 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-162">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="6dacc-163">注意画笔属性的有效输入可以是关键字或十六进制颜色值。</span><span class="sxs-lookup"><span data-stu-id="6dacc-163">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="6dacc-164">有关可用颜色关键字的详细信息，请参阅 <xref:System.Windows.Media.Colors> 命名空间中类的属性 <xref:System.Windows.Media> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-164">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
```xaml
<Canvas Background="LightGray">
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 <span data-ttu-id="6dacc-165">下图显示了呈现的 <xref:System.Windows.Shapes.Ellipse> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-165">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="6dacc-166">![椭圆](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="6dacc-166">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="6dacc-167">或者，可以使用属性元素语法显式创建 <xref:System.Windows.Media.SolidColorBrush> 对象，以使用纯色绘制形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-167">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 <span data-ttu-id="6dacc-168">下图显示了呈现的形状。</span><span class="sxs-lookup"><span data-stu-id="6dacc-168">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="6dacc-169">![SolidColorBrush 图示](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="6dacc-169">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="6dacc-170">还可以使用渐变、图像、模式等绘制形状的笔划或填充。</span><span class="sxs-lookup"><span data-stu-id="6dacc-170">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="6dacc-171">有关详细信息，请参阅[采用纯色和渐变进行绘制概述](painting-with-solid-colors-and-gradients-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="6dacc-171">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="6dacc-172">可拉伸的形状</span><span class="sxs-lookup"><span data-stu-id="6dacc-172">Stretchable Shapes</span></span>  
 <span data-ttu-id="6dacc-173"><xref:System.Windows.Shapes.Line>、、 <xref:System.Windows.Shapes.Path> 、 <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> 和类都 <xref:System.Windows.Shapes.Rectangle> 有 <xref:System.Windows.Shapes.Shape.Stretch%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6dacc-173">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="6dacc-174">此属性确定如何 <xref:System.Windows.Shapes.Shape> 拉伸对象的内容（要绘制的形状）以填充 <xref:System.Windows.Shapes.Shape> 对象的布局空间。</span><span class="sxs-lookup"><span data-stu-id="6dacc-174">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="6dacc-175"><xref:System.Windows.Shapes.Shape>对象的布局空间是布局系统分配的空间量 <xref:System.Windows.Shapes.Shape> ，因为显式 <xref:System.Windows.FrameworkElement.Width%2A> 和设置， <xref:System.Windows.FrameworkElement.Height%2A> 或者因为其 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> 和设置而设置 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-175">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="6dacc-176">有关 Windows Presentation Foundation 中布局的其他信息，请参阅[布局](../advanced/layout.md)概述。</span><span class="sxs-lookup"><span data-stu-id="6dacc-176">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="6dacc-177">Stretch 属性采用下列值之一：</span><span class="sxs-lookup"><span data-stu-id="6dacc-177">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="6dacc-178"><xref:System.Windows.Media.Stretch.None>： <xref:System.Windows.Shapes.Shape> 不拉伸对象的内容。</span><span class="sxs-lookup"><span data-stu-id="6dacc-178"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="6dacc-179"><xref:System.Windows.Media.Stretch.Fill>： <xref:System.Windows.Shapes.Shape> 拉伸对象的内容以填充其布局空间。</span><span class="sxs-lookup"><span data-stu-id="6dacc-179"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="6dacc-180">不保留纵横比。</span><span class="sxs-lookup"><span data-stu-id="6dacc-180">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="6dacc-181"><xref:System.Windows.Media.Stretch.Uniform>： <xref:System.Windows.Shapes.Shape> 对象的内容会尽可能拉伸以填充其布局空间，同时保留其原始纵横比。</span><span class="sxs-lookup"><span data-stu-id="6dacc-181"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="6dacc-182"><xref:System.Windows.Media.Stretch.UniformToFill>： <xref:System.Windows.Shapes.Shape> 拉伸对象的内容以完全填充其布局空间，同时保留其原始纵横比。</span><span class="sxs-lookup"><span data-stu-id="6dacc-182"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="6dacc-183">请注意，当 <xref:System.Windows.Shapes.Shape> 拉伸对象的内容时，将在 <xref:System.Windows.Shapes.Shape> 拉伸后绘制对象的轮廓。</span><span class="sxs-lookup"><span data-stu-id="6dacc-183">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="6dacc-184">在下面的示例中， <xref:System.Windows.Shapes.Polygon> 用于绘制从（0，0）到（0，1）到（1，1）的非常小的三角形。</span><span class="sxs-lookup"><span data-stu-id="6dacc-184">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="6dacc-185"><xref:System.Windows.Shapes.Polygon>对象的 <xref:System.Windows.FrameworkElement.Width%2A> 和 <xref:System.Windows.FrameworkElement.Height%2A> 设置为100，并将其 stretch 属性设置为 Fill。</span><span class="sxs-lookup"><span data-stu-id="6dacc-185">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="6dacc-186">因此， <xref:System.Windows.Shapes.Polygon> 会拉伸对象的内容（三角形）以填充更大的空间。</span><span class="sxs-lookup"><span data-stu-id="6dacc-186">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>
## <a name="transforming-shapes"></a><span data-ttu-id="6dacc-187">转换形状</span><span class="sxs-lookup"><span data-stu-id="6dacc-187">Transforming Shapes</span></span>  
 <span data-ttu-id="6dacc-188"><xref:System.Windows.Media.Transform>类提供在二维平面中转换形状的方式。</span><span class="sxs-lookup"><span data-stu-id="6dacc-188">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="6dacc-189">不同类型的转换包括旋转（ <xref:System.Windows.Media.RotateTransform> ）、缩放（ <xref:System.Windows.Media.ScaleTransform> ）、倾斜（ <xref:System.Windows.Media.SkewTransform> ）和平移（ <xref:System.Windows.Media.TranslateTransform> ）。</span><span class="sxs-lookup"><span data-stu-id="6dacc-189">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="6dacc-190">应用于形状的常见转换就是旋转。</span><span class="sxs-lookup"><span data-stu-id="6dacc-190">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="6dacc-191">若要旋转形状，请创建 <xref:System.Windows.Media.RotateTransform> 并指定其 <xref:System.Windows.Media.RotateTransform.Angle%2A> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-191">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="6dacc-192"><xref:System.Windows.Media.RotateTransform.Angle%2A>45 的以顺时针方向旋转元素，45度为90，顺时针旋转元素 90; 依此类推。</span><span class="sxs-lookup"><span data-stu-id="6dacc-192">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="6dacc-193"><xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> 如果要控制旋转元素的点，请设置和属性。</span><span class="sxs-lookup"><span data-stu-id="6dacc-193">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="6dacc-194">这些属性值在被转换的元素的坐标空间中表示。</span><span class="sxs-lookup"><span data-stu-id="6dacc-194">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="6dacc-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A>和 <xref:System.Windows.Media.RotateTransform.CenterY%2A> 的默认值为零。</span><span class="sxs-lookup"><span data-stu-id="6dacc-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="6dacc-196">最后，将应用 <xref:System.Windows.Media.RotateTransform> 到元素。</span><span class="sxs-lookup"><span data-stu-id="6dacc-196">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="6dacc-197">如果不希望转换影响布局，请设置形状的 <xref:System.Windows.UIElement.RenderTransform%2A> 属性。</span><span class="sxs-lookup"><span data-stu-id="6dacc-197">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="6dacc-198">在下面的示例中， <xref:System.Windows.Media.RotateTransform> 用于在形状的左上角（0，0）旋转形状45度。</span><span class="sxs-lookup"><span data-stu-id="6dacc-198">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="6dacc-199">在以下示例中，另一个形状也旋转了 45 度，但这次它围绕点 (25,50) 旋转。</span><span class="sxs-lookup"><span data-stu-id="6dacc-199">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="6dacc-200">下图显示了应用两次转换的结果。</span><span class="sxs-lookup"><span data-stu-id="6dacc-200">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="6dacc-201">![以不同中心点进行的 45 度旋转](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="6dacc-201">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="6dacc-202">在前面的示例中，对每一个形状对象应用了一次转换。</span><span class="sxs-lookup"><span data-stu-id="6dacc-202">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="6dacc-203">若要将多个转换应用于一个形状（或任何其他 UI 元素），请使用 <xref:System.Windows.Media.TransformGroup> 。</span><span class="sxs-lookup"><span data-stu-id="6dacc-203">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dacc-204">另请参阅</span><span class="sxs-lookup"><span data-stu-id="6dacc-204">See also</span></span>

- [<span data-ttu-id="6dacc-205">二维图形和图像处理</span><span class="sxs-lookup"><span data-stu-id="6dacc-205">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="6dacc-206">使用纯色和渐变进行绘制概述</span><span class="sxs-lookup"><span data-stu-id="6dacc-206">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="6dacc-207">Geometry 概述</span><span class="sxs-lookup"><span data-stu-id="6dacc-207">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="6dacc-208">演练：我的第一个 WPF 桌面应用程序</span><span class="sxs-lookup"><span data-stu-id="6dacc-208">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="6dacc-209">动画概述</span><span class="sxs-lookup"><span data-stu-id="6dacc-209">Animation Overview</span></span>](animation-overview.md)
