---
title: RichTextBox 概述
description: '了解 Windows Presentation Foundation RichTextBox 控件如何允许用户显示或编辑内容（如文本、图像和表）。 请参阅 XAML 和 c # 示例。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], RichTextBox
- RichTextBox control [WPF], about RichTextBox control
ms.assetid: c94548b2-c1e9-4b62-b10c-dd8740eb23d8
ms.openlocfilehash: 525e27f9602136c68f160c738fd1c92ea761536c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166238"
---
# <a name="richtextbox-overview"></a>RichTextBox 概述

<xref:System.Windows.Controls.RichTextBox>利用该控件，可以显示或编辑流内容，包括段落、图像、表等。 本主题将介绍 <xref:System.Windows.Controls.TextBox> 类，并提供有关如何在和 c # 中使用它的示例 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a>使用 TextBox 还是 RichTextBox？

<xref:System.Windows.Controls.RichTextBox>和都 <xref:System.Windows.Controls.TextBox> 允许用户编辑文本，但是，在不同的方案中使用这两个控件。 <xref:System.Windows.Controls.RichTextBox>当用户需要编辑带格式的文本、图像、表或其他丰富内容时，最好选择。 例如，编辑需要格式设置、图像等的文档、文章或博客最好是使用来完成的 <xref:System.Windows.Controls.RichTextBox> 。 <xref:System.Windows.Controls.TextBox>需要较少的系统资源 <xref:System.Windows.Controls.RichTextBox> ，如果只需要编辑纯文本（即窗体中的使用情况），则它是理想的选择。 有关的详细信息，请参阅[TextBox 概述](textbox-overview.md) <xref:System.Windows.Controls.TextBox> 。 下表总结了和的主要功能 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。

|控制|实时拼写检查|上下文菜单|格式命令，如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （Ctr + B）|<xref:System.Windows.Documents.FlowDocument>内容，如图像、段落、表等。|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|“是”|是|否|不能。|
|<xref:System.Windows.Controls.RichTextBox>|“是”|“是”|“是”|是|

> [!NOTE]
> 虽然不 <xref:System.Windows.Controls.TextBox> 支持格式相关的命令 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （如（Ctr + B）），但这两个控件（例如）支持许多基本命令 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> 。

后面将更详细地介绍上表中的功能。

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a>创建 RichTextBox

下面的代码演示如何创建一个 <xref:System.Windows.Controls.RichTextBox> ，用户可以在其中编辑丰富内容。

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

具体而言，中编辑的内容 <xref:System.Windows.Controls.RichTextBox> 是流内容。 流内容可包含许多类型的元素，包括带格式的文本、图像、列表和表格。 有关流文档的详细信息，请参阅[流文档概述](../advanced/flow-document-overview.md)。 为了包含流内容，将 <xref:System.Windows.Controls.RichTextBox> 承载一个对象， <xref:System.Windows.Documents.FlowDocument> 该对象又包含可编辑的内容。 为了演示中的流内容 <xref:System.Windows.Controls.RichTextBox> ，以下代码演示了如何 <xref:System.Windows.Controls.RichTextBox> 使用段落和粗体文本创建。

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

下图显示了此示例的呈现效果。

![具有内容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")

元素（例如 <xref:System.Windows.Documents.Paragraph> 和） <xref:System.Windows.Documents.Bold> 确定中的内容如何 <xref:System.Windows.Controls.RichTextBox> 显示。 当用户编辑 <xref:System.Windows.Controls.RichTextBox> 内容时，它们会更改此流内容。 若要了解有关流内容的功能及其工作方式的详细信息，请参阅[流文档概述](../advanced/flow-document-overview.md)。

> [!NOTE]
> 中的流内容的 <xref:System.Windows.Controls.RichTextBox> 行为与其他控件中包含的流内容完全相同。 例如，不存在中的列 <xref:System.Windows.Controls.RichTextBox> ，因此不会自动调整大小行为。 而且，内置功能（如搜索、查看模式、页面导航和缩放）在中不可用 <xref:System.Windows.Controls.RichTextBox> 。

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a>实时拼写检查

您可以在或中启用实时拼写检查 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。 启用拼写检查时，任何拼写错误的字词下方都会出现红线（见下图）。

![带有拼写&#45;检查的 Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")

若要了解如何启用拼写检查，请参阅[在文本编辑控件中启用拼写检查](how-to-enable-spell-checking-in-a-text-editing-control.md)。

<a name="context_menu"></a>

## <a name="context-menu"></a>上下文菜单

默认情况下， <xref:System.Windows.Controls.TextBox> 和都 <xref:System.Windows.Controls.RichTextBox> 具有一个上下文菜单，当用户在该控件内单击鼠标右键时，将显示该菜单。 上下文菜单使用户可以剪切、复制或粘贴（见下图）。

![具有上下文菜单的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")

可以创建自己的自定义上下文菜单来重写默认的上下文菜单。 有关详细信息，请参阅[在 RichTextBox 中定位自定义上下文菜单](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a>编辑命令

编辑命令使用户能够在中设置可编辑内容的格式 <xref:System.Windows.Controls.RichTextBox> 。 除了基本的编辑命令外， <xref:System.Windows.Controls.RichTextBox> 还包括不支持的格式设置命令 <xref:System.Windows.Controls.TextBox> 。 例如，当在中编辑时 <xref:System.Windows.Controls.RichTextBox> ，用户可以按 Ctr + B 来切换粗体文本格式。 <xref:System.Windows.Documents.EditingCommands>有关可用命令的完整列表，请参阅。 除了使用键盘快捷方式，还可以将命令与按钮之类的其他控件挂钩。 以下示例演示如何创建如何创建简单的工具栏，其中包含用户可用来更改文本格式的按钮。

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

下图显示此示例的显示效果。

![具有工具栏的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a>检测内容何时更改

通常， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件应该用于在或更改中的文本时进行检测， <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 而不是像预期那样进行检测 <xref:System.Windows.UIElement.KeyDown> 。 有关示例，请参阅[检测 TextBox 中的文本何时更改](how-to-detect-when-text-in-a-textbox-has-changed.md)。

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a>保存、加载和打印 RichTextBox 内容

下面的示例演示如何将的内容保存 <xref:System.Windows.Controls.RichTextBox> 到文件，将该内容重新加载到 <xref:System.Windows.Controls.RichTextBox> 中，然后打印内容。 下面是示例的标记。

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

下面是该示例的隐藏代码。

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a>请参阅

- [操作指南主题](richtextbox-how-to-topics.md)
- [TextBox 概述](textbox-overview.md)
