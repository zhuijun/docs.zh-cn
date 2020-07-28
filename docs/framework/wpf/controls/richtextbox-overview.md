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
# <a name="richtextbox-overview"></a><span data-ttu-id="0ae9f-104">RichTextBox 概述</span><span class="sxs-lookup"><span data-stu-id="0ae9f-104">RichTextBox Overview</span></span>

<span data-ttu-id="0ae9f-105"><xref:System.Windows.Controls.RichTextBox>利用该控件，可以显示或编辑流内容，包括段落、图像、表等。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-105">The <xref:System.Windows.Controls.RichTextBox> control enables you to display or edit flow content including paragraphs, images, tables, and more.</span></span> <span data-ttu-id="0ae9f-106">本主题将介绍 <xref:System.Windows.Controls.TextBox> 类，并提供有关如何在和 c # 中使用它的示例 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-106">This topic introduces the <xref:System.Windows.Controls.TextBox> class and provides examples of how to use it in both [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] and C#.</span></span>

<a name="textbox_or_richtextbox"></a>

## <a name="textbox-or-richtextbox"></a><span data-ttu-id="0ae9f-107">使用 TextBox 还是 RichTextBox？</span><span class="sxs-lookup"><span data-stu-id="0ae9f-107">TextBox or RichTextBox?</span></span>

<span data-ttu-id="0ae9f-108"><xref:System.Windows.Controls.RichTextBox>和都 <xref:System.Windows.Controls.TextBox> 允许用户编辑文本，但是，在不同的方案中使用这两个控件。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-108">Both <xref:System.Windows.Controls.RichTextBox> and <xref:System.Windows.Controls.TextBox> allow users to edit text, however, the two controls are used in different scenarios.</span></span> <span data-ttu-id="0ae9f-109"><xref:System.Windows.Controls.RichTextBox>当用户需要编辑带格式的文本、图像、表或其他丰富内容时，最好选择。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-109">A <xref:System.Windows.Controls.RichTextBox> is a better choice when it is necessary for the user to edit formatted text, images, tables, or other rich content.</span></span> <span data-ttu-id="0ae9f-110">例如，编辑需要格式设置、图像等的文档、文章或博客最好是使用来完成的 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-110">For example, editing a document, article, or blog that requires formatting, images, etc is best accomplished using a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="0ae9f-111"><xref:System.Windows.Controls.TextBox>需要较少的系统资源 <xref:System.Windows.Controls.RichTextBox> ，如果只需要编辑纯文本（即窗体中的使用情况），则它是理想的选择。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-111">A <xref:System.Windows.Controls.TextBox> requires less system resources then a <xref:System.Windows.Controls.RichTextBox> and it is ideal when only plain text needs to be edited (i.e. usage in forms).</span></span> <span data-ttu-id="0ae9f-112">有关的详细信息，请参阅[TextBox 概述](textbox-overview.md) <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-112">See [TextBox Overview](textbox-overview.md) for more information on <xref:System.Windows.Controls.TextBox>.</span></span> <span data-ttu-id="0ae9f-113">下表总结了和的主要功能 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-113">The table below summarizes the main features of <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox>.</span></span>

|<span data-ttu-id="0ae9f-114">控制</span><span class="sxs-lookup"><span data-stu-id="0ae9f-114">Control</span></span>|<span data-ttu-id="0ae9f-115">实时拼写检查</span><span class="sxs-lookup"><span data-stu-id="0ae9f-115">Real-time Spellchecking</span></span>|<span data-ttu-id="0ae9f-116">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="0ae9f-116">Context Menu</span></span>|<span data-ttu-id="0ae9f-117">格式命令，如 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （Ctr + B）</span><span class="sxs-lookup"><span data-stu-id="0ae9f-117">Formatting commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B)</span></span>|<span data-ttu-id="0ae9f-118"><xref:System.Windows.Documents.FlowDocument>内容，如图像、段落、表等。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-118"><xref:System.Windows.Documents.FlowDocument> content like images, paragraphs, tables, etc.</span></span>|
|-------------|------------------------------|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="0ae9f-119">“是”</span><span class="sxs-lookup"><span data-stu-id="0ae9f-119">Yes</span></span>|<span data-ttu-id="0ae9f-120">是</span><span class="sxs-lookup"><span data-stu-id="0ae9f-120">Yes</span></span>|<span data-ttu-id="0ae9f-121">否</span><span class="sxs-lookup"><span data-stu-id="0ae9f-121">No</span></span>|<span data-ttu-id="0ae9f-122">不能。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-122">No.</span></span>|
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="0ae9f-123">“是”</span><span class="sxs-lookup"><span data-stu-id="0ae9f-123">Yes</span></span>|<span data-ttu-id="0ae9f-124">“是”</span><span class="sxs-lookup"><span data-stu-id="0ae9f-124">Yes</span></span>|<span data-ttu-id="0ae9f-125">“是”</span><span class="sxs-lookup"><span data-stu-id="0ae9f-125">Yes</span></span>|<span data-ttu-id="0ae9f-126">是</span><span class="sxs-lookup"><span data-stu-id="0ae9f-126">Yes</span></span>|

