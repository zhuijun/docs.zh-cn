---
title: 流文档概述
description: 了解 Windows Presentation Foundation 中的流文档，该文档根据窗口大小、设备分辨率和用户首选项动态调整内容。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: dac0cb91175a1398a0124020c048e14d7bcd1f76
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165235"
---
# <a name="flow-document-overview"></a>流文档概述

流文档旨在优化查看和可读性。 流文档根据运行时变量（例如，窗口大小、设备分辨率和可选的用户首选项）来动态调整和重新排列内容，而不是设置为一个预定义的布局。 此外，流文档还提供一些高级文档功能，例如分页和分栏。 本主题概述了流文档及其创建方式。

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>什么是流文档？

流文档旨在根据窗口大小、设备分辨率和其他环境变量来“重排内容”。 此外，流文档还具有很多内置功能，包括搜索、能够优化可读性的查看模式以及更改字体大小和外观的功能。 当易读性是文档的主要使用要求时，最适合使用流文档。 相反，固定文档旨在提供静态表示形式。 当源内容的保真度至关重要时，就适合使用固定文档。 有关不同类型的文档的详细信息，请参阅[WPF 中的文档](documents-in-wpf.md)。

下图演示在多个不同大小的窗口中查看同一个示例流文档的情况。 随着显示区域的变化，内容将重新布局，以充分利用可用空间。

![流文档内容调整](./media/edocs-flowdocument.png "eDocs_FlowDocument")

如上图所示，流内容可包括多个组成部分，包括段落、列表、图像等等。 这些组成部分对应于标记中的元素和程序代码中的对象。 稍后将在本概述的 "[与流相关的类](#flow_related_classes)" 一节中详细介绍这些类。 现在，下面是一个简单的代码示例，该示例创建一个流文档，该文档包含一个带有文本粗体文本和列表的段落。

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

下图显示了此代码片段。

