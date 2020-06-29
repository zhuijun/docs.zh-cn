---
title: 样式和模板
description: 了解适用于 .NET Core 的 Windows Presentation Foundation (WPF) 中的 XAML 资源。 了解与样式和主题相关的 XAML 资源类型。
author: adegeo
ms.author: adegeo
ms.date: 09/09/2019
dev_langs:
- csharp
- vb
ms.openlocfilehash: faa54e0a3c827717114ca6ca4f033c1c4c3acfa8
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325785"
---
# <a name="styles-and-templates-in-wpf"></a>WPF 中的样式和模板

Windows Presentation Foundation (WPF) 样式设置和模板化是指一套功能，这套功能使开发者和设计者能够为其产品创建极具视觉表现力的效果和一致的外观。 自定义应用的外观时，需要一个强大的样式设置和模板化模型，以便维护和共享应用内部和应用之间的外观。 WPF 就提供了这样的模型。

WPF 样式设置模型的另一项功能是将呈现与逻辑分离。 设计者可以仅使用 XAML 处理应用外观，与此同时开发者使用 C# 或 Visual Basic 处理编程逻辑。

本概述侧重于应用的样式设置和模板化两方面，不讨论任何数据绑定概念。 有关数据绑定的信息，请参阅[数据绑定概述](../data/data-binding-overview.md)。

了解资源很重要，正是这些资源使样式和模板能够重复使用。 有关资源的详细信息，请参阅 [XAML 资源](xaml-resources-define.md)。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="sample"></a>示例