> [!NOTE]
> <span data-ttu-id="0ae9f-127">虽然不 <xref:System.Windows.Controls.TextBox> 支持格式相关的命令 <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> （如（Ctr + B）），但这两个控件（例如）支持许多基本命令 <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-127">Although <xref:System.Windows.Controls.TextBox> does not support formatting related commands like <xref:System.Windows.Documents.EditingCommands.ToggleBold%2A> (Ctr+B), many basic commands are supported by both controls such as <xref:System.Windows.Documents.EditingCommands.MoveToLineEnd%2A>.</span></span>

<span data-ttu-id="0ae9f-128">后面将更详细地介绍上表中的功能。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-128">The features from the table above are covered in more detail later.</span></span>

<a name="creating_a_richtextbox"></a>

## <a name="creating-a-richtextbox"></a><span data-ttu-id="0ae9f-129">创建 RichTextBox</span><span class="sxs-lookup"><span data-stu-id="0ae9f-129">Creating a RichTextBox</span></span>

<span data-ttu-id="0ae9f-130">下面的代码演示如何创建一个 <xref:System.Windows.Controls.RichTextBox> ，用户可以在其中编辑丰富内容。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-130">The code below shows how to create a <xref:System.Windows.Controls.RichTextBox> that a user can edit rich content in.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#BasicRichTextBoxExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/BasicRichTextBoxExample.xaml#basicrichtextboxexamplewholepage)]

