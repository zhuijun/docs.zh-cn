---
title: Popup 放置行为
description: 了解如何使用属性指定 Windows Presentation Foundation Popup 相对于控件、鼠标或屏幕的位置。
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 8184805518bc56693ead4c7d1f0e9a1bff9bff8f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167741"
---
# <a name="popup-placement-behavior"></a>Popup 放置行为
<xref:System.Windows.Controls.Primitives.Popup> 控件在一个浮动在应用程序上的单独窗口中显示内容。 可通过使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性来指定 <xref:System.Windows.Controls.Primitives.Popup> 相对于控件、鼠标或屏幕的位置。  这些属性协同工作，使你可以灵活地指定 <xref:System.Windows.Controls.Primitives.Popup> 的位置。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip> 和 <xref:System.Windows.Controls.ContextMenu> 类还定义了这五个属性，并且两者的行为相似。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>定位 Popup  
 可将 <xref:System.Windows.Controls.Primitives.Popup> 相对于 <xref:System.Windows.UIElement> 或整个屏幕进行放置。  以下示例创建了四个相对于 <xref:System.Windows.UIElement>（在本例中，它是一个图像）的 <xref:System.Windows.Controls.Primitives.Popup> 控件。 所有这些 <xref:System.Windows.Controls.Primitives.Popup> 控件都将 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 属性设置为 `image1`，但每个 <xref:System.Windows.Controls.Primitives.Popup> 具有不同的 Placement 属性值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下图显示了该图像和这些 <xref:System.Windows.Controls.Primitives.Popup> 控件  
  
 ![带有四个 Popup 控件的图像](./media/popup-placement-behavior/popup-placement-intro.png "带有四个 Popup 的图像")
  
 这一简单的示例演示了如何设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性，但你可通过使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性，更好地控制 <xref:System.Windows.Controls.Primitives.Popup> 的位置。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>术语的定义：Popup 剖析  
 对于理解 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.Placement%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>、<xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性彼此关联的方式以及它们与 <xref:System.Windows.Controls.Primitives.Popup> 关联的方式，以下术语非常实用：  
  
- 目标对象  
  
- 目标区域  
  
- 目标原点  
  
- Popup 对齐点  
  
 这些术语为引用 <xref:System.Windows.Controls.Primitives.Popup> 的各个方面及其关联的控件提供了一种便捷的方法。  
  
