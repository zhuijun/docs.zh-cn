---
title: 命令概述
description: 了解如何在 Windows Presentation Foundation 中提供输入机制，该机制提供比设备输入更具语义级别的输入处理。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interfaces [WPF], ICommandSource
- command library [WPF]
- commands [WPF], definition of
- CommandBindings [WPF]
- ICommandSource interfaces [WPF]
- commanding [WPF]
- CommandManager [WPF]
ms.assetid: bc208dfe-367d-426a-99de-52b7e7511e81
ms.openlocfilehash: 4f7d12fbf0de9b1546f15061ab7eb1318378bbbb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168127"
---
# <a name="commanding-overview"></a>命令概述
<a name="introduction"></a>命令是 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 中的一种输出机制，与设备输出相比，其提供的输出处理更侧重于语义级别。 示例命令如许多应用程序均具有的“复制”****、“剪切”**** 和“粘贴”**** 操作。  
  
 本概述定义 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中有哪些命令、哪些类属于命令模型以及如何在应用程序中使用和创建命令。  
  
 本主题包含以下各节：  
  
- [什么是命令？](#commands_at_10000_feet)  
  
- [WPF 中的简单命令示例](#simple_command)  
  
- [WPF 命令中的四个主要概念](#Four_main_Concepts)  
  
- [命令库](#Command_Library)  
  
- [创建自定义命令](#creating_commands)  
  
<a name="commands_at_10000_feet"></a>
## <a name="what-are-commands"></a>什么是命令？  
 命令具有多个用途。 第一个用途是分隔语义和从执行命令的逻辑调用命令的对象。 这可使多个不同的源调用同一命令逻辑，并且可针对不同目标自定义命令逻辑。 例如，许多应用程序中均有的编辑操作“复制”****、“剪切”**** 和“粘贴”**** 若通过使用命令来实现，那么可通过使用不同的用户操作来调用它们。 应用程序可允许用户通过单击按钮、选择菜单中的项或使用组合键（例如 Ctrl+X）来剪切所选对象或文本。 通过使用命令，可将每种类型的用户操作绑定到相同逻辑。  
  
 命令的另一用途是指示操作是否可用。 继续以剪切对象或文本为例，此操作只有在选择了内容时才会发生作用。 如果用户在未选择任何内容的情况下尝试剪切对象或文本，则不会发生任何操作。 为了向用户指示这一点，许多应用程序通过禁用按钮和菜单项来告知用户是否可以执行某操作。 命令可以通过实现 <xref:System.Windows.Input.ICommand.CanExecute%2A> 方法来指示操作是否可行。 按钮可以订阅 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件，如果 <xref:System.Windows.Input.ICommand.CanExecute%2A> 返回 `false` 则禁用，如果 <xref:System.Windows.Input.ICommand.CanExecute%2A> 返回 `true` 则启用。  
  
 虽然命令的语义在应用程序和类之间可保持一致，但操作的逻辑特定于操作所针对的特定对象。 组合键 Ctrl+X 调用文本类、图像类和 Web 浏览器中的“剪切”**** 命令，但执行“剪切”**** 操作的实际逻辑由执行剪切的应用程序定义。 <xref:System.Windows.Input.RoutedCommand> 使客户端实现逻辑。 文本对象可将所选文本剪切到剪贴板，而图像对象则剪切所选图像。 应用程序处理 <xref:System.Windows.Input.CommandManager.Executed> 事件时可访问命令的目标，并根据目标的类型采取相应操作。  
  
<a name="simple_command"></a>
## <a name="simple-command-example-in-wpf"></a>WPF 中的简单命令示例  
 使用 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中命令的最简单方式是使用其中一个命令库类中预定义的 <xref:System.Windows.Input.RoutedCommand>；使用具有命令处理本机支持的控件；使用具有命令调用本机支持的控件。  <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令是 <xref:System.Windows.Input.ApplicationCommands> 类中的预定义命令之一。  <xref:System.Windows.Controls.TextBox> 控件含有用于处理 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令的内置逻辑。  <xref:System.Windows.Controls.MenuItem> 类具有调用命令的本机支持。  
  
 以下示例显示了如何设置 <xref:System.Windows.Controls.MenuItem>，以便在单击时它将调用 <xref:System.Windows.Controls.TextBox> 上的 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令，假定 <xref:System.Windows.Controls.TextBox> 具有键盘焦点。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewSimpleCommand](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewsimplecommand)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Four_main_Concepts"></a>
## <a name="four-main-concepts-in-wpf-commanding"></a>WPF 命令中的四个主要概念  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的路由命令模型可分解为四个主要概念：命令、命令源、命令目标和命令绑定：  
  
- *命令*是要执行的操作。  
  
- *命令源*是调用命令的对象。  
  
- *命令目标*是在其上执行命令的对象。  
  
- *命令绑定*是将命令逻辑映射到命令的对象。  
  
 在前面的示例中，<xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令是命令，<xref:System.Windows.Controls.MenuItem> 是命令源，<xref:System.Windows.Controls.TextBox> 是命令目标，命令绑定由 <xref:System.Windows.Controls.TextBox> 控件提供。  值得注意的是，<xref:System.Windows.Input.CommandBinding> 并不总是由作为命令目标类的控件提供。  通常，<xref:System.Windows.Input.CommandBinding> 必须由应用程序开发者创建，否则 <xref:System.Windows.Input.CommandBinding> 可能会附加到命令目标的上级元素。  
  
<a name="Commands"></a>
### <a name="commands"></a>命令  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令是通过实现 <xref:System.Windows.Input.ICommand> 接口创建的。  <xref:System.Windows.Input.ICommand> 公开了两种方法 <xref:System.Windows.Input.ICommand.Execute%2A> 和 <xref:System.Windows.Input.ICommand.CanExecute%2A>，以及一个事件 <xref:System.Windows.Input.ICommand.CanExecuteChanged>。 <xref:System.Windows.Input.ICommand.Execute%2A> 执行与该命令关联的操作。 <xref:System.Windows.Input.ICommand.CanExecute%2A> 确定是否可以在当前命令目标上执行该命令。 如果集中管理命令操作的命令管理器检测到命令源中存在一个可能使已引发命令无效但尚未由命令绑定执行的更改，则会引发 <xref:System.Windows.Input.ICommand.CanExecuteChanged>。  <xref:System.Windows.Input.ICommand> 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 实现是 <xref:System.Windows.Input.RoutedCommand> 类，并且是本概述的重点。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中输入的主要源是鼠标、键盘、墨迹和路由命令。  面向设备程度更高的输入使用 <xref:System.Windows.RoutedEvent> 通知应用程序页中的对象输入事件已发生。  <xref:System.Windows.Input.RoutedCommand> 也不例外。  <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 和 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法不包含该命令的应用程序逻辑，而是引发通过元素树通行和浮升的路由事件，直到遇到具有 <xref:System.Windows.Input.CommandBinding> 的对象。  <xref:System.Windows.Input.CommandBinding> 包含这些事件的处理程序，命令正是由这些处理程序执行。  有关 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中事件路由的详细信息，请参阅[路由事件概述](routed-events-overview.md)。  
  
 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.RoutedCommand.Execute%2A> 方法引发命令目标上的 <xref:System.Windows.Input.CommandManager.PreviewExecuted> 和 <xref:System.Windows.Input.CommandManager.Executed> 事件。  <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法引发命令目标上的 <xref:System.Windows.Input.CommandManager.CanExecute> 和 <xref:System.Windows.Input.CommandManager.PreviewCanExecute> 事件。  这些事件通过元素树通行和浮升，直到遇到一个具有针对该特定命令的 <xref:System.Windows.Input.CommandBinding> 的对象。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供了分布在几个类中的一组常用路由命令：<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.ComponentCommands> 和 <xref:System.Windows.Documents.EditingCommands>。  这些类仅由 <xref:System.Windows.Input.RoutedCommand> 对象构成，而不包含命令的实现逻辑。  实现逻辑由在其上执行命令的对象负责。  
  
<a name="Command_Sources"></a>
### <a name="command-sources"></a>命令源  
 命令源是调用命令的对象。  命令源的示例有 <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.Button> 和 <xref:System.Windows.Input.KeyGesture>。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的命令源通常实现 <xref:System.Windows.Input.ICommandSource> 接口。  
  
 <xref:System.Windows.Input.ICommandSource> 公开三个属性：<xref:System.Windows.Input.ICommandSource.Command%2A>、<xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 和 <xref:System.Windows.Input.ICommandSource.CommandParameter%2A>：  
  
- <xref:System.Windows.Input.ICommandSource.Command%2A> 是在调用命令源时执行的命令。  
  
- <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 是要执行命令的对象。  值得注意的是，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，仅当 <xref:System.Windows.Input.ICommand> 为 <xref:System.Windows.Input.RoutedCommand> 时，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 属性才适用。  如果在 <xref:System.Windows.Input.ICommandSource> 上设置 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 并且相应的命令不是 <xref:System.Windows.Input.RoutedCommand>，则忽略命令目标。 如果未设置 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A>，则具有键盘焦点的元素将成为命令目标。  
  
- <xref:System.Windows.Input.ICommandSource.CommandParameter%2A> 是用于将信息传递给实现命令的处理程序的用户定义数据类型。  
  
 实现 <xref:System.Windows.Input.ICommandSource> 的 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 类是 <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Documents.Hyperlink> 和 <xref:System.Windows.Input.InputBinding>。  单击 <xref:System.Windows.Controls.Primitives.ButtonBase>、<xref:System.Windows.Controls.MenuItem> 和 <xref:System.Windows.Documents.Hyperlink> 时，调用一个命令，当执行与其关联的 <xref:System.Windows.Input.InputGesture> 时，<xref:System.Windows.Input.InputBinding> 调用命令。  
  
 以下示例显示如何将 <xref:System.Windows.Controls.ContextMenu> 中的 <xref:System.Windows.Controls.MenuItem> 用作 <xref:System.Windows.Input.ApplicationCommands.Properties%2A> 命令的命令源。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewCmdSourceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewcmdsourcexaml)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcmdsource)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCmdSource](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcmdsource)]  
  
 通常，命令源将侦听 <xref:System.Windows.Input.RoutedCommand.CanExecuteChanged> 事件。  此事件通知命令源在当前命令目标上执行命令的能力可能已发生更改。  命令源可以使用 <xref:System.Windows.Input.RoutedCommand.CanExecute%2A> 方法查询 <xref:System.Windows.Input.RoutedCommand> 的当前状态。  如果命令无法执行，命令源可禁用自身。  此情况的一个示例是 <xref:System.Windows.Controls.MenuItem>，在命令无法执行时，它自身将灰显。  
  
 <xref:System.Windows.Input.InputGesture> 可以用作命令源。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中的两种输入笔势是 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.MouseGesture>。  可以将 <xref:System.Windows.Input.KeyGesture> 视为键盘快捷方式，例如 Ctrl+C。  <xref:System.Windows.Input.KeyGesture> 由一个 <xref:System.Windows.Input.Key> 和一组 <xref:System.Windows.Input.ModifierKeys> 组成。  <xref:System.Windows.Input.MouseGesture> 由 <xref:System.Windows.Input.MouseAction> 和一组可选的 <xref:System.Windows.Input.ModifierKeys> 组成。  
  
 为了将 <xref:System.Windows.Input.InputGesture> 用作命令源，它必须与一个命令相关联。 可通过几种方式来实现此目的。  其中一种方法是使用 <xref:System.Windows.Input.InputBinding>。  
  
 以下示例演示如何在 <xref:System.Windows.Input.KeyGesture> 和 <xref:System.Windows.Input.RoutedCommand> 之间创建 <xref:System.Windows.Input.KeyBinding>。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlkeybinding)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeybinding)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyBinding](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeybinding)]  
  
 将 <xref:System.Windows.Input.InputGesture> 关联到 <xref:System.Windows.Input.RoutedCommand> 的另一种方法是将 <xref:System.Windows.Input.InputGesture> 添加到 <xref:System.Windows.Input.RoutedCommand> 上的 <xref:System.Windows.Input.InputGestureCollection>。  
  
 以下示例演示如何将 <xref:System.Windows.Input.KeyGesture> 添加到 <xref:System.Windows.Input.RoutedCommand> 的 <xref:System.Windows.Input.InputGestureCollection> 中。  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewkeygestureoncmd)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewKeyGestureOnCmd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewkeygestureoncmd)]  
  
