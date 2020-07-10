---
title: Popup 放置行为
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243253"
---
# <a name="popup-placement-behavior"></a>Popup 放置行为
<xref:System.Windows.Controls.Primitives.Popup>控件在单独的窗口中显示内容，该窗口浮动在应用程序上。 <xref:System.Windows.Controls.Primitives.Popup>通过使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 、、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性，可以指定相对于控件、鼠标或屏幕的位置。  这些属性一起使用，使你可以灵活地指定的位置 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
> [!NOTE]
> <xref:System.Windows.Controls.ToolTip>和 <xref:System.Windows.Controls.ContextMenu> 类还定义这五个属性，行为类似。  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>定位 Popup  
 的位置 <xref:System.Windows.Controls.Primitives.Popup> 可以相对于 <xref:System.Windows.UIElement> 或整个屏幕。  下面的示例创建了四个 <xref:System.Windows.Controls.Primitives.Popup> 相对于的控件 <xref:System.Windows.UIElement> （在本例中为图像）。 所有控件的 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 属性都设置为 `image1` ，但 <xref:System.Windows.Controls.Primitives.Popup> 对于 "位置" 属性，每个控件都有不同的值。  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 下图显示了图像和 <xref:System.Windows.Controls.Primitives.Popup> 控件  
  
 ![带有四个 Popup 控件的图像](./media/popup-placement-behavior/popup-placement-intro.png "带有四个弹出窗口的图像")
  
 这个简单的示例演示如何设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性，但通过使用 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性，您可以更好地控制所定位的位置 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>术语定义：Popup 解析  
 以下术语有助于了解 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和属性彼此之间的关系， <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 以及如何相互关联 <xref:System.Windows.Controls.Primitives.Popup> ：  
  
- “目标对象”  
  
- 目标区域  
  
- 目标原点  
  
- Popup 对齐点  
  
 这些术语提供了一种便捷的方法来引用的各个方面 <xref:System.Windows.Controls.Primitives.Popup> 以及它所关联的控件。  
  
### <a name="target-object"></a>目标对象  
 *目标对象*是 <xref:System.Windows.Controls.Primitives.Popup> 与关联的元素。 如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 设置了属性，它将指定目标对象。  如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 未设置，并且 <xref:System.Windows.Controls.Primitives.Popup> 具有父，则父对象是目标对象。  如果没有任何 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 值，并且没有父对象，则没有目标对象，并且 <xref:System.Windows.Controls.Primitives.Popup> 相对于屏幕进行定位。  
  
 下面的示例创建一个 <xref:System.Windows.Controls.Primitives.Popup> ，它是的子级 <xref:System.Windows.Controls.Canvas> 。  该示例不在上设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 属性 <xref:System.Windows.Controls.Primitives.Popup> 。 的默认值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType> ，因此显示在 <xref:System.Windows.Controls.Primitives.Popup> 下方 <xref:System.Windows.Controls.Canvas> 。  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 下图显示了相对于 <xref:System.Windows.Controls.Primitives.Popup> 的定位 <xref:System.Windows.Controls.Canvas> 。  
  
 ![没有 PlacementTarget 的 Popup 控件](./media/popup-placement-behavior/popup-placement-no-placement-target.png "无 System.windows.controls.primitives.popup.placementtarget 的弹出窗口。")  

 下面的示例创建一个， <xref:System.Windows.Controls.Primitives.Popup> 它是的子 <xref:System.Windows.Controls.Canvas> ，但这一次将 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 设置为 `ellipse1` ，因此，popup 显示在下方 <xref:System.Windows.Shapes.Ellipse> 。  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 下图显示了相对于 <xref:System.Windows.Controls.Primitives.Popup> 的定位 <xref:System.Windows.Shapes.Ellipse> 。  
  
 ![相对于椭圆形定位的 Popup](./media/popup-placement-behavior/popup-placement-with-placement-target.png "具有 PlacementTarget 的 Popup")
  
> [!NOTE]
> 对于 <xref:System.Windows.Controls.ToolTip> ，的默认值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 。  对于 <xref:System.Windows.Controls.ContextMenu> ，的默认值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> 。 这些值将在后面的“属性如何协同工作”部分中进行说明。  
  