![屏幕快照：呈现的 FlowDocument 示例](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

在此示例中， <xref:System.Windows.Controls.FlowDocumentReader> 控件用于承载流内容。 有关流内容托管控件的详细信息，请参阅[流文档类型](#flow_document_types)。 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.List> 、 <xref:System.Windows.Documents.ListItem> 和 <xref:System.Windows.Documents.Bold> 元素用于根据标记中的顺序来控制内容格式设置。 例如， <xref:System.Windows.Documents.Bold> 元素仅跨越段落中的部分文本; 因此，只有文本部分为粗体。 如果使用过 HTML，你就会了解这一点。

如上图所示，流文档中内置了几个功能：

- 搜索：允许用户对整个文档执行全文搜索。

- 查看模式：用户可选择喜欢的查看模式，包括单页（一次一页）查看模式、一次两页（书本阅读格式）查看模式和连续滚动（无界限）查看模式。  有关这些查看模式的详细信息，请参阅 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 。

- 页面导航控件：如果文档的查看模式使用页面，则页面导航控件包括一个用于跳转到下一页（向下键）或上一页（向上键）的按钮，以及显示当前页码和总页数的指示器。 也可使用键盘上的箭头键来实现翻页操作。

- 缩放：缩放控件可使用户通过单击加号或减号按钮来相应地增大或减小缩放级别。 缩放控件还包括一个用于调整缩放级别的滑块。 有关详细信息，请参阅 <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A>。

这些功能可根据用于托管流内容的控件进行修改。 下一节介绍了各种控件。

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>流文档类型

流文档内容的显示和外观依赖于用于托管流内容的对象。 有四个支持查看流内容的控件： <xref:System.Windows.Controls.FlowDocumentReader> 、 <xref:System.Windows.Controls.FlowDocumentPageViewer> 、 <xref:System.Windows.Controls.RichTextBox> 和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 。 下面简要介绍了这些控件。

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>需要直接承载流内容，因此所有这些查看控件都将使用 <xref:System.Windows.Documents.FlowDocument> 来启用流内容承载。

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>包括使用户能够在各种查看模式之间进行动态选择的功能，包括单页（一次一页）查看模式、一次两页（书籍阅读格式）查看模式和连续滚动（无限）查看模式。 有关这些查看模式的详细信息，请参阅 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> 。 如果不需要在不同查看模式之间动态切换的功能， <xref:System.Windows.Controls.FlowDocumentPageViewer> 并提供了 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 在特定查看模式下固定的轻型流内容查看器。

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer 和 FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>以一次一页的查看模式显示内容，同时以 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 连续滚动模式显示内容。 <xref:System.Windows.Controls.FlowDocumentPageViewer>和 <xref:System.Windows.Controls.FlowDocumentScrollViewer> 都固定到特定的查看模式。 比较到 <xref:System.Windows.Controls.FlowDocumentReader> ，其中包括使用户能够在各种查看模式（由枚举提供）之间动态选择的功能 <xref:System.Windows.Controls.FlowDocumentReaderViewingMode> ，成本比或更多 <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> 。

默认情况下，总是显示垂直滚动条，而水平滚动条则在需要时显示。 的默认 UI <xref:System.Windows.Controls.FlowDocumentScrollViewer> 不包含工具栏; 但是， <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A> 属性可用于启用内置工具栏。

### <a name="richtextbox"></a>RichTextBox

<xref:System.Windows.Controls.RichTextBox>如果希望允许用户编辑流内容，请使用。 例如，如果想要创建一个允许用户处理表、斜体和粗体格式等操作的编辑器，则可以使用 <xref:System.Windows.Controls.RichTextBox> 。 有关详细信息，请参阅[RichTextBox 概述](../controls/richtextbox-overview.md)。

> [!NOTE]
> 中的流内容的 <xref:System.Windows.Controls.RichTextBox> 行为与其他控件中包含的流内容完全相同。 例如，不存在中的列 <xref:System.Windows.Controls.RichTextBox> ，因此不会自动调整大小行为。 而且，流内容（如搜索、查看模式、页面导航和缩放）的通常内置功能在中不可用 <xref:System.Windows.Controls.RichTextBox> 。

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>创建流内容

流内容可能比较复杂，包括各种元素，包括文本、图像、表甚至是 <xref:System.Windows.UIElement> 控件等派生类。 若要了解如何创建复杂流内容，掌握下列知识点非常关键：

- **与流相关的类**：流内容中使用的每个类都有特定用途。 此外，了解各种流类之间的层次关系有助于了解其使用方式。 例如，派生自类的类 <xref:System.Windows.Documents.Block> 用于包含其他对象，而派生自的类 <xref:System.Windows.Documents.Inline> 包含所显示的对象。

- **内容架构**：流文档可能需要大量嵌套元素。 内容架构指定了元素之间可能存在的父/子关系。

以下各节详细介绍了上述每个方面。

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>与流相关的类

下图演示了流内容中最常使用的对象：

![示意图：流内容元素类层次结构](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

根据流内容的用途，可分为两个重要类别：

1. **Block 派生类**：也称为“Block 内容元素”，或简称为“Block 元素”。 从继承的元素 <xref:System.Windows.Documents.Block> 可用于对公共父项下的元素进行分组，或将公共属性应用于组。

2. **Inline 派生类**：也称为“Inline 内容元素”，或简称为“Inline 元素”。 从继承的元素 <xref:System.Windows.Documents.Inline> 要么包含在块元素中，要么包含在另一个内联元素中。 Inline 元素通常用作在屏幕上呈现的内容的直接容器。 例如， <xref:System.Windows.Documents.Paragraph> （块元素）可以包含 <xref:System.Windows.Documents.Run> （内联元素），但 <xref:System.Windows.Documents.Run> 实际上包含在屏幕上呈现的文本。

下面简要介绍了这两个类别中的每个类。

### <a name="block-derived-classes"></a>Block 派生类

**Paragraph**

<xref:System.Windows.Documents.Paragraph>通常用于将内容分组到一个段落中。 Paragraph 的最简单且最常见的用途是创建文本段落。

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

但是，您还可以包含其他内联派生的元素，如下所示。

**节**

<xref:System.Windows.Documents.Section>仅用于包含其他 <xref:System.Windows.Documents.Block> 派生元素。 它不会向其中包含的元素应用任何默认格式。 但是，在上设置的任何属性值都 <xref:System.Windows.Documents.Section> 适用于其子元素。 使用节能够以编程方式循环访问其子集合。 <xref:System.Windows.Documents.Section>与 HTML 中的标记使用方式类似 \<DIV> 。

在下面的示例中，定义了三个段落 <xref:System.Windows.Documents.Section> 。 此部分的 <xref:System.Windows.Documents.TextElement.Background%2A> 属性值为红色，因此段落的背景色也为红色。

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>启用 <xref:System.Windows.UIElement> <xref:System.Windows.Controls.Button> 要嵌入到块派生流内容中的元素（即）。 <xref:System.Windows.Documents.InlineUIContainer>（如下所示）用于 <xref:System.Windows.UIElement> 在内联派生的流内容中嵌入元素。 <xref:System.Windows.Documents.BlockUIContainer>和非常 <xref:System.Windows.Documents.InlineUIContainer> 重要，因为 <xref:System.Windows.UIElement> 在流内容中无法使用，除非它包含在这两个元素之一中。

下面的示例演示如何使用 <xref:System.Windows.Documents.BlockUIContainer> 元素来承载 <xref:System.Windows.UIElement> 流内容中的对象。

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

下图显示了此示例的呈现效果：

![显示在流内容中嵌入的 UIElement 的屏幕截图。](./media/flow-document-overview/embedded-blockuicontainer.png)

**列表**

<xref:System.Windows.Documents.List>用于创建项目符号列表或数字列表。 将 <xref:System.Windows.Documents.List.MarkerStyle%2A> 属性设置为一个 <xref:System.Windows.TextMarkerStyle> 枚举值，以确定列表的样式。 下例演示了如何创建简单列表。

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>是唯一一个使用 <xref:System.Windows.Documents.ListItemCollection> 来管理子元素的流元素。

**表**

<xref:System.Windows.Documents.Table>用于创建表。 <xref:System.Windows.Documents.Table>与元素类似， <xref:System.Windows.Controls.Grid> 但具有更多的功能，因此需要更大的资源开销。 因为 <xref:System.Windows.Controls.Grid> 是 <xref:System.Windows.UIElement> ，所以它不能在流内容中使用，除非它包含在 <xref:System.Windows.Documents.BlockUIContainer> 或中 <xref:System.Windows.Documents.InlineUIContainer> 。 有关的详细信息 <xref:System.Windows.Documents.Table> ，请参阅[表概述](table-overview.md)。

### <a name="inline-derived-classes"></a>Inline 派生类

**Run**

<xref:System.Windows.Documents.Run>用于包含无格式文本。 你可能希望 <xref:System.Windows.Documents.Run> 对象在流内容中广泛使用。 但在标记中， <xref:System.Windows.Documents.Run> 无需显式使用元素。 <xref:System.Windows.Documents.Run>需要在使用代码创建或操作流文档时使用。 例如，在下面的标记中，第一个 <xref:System.Windows.Documents.Paragraph> 显式指定 <xref:System.Windows.Documents.Run> 元素，而第二个不指定。 这两个段落生成相同的输出。

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> 从 .NET Framework 4 开始，对象的 <xref:System.Windows.Documents.Run.Text%2A> 属性 <xref:System.Windows.Documents.Run> 是依赖属性。 可以将属性绑定 <xref:System.Windows.Documents.Run.Text%2A> 到数据源，例如 <xref:System.Windows.Controls.TextBlock> 。 <xref:System.Windows.Documents.Run.Text%2A>属性完全支持单向绑定。 <xref:System.Windows.Documents.Run.Text%2A>属性还支持双向绑定，但除外 <xref:System.Windows.Controls.RichTextBox> 。 有关示例，请参见 <xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>。

**格**

<xref:System.Windows.Documents.Span>将其他内联内容元素组合在一起。 不会对元素中的内容应用任何固有的呈现 <xref:System.Windows.Documents.Span> 。 但是，从继承的元素 <xref:System.Windows.Documents.Span> 包括 <xref:System.Windows.Documents.Hyperlink> 、 <xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Italic> 和会 <xref:System.Windows.Documents.Underline> 将格式应用于文本。

下面是一个示例， <xref:System.Windows.Documents.Span> 其中包含文本、 <xref:System.Windows.Documents.Bold> 元素和的内联内容 <xref:System.Windows.Controls.Button> 。

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

下面的屏幕截图显示了此示例的呈现效果。

![屏幕快照：呈现的 Span 示例](./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>启用 <xref:System.Windows.UIElement> <xref:System.Windows.Controls.Button> 要嵌入到内容元素中的元素（即像这样的控件） <xref:System.Windows.Documents.Inline> 。 此元素是上面所述的内联等效项 <xref:System.Windows.Documents.BlockUIContainer> 。 下面的示例使用 <xref:System.Windows.Documents.InlineUIContainer> <xref:System.Windows.Controls.Button> 在中插入内联 <xref:System.Windows.Documents.Paragraph> 。

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>不需要在标记中显式使用。 如果省略此方法，则在 <xref:System.Windows.Documents.InlineUIContainer> 编译代码时仍将创建。

**Figure 和 Floater**

<xref:System.Windows.Documents.Figure>和 <xref:System.Windows.Documents.Floater> 用于将内容嵌入到具有可独立于主内容流自定义的放置属性的位置属性。 <xref:System.Windows.Documents.Figure>或 <xref:System.Windows.Documents.Floater> 元素通常用于突出显示或强调设计部分内容，以承载主内容流中的支持图像或其他内容，或插入松散相关的内容（如播发）。

下面的示例演示如何在 <xref:System.Windows.Documents.Figure> 文本段落中嵌入。

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

下图显示了此示例的呈现效果。

![屏幕快照：图示例](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>和 <xref:System.Windows.Documents.Floater> 在不同方案中的使用方式不同。

**算**

- 可定位：可设置其水平和垂直定位点，以便相对于页面、内容、栏或段落进行停靠。 你还可以使用其 <xref:System.Windows.Documents.Figure.HorizontalOffset%2A> 和 <xref:System.Windows.Documents.Figure.VerticalOffset%2A> 属性来指定任意偏移量。

- 可调整到多个列：可将 <xref:System.Windows.Documents.Figure> 高度和宽度设置为页面、内容或列的高度或宽度的倍数。 请注意，对于页面和内容，倍数不能大于 1。 例如，可以将的宽度设置为 <xref:System.Windows.Documents.Figure> "0.5 页" 或 "0.25 content" 或 "2 列"。 还可将高度和宽度设置为绝对像素值。

- 不分页：如果中的内容 <xref:System.Windows.Documents.Figure> 无法放入 <xref:System.Windows.Documents.Figure> ，它将呈现合适的内容，并丢失剩余内容

**Floater：**

- 无法定位，可在能够为其提供空间的任何位置呈现。 不能设置偏移或定位 <xref:System.Windows.Documents.Floater> 。

- 不能调整为多列：默认情况下， <xref:System.Windows.Documents.Floater> 在一列的大小。 它有一个 <xref:System.Windows.Documents.Floater.Width%2A> 可设置为绝对像素值的属性，但如果此值大于一个列宽，则将忽略该属性，并将浮标调整到一列。 您可以通过设置正确的像素宽度来将其大小调整为小于一列，但调整大小不是列相对的，因此 "0.5 列" 不是宽度的有效表达式 <xref:System.Windows.Documents.Floater> 。 <xref:System.Windows.Documents.Floater>没有高度属性，且无法设置其高度，其高度取决于内容

- <xref:System.Windows.Documents.Floater>分页：如果其指定宽度的内容超出了1列高度，则浮标会断开并分页到下一列、下一页等。

 <xref:System.Windows.Documents.Figure>是一个很好的位置，可将独立内容置于要控制其大小和位置的位置，并确信内容符合指定的大小。 <xref:System.Windows.Documents.Floater>是放置更多自由流动内容的好位置，该内容与主页内容相似，但与主页内容分离。

**LineBreak**

<xref:System.Windows.Documents.LineBreak>导致在流内容中出现分行符。 以下示例演示了 <xref:System.Windows.Documents.LineBreak> 的用法。

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

下面的屏幕截图显示了此示例的呈现效果。

![屏幕快照：LineBreak 示例](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>流集合元素

在上述许多示例中， <xref:System.Windows.Documents.BlockCollection> 和用于以 <xref:System.Windows.Documents.InlineCollection> 编程方式构造流内容。 例如，若要向添加元素 <xref:System.Windows.Documents.Paragraph> ，可以使用以下语法：

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

这会将添加 <xref:System.Windows.Documents.Run> 到的 <xref:System.Windows.Documents.InlineCollection> <xref:System.Windows.Documents.Paragraph> 。  这与 <xref:System.Windows.Documents.Run> 标记中的隐式相同 <xref:System.Windows.Documents.Paragraph> ：

```xml
<Paragraph>
Some Text
</Paragraph>
```

作为使用的示例 <xref:System.Windows.Documents.BlockCollection> ，下面的示例创建一个新的， <xref:System.Windows.Documents.Section> 然后使用**add**方法将一个新添加 <xref:System.Windows.Documents.Paragraph> 到 <xref:System.Windows.Documents.Section> 内容。

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

除向流集合中添加项之外，还可以移除项。  下面的示例删除中的最后一个 <xref:System.Windows.Documents.Inline> 元素 <xref:System.Windows.Documents.Span> 。

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

下面的示例从中清除所有内容（ <xref:System.Windows.Documents.Inline> 元素） <xref:System.Windows.Documents.Span> 。

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

以编程方式使用流内容时，可能会广泛使用这些集合。

Flow 元素是否使用 <xref:System.Windows.Documents.InlineCollection> （Inlines）或 <xref:System.Windows.Documents.BlockCollection> （块）来包含其子元素取决于父元素（ <xref:System.Windows.Documents.Block> 或 <xref:System.Windows.Documents.Inline> ）可以包含的子元素的类型。 下一节中的内容架构中概述了流内容元素的包容规则。

> [!NOTE]
> 存在与流内容一起使用的第三种类型的集合， <xref:System.Windows.Documents.ListItemCollection> 但此集合仅用于 <xref:System.Windows.Documents.List> 。 此外，还使用了多个集合 <xref:System.Windows.Documents.Table> 。 有关详细信息，请参阅[表概述](table-overview.md)。

<a name="content_schema"></a>

## <a name="content-schema"></a>内容架构

不同流内容元素的数量是如此之多，因此了解某个元素可包含的子元素类型非常困难。 下面的关系图概述了流元素的包容规则。 箭头表示可能存在的父/子关系。

![示意图：流内容包含架构](./media/flow-content-schema.png "Flow_Content_Schema")

正如上面的关系图中所示，允许元素的子元素不一定由元素是元素还是元素确定 <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Inline> 。 例如，一个 <xref:System.Windows.Documents.Span> （ <xref:System.Windows.Documents.Inline> 元素）只能具有 <xref:System.Windows.Documents.Inline> 子元素，而 <xref:System.Windows.Documents.Figure> （也是一个 <xref:System.Windows.Documents.Inline> 元素）只能具有 <xref:System.Windows.Documents.Block> 子元素。 因此，关系图可用于快速确定哪些元素可以包含在其他元素中。 例如，使用关系图确定如何构造的流内容 <xref:System.Windows.Controls.RichTextBox> 。

**1.** <xref:System.Windows.Controls.RichTextBox> 必须包含一个 <xref:System.Windows.Documents.FlowDocument> ，而后者又必须包含一个 <xref:System.Windows.Documents.Block> 派生的对象。 下面是上述关系图中的对应部分。

![示意图：RichTextBox 包含规则](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

到此为止，标记可能类似于所示内容。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** 根据关系图，有几个 <xref:System.Windows.Documents.Block> 元素可供选择，包括、、 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.Table> 、 <xref:System.Windows.Documents.List> 和 <xref:System.Windows.Documents.BlockUIContainer> （请参阅上面的块派生类）。 假设我们需要 <xref:System.Windows.Documents.Table> 。 根据上面的关系图， <xref:System.Windows.Documents.Table> 包含包含 <xref:System.Windows.Documents.TableRowGroup> 元素的 <xref:System.Windows.Documents.TableRow> 元素，这些元素包含 <xref:System.Windows.Documents.TableCell> 一个派生的 <xref:System.Windows.Documents.Block> 对象。 下面是 <xref:System.Windows.Documents.Table> 从上图中获取的相应段。

![关系图：表的父&#47;子架构](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")

下面是对应的标记。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** 同样，下需要一个或多个 <xref:System.Windows.Documents.Block> 元素 <xref:System.Windows.Documents.TableCell> 。 为简单起见，在单元格内部放置一些文本。 使用带有元素的可以实现此目的 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Run> 。 下图显示了关系图中的相应段，其中显示了 <xref:System.Windows.Documents.Paragraph> 可以采用 <xref:System.Windows.Documents.Inline> 元素，并且 <xref:System.Windows.Documents.Run> （ <xref:System.Windows.Documents.Inline> 元素）只能采用纯文本。

![关系图：段落的父&#47;子架构](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")

![关系图：用于运行的父&#47;子架构](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")

下面是标记中的完整示例。

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>自定义文本

通常，文本是流文档中最普遍的内容类型。 尽管上面介绍的对象可用于控制文本呈现方式的大多数方面，但本文还介绍了其他一些自定义文本的方法。

### <a name="text-decorations"></a>文本修饰

使用文本修饰，可向文本应用下划线、上划线、基线和删除线效果（请参见下图）。 使用 <xref:System.Windows.Documents.Inline.TextDecorations%2A> 由多个对象（包括 <xref:System.Windows.Documents.Inline> 、 <xref:System.Windows.Documents.Paragraph> 、和）公开的属性添加这些修饰 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> 。

以下示例演示如何设置 <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> 的 <xref:System.Windows.Documents.Paragraph> 属性。

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

下图显示了此示例的呈现效果。

![屏幕快照：具有默认删除线效果的文本](./media/inline-textdec-strike.png "Inline_TextDec_Strike")

下图显示了上**划线**、**基线**和**下划线**修饰的分别呈现方式。

![屏幕快照：上划线 TextDecorator](./media/inline-textdec-over.png "Inline_TextDec_Over")

![屏幕快照：文本上的默认基线效果](./media/inline-textdec-base.png "Inline_TextDec_Base")

![屏幕快照：具有默认下划线效果的文本](./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>版式

与 <xref:System.Windows.Documents.TextElement.Typography%2A> 流相关的大部分内容（包括 <xref:System.Windows.Documents.TextElement> 、、和）公开此属性 <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Controls.TextBox> 。 此属性用于控制文本的版式特征/变体（即小型大写字母或大型大写字母、设置上标和下标等）。

下面的示例演示如何 <xref:System.Windows.Documents.TextElement.Typography%2A> 使用 <xref:System.Windows.Documents.Paragraph> 作为示例元素来设置特性。

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

下图显示了此示例的呈现效果。

![屏幕快照：改变版式的文本](./media/textelement-typog.png "TextElement_Typog")

与此相反，下图显示了一个具有默认版式属性的类似示例的呈现效果。

![屏幕快照：改变版式的文本](./media/textelement-typog-default.png "TextElement_Typog_Default")

下面的示例演示如何以 <xref:System.Windows.Controls.TextBox.Typography%2A> 编程方式设置属性。

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

有关版式的详细信息，请参阅[WPF 中的版式](typography-in-wpf.md)。

## <a name="see-also"></a>请参阅

- [Text](optimizing-performance-text.md)
- [WPF 中的版式](typography-in-wpf.md)
- [操作指南主题](flow-content-elements-how-to-topics.md)
- [TextElement 内容模型概述](textelement-content-model-overview.md)
- [RichTextBox 概述](../controls/richtextbox-overview.md)
- [WPF 中的文档](documents-in-wpf.md)
- [表概述](table-overview.md)
- [批注概述](annotations-overview.md)