### <a name="target-object"></a>目标对象  
 目标对象是与 <xref:System.Windows.Controls.Primitives.Popup> 关联的元素。 如果已设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 属性，则它指定目标对象。  如果未设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 并且 <xref:System.Windows.Controls.Primitives.Popup> 具有父级，则父级就是目标对象。  如果没有 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 值并且没有父级，则没有目标对象并且 <xref:System.Windows.Controls.Primitives.Popup> 相对于屏幕进行定位。  
  
 以下示例创建了一个作为 <xref:System.Windows.Controls.Canvas> 的子级的 <xref:System.Windows.Controls.Primitives.Popup>。  该示例未对 <xref:System.Windows.Controls.Primitives.Popup> 设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 属性。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的默认值为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>，因此 <xref:System.Windows.Controls.Primitives.Popup> 在 <xref:System.Windows.Controls.Canvas> 下方显示。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下图显示了 <xref:System.Windows.Controls.Primitives.Popup> 相对于 <xref:System.Windows.Controls.Canvas> 进行定位。  
  
 ![没有 PlacementTarget 的 Popup 控件](./media/popup-placement-behavior/popup-placement-no-placement-target.png "没有 PlacementTarget 的 Popup。")  

 以下示例创建了一个作为 <xref:System.Windows.Controls.Canvas> 的子级的 <xref:System.Windows.Controls.Primitives.Popup>，但这一次将 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 设置为 `ellipse1`，因此 Popup 在 <xref:System.Windows.Shapes.Ellipse> 下方显示。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下图显示了 <xref:System.Windows.Controls.Primitives.Popup> 相对于 <xref:System.Windows.Shapes.Ellipse> 进行定位。  
  
 ![相对于椭圆形定位的 Popup](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的 Popup")
  
> [!NOTE]
> 对于 <xref:System.Windows.Controls.ToolTip>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的默认值是 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>。  对于 <xref:System.Windows.Controls.ContextMenu>，<xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的默认值是 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>。 这些值将在后面的“属性如何协同工作”部分中进行说明。  
  
### <a name="target-area"></a>目标区域  
 目标区域是屏幕上与 <xref:System.Windows.Controls.Primitives.Popup> 相对的区域。 在前面的示例中，<xref:System.Windows.Controls.Primitives.Popup> 与目标对象的边界对齐，但在某些情况下，即使 <xref:System.Windows.Controls.Primitives.Popup> 具有目标对象，<xref:System.Windows.Controls.Primitives.Popup> 也将与其他边界对齐。  如果已设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 属性，则目标区域与目标对象的边界不同。  
  
 以下示例创建了两个 <xref:System.Windows.Controls.Canvas> 对象，每个对象包含一个 <xref:System.Windows.Shapes.Rectangle> 和一个 <xref:System.Windows.Controls.Primitives.Popup>。  在这两种情况下，<xref:System.Windows.Controls.Primitives.Popup> 的目标对象都是 <xref:System.Windows.Controls.Canvas>。 第一个 <xref:System.Windows.Controls.Canvas> 中的 <xref:System.Windows.Controls.Primitives.Popup> 设置了 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>，其 <xref:System.Windows.Rect.X%2A>、<xref:System.Windows.Rect.Y%2A>、<xref:System.Windows.Rect.Width%2A> 和 <xref:System.Windows.Rect.Height%2A> 属性分别设置为 50、50、50 和 100。 第二个 <xref:System.Windows.Controls.Canvas> 中的 <xref:System.Windows.Controls.Primitives.Popup> 未设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  因此，第一个 <xref:System.Windows.Controls.Primitives.Popup> 位于 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 下方，而第二个 <xref:System.Windows.Controls.Primitives.Popup> 位于 <xref:System.Windows.Controls.Canvas> 下方。 每个 <xref:System.Windows.Controls.Canvas> 还包含一个 <xref:System.Windows.Shapes.Rectangle>，它与第一个 <xref:System.Windows.Controls.Primitives.Popup> 的 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 具有相同的边界。  请注意，<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 不会在应用程序中创建可见元素；该示例创建了一个表示 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 的 <xref:System.Windows.Shapes.Rectangle>。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下图显示前面示例的结果。  
  
 ![具有和没有 PlacementRectangle 的 Popup](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "具有和没有 PlacementRectangle 的 Popup。")  

### <a name="target-origin-and-popup-alignment-point"></a>目标原点和目标对齐点  
 *目标原点*和 *Popup 对齐点*分别是目标区域和 Popup 上用于定位定位的参照点。 可使用 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性使 Popup 从目标区域偏移。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 相对于目标原点和 Popup 对齐点。 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性的值确定目标原点和 Popup 对齐点的位置。  
  
 以下示例创建了一个 <xref:System.Windows.Controls.Primitives.Popup>，并将 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性设置为 20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>（默认值），因此目标原点是目标区域的左下角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下图显示前面示例的结果。  
  
 ![使用目标原点对齐点的 Popup 放置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "具有 HorizontalOffset 和 VerticalOffset 的 Popup。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>属性如何协同工作  
 需要将 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值一起考虑，才可确定正确的目标区域、目标原点和 Popup 对齐点。  例如，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 的值是 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>，则目标对象不存在、<xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将被忽略并且目标区域是鼠标指针的边界。 另一方面，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>，则 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级决定目标对象，而 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 决定目标区域。  
  
 下表介绍了目标对象、目标区域、目标原点和 Popup 对齐点，并指示是否对每个 <xref:System.Windows.Controls.Primitives.PlacementMode> 枚举值使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>。  
  
|PlacementMode|目标对象|目标区域|目标原点|Popup 对齐点|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|屏幕或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于屏幕。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|屏幕或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于屏幕。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的左下角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的中心。|<xref:System.Windows.Controls.Primitives.Popup> 的中心。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 定义。|由 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 定义。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|鼠标指针的边界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将被忽略。|目标区域的左下角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|鼠标指针的边界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将被忽略。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的右上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级。|目标对象或 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>（如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 相对于目标对象。|目标区域的左上角。|<xref:System.Windows.Controls.Primitives.Popup> 的左下角。|  
  
 下图显示了每个 <xref:System.Windows.Controls.Primitives.PlacementMode> 值的 <xref:System.Windows.Controls.Primitives.Popup>、目标区域、目标原点和 Popup 对齐点。 在每个图中，目标区域为黄色，而 <xref:System.Windows.Controls.Primitives.Popup> 为蓝色。  
  
 ![采用 Absolute 或 AbsolutePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-absolute.png "Placement 为 Absolute 或 AbsolutePoint。")
  
 ![采用 Bottom 定位的 Popup](./media/popup-placement-behavior/popup-placement-bottom.png "Placement 为 Bottom。")
  
 ![采用 Center 定位的 Popup](./media/popup-placement-behavior/popup-placement-center.png "Placement 为 Center。")
  
 ![采用 Left 定位的 Popup](./media/popup-placement-behavior/popup-placement-left.png "Placement 为 Left。")
  
 ![采用 Mouse 定位的 Popup](./media/popup-placement-behavior/popup-placement-mouse.png "Placement 为 Mouse。")  
  
 ![采用 MousePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-mousepoint.png "Placement 为 MousePoint。")  
  
 ![采用 Relative 或 RelativePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-relative.png "Placement 为 Relative 或 RelativePoint。")
  
 ![采用 Right 定位的 Popup](./media/popup-placement-behavior/popup-placement-right.png "Placement 为 Right。")
  
 ![采用 Top 定位的 Popup](./media/popup-placement-behavior/popup-placement-top.png "Placement 为 Top。")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>当 Popup 到达屏幕边缘时  
 出于安全原因，屏幕边缘不能隐藏 <xref:System.Windows.Controls.Primitives.Popup>。 当 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕边缘时，将出现以下三种情况之一：  
  
- Popup 沿着将遮挡 <xref:System.Windows.Controls.Primitives.Popup> 的屏幕边缘重新自行对齐。  
  
- Popup 使用其他 Popup 对齐点。  
  
- Popup 使用其他目标原点和 Popup 对齐点。  
  
 将在本部分后面进一步介绍这些选项。  
  
 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕边缘时的行为取决于 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性值以及它所到达的具体屏幕边缘。 下表汇总了针对每个 <xref:System.Windows.Controls.Primitives.PlacementMode> 值，<xref:System.Windows.Controls.Primitives.Popup> 到达屏幕边缘时的行为。  
  
|PlacementMode|上边缘|下边缘|左边缘|右边缘|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|与上边缘对齐。|Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|与左边缘对齐。|Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|与上边缘对齐。|目标原点更改为目标区域的左上角，而 Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|与上边缘对齐。|与下边缘对齐。|目标原点更改为目标区域的右上角，而 Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|与上边缘对齐。|目标原点更改为目标区域（鼠标指针的边界）的左上角，而 Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|与上边缘对齐。|Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|与左边缘对齐。|Popup 对齐点更改为 Popup 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|与上边缘对齐。|Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。|与左边缘对齐。|Popup 对齐点更改为 Popup 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|目标原点更改为目标区域的左上角，而 Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目标原点更改为目标区域的左下角，而 Popup 对齐点更改为 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。 实际上，这与 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 是 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 时相同。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
  
### <a name="aligning-to-the-screen-edge"></a>对屏幕边缘对齐  
 <xref:System.Windows.Controls.Primitives.Popup> 可通过重新自行定位以与屏幕边缘对齐，使整个 <xref:System.Windows.Controls.Primitives.Popup> 在屏幕上可见。  出现这种情况时，目标原点和 Popup 对齐点之间的距离可能与 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 的值不同。 当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>、<xref:System.Windows.Controls.Primitives.PlacementMode.Center> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 时，<xref:System.Windows.Controls.Primitives.Popup> 将自身与每个屏幕边缘对齐。  例如，假定 <xref:System.Windows.Controls.Primitives.Popup> 将 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 并将 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 设置为 100。  如果屏幕下边缘隐藏全部或部分 <xref:System.Windows.Controls.Primitives.Popup>，则 <xref:System.Windows.Controls.Primitives.Popup> 沿屏幕下边缘重新自行定位，并且目标原点和 Popup 对齐点之间的垂直距离小于 100。 下图演示了此情况。  
  
 ![与屏幕边缘对齐的 Popup](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Popup 与屏幕边缘对齐。")
  
### <a name="changing-the-popup-alignment-point"></a>更改 Popup 对齐点  
 如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>、<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>，则当 Popup 到达屏幕下边缘或右边缘时，Popup 对齐点将发生更改。  
  
 下图演示当屏幕下边缘隐藏全部或部分 <xref:System.Windows.Controls.Primitives.Popup> 时，Popup 对齐点为 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![由于底部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup 到达屏幕下边缘，并更改 Popup 对齐点。")  

 下图演示了当屏幕下边缘隐藏 <xref:System.Windows.Controls.Primitives.Popup> 时，Popup 对齐点为 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![由于屏幕边缘而产生的新 Popup 对齐点](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup 到达屏幕右边缘，并更改 Popup 对齐点。")
  
 如果 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕的下边缘和右边缘，则 Popup 对齐点为 <xref:System.Windows.Controls.Primitives.Popup> 的右下角。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>更改目标原点和 Popup 对齐点  
 当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>、<xref:System.Windows.Controls.Primitives.PlacementMode.Left>、<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>、<xref:System.Windows.Controls.Primitives.PlacementMode.Right> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.Top>时，如果 Popup 到达某个屏幕边缘，则目标原点和 Popup 对齐点将发生更改。  导致位置变化的屏幕边缘取决于 <xref:System.Windows.Controls.Primitives.PlacementMode> 值。  
  
 下图演示了当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 并且 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕下边缘时，目标原点是目标区域的左上角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![由于底部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Placement 为 Bottom，并且 Popup 到达屏幕下边缘。")
  
 下图演示了当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> 并且 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕左边缘时，目标原点是目标区域的右上角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 ![由于左侧屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Placement 为 Left，并且 Popup 到达屏幕左边缘。")  
  
 下图演示了当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Right> 并且 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕右边缘时，目标原点是目标区域的左上角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的右上角。  
  
 ![由于右侧屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Placement 为 Right，并且 Popup 到达屏幕右边缘。")  

 下图演示了当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 并且 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕上边缘时，目标原点是目标区域的左下角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的左上角。  
  
 ![由于顶部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement 为 Top，并且 Popup 到达屏幕上边缘。")  
  
 下图演示了当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 是 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 并且 <xref:System.Windows.Controls.Primitives.Popup> 到达屏幕下边缘时，目标原点是目标区域（鼠标指针的边界）的左上角，而 Popup 对齐点是 <xref:System.Windows.Controls.Primitives.Popup> 的左下角。  
  
 ![由于鼠标接近屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Placement 为 Mouse，并且 Popup 到达屏幕下边缘。")
  
### <a name="customizing-popup-placement"></a>自定义 Popup 放置  
 可通过将 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> 来自定义目标原点和 Popup 对齐点。 然后定义一个 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委托，该委托返回 <xref:System.Windows.Controls.Primitives.Popup> 的一组可能的放置点和主轴（按优先顺序排列）。 显示 <xref:System.Windows.Controls.Primitives.Popup> 最大部分的点被选中。  如果屏幕边缘隐藏了 <xref:System.Windows.Controls.Primitives.Popup>，则 <xref:System.Windows.Controls.Primitives.Popup> 的位置会自动调整。 有关示例，请参阅[指定自定义 Popup 位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>请参阅

- [Popup 放置示例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
