---
title: 装饰器概述
description: 了解 Windows Presentation Foundation 装饰器，一种特殊类型的 FrameworkElement，用于向用户提供提示，例如元素的函数句柄。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167731"
---
# <a name="adorners-overview"></a><span data-ttu-id="ba6e9-103">装饰器概述</span><span class="sxs-lookup"><span data-stu-id="ba6e9-103">Adorners Overview</span></span>

<span data-ttu-id="ba6e9-104">装饰器是一种特殊类型的 <xref:System.Windows.FrameworkElement> ，用于向用户提供视觉提示。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-104">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="ba6e9-105">装饰器有很多用途，可用来向元素添加功能句柄，或者提供有关某个控件的状态信息。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-105">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="ba6e9-106">关于装饰器</span><span class="sxs-lookup"><span data-stu-id="ba6e9-106">About Adorners</span></span>

<span data-ttu-id="ba6e9-107"><xref:System.Windows.Documents.Adorner>是 <xref:System.Windows.FrameworkElement> 绑定到的自定义 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-107">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="ba6e9-108">装饰器呈现在中 <xref:System.Windows.Documents.AdornerLayer> ，后者是始终位于装饰元素或装饰元素集合之上的呈现图面。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-108">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="ba6e9-109">装饰器的呈现独立于呈现 <xref:System.Windows.UIElement> 装饰器所绑定到的。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-109">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="ba6e9-110">装饰器通常使用位于装饰元素左上角的标准2D 坐标原点，相对于其绑定到的元素进行定位。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-110">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="ba6e9-111">装饰器的常见应用包括：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-111">Common applications for adorners include:</span></span>

- <span data-ttu-id="ba6e9-112">将函数句柄添加到 <xref:System.Windows.UIElement> ，使用户能够以某种方式（调整大小、旋转、重定位等）操作元素。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-112">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="ba6e9-113">提供视觉反馈以指示各种状态，或者响应各种事件。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-113">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="ba6e9-114">覆盖上的视觉修饰 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-114">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="ba6e9-115">直观屏蔽或重写的部分或全部 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-115">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="ba6e9-116">提供用于装饰视觉元素的基本框架。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-116">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="ba6e9-117">下表列出了装饰对象时使用的主要类型及其用途。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-117">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="ba6e9-118">下面是几个用法示例：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-118">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="ba6e9-119">一个抽象基类，从中继承所有的具体装饰器实现。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-119">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="ba6e9-120">一个类，表示一个或多个装饰元素的装饰器的呈现层。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-120">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="ba6e9-121">一个类，使装饰器层与元素集合相关联。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-121">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="ba6e9-122">实现自定义装饰器</span><span class="sxs-lookup"><span data-stu-id="ba6e9-122">Implementing a Custom Adorner</span></span>

