---
title: 在 WPF 中创建模板 - .NET 桌面
description: 了解如何在 Windows Presentation Foundation 和 .NET Core 中创建和引用控件模板。
author: adegeo
ms.author: adegeo
ms.date: 11/15/2019
no-loc:
- <Window>
- <ControlTemplate>
- <Ellipse>
- <ContentPresenter>
- <Trigger>
- <Setter>
- <PropertyTrigger>
- <Grid>
- <VisualStateManager.VisualStateGroups>
- <VisualStateGroup>
- <VisualState>
- <Storyboard>
- SizeToContent
- MinWidth
- TargetType
- Title
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.openlocfilehash: c372659676b450cde789c96e45c7ec5de2aea194
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325721"
---
# <a name="create-a-template-for-a-control"></a>创建控件模板

使用 Windows Presentation Foundation (WPF)，可以使用自己的可重用模板自定义现有控件的可视结构和行为。 可以对应用程序、窗口和页面全局应用模板，也可以将模板直接应用于控件。 需要新建控件的大多数场景均可改为为现有控件创建新模板。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

本文将介绍如何为 <xref:System.Windows.Controls.Button> 控件创建新的 <xref:System.Windows.Controls.ControlTemplate>。

## <a name="when-to-create-a-controltemplate"></a>何时创建 ControlTemplate

控件有许多属性，例如 <xref:System.Windows.Controls.Border.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A> 和 <xref:System.Windows.Controls.Control.FontFamily%2A>。 这些属性控制控件外观的不同方面，但可通过设置这些属性进行的更改有限。 例如，可以从 <xref:System.Windows.Controls.CheckBox> 中将 <xref:System.Windows.Controls.Control.Foreground%2A> 属性设置为蓝色，并将 <xref:System.Windows.Controls.Control.FontStyle%2A> 设置为斜体。 要自定义设置控件中其他属性无法实现的控件外观时，则创建 <xref:System.Windows.Controls.ControlTemplate>。

在多数用户界面中，按钮的总体外观相同：即一个包含某些文本的矩形。 若想要创建一个圆形的按钮，可以创建一个继承自该按钮或重新创建该按钮功能的新控件。 此外，新用户控件还会提供圆形视觉对象。

通过自定义现有控件的可视布局，可以避免创建新控件。 借助圆形按钮，可创建具有所需可视布局的 <xref:System.Windows.Controls.ControlTemplate>。

另一方面，如果你需要具有新功能、其他属性和新设置的控件，可创建新的 <xref:System.Windows.Controls.UserControl>。

## <a name="prerequisites"></a>先决条件

创建新的 WPF 应用程序，在 MainWindow.xaml（或选择的其他窗口）的 \<Window> 元素中设置以下属性：

|     |     |
| --- | --- |
| **Title**         | `Template Intro Sample` |
| **SizeToContent** | `WidthAndHeight` |
| **MinWidth**      | `250` |

将 \<Window> 元素的内容设置为以下 XAML：

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

最后，MainWindow.xaml 文件应如下所示：

