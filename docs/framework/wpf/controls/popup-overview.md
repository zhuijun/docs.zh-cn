---
title: Popup 概述
description: 了解 Windows Presentation Foundation Popup 控件，该控件提供一种在当前应用程序上浮动的窗口中显示内容的方式。
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 84eaddc53366df6d1da1a0a005d3618268f8cce2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167542"
---
# <a name="popup-overview"></a>Popup 概述
<xref:System.Windows.Controls.Primitives.Popup>控件提供了一种在相对于指定的元素或屏幕坐标浮动于当前应用程序窗口的单独窗口中显示内容的方式。 本主题介绍 <xref:System.Windows.Controls.Primitives.Popup> 控件并提供有关其用法的信息。  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>什么是 Popup？  
 <xref:System.Windows.Controls.Primitives.Popup>控件在与屏幕上的元素或点相对的单独窗口中显示内容。 当 <xref:System.Windows.Controls.Primitives.Popup> 可见时，属性将 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 设置为 `true` 。  
  
> [!NOTE]
> <xref:System.Windows.Controls.Primitives.Popup>当鼠标指针移到其父对象上时，不会自动打开。 如果希望 <xref:System.Windows.Controls.Primitives.Popup> 自动打开，请使用 <xref:System.Windows.Controls.ToolTip> 或 <xref:System.Windows.Controls.ToolTipService> 类。 有关详细信息，请参阅 [ToolTip 概述](tooltip-overview.md)。  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>创建弹出项。  
 下面的示例演示如何定义控件 <xref:System.Windows.Controls.Primitives.Popup> ，该控件是控件的子元素 <xref:System.Windows.Controls.Button> 。 由于只能 <xref:System.Windows.Controls.Button> 有一个子元素，因此，此示例将的 <xref:System.Windows.Controls.Button> 和控件的文本放 <xref:System.Windows.Controls.Primitives.Popup> 在中 <xref:System.Windows.Controls.StackPanel> 。 的内容将显示 <xref:System.Windows.Controls.Primitives.Popup> 在控件中 <xref:System.Windows.Controls.TextBlock> ，该控件将其文本显示在一个单独的窗口中，该窗口浮动在相关控件附近的应用程序窗口 <xref:System.Windows.Controls.Button> 。  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>实现 Popup 的控件  
 可以将 <xref:System.Windows.Controls.Primitives.Popup> 控件生成到其他控件中。 以下控件 <xref:System.Windows.Controls.Primitives.Popup> 为特定用途实现控件：  
  
- <xref:System.Windows.Controls.ToolTip>. 如果要为元素创建工具提示，请使用 <xref:System.Windows.Controls.ToolTip> 和 <xref:System.Windows.Controls.ToolTipService> 类。 有关详细信息，请参阅 [ToolTip 概述](tooltip-overview.md)。  
  
- <xref:System.Windows.Controls.ContextMenu>. 如果要为元素创建上下文菜单，请使用 <xref:System.Windows.Controls.ContextMenu> 控件。 有关详细信息，请参阅 [ContextMenu 概述](contextmenu-overview.md)。  
  
- <xref:System.Windows.Controls.ComboBox>. 如果要创建具有可显示或隐藏的下拉列表框的选择控件，请使用 <xref:System.Windows.Controls.ComboBox> 控件。  
  
- <xref:System.Windows.Controls.Expander>. 若要创建一个控件，该控件显示具有可折叠区域（显示内容）的标题，请使用 <xref:System.Windows.Controls.Expander> 控件。 有关详细信息，请参阅 [Expander 概述](expander-overview.md)。  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Popup 行为和外观  
 <xref:System.Windows.Controls.Primitives.Popup>控件提供使您能够自定义其行为和外观的功能。 例如，可以设置打开和关闭行为、动画、不透明度和位图效果，以及 <xref:System.Windows.Controls.Primitives.Popup> 大小和位置。  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>打开和关闭行为  
 <xref:System.Windows.Controls.Primitives.Popup>当 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 属性设置为时，控件将显示其内容 `true` 。 默认情况下，一直 <xref:System.Windows.Controls.Primitives.Popup> 保持打开状态，直到 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 属性设置为 `false` 。 但是，您可以通过将 <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> 属性设置为来更改默认行为 `false` 。 如果将此属性设置为 `false` ，则 " <xref:System.Windows.Controls.Primitives.Popup> 内容" 窗口将具有鼠标捕获。 <xref:System.Windows.Controls.Primitives.Popup>当鼠标事件在窗口外发生时，将丢失鼠标捕获并关闭窗口 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> 当 <xref:System.Windows.Controls.Primitives.Popup> 内容窗口处于打开或关闭状态时，将引发和事件。  
  
