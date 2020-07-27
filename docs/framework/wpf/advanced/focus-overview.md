---
title: 焦点概述
description: 了解 Windows Presentation Foundation 中与焦点相关的两个主要概念：键盘焦点和逻辑焦点。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], focus
- focus in applications [WPF]
ms.assetid: 0230c4eb-0c8a-462b-ac4b-ae3e511659f4
ms.openlocfilehash: 71aeb577cccd2c3b16df1c5a3cb772dd1f5479e2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165109"
---
# <a name="focus-overview"></a>焦点概述
在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，有两个与焦点有关的主要概念：键盘焦点和逻辑焦点。  键盘焦点指接收键盘输入的元素，而逻辑焦点指焦点范围中具有焦点的元素。  本概述详细介绍了这些概念。  对于创建具有多个可获取焦点的区域的复杂应用程序来说，理解这些概念之间的区别非常重要。  
  
 参与焦点管理的主要类包括 <xref:System.Windows.Input.Keyboard> 类、 <xref:System.Windows.Input.FocusManager> 类和基元素类，如 <xref:System.Windows.UIElement> 和 <xref:System.Windows.ContentElement> 。  有关基元素的详细信息，请参阅[基元素概述](base-elements-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard>类主要与键盘焦点相关，并 <xref:System.Windows.Input.FocusManager> 主要与逻辑焦点相关，但这并不是绝对差别。  具有键盘焦点的元素也具有逻辑焦点，但具有逻辑焦点的元素不一定具有键盘焦点。  当你使用 <xref:System.Windows.Input.Keyboard> 类设置具有键盘焦点的元素时，这会很明显，还可以在元素上设置逻辑焦点。  

<a name="Keyboard_Focus"></a>
## <a name="keyboard-focus"></a>键盘焦点  
 键盘焦点指当前正在接收键盘输入的元素。  在整个桌面上，只能有一个具有键盘焦点的元素。  在中 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ，具有键盘焦点的元素将 <xref:System.Windows.IInputElement.IsKeyboardFocused%2A> 设置为 `true` 。  <xref:System.Windows.Input.Keyboard.FocusedElement%2A>类上的静态属性 <xref:System.Windows.Input.Keyboard> 获取当前具有键盘焦点的元素。  
  
 为了使元素能够获取键盘焦点， <xref:System.Windows.UIElement.Focusable%2A> <xref:System.Windows.UIElement.IsVisible%2A> 基本元素上的和属性必须设置为 `true` 。  某些类，如 <xref:System.Windows.Controls.Panel> 基类， <xref:System.Windows.UIElement.Focusable%2A> 默认情况下将设置为 `false` ; 因此， <xref:System.Windows.UIElement.Focusable%2A> `true` 如果希望此类元素能够获取键盘焦点，则必须将设置为。  
  
 可通过用户与 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 交互（例如，按 Tab 键导航到某个元素或者在某些元素上单击鼠标）来获取键盘焦点。  还可以通过使用类上的方法以编程方式获取键盘焦点 <xref:System.Windows.Input.Keyboard.Focus%2A> <xref:System.Windows.Input.Keyboard> 。  <xref:System.Windows.Input.Keyboard.Focus%2A>方法尝试给指定元素的键盘焦点。  返回的元素是具有键盘焦点的元素，如果旧的或新的焦点对象阻止请求，则具有键盘焦点的元素可能不是请求的元素。  
  
 下面的示例使用 <xref:System.Windows.Input.Keyboard.Focus%2A> 方法将键盘焦点设置在上 <xref:System.Windows.Controls.Button> 。  
  
 [!code-csharp[focussample#FocusSampleSetFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplesetfocus)]
 [!code-vb[focussample#FocusSampleSetFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplesetfocus)]  
  
 <xref:System.Windows.UIElement.IsKeyboardFocused%2A>基元素类的属性获取一个值，该值指示元素是否具有键盘焦点。  <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A>基元素类的属性获取一个值，该值指示该元素或它的任何一个可视子元素是否具有键盘焦点。  
  
 在应用程序启动时设置初始焦点时，接收焦点的元素必须位于应用程序加载的初始窗口的可视化树中，并且该元素必须具有 <xref:System.Windows.UIElement.Focusable%2A> 并 <xref:System.Windows.UIElement.IsVisible%2A> 将设置为 `true` 。  建议在事件处理程序中设置初始焦点 <xref:System.Windows.FrameworkElement.Loaded> 。  <xref:System.Windows.Threading.Dispatcher>还可以通过调用或来使用回调 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 。  
  
<a name="Logical_Focus"></a>
## <a name="logical-focus"></a>逻辑焦点  
 逻辑焦点引用 <xref:System.Windows.Input.FocusManager.FocusedElement%2A?displayProperty=nameWithType> 焦点范围内的。  焦点作用域是跟踪 <xref:System.Windows.Input.FocusManager.FocusedElement%2A> 其作用域内的的元素。  键盘焦点离开焦点范围时，焦点元素会失去键盘焦点，但保留逻辑焦点。  键盘焦点返回到焦点范围时，焦点元素会再次获得键盘焦点。  这使得键盘焦点可在多个焦点范围之间切换，但确保了焦点返回到焦点范围时，焦点范围中的焦点元素重新获得键盘焦点。  
  
 一个应用程序中可以有多个具有逻辑焦点的元素，但在一个特定的焦点范围中只能有一个具有逻辑焦点的元素。  
  
 具有键盘焦点的元素还具有其所属焦点范围的逻辑焦点。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]通过将 <xref:System.Windows.Input.FocusManager> 附加属性设置 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 为，可以在中将元素转换为焦点范围 `true` 。  在代码中，可以通过调用将元素转换为焦点范围 <xref:System.Windows.Input.FocusManager.SetIsFocusScope%2A> 。  
  
 下面的示例 <xref:System.Windows.Controls.StackPanel> 通过设置附加属性，使成为焦点范围 <xref:System.Windows.Input.FocusManager.IsFocusScope%2A> 。  
  
 [!code-xaml[MarkupSnippets#MarkupIsFocusScopeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupisfocusscopexaml)]  
  
 [!code-csharp[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focussetisfocusscope)]
 [!code-vb[FocusSnippets#FocusSetIsFocusScope](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focussetisfocusscope)]  
  
 <xref:System.Windows.Input.FocusManager.GetFocusScope%2A>返回指定元素的焦点范围。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]默认情况下，焦点范围为、、 <xref:System.Windows.Window> 和的类 <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.ToolBar> <xref:System.Windows.Controls.ContextMenu> 。  
  
 <xref:System.Windows.Input.FocusManager.GetFocusedElement%2A>获取指定焦点范围的聚焦元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>设置指定焦点范围中的焦点元素。  <xref:System.Windows.Input.FocusManager.SetFocusedElement%2A>通常用于设置初始聚焦元素。  
  
 以下示例在焦点范围上设置焦点元素并获取焦点范围的焦点元素。  
  
 [!code-csharp[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSnippets/CSharp/Window1.xaml.cs#focusgetsetfocusedelement)]
 [!code-vb[FocusSnippets#FocusGetSetFocusedElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSnippets/visualbasic/window1.xaml.vb#focusgetsetfocusedelement)]  
  
<a name="Keyboard_Navigation"></a>
## <a name="keyboard-navigation"></a>键盘导航  
 <xref:System.Windows.Input.KeyboardNavigation>类负责在按下一个导航键时实现默认键盘焦点导航。  导航键包括：Tab、Shift+Tab、Ctrl+Tab、Ctrl+Shift+Tab、向上键、向下键、向左键和向右键。  
  
 可以通过设置附加的 <xref:System.Windows.Input.KeyboardNavigation> 属性、和来更改导航容器的导航行为 <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.ControlTabNavigation%2A> <xref:System.Windows.Input.KeyboardNavigation.DirectionalNavigation%2A> 。  这些属性的类型为 <xref:System.Windows.Input.KeyboardNavigationMode> ，可能的值为 <xref:System.Windows.Input.KeyboardNavigationMode.Continue> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Local> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Contained> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> 、 <xref:System.Windows.Input.KeyboardNavigationMode.Once> 和 <xref:System.Windows.Input.KeyboardNavigationMode.None> 。  默认值为 <xref:System.Windows.Input.KeyboardNavigationMode.Continue> ，这意味着该元素不是导航容器。  
  
 下面的示例创建一个 <xref:System.Windows.Controls.Menu> 具有多个 <xref:System.Windows.Controls.MenuItem> 对象的。  在 <xref:System.Windows.Input.KeyboardNavigation.TabNavigation%2A> 上，附加属性设置为 <xref:System.Windows.Input.KeyboardNavigationMode.Cycle> <xref:System.Windows.Controls.Menu> 。  当使用中的 tab 键更改焦点时 <xref:System.Windows.Controls.Menu> ，焦点将从每个元素移动，当到达最后一个元素时，焦点将返回到第一个元素。  
  
 [!code-xaml[MarkupSnippets#MarkupKeyboardNavigationTabNavigationXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml#markupkeyboardnavigationtabnavigationxaml)]  
  
 [!code-csharp[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MarkupSnippets/CSharp/Window1.xaml.cs#markupkeyboardnavigationtabnavigationcode)]
 [!code-vb[MarkupSnippets#MarkupKeyboardNavigationTabNavigationCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MarkupSnippets/visualbasic/window1.xaml.vb#markupkeyboardnavigationtabnavigationcode)]  
  
<a name="Manipulating_Focus_Programmatically"></a>
## <a name="navigating-focus-programmatically"></a>以编程方式导航焦点  
 用于处理焦点的其他 API 为 <xref:System.Windows.UIElement.MoveFocus%2A> 和 <xref:System.Windows.UIElement.PredictFocus%2A> 。  
  
 <xref:System.Windows.FrameworkElement.MoveFocus%2A>将焦点更改为应用程序中的下一个元素。  <xref:System.Windows.Input.TraversalRequest>用于指定方向。   <xref:System.Windows.Input.FocusNavigationDirection>传递的用于 <xref:System.Windows.UIElement.MoveFocus%2A> 指定可以移动的不同方向焦点，如 <xref:System.Windows.Input.FocusNavigationDirection.First> 、 <xref:System.Windows.Input.FocusNavigationDirection.Last> <xref:System.Windows.Input.FocusNavigationDirection.Up> 和 <xref:System.Windows.Input.FocusNavigationDirection.Down> 。  
  
 下面的示例使用 <xref:System.Windows.FrameworkElement.MoveFocus%2A> 更改焦点元素。  
  
 [!code-csharp[focussample#FocusSampleMoveFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/FocusSample/CSharp/Window1.xaml.cs#focussamplemovefocus)]
 [!code-vb[focussample#FocusSampleMoveFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FocusSample/visualbasic/window1.xaml.vb#focussamplemovefocus)]  
  
 <xref:System.Windows.FrameworkElement.PredictFocus%2A>返回当焦点被更改时将接收焦点的对象。  目前仅 <xref:System.Windows.Input.FocusNavigationDirection.Up> 支持、 <xref:System.Windows.Input.FocusNavigationDirection.Down> 、 <xref:System.Windows.Input.FocusNavigationDirection.Left> 和 <xref:System.Windows.Input.FocusNavigationDirection.Right> <xref:System.Windows.FrameworkElement.PredictFocus%2A> 。  
  
<a name="Focus_Events"></a>
## <a name="focus-events"></a>焦点事件  
 与键盘焦点相关的事件为 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> 、 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus> 和 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocus> <xref:System.Windows.Input.Keyboard.LostKeyboardFocus> 。  事件在类上定义为附加事件 <xref:System.Windows.Input.Keyboard> ，但更易于访问，作为基元素类上的等效路由事件。  有关事件的详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.Keyboard.GotKeyboardFocus>当元素获取键盘焦点时，将引发。  <xref:System.Windows.Input.Keyboard.LostKeyboardFocus>当元素失去键盘焦点时引发。  如果 <xref:System.Windows.Input.Keyboard.PreviewGotKeyboardFocus> 处理了事件或 <xref:System.Windows.Input.Keyboard.PreviewLostKeyboardFocusEvent> 事件并且 <xref:System.Windows.RoutedEventArgs.Handled%2A> 将设置为 `true` ，则焦点将不会更改。  
  
 下面的示例将 <xref:System.Windows.UIElement.GotKeyboardFocus> 和 <xref:System.Windows.UIElement.LostKeyboardFocus> 事件处理程序附加到 <xref:System.Windows.Controls.TextBox> 。  
  
 [!code-xaml[keyboardsample#KeyboardSampleXAMLHandlerHookup](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml#keyboardsamplexamlhandlerhookup)]  
  
 当 <xref:System.Windows.Controls.TextBox> 获取键盘焦点时， <xref:System.Windows.Controls.Control.Background%2A> 的属性将 <xref:System.Windows.Controls.TextBox> 更改为 <xref:System.Windows.Media.Brushes.LightBlue%2A> 。  
  
 [!code-csharp[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplegotfocus)]
 [!code-vb[keyboardsample#KeyboardSampleGotFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplegotfocus)]  
  
 当 <xref:System.Windows.Controls.TextBox> 失去键盘焦点时， <xref:System.Windows.Controls.Control.Background%2A> 的属性将 <xref:System.Windows.Controls.TextBox> 改回为白色。  
  
 [!code-csharp[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyboardSample/CSharp/Window1.xaml.cs#keyboardsamplelostfocus)]
 [!code-vb[keyboardsample#KeyboardSampleLostFocus](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyboardSample/visualbasic/window1.xaml.vb#keyboardsamplelostfocus)]  
  
 与逻辑焦点相关的事件包括 <xref:System.Windows.UIElement.GotFocus> 和 <xref:System.Windows.UIElement.LostFocus> 。  这些事件定义 <xref:System.Windows.Input.FocusManager> 为作为附加事件，但不 <xref:System.Windows.Input.FocusManager> 公开 CLR 事件包装。  <xref:System.Windows.UIElement>并 <xref:System.Windows.ContentElement> 更方便地公开这些事件。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Input.FocusManager>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.ContentElement>
- [输入概述](input-overview.md)
- [基元素概述](base-elements-overview.md)