[!code-xaml[InitialWhole](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#InitialWhole)]

如果你运行应用程序，它将如下所示：

![包含两个无样式的按钮的 WPF 窗口](media/create-apply-template/unstyled-button.png)

## <a name="create-a-controltemplate"></a>创建 ControlTemplate

声明 <xref:System.Windows.Controls.ControlTemplate> 的最常见方法是在 XAML 文件的 `Resources` 部分中声明为资源。 模板是资源，因此它们遵从适用于所有资源的相同范围规则。 简言之，声明模板的位置会影响模板的应用范围。 例如，如果在应用程序定义 XAML 文件的根元素中声明模板，则该模板可以在应用程序中的任何位置使用。 如果在窗口中定义模板，则仅该窗口中的控件可以使用该模板。

首先，将 `Window.Resources` 元素添加到 MainWindow.xaml 文件：

[!code-xaml[WindowResStart](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window2.xaml#WindowResStart)]

使用以下属性创建新的 \<ControlTemplate>：

|     |     |
| --- | --- |
| **x:Key**         | `roundbutton` |
| **TargetType**    | `Button` |

此控制模板很简单：

- 控件的根元素 <xref:System.Windows.Controls.Grid>
- 用于绘制按钮圆形外观的 <xref:System.Windows.Shapes.Ellipse>
- 用于显示用户指定的按钮内容的 <xref:System.Windows.Controls.ContentPresenter>

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#ControlTemplate)]

### <a name="templatebinding"></a>TemplateBinding

创建新的 <xref:System.Windows.Controls.ControlTemplate> 时，可能仍然想要使用公共属性更改控件外观。 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 标记扩展将 <xref:System.Windows.Controls.ControlTemplate> 中元素的属性绑定到由控件定义的公共属性。 使用 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 时，可让控件属性用作模板参数。 换言之，设置控件属性后，该值将传递到包含 [TemplateBinding](../../framework/wpf/advanced/templatebinding-markup-extension.md) 的元素。

### <a name="ellipse"></a>椭圆形

请注意，\<Ellipse> 元素的 :::no-loc text="Fill"::: 和 :::no-loc text="Stroke"::: 属性绑定到了控件的 <xref:System.Windows.Controls.Control.Foreground> 和 <xref:System.Windows.Controls.Control.Background> 属性  。

### <a name="contentpresenter"></a>ContentPresenter

此外，还将 [\<ContentPresenter>](xref:System.Windows.Controls.ContentPresenter) 元素添加到了模板。 此模板专为按钮设计，因此请注意该按钮继承自 <xref:System.Windows.Controls.ContentControl>。 此按钮会显示该元素的内容。 可以在该按钮中设置任何内容，例如纯文本，甚至其他控件。 以下两个按钮均有效：

```xaml
<Button>My Text</Button>

<!-- and -->

<Button>
    <CheckBox>Checkbox in a button</CheckBox>
</Button>
```

在前面的两个示例中，将文本和复选框设置为 [Button.Content](xref:System.Windows.Controls.ContentControl.Content) 属性。 设置为内容的任何内容都可通过 \<ContentPresenter> 显示，这是模板的功能。

若将 <xref:System.Windows.Controls.ControlTemplate> 应用到 <xref:System.Windows.Controls.ContentControl> 类型（例如 `Button`），将在元素树中搜索 <xref:System.Windows.Controls.ContentPresenter>。 若找到了 `ContentPresenter`，模板会自动将控件的 <xref:System.Windows.Controls.ContentControl.Content> 属性绑定到 `ContentPresenter`。

## <a name="use-the-template"></a>使用模板

找到本文开头声明的按钮。

[!code-xaml[Initial](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window1.xaml#Initial)]

将第二个按钮的 <xref:System.Windows.Controls.Control.Template> 属性设置为 `roundbutton` 资源：

[!code-xaml[StyledButton](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButton)]

若运行项目并查看结果，将看到此按钮具有圆形背景。

![包含一个模板椭圆按钮的 WPF 窗口](media/create-apply-template/styled-button.png)

你可能已注意到，此按钮不是一个圆形，而是倾斜的。 由于 \<Ellipse> 元素的工作方式，它始终会扩展并填充可用空间。 将此按钮的 :::no-loc text="width"::: 和 :::no-loc text="height"::: 属性更改为同一个值，以使圆形均衡： 

[!code-xaml[StyledButtonSize](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window3.xaml#StyledButtonSize)]

![包含一个模板圆形按钮的 WPF 窗口](media/create-apply-template/styled-uniform-button.png)

## <a name="add-a-trigger"></a>添加触发器

即使已应用模板的按钮看上去与众不同，但它的行为与任何其他按钮相同。 若按下此按钮，将触发 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 事件。 不过，你可能已注意到，当你将鼠标移到此按钮上方时，此按钮的视觉对象不会改变。 这些视觉对象交互均由模板定义。

通过 WPF 提供的动态事件和属性系统，你可以监视特定属性是否是某个值，必要时还可重新设置模板样式。 在此示例中，你将监视按钮的 <xref:System.Windows.UIElement.IsMouseOver> 属性。 当鼠标位于控件上方时，使用新颜色设置 \<Ellipse> 的样式。 此触发器类型称为 PropertyTrigger。

必须为 \<Ellipse> 添加一个可引用的名称，以便于触发器起作用。 将其命名为“backgroundElement”。

[!code-xaml[EllipseName](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml#EllipseName)]

接下来，将新的 <xref:System.Windows.Trigger> 添加到 [ControlTemplate.Triggers](xref:System.Windows.Controls.ControlTemplate.Triggers) 集合。 此触发器将监视 `IsMouseOver` 事件是否为值 `true`。

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window4.xaml?name=ControlTemplate&highlight=6-10)]

接下来，将 \<Setter> 添加到 \<Trigger>，后者会将 \<Ellipse> 的 Fill 属性更改为一种新颜色   。

[!code-xaml[MouseOver](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#MouseOver)]

运行该项目。 请注意，将鼠标移到按钮上方时，\<Ellipse> 的颜色会改变。

![鼠标移到 WPF 按钮上方，以更改填充色](media/create-apply-template/mouse-move-over-button.gif)

## <a name="use-a-visualstate"></a>使用 VisualState

视觉状态由控件定义和触发。 例如，当鼠标移到控件上方时，将触发 `CommonStates.MouseOver` 状态。 可以基于控件的当前状态对属性更改进行动画处理。 在上一个部分中，当 `IsMouseOver` 属性为 `true` 时，使用 \<PropertyTrigger> 可将按钮的前景色更改为 `AliceBlue`。 可改为创建一个视觉状态，来对此颜色的更改进行动画处理，以实现平稳过过渡。 有关 VisualStates 的详细信息，请参阅 [WPF 中的样式和模板](../fundamentals/styles-templates-overview.md#visual-states)。

若要将 \<PropertyTrigger> 转换为动画效果的视觉状态，首先要从模板删除 \<ControlTemplate.Triggers> 元素 。

[!code-xaml[CleanTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window5.xaml#CleanTemplate)]

接下来，在控件模板的 \<Grid> 根中，为 `CommonStates` 添加具有 \<VisualStateGroup> 的 \<VisualStateManager.VisualStateGroups> 元素  。 定义两种状态：`Normal` 和 `MouseOver`。

[!code-xaml[VisualState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#VisualState)]

触发 \<VisualState> 时，将应用该状态中定义的任何动画。 为每种状态创建动画。 动画位于 \<Storyboard> 元素中。 有关情节提要的详细信息，请参阅[情节提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

- 普通

  此状态对椭圆填充进行动画处理，将其还原为控件的 `Background` 颜色。

  [!code-xaml[NormalState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#NormalState)]

- MouseOver

  此状态对椭圆 `Background` 颜色进行动画处理，将其更改为新颜色 `Yellow`。

  [!code-xaml[MouseOverState](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window6.xaml#MouseOverState)]

\<ControlTemplate> 现在应如下所示 。

[!code-xaml[FinalTemplate](~/samples/snippets/desktop-guide/wpf/styles-templates-create-apply-template/csharp/Window7.xaml#FinalTemplate)]

运行该项目。 请注意，将鼠标移到按钮上方时，\<Ellipse> 的颜色会进行动画处理。

![鼠标移到 WPF 按钮上方，以更改填充色](media/create-apply-template/mouse-move-over-button-visualstate.gif)

## <a name="next-steps"></a>后续步骤

- [在 WPF 中为控件创建样式](../fundamentals/styles-templates-create-apply-style.md)
- [WPF 中的样式和模板](../fundamentals/styles-templates-overview.md)
- [XAML 资源概述](../fundamentals/xaml-resources-define.md)