### <a name="target-area"></a>目标区域  
 *目标区域*是屏幕上相关的区域 <xref:System.Windows.Controls.Primitives.Popup> 。 在前面的示例中，与 <xref:System.Windows.Controls.Primitives.Popup> 目标对象的边界对齐，但在某些情况下， <xref:System.Windows.Controls.Primitives.Popup> 即使 <xref:System.Windows.Controls.Primitives.Popup> 有目标对象，也与其他边界对齐。  如果 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 设置了属性，则目标区域不同于目标对象的边界。  
  
 下面的示例创建两个 <xref:System.Windows.Controls.Canvas> 对象，每个对象都包含一个 <xref:System.Windows.Shapes.Rectangle> 和一个 <xref:System.Windows.Controls.Primitives.Popup> 。  在这两种情况下，的目标对象 <xref:System.Windows.Controls.Primitives.Popup> 是 <xref:System.Windows.Controls.Canvas> 。 <xref:System.Windows.Controls.Primitives.Popup>第一项 <xref:System.Windows.Controls.Canvas> 具有 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 集，其 <xref:System.Windows.Rect.X%2A> 、 <xref:System.Windows.Rect.Y%2A> 、 <xref:System.Windows.Rect.Width%2A> 和 <xref:System.Windows.Rect.Height%2A> 属性分别设置为50、50、50和100。 <xref:System.Windows.Controls.Primitives.Popup>在第二个中，没有 <xref:System.Windows.Controls.Canvas> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 设置。  因此，第一个位于 <xref:System.Windows.Controls.Primitives.Popup> 下， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 第二个位于下 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Canvas> 。 每个 <xref:System.Windows.Controls.Canvas> 还包含与 <xref:System.Windows.Shapes.Rectangle> 第一个具有相同边界的 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup> 。  请注意，不 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 会在应用程序中创建可见的元素; 此示例将创建一个 <xref:System.Windows.Shapes.Rectangle> 来表示 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 。  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 下图显示前面示例的结果。  
  
 ![具有和没有 PlacementRectangle 的 Popup](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "具有和没有 System.windows.controls.primitives.popup.placementrectangle 的 Popup。")  

### <a name="target-origin-and-popup-alignment-point"></a>目标原点和目标对齐点  
 *目标原点*和 *Popup 对齐点*分别是目标区域和 Popup 上用于定位定位的参照点。 您可以使用 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性来从目标区域偏移弹出窗口。  <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 相对于目标原点和 popup 对齐点。 属性的值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 确定目标原点和 popup 对齐点的位置。  
  
 下面的示例创建一个 <xref:System.Windows.Controls.Primitives.Popup> ，并将 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 属性设置为20。  <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>将属性设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (默认) ，因此目标原点是目标区域的左下角，popup 对齐点是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 下图显示前面示例的结果。  
  
 ![使用目标原点对齐点的 Popup 放置](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "带 System.windows.controls.primitives.popup.horizontaloffset 和 System.windows.controls.primitives.popup.verticaloffset 的弹出窗口。")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>属性如何协同工作  
 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>、和的值 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 都需要组合在一起，以确定正确的目标区域、目标原点和 popup 对齐点。  例如，如果的值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为，则没有 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 目标对象，将 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 忽略，并且目标区域是鼠标指针的边界。 另一方面，如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> ，则 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 或父级确定目标对象并 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 确定目标区域。  
  
 下表介绍目标对象、目标区域、目标原点和 popup 对齐点，并指示是否 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将和用于每个 <xref:System.Windows.Controls.Primitives.PlacementMode> 枚举值。  
  
