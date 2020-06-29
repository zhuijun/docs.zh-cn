---
title: 为控件创建样式
description: 了解如何在 Windows Presentation Foundation 和 .NET Core 中创建和引用控件样式。
author: adegeo
ms.author: adegeo
ms.date: 09/12/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: de186cd6da83ffef8a5cd59df581e88b24bc474d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325789"
---
# <a name="create-a-style-for-a-control-in-wpf"></a>在 WPF 中为控件创建样式

使用 Windows Presentation Foundation (WPF)，可以使用自己的可重用样式自定义现有控件的外观。 可以对应用、窗口和页面全局应用样式，也可以将样式直接应用于控件。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="create-a-style"></a>创建样式

可以将 <xref:System.Windows.Style> 视为一种将一组属性值应用到一个或多个元素的便利方法。 可以对从 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement>（如 <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Button>）派生的任何元素使用样式。

声明样式的最常见方法是在 XAML 文件的 `Resources` 部分中声明为样式。 样式是一种资源，因此它们遵从适用于所有资源的相同范围规则。 简言之，声明样式的位置会影响样式的应用范围。 例如，如果在应用定义 XAML 文件的根元素中声明样式，则该样式可以在应用中的任何位置使用。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/App.xaml#AppResources)]

如果在应用的一个 XAML 文件中声明样式，则该样式只能在该 XAML 文件中使用。 有关资源的范围规则的详细信息，请参阅 [XAML 资源](xaml-resources-define.md)。