<span data-ttu-id="ba6e9-123">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 提供的装饰器框架的主要用于支持创建自定义装饰器。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-123">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="ba6e9-124">通过实现继承自抽象类的类来创建自定义装饰器 <xref:System.Windows.Documents.Adorner> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-124">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="ba6e9-125">的父级 <xref:System.Windows.Documents.Adorner> 是 <xref:System.Windows.Documents.AdornerLayer> 呈现的 <xref:System.Windows.Documents.Adorner> ，而不是要装饰的元素。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-125">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="ba6e9-126">下面的示例展示了实现简单装饰器的类。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-126">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="ba6e9-127">示例装饰器只是使用圆圈装饰的角 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-127">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="ba6e9-128">下图显示了应用于的 SimpleCircleAdorner <xref:System.Windows.Controls.TextBox> ：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-128">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![显示所装饰文本框的屏幕截图。](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="ba6e9-130">装饰器的呈现行为</span><span class="sxs-lookup"><span data-stu-id="ba6e9-130">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="ba6e9-131">请务必注意，装饰器不包括任何继承呈现行为，确保装饰器呈现是装饰器实施者的责任。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-131">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="ba6e9-132">实现呈现行为的常见方法是重写 <xref:System.Windows.UIElement.OnRender%2A> 方法，并使用一个或多个 <xref:System.Windows.Media.DrawingContext> 对象根据需要呈现装饰器的视觉对象（如上面的示例所示）。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-132">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="ba6e9-133">放置在装饰器层中的任何内容将呈现在设置的其他任何样式的顶部。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-133">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="ba6e9-134">换言之，装饰器始终以可见的方式位于顶部，无法使用 z 顺序重写。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-134">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="ba6e9-135">事件和命中测试</span><span class="sxs-lookup"><span data-stu-id="ba6e9-135">Events and Hit Testing</span></span>

<span data-ttu-id="ba6e9-136">装饰器接收输入事件的方式与任何其他 <xref:System.Windows.FrameworkElement> 的一样。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-136">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="ba6e9-137">因为装饰器的 z 顺序始终高于它装饰的元素，所以装饰器 <xref:System.Windows.UIElement.Drop> <xref:System.Windows.UIElement.MouseMove> 会接收可能适用于基础装饰元素的输入事件（如或）。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-137">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="ba6e9-138">装饰器可以侦听某些输入事件，并通过重新引发这些事件将它们传递到基础装饰元素。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-138">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="ba6e9-139">若要启用装饰器下元素的传递命中测试，请在装饰器上将 "命中测试" <xref:System.Windows.UIElement.IsHitTestVisible%2A> 属性设置为**false** 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-139">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="ba6e9-140">有关命中测试的详细信息，请参阅[可视化层中的命中测试](../graphics-multimedia/hit-testing-in-the-visual-layer.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-140">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="ba6e9-141">装饰单个 UIElement</span><span class="sxs-lookup"><span data-stu-id="ba6e9-141">Adorning a Single UIElement</span></span>

<span data-ttu-id="ba6e9-142">若要将装饰器绑定到特定的 <xref:System.Windows.UIElement> ，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="ba6e9-143">调用静态方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，以获取 <xref:System.Windows.Documents.AdornerLayer> 要装饰的的对象 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="ba6e9-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>从指定的开始向上遍历可视化树， <xref:System.Windows.UIElement> 并返回它找到的第一个装饰器层。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="ba6e9-145">（如果未发现装饰器层，该方法将返回 null。）</span><span class="sxs-lookup"><span data-stu-id="ba6e9-145">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="ba6e9-146">调用 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法以将装饰器绑定到目标 <xref:System.Windows.UIElement> 。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="ba6e9-147">下面的示例将 SimpleCircleAdorner （如上所示）绑定到一个 <xref:System.Windows.Controls.TextBox> 命名*myTextBox*：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="ba6e9-148">目前不支持使用 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 将装饰器绑定到另一个元素。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="ba6e9-149">装饰面板的子级</span><span class="sxs-lookup"><span data-stu-id="ba6e9-149">Adorning the Children of a Panel</span></span>

<span data-ttu-id="ba6e9-150">若要将装饰器绑定到的子节点 <xref:System.Windows.Controls.Panel> ，请执行以下步骤：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="ba6e9-151">调用 `static` 方法 <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> ，为要装饰其子级的元素查找装饰器层。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="ba6e9-152">枚举父元素的子级并调用 <xref:System.Windows.Documents.AdornerLayer.Add%2A> 方法，将装饰器绑定到每个子元素。</span><span class="sxs-lookup"><span data-stu-id="ba6e9-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="ba6e9-153">下面的示例将 SimpleCircleAdorner （如上所示）绑定到 <xref:System.Windows.Controls.StackPanel> 名为*myStackPanel*的子元素：</span><span class="sxs-lookup"><span data-stu-id="ba6e9-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="ba6e9-154">请参阅</span><span class="sxs-lookup"><span data-stu-id="ba6e9-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="ba6e9-155">WPF 中的形状和基本图形概述</span><span class="sxs-lookup"><span data-stu-id="ba6e9-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="ba6e9-156">使用图像、图形和视觉对象进行绘制</span><span class="sxs-lookup"><span data-stu-id="ba6e9-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="ba6e9-157">Drawing 对象概述</span><span class="sxs-lookup"><span data-stu-id="ba6e9-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="ba6e9-158">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="ba6e9-158">How-to Topics</span></span>](adorners-how-to-topics.md)