|PlacementMode|“目标对象”|目标区域|目标原点|Popup 对齐点|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|屏幕或（ <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相对于屏幕。|目标区域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|屏幕或（ <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置）。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>相对于屏幕。|目标区域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的左下角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的中心。|的中心 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|由定义 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 。|由定义 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的左上角。|的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|鼠标指针的边界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将被忽略。|目标区域的左下角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|不适用。 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 将被忽略。|鼠标指针的边界。 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 将被忽略。|目标区域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的左上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的右上角。|的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>或父。|目标对象， <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 如果已设置，则为。  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>是相对于目标对象的。|目标区域的左上角。|的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
  
 下图显示 <xref:System.Windows.Controls.Primitives.Popup> 每个值的、目标区域、目标原点和 popup 对齐点 <xref:System.Windows.Controls.Primitives.PlacementMode> 。 在每个图中，目标区域为黄色， <xref:System.Windows.Controls.Primitives.Popup> 为蓝色。  
  
 ![采用 Absolute 或 AbsolutePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-absolute.png "放置是绝对的或 Absolutepoint 定位的。")
  
 ![采用 Bottom 定位的 Popup](./media/popup-placement-behavior/popup-placement-bottom.png "放置为底端。")
  
 ![采用 Center 定位的 Popup](./media/popup-placement-behavior/popup-placement-center.png "放置是中心。")
  
 ![采用 Left 定位的 Popup](./media/popup-placement-behavior/popup-placement-left.png "位置为左。")
  
 ![采用 Mouse 定位的 Popup](./media/popup-placement-behavior/popup-placement-mouse.png "位置为鼠标。")  
  
 ![采用 MousePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-mousepoint.png "放置是 Mousepoint 定位的。")  
  
 ![采用 Relative 或 RelativePoint 定位的 Popup](./media/popup-placement-behavior/popup-placement-relative.png "位置是相对的或 Relativepoint 定位的。")
  
 ![采用 Right 定位的 Popup](./media/popup-placement-behavior/popup-placement-right.png "放置是正确的。")
  
 ![采用 Top 定位的 Popup](./media/popup-placement-behavior/popup-placement-top.png "位置为 Top。")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>当 Popup 到达屏幕边缘时  
 出于安全原因， <xref:System.Windows.Controls.Primitives.Popup> 无法通过屏幕边缘隐藏。 当遇到屏幕边缘时，会出现以下三种情况之一 <xref:System.Windows.Controls.Primitives.Popup> ：  
  
- 弹出式窗口边缘的 popup，将会掩盖 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
- Popup 使用其他 Popup 对齐点。  
  
- Popup 使用其他目标原点和 Popup 对齐点。  
  
 将在本部分后面进一步介绍这些选项。  
  
 <xref:System.Windows.Controls.Primitives.Popup>当遇到屏幕边缘时的行为取决于属性的值 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 以及 popup 遇到的屏幕边缘。 下表总结了在 <xref:System.Windows.Controls.Primitives.Popup> 遇到每个值的屏幕边缘时的行为 <xref:System.Windows.Controls.Primitives.PlacementMode> 。  
  
|PlacementMode|上边缘|下边缘|左边缘|右边缘|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|与上边缘对齐。|Popup 对齐点更改为的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|与左边缘对齐。|Popup 对齐点更改为的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|与上边缘对齐。|目标原点更改为目标区域的左上角，而 popup 对齐点更改为的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|与上边缘对齐。|与下边缘对齐。|目标原点更改为目标区域的右上角，popup 对齐点更改为的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|与上边缘对齐。|目标原点更改为目标区域的左上角， (鼠标指针的边界) 并且 popup 对齐点更改为的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|与上边缘对齐。|Popup 对齐点更改为的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|与左边缘对齐。|Popup 对齐点更改为 Popup 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|与上边缘对齐。|Popup 对齐点更改为的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。|与左边缘对齐。|Popup 对齐点更改为 Popup 的右上角。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|与上边缘对齐。|与下边缘对齐。|与左边缘对齐。|目标原点更改为目标区域的左上角，而 popup 对齐点更改为的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|目标原点更改为目标区域的左下角，popup 对齐点更改为的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。 实际上，这与在时相同 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 。|与下边缘对齐。|与左边缘对齐。|与右边缘对齐。|  
  
### <a name="aligning-to-the-screen-edge"></a>对屏幕边缘对齐  
 <xref:System.Windows.Controls.Primitives.Popup>可以通过重新定位自身来使屏幕边缘对齐，使整个在 <xref:System.Windows.Controls.Primitives.Popup> 屏幕上可见。  出现这种情况时，目标原点和 popup 对齐点之间的距离可能与和的值 <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 不同 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 。 当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.Center> 或时 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> ，将 <xref:System.Windows.Controls.Primitives.Popup> 自身与每个屏幕边缘对齐。  例如，假定将 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> 并 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 将设置为100。  如果屏幕的下边缘隐藏全部或部分 <xref:System.Windows.Controls.Primitives.Popup> ，则会在屏幕的 <xref:System.Windows.Controls.Primitives.Popup> 下边缘重新定位自身，目标原点和 popup 对齐点之间的垂直距离小于100。 下图演示了此情况。  
  
 ![与屏幕边缘对齐的 Popup](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "弹出项与屏幕边缘对齐。")
  