[!code-xaml[AppResources](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowSingleResource.xaml#WindowResources)]

样式由 `<Setter>` 子元素组成，这些元素在应用了样式的元素上设置属性。 在上面的示例中，请注意，样式已设置为通过 `TargetType` 属性应用于 `TextBlock` 类型。 样式会将 <xref:System.Windows.Controls.Control.FontSize%2A> 设置为 `15`，并将 <xref:System.Windows.Controls.Control.FontWeight%2A> 设置为 `ExtraBold`。 为样式更改的每个属性添加一个 `<Setter>`。

## <a name="apply-a-style-implicitly"></a>隐式应用样式

<xref:System.Windows.Style> 是一种将一组属性值应用到多个元素的便利方法。 例如，请考虑以下 <xref:System.Windows.Controls.TextBlock> 元素及其在窗口中的默认外观。

[!code-xaml[TextBlocks](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetTextBlocks)]

![样式设置示例屏幕截图](./media/styles-and-templates-overview/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")

可以通过直接对每个 <xref:System.Windows.Controls.TextBlock> 元素设置属性（如 <xref:System.Windows.Controls.Control.FontSize%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A>）来更改默认外观。 但是，如果需要让 <xref:System.Windows.Controls.TextBlock> 元素共享某些属性，可以在 XAML 文件的 `Resources` 部分中创建 <xref:System.Windows.Style>，如下所示。

[!code-xaml[DefaultTextBlockStyle](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window1.xaml#SnippetDefaultTextBlockStyle)]

将样式的 <xref:System.Windows.Style.TargetType%2A> 设置为 <xref:System.Windows.Controls.TextBlock> 类型并省略 `x:Key` 属性时，该样式将应用到样式的所有 <xref:System.Windows.Controls.TextBlock> 元素，通常是 XAML 文件本身。

现在 <xref:System.Windows.Controls.TextBlock> 元素如下所示。

![样式设置示例屏幕截图](./media/styles-and-templates-overview/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")

## <a name="apply-a-style-explicitly"></a>显式应用样式

如果向样式添加具有值的 `x:Key` 属性，则样式将不再隐式应用于 <xref:System.Windows.Style.TargetType%2A> 的所有元素。 只有显式引用样式的元素才会应用样式。

下面是上一节中的样式，但使用 `x:Key` 属性进行了声明。

[!code-xaml[ExplicitStyleDeclare](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleDeclare)]

若要应用样式，请使用 [StaticResource 标记扩展](../../framework/wpf/advanced/staticresource-markup-extension.md)将元素上的 <xref:System.Windows.FrameworkElement.Style%2A> 属性设置为 `x:Key` 值，如下所示。

[!code-xaml[ExplicitStyleReference](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/WindowExplicitStyle.xaml#ExplicitStyleReference)]

请注意，第一个 <xref:System.Windows.Controls.TextBlock> 元素已应用样式，而第二个 TextBlock 元素保持不变。 上一节中的隐式样式已更改为声明了 `x:Key` 属性的样式，也就是说，该样式影响的唯一元素是直接引用该样式的那个元素。

![样式设置示例屏幕截图](./media/styles-and-templates-overview/create-a-style-explicit-textblock.png "create-a-style-explicit-textblock")

在显式或隐式应用样式后，它将变为密封状态，不能更改。 如果要更改已应用的样式，请创建新的样式来替换现有样式。 有关更多信息，请参见 <xref:System.Windows.Style.IsSealed%2A> 属性。

可以创建一个根据自定义逻辑选择要应用的样式的对象。 有关示例，请参阅为 <xref:System.Windows.Controls.StyleSelector> 类提供的示例。

## <a name="apply-a-style-programmatically"></a>以编程方式应用样式

若要以编程方式将已命名的样式分配到元素，请从资源集合中获取样式，并将其分配到元素的 <xref:System.Windows.FrameworkElement.Style%2A> 属性。 资源集合中的项属于 <xref:System.Object> 类型。 因此，在将检索到的样式分配给 `Style` 属性之前，必须将它强制转换为 <xref:System.Windows.Style?displayProperty=fullName>。 例如，下面的代码将名为 `textblock1` 的 `TextBlock` 的样式设置为定义的样式 `TitleText`。

[!code-csharp[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml.cs#SnippetSetStyleCode)]
[!code-vb[SetStyleCode](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/MainWindow.xaml.vb#SnippetSetStyleCode)]

## <a name="extend-a-style"></a>扩展样式

也许你希望两个 <xref:System.Windows.Controls.TextBlock> 元素共享某些属性值，如 <xref:System.Windows.Controls.Control.FontFamily%2A> 和居中的 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>。 你可能还希望文本“My Pictures”  具有一些其他属性。 可以通过创建基于第一个样式的新样式来实现此目的，如下所示。

[!code-xaml[DefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

[!code-xaml[TextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

此 `TextBlock` 样式现在居中，使用大小为 `26` 的 `Comic Sans MS` 字体，并将前景色设置为如示例中显示的 <xref:System.Windows.Media.LinearGradientBrush>。 请注意，它会重写基本样式的 <xref:System.Windows.Controls.Control.FontSize%2A> 值。 如果有多个 <xref:System.Windows.Setter> 指向 <xref:System.Windows.Style> 中的同一属性，则最后声明的 `Setter` 优先。

<xref:System.Windows.Controls.TextBlock> 元素现在如下所示：

![带样式的 TextBlock](./media/styles-and-templates-overview/stylingintro-textblocks.png "StylingIntro_TextBlocks")

此 `TitleText` 样式扩展为 <xref:System.Windows.Controls.TextBlock> 类型创建的样式，该样式由 `BasedOn="{StaticResource {x:Type TextBlock}}"` 引用。 还可以使用样式的 `x:Key` 扩展具有 `x:Key` 的样式。 例如，如果有一个名为 `Header1` 的样式，并且你需要扩展该样式，可以使用 `BasedOn="{StaticResource Header1}"`。

## <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType 属性与 x:Key 属性之间的关系

如前所述，将 <xref:System.Windows.Style.TargetType%2A> 属性设置为 `TextBlock` 时，如果不为样式分配 `x:Key`，会导致将样式应用于所有 <xref:System.Windows.Controls.TextBlock> 元素。 在此情况下，`x:Key` 隐式设置为 `{x:Type TextBlock}`。 这意味着，如果将 `x:Key` 值显式设置为除 `{x:Type TextBlock}` 以外的任何值，则 <xref:System.Windows.Style> 不会自动应用于所有 `TextBlock` 元素。 相反，必须将该样式（通过使用 `x:Key` 值）显式应用到 `TextBlock` 元素。 如果你的样式位于资源部分中，并且你未对样式设置 `TargetType` 属性，则必须设置 `x:Key` 属性。

除了为 `x:Key` 提供默认值以外，`TargetType` 属性还指定 setter 属性应用到的类型。 如果不指定 `TargetType`，则必须使用语法 `Property="ClassName.Property"`，通过类名称限定 <xref:System.Windows.Setter> 对象中的属性。 例如，必须将 <xref:System.Windows.Setter.Property%2A> 设置为 `"TextBlock.FontSize"` 或 `"Control.FontSize"`，而不是设置 `Property="FontSize"`。

另请注意，许多 WPF 控件由其他 WPF 控件的组合构成。 如果创建应用于某个类型的所有控件的样式，可能会产生意外结果。 例如，如果创建一个样式，该样式以 <xref:System.Windows.Window>中的 <xref:System.Windows.Controls.TextBlock> 类型为目标，那么，即使 `TextBlock` 是另一个控件（如 <xref:System.Windows.Controls.ListBox>）的一部分，该样式也将应用于窗口中的所有 `TextBlock` 控件。

## <a name="see-also"></a>请参阅

<!-- - [Create a style for a control](styles-templates-create-apply-template.md) -->
- [XAML 资源概述](xaml-resources-define.md)
- [XAML 概述（WPF 和 .NET Core）](xaml.md)