<a name="Animation"></a>
### <a name="animation"></a>动画  
 <xref:System.Windows.Controls.Primitives.Popup>控件具有对动画的内置支持，通常与淡入和滑入等行为关联。 可以通过将 <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> 属性设置为枚举值来打开这些动画 <xref:System.Windows.Controls.Primitives.PopupAnimation> 。 <xref:System.Windows.Controls.Primitives.Popup>若要使动画正常工作，必须将 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 属性设置为 `true` 。  
  
 还可以应用类似于 <xref:System.Windows.Media.Animation.Storyboard> 控件的动画 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>不透明度和位图效果  
 <xref:System.Windows.UIElement.Opacity%2A>控件的属性 <xref:System.Windows.Controls.Primitives.Popup> 在其内容上不起作用。 默认情况下， <xref:System.Windows.Controls.Primitives.Popup> 内容窗口不透明。 若要创建透明 <xref:System.Windows.Controls.Primitives.Popup> ，请将 <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> 属性设置为 `true` 。  
  
 的内容 <xref:System.Windows.Controls.Primitives.Popup> 不会继承位图效果，如 <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> 您在 <xref:System.Windows.Controls.Primitives.Popup> 控件上或在父窗口中的任何其他元素上直接设置的位图效果。 若要在的内容中显示位图效果 <xref:System.Windows.Controls.Primitives.Popup> ，必须直接在其内容上设置位图效果。 例如，如果的子级 <xref:System.Windows.Controls.Primitives.Popup> 是 <xref:System.Windows.Controls.StackPanel> ，则设置上的位图效果 <xref:System.Windows.Controls.StackPanel> 。  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Popup 大小  
 默认情况下，会 <xref:System.Windows.Controls.Primitives.Popup> 自动调整其内容的大小。 自动调整大小时，某些位图效果可能会隐藏，因为为内容定义的屏幕区域的默认大小 <xref:System.Windows.Controls.Primitives.Popup> 不能为位图效果提供足够的空间。  
  
 <xref:System.Windows.Controls.Primitives.Popup>在内容上设置时，内容也可能会被遮住 <xref:System.Windows.UIElement.RenderTransform%2A> 。 在这种情况下，如果转换的内容超出了原始区域，某些内容可能会被隐藏 <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.Primitives.Popup> 。 如果位图效果或变换需要更多空间，则可以定义内容周围的边距，以便为 <xref:System.Windows.Controls.Primitives.Popup> 控件提供更多的区域。  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>定义 Popup 位置  
 可以通过设置 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 、 <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> 、、 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> 和 <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> 属性来定位 popup。 有关详细信息，请参阅 [Popup 放置行为](popup-placement-behavior.md)。 当 <xref:System.Windows.Controls.Primitives.Popup> 屏幕上显示时，如果重新定位其父项，则不会重新定位。  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>自定义 Popup 放置  
 您可以 <xref:System.Windows.Controls.Primitives.Popup> 通过指定一组相对于 <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> 您希望显示的位置的坐标来自定义控件的位置 <xref:System.Windows.Controls.Primitives.Popup> 。  
  
 若要自定义位置，请将 <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> 属性设置为 <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> 。 然后，定义一个 <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> 委托，该委托返回一组可能的位置点和主轴（按优先顺序排列） <xref:System.Windows.Controls.Primitives.Popup> 。 将自动选择显示最大部分的点 <xref:System.Windows.Controls.Primitives.Popup> 。 有关示例，请参阅[指定自定义 Popup 位置](how-to-specify-a-custom-popup-position.md)。  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Popup 和可视化树  
 <xref:System.Windows.Controls.Primitives.Popup>控件没有自己的可视化树; 当调用的方法时，该控件返回的大小为0（零） <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> <xref:System.Windows.Controls.Primitives.Popup> 。 但是，在将的 <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> 属性设置为时，将 <xref:System.Windows.Controls.Primitives.Popup> `true` 创建一个具有其自己的可视化树的新窗口。 新窗口包含 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 的内容 <xref:System.Windows.Controls.Primitives.Popup> 。 新窗口的宽度和高度不能超过屏幕宽度或高度的 75%。  
  
 控件将对 <xref:System.Windows.Controls.Primitives.Popup> 其内容的引用 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 作为逻辑子级维护。 当创建新窗口时，的内容 <xref:System.Windows.Controls.Primitives.Popup> 将成为窗口的可视子级，并且保持的逻辑子级 <xref:System.Windows.Controls.Primitives.Popup> 。 相反， <xref:System.Windows.Controls.Primitives.Popup> 将保留其内容的逻辑父级 <xref:System.Windows.Controls.Primitives.Popup.Child%2A> 。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [操作指南主题](popup-how-to-topics.md)
- [操作指南主题](tooltip-how-to-topics.md)