<a name="Command_Binding"></a>
### <a name="commandbinding"></a>CommandBinding  
 <xref:System.Windows.Input.CommandBinding> 将命令与实现该命令的事件处理程序相关联。  
  
 <xref:System.Windows.Input.CommandBinding> 类包含 <xref:System.Windows.Input.CommandBinding.Command%2A> 属性，及 <xref:System.Windows.Input.CommandBinding.PreviewExecuted>、<xref:System.Windows.Input.CommandBinding.Executed>、<xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件。  
  
 <xref:System.Windows.Input.CommandBinding.Command%2A> 是与 <xref:System.Windows.Input.CommandBinding> 关联的命令。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewExecuted> 和 <xref:System.Windows.Input.CommandBinding.Executed> 事件的事件处理程序实现命令逻辑。  附加到 <xref:System.Windows.Input.CommandBinding.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 事件的事件处理程序确定是否可以在当前命令目标上执行该命令。  
  
 以下示例演示如何在应用程序的根 <xref:System.Windows.Window> 上创建 <xref:System.Windows.Input.CommandBinding>。  <xref:System.Windows.Input.CommandBinding> 将 <xref:System.Windows.Input.ApplicationCommands.Open%2A> 命令与 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandBinding.CanExecute> 处理程序关联。  
  
 [!code-xaml[commandwithhandler#CommandHandlerCommandBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml#commandhandlercommandbinding)]  
  
 [!code-csharp[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandHandlerProcedural/CSharp/Window1.xaml.cs#commandhandlerbindinginit)]
 [!code-vb[CommandHandlerProcedural#CommandHandlerBindingInit](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandHandlerProcedural/visualbasic/window1.xaml.vb#commandhandlerbindinginit)]  
  
 接下来，创建了 <xref:System.Windows.Input.ExecutedRoutedEventHandler> 和 <xref:System.Windows.Input.CanExecuteRoutedEventHandler>。  <xref:System.Windows.Input.ExecutedRoutedEventHandler> 打开了显示字符串的 <xref:System.Windows.MessageBox>，该字符串表示已执行此命令。  <xref:System.Windows.Input.CanExecuteRoutedEventHandler> 将 <xref:System.Windows.Input.CanExecuteRoutedEventArgs.CanExecute%2A> 属性设置为 `true`。  
  
 [!code-csharp[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlerexecutedhandler)]
 [!code-vb[commandwithhandler#CommandHandlerExecutedHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlerexecutedhandler)]  
  
 [!code-csharp[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/commandWithHandler/CSharp/Window1.xaml.cs#commandhandlercanexecutehandler)]
 [!code-vb[commandwithhandler#CommandHandlerCanExecuteHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/commandWithHandler/VisualBasic/Window1.xaml.vb#commandhandlercanexecutehandler)]  
  
 将 <xref:System.Windows.Input.CommandBinding> 附加到特定对象，例如应用程序或控件的根 <xref:System.Windows.Window>。  <xref:System.Windows.Input.CommandBinding> 附加到的对象定义了绑定的范围。  例如，附加到命令目标的上级元素的 <xref:System.Windows.Input.CommandBinding> 可以通过 <xref:System.Windows.Input.CommandBinding.Executed> 事件到达，但无法到达附加到命令目标的下级元素的 <xref:System.Windows.Input.CommandBinding>。  其直接原因在于 <xref:System.Windows.RoutedEvent> 从引发事件的对象通行和浮升的方式。  
  
 在某些情况下，<xref:System.Windows.Input.CommandBinding> 会附加到命令目标本身，例如 <xref:System.Windows.Controls.TextBox> 类及 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.ApplicationCommands.Copy%2A> 和 <xref:System.Windows.Input.ApplicationCommands.Paste%2A> 命令。 然而，很多时候将 <xref:System.Windows.Input.CommandBinding> 附加到命令目标的上级元素（例如主要 <xref:System.Windows.Window> 或应用程序对象）会更加方便，尤其是在同一 <xref:System.Windows.Input.CommandBinding> 可用于多个命令目标时。  这是在创建命令基础结构时需要考虑的设计决策。  
  
<a name="Commane_Target"></a>
### <a name="command-target"></a>命令目标  
 命令目标是在其上执行命令的元素。  关于 <xref:System.Windows.Input.RoutedCommand>，命令目标是 <xref:System.Windows.Input.CommandManager.Executed> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 的路由开始的元素。  如前所述，在 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 中，仅当 <xref:System.Windows.Input.ICommand> 为 <xref:System.Windows.Input.RoutedCommand> 时，<xref:System.Windows.Input.ICommandSource> 上的 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 属性才适用。  如果在 <xref:System.Windows.Input.ICommandSource> 上设置 <xref:System.Windows.Input.ICommandSource.CommandTarget%2A> 并且相应的命令不是 <xref:System.Windows.Input.RoutedCommand>，则忽略命令目标。  
  
 命令源可以显式设置命令目标。  如果未定义命令目标，则具有键盘焦点的元素将用作命令目标。  将具有键盘焦点的元素用作命令目标的一个好处在于，这样可使应用程序开发者能够使用同一命令源在多个目标上调用命令，而无需跟踪命令目标。  例如，如果 <xref:System.Windows.Controls.MenuItem> 在具有 <xref:System.Windows.Controls.TextBox> 控件和 <xref:System.Windows.Controls.PasswordBox> 控件的应用程序中调用“Paste”命令，则目标可以是 <xref:System.Windows.Controls.TextBox> 或 <xref:System.Windows.Controls.PasswordBox>，具体取决于哪个控件具有键盘焦点****。  
  
 以下示例演示如何在标记和代码隐藏中显式设置命令目标。  
  
 [!code-xaml[CommandingOverviewSnippets#CommandingOverviewXAMLCommandTarget](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml#commandingoverviewxamlcommandtarget)]  
  
 [!code-csharp[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#commandingoverviewcommandtargetcodebehind)]
 [!code-vb[CommandingOverviewSnippets#CommandingOverviewCommandTargetCodeBehind](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#commandingoverviewcommandtargetcodebehind)]  
  
<a name="Command_Manager"></a>
### <a name="the-commandmanager"></a>CommandManager  
 <xref:System.Windows.Input.CommandManager> 提供许多与命令相关的函数。  它提供了一组静态方法，用于在特定元素中添加和删除 <xref:System.Windows.Input.CommandManager.PreviewExecuted>、<xref:System.Windows.Input.CommandManager.Executed>、<xref:System.Windows.Input.CommandManager.PreviewCanExecute> 和 <xref:System.Windows.Input.CommandManager.CanExecute> 事件处理程序。  它提供了将 <xref:System.Windows.Input.CommandBinding> 和 <xref:System.Windows.Input.InputBinding> 对象注册到特定类的方法。  <xref:System.Windows.Input.CommandManager> 还通过 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件提供了一种方法，用于在应引发 <xref:System.Windows.Input.ICommand.CanExecuteChanged> 事件时通知命令。  
  
 <xref:System.Windows.Input.CommandManager.InvalidateRequerySuggested%2A> 方法强制 <xref:System.Windows.Input.CommandManager> 引发 <xref:System.Windows.Input.CommandManager.RequerySuggested> 事件。  这在应禁用/启用命令的情况下非常有用，但对于 <xref:System.Windows.Input.CommandManager> 可识别的情况，则不太有用。  
  
<a name="Command_Library"></a>
## <a name="command-library"></a>命令库  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 提供一组预定义命令。  命令库包括以下类：<xref:System.Windows.Input.ApplicationCommands>、<xref:System.Windows.Input.NavigationCommands>、<xref:System.Windows.Input.MediaCommands>、<xref:System.Windows.Documents.EditingCommands> 和 <xref:System.Windows.Input.ComponentCommands>。  这些类提供诸如 <xref:System.Windows.Input.ApplicationCommands.Cut%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseBack%2A>、<xref:System.Windows.Input.NavigationCommands.BrowseForward%2A>、<xref:System.Windows.Input.MediaCommands.Play%2A>、<xref:System.Windows.Input.MediaCommands.Stop%2A> 和 <xref:System.Windows.Input.MediaCommands.Pause%2A> 的命令。  
  
 许多这些命令都包含一组默认输入绑定。  例如，如果指定应用程序处理 "复制" 命令，则会自动获取键盘绑定 "CTRL + C"。还会获取其他输入设备的绑定，如 Tablet PC 笔笔势和语音信息。  
  
 使用 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 引用各个命令库中的命令时，通常可省略公开静态命令属性的库类的类名。 一般来说，命令名称是明确作为字符串的，且存在所属类型来提供命令的逻辑分组，不过对于消除二义性这并不必要。 例如，可指定 `Command="Cut"` 而不是更为冗长的 `Command="ApplicationCommands.Cut"`。 这是一个方便的机制，内置于 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 命令处理器中（更准确地说，它是 <xref:System.Windows.Input.ICommand> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 处理器在加载时引用的类型转换器行为）。  
  
<a name="creating_commands"></a>
## <a name="creating-custom-commands"></a>创建自定义命令  
 如果命令库类中的命令不能满足需要，你可以创建自己的命令。  可通过两种方式创建自定义命令。  第一种方式是从头开始并实现 <xref:System.Windows.Input.ICommand> 接口。  另一种更常见的方法是创建 <xref:System.Windows.Input.RoutedCommand> 或 <xref:System.Windows.Input.RoutedUICommand>。  
  
 有关创建自定义 <xref:System.Windows.Input.RoutedCommand> 的示例，请参阅[创建自定义 RoutedCommand 示例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)。  
  
## <a name="see-also"></a>另请参阅

- <xref:System.Windows.Input.RoutedCommand>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Input.InputBinding>
- <xref:System.Windows.Input.CommandManager>
- [输入概述](input-overview.md)
- [路由事件概述](routed-events-overview.md)
- [实现 ICommandSource](how-to-implement-icommandsource.md)
- [如何：将命令添加到菜单项](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms741839(v=vs.90))
- [创建自定义 RoutedCommand 示例](https://github.com/Microsoft/WPF-Samples/tree/master/Input%20and%20Commands/CustomRoutedCommand)