### <a name="changing-the-popup-alignment-point"></a>更改 Popup 对齐点  
 如果 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint> 、 <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint> 或 <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint> ，则当 popup 遇到下边缘或右边缘时，popup 对齐点将发生更改。  
  
 下图演示当下屏幕边缘隐藏全部或部分时 <xref:System.Windows.Controls.Primitives.Popup> ，popup 对齐点是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于底部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup 到达屏幕下边缘，并更改 popup 对齐点。")  

 下图演示当 <xref:System.Windows.Controls.Primitives.Popup> 右屏幕边缘隐藏时，popup 对齐点是的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于屏幕边缘而产生的新 Popup 对齐点](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup 遇到屏幕的右边缘，并更改 popup 对齐点。")
  
 如果 <xref:System.Windows.Controls.Primitives.Popup> 遇到屏幕的下边缘和右边缘，则 popup 对齐点为的右下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>更改目标原点和 Popup 对齐点  
 当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 、、、或时 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> ，如果遇到某个屏幕边缘，则目标原点和 popup 对齐点将发生变化。  导致位置变化的屏幕边缘取决于 <xref:System.Windows.Controls.Primitives.PlacementMode> 值。  
  
 下图演示当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> 并且 <xref:System.Windows.Controls.Primitives.Popup> 遇到底部屏幕边缘时，目标原点是目标区域的左上角，而 popup 对齐点是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于底部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "放置是底部，并且 popup 到达屏幕的下边缘。")
  
 下图演示 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 了当为 <xref:System.Windows.Controls.Primitives.PlacementMode.Left> 并且 <xref:System.Windows.Controls.Primitives.Popup> 遇到屏幕左边缘时，目标原点是目标区域的右上角，popup 对齐点是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于左侧屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "放在左侧，并且 popup 到达屏幕的左边缘。")  
  
 下图演示当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Right> 并且 <xref:System.Windows.Controls.Primitives.Popup> 遇到屏幕右边缘时，目标原点是目标区域的左上角，而 popup 对齐点是的右上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于右侧屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "放置是正确的，并且 popup 到达屏幕右边缘。")  

 下图演示 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 了当为 <xref:System.Windows.Controls.Primitives.PlacementMode.Top> 并且 <xref:System.Windows.Controls.Primitives.Popup> 遇到顶部屏幕边缘时，目标原点是目标区域的左下角，popup 对齐点是的左上角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于顶部屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "放置为顶部，并且 popup 到达屏幕的上边缘。")  
  
 下图演示当 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 为 <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> 并且 <xref:System.Windows.Controls.Primitives.Popup> 遇到了下边缘屏幕边缘时，目标原点是目标区域的左上角 (鼠标指针的边界) ，popup 对齐点是的左下角 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 ![由于鼠标接近屏幕边缘而产生的新对齐点](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "放置是鼠标，并且 popup 到达屏幕的下边缘。")
  
### <a name="customizing-popup-placement"></a>自定义 Popup 放置  
 您可以通过将属性设置为来自定义目标原点和 popup 对齐点 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> 。 然后定义一个 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委托，该委托返回一组可能的位置点，并按) 的首选项 (<xref:System.Windows.Controls.Primitives.Popup> 。 将选择显示的最大部分的点 <xref:System.Windows.Controls.Primitives.Popup> 。  <xref:System.Windows.Controls.Primitives.Popup>如果屏幕边缘隐藏，将自动调整的位置 <xref:System.Windows.Controls.Primitives.Popup> 。 有关示例，请参阅[指定自定义 Popup 位置](how-to-specify-a-custom-popup-position.md)。  
  
## <a name="see-also"></a>另请参阅

- [Popup 放置示例](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS)