本概述中提供的示例代码基于下图所示的[简单照片浏览应用程序](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

![带样式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

此简单照片示例使用样式设置和模板化创建极具视觉表现力的用户体验。 该示例具有两个 <xref:System.Windows.Controls.TextBlock> 元素和一个绑定到图像列表的 <xref:System.Windows.Controls.ListBox> 控件。

有关完整示例，请参阅[样式设置和模板化示例简介](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)。

## <a name="styles"></a>样式

可以将 <xref:System.Windows.Style> 视为一种将一组属性值应用到多个元素的便捷方法。 可以对从 <xref:System.Windows.FrameworkElement> 或 <xref:System.Windows.FrameworkContentElement> 派生的任何元素（如 <xref:System.Windows.Window> 或 <xref:System.Windows.Controls.Button>）使用样式。

声明样式的最常见方法是在 XAML 文件的 `Resources` 部分中声明为资源。 样式是一种资源，因此它们遵从适用于所有资源的相同范围规则。 简而言之，声明样式的位置会影响样式的应用范围。 例如，如果在应用定义 XAML 文件的根元素中声明样式，则该样式可以在应用中的任何位置使用。

例如，以下 XAML 代码为 `TextBlock` 声明了两个样式，一个自动应用于所有 `TextBlock` 元素，另一个则必须显式引用。

[!code-xaml[SnippetDefaultTextBlockStyleBasedOn](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetDefaultTextBlockStyleBasedOn)]

下面举例说明了如何使用上面声明的样式。

[!code-xaml[SnippetTextBlocksExplicit](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window2.xaml#SnippetTextBlocksExplicit)]

![带样式的 TextBlock](./media/styles-and-templates-overview/stylingintro-textblocks.png)

有关详细信息，请参阅[为控件创建样式](styles-templates-create-apply-style.md)。

## <a name="controltemplates"></a>ControlTemplate

在 WPF 中，控件的 <xref:System.Windows.Controls.ControlTemplate> 用于定义控件的外观。 可以通过定义新的 <xref:System.Windows.Controls.ControlTemplate> 并将其分配给控件来更改控件的结构和外观。 在许多情况下，模板提供了足够的灵活性，从而无需自行编写自定义控件。

每个控件都有一个分配给 [Control.Template](xref:System.Windows.Controls.Control.Template) 属性的默认模板。 该模板将控件的视觉呈现与控件的功能关联起来。 因为在 XAML 中定义了模板，所以无需编写任何代码即可更改控件的外观。 每个模板都是为特定控件（例如 <xref:System.Windows.Controls.Button>）设计的。

通常在 XAML 文件的 `Resources` 部分中将模板声明为资源。 与所有资源一样，将应用范围规则。

控件模板比样式复杂得多。 这是因为控件模板重写了整个控件的视觉外观，而样式只是将属性更改应用于现有控件。 但是，控件模板是通过设置 [Control.Template](xref:System.Windows.Controls.Control.Template) 属性来应用的，因此可以使用样式来定义或设置模板。

设计器通常允许创建现有模板的副本并进行修改。 例如，在 Visual Studio WPF 设计器中，选择一个 `CheckBox` 控件，然后右键单击并选择“编辑模板” > “创建副本”   。 此命令会生成一个*用于定义模板的样式*。

```xaml
<Style x:Key="CheckBoxStyle1" TargetType="{x:Type CheckBox}">
    <Setter Property="FocusVisualStyle" Value="{StaticResource FocusVisual1}"/>
    <Setter Property="Background" Value="{StaticResource OptionMark.Static.Background1}"/>
    <Setter Property="BorderBrush" Value="{StaticResource OptionMark.Static.Border1}"/>
    <Setter Property="Foreground" Value="{DynamicResource {x:Static SystemColors.ControlTextBrushKey}}"/>
    <Setter Property="BorderThickness" Value="1"/>
    <Setter Property="Template">
        <Setter.Value>
            <ControlTemplate TargetType="{x:Type CheckBox}">
                <Grid x:Name="templateRoot" Background="Transparent" SnapsToDevicePixels="True">
                    <Grid.ColumnDefinitions>
                        <ColumnDefinition Width="Auto"/>
                        <ColumnDefinition Width="*"/>
                    </Grid.ColumnDefinitions>
                    <Border x:Name="checkBoxBorder" Background="{TemplateBinding Background}" BorderThickness="{TemplateBinding BorderThickness}" BorderBrush="{TemplateBinding BorderBrush}" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="1" VerticalAlignment="{TemplateBinding VerticalContentAlignment}">
                        <Grid x:Name="markGrid">
                            <Path x:Name="optionMark" Data="F1 M 9.97498,1.22334L 4.6983,9.09834L 4.52164,9.09834L 0,5.19331L 1.27664,3.52165L 4.255,6.08833L 8.33331,1.52588e-005L 9.97498,1.22334 Z " Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="1" Opacity="0" Stretch="None"/>
                            <Rectangle x:Name="indeterminateMark" Fill="{StaticResource OptionMark.Static.Glyph1}" Margin="2" Opacity="0"/>
                        </Grid>
                    </Border>
                    <ContentPresenter x:Name="contentPresenter" Grid.Column="1" Focusable="False" HorizontalAlignment="{TemplateBinding HorizontalContentAlignment}" Margin="{TemplateBinding Padding}" RecognizesAccessKey="True" SnapsToDevicePixels="{TemplateBinding SnapsToDevicePixels}" VerticalAlignment="{TemplateBinding VerticalContentAlignment}"/>
                </Grid>
                <ControlTemplate.Triggers>
                    <Trigger Property="HasContent" Value="true">
                        <Setter Property="FocusVisualStyle" Value="{StaticResource OptionMarkFocusVisual1}"/>
                        <Setter Property="Padding" Value="4,-1,0,0"/>

... content removed to save space ...
```

通过编辑模板副本可以很好地了解模板的工作原理。 与其新建一个空白模板，不如编辑副本并更改视觉呈现的某些方面来得简单。

有关示例，请参阅[为控件创建模板](../themes/how-to-create-apply-template.md)。

### <a name="templatebinding"></a>TemplateBinding

你可能已经注意到，上一部分中定义的模板资源使用了 [TemplateBinding 标记扩展](../../framework/wpf/advanced/templatebinding-markup-extension.md)。 对于模板方案来说，`TemplateBinding` 是绑定的优化形式，类似于使用 `{Binding RelativeSource={RelativeSource TemplatedParent}}` 构造的绑定。 `TemplateBinding` 可用于将模板的各个部分绑定到控件的各个属性。 例如，每个控件都有一个 <xref:System.Windows.Controls.Control.BorderThickness> 属性。 可使用 `TemplateBinding` 管理此控件设置影响模板中的哪个元素。

### <a name="contentcontrol-and-itemscontrol"></a>ContentControl 和 ItemsControl

如果在 <xref:System.Windows.Controls.ContentControl> 的 <xref:System.Windows.Controls.ControlTemplate> 中声明了 <xref:System.Windows.Controls.ContentPresenter>，<xref:System.Windows.Controls.ContentPresenter> 将自动绑定到 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 和 <xref:System.Windows.Controls.ContentControl.Content%2A> 属性。 同样，<xref:System.Windows.Controls.ItemsControl> 的 <xref:System.Windows.Controls.ControlTemplate> 中的 <xref:System.Windows.Controls.ItemsPresenter> 将自动绑定到 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 和 <xref:System.Windows.Controls.ItemsControl.Items%2A> 属性。

## <a name="datatemplates"></a>DataTemplate

在此示例应用中，有一个绑定到照片列表的 <xref:System.Windows.Controls.ListBox> 控件。

[!code-xaml[ListBox](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window3.xaml#SnippetListBox)]

此 <xref:System.Windows.Controls.ListBox> 当前如下所示。

![应用模板之前的 ListBox](./media/styles-and-templates-overview/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")

大多数控件都具有某些类型的内容，并且该内容通常来自要绑定到的数据。 在此示例中，数据是照片列表。 在 WPF 中，使用 <xref:System.Windows.DataTemplate> 定义数据的视觉表示形式。 基本上，放入 <xref:System.Windows.DataTemplate> 的内容决定了数据在呈现的应用中的外观。

在示例应用中，每个自定义 `Photo` 对象都有一个字符串类型的 `Source` 属性，用于指定图像的文件路径。 当前，照片对象显示为文件路径。

[!code-csharp[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Photo.cs#PhotoClass)]
[!code-vb[PhotoClass](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/vb/Photo.vb#PhotoClass)]

若要使照片显示为图像，请将 <xref:System.Windows.DataTemplate> 创建为资源。

[!code-xaml[DataTemplate](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window4.xaml#SnippetDataTemplate)]

请注意，<xref:System.Windows.DataTemplate.DataType%2A> 属性与 <xref:System.Windows.Style> 的 <xref:System.Windows.Style.TargetType%2A> 属性相似。 如果 <xref:System.Windows.DataTemplate> 在 resources 部分中，则在将 <xref:System.Windows.DataTemplate.DataType%2A> 属性指定为某个类型并且省略 `x:Key` 时，只要该类型出现，就会应用 <xref:System.Windows.DataTemplate>。 始终可以选择为 <xref:System.Windows.DataTemplate> 分配 `x:Key`，然后将其设置为采用 <xref:System.Windows.DataTemplate> 类型的属性（例如 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> 属性或 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> 属性）的 `StaticResource`。

实质上，上述示例中的 <xref:System.Windows.DataTemplate> 定义每当存在 `Photo` 对象时，它都应显示为 <xref:System.Windows.Controls.Border> 内的 <xref:System.Windows.Controls.Image>。 有了这个 <xref:System.Windows.DataTemplate>，我们的应用现在如下所示。

![照片图](./media/styles-and-templates-overview/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")

数据模板化模型提供其他功能。 例如，如果要使用 <xref:System.Windows.Controls.HeaderedItemsControl> 类型（例如 <xref:System.Windows.Controls.Menu> 或 <xref:System.Windows.Controls.TreeView>）显示包含其他集合的集合数据，可以使用 <xref:System.Windows.HierarchicalDataTemplate>。 另一个数据模板化功能是 <xref:System.Windows.Controls.DataTemplateSelector>，该功能允许基于自定义逻辑选择要使用的 <xref:System.Windows.DataTemplate>。 有关详细信息，请参阅[数据模板化概述](../../framework/wpf/data/data-templating-overview.md)，该概述提供不同数据模板化功能的更多深入讨论。

## <a name="triggers"></a>触发器

触发器在属性值发生更改或引发事件时设置属性或启动操作，例如动画。 <xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate> 和 <xref:System.Windows.DataTemplate> 都具有可包含一组触发器的 `Triggers` 属性。 触发器分为几种类型。

### <a name="propertytriggers"></a>PropertyTrigger

根据属性的值设置属性值或启动操作的 <xref:System.Windows.Trigger> 称为属性触发器。

若要演示如何使用属性触发器，可以使每个 <xref:System.Windows.Controls.ListBoxItem> 在未选中时部分透明。 以下样式将 <xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.UIElement.Opacity%2A> 值设置为 `0.5`。 但是，当 <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A> 属性为 `true` 时，<xref:System.Windows.UIElement.Opacity%2A> 设置为 `1.0`。

[!code-xaml[PropertyTrigger](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window5.xaml#SnippetPropertyTrigger)]

此示例使用 <xref:System.Windows.Trigger> 设置属性值，但请注意，<xref:System.Windows.Trigger> 类还有 <xref:System.Windows.TriggerBase.EnterActions%2A> 和 <xref:System.Windows.TriggerBase.ExitActions%2A> 属性，这些属性可使触发器执行操作。

请注意，<xref:System.Windows.Controls.ListBoxItem> 的 <xref:System.Windows.FrameworkElement.MaxHeight%2A> 属性设置为 `75`。 在下图中，第三项是选中的项。

![带样式的 ListView](./media/styles-and-templates-overview/stylingintro-triggers.png "StylingIntro_triggers")

### <a name="eventtriggers-and-storyboards"></a>EventTrigger 和情节提要

另一个触发器类型是 <xref:System.Windows.EventTrigger>，用于根据某个事件的发生启动一组操作。 例如，以下 <xref:System.Windows.EventTrigger> 对象指定当鼠标指针进入 <xref:System.Windows.Controls.ListBoxItem> 时，<xref:System.Windows.FrameworkElement.MaxHeight%2A> 属性在 `0.2` 秒的时间内动画化为值 `90`。 当鼠标离开该项时，属性在 `1` 秒的时间内返回到原始值。 请注意，不需要为 <xref:System.Windows.ContentElement.MouseLeave> 动画指定 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> 值。 这是因为动画能够跟踪原始值。

[!code-xaml[StyleEventTriggers](~/samples/snippets/desktop-guide/wpf/styles-and-templates-intro/csharp/Window6.xaml#SnippetStyleEventTriggers)]

有关详细信息，请参阅[情节提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

在下图中，鼠标指向第三项。

![样式设置示例屏幕截图](./media/styles-and-templates-overview/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTrigger、DataTrigger 和 MultiDataTrigger

除了 <xref:System.Windows.Trigger> 和 <xref:System.Windows.EventTrigger>，还有其他类型的触发器。 <xref:System.Windows.MultiTrigger> 允许基于多个条件设置属性值。 当条件的属性为数据绑定时，使用 <xref:System.Windows.DataTrigger> 和 <xref:System.Windows.MultiDataTrigger>。

## <a name="visual-states"></a>视觉状态

控件始终处于特定的**状态**。 例如，当鼠标在控件的表面上移动时，该控件被视为处于公用状态 `MouseOver`。 没有特定状态的控件被视为处于公用 `Normal` 状态。 状态分为多个组，前面提到的状态属于 `CommonStates` 状态组。 大多数控件都有两个状态组：`CommonStates` 和 `FocusStates`。 在应用于控件的每个状态组中，控件始终处于每个组的一种状态，例如 `CommonStates.MouseOver` 和 `FocusStates.Unfocused`。 但是，控件不能处于同一组中的两种不同状态，例如 `CommonStates.Normal` 和 `CommonStates.Disabled`。 下面是大多数控件可以识别和使用的状态表。

| VisualState 名称 | VisualStateGroup 名称 | 描述 |
| ---------------- | --------------------- | ----------- |
| 普通           | CommonStates          | 默认状态。 |
| MouseOver        | CommonStates          | 鼠标指针悬停在控件上方。 |
| 已按下          | CommonStates          | 已按下控件。 |
| 已禁用         | CommonStates          | 已禁用控件。 |
| 已设定焦点          | FocusStates           | 控件有焦点。 |
| 失去焦点        | FocusStates           | 控件没有焦点。 |

通过在控件模板的根元素上定义 <xref:System.Windows.VisualStateManager?displayProperty=fullName>，可以在控件进入特定状态时触发动画。 `VisualStateManager` 声明要监视的 <xref:System.Windows.VisualStateGroup> 和 <xref:System.Windows.VisualState> 的组合。 当控件进入受监视状态时，将启动 `VisaulStateManager` 定义的动画。

例如，以下 XAML 代码监视 `CommonStates.MouseOver` 状态，以对名为 `backgroundElement` 的元素的填充颜色进行动画处理。 当控件恢复为 `CommonStates.Normal` 状态时，将还原名为 `backgroundElement` 的元素的填充颜色。

```xaml
<ControlTemplate x:Key="roundbutton" TargetType="Button">
    <Grid>
        <VisualStateManager.VisualStateGroups>
            <VisualStateGroup Name="CommonStates">
                <VisualState Name="Normal">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="{TemplateBinding Background}"
                                    Duration="0:0:0.3"/>
                </VisualState>
                <VisualState Name="MouseOver">
                    <ColorAnimation Storyboard.TargetName="backgroundElement"
                                    Storyboard.TargetProperty="(Shape.Fill).(SolidColorBrush.Color)"
                                    To="Yellow"
                                    Duration="0:0:0.3"/>
                </VisualState>
            </VisualStateGroup>
        </VisualStateManager.VisualStateGroups>

        ...
```

有关情节提要的详细信息，请参阅[情节提要概述](../../framework/wpf/graphics-multimedia/storyboards-overview.md)。

## <a name="shared-resources-and-themes"></a>共享资源和主题

典型的 WPF 应用可能具有多个 UI 资源，它们可应用于整个应用。 这组资源统称为应用的主题。 WPF 支持使用封装为 <xref:System.Windows.ResourceDictionary> 类的资源字典将 UI 资源打包为主题。

WPF 主题通过使用 WPF 公开的样式设置和模板化机制来定义，该机制用于自定义任何元素的视觉对象。

WPF 主题资源存储在嵌入的资源字典中。 这些资源必须嵌入到已签名的程序集内，并且可以嵌入到与代码本身相同的程序集内或并行程序集内。 对于包含 WPF 控件的程序集 PresentationFramework.dll，主题资源位于一系列并行程序集内。

该主题成为在搜索元素样式时最后查看的位置。 通常，搜索先沿着元素树搜索适当的资源，然后在应用资源集合中查找，最后查询系统。 这样一来，应用开发者便有机会在到达主题之前在树或应用级别上为任何对象重新定义样式。

可以将资源字典定义为单独的文件，这些文件支持跨多个应用重复使用主题。 还可以通过定义多个资源字典来创建可交换的主题，这些资源字典以不同的值提供相同类型的资源。 在应用级别上重新定义这些样式或其他资源是设计应用外观的推荐方法。

若要跨应用共享一组资源（包括样式和模板），可创建 XAML 文件，并定义包含对 `shared.xaml` 文件的引用的 <xref:System.Windows.ResourceDictionary>。

```xaml
<ResourceDictionary.MergedDictionaries>
  <ResourceDictionary Source="Shared.xaml" />
</ResourceDictionary.MergedDictionaries>
```

它是 `shared.xaml` 的共享，用于定义包含一组样式和画笔资源的 <xref:System.Windows.ResourceDictionary>，从而使应用中的控件具有一致的外观。

有关详细信息，请参阅[合并资源字典](../../framework/wpf/advanced/merged-resource-dictionaries.md)。

如果要为自定义控件创建主题，请参阅[控件创作概述](../../framework/wpf/controls/control-authoring-overview.md#defining-resources-at-the-theme-level)的**在主题级别定义资源**部分。

## <a name="see-also"></a>请参阅

- [WPF 中的 Pack URI](../../framework/wpf/app-development/pack-uris-in-wpf.md)
- [如何：查找由 ControlTemplate 生成的元素](../../framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)
- [查找由 DataTemplate 生成的元素](../../framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