<span data-ttu-id="0ae9f-131">具体而言，中编辑的内容 <xref:System.Windows.Controls.RichTextBox> 是流内容。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-131">Specifically, the content edited in a <xref:System.Windows.Controls.RichTextBox> is flow content.</span></span> <span data-ttu-id="0ae9f-132">流内容可包含许多类型的元素，包括带格式的文本、图像、列表和表格。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-132">Flow content can contain many types of elements including formatted text, images, lists, and tables.</span></span> <span data-ttu-id="0ae9f-133">有关流文档的详细信息，请参阅[流文档概述](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-133">See [Flow Document Overview](../advanced/flow-document-overview.md) for in depth information on flow documents.</span></span> <span data-ttu-id="0ae9f-134">为了包含流内容，将 <xref:System.Windows.Controls.RichTextBox> 承载一个对象， <xref:System.Windows.Documents.FlowDocument> 该对象又包含可编辑的内容。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-134">In order to contain flow content, a <xref:System.Windows.Controls.RichTextBox> hosts a <xref:System.Windows.Documents.FlowDocument> object which in turn contains the editable content.</span></span> <span data-ttu-id="0ae9f-135">为了演示中的流内容 <xref:System.Windows.Controls.RichTextBox> ，以下代码演示了如何 <xref:System.Windows.Controls.RichTextBox> 使用段落和粗体文本创建。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-135">To demonstrate flow content in a <xref:System.Windows.Controls.RichTextBox>, the following code shows how to create a <xref:System.Windows.Controls.RichTextBox> with a paragraph and some bolded text.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#RichTextBoxWithContentExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/RichTextBoxWithContentExample.xaml#richtextboxwithcontentexamplewholepage)]

[!code-csharp[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/CSharp/BasicRichTextBoxWithContentExample.cs#basicrichtextboxwithcontentcodeonlyexample)]
[!code-vb[RichTextBoxMiscSnippets_procedural_snip#BasicRichTextBoxWithContentCodeOnlyExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_procedural_snip/visualbasic/basicrichtextboxwithcontentexample.vb#basicrichtextboxwithcontentcodeonlyexample)]

<span data-ttu-id="0ae9f-136">下图显示了此示例的呈现效果。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-136">The following illustration shows how this sample renders.</span></span>

<span data-ttu-id="0ae9f-137">![具有内容的 RichTextBox](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span><span class="sxs-lookup"><span data-stu-id="0ae9f-137">![RichTextBox with content](./media/editing-richtextbox-with-content.png "Editing_RichTextBox_with_Content")</span></span>

<span data-ttu-id="0ae9f-138">元素（例如 <xref:System.Windows.Documents.Paragraph> 和） <xref:System.Windows.Documents.Bold> 确定中的内容如何 <xref:System.Windows.Controls.RichTextBox> 显示。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-138">Elements like <xref:System.Windows.Documents.Paragraph> and <xref:System.Windows.Documents.Bold> determine how the content inside a <xref:System.Windows.Controls.RichTextBox> appears.</span></span> <span data-ttu-id="0ae9f-139">当用户编辑 <xref:System.Windows.Controls.RichTextBox> 内容时，它们会更改此流内容。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-139">As a user edits <xref:System.Windows.Controls.RichTextBox> content, they change this flow content.</span></span> <span data-ttu-id="0ae9f-140">若要了解有关流内容的功能及其工作方式的详细信息，请参阅[流文档概述](../advanced/flow-document-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-140">To learn more about the features of flow content and how to work with it, see [Flow Document Overview](../advanced/flow-document-overview.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0ae9f-141">中的流内容的 <xref:System.Windows.Controls.RichTextBox> 行为与其他控件中包含的流内容完全相同。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-141">Flow content inside a <xref:System.Windows.Controls.RichTextBox> does not behave exactly like flow content contained in other controls.</span></span> <span data-ttu-id="0ae9f-142">例如，不存在中的列 <xref:System.Windows.Controls.RichTextBox> ，因此不会自动调整大小行为。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-142">For example, there are no columns in a <xref:System.Windows.Controls.RichTextBox> and hence no automatic resizing behavior.</span></span> <span data-ttu-id="0ae9f-143">而且，内置功能（如搜索、查看模式、页面导航和缩放）在中不可用 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-143">Also, built in features like search, viewing mode, page navigation, and zoom are not available within a <xref:System.Windows.Controls.RichTextBox>.</span></span>

<a name="realtime_spellechecking"></a>

## <a name="real-time-spell-checking"></a><span data-ttu-id="0ae9f-144">实时拼写检查</span><span class="sxs-lookup"><span data-stu-id="0ae9f-144">Real-time Spell Checking</span></span>

<span data-ttu-id="0ae9f-145">您可以在或中启用实时拼写检查 <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-145">You can enable real-time spell checking in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="0ae9f-146">启用拼写检查时，任何拼写错误的字词下方都会出现红线（见下图）。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-146">When spellchecking is turned on, a red line appears underneath any misspelled words (see picture below).</span></span>

<span data-ttu-id="0ae9f-147">![带有拼写&#45;检查的 Textbox](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span><span class="sxs-lookup"><span data-stu-id="0ae9f-147">![Textbox with spell&#45;checking](./media/editing-textbox-with-spellchecking.png "Editing_TextBox_with_Spellchecking")</span></span>

<span data-ttu-id="0ae9f-148">若要了解如何启用拼写检查，请参阅[在文本编辑控件中启用拼写检查](how-to-enable-spell-checking-in-a-text-editing-control.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-148">See [Enable Spell Checking in a Text Editing Control](how-to-enable-spell-checking-in-a-text-editing-control.md) to learn how to enable spellchecking.</span></span>

<a name="context_menu"></a>

## <a name="context-menu"></a><span data-ttu-id="0ae9f-149">上下文菜单</span><span class="sxs-lookup"><span data-stu-id="0ae9f-149">Context Menu</span></span>

<span data-ttu-id="0ae9f-150">默认情况下， <xref:System.Windows.Controls.TextBox> 和都 <xref:System.Windows.Controls.RichTextBox> 具有一个上下文菜单，当用户在该控件内单击鼠标右键时，将显示该菜单。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-150">By default, both <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.RichTextBox> have a context menu that appears when a user right-clicks inside the control.</span></span> <span data-ttu-id="0ae9f-151">上下文菜单使用户可以剪切、复制或粘贴（见下图）。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-151">The context menu allows the user to cut, copy, or paste (see illustration below).</span></span>

<span data-ttu-id="0ae9f-152">![具有上下文菜单的 TextBox](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")</span><span class="sxs-lookup"><span data-stu-id="0ae9f-152">![TextBox with context menu](./media/editing-textbox-with-context-menu.png "Editing_TextBox_with_Context_Menu")</span></span>

<span data-ttu-id="0ae9f-153">可以创建自己的自定义上下文菜单来重写默认的上下文菜单。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-153">You can create your own custom context menu to override the default one.</span></span> <span data-ttu-id="0ae9f-154">有关详细信息，请参阅[在 RichTextBox 中定位自定义上下文菜单](how-to-position-a-custom-context-menu-in-a-richtextbox.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-154">See [Position a Custom Context Menu in a RichTextBox](how-to-position-a-custom-context-menu-in-a-richtextbox.md) for more information.</span></span>

<a name="detect_when_content_changes"></a>

## <a name="editing-commands"></a><span data-ttu-id="0ae9f-155">编辑命令</span><span class="sxs-lookup"><span data-stu-id="0ae9f-155">Editing Commands</span></span>

<span data-ttu-id="0ae9f-156">编辑命令使用户能够在中设置可编辑内容的格式 <xref:System.Windows.Controls.RichTextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-156">Editing commands enable users to format editable content inside a <xref:System.Windows.Controls.RichTextBox>.</span></span> <span data-ttu-id="0ae9f-157">除了基本的编辑命令外， <xref:System.Windows.Controls.RichTextBox> 还包括不支持的格式设置命令 <xref:System.Windows.Controls.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-157">Besides basic editing commands, <xref:System.Windows.Controls.RichTextBox> includes formatting commands that <xref:System.Windows.Controls.TextBox> does not support.</span></span> <span data-ttu-id="0ae9f-158">例如，当在中编辑时 <xref:System.Windows.Controls.RichTextBox> ，用户可以按 Ctr + B 来切换粗体文本格式。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-158">For example, when editing in a <xref:System.Windows.Controls.RichTextBox>, a user could press Ctr+B to toggle bold text formatting.</span></span> <span data-ttu-id="0ae9f-159"><xref:System.Windows.Documents.EditingCommands>有关可用命令的完整列表，请参阅。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-159">See <xref:System.Windows.Documents.EditingCommands> for a complete list of commands available.</span></span> <span data-ttu-id="0ae9f-160">除了使用键盘快捷方式，还可以将命令与按钮之类的其他控件挂钩。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-160">In addition to using keyboard shortcuts, you can hook commands up to other controls like buttons.</span></span> <span data-ttu-id="0ae9f-161">以下示例演示如何创建如何创建简单的工具栏，其中包含用户可用来更改文本格式的按钮。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-161">The following example shows how to create a simple tool bar containing buttons that the user can use to change text formatting.</span></span>

[!code-xaml[RichTextBox_InputPanel_snip#RichTextBoxWithToolBarExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBox_InputPanel_snip/CS/Window1.xaml#richtextboxwithtoolbarexamplewholepage)]

<span data-ttu-id="0ae9f-162">下图显示此示例的显示效果。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-162">The following illustration shows how this sample displays.</span></span>

<span data-ttu-id="0ae9f-163">![具有工具栏的 RichTextBox](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")</span><span class="sxs-lookup"><span data-stu-id="0ae9f-163">![RichTextBox with ToolBar](./media/editing-richtextbox-with-toobar.gif "Editing_RichTextBox_with_TooBar")</span></span>

<a name="editing_commands"></a>

## <a name="detect-when-content-changes"></a><span data-ttu-id="0ae9f-164">检测内容何时更改</span><span class="sxs-lookup"><span data-stu-id="0ae9f-164">Detect when Content Changes</span></span>

<span data-ttu-id="0ae9f-165">通常， <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> 事件应该用于在或更改中的文本时进行检测， <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.RichTextBox> 而不是像预期那样进行检测 <xref:System.Windows.UIElement.KeyDown> 。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-165">Usually the <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> event should be used to detect whenever the text in a <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox> changes rather then <xref:System.Windows.UIElement.KeyDown> as you might expect.</span></span> <span data-ttu-id="0ae9f-166">有关示例，请参阅[检测 TextBox 中的文本何时更改](how-to-detect-when-text-in-a-textbox-has-changed.md)。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-166">See [Detect When Text in a TextBox Has Changed](how-to-detect-when-text-in-a-textbox-has-changed.md) for an example.</span></span>

<a name="save_load_and_print_richtextbox_content"></a>

## <a name="save-load-and-print-richtextbox-content"></a><span data-ttu-id="0ae9f-167">保存、加载和打印 RichTextBox 内容</span><span class="sxs-lookup"><span data-stu-id="0ae9f-167">Save, Load, and Print RichTextBox Content</span></span>

<span data-ttu-id="0ae9f-168">下面的示例演示如何将的内容保存 <xref:System.Windows.Controls.RichTextBox> 到文件，将该内容重新加载到 <xref:System.Windows.Controls.RichTextBox> 中，然后打印内容。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-168">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span> <span data-ttu-id="0ae9f-169">下面是示例的标记。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-169">Below is the markup for the example.</span></span>

[!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]

<span data-ttu-id="0ae9f-170">下面是该示例的隐藏代码。</span><span class="sxs-lookup"><span data-stu-id="0ae9f-170">Below is the code behind for the example.</span></span>

[!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
[!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]

## <a name="see-also"></a><span data-ttu-id="0ae9f-171">请参阅</span><span class="sxs-lookup"><span data-stu-id="0ae9f-171">See also</span></span>

- [<span data-ttu-id="0ae9f-172">操作指南主题</span><span class="sxs-lookup"><span data-stu-id="0ae9f-172">How-to Topics</span></span>](richtextbox-how-to-topics.md)
- [<span data-ttu-id="0ae9f-173">TextBox 概述</span><span class="sxs-lookup"><span data-stu-id="0ae9f-173">TextBox Overview</span></span>](textbox-overview.md)
